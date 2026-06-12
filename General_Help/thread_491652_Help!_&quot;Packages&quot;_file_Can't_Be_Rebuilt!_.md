---
title: "Help! &quot;Packages&quot; file Can't Be Rebuilt! Scanpackages BROKEN! Please Help!"
date: 2007-07-03
forum: General Help
---

### Post by OzzyFrank on 2007-07-03
I have posted a thread about my drives being scanned while runnning dpkg-scanpackages:

[http://ubuntuforums.org/showthread.php?t=488482](http://ubuntuforums.org/showthread.php?t=488482)

The problems is it gets to the "find: Symbolic link" part and loops forever. I just let it run all night and it was still running in circles over that spot! I noticed last night the Packages file that is generated at the end of the process (and that package managers need) has not been updated since May, when I installed Feisty, so something is definitely amiss! I deleted the file in case, so now there is no Packages file, as the scanpackages process never ends so the output is never created. I think this may be why I had package managers slow my system to a crawl (then a halt) since installing Feisty.

Here is the point it gets stuck on and never recovers from:

[COLOR="Blue"]find: Symbolic link `./.wine/dosdevices/z:/sys/block/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/event4/device/bus/drivers/ehci_hcd/0000:02:0b.2/usb8/usb_device:usbdev8.1/subsystem/usbdev2.3/device/2-1:1.0/usb_endpoint:usbdev2.3_ep81/subsystem/usbdev7.1_ep00/device/7-1/driver/usb4/subsystem/devices/3-0:1.0/driver/8-0:1.0/ep_81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.[/COLOR]

Can SOMEONE please help with a suggestion, as this is somewhat more than trivial. Any command option I could add before executing the scanpackages command? ANYTHING??

---

### Post by kuja on 2007-07-05
I don't see any options for dealing with it. You should report it as a bug.

---

