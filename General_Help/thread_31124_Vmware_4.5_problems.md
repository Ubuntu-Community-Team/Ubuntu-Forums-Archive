---
title: "Vmware 4.5 problems"
date: 2005-05-01
forum: General Help
---

### Post by awilisch on 2005-05-01
I've installed vmware 4.5, compiled the kernel module, which it says works perfectly. vmware starts and I was able to register. however once I reboot, running vmware gives me a dialog saying it's not configured and I need to run vmware-config.pl. if I run this, it recomplies the module then it works fine until the next time I reboot. I've run into this problem with Gentoo as well, but I have never figured out what the problem is. Has anyone else run into this and might have a solution?

Regards,
Aric Wilisch

---

### Post by awilisch on 2005-05-02
Another thing. When I run vmware-config.pl it compiles the kernel modules (vmmon vmnet). If I do a search for vmmon I get the following:

/dev/vmmon
find: /proc/8032/task: No such file or directory
/sys/module/vmmon
/sys/class/misc/vmmon

Under /dev I see:

awilisch@dauntless:/dev$ ls -l vm*
crw-rw----  1 root root  10, 165 2005-05-02 21:08 vmmon
crw-------  1 root root 119,   0 2005-05-02 21:08 vmnet0
crw-------  1 root root 119,   1 2005-05-02 21:08 vmnet1
crw-------  1 root root 119,   8 2005-05-02 21:08 vmnet8
awilisch@dauntless:/dev$

After I reboot, doing a find / -name vmmon -print returns no results, and ls -l /dev/vm* returns no results. So for some reason, rebooting deletes these files. 

Anyone have any ideas why this would happen?

---

### Post by mlmurray on 2005-05-02
Well, I'm sorry I can't help you, but I've noticed this exact same behavior as well.  It looks like you're on the right track, though.  I hadn't thought to check the /dev/ directory.

No help. But, at least you know your not alone ... :???:

---

### Post by codejunkie on 2005-05-02
[http://www.ubuntulinux.org/wiki/VMware](http://www.ubuntulinux.org/wiki/VMware) this should help you get VMware 4.5 up and running hope this helps.

---

### Post by A-star on 2005-05-03
Maybe this thread can help you:
[http://www.ubuntuforums.org/showthread.php?t=24255](http://www.ubuntuforums.org/showthread.php?t=24255)

---

### Post by mlmurray on 2005-05-03
Thanks, codejunkie

I already had the any-any update, but hadn't run it yet thinking it only had to do with the 2.6.11 kernels.  I haven't rebooted yet, to see if my devices come back (still at work), but I have faith... :) 

-Mark

---

### Post by rothbart on 2005-05-03
[QUOTE=codejunkie][http://www.ubuntulinux.org/wiki/VMware](http://www.ubuntulinux.org/wiki/VMware) this should help you get VMware 4.5 up and running hope this helps.[/QUOTE]

I'd be curious if anyone can get DVD Decrypter to run using Ubuntu.  Yes, I've gotten it to run under Linux via WINE but I'm trying to get DVD Decrypter to access my NEC 1300A drive via VMware Workstation.  The drive is using SCSI emulation and while it shows up, I cannot get DVD Decrypter to make heads or tails of it.

Thanks for bringing up the vmware-config.pl problem, I'd just learned to live with it (although I thought it was use of apt-get that caused the config script to need to be run again -- I don't reboot too often).  I'll try those tips out as soon as I get a chance.  Thanks for bringing up the good question!

---

