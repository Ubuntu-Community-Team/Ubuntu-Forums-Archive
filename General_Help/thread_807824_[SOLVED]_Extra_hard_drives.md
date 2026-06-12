---
title: "[SOLVED] Extra hard drives"
date: 2008-05-26
forum: General Help
---

### Post by AmpersUK on 2008-05-26
I have loaded 8.04 onto my first hard drive. I am not dual-booting with any other operating system.

I want to put some of my data onto my other hard drives.

When I try to copy files over I get an error message. Something along the lines that I don't have permission.

I check the hard drives and find they are owned by "root".

How can I change this so they are owned by my own user name. I am the only user on the computer.

I am using a desktop ASUS with three 500GB hard drives and 2GB of memory.

---

### Post by forestpixie on 2008-05-26
can you post these 

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by AmpersUK on 2008-05-26
> **forestpixie said:**
> can you post these 

```
sudo fdisk -l
cat /etc/fstab
```

I typed these into Terminal and received the following:


[sudo] password for ampers:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb255b255

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x253300d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac0da221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       60045   482303430    5  Extended
/dev/sdc5               2       60045   482303398+  83  Linux
ampers@Andrew:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f9092be-474a-4468-b79f-6f91fba2a152 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=604bb2b5-bc2a-4730-9208-2c50e05816b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
ampers@Andrew:~$    

And then checked, and get the message that I don't have permissions to copy to the other hard disks.

---

### Post by forestpixie on 2008-05-26
You just need to add them to fstab and they will mount at boot. Have to make folders for them to mount in and then edit the fstab file. 

I will call them respectively disc1 and disc2 - you can change these to more suitable names as long as you change them for the folder name and in fstab - they must [COLOR="Red"]match[/COLOR]

```
sudo mkdir /media/[COLOR="#ff0000"]disc1[/COLOR]
sudo mkdir /media/[COLOR="#ff0000"]disc2[/COLOR]
```

Now backup and edit the fstab file

```
sudo cp /etc/fstab /etc/fstab.2605
gksudo gedit /etc/fstab
```

Add these lines to the end of the fstab file

```
/dev/sdb1 /media/[COLOR="#ff0000"]disc1[/COLOR]     ext3    defaults        0       2
/dev/sdc5 /media/[COLOR="Red"]disc2[/COLOR]     ext3    defaults        0       2
```

To check that they mount

```
sudo mount -a
```

If all is ok they will also mount on boot.

It is possible to use UUID, install does that by default, as well - trouble being if anything changes with the partition so does the UUID - but fstab would need changing manually. If you want to use UUID run this command 

```
sudo blkid
```

It will give you a number similar to 
UUID=604bb2b5-bc2a-4730-9208-2c50e05816b8

for each of your partitions - where the lines to add above look like 

/dev/sdc5 /media/disc2     ext3    defaults        0       2

change the line to be 

UUID=longnumberandletterchain /media/disc2     ext3    defaults        0       2

---

### Post by bigbrovar on 2008-05-26
here is how i did mine .. hope it works for u... :) 


Open up a terminal window and run the following command:

[PHP] sudo fdisk -l[/PHP]


this would give u a list of all the drive on ur pc ..
mine looks like this 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb61906e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6528       19457   103860225   83  Linux
/dev/sda2               1        6527    52428096    5  Extended
/dev/sda5               1        6254    50235192   83  Linux
/dev/sda6            6255        6527     2192841   82  Linux swap / Solaris


if u see the drive u wants to mount .. that means u can mount it .. in my case the drive i wanted to mount is /dev/sda1 ...

now once u have seen the drive u want to mount 
u now would have to creat a virtual drive .. this is where ubuntu would mount the drive .. (ubuntu mounts all drives in /media)
so u have to create a virtual drive in /media where ubuntu would mount ur drive ... the name of my virtual drive is Data

so in my case i just did

[PHP]sudo mkdir /media/Data[/PHP]
make sure the name of the virtual drive contains no special character or space .. very important ..

to give the drive writable partition just do this - substituting Data for what ever name u use-
[PHP]
sudo chmod 777 /media/Data[/PHP]

If you want to mount your drive right away, and you don’t care if it’s mounted automatically every time you boot - then in terminal run the following command:
  
[PHP]  sudo mount /dev/sda1 /media/Data[/PHP]


now the sda1 in my case would be mounted in /media/Data
to made it to me automatically mounted each time i reboot .. then u need to add the it to ur fstab 

run this 

[PHP]sudo gedit /etc/fstab[/PHP]

add this to the bottom of file 

/dev/sda1 /media/Data ext3 defaults 0 0

remember  substitute both the name of my hard drive for yours (mine is sda1), and my mount point name for yours. Then save the file.

to make ur drives to me mounted without reboot just do this 

[PHP]sudo mount -a[/PHP]

