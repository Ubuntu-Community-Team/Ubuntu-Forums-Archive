---
title: "Sansa Fuze needs formatting"
date: 2013-08-06
forum: General Help
---

### Post by Orsb on 2013-08-06
Hi there,

I have a Sansa Fuze 2 GB v1 mp3 player which acts in an odd way, eg. I can delete files but when I unplug the device and it restarts all files are back. I have tried reset to factory settings, format, check the connection mode, but nothing helps.

Therefore, I have figured, that the best would be to format the whole thing. I have found some material online, but i got stuck at a rather early stage. Here is what I have done so far:

In terminal I typed: sudo fdisk -l

and it gave me the following information:
It does not appear to be a partition table

and it showed that I have four devices listed with the following entry in System
/dev/sdb1 Unknown
/dev/sdb2 Novell Netware 386
/dev/sdb3 Unknown
/dev/sdb4 Unknown

Any help on how to move forward would be greatly appreciated.

---

### Post by Jonor on 2013-08-06
You could have a look at the [Fuze forums]("http://forums.sandisk.com/t5/Sansa-Fuze/bd-p/fuze").
I have a similar player, the clip+ which is fantastic, but does have some slow/buggy software. However, using Linux, that is nothing very shocking.
Failed deletion is the main issue here too, here are some things that should help get the job done.
To delete music  :
1. Move the entire MUSIC folder to Trash, give the player plenty of time to do this, mine is slow.
2. Delete MUSIC from Trash, best not rush this either.
3. Make a new MUSIC folder and copy/paste in the new material.

This succeeds 99 times out of 100. One time it did not i too reformatted, using gnome-disk-utility, risking the entire player, 
but i think Sansa put all the essential files in protected ROM so no harm was done. 
After that MUSIC appeared empty but when pasting in new files, one banner appeared requesting permission to replace one odd file, but that was the only failing.

---

### Post by Orsb on 2013-08-19
Hi Jonor,

Thanks for you reply. Unfortunately, I was unable to delete the files as it seems that the system is read-only. Even if I delete the files by connecting the device to my computer, when the device refreshes its database the files are back.

Thus, I thought that only through formatting can this issue be solved.
The application available in Ubuntu (disk utility and GParted) cannot format it either.

I would need some help to format it through the terminal as I believe that is the only available option remained.

Thanks

---

### Post by tgalati4 on 2013-08-19
I'm not familiar with the Fuze, but some players have a reset button in the battery compartment or a pin hole that wipes the player clean.  Also, is there an internal format menu item in system settings on the device itself?  Using linux tools to format a player is risky because some players have odd partition table layouts.

---

### Post by Jonor on 2013-08-19
Formatting through the terminal is fairly easy and worked on my clip+ today but before showing how it is done i would personally reccommend retrying the in-player format after recharging the battery. Deleting or formatting probably will fail if there is not enough power to do it. Also make sure the USB Mode, found in system settings, is set to MSC.
Make external backups of anything important since if formatting is messed up then all software on the ubuntu box could be lost !

1. Plug the Fuze into a usb on the Ubuntu box. Ubuntu will give the device a couple of different types of code names every time this is done, the one we will be using is a short reuseable name that may change whenever other devices are added or removed. As it could be a disaster to format the wrong thing make sure no other device is added or removed until the process is complete.
2. Put in a  full screen terminal ```
blkid
``` and press enter on the keyboard.

 Identify which line the Fuze is on and take a note of the code name at the very beginning of that line, it might be sdb1 or perhaps sdc1 or something similar.
 Lets imagine it was sdz1, now put into a terminal ```
sudo mkfs.vfat -n 0123-4567 /dev/sdz1
``` and press enter on the keyboard. You will need to supply your password.
If this step is done the fuze will get something called a device label of 0123-4567. I suggest this because that is what my clip+ device label was, but you could change it to some other short name such as myfuze i suppose.

That should be it.

---

### Post by Jonor on 2013-08-20
I forgot to mention two small steps in my above post. 
Before doing ```
sudo mkfs.vfat -n 0123-4567 /dev/sdz1
```

