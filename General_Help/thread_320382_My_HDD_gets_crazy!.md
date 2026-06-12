---
title: "My HDD gets crazy!"
date: 2006-12-17
forum: General Help
---

### Post by Azathoth_ on 2006-12-17
Hi, i have a lot of problems with my Ubuntu Edgy about hard disk. I have two HDD which are one Seagate SATA and the other is a Seagate ATA.
A lot of times when i am doing things, like chatting, playing Enemy Territory, using OpenOffice and a lot of times my hard disk gets crazy and i cannot close the session, instead i have two reboot manually my computer.

Can anyone help me? I do not know if any program can make this automatly, to uses a lot of hard disk resources.
If anyone doesn't know... is there any program i can uses to know the hard drive it is using and the program uses all resources?

Thank very much

---

### Post by maxamillion on 2006-12-17
I'm not entirely sure what you mean by HDD getting crazy, but it sounds more like there is a memory leak somewhere and you X session freezes and if that is the case all you need to do is hit ctrl+alt+backspace, it will kill the X session and restart the X server resulting in you sitting infront of a login screen.

Otherwise if you want to control the performance of your hard drive, type "man hdparm" in the terminal and read what it has to say, very educational. :)

---

### Post by Azathoth_ on 2006-12-17
I's because i think one program is using a lot of my hdd resources and then, sometimes i cannot do anything because my hdd is working at 100%
Anyway i have tried to modify hdd configuration using hddparm but no results

---

### Post by bulldog on 2006-12-17
You can try to type  top in your terminal to see what's using your resources.

---

### Post by Azathoth_ on 2006-12-17
> **bulldog said:**
> You can try to type  top in your terminal to see what's using your resources.

Thanks.
Anyway does anyone knows a program that could show which programs are using my hdd %?

---

### Post by bulldog on 2006-12-17
There should be,but I know nothing about them.
However if you run ubuntu and didn't install 'strange applications' your hard disk will only run once and a while for a short period.

If your disk is read without any reason,you have either installed something which is running in the background and you should know of,or the disk is gonna breakdown.
Can you tell us the amount of RAM installed on your computer?
It could be it's swapping all the time.

---

### Post by Azathoth_ on 2006-12-17
Ok, see this images:
[http://www.imagehost.ro/pict//1717132045855e90a0a72.png](http://www.imagehost.ro/pict//1717132045855e90a0a72.png)
[http://www.imagehost.ro/pict//1717142045855ecc129a0.png](http://www.imagehost.ro/pict//1717142045855ecc129a0.png)

Maybe it can be, but i don't know why sometimes i don't do anything it uses too much hdd %.
I have a swap of 1 GB, the double of my RAM

---

### Post by Azathoth_ on 2006-12-17
Can anyone help me?

---

### Post by bulldog on 2006-12-17
You have 512MB RAM installed,it's sufficient but no more as that.
You run quite some apps together,and Beryl.
Do you have some plugins in Beryl which could cause the swapping,because I presume that's what's going on.

Close all the applications and see what happens and close Beryl too and switch to metacity.

It's just a game of eliminating things and put them on again to see when the disk usage   appears so you know what it causes it.

Nobody can do that better as you,you have the computer on your hands :D

---

### Post by chrisccoulson on 2006-12-17
Azathoth_: Your screenshot suggests you don't have an active swap partition, so I'm sure the activity isn't due to swapping. Can you post the contents of /etc/fstab?

---

### Post by Azathoth_ on 2006-12-17
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda6
UUID=75e8bbfc-7a76-43ae-bd41-b28d5acced61 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1
UUID=C86F-B9B9  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0

# /dev/sda3
UUID=859F-F0A6  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0

# /dev/sda4
UUID=42CF-F115  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       0

# /dev/sda5
#UUID=BC0CF6D20CF686A4 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
#/dev/sda5	/media/sda5	ntfs-fuse	auto,gid=1001,umask=0002 0	0
/dev/sda5	/media/sda5	ntfs-3g	defaults,locale=es_ES.utf8   0    0

# /dev/sda7
UUID=bd91af91-145b-4bd7-a297-9ef8318301ce none            swap    sw              0       0

/dev/sdb1  	/media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       0

/dev/sdb5	/media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#/dev/           /media/floppy0  auto    rw,user,noauto  0       0

none            /sys            sysfs   defaults                        0      0


This is my fstab, but i think it might by one of this two possibilities.
I use beryl with some pluggins and i don't know a lot about swap. Can i enable my partition swap if it is not active?

Thanks a lot

---

### Post by chrisccoulson on 2006-12-17
I definately don't see a mounted swap partition. What is the output of fdisk -l?

---

### Post by Azathoth_ on 2006-12-17
I opened gparted and swap was not monted.
I have tried to solve this, but i cannot ddo.
I tried to remake the partition, after "sudo mkswap -c /dev/sda7", after 
"sudo gedit /etc/fstab" and changed to UUID", the next step was "sudo 
swapon -a", and the next step was "sudo 
/etc/initramfs-tools/conf.d/resume" and change the UUID for this new, 
and the last step was "sudo update-initramfs -u"

How can i activate swap?

---

### Post by Azathoth_ on 2006-12-18
How can i activate swap

---

### Post by chrisccoulson on 2006-12-18
Oops, I didn't see the swap partition in your fstab before.

Have you tried replacing the UUID in fstab with /dev/sda7, and then trying sudo swapon -a again?

---

### Post by Azathoth_ on 2006-12-18
When i open gnome-system-monitor, in resources, it appears i use swap, but not a lot, only a 30% so-so of my RAM used.

---

