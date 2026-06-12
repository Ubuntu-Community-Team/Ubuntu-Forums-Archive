---
title: "Suspend &amp; Hibernate Issues"
date: 2008-03-30
forum: General Help
---

### Post by alsoknownas on 2008-03-30
I'm running Ubuntu Gusty 7.10 on my laptop which has an AMD Turion64 processor. I have seen other threads on this issue but I have encountered problems with the methods they suggest.

When I try to Suspend my laptop I get the message:
>  "suspend2ram failed on unloading 'usb_storage'. Trying to recover....."
 and when I go to hibernate I get the message:
>  "The resume partition is not setup. Probably you need to add a 'resume=...' option to your kernel command line and reboot. Suspend to disk and resume is not possible without a resume partition. please consult the documentation. You can skip this check by setting SUSPEND2DISK_SKIP_RESUME_CHECK to 'yes' in the sleep configuration file" 

I have installed both the uswsusp & powersaved packages after reading other threads about this issue. When using uswsusp I get the message in the terminal that the s2ram command cannot be found and s2disk "Could not stat the resume device file. Reason: No such file or directory".

How would I go about adding a "resume=..." option to my kernel command line, and what's the problem with not being able to unload "usb_storage? And is a resume partition the same as a swap partition or would I need to create a separate partition?

What would you suggest to get suspend and hibernate working again? :confused:

---

### Post by alsoknownas on 2008-03-31
Bump...anyone...

---

### Post by madmatrixz3000 on 2008-04-02
I'm having the same problem HELP!!!

---

### Post by pointone on 2008-04-02
Your resume partition is indeed the swap partition. Edit /boot/grub/menu.lst and scroll down to the bottom. Check to see if your Ubuntu GRUB menu entries have "resume=/dev/*d*#" in the "kernel" line, as in "resume=/dev/sda3", where "/dev/*d*#" is your swap partition.

---

