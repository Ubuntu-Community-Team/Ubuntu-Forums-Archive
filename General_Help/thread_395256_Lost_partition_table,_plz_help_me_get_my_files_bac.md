---
title: "Lost partition table, plz help me get my files back!!!"
date: 2007-03-27
forum: General Help
---

### Post by geoisonfire on 2007-03-27
This is a long story and the situation is not that easy I guess. But plz, plz help me guys !!!! I have 70% of my important data in my hard disk and I wan them back!!!

I was using Ubuntu 6.10, xp and vista triple boot for the past 2 month and everything was ok. I used grub as the first boot menu, if I wanted to go Ubuntu, I just needed to enter the first selection on that (Can't really remember what that called). If I wanted to go Xp or Vista, I just needed to enter the last selection in grub( xp or longhorn something like that I believe) , then it would change to vista winload menu, which allow to choose xp or vista.
 
So above information was what my system looked like before things went wrong.

4 or 5 days ago, I was interested in installing x86 osx (or hackentash) on my pc. SInce there is not extra space left in my pc, I decided to detect my Ubuntu partition (both swap and ext3 together about 8 G). And I did that, everything worked fine. I only had winload menu after booting after that which allow me to choice xp or vista.

So then I went to xp created a new 8G ntfs and set is as primary partition ready to try installing x86 osx on that.(most people on the internet said you have to create a new primary partition in order to install osx, that why I did that). However, some also said you would also need to set this new  primary partition as active when booting up. (Now I realized that this is a big big mistake!!! but it's too late...)
So, instead of set c:/ as active partition by default, I change it to that new primary partition.

After that, I reboot,and boot from osx x86 cd, it stuck at the gray screen with apple logo. Obviously, something was wrong, I went to boot back to xp or vista by changing the active partition again. 

But again, I didn't know how at the time (I know it now, but again it's too late...)  and made a big big stupid mistake!!!!!
I boot from xp install disc, and trying to reinstall xp, when it ask me which partition to install xp, (normally I would select c:/ since that's where I used to have xp window system on) , I choice to detect that 8G partition that I created before, then it pop up something which probably warning   
me this is a primary partition , couldn't remember) , I click yes, and went back to partition table, 

all my previous partition was gone!!!
omg, I stop the next step, (didn't format my hard disk), but now I can't boot to xp or vista  anymore and my Partition table is gone. btw, since I  detected Ubuntu, all I can do is using live cd.

Here's what it looked like after I used sudo gpart /dev/hda


```
[COLOR="Blue"]ubuntu@ubuntu:~$ sudo gpart /dev/hda

** Error: invalid extended ptbl found at sector(53657100).

Begin scan...
Possible partition(Windows NT/W2K FS), size(18002mb), offset(0mb)
Possible extended partition at offset(18002mb)
Possible partition(Windows NT/W2K FS), size(8197mb), offset(18002mb)
Possible partition(Windows NT/W2K FS), size(21799mb), offset(26199mb)
Possible partition(Windows NT/W2K FS), size(10001mb), offset(47998mb)
Possible partition(Windows NT/W2K FS), size(18308mb), offset(58000mb)
End scan.

Checking partitions...

* Warning: more than one extended partition: 2.
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): invalid
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): invalid
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary
Ok.

Guessed primary partition table:
Primary partition(1)
type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
size: 18002mb #s(36869104) s(63-36869166)
chs: (0/1/1)-(1023/254/63)d (0/1/1)-(2294/254/55)r

Primary partition(2)
type: 015(0x0F)(Extended DOS, LBA)
size: 29996mb #s(61432560) s(36869175-98301734)
chs: (1023/254/63)-(1023/254/63)d (2295/0/1)-(6118/254/63)r

Primary partition(3)
type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
size: 18308mb #s(37495640) s(118784673-156280312)
chs: (1023/254/63)-(1023/254/63)d (7394/1/1)-(9727/254/56)r

Primary partition(4)
type: 000(0x00)(unused)
size: 0mb #s(0) s(0-0)
chs: (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r[/COLOR]
```



My actual partition table using sudo fdisk -l /dev/hda

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2295    18433024    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            3341        9728    51311610    f  W95 Ext'd (LBA)
/dev/hda3          207176        8283   549881402+  ff  BBT
Partition 3 does not end on cylinder boundary.
/dev/hda5            3341        6119    22322286    7  HPFS/NTFS
/dev/hda6          207176        8283   549881402+  ff  BBT
```



What do i need to do now!!!
I had two primary partitions, I want my first one back ( 18G), the second one(8G) is the one I created in order to install x86 osx , however, my partition was gone even before I get chance to try that.
I have really important files in my logical partitions, What do i need to do now!

I am almost crying now, plz help me to get my partition table back, as well as all my files. thx

---

### Post by jenhsun on 2007-03-27
I think the most important thing is you data, data and data.

I used to have such nightmare. I am not sure the data recovery in Linux since your data might under windows system. 
In addition, to create a new partition table will not lose any data? I doubt of it.
Anyway, here is a good software for you.
[http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)

You can get that from some p2p network, good to have a try.

---

### Post by geoisonfire on 2007-03-28
You are right. My data!!!
I actually i used to backup all my important data into usb disc. However, few days ago, I moved some of these data out to my computer in order to leave more space for my usb. (I use these space to move some of my new data into another pc.) So i did back up my new data, but left old important data in my computer. Who knows my computer just went wrong in the next day...

---

### Post by Ocxic on 2007-03-28
if you use fdisk tor recreat your EXACCT partiton table, the you will restore the drive, to all it's glory, then i suggrsdt backing up and reformating

---

### Post by geoisonfire on 2007-03-28
That's what I believe as well. However, I am not sure how to make the partition table back like it used to be. This is my first time on doing such thing! So I would hope if someone can really help me doing this. At least teach the correct method. thx people

---

### Post by Ocxic on 2007-03-30
test diskuse testdisk  its a program in the repositories from a live cd, if you can't boot, then using the listing of the partitons it find re-create your partition table using fdisk.

---

### Post by geoisonfire on 2007-04-01
Thx a lot Ocxic, I find all my lost partitions back using fdisk, then reinstalled  xp on c:/ , now everything works fine. I got all my data back! :lolflag: :) :)

---

