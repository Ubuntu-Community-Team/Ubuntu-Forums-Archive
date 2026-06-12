---
title: "Screen size in virtualbox"
date: 2007-07-16
forum: General Help
---

### Post by ali780 on 2007-07-16
Hi
How can I change the sreen of Windows Xp that is installed in virtualbox in ubuntu 7.04 a little bigger?
Thanks

---

### Post by prodezigner on 2007-07-16
This is the easiest way I know how to do it:

1) Install Guest Additions (when running WinXP click on the middle menu item at the top, I think it's Machine...<doing this from memory>)

2) Right click on the CD in the bottom right and choose Disc Image... it should be listed in that field, select it.

3) Run it in Windows XP, choose OK and Continue on the drivers.

4) Reboot your virtual machine and then change the CD-ROM back from Image to CD/DVD ROM

5) IF YOU WANT TO RUN FULLSCREEN: Open a terminal... type: gnome-session-remove gnome-panel

THIS WILL KILL YOUR GUI FOR UBUNTU!!!! TO GET IT BACK, PRESS CTRL-ALT-BACKSPACE!!!!

6) Now in VirtualBox press CTRL-F (right side CTRL) for fullscreen and the same to leave it.

Hope this helps.

---

