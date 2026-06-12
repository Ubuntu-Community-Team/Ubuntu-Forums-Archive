---
title: "advice needed on troubleshooting boot problem"
date: 2017-09-12
forum: General Help
---

### Post by dougcb68 on 2017-09-12
On a Sager NP5855 Laptop running Ubuntu 16.04 LTS operating system.


After several weeks of behaving normally, the machine began to act as follows at power on after a normal shut down:


Power key pressed
Sager splash screen displays as normal
screen goes to normal desktop color but is otherwise blank
HD light blinks
screen blinks to black
returns to normal desktop color but is othrwise blank
HD light stops blinking
Nothing else happens no matter how long I wait.




At this point I can recover by:
1) Pressing the power button until machine shuts down
2) restarting the machine with the power button
3) Sager splash screen appears
4) GRUB loads
5) I choose Advanced Options for Ubuntu
6) then Ubuntu, with Linux 4.10.0-32generic (recovery mode)
7) It then boots and goes to: Recovery Menu (file system status: read only)
and I choose the resume normal boot option
It prompts that it is exiting recovery mode
then goes back to Recovery Menu (file system status: read only)
8) I choose the resume normal boot option
It prompts that it is exiting recovery mode


Finally, it boots up to my desktop and all is fine! Lucky me.


I would appreciate it if anybody could suggest the steps I might follow to resolve this issue.

---

### Post by TheFu on 2017-09-12
Welcome to the forums.

Look at the log files for any errors and warnings.  Probably want to ssh in from a different computer, since the desktop isn't responding. If that fails, use the recovery mode from an alternate boot media (so do NOT boot from the same disk), so you can look at the logs left from the failure.

Without knowledge of the logged issue, nobody can help.

---

### Post by lammert-nijhof on 2017-09-12
If you are logged in, you could go to the terminal and try the next commands:
> sudo grub-install /dev/sda 
sudo update-grub
and reboot, maybe it helps.

---

### Post by TheFu on 2017-09-12
> **lammert-nijhof said:**
> If you are logged in, you could go to the terminal and try the next commands:

and reboot, maybe it helps.

And it shouldn't harm anything, assuming sda is the correct boot device (it usually is).

---

