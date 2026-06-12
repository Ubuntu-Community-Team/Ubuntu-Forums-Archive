---
title: "No GRUB found"
date: 2013-02-27
forum: General Help
---

### Post by juapo2 on 2013-02-27
Hello,

So I had Windows and then I installed Ubuntu in a partition a couple of years ago. Today I wanted to remove Windows and I used OS Uninstaller GUI to remove both WIN partitions. Everything was cool at this point. I inserted WinXP cd, as I decided to remove the previous Win I had and leave a small WinXP copy in my drive, so when the WinXP setup loaded, I accidentally deleted two partitions, of about 2GB each. I rebooted and I was hoping I had not removed my Ubuntu, but a message saying "GRUB not found" appeared and wouldnt boot Ubuntu.

My questions is WHAT DID I DO!?

Any help is greatly appreciated, I have years of files and logins from my work there, and it would be really bad to lose them all.

Regards,
Richi

---

### Post by fdrake on 2013-02-28
> **juapo2 said:**
> Hello,

So I had Windows and then I installed Ubuntu in a partition a couple of years ago. Today I wanted to remove Windows and I used OS Uninstaller GUI to remove both WIN partitions. Everything was cool at this point. I inserted WinXP cd, as I decided to remove the previous Win I had and leave a small WinXP copy in my drive, so when the WinXP setup loaded, I accidentally deleted two partitions, of about 2GB each. I rebooted and I was hoping I had not removed my Ubuntu, but a message saying "GRUB not found" appeared and wouldnt boot Ubuntu.

My questions is WHAT DID I DO!?

Any help is greatly appreciated, I have years of files and logins from my work there, and it would be really bad to lose them all.

Regards,
Richi

boot with a live cd and check that your ubuntu partitions arent gone(use command "sudo fdisk -l"). if ubuntu is still there just fix the grub boot loader, follow the tutorial:
[http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/](http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/)

---

### Post by oldfred on 2013-02-28
It may be better to see exactly what is where. If you are sure you deleted a boot partition, you may be able to recover it with testdisk, but STOP writing to drive as you may be overwriting that data.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

