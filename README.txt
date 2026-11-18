# Neerada Primary Grading System

This ZIP contains the unified entry flow for both Lower Primary and Higher Primary while preserving the existing grading systems.

## Entry flow
- `splash.html` is the first page and automatically opens `login.html`.
- `login.html` accepts both teacher and student accounts and routes the account to the correct Lower Primary or Higher Primary system.
- `lower.html` and `higher.html` retain the existing grading behavior.
- Each signed-in account has a Logout button that returns to `login.html`.
- Student accounts open a read-only student page showing the student's profile data and the grades recorded by teachers.

## Files
- `splash.html` — splash screen.
- `login.html` — unified teacher/student login.
- `lower.html` / `higher.html` — existing grading applications with only the requested session/logout/student-view changes.
- `lower.css` / `higher.css` — existing separated stylesheets.
- `*-config.json` — existing Firebase configuration.
- `*-users.json` — temporary teacher/student accounts.
- `*-roster.json` — class/student roster data.

The lower portal has 25 classrooms × 35 students = 875 students. The higher portal has 12 classrooms × 35 students = 420 students; because a higher-primary teacher count was not explicitly supplied, the package uses one teacher account per classroom (12).

Firebase quotas/storage remain controlled by the Firebase project plan and console. No Firebase configuration or database structure was changed for this request.

Admin portal:
- Username: admin
- Password: Admin123!
- Admin dashboard shows total students, teachers, classes, and accounts across both systems.
- Admin can set shared system name and one overall logo; that logo is also used as the favicon and Apple touch icon.
- Teacher settings and rosters are now scoped to each teacher account.
- Student accounts have a read-only personal dashboard plus their existing grade view.

- Teacher/student accounts have account-specific profile information and profile photos; teacher/student settings no longer provide a logo upload.
- Admin branding is available from the Admin Settings gear.

Data persistence:
- Lower Primary application data and account-specific settings are stored in the Lower Primary Firebase Firestore project.
- Higher Primary application data and account-specific settings are stored in the Higher Primary Firebase Firestore project.
- Shared system branding and administrator profile data are stored in Firebase and are available across browsers/devices.
- Application data is no longer written to browser localStorage or IndexedDB as the data source of truth.
