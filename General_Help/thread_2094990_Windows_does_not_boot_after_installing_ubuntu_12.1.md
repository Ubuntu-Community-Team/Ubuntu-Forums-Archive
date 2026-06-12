---
title: "Windows does not boot after installing ubuntu 12.10"
date: 2012-12-15
forum: General Help
---

### Post by kanishkdudeja on 2012-12-15
I was running windows 7 earlier.

when i installed ubuntu 12.10 in another partition, ubuntu booted fine.

But now when i boot windows, it says 

Disk Error. Press any key to restart.

What should i do?

---

### Post by Mark Phelps on 2012-12-15
What exactly did you do to create the partition space for Ubuntu?

Did you make the MISTAKE of using the Ubuntu installer to shrink the Win7 OS partition to make room?

---

### Post by oldfred on 2012-12-15
Lets see what is where.
      

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by kanishkdudeja on 2012-12-16
@Mark Phelps: yes maybe i did. not sure. it was some time back. but yeah it does seem to me that this is why this happened.

@oldfred: il soon post the boot info report. probably then you guys will be able to introspect better as to why is it happening and how it could be solved.

---

