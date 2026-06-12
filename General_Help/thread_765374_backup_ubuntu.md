---
title: "backup ubuntu"
date: 2008-04-24
forum: General Help
---

### Post by karq on 2008-04-24
I want to format my hdd and after that install the new ubuntu 8.04. But can I  backup my ubuntu 7.10?? I want to backup everything what I have installed and so on.

---

### Post by chrisccoulson on 2008-04-24
Your decision on how to backup your system will depend on how much stuff you want to back up. Before I do an upgrade, I use [**_this_**]("http://ubuntuforums.org/showthread.php?t=35087") method to backup my entire system. I've used it several times (and restored from it several times too), and I've never had any issues.

Using that method, I exclude all virtual filesystems from the backup archive (eg /proc, /dev, /sys, /var/run, /var/lock). Just remember to recreate all these empty folders should you need to restore from your backup. I also don't backup /home this way, as I synchronize /home with an external USB disk regularly. Adding /home to the backup archive would make the archive too large in my case.

Hope that helps

---

### Post by karq on 2008-04-24
So I just make copys of folders in the filesystem and after clean install I just overwrite them?

---

### Post by chrisccoulson on 2008-04-24
The method I was suggesting was to archive your filesystem in to a tar file. Whatever method you choose, you absolutely must maintain file permissions and ownership, else the system won't work properly if you restore from your backup.

Out of interest, why are you formatting your 7.10 system to install 8.04? Why not just upgrade?

---

### Post by louieb on 2008-04-24
Whenever I make a major change such as a distribution upgrade I use Partimage available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and the [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")CD. 

Partimage Is not as flexible as using tar.  PartImage doesn't restore single files like tar can.  It  saves and restores partitions.  

Both are good. Each has it advantages. For me I use partimage because I'm to lazy to dig in:) and understand tar like like I probably should.

---

### Post by karq on 2008-05-02
Thanks a lot for help. Made a clean install and I but my files on another HDD.

---

