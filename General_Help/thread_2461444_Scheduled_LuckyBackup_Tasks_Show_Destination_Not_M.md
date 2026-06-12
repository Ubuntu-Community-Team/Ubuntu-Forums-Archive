---
title: "Scheduled LuckyBackup Tasks Show Destination Not Mounted"
date: 2021-04-30
forum: General Help
---

### Post by G_M_Slater on 2021-04-30
I am running LuckyBackup version 0.5.0 on UbuntuStudio 21.04. If I open the program and run the selected profile/task manually, everything backs up to my USB drive normally. I also have that same profile/task scheduled to run each night. It runs, but the log shows that no actions were performed because the destination drive was not mounted (although it is). Does anyone know how to resolve this behavior?

---

### Post by Xian on 2021-04-30
Try a quick settings change:

Go to [FONT=Consolas]Profile > Schedule > and modify the schedule. 

Enable both of the options "Skip Critical" and "Console Mode".

[/FONT]

---

### Post by G_M_Slater on 2021-04-30
> **Xian said:**
> Try a quick settings change:

Go to [FONT=Consolas]Profile > Schedule > and modify the schedule. 

Enable both of the options "Skip Critical" and "Console Mode".

[/FONT]

Thanks for the tip. I will try it out and see what happens tonight when the task runs again.

---

### Post by G_M_Slater on 2021-05-01
Selecting the "Skip Critical" and "Console Mode" options resolved. Thank you for the quick help!

---

