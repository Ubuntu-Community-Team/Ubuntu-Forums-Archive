---
title: "Partitioning Recomendations"
date: 2015-02-08
forum: General Help
---

### Post by cassialeilani on 2015-02-08
I plan to dual-boot Windows 8 and Ubuntu on my HP 15 500GB memory notebook. How much partition space would one recommend for the Windows OS partition, Ubuntu OS partition, shared space, and swap? I don't require a lot of space in the shared space because I keep the majority of my data on an external hard-drive.

---

### Post by v3.xx on 2015-02-08
Swap should equal the amount of ram you have.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+much+swap&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+much+swap&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2015-02-08
Windows tends to need lots of extra space, but even Ubuntu should have some.

Windows system partition often is 30 to 50GB, but if installing games or other larger apps may need more.
Ubuntu can easily be 20 or 25GB, if you have separate /home or store most data in /mnt/data Linux partition or a shared NTFS data partition. But if not automatically moving data to other partitions /home inside / (root) can grow a lot, depending on your data.

Variety of suggestions:
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by cassialeilani on 2015-02-09
Thank you for your answers.

---

### Post by ptn107 on 2015-02-09
I only play some games with Windows 8.1 so I only made it 100 GB.  Windows alone takes about ~20-35 GB.  Luckily you can resize the Windows partition later pretty easily if you made it too small.

My root '/' linux partition is only 12GB.  I have never had any linux distro take even 50% of that and I have a crap ton of software installed for work and school.  My swap is equal to my RAM (4 GB), but 2 GB for swap is enough.  If you even use that much swap that's a sign you need more actual RAM.  My home '/home' folder takes up the rest since everything else is stored there.

---

