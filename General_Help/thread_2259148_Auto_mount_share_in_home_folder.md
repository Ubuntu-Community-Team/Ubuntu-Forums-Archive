---
title: "Auto mount share in home folder"
date: 2015-01-02
forum: General Help
---

### Post by dagring on 2015-01-02
Hi,

I have to disk on my Ubuntu 14.04 system. One for the home folder and OS. The other is for personal files. I have tried to mount a share in mye home folder, and it goes well when I do:

 sudo mount --bind /media/dag/25019a70-1441-46dc-af5a-822545927f78/Videoklipp /home/dag/Videoklipp

The share is mounted and I can access it like another share in my home folder, but when I put this in /etc/fstab (/media/dag/25019a70-1441-46dc-af5a-822545927f78/Videoklipp /home/dag/Videoklipp none defaults,bind 0 0), my system will not reboot properly.

I have tried to figure out what i'm doing wrong. Can anybody give me a hint?

Dag R

---

### Post by Impavidus on 2015-01-02
The partition only gets mounted at /media/dag/25019a70-1441-46dc-af5a-822545927f78 when you click it in the file manager. During boot it's not mounted yet, so the bind mount in fstab fails.

---

### Post by hal8000b on 2015-01-02
Try mounting with bind and UUID and just partition number.
To find the partition number run

sudo fdisk -l

You can then mount manually with:

sudo mount /media/dag/sdax  /home/dag/Videoklipp

(replace sdax with correct partition number)

If all goes well append a line like

/media/dag/sdax  /home/dag/Videoklipp ext3  defaults 0 2

The man page of fstab will give you explanation of options, just make sure
sdax is correct partition and ext3 reflects current filesystem type.
If ever you add, change or modify partitions, the partition number could
change so bear this in mind.

---

### Post by dagring on 2015-01-03
It's maybe easer to make a symbolic link? With your idea I get the whole partition (sdax) in /home/dag/Videoklipp?

---

### Post by Morbius1 on 2015-01-03
A symbolic link will not work either if [COLOR=#0000cd] 		[/COLOR][COLOR=#0000cd]Impavidus[/COLOR] is right. Why not post the output of this command so people here don't have to guess:
```
cat /etc/fstab
```

---

### Post by dagring on 2015-01-03
Here it is, I have commented out the line I was troubling with:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=131c68b1-b398-4bea-b639-ff507cb00ad3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=202620b4-7f2f-432b-b8b9-c1d1f309e984 none            swap    sw              0       0
#/home/users    /export/users   none    bind  0  0
#/media/dag/25019a70-1441-46dc-af5a-822545927f78/Videoklipp /home/dag/Videoklipp none defaults,bind 0 0

---

### Post by Morbius1 on 2015-01-03
Then **[COLOR=#0000cd]Impavidus [/COLOR]**[COLOR=#000000]was correct in his observation.You don't have the partition you are binding to mounted first.

After the swap line have the partition mounted at boot. If it's an ext4 partition:
[/COLOR]```
UUID=25019a70-1441-46dc-af5a-822545927f78 /media/Storage ext4 defaults,noatime 0 2
```
Then follow that with a bind from the subfolder to your home subfolder:
```
/media/Storage/Videoklipp /home/dag/Videoklipp auto bind 0 0
```
And create the /media/Storage mount point:
```
sudo mkdir /media/Storage
```

Unmount the partition if you currently have it mounted:
```
sudo umount /media/dag/25019a70-1441-46dc-af5a-822545927f78
```
[COLOR=#000000] Then remount it and the bind with this command:[/COLOR][COLOR=#0000cd]
[/COLOR][COLOR=#000000] ```
sudo mount -a
```[/COLOR][COLOR=#0000cd]

[/COLOR]

---

### Post by dagring on 2015-01-06
It works now. I ran the mount -a and rebooted afterwards to see if it accepted the lines I have added in /etc/fstab. Thanx a lot for your directions!

Dag R

---

