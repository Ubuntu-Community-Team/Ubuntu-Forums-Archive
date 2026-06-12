---
title: "how can i add space from one drive to another"
date: 2006-11-24
forum: General Help
---

### Post by eilker1917 on 2006-11-24
i have 80 gb hard disk,

c: (hda1) 30 gb // windows xp/fat32
d: (hda5) 26 gb// windows xp/fat32
e  (hda7) 19 gb// kubuntu 6.06 /ext3

i wanna take 15 gb from hda1 or hda5 (i can provide 15 gb free in d ,by cut and paste to c). i wanna make hda7  34 gb. how can i do this in a safe way? 
is partition magic solution ? or what do u suggest me ? i am scare of grub error and mbr thing.i have installed lamp server to my kubuntu 6.06, it already is web and ftp server. i dont wanna lose those by stupid mistakes, as you see below i dont have space in hda7(kubuntu) and i am gonna install vmware to check other distro's.

help please...





file system                    Boy   Dolu free   Kull% Ba&#287;lan&#305;lan yer
/dev/hda7                      19G   18G  352M  99% /
varrun                         248M   96K  248M   1% /var/run
varlock                        248M  4,0K  248M   1% /var/lock
udev                           248M  128K  248M   1% /dev
devshm                         248M     0  248M   0% /dev/shm
lrm                            248M   20M  229M   8% /lib/modules/2.6.15-23-386/volatile
/dev/hda1                       30G   13G   17G  43% /media/hda1
/dev/hda5                       26G   21G  5,1G  81% /media/hda5

---

### Post by tenjin on 2006-11-24
Hi,

I'm sure there are people who can give a more detailed answer but this is what I would do.

Option 1

Repartition and literally move space around. Not sure what is the best tool to use for this.

Option 2

Find a folder structure on "/" that is a) big and b) easy to move (e.g. won't cause the machine to crash, so choose something static) and then:

i. Create a new folder on your second drive.
ii. Move the contents of your chosen folder to the new folder on the new drive.
iii. Make a sym link (ln -s <target> <link name>) from the old position to the new one.

For example:

If you want to move this folder:

/home/bob/mp3

- to /dev/hdb1

i. mount /dev/hdb1 /mnt/drive2

ii. mkdir /mnt/drive2/home
mkdir /mnt/drive2/home/bob

iii. mv /home/bob/mp3 /mnt/drive2/home/bob

iv. ln -s /mnt/drive2/home/bob/mp3 /home/bob/mp3

(Check the synatax - I'm writing this from memory on a Windows box!)

Your mp3s are now on your second drive, but look to all intents and purposes like they are still on your "/" partition. So, you get more space on "/" without partitioning.

Cheers

D.

---

### Post by tenjin on 2006-11-24
Hi,

I missed a key bit from your post I fear...

Use partition magic to shrink one of your Windows XP partitions. Then create a new ext3 partition in its place. Then follow my instructions as above.

Cheers

D.

---

### Post by CatKiller on 2006-11-24
There have been reports that Partition Magic doesn't like ext3 that much. I've not used it, so I couldn't say. Use the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") instead.

You'll need to shrink your hda1, then move/grow your hda2, hda5, hda6 and hda7 partitions.

---

### Post by tenjin on 2006-11-24
Hi,

Partition Magic is fine, but you will need a later version (7+ I think).

Cheers

D.

---

### Post by andyrobo60 on 2006-11-24
Is GParted any good at resizing ntfs partitions??

---

### Post by jimbob on 2006-11-24
Yes , Gparted will handle NTFS partitions quite well ...

---

