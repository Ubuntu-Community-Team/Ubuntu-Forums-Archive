---
title: "Need help installing Ubuntu 13.04 i386 on a 2 year old netbook."
date: 2013-08-11
forum: General Help
---

### Post by guy3 on 2013-08-11
Hello, I have an issue with installing Ubuntu on a netbook, any help will be appreciated.

Since the netbook was slow with windows 7, I thought that installing Ubuntu alongside on the second partition would help do things faster  (also keeping Win 7 just incase). The problem is, I am not sure how to just -install- it there. I choose "Something Else" in the "Installation type" menu, it shows all my partitions, but from there I am lost. I do not know if I should just click on the partition I wish to be the Ubuntu drive and click "Install Now" or do I have to double click it and choose something from "Use as" list and if I have to, then I have no idea what would something do or how they would affect my pc. I read somewhere that ext4 is unsupported by Windows, but I need to keep all the files on there. Yes, all the files on there have to remain and I have no way getting them elsewhere which I believe causes a problem too.

Thank you.

---

### Post by oldfred on 2013-08-11
Most Windows 7 systems use all  4 primary partitions, so you may have to delete one.

 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


        My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by SweetAurora on 2013-08-11
Putting Ubuntu 13.04 on that thing will make it just as slow. Ubuntu uses the same amount of resources as Win7. I suggest using Xubuntu on that netbook.

---

### Post by 3rdalbum on 2013-08-11
You can only install Ubuntu on a Linux filesystem, not one readable in Windows, unless you format the partition.

You may be able to resize one partition downwards and create an ext4 Linux partition in the new free space, bearing in mind the 4 partition limit in PCs. This is what the "Install Ubuntu side-by-side" option does, if you were offered it in the installer.

If you want to erase that partition you mentioned in your post, click it in the Something Else screen and click Edit Partition. Set the filesystem to ext4 and the mount point to / and you can continue the installation. All data in the partition will be erased.

---

