---
title: "Win XP in VMware: need to defrag?"
date: 2006-09-01
forum: General Help
---

### Post by tribaal on 2006-09-01
Hi folks!

I just finished installing VMware server (using this guide), and started out by creating a WinXP virtual machine. I know, installing XP over Ubuntu seems pretty odd, but I need a working Windows copy on my Ubuntu Laptop for school (learning .net and such), and I'm not going to go through the hassle of installing XP over Ubuntu, resize, and reinstall Ubuntu.

So my question is:

XP now has around 10Gb of allocated disk space, in the form of files (the regular way for VMware to create virtual machines). My fresh XP install shows 15% of fragmentation (urgh!), should I defrag my winxp "ntfs" virtual drive (which sits on a physical ext3 filesystem)? 
Will defraggin' the virtual drive have any impact on performances?

Also, will my virtual XP benefit from linux's memory management policy (i.e. using RAM as disk cache when unused)?

Thanks a lot.

- trib'

PS: Moderators, please move my thread around as you see fit, I don't know if it belongs in this subforum...

---

### Post by GTvulse on 2006-09-01
Yes, but don't limit yourself to defrag with the WinXP utilitiy. Use VMWare tools. That'll allow you to recover real disk space both in the VM image and in the host filesystem. On you question about memory management, the answer isn't as simple. VMWare manages memory for its virtual machines, and the host OS manages memory for VMWare.

---

### Post by tribaal on 2006-09-01
Ok, I will follow your advice on defrag, thanks a lot!
Edit: Just did, it works great, and it's much faster, too. Thanks a lot for the tip :)

However I think you missed my point on the memory management side: I was wondering if windows XP would benefit from the disk cache usage of linux's RAM, speeding up winXP's (that's to say VMware's) accesses to the physical hard drive... ? The process is explained perfectly on the page I link to in my signature (the first one): unused RAM is filled up with disk cache, and it's swapped out when something elses suddently needs the memory.

If my understanding of how VMware works is correct, then I guess the answer is yes. However I'd like to know that "for sure", because I'm curious :)


Hope this all makes sense?

- trib'

---

### Post by GTvulse on 2006-09-02
He :-). I think I'll expand a bit. Windows uses its own memory management and that includes its own swap and disk cache. VMWare is cleverly lying to it telling it that it is running in its own hardware. In order to do this, VMWare has to emulate all the low-level hardware interactions and in doing so, it has to take over a lot of the high-level services that usually would be provided directly by the kernel (no matter that the kernel be Linux, FreeBSD, WinNT (a.k.a XP) whatever). So, any benefit of disk cache management by the host OS is occuring through several layers of indirection. That means that, if you want to increase the speed and performance of your virtual machine, you have to do two things, first increase the amount of total physical RAM of the host OS. and second, assign enough of that RAM to the VM so that the VM can load all the OS and apps into memory. Say 2Gb of real RAM and give 1Gb to the VM.

---

### Post by tribaal on 2006-09-02
Oh ok so VMware manages memory and disk at kernel level. I guess I'm used to emulation too much, actually VMware goes way beyond that.

Thanks for the answer!

- trib'

---

