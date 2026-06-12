---
title: "lockups"
date: 2005-04-03
forum: General Help
---

### Post by lee_connell on 2005-04-03
Hi all,

I need some assistance in figuring out why my system locks up completely and makes my hard drive light stay solid with no activity.  It happens at non-frequent times and never is the same so it's hard to say what's doing it.

Sometimes in firefox it does it, sometimes while ubuntu auto-mounts a cdrom, sometimes with the screensaver etc...

Can I set something up within my system to log activity or something to figure out why my system is locking up?  I am using a hp pavilion notebook w/ centrino.  512mb, 1.6ghz, 80gb harddrive.  I don't know if it's acpi causing it or the ipw2100 driver because that has reset problems when using acpi.  I have no clue what it is.

thanks,

Lee

---

### Post by ubuntu_demon on 2005-04-03
do a search first next time

might be RenderAccel "true" in your xorg.conf

see these threads :

[http://www.ubuntuforums.org/showthread.php?t=23388](http://www.ubuntuforums.org/showthread.php?t=23388)
[http://www.ubuntuforums.org/showthread.php?t=23473](http://www.ubuntuforums.org/showthread.php?t=23473)

---

### Post by lee_connell on 2005-04-05
I don't have renderaccel in my xorg.conf log, i'm using default xorg.conf made by ubuntu, just replaced ati driver with fglrx.  

How about inotify, it seems this isn't totally stable yet so i'll try the noinotify to the boot and see what happens.

---

### Post by vnbuddy2002 on 2005-04-06
I had the same problem, but after doing some research on it. I finally got my system stable. 

There are a couple of things that cause the system lockup

1. Memory.
- Make sure your memory is in good condition. I suggest you use memtest86 do extensive tests. Make sure all tests are passed.

2. noapic
- [http://ubuntuforums.org/showpost.php?p=44442&postcount=8](http://ubuntuforums.org/showpost.php?p=44442&postcount=8)


Unfortunately, my system experienced both of the issues. After all that, everything is acting "normal"...... At least so far...

---