they u have it 

if u have any problem let me know ..

---

### Post by AmpersUK on 2008-05-26
> **forestpixie said:**
> You just need to add them to fstab and they will mount at boot. Have to make folders for them to mount in and then edit the fstab file. 

I will call them respectively disc1 and disc2 - you can change these to more suitable names as long as you change them for the folder name and in fstab - they must [COLOR=Red]match[/COLOR]

```
sudo mkdir /media/[COLOR=#ff0000]disc1[/COLOR]
sudo mkdir /media/[COLOR=#ff0000]disc2[/COLOR]
```Now backup and edit the fstab file

```
sudo cp /etc/fstab /etc/fstab.2605
gksudo gedit /etc/fstab
```Add these lines to the end of the fstab file

```
/dev/sdb1 /media/[COLOR=#ff0000]disc1[/COLOR]     ext3    defaults        0       2
/dev/sdc5 /media/[COLOR=Red]disc2[/COLOR]     ext3    defaults        0       2
```To check that they mount

```
sudo mount -a
```If all is ok they will also mount on boot.

It is possible to use UUID, install does that by default, as well - trouble being if anything changes with the partition so does the UUID - but fstab would need changing manually. If you want to use UUID run this command 

```
sudo blkid
```It will give you a number similar to 
UUID=604bb2b5-bc2a-4730-9208-2c50e05816b8

for each of your partitions - where the lines to add above look like 

/dev/sdc5 /media/disc2     ext3    defaults        0       2

change the line to be 

UUID=longnumberandletterchain /media/disc2     ext3    defaults        0       2

I tried the first part but got the usual message saying No, and mentioning "backend" whatever that means.

I tried just the first part but got a little bewildered when I got this result:

ampers@Andrew:~$ sudo blkid
[sudo] password for ampers:
/dev/sda1: UUID="4f9092be-474a-4468-b79f-6f91fba2a152" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="604bb2b5-bc2a-4730-9208-2c50e05816b8"
/dev/sdb1: UUID="f22d3681-643d-4208-9379-9844c2308f92" TYPE="ext3"
/dev/sdc5: UUID="5dd6c6de-f4dc-22a6-d02f-00a2e9d50e81" TYPE="ext3"
ampers@Andrew:~$

---

### Post by AmpersUK on 2008-05-26
[quote=bigbrovar;5045657]here is how i did mine .. hope it works for u... :) 


Open up a terminal window and run the following command:

[php] sudo fdisk -l[/php]
this would give u a list of all the drive on ur pc ..
mine looks like this 

Mine looked like the following - it doesn't look like I can see my other two hard drives does it?


[sudo] password for ampers:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb255b255

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x253300d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac0da221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       60045   482303430    5  Extended
/dev/sdc5               2       60045   482303398+  83  Linux
ampers@Andrew:~$

---

### Post by forestpixie on 2008-05-26
> **AmpersUK said:**
> I tried the first part but got the usual message saying No, and mentioning "backend" whatever that means.

I tried just the first part but got a little bewildered when I got this result:

ampers@Andrew:~$ sudo blkid
[sudo] password for ampers:
/dev/sda1: UUID="4f9092be-474a-4468-b79f-6f91fba2a152" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="604bb2b5-bc2a-4730-9208-2c50e05816b8"
/dev/sdb1: UUID="f22d3681-643d-4208-9379-9844c2308f92" TYPE="ext3"
/dev/sdc5: UUID="5dd6c6de-f4dc-22a6-d02f-00a2e9d50e81" TYPE="ext3"
ampers@Andrew:~$

Hi - you need to post the error messages you get so we can see them please, yea can be bewildering I know :)

You can use the UUID's instead of /dev/sdb1 or sdc5 when you edit the fstab file.

Are you saying that you get an erro when you try to run the mkdir command?

All 3 of your drives are there - the way it works inlinux is

sda - drive1
sdb - drive2
sdc - drive3

then add numbers for the partitions on each drive

sda1 - first partition on first drive

In your case you have extended partitions as well - to confuse you more :)

sdc5 is a partition on your 3rd drive - we are trying to get it to mount fstab with this line

/dev/sdc5 /media/disc2     ext3    defaults        0       2

Clear as mud I'm sure.

Lets get the work done and then we can look at what we've done and try to get a bit of understanding - got all day and most of the night :D


Edit - you are running these commands ina terminal aren't you?

---

### Post by bigbrovar on 2008-05-26
> **AmpersUK said:**
> [quote=bigbrovar;5045657]here is how i did mine .. hope it works for u... :) 


Open up a terminal window and run the following command:

[php] sudo fdisk -l[/php]
this would give u a list of all the drive on ur pc ..
mine looks like this 

Mine looked like the following - it doesn't look like I can see my other two hard drives does it?


