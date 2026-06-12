---
title: "read write permission fat32"
date: 2007-01-04
forum: General Help
---

### Post by hostage on 2007-01-04
Hello i have some questions here i would like to be answered.

1: If i make a fat32 partition on my hard disk, will i automatic get "read/write" permission to the disk?

2: Can i unpack files bigger then 4gb on a fat32 partition, if not. How can i solve it?

3: Is there any other Partition option i can use instead of "fat32 & ntfs" to get read/write permission and at the same time handle files bigger then 4gb?
____________________________________________________________________________________________________________

Now i use NTFS on my "movie & music" hard discs and i don't have permission to them, i have used "ntfs-3g" to make it work but one of the hard disks disappear. It would be nice if i could unpack files bigger then 4gb!
____________________________________________________________________________________________________________

????

---

### Post by bodhi.zazen on 2007-01-04
Mounting and permissions depends on the file system. Ext3, reiserFS, or any Linux ative file system can give you RW access !

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by hostage on 2007-01-04
Okey :) 

so if i use "Ext3 or reiserFS" then i can handle files bigger then 4gb?

---

### Post by bodhi.zazen on 2007-01-04
According to the wiki:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

ext3 has a file size limit of 16GiB to 2TiB

---

### Post by hostage on 2007-01-04
okey... thank you for the answeres, now i think i can solve the problem :D

---

### Post by hostage on 2007-01-04
Hmm one thing left!

How can i make a ntfs partition to ext3 without loose all data?

I have all the movies and music on a ntfs parition but i want ext3 on it instead of ntfs
without loose all data

---

### Post by bodhi.zazen on 2007-01-04
> **hostage said:**
> Hmm one thing left!

How can i make a ntfs partition to ext3 without loose all data?

I have all the movies and music on a ntfs partition but i want ext3 on it instead of ntfs
without loose all data

You can't.

You will loose all the data if you format the partition.

You will need to move you data to an alternate location (another partition, CD/DVD), format, and move it back.

---

### Post by hostage on 2007-01-04
okey this is my last question.

How do i make a ext3 partition?

---

### Post by bodhi.zazen on 2007-01-04
> **hostage said:**
> okey this is my last question.

How do i make a ext3 partition?

No, no, this is good !

Keep asking questions I know the answer to :p

Unmount the partition before you format it ;)

You can partition with gparted (install gparted with synaptic)

```
sudo aptitude install gparted
```

Gparted is a gui.

From the CLI:```
mkfs.ext3 <device>
``` Where <device> is the partition to format (for example /dev/hda1)

---

### Post by Mena.T.L on 2007-01-04
Great Thanks Friends ... I really Was Confused About This ...
Thanks Again...

Mena
God Bless

---

### Post by Mena.T.L on 2007-01-04
> **bodhi.zazen said:**
> No, no, this is good !

Keep asking questions I know the answer to :p

Unmount the partition before you format it ;)

You can partition with gparted (install gparted with synaptic)

```
sudo aptitude install gparted
```

Gparted is a gui.

From the CLI:```
mkfs.ext3 <device>
``` Where <device> is the partition to format (for example /dev/hda1)

I Do What You Said And Now I Cant Se My partions And I cant Mount Them ....
plz Tell Me the reason AndThe Solution.....


Thanks

Merry Christmass

Mena

---

### Post by Mena.T.L on 2007-01-04
Freinds I need Help Here ....Plz

---

### Post by bodhi.zazen on 2007-01-04
LOL Mena.T.L, could you describe what your are trying to do, what your did, and how we can help :lol:

```
sudo fdisk -l
```will list your partitions.

What partition are you formatting/mounting, what command are you using, and what error message are you getting.

---

### Post by Mena.T.L on 2007-01-04
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406   83  Linux
/dev/hda2            1366        9729    67183830    5  Extended
/dev/hda3            1276        1365      722925   82  Linux swap / Solaris
/dev/hda5            1366        3915    20482843+  83  Linux
/dev/hda6            3916        5827    15358108+  83  Linux
/dev/hda7            5828        8377    20482843+  83  Linux
/dev/hda8            8378        9729    10859908+  83  Linux

