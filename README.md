## Reflection

### 1. What did you observe about the app lifecycle when switching between screens or minimizing the app?

By printing logs as I navigated the app, I noticed a clear pattern:

*   **When I go to Screen 2:** Screen 1 doesn't just disappear. First, it pauses (`onPause`), then Screen 2 gets created and started (`onCreate`, `onStart`, `onResume`). Only after Screen 2 is visible does Screen 1 fully stop (`onStop`).

*   **When I press Back to return to Screen 1:** The reverse happens. Screen 2 pauses, Screen 1 restarts and comes back into view (`onRestart`, `onStart`, `onResume`), and then Screen 2 is fully stopped and destroyed (`onStop`, `onDestroy`).

*   **When I minimize the app (press the home button):** The current screen quickly calls `onPause` and `onStop` as it goes into the background. When I open the app again, it comes back to life using `onRestart`, `onStart`, and `onResume`.

### 2. What did you learn about activity management in Android?

I learned that Android is very organized about how it handles screens (Activities). It's not random; it follows a strict set of rules called the **Activity Lifecycle**.

The main takeaway for me is that activities can be in different states: active, paused, or stopped (hidden). Knowing which state an activity is in is important. For example, I shouldn't have the app doing heavy work if it's just paused or stopped in the background, because that would waste the phone's battery. This project made it clear why `onCreate`, `onPause`, and the other lifecycle methods are so important for building good apps.
