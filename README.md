# WaterDefender

WaterDefender is a Laravel application for the TLE2 project. It is currently the project foundation: a Laravel 13 application with Livewire 4, Blaze, Vite, and Tailwind CSS configured for iterative development.

## Current status

The application currently serves the Laravel welcome page at `/`. Domain-specific WaterDefender functionality has not yet been implemented. The repository includes the standard Laravel user, cache, and queue migrations, plus baseline unit and feature tests.

## Technology stack

- PHP 8.3 or newer
- Laravel 13
- Livewire 4 and Livewire Blaze
- Vite and Tailwind CSS 4
- SQLite by default (other Laravel-supported databases can be configured)
- Pest 5, Larastan, and Laravel Pint for testing, static analysis, and formatting

## Requirements

Install the following before setting up the project:

- PHP 8.3+
- Composer
- Node.js and npm (the repository specifies Node 26.13.1 and npm 12.2.3 through Volta)

## Installation

Clone the repository, enter the project directory, and run the bundled setup script:

```bash
git clone <repository-url>
cd WaterDefender
composer run setup
```

The setup script installs dependencies, creates `.env` from `.env.example` when needed, generates the application key, runs migrations, and builds frontend assets.

For a manual setup:

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
npm install
npm run build
```

On Windows PowerShell, use `Copy-Item .env.example .env` instead of `cp .env.example .env`.

## Running locally

Start the Laravel development environment with:

```bash
composer run dev
```

The application is normally available at [http://localhost:8000](http://localhost:8000). To run only the frontend asset watcher, use `npm run dev`.

## Testing and quality checks

Run the complete project check suite with:

```bash
composer run test
```

This clears configuration, checks formatting, runs Larastan, and executes Pest. Useful focused commands include:

```bash
php artisan test --compact
vendor/bin/pint --dirty --format agent
php artisan test tests/Feature/ExampleTest.php
phpstan analyse
```

## Project structure

```text
app/          Application code
bootstrap/    Framework bootstrapping
config/       Application configuration
database/     Migrations, factories, and seeders
resources/    Blade views, JavaScript, and CSS
routes/       HTTP and console routes
tests/        Pest feature and unit tests
public/       Web entry point and public assets
```

## Configuration

Runtime configuration is read from `.env`. The default configuration uses SQLite and stores sessions, cache, and queued jobs in the database. Do not commit local secrets or a populated `.env` file.

To use another database, update the relevant `DB_*` values in `.env` and run `php artisan migrate`.

## Contributing

Keep changes focused, follow the existing Laravel conventions, add or update Pest tests for behavior changes, and run `composer run test` before opening a pull request.

## License

This project is currently distributed under the MIT license declared by the application package metadata.
