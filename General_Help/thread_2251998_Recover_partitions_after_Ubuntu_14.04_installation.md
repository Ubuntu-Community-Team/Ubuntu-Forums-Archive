---
title: "Recover partitions after Ubuntu 14.04 installation"
date: 2014-11-08
forum: General Help
---

### Post by SteDolphin on 2014-11-08
Hi there ...

I did a BIG mistake. I had this situation. 1TB Disk with four partitions. 1 Partition ext4 with Ubuntu 12.04 LTS, a second partition SWAP, 3 and 4 ext4 partitions with DATA :cry: :cry: :cry:

I copied all the important data on the two partitions which was meant to be untouched. I started the installation of 14.04, and I was doing some other things ... so when it apperared the menu ... erase the disk, I just did it :cry:

The meaning was to delete just the first partition, but now I have Ubuntu 14.04 working like a charm on one single partitions and clearly all my important data are gone ...

Do you believe is there a way I can get back my data ???

Thanks a lot in advance

Steve

---

### Post by oldfred on 2014-11-08
STOP using system. All activity is overwriting more data. And Linux randomly writes data anywhere in its partition and if the new partition overlaps old data keeps getting overwritten.

Did it reuse an existing swap? If so that will not overwrite data, but if new swap created then even mounting live installer will overwrite any data that was on drive in area where new swap is. Live system uses swap to speed things up and that will definitely overwrite that area.

If existing swap reused you can use live installer and then install testdisk. If new swap better to use parted magic or maybe gparted. I think parted magic has testdisk by default.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk Instructions
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If installing and wanting to keep any partitions, you must use Something Else or manual install. Then you can choose which partition is /, which is /home or other partitions. You cannot mount data partitions directly as part of install, but can add later to fstab.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by SteDolphin on 2014-11-08
Thanks a lot for the answer, but I've got lost ...

so at the moment I have a new partition which is big all the disk and of corse a new swap was created as during the installation Ubuntu install created one partition plus the new swap.

I don't mind screwing up the actual installation, what is important to me right now is just to recover my old data ...

so in this case what would be the corect one ??? Might be testdisk, I have checked but it never mention ext4 partition to be recovered ...

I never had any problem in installing Ubuntu even with multiboot or other but ... sh#t this time I did it just too quick ... :(

Steve

---

### Post by oldfred on 2014-11-08
Testdisk should show older partitions. It even finds where you may have resized a partition and shows it multiple times. But you have to select a set of partitions that does not overlap. If you know sizes or start and end sectors of old partitions you can use some other tools  also.

If testdisk deeper search does not show files, then your only choice is photorec or similar scan tools. I have used photorec. It is a long slow process, requires another drive with enough room for recovered data. And it only recovers files by type with extension not full file name. If photos or mp3, they have internal data to recover a file name. And other files you have to manually rename. I had backup of text files, but photorec found all the deleted  copies I had saved since backup and I had to compare many old copies with backup to try to restore all data. 

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

