> **Upload status (2026-09-24):** This repository currently contains documentation only. The backend and Flutter source have not yet been pushed. The setup commands below will work only after those directories are uploaded. Do not present this repository as a runnable demo yet.

# Laravel Market — Laravel + MySQL + Flutter

Independent learning portfolio project featuring a Laravel 12 e-commerce storefront and admin dashboard, REST API, MySQL database, and a separate Flutter Android customer app.

## Features
- Public product catalog; admin login, product management and order status management.
- Mobile customer registration/login, catalog search, cart, cash-on-delivery checkout, and order history.
- Server-side order totals and stock control.

## Run locally
Requirements: PHP 8.2+, Composer, MySQL/MariaDB, Flutter SDK and Android Studio. Create a MySQL database called `portfolio_laravel_shop`.

```powershell
cd backend
composer install
Copy-Item .env.example .env
# Set DB_USERNAME and DB_PASSWORD in .env
php artisan key:generate
php artisan migrate --seed
php artisan serve --host=0.0.0.0 --port=8000
```

In a separate terminal:

```powershell
cd mobile
flutter create --platforms=android .
flutter pub get
flutter run --dart-define=API_URL=http://10.0.2.2:8000/api
```

Enable Android HTTP cleartext for local development in `android/app/src/main/AndroidManifest.xml`; use HTTPS for any public deployment. See `mobile/README.md` for emulator vs physical-device details.

The local web storefront is at http://127.0.0.1:8000, with admin login at /login. Demo admin: `admin@example.com / password123`. Demo customer: `customer@example.com / password123`. **Change these credentials before public deployment.**

## Documentation

The client demo, mobile setup, and publishing guides are in the separately prepared source archive; they are not yet committed here.

## Scope and status

A portfolio **learning MVP**, not a production-ready commercial store. No payment processor, shipping integration, email verification, refunds, or production security review. Flutter Android platform scaffolding is generated locally via `flutter create`; no pre-built APK or live hosting is supplied. Full runtime and Android build were not verified in the generation environment.