do ```
sudo umount /dev/sdz1
```

but as mentioned before replacing sdz1 with whatever code was at the beginning of the blkid Fuze line.

Then at the very end, after the mkfs.vfat .. formatting step disconnect and then reconnect the Fuze by the usb
so as to mount it again. These two steps take the Fuze out of regular use for servicing and then put it back in regular use.

---

### Post by Orsb on 2013-08-20
Dear Jonor,

Thanks for your help in helping me to sort this out.
I have followed your instructions and encountered the following problems.

blkid
did not actually show my device listed, so I entered

sudo blkid

The device is at:
/dev/sdb

So, I entered:
sudo umount /dev/sdb

and then:
sudo mkfs.vfat -n 0123-4567 /dev/sdb

It gave me the following error message:
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)

So, I entered:
sudo mkfs.vfat -I /dev/sdb

which gave me the following error:
mkfs.vfat: failed whilst writing FAT

Do you have any suggestion on how to proceed?

Thanks

---

### Post by Jonor on 2013-08-20
There is usually a digit after the b of sdb such as sdb1.
I would not risk using the -I overide at this stage, it might bork the player.
Would you copy the output of sudo blkid and paste it into a post for us to see ?
Bear in mind i find Sansa mini usb connections unreliable, you may need to disconnect and reconnect the Fuze a few times to get things working properly.

---

### Post by Orsb on 2013-08-20
Here is the output of sudo blkid:

/dev/sda1: LABEL="RECOVERY" UUID="D6EA131FEA12FB85" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM" UUID="EA4AE9064AE8D07D" TYPE="ntfs" 
/dev/sda3: UUID="324A3EA54A3E662F" TYPE="ntfs" 
/dev/sda5: UUID="83bee22d-607c-4031-ba11-1e384b86a58d" TYPE="ext2" 
/dev/sda6: UUID="56b2a671-4c37-400f-bf61-39505f613edc" TYPE="ext4" 
/dev/sda7: UUID="8b6ad6e0-f69a-4bb9-8ff3-d06f6fb43e57" TYPE="ext4" 
/dev/sda8: UUID="545d7d2e-730d-4e91-9fa8-9fd041225963" TYPE="swap" 
/dev/sdb: SEC_TYPE="msdos" LABEL="SANSA FUZE" UUID="3460-C4BD" TYPE="vfat"

---

### Post by Jonor on 2013-08-20
I don't know why you are not getting a digit after the b of sdb. My player produces one.
If you'd rather not wait for someone more knowledgable to help us out and accept the
risks of loosing the player retry but doing the formatting step with the n and the label in i.e.

sudo blkid (to check what name ubuntu has given the player)
sudo umount /dev/sdz    (but replace the z with  b or whatever)
sudo mkfs.vfat -nI 0123-4567 /dev/sdz

Then unplug and replug the player to mount it again.

If that doesn't work try again with the n and I swapped around.

sudo mkfs.vfat -In 0123-4567 /dev/sdz

Best of luck !

---

### Post by Orsb on 2013-08-20
I used:
sudo mkfs.vfat -In 0123-4567 /dev/sdb

it produced the following error message:
mkfs.vfat: failed whilst writing FAT

In my first post, I put the output of fdisk -l, which does show sdb with 1-4, but seems to be a problem with the partition table.

---

### Post by Jonor on 2013-08-20
Try doing a Restore Factory Settings found in System Settings on the player ?

---

### Post by Jonor on 2013-08-20
A long shot, high risk; putting numbers in anyway !

I.E. 

sudo mkfs.vfat -n 0123-4567 /dev/sdz1

if this does not work then 

sudo mkfs.vfat -n 0123-4567 /dev/sdz2 

through to 

sudo mkfs.vfat -n 0123-4567 /dev/sdz4

There seems little point going beyond 4.

---

### Post by eddie5 on 2013-08-20
I have a sansa clip and that has the format utility built in under settings. I am sure the Fuze has a similar facility.

eddie

---

### Post by Orsb on 2013-08-23
Still no luck, but thanks for the help.

---

