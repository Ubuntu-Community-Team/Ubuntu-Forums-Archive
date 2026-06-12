---
title: "Noob to Ubuntu and still trying to figure out the basics...."
date: 2008-04-18
forum: General Help
---

### Post by slicemaster on 2008-04-18
Noob to Ubuntu and still trying to figure out the basics....

well, I have been using windows for many years and have recently become interested in Linux. my experience in windows computing is extensive and I figured I could handle configuring Ubuntu. and boy was I humbled quickly. even though windows is a cruddy piece of software, it still makes usability easy and it is a no brainier to use so to speak. I am sure that I will get used to Ubuntu but It is just simply difficult to get a hang of all the terminology and what not, either way I am pleased with my experience so fare and I hope I will be competent in no time. either way, I need some help....
two problems...

first, I have a networking problem, I am running several PCs in the house and all of them are configured with windows XP professional. there are no connectivity problem between them, and since I set up samba on my Ubuntu box, there are no problems with me being able to access them....all except for one. it is wearied but for some reason I can not access one of the computers shared resources. Ubuntu gives me this error.... “folder contents could not be displayed. sorry could not display all the contents of...” so on so forth, but what ticks me off is it is a problem with only this computer, I can access the rest of them fine, I double click them from the network explorer and it prompts me for the login info, and bingo, but that one computer doesn't even prompt for login information...i have looked around the forms and their doesn't seem to be a standard answer of how to fix the problem.

second, I have a data drive that is a partition on my HDD that is formated in fat 32 so that is is accessible in both windows and in Ubuntu Linux, however it doesn't seem to mount or at least I don't have any proof that it does such as the drive showing up in “computer”, I only see my CD-ROMs and the file system. thats it. any ideas on how to fix it, once again I have read in the forms and have not come across a standard answer...


thanks,
Slice

---

### Post by kpkeerthi on 2008-04-18
Can you post the output of 
```

sudo fdisk -l

```

This should list all the partitions available in the system. Your FAT32 may need to be mounted manually.

(Sorry I cannot help with the samba thing)

---

### Post by Jarramundi on 2008-04-18
have you tried looking in /media for your data drive?  You need to mount these yourself but there is an automount app available in the synaptic package manager which works well. Other than that, I had a problem mounting a drive because of an unclean unmount when I took the drive out of a windows machine, and I had to find code to fix the problem.

---

### Post by slicemaster on 2008-04-18
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000acd86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        8511    48829567+   b  W95 FAT32
/dev/sda3            8512        9729     9783585   82  Linux swap / Solaris
referrals@referrals-desktop:~$

---

### Post by slicemaster on 2008-04-18
> **Jarramundi said:**
> have you tried looking in /media for your data drive?  You need to mount these yourself but there is an automount app available in the synaptic package manager which works well. Other than that, I had a problem mounting a drive because of an unclean unmount when I took the drive out of a windows machine, and I had to find code to fix the problem.

yes, and no it isnt their....i am sure ubuntu is not mounting the drive automaticaly....

---

### Post by slicemaster on 2008-04-18
this is wierd....i just dismounted the data drive that is fat32.....i had tried mounting it manualy....restarted and now it mounted automaticaly....cool, not sure why it just chose to start working but hay....if it works....still no luck with the samba thing

---

### Post by edward4130 on 2008-04-18
On the first issue, possible items to look into:
is the xp share a WINS server?
is the xp host FAT32 formatted?

Sometimes these quirks can work around by pushing data instead of pulling to get you by till resolved.  I am not a windows guy and have not used it for anything in 5 years and barely used it in over 15, so I hope i at least got you thinking in the right direction, if it works on other xp shares it is that xp share.

On the second.

You need to set the mountpoint for the shared partition. You will do this in the fstab file it is at "/etc/fstab"  whatever your partition is like hda4 you can have it mount hda4 as a drive on the desktop or even as a directory under a program I have 2 500GB drives under my mythtv directory for video file when you look at the filesystem it looks like I have a terrabyte in the top directory.  Mine is below but yours will be different because of IDE drives instead of SATA and of course your need will be different.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6312c605-9e7a-4838-9c37-8a9598cdfe36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=a152c23b-22ac-471f-a895-47683186bef0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0
/dev/sdc1       /var/lib/mythtv/recordings ext3    defaults        0       2
/dev/sda1       /var/lib/mythtv/videos ext3    defaults        0       2




```

Others may chime in soon but how fstab works you can do some really cool things.
to get your partition info if you dont already know this use "gparted" to get it.

---

### Post by edward4130 on 2008-04-18
Great!

good that it is automounting, but if you want your shared partition to be under your user.  Like "/home/username/documents" on the Ubuntu then use the fstab stuff.  I have heard of people doing it and teh same kinda thing on the Windoze side so whatever OS they are on the files are in the same place ready to go :)

---

### Post by slicemaster on 2008-04-18
> **edward4130 said:**
> Great!

good that it is automounting, but if you want your shared partition to be under your user.  Like "/home/username/documents" on the Ubuntu then use the fstab stuff.  I have heard of people doing it and teh same kinda thing on the Windoze side so whatever OS they are on the files are in the same place ready to go :)

thanks for the advice... the more i use ubuntu the more i understand the lingo assocated with it so i am happy using it... also note i found a work around for accessing that windows share that would not open up in the network manager.... i just selected, places conect to server, and then told it it was a windows share, input the ip address, no need for name resolution, and bam, it worked....probibly a issue with windows and its wins....windows network name resolution is a mess and has been since it was invented, too easy to get fragmented networks. anyways thanks, and if anyone has these same problems as i did i hope they see this post.

peace guys and thanks for the REALLY quick responces...

---

### Post by slicemaster on 2008-04-18
well, i can atleast open the drive and mount it but i cant get it to mount the fat partition on boot.... please help here is my fstab....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=af8e7351-6d66-429e-9275-4621997875b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=2206-4E72  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=124cbe79-8aff-44f8-b611-fb4e7e82e9cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

here is my fdisk -l

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=af8e7351-6d66-429e-9275-4621997875b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=2206-4E72  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=124cbe79-8aff-44f8-b611-fb4e7e82e9cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

i want sda2 to be mounted permintly with the mount point of data
thanks

---

### Post by slicemaster on 2008-04-18
ok, sorry for all the questions but i was able to resolve all the problems i was having with the disk mounting with a cool program called....storage device manager....really cool app so you dont have to use command line to fix these types of issues. why isnt this included with ubuntu? this seems like a important thing to have if you dont want to dink around in the termanal all day.

peace.

lovin it so far, just trying to get over that learning curve...

---

