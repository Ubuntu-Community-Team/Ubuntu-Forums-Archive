---
title: "Linux partitioning. Dual boot, VMWare"
date: 2014-10-28
forum: General Help
---

### Post by sports fan Matt on 2014-10-28
My Windows 7 partition is running very well, and I'm using VMWare to run Ubuntu 14.04 and another Linux OS. While I don't mind doing this, would it be completely odd to only run W7 in VMWare and use Ubuntu as my main?  Or I could dual boot (Isn't that what I'm doing anyway kind of) W7 and 14.04?

I'd really like thoughts from the community as I'm not liking Windows 10, with the metro tiles, although I like the Windows 7 start menu.  Decisions, Decisions...

---

### Post by sammiev on 2014-10-28
I love to dual boot and use the VM for testing anything I want to test. Really it's up to you and enjoy what you want to do. :)

---

### Post by sports fan Matt on 2014-10-28
I dualbooted for four years..loved it too, and I'm really worried about Windows 10 for my clients...they may become confused...What if I set up W7 and Ubuntu 14.04 64 bit on C: then used Windows 10 and centos7 for VMWare?  If you look at my screenshot, how much would I need for W7 and 14.04?

---

### Post by sports fan Matt on 2014-10-28
Here is an updated screenshot.  Can I split my C drive because I cannot seem to shrink my Virtual machine drive F which I'd like to do and how much should I give the Virtual Machine drive?.

---

### Post by ajgreeny on 2014-10-28
I dual booted for many years after finding Ubuntu in 2005, but the problem was (if you want to call it a problem) that I only ever booted into Windows firstly to check that it ran properly, just in case I ever needed it, and secondly to update the virus checker that I ran on it.  Having started using Ubuntu in 2005 I never again really "used" Windows to really do anything, so it did eventually, of course, get written over by my Ubuntu, now Xubuntu, installation.

Interestingly, I now have to run my old WinXP as a VM solely to update my satnav, which not surprisingly, but very disappointingly, can not be done in Ubuntu or any other Linux OS.

My point?
Use whatever works for you.  If a VM of an OS works for you, be it Linux or Windows, run it and be happy.  There is no need to worry about what other people think; just do your own thing.

---

### Post by sports fan Matt on 2014-10-28
AJ, I completely understand. Part of the reason is I want things (like Ubuntu) that I am familiar with to run fast and tinker around with other things i'm not as familiar with.

---

### Post by sports fan Matt on 2014-10-28
I'd like to move my unallocated space to my C: drive on SDA2 without adding any more to my VMware partition's drive (Drive F). How can I complete this?

---

### Post by yancek on 2014-10-28
You can't do it directly.  You can expand partitions to contiguous space but in your case you have sda3 between your windows partition sda2 and the unallocated space.  Creating a partition out of the unallocated space and then moving your VMWare files to that partition would allow you to delete the current VMWare partition and use that unallocated space to add to sda2.  The problem with that is it adds the complication of changing that partition number.  Additionally, and more important is the fact that the amount Used on your VMWare is larger than your unallocated space so it won't really work.  If you want more space for windows, create an ntfs partition from the unallocated space.

---

### Post by sports fan Matt on 2014-10-28
So my next question is what can I do with the allocated space?

---

### Post by fantab on 2014-10-28
deleted.

---

### Post by sports fan Matt on 2014-10-29
I understand :)  I don't need like 125 GB for my Virtual machines so I'm trying to see what I can do :)

---

### Post by mörgæs on 2014-10-29
Threads merged. 
When dealing with the same or a closely related topic please keep everything in one thread.

---

### Post by yancek on 2014-10-29
You can create another partition for your windows with it as that is your primary OS.

Some people would refer to running a system in a virtual machine as dual-booting, others would not.  If something goes wrong with your windows, you can't boot Ubuntu as it is dependent upon it to boot, being installed inside windows.  The reverse would be the same case.

---

