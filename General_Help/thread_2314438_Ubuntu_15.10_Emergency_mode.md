---
title: "Ubuntu 15.10: Emergency mode"
date: 2016-02-21
forum: General Help
---

### Post by Macamba on 2016-02-21
**Yesterday my system booted fine, now it starts in 'emergency mode'. What are my options?**

I got a new computer, installed a second harddisk, on which I installed Ubuntu 15.10. I moved data from my old system to the new one using SSH. Yesterday I actually booted both to Ubuntu and Windows 10 without a problem. When I now start the computer, select Ubuntu from Grub I go into emergency mode. The only thing I now is that I performed an update yesterday. One where I did not have to enter my password.

The message coming with the emergency mode (see also the screen picture):
```
[1.890391] radeon 0000:01:00.0 VCE init error (-110)
fcsk from util-linux 2.26.2
/def/sdb1: clean, 251166/1564672 files, 1206115/6249728 blocks
Welcome to emergency mode! After logging in, type "journalctl -xb" to view 
system logs, "systemctl reboot" to reboot, "systemctl default" or ^D to 
try again to boot into default mode.
root@Hermod:~#
```

[B][LIST]
[*]What do I need to do to log in into Linux on the command line? I can not login with my user account (with admin rights)
[*]What can I do to get my system running again?
[/LIST][/B]


[IMG]http://s12.postimg.org/5vwoe9lvx/boot_failed.jpg[/IMG]

---

### Post by Macamba on 2016-02-21
I did a quick search on **radeon 0000:01:00.0 VCE init error**. I see it is a quite common bug with AMD/Ubuntu 15.10. Install Ubuntu 14.04.4 LTS?

---

### Post by Macamba on 2016-02-22
ATM I'm installing 14.04.

---

