---
title: "No Save/Open Window [Ubuntu 17.10]"
date: 2017-11-05
forum: General Help
---

### Post by kennycap on 2017-11-05
I tried to save a file using LibreOffice and all that happens is that the LibreOffice app turns grey and no save window shows up.  I initially though it had something to do with LibreOffice.  However, when I went onto Google Drive and tried to upload a file, no save/open window shows up.  My web browser just dims itself in a grey tone and no window shows up.  I even tried to upload files onto Canvas and other websites and I still don't have a save/open window showing up.  The web browser or application just dims to grey and that's it.  I'm beginning to think that it may be the OS that's the problem as it happens with Google Drive, YouTube, and any other app that prompts a file explorer to save/open files.

[ATTACH=CONFIG]277428[/ATTACH]
Edit: Here's the screenshot of LibreOffice.  I noticed something curious about this screenshot.  Even though my monitor is in 1440x900, it somehow seems wider than it actually is.  Looks like my screen resolution is too big for my laptop screen so it must have blocked out the save window.

---

### Post by deadflowr on 2017-11-05
Go to System settings >> Displays and try turning off the second monitor.
(Your system thinks you have a second monitor attached (maybe you do, maybe you don't) and the new desktop (gnome) now tries to open save dialogs in that second monitor/display)

EDIT:
Okay, so you need to go to System Settings >> Devices >> Display.
Then toggle the top settings to Single display.
Then click on the display you want (of the options for displays which should be listed right under the top layout bar (the top layout bar being the options to set as single, mirror or join)
Once you select the display check the Apply button in the corner to make the changes.

(You should not have to worry if by chance you choose the wrong display and cannot see the screen anymore, as the default settings must be okay-ed within 20 seconds or it automatically reverses itself back to the display previously set.)

Hope it helps, or makes sense.

---

