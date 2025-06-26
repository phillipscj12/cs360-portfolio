**1. App Goals & User Needs**  
My Weight-Tracking app allows users to log daily weights, view them in a grid, and optionally receive SMS reminders when they hit goals. It addresses the need for a simple, on-the-go way to monitor weight trends and stay motivated.

**2. Screens & User-Centered UI**  
- **Login screen:** Secures each user’s data.  
- **Main grid:** Shows historical weight entries at a glance.  
- **Add-entry form:** Minimal inputs (weight + date) to keep logging friction low.  
- **Permissions prompt:** Lets users opt into SMS without blocking core features.  
I chose large, readable fonts and a clean layout so users of any age can tap and read easily.

**3. Coding Approach & Techniques**  
- I created a `DbHelper` class extending `SQLiteOpenHelper` for all CRUD operations.  
- I used Android’s **ViewBinding** and the **RecyclerView** pattern to keep UI and data code cleanly separated.  
- In future projects I’ll continue modularizing data access (e.g. repository pattern) and writing small helper methods to reduce duplication.

**4. Testing & Validation**  
- I ran the Android Emulator on API levels 21, 29, and 33.  
- I tested permission grant/deny flows for SMS.  
- I verified data persisted across restarts.  
This uncovered a bug where the RecyclerView wasn’t refreshing after an insert—and taught me to write a small `refreshData()` helper.

**5. Innovation & Challenges**  
I needed to handle users who denied SMS permission gracefully. Instead of crashing, I wrapped the `sendTextMessage()` call in a permission check and defaulted to an in-app toast notification.

**6. Key Strength**  
I’m most proud of my `DbHelper` abstraction: all SQLite schema, versioning, and CRUD logic lives in one place, making the rest of the app code easy to read and maintain.
