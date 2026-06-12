---
title: "Suspend Ubuntu for Dual Boot"
date: 2016-05-11
forum: General Help
---

### Post by the_mulletator on 2016-05-11
I am dual booting Windows 7 and Lubuntu.  Every time I switch to Windows I have to shut down my linux install and re-open everything when I come back.  I am looking for a way to save the state before I shut down and switch OSes.  Such that all the same programs are open in the same workspaces.

Has anyone done this?  The suspend function would work but I need to be able to access the GRUB menu when I hit the power button.  If I suspend now I just come right back to Lubuntu.

Thanks in advance.

---

### Post by egeezer on 2016-05-11
Dual booting is like establishing two entirely different computers on the same hard drive.  There is only one CPU and one RAM array, either of which can be controlled by one system or the other, but not by both simultaneously.  To suspend one while running the other would require you to have two RAM arrays so that the Lubuntu RAM would remain powered while the CPU is running Windows.  I'm not a hardware expert, but I've never heard of such an arrangement.

Edit: come to think of it, even that wouldn't work, because the full system doesn't reside in RAM during Suspend.

---

### Post by the_mulletator on 2016-05-11
I don't necessarily need to suspend.  Is there a way to save the state to the hard drive?  All I want to do is have the same state when I return to Ubuntu from Windows.

---

### Post by oldfred on 2016-05-11
That is called hibernation.

But I do not use hibernation as Ubuntu boots fast enough for me and I do not save state. I do see many threads on hibernation issues. Both Windows & Ubuntu.

Many in Forums suggest using VirtualBox or other virtual install.
But you need lots of RAM as you have to allocate between systems. And lose some speed, so not particularly good for gaming.

---

### Post by Bucky Ball on 2016-05-11
> **oldfred said:**
> Many in Forums suggest using VirtualBox or other virtual install.

+1. The absolutely easiest way to do what you are suggesting, but not suitable for everyone, every workflow or situation. Maybe it's suitable for yours, though ...

In effect, you have both OSs running at once. No rebooting, suspending, hibernating or anything else. Just launch Virtualbox and launch the Windows virtual machine (or the Ubuntu VM inside Windows) and you're there.

---

### Post by the_mulletator on 2016-05-11
I've used virtualbox lots.  Yeah that works but not for me.  I use windows for certain programs that need 100% of the computer resources.  I wish they would run in Linux, then I would have no need for Windows.

Hibernation might work.  Does anyone know how to set up hibernation so that it stores to disk and is accessible during boot?

---

### Post by the_mulletator on 2016-05-11
Hey, I may have found a solution.  I found a utility called s2disk. Here is the man page [s2disk]("http://manpages.ubuntu.com/manpages/trusty/man8/s2disk.8.html").  It hibernates to disk with some options for control.  

I just tested it and it seems to work as expected.  I was able to access the GRUB menu and run Windows.  Then on returning to linux my state stayed the same.

---

