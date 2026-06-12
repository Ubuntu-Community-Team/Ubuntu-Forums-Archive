---
title: "Why can't I see my text file changes?"
date: 2021-01-11
forum: General Help
---

### Post by rfresh737 on 2021-01-11
I have a java jar app. It opens a text file and reads in come configuration data. Part of this configuration data is the app's window size (top, left, width, height). This allows the user to move the window and when they quit the app, these values get written to this text file so upon the next start up, the window can be positioned to the last location. This works fine. I can move the main form window, quit, and restart the app. The main form window always restores to the last known location.

The problem (puzzle) for me is this: when I move the window and quit, I open the text file and look at the window values. I do not see the new values. I see the previous values, yet if I start up the app, the main form is right where it needs to be. So of course I think I must be going crazy here. Why don't I see the values in the text editor updated? The configuration file ends with a .cfg but it's a plain text file.

Thank you...

---

### Post by agvantibo on 2021-01-12
What text editor are you using? There most definitely should be a reload button.

---

### Post by HermanAB on 2021-01-12
Try doing a sysexec of the sync command to flush the file system buffers after saving the file.

---

