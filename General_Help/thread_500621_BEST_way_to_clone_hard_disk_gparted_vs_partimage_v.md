---
title: "BEST way to clone hard disk? gparted vs partimage vs ghost vs mkcdrec vs sysresccd"
date: 2007-07-14
forum: General Help
---

### Post by TDK800 on 2007-07-14
Looking for best way to clone/restore complete harddisks with all installed apps and settings and partitions in 3 ways:

1) when hard disk fails can just switch to another hard disk that contains the cloned image. 

2) when hard disk fails can insert an empty unpartitioned hard disk and boot up restore software from USB clip and clone hard disk image from DVD to the new hard disk and then boot from the hard disk like nothing had happened.

3) when hard disk fails can insert an empty unpartitioned hard disk and boot up from DVD and clone hard disk image from that DVD to the new hard disk and then boot from the hard disk like nothing had happened.

A lot of things have been mentioned in the forums from gparted, sysresccd, partimage, ghost, Mkcdrec, Clonezilla to manual backup scripts. But which is the best?

Some URLs for those who find this thread in future:

Ghost 4 Linux:
[http://pcquest.ciol.com/content/linux/2005/105041202.asp](http://pcquest.ciol.com/content/linux/2005/105041202.asp)

PartImage:
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)

Gparted:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Mkcdrec:
[http://www.improvedsource.com/view.php/Linux-System/18/](http://www.improvedsource.com/view.php/Linux-System/18/)

Sysresccd:
[http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick)

Clonezilla:
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by regomodo on 2007-07-14
i find ghost for linux horrendously slow. I just gave up and did a $sudo cp -a -(?) /media/1/* /media/2

Cant remember the other option. Think it was an f

---

### Post by ~X~ on 2007-07-14
I've just installed ubuntu on a dual boot xp on one drive ubuntu on another, I have acronis true image installed on xp which allows me to backup and restore ubuntu from within xp

If your running dual boot could be one solution, acronis is fast when creating images


~X~

---

### Post by mdurham on 2007-07-14
I find rsync to a usb drive suits me fine and it's very reliable. It can also update the image with minimal transfer of data.
Cheers, Mike

---

### Post by Absorbed on 2007-07-14
I use partimage. I have two ext3 partitions, one which is my root, and the other to save backup information. To backup or restore, I boot from the liveCD, add universe sources, apt-get install partimage, mount the hd I wish to save my backup or which has the saved partimage file on (leaving the actually partition that I am backing up unmounted) and then run partimage. It's straight forward and has worked perfectly thus far.

---

### Post by sefs on 2007-07-14
Partimage is very nice. But i would like to move to something like the below that does not depend on tools but basic OS commands sort of.

Another way may be to use any Live CD that contains a program callked dd_rescue.

I've been trying to figure out how to construct the piping with dd_rescue but have been unsuccessful

What i'd like to see is dd_rescue clone, compress and split the file on the fly with a command something like this

dd_rescue /dev/hda | tar -zcvf | split --bytes=4000m  /dev/sda1/hda.img.gz hda1_split

I have no idea what i am doing above could someone give the correct piping if that is possible?

Then I can save the mbr and extended partition info like so.
save mbr
--------
sudo dd if=/dev/hda of=/dev/sda1/backup-hda.mbr count 1 bs=512

save extended
--------------
sudo sdisk -d /dev/hda > backup-hda.sf


And when its time to restore do the reverse command for dd_rescue
dd_rescue /dev/sda1/ cat hda1_split* > /dev/sda1/hda.img.gz | tar -zxvf  (again this is totally incorrect need some guru to give correct piping command to join file parts, uncompress and restore with dd_rescue)

and then restore the mbr and extended....

restore mbr
-----------
sudo dd if=/dev/sda1/backup-hda.mbr of=/dev/hda

restore extended
-----------------
sudo sdisk /dev/hda < backup-hda.sf


I suspect a method like this can work across operating systems with just thee basic commands and tools.

---

