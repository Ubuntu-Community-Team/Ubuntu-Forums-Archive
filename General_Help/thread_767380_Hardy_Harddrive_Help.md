---
title: "Hardy Harddrive Help"
date: 2008-04-25
forum: General Help
---

### Post by amoore on 2008-04-25
I'm trying to add a second harddrive to my fresh installation of Hardy but I just can seem to get it to mount. This is what I'm doing. hopfuly some one can point out what I'm doing wrong.

My /ect/fstab looks like the following  

```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=47b418a8-d103-4c75-ac3b-9bcebb670e5e /               ext3    relatime,erro$
# /dev/sda5
UUID=0fdb8fd3-e093-4429-8fc2-7a33cc7cd74f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

``` 

When I append:[HTML] /dev/sdb1       /media/200GBHD   ext3 defaults 0 0[/HTML]

I then add this to my fstab config as shown below:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=47b418a8-d103-4c75-ac3b-9bcebb670e5e /               ext3    relatime,erro$
# /dev/sda5
UUID=0fdb8fd3-e093-4429-8fc2-7a33cc7cd74f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/200GBHD   ext3 defaults 0 0

```

and 

```
sudo mkdir /media/200GBHD
```
```

sudo chmod 777 /media/200GBHD
```


but I can get the drive to mount!:confused:

gparted shows the drive as sdb. 

Can anyone help me?

---

### Post by SnakeHips on 2008-04-25
in terminal

```
sudo mount -a
```

then from your file manager GUI see if you can browse /media/200GBHD ,if so a reboot should then automount it.

---

### Post by amoore on 2008-04-25
I get:

```
amoore@amoore-desktop:~$ sudo mount -a
[sudo] password for amoore: 
mount: special device /dev/sdb1 does not exist
amoore@amoore-desktop:~$ 

```

and rebooting doesn't help either.

Attached is a screen capture of gparted

However, if I boot using an old Xubuntu CD I can see the harddrive just fine.

---

### Post by dondad on 2008-04-25
Doesn't it need a uuid in fstab?

---

### Post by Ornette on 2008-04-25
I have a similar problem. After upgrading to Hardy, one of my hard drives is not detected. I've checked /dev (and /dev/disck/by-uuid , etc.) but it only shows the other hard drives. Of course BIOS detects it correctly.

I don't know if it has something to do with this line in dmesg:

```
[   44.012542] ata1.01: model number mismatch 'S&#65533;M&#65533;U&#65533;G&#65533;S&#65533;1&#65533;0&#65533;N&#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533;' != 'SAMSUNG SP1604N'
```

That SAMSUNG is the undetected hard drive.

Besides this I've had trouble with the other drives since the id's of the drives and partitions have changed. But I solved that tweaking fstab.

Does anyone knows how to get that other drive working?

---

### Post by amoore on 2008-04-25
I have a maxtor drive, wish I could get it to work.

---

### Post by Savel on 2008-04-25
I have the same problem with a 320GB HD Western Digital, and i didn't find a solution, so i went back to gutsy...................................

I hope someone find a solution to that issue.............................

---

### Post by futz on 2008-04-26
> **amoore said:**
> I'm trying to add a second harddrive to my fresh installation of Hardy but I just can seem to get it to mount. This is what I'm doing. hopfuly some one can point out what I'm doing wrong.

My /ect/fstab looks like the following
That looks right. I just finished adding all my partitions to fstab in Hardy and it worked fine.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda1	/media/sda1	ext3	defaults	0	2	
/dev/sda2	/media/sda2	ext3	defaults	0	2	
/dev/sda5	/media/sda5	ext3	defaults	0	2	
/dev/sda6	/media/sda6	ext3	defaults	0	2	
/dev/sda7	/media/sda7	ext3	defaults	0	2	
/dev/sdb1	/media/sdb1	ext3	defaults	0	2	
/dev/sdc1	/media/sdc1	ext3	defaults	0	2	
/dev/sdc2	/media/sdc2	ext3	defaults	0	2	
/dev/sdc3	/media/sdc3	ext3	defaults	0	2	
/dev/sdc4	/media/sdc4	ext3	defaults	0	2	
/dev/sdd1	/media/sdd1	ext3	defaults	0	2	
/dev/sdd2	/media/sdd2	ext3	defaults	0	2	
/dev/sde1	/media/sde1	ext3	defaults	0	2	
/dev/sde2	/media/sde2	ext3	defaults	0	2	

# /dev/sda8
UUID=c479c234-a725-464b-9f86-0b61e4f0313a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=40649613-d006-4ef0-bb73-96f6c09ae138 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
I like my drives named as what they are, rather than a descriptive name. Helps me stay organized.

Anyway, it works exactly the same as every other Linux distro I've ever used.

EDIT: OH! They don't automount! More tinkering required...
EDIT2: Took a reboot to fix that. They automount fine. But now the stupid thing is renaming them to 209.7 GB Media and similar names like that.

---

### Post by futz on 2008-04-27
> **futz said:**
> I like my drives named as what they are, rather than a descriptive name. Helps me stay organized.

Anyway, it works exactly the same as every other Linux distro I've ever used.

EDIT2: Took a reboot to fix that. They automount fine. But now the stupid thing is renaming them to 209.7 GB Media and similar names like that.
OK, it doesn't work exactly the same as it did pre-Hardy. The new Nautilus guts has changed how mounted drives are labeled. It used to use the mount point as a label if your drive wasn't labeled. Now it doesn't and if your drive isn't labeled it would label the drive as "size-in-gigabytes Media", which is USELESS if you, like me, have many large identical-size partitions. They all get named the same thing! :rolleyes:

The cure is to use e2label to label your drives. Here's a typical command line to do it, in this case to my sde1 drive:
```
sudo e2label /dev/sde1 sde1
```
After labeling all drives just reboot and everything is fine again.

---

### Post by amoore on 2008-04-27
I found a different solution than the one listed above by futz

I reinstalled hardy at the startup screen from the cdrom append the boot option.  

```
all_generic_ide
```

Then you can add your drives like you normally do by configuring your fstab config.

hope this helps someone else.

---

### Post by Ornette on 2008-04-27
> **Ornette said:**
> I have a similar problem. After upgrading to Hardy, one of my hard drives is not detected. I've checked /dev (and /dev/disck/by-uuid , etc.) but it only shows the other hard drives. Of course BIOS detects it correctly.

I don't know if it has something to do with this line in dmesg:

```
[   44.012542] ata1.01: model number mismatch 'S&#65533;M&#65533;U&#65533;G&#65533;S&#65533;1&#65533;0&#65533;N&#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533; &#65533;' != 'SAMSUNG SP1604N'
```

That SAMSUNG is the undetected hard drive.

Besides this I've had trouble with the other drives since the id's of the drives and partitions have changed. But I solved that tweaking fstab.

Does anyone knows how to get that other drive working?

I've found a solution to this problem. I did as it says here in the first comment:

[https://bugs.launchpad.net/ubuntu/+bug/106139](https://bugs.launchpad.net/ubuntu/+bug/106139)

Just renaming your initrd-xxxx.bak to initrd-xxxx solved the problem. It looks like kernel update did something wrong.

---

