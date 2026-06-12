---
title: "Ubuntu startup screen is blank"
date: 2007-11-12
forum: General Help
---

### Post by aho on 2007-11-12
I have had this problem for ages now, and i am hoping i can finally get it fixed.

I'm now using Ubuntu 7.10, and the start up process is VERY SLOW, and the screen is blank, When the login screen finally shows up it works great! Im also having the same problem when shutting down.

Any suggestions on how i can fix this?
Please give any suggestions in small easy steps as i'm not an experienced user.

Thanks!

---

### Post by disturbedite on 2007-11-12
edit /boot/grub/menu.lst as root/su and remove quiet from the kernel section.

i.e. (mine)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=ab7af290-ce43-4e65-96df-b92e84791e95 ro *quiet* splash

or hit e at grub menu to edit and do that.

or simply hit alt+F2 every time after you select the kernel to boot.

---

### Post by aho on 2007-11-12
i have tryed all of that. and no good :-( still got the same problem.

Any more suggestions?

---

### Post by aho on 2007-11-12
Still stuck. 

Is there anything else i can do to fix this?

---

### Post by disturbedite on 2007-11-13
if nothing comes up when you hit alt+F2 after you choose your kernel then there is definitely something wrong.  (i'd say seriously wrong).

did you happen to edit the grub menu before?  if you did, perhaps you made a mistake you didn't realize that is preventing you from booting.

---

### Post by Iztari on 2007-11-13
Try what they did here to fix it: 
[http://ubuntuforums.org/showthread.php?t=596162]("http://ubuntuforums.org/showthread.php?t=596162")
That worked for me perfectly

---

### Post by aho on 2007-11-13
I have done what Iztari suggested, and now i get the following message on the startup:
```
Starting Up...
Loading, Please wait...
     Check root: bootary cat /proc/cmdline
     or missing modules, devices: /proc/modules ls /dev
ALERT! /dev/desk/by-uuid/68b2b7da-1394-4ff8-98fb-0d30d5fb5930 does not exist. Dr
opping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built in commands.
```

---

