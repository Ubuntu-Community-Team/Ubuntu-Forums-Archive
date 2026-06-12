---
title: "Duplicate Boot Partition"
date: 2006-07-22
forum: General Help
---

### Post by 6and9.42 on 2006-07-22
Hello,

Ok, linux newbie here, I had win 2k installed and decided to dual-boot with ubuntu. I shrunk the win partition and installed ubuntu on the end of the drive. No problems, everything has worked great except I've now realized I didn't give enough spacea for ubuntu (about 7GB using ext3). I cleaned up the win drive and shrunk it down another 20GB, formated it ext3, and copied the original linux partition to the 20GB partition (using gparted). My plan was to delete the original linux partition and extend the new one so I'd have 27GB.

Question is, first, am I going about this all wrong? And, if not ;) how would I boot into the new partition? Are there any risks I need to watch out for or specific things to check on the new partition before I fully move over and delete the old partition?

Thanks a ton! :)

g.

---

### Post by Herman on 2006-07-23
Presuming you are using GParted LiveCD;
The simplest way is to just copy the partition and paste it so it'll be right behind the Windows partition. It will recieve a new partition number. Then delete your old partition, resize your new partition to take up all the remaining free space, re-install GRUB and edit /etc/fstab. (Because it has a new partition number). That's what you have started to do already.

Otherwise, if you don't want to edit /etc/fstab and re-install GRUB, you'll have to start again and you can;[LIST=1]
[*] copy the partition and paste it in the middle of the free space. It will receive a new partition number.
[*]Then delete the old partition first, making the original partition number vacant and available.
[*]Then copy and paste the copy of the partition to where you really want it, (behind Windows), and it will have its original partition number back again.
[*] Delete the intermediate copy and resize the new partition to fill the remianing free space. Boot your Operating system and continue using it. There is no need to re-install GRUB or edit /etc/fstab this way.[/LIST]Thirdly, you could just wait a few days or a week or so. A new version of [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") is expected very soon, I don't know when, but it will have the ability to move all filesystems.
> Release 0.3 is not that far away and it includes a VERY nice feature: **moving of all filesystems** The above is quoted from [GParted LiveCD News.]("http://gparted.sourceforge.net/news.php")
That will make life a lot easier! 
Regards, Herman :D

---

### Post by aysiu on 2006-07-23
You may want to take a  look at this before you start "copying" partitions: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by 6and9.42 on 2006-07-23
Herman: Great, thanks for the info. I think I'll go with your 2nd plan or just wait for the new gparted (I am indeed using the livecd).

aysiu: Is there any reason to use PartImage over just copying the partitions as I have? I unfortunately can't get internet to work on a livecd due to the network card I have ](*,) thanks again.

g.

---

### Post by aysiu on 2006-07-23
If you don't have internet, forget PartImage. The advantage would be that it copies the partition exactly as it is.

---

