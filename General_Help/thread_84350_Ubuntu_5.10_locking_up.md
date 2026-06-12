---
title: "Ubuntu 5.10 locking up"
date: 2005-10-30
forum: General Help
---

### Post by welly on 2005-10-30
Hello all,

I've just done an install of Ubuntu 5.10 (AMD64 version) on my Athlon 64 3000+. The install went fine with no errors. The system boots up happily, however after logging in, while the desktop is booting, the machine keeps locking up. I was told to try adding noinotify into the grub loader, which i've done but this doesn't seem to make a difference. Any suggestions would be really appreciated!

Thanks,

Alastair

---

### Post by welly on 2005-10-31
I've had a look through the syslog, messages and Xorg.0.log and there's nothing that really stands out to me why it's locking up so looking for other suggestions! Really need this machine up and running as it's my main machine and I don't want to go back to windows :( Any help would be really, really appreciated.

---

### Post by ubuntu_demon on 2005-10-31
Does it lock after the gdm login screen or before ?

If it locks after you try to log in then it might be just a case of wrong permissions of one or more essential files in ~

What videocard do you have ?

Please post your logs and xorg.conf

---

### Post by welly on 2005-10-31
[QUOTE=ubuntu_demon]Does it lock after the gdm login screen or before ?

If it locks after you try to log in then it might be just a case of wrong permissions of one or more essential files in ~

What videocard do you have ?

Please post your logs and xorg.conf[/QUOTE]

Yeah, it locks up just after I've logged in.. just before it would normally start displaying the service (window manager/nautilus etc) icons.

I've got an ATI x600 pro video card. The logs are as follows -

[http://www.transmogrify.co.uk/misc/faillog.txt](http://www.transmogrify.co.uk/misc/faillog.txt)
[http://www.transmogrify.co.uk/misc/messages.txt](http://www.transmogrify.co.uk/misc/messages.txt)
[http://www.transmogrify.co.uk/misc/syslog.txt](http://www.transmogrify.co.uk/misc/syslog.txt)
[http://www.transmogrify.co.uk/misc/xorg.conf.txt](http://www.transmogrify.co.uk/misc/xorg.conf.txt)
[http://www.transmogrify.co.uk/misc/Xorg.0.log.txt](http://www.transmogrify.co.uk/misc/Xorg.0.log.txt)

Many thanks!

Alastair

---

### Post by fishy6969 on 2005-10-31
Hi,

I've had exactly the same problem. The only way I've found to correct it was documented in this thread [http://www.ubuntuforums.org/showthread.php?t=78617&highlight=radeon+x600](http://www.ubuntuforums.org/showthread.php?t=78617&highlight=radeon+x600)
I've got as far as loading the vesa drivers and it seems to work fine. I'll try the next stage (the xorg-driver-fglrx driver) tomorrow)

---