[sudo] password for ampers:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb255b255

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x253300d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac0da221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       60045   482303430    5  Extended
/dev/sdc5               2       60045   482303398+  83  Linux
ampers@Andrew:~$


u see am quite new to linux myself but from the little i know ... Ur system seem to have seen the 3 other drives .. u just dont know it ..

u need to know that 

In windows disk drives are assigned an alphabet letter, and traditionally - floppy disk drives were a: and / or b:, and the main hard drive was c:/. Then the first cdrom or dvdrom was d:/, and any additional drives would be e:, f:, and so on. In linux it’s kind of the same, but in a different format. All hard drives installed are listed in the ‘device’ or /dev directory. All drives start with the appendage “sd” i (think for storage drive)

So, if you have 2 hard drives and one cdrom - then you have 3 devices. You have a sda, sdb, and sdc. The number of partitions comes next. If your main hard drive is linux - and you have 3 partitions, then you’ll have a sda1, sd2, and sd5. The partition numbers aren’t in a logical order - sda5 is always the swap partition.

from what i can see 

u have 

Disk /dev/**sda**: 500.1 GB, 500107862016 bytes --your first drive

Disk /dev/**sdb**: 500.1 GB, 500107862016 bytes -- your second drive

Disk /dev/**sdc**: 500.1 GB, 500107862016 bytes  --your third drive

---

### Post by AmpersUK on 2008-05-26
[quote=forestpixie;5045833]Hi - you need to post the error messages you get so we can see them please, yea can be bewildering I know :)

OK, since rebooting for a second time, I can see the hard drive icons on my desktop.

When I tried copying a small file to one of them, I get the following error message.

**Error opening file '/media/disc1/JMorris852.pdf': Permission denied**

So it seems I can now see the drives, but they are listed in the "Permissions" tab, under "Properties" when I right click the ocons on the desktop as...

**The permissions of "disk 1" could not be determined.**
[I]
and[/I]

**The permissions of "disk 2" could not be determined.**

So something so far seems to have happened so we are probably half way there?

---

### Post by geo909 on 2008-05-26
There is a tool with a graphical interface called
PYSDM (PYthon Storage Device Manager).

PYSDM let's you configure the way your harddrives are handled by your system by just clicking boxes. It actually writes lines in fstab so it is good if you don't want to mess up with configuration files.

You can find it in synaptic.
After the installation you will find it under "system" menu, but I'm not sure.

Hope that helps

---

### Post by forestpixie on 2008-05-26
Might help indeed - I get confused with permissions at the best of times, I have the same 'can't be determined' if I look in nautilus - but I have access to all my drives.

Back a bit later

---

### Post by AmpersUK on 2008-05-26
> **geo909 said:**
> There is a tool with a graphical interface called
PYSDM (PYthon Storage Device Manager).

PYSDM let's you configure the way your harddrives are handled by your system by just clicking boxes. It actually writes lines in fstab so it is good if you don't want to mess up with configuration files.

You can find it in synaptic.
After the installation you will find it under "system" menu, but I'm not sure.

Hope that helps

No, alas.

I downloaded it and rebooted. Then found it (called:"Storage Device Manager" under System/Administration.

However, after putting in my password, it opens up, the main screen is all greyed out and cannot be used in any way.

---

### Post by bigbrovar on 2008-05-26
ok let me give u a trick i used 

run gksu nautilus 

then go to /media .... now right click on each drive and set ownership to ur username  set the read and write permissions ... u can look at how i did mine for a guide 

   
[IMG]http://farm3.static.flickr.com/2394/2523825147_b46a21701f_o_d.jpg[/IMG]

---

### Post by AmpersUK on 2008-05-26
[COLOR=Magenta]**Purrrfect!!!**[/COLOR]

Thank you so much for that. A great solution.

Now all works perfectly. (used to prove I can spell perfect) :-)

---

### Post by forestpixie on 2008-05-26
Can we just check two things - do these 2 from a terminal please

```
ls /media
cat /etc/fstab
```

If you are sure that the names are the same in both /media and fstab don't bother and run the command bigbrovar gave for each

```
sudo chmod 777 /media/###*
```

replace ###* with real name of folders in /media

Edit - great - can you mark thread solved please :)

---

### Post by AmpersUK on 2008-05-26
> **forestpixie said:**
> Can we just check two things - do these 2 from a terminal please

```
ls /media
cat /etc/fstab
```If you are sure that the names are the same in both /media and fstab don't bother and run the command bigbrovar gave for each

```
sudo chmod 777 /media/###*
```replace ###* with real name of folders in /media

Edit - great - can you mark thread solved please :)

Thanks for your help but I guess my last message crossed with your in the post.

As it now works, I guess I had entered the earlier commands as you gave, correctly.

Thanks for your help. Much appreciated.

---

