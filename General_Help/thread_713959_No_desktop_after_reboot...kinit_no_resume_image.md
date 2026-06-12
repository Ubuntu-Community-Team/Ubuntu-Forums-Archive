---
title: "No desktop after reboot...kinit: no resume image"
date: 2008-03-03
forum: General Help
---

### Post by seeker1458 on 2008-03-03
I just got done installing syslog-ng and went to do a reboot. I get the grub loader, and the ubuntu splash screen, but the system loads to the shell, not the desktop environment. I have tried running "sudo apt-get install ubuntu-desktop" and it says that I've got the most current version. So I tried re-installing it, no luck. I also tried reconfiguring xserver. But when I finish and type "startx" it flicks to a black and white checker-boarded screen with a big black "X" as the pointer, then shuts the monitor off. Tower still is up and running but no signal is being put out to the monitor. I can log in through shell and access files and such, but why is my nice desktop now a black screen? 

Upon boot this is what I get:

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/1164e1-2530-4687-9aad-f8cba13417ab = s
da5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/1164e1-2530-4687-9aad-f8cba1341
7ab
kinit: No resume image, doing normal boot...

Ubuntu 7.10 syslog1-desktop tty1

syslog1-desktop login:

***don't be confused, the name of the system is syslog1...not going to be used for anything but a syslog server***

---

### Post by linuxtoindia on 2008-03-22
sudo dpkg-reconfigure xserver-xorg''

after that type gdm
or reinstall gdm
or such commands
def

---

