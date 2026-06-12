---
title: "Ubuntu won't start"
date: 2014-01-29
forum: General Help
---

### Post by Lingonsylt on 2014-01-29
Not sure if my problem is a general ubuntu one or if it is specifically related to mac, so I dont know in which area to put the thread, but I try here.

I was browsing the web when firefox froze, so I tried to restart it but didnt work. Tried chromium, same problem. Got an empty error-message-box. Restarted the computer but then ubuntu wouldnt start. Usually, before the screen whith the logo where the discs are checked, some text rolls over the screen too fast to read. Now, ubuntu stops at this text and does not go on. I rebooted to OSX and safari worked, but crashed every now and then. I never use OSX, and it is about 4-5 years old and never updated so I am not sure if the safari crash is because of the outdated version, or if both the safari problem and the ubuntu problem is because of trouble with the harddrive.

I fear that the hard-drive might have crashed...

Any body who has an idea what has gone wrong, if it can be fixed or how?

---

### Post by ian-weisser on 2014-01-29
If the hard drive crashed, then do you think it's likely OSX would work?

What, exactly does that mysterious startup text (that you can now read because it stops) say?

Have you booted into your Recovery Mode from GRUB? To check your logs in /var/log/syslog?

Do you have a Live media (CD or USB) handy? You may need it to run fsck (filesystem check application, which cannot run while the disk is mounted)

---

### Post by Lingonsylt on 2014-01-30
Thank you for your answer.

I have experienced external flashdrives that krashed when still some of the data where intact, other partly damaged and some completely lost, so to me it seems possible that OSX could work, but I may be wrong.

The text on the screen is this:

mount: mounting /dev on /root/dev failed : No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesysten doesnt have /sbin/init.
[1.572041] usb 4-1: new full speed USB device using ohci_hcd and address 2
No limit found. Try passing init=bootarg.

BusyBox v1.13.3 ( (ubuntu 1:1.13.3 Ubuntu11) built-in shell (ash)
Enter ¨help¨ for a list of built-in commands.

(initramfs) 1.7733131 usb 4-1: configuration #1 chosen from 1 choice
[ 1.797144] hub 4-1:1.0 USB hub not found
[ 1.800109] hub 4-1:1.0 3 ports detected
[ 2.116099] usb 3-5: new low speed USB deviceusing ohc i_hcdand address 2
[ 2.332172] usb 3-5: configuration #1 chosen from 1 choice
[ 2.640102] usb 3-6: new full speed USB device using ohc i_hcd and address 3
[ 2.864171] usb 3-6: configuration #1 chosen from 1 choise
[ 2.954171] usb 4-1.1: new full speed USB device using ohc i_hcd and address 3
[ 3.077174] usb 4-1.1: configuration #1 chosen from 1 choice
[ 3.158106] usb 4-1.2: new full speed USB device using ohci_hcd and address 4
[ 3.269168] usb 4-1.2: configuration #1 chosen from 1 choice

Trying to boot in recovery mode gives the same problem.

I shall try to use the cd.

---

### Post by Lingonsylt on 2014-01-30
I found an old cd with ubuntu 9.04, but I am not sure how to use fsck.

---

### Post by ian-weisser on 2014-01-30
> **Lingonsylt said:**
> 
The text on the screen is this:

mount: mounting /dev on /root/dev failed : No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesysten doesnt have /sbin/init.

BusyBox v1.13.3 ( (ubuntu 1:1.13.3 Ubuntu11) built-in shell (ash)
Enter ¨help¨ for a list of built-in commands.

The system is trying to tell you that it cannot mount root filesystem (/).
That is sometimes due to a problem with the filesystem itself.
However, it is sometimes due to grub pointing to the wrong or mislabeled disk.

How to use fsck from a Live media has been explained many times in this forum, so I won't duplicate all that work here.
Here's an example: [http://ubuntuforums.org/showthread.php?t=1518426](http://ubuntuforums.org/showthread.php?t=1518426)

---

### Post by Lingonsylt on 2014-01-30
Thank you!

That was a whole lot of errors on that disk! Something with "inod" something that I didnt understand. But I have a fresh backup so I felt ok just pressing "y" every time fsck asked "fix?" and now it seems to work. It starts up nicely and seem to be ok. Thank you a lot!

---

### Post by ian-weisser on 2014-01-30
Glad it's working for you now!

---