Partition table entries are not in disk order


This is message I got...

Thanks

---

### Post by bodhi.zazen on 2007-01-04
Looks good.

What partition are you trying to mount/format ?

---

### Post by Mena.T.L on 2007-01-04
> **bodhi.zazen said:**
> Looks good.

What partition are you trying to mount/format ?

/dev/hda5 1366 3915 20482843+ 83 Linux
/dev/hda6 3916 5827 15358108+ 83 Linux
/dev/hda7 5828 8377 20482843+ 83 Linux
/dev/hda8 8378 9729 10859908+ 83 Linux


These ......

Thanks

---

### Post by bodhi.zazen on 2007-01-04
lets start with /dev/hda5

```
sudo mkdir /media/hda5
sudo mount /dev/hda5 /media/hda5
sudo chmod 777 /media/hda5
```

Any error messages ?

---

### Post by Mena.T.L on 2007-01-04
> **bodhi.zazen said:**
> lets start with /dev/hda5

```
sudo mkdir /media/hda5
sudo mount /dev/hda5 /media/hda5
sudo chmod 777 /media/hda5
```

Any error messages ?



THIS....FROM FIRST 

cannot create directory `/media/hda5': File exists

then i type the secined one it get also an error message 

the third one nothing happened i tried it again but tayped the seconed one and it tell me this 
mount: /dev/hda5 already mounted or /media/hda5 busy
mount: according to mtab, /dev/hda5 is already mounted on /media/hda5

---

### Post by bodhi.zazen on 2007-01-04
Alrighty then :p

/dev/hda5 is successfully mounted at /media/hda5 ;)

Try this:

```
ls -l /media
cd /media/hda5
ls
mkdir test
ls
```

The first ls -l /media will list all your subdirectories and permissions.

With the third ls you should see a new directory "test" listed in /media/hda5 :p

To remove it:```
rm -R /media/hda5/test
```

If you want to format /dev/hda5, unmount it first:```
umount /media/hda5
```Then format away :p

---

### Post by Mena.T.L on 2007-01-04
Thanks My Friend Great Thanks To God And You 

Thanks Again

Mena

---

### Post by bodhi.zazen on 2007-01-04
LOL Mena, you are most welcome :p

---

### Post by Mena.T.L on 2007-01-04
Friend I Do That But there is something ...

I still cant see my partitions......

---

### Post by bodhi.zazen on 2007-01-04
Whatever do you mean ? No desktop icons ? What ?

You should be able to open nautilus and browse to /media and see your partitions...

---

### Post by Mena.T.L on 2007-01-04
[B][COLOR="Blue"]Yes No Desktop Icon ....

and For You should be able to open nautilus and browse to /media and see your partitions...

I cant...

Thanks Again[/COLOR][/B]

---

### Post by bodhi.zazen on 2007-01-04
Interesting. [color=blue]I like the blue by the way[/color] :p

what version (of Ubuntu) are you running?

Try something simple for me, log out and back into gnome.

---

### Post by Mena.T.L on 2007-01-04
I am Using Ubuntu 6.10 Christian Edition .....The Last One 

And I have Already restart The System After Doing That In The first Time ... I am Doing Something Now .... And One More Thing If Log Out And Log In Again The Thing I am doing Will be Working And If I Start It from beginig It Says Another One Is Working ,,,,,,,, What Should I Do To Get It Again From Last Time...


Thanks...

---

### Post by hostage on 2007-01-05
Thanks for all the answeres :P i will try to make a ext3 partiotion when i get RW acess to my hard driver so i can save the data in it. Then i will Format the disk and make a ext3 :D 

cool there is a Christian version of ubuntu? :P

---

### Post by bodhi.zazen on 2007-01-05
> **hostage said:**
> Thanks for all the answeres :P i will try to make a ext3 partiotion when i get RW acess to my hard driver so i can save the data in it. Then i will Format the disk and make a ext3 :D 

cool there is a Christian version of ubuntu? :P

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)

---

