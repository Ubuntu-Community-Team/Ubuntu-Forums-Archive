---
title: "Urgent help with partitioning my Hard drive"
date: 2013-06-22
forum: General Help
---

### Post by CyBeR pHeOnIx on 2013-06-22
[[IMG]http://s23.postimg.org/jjgeaug93/Screenshot.jpg[/IMG]]("http://postimg.org/image/jjgeaug93/")

The above link shows a Screenshot of my partitions. I am currently using Linux Mint 13. I want to install ubuntu now. So i need a partition with a size of 230 GB. How must i partition this ? When i right-click on dev/sda1 the resize option is disabled.          :confused:

---

### Post by oldfred on 2013-06-22
You cannot use gparted or other Linux partition tools on mounted partitions. So you have to use liveDVD or flash drive. Even then liveCD like to mount swap and may need you to click on swap and right click swap off.

Are you adding Ubuntu or replacing your current install? You can use current swap even if dual booting as long as you are not hibernating or encrypting one or the other.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If dual booting with your current install which is not Windows you should use a ext4 partition as the shared data partition, only if Windows would NTFS be better for data.

---

