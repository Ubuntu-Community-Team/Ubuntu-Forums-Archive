---
title: "Power Hibernation Fail To Resume"
date: 2018-08-11
forum: General Help
---

### Post by kenneth17 on 2018-08-11
Screen goes to black when computer is inactive.

Moving mouse or typing on keyboard produces no result - computer fails to resume - screen remains black.

Only pushing power button and restarting works.

Please advise.

---

### Post by ajgreeny on 2018-08-11
Hibernation or just suspend?
What hardware do you have, as it may be that the graphics do not return to a properly working state?
What Ubuntu version?

The ability to hibernate has not been a default option for many versions of Ubuntu but can be enabled on some hardware. Very often however, the problem is that the system will not resume properly after coming back from hibernation.

---

### Post by kenneth17 on 2018-08-12
I just have the monitor the (Dell) computer came with.

Not sure what the difference is betweeen hibernation and suspend. The computer just stops responding and has a black screen.

Is there anything that I can do? Something in the the bios?

---

### Post by ajgreeny on 2018-08-12
If you have not enabled hibernation yourself then your computer goes into suspension, not hibernation.

After coming back to a black screen with no GUI desktop try using Ctrl+Alt+F2 to get to a command line and log in there with your username and password, (password will not appear as you type but will be entered so type carefully and hit Enter), then use command ```
sudo apt update
sudo apt upgrade
``` one by one to make sure your system is fully updated.

---

