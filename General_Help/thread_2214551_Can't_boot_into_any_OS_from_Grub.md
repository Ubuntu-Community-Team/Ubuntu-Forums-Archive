---
title: "Can't boot into any OS from Grub"
date: 2014-04-01
forum: General Help
---

### Post by JJossie on 2014-04-01
I'm pretty sure I know what I did wrong at first, but I don't know how to fix it. Anyways, when I boot into grub, the only options available are the two memtests. The other day I was fiddling around with grub Customizer and I guess I accidentally hid the options to boot into my two OS's, Win7 and ubuntu 13.10. So, basically, Grub works just fine, I'm 99% sure both operating systems are fine, it's just that I can't choose the option to boot into them from grub. Yes, I can access the command line, but I've looked up how to boot into Ubuntu from the command line, and I can't seem to get it. 
How do I use the command line to boot into ubuntu?

---

### Post by oldfred on 2014-04-01
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

      
 **Manual boot:**
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
#OR:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by JJossie on 2014-04-07
Well, I used your instructions for manual boot to get into ubuntu. It worked, and I was then able to put the options for Windows 7 and Ubuntu back on the grub menu (using grub customizer). When I rebooted, The command gave some error at first and all the fonts were messed up (that was like that before.) After the error, it still booted. Anyways, I'm trying to switch to BURG right now.

---

### Post by JJossie on 2014-04-10
Basically, the problem discussed in this thread is solved. so although I'm still having problems with BURG, I will be starting a new thread for that and marking this a solved.

---

