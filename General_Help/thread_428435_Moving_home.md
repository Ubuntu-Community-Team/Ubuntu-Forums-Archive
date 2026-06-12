---
title: "Moving /home"
date: 2007-04-30
forum: General Help
---

### Post by merlinus on 2007-04-30
Is it possible to move /home to a new partition, keeping all of the programs, settings, and preferences, without too much difficulty?

Thanks.

-merlin

---

### Post by Skrynesaver on 2007-04-30
Define too much difficulty ;)
If you have the new ext3 partition made, lets call it [I]hda3
[/I]```

sudo mkdir  /new_home
sudo mount /dev/hda3 /new_home
sudo cp -Rp /home/* /new-home
gksudo gedit/etc/fstab
```
coment out the current home partition with a #
copy the old home partition line, changing the first entry on this line to the UUID returned by
```
sudo vol_id -u /dev/hda3
```
save the file.
```
umount /new_home
```
Hereafter booting should give you the new partition mounted on /home

---

### Post by sefs on 2007-04-30
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by nealklomp on 2007-04-30
um, what does the current home partition look like?
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4878ad58-e167-434a-8e13-484488889732 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=6654599A54596DB5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=850ba66b-058a-43e0-b20d-db5806902cce /media/sda2     ext3    defaults        0       2
# /dev/sda4
UUID=ee165be9-6c23-4e19-a71a-d755e4e44d4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Skrynesaver on 2007-04-30
you don't currently have a /home partition, that's ok though, I presume this is the partition you wish to make your home partition
>  UUID=850ba66b-058a-43e0-b20d-db5806902cce /media/sda2     ext3    defaults        0       2
So all as I suggested above except change this line to 
>  UUID=850ba66b-058a-43e0-b20d-db5806902cce /home     ext3    defaults        0       2
Hope that helps

---

### Post by gjtoth on 2007-04-30
I'm attempting to do this, too.  Here's what's transpired so far:

*  I did a fresh install of Feisty.  During the install, Feisty gave me the option to create another partition on the drive, which I did and Feisty was installed on the blank partition leaving the old Beta Feisty on the other partition intact -- Boy did THAT come in handy as I forgot to back up a couple of directories!  The FRESH INSTALL Feisty is on HDA3 whilst the old system is on HDA1.

*  After I was certain I had everything I needed from the old system partition, I booted up GParted and formatted that partition in Ext 3.

*  Copied my current /home directory over to the HDA1.

I've attempted to follow the instructions here and at PsychoCat's however, here's where I'm stuck.  My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/hda3 :
UUID=e30f5fa4-1e53-415a-b883-05de046a3162	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/hda6 :
UUID=479adf52-64b9-48d5-8c42-13362a913725	none	swap	sw	0	0
/dev/hdc	/media/cdrom0	udf,iso9660	user,noauto	0	0
/dev/hdd	/media/cdrom1	udf,iso9660	user,noauto	0	0
/tmp/app/1/image	/tmp/app/1	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/2/image	/tmp/app/2	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/3/image	/tmp/app/3	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/4/image	/tmp/app/4	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/5/image	/tmp/app/5	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/6/image	/tmp/app/6	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/7/image	/tmp/app/7	cramfs,iso9660	user,noauto,ro,loop,exec	0	0

How do I tell it to make the HDA1 /home my home and not the HDA3?

---

### Post by sefs on 2007-04-30
something like this should work in your fstab...

```

/dev/hda1	/home		ext3		nodev,nosuid,errors=remount-ro		0	2

```



note that this is a pre-edgy type mount .... as you can see by the absence of the complex looking guids now present in your fstab, but it should still work.

---

### Post by merlinus on 2007-05-01
[QUOTE=Skrynesaver;2565453]Define too much difficulty ;)
If you have the new ext3 partition made, lets call it [I]hda3
[/I]```

sudo mkdir  /new_home
sudo mount /dev/hda3 /new_home
sudo cp -Rp /home/* /new_home
gksudo gedit/etc/fstab
```

comment out the current home partition with a #

----I got this far, substituting sda7 for hda3, but am not sure I understand which partition to comment out.

here is my fstab. I do not currently have a separate partition for /home, but sda8 is where /root lives:

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=74ea0d79-f0a5-4381-a98d-08258758e696 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=143857E33857C302 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=18082DAD082D8B38 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=D444F4A544F48B8C /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda8 :
UUID=8d0e34ce-515e-4595-b8d3-f04930ca0baa none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda7 /media/sda7 ext3 defaults 0 1

I am worried that this will destroy grub, which happened when I resized and added the new partition. I have spent most of today tracking down a way to fix it, and definitely do not want to go there again!

Sorry for my confusion....

Thanks.

-merlin

---

### Post by Skrynesaver on 2007-05-01
At the moment you have no entry for hda1 in your /etc/fstab.
If you run the following line it will return a unique id for the hda1 partition.
```
vol_id -u /dev/hda1
```
copy this uuid into the following lines and insert it into your /etc/fstab
```

#Entry for /dev/hda1:
UUID=<UUID FROM VOL_ID> /home           ext3    defaults        0       2

```

---

### Post by merlinus on 2007-05-01
[QUOTE=Skrynesaver;2570039]At the moment you have no entry for hda1 in your /etc/fstab.
If you run the following line it will return a unique id for the hda1 partition.
```
vol_id -u /dev/hda1
```

here are my results for this:
 vol_id -u /dev/hda1
/dev/hda1: error open volume

I changed hda1 to sda1, with similar results:

vol_id -u /dev/sda1
/dev/sda1: error open volume

I am running 7.04, in case this matters.

Thanks.

-merlin

---

### Post by Skrynesaver on 2007-05-01
Sorry, my fault, to get this info from a drive you need to be able to open the volumeID, this requires root privalege
```

sudo vol_id -u /dev/hda1

```

---

### Post by merlinus on 2007-05-01
Hi, and thanks for trying to help.

But I have no hda1,

My /home disk appears to be sda8, and the one I want to move it to is sda7.

Perhaps it is due to your version of ubuntu versus mine?

Meanwhile, I tried to follow directions at pussycats for doing the move, but things got screwed up when I inadvertently closed the terminal window, after which nothing worked.

Following their directions to recover the old system by booting from the live cd did not work because I could not mount sda8.

Now I am completely lost....

-merlin

---

### Post by gjtoth on 2007-05-01
> **sefs said:**
> something like this should work in your fstab...

```

/dev/hda1	/home		ext3		nodev,nosuid,errors=remount-ro		0	2

```



note that this is a pre-edgy type mount .... as you can see by the absence of the complex looking guids now present in your fstab, but it should still work.

Noperzzzzzzzzzzz.... bombed for me.

I tried this and it bombed too:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/hda3 :
UUID=e30f5fa4-1e53-415a-b883-05de046a3162	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/hda1 :
UUID=8a4db246-91fa-4d2f-a005-6b44e3e761f8	/	ext3	defaults,errors=remount-rw	0	2
#Entry for /dev/hdb1 :
UUID=68b714f2-7e54-497f-937d-a215b92e049d	/media/disk-1	ext3	defaults	0	2
#Entry for /dev/hdb2 :
UUID=3f56d014-a8a4-42c9-a4bc-e883de8e275b	/media/disk-2	ext3	defaults	0	2
#Entry for /dev/hda6 :
UUID=479adf52-64b9-48d5-8c42-13362a913725	none	swap	sw	0	0
/dev/hdc	/media/cdrom0	udf,iso9660	user,noauto	0	0
/dev/hdd	/media/cdrom1	udf,iso9660	user,noauto	0	0
/tmp/app/1/image	/tmp/app/1	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/2/image	/tmp/app/2	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/3/image	/tmp/app/3	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/4/image	/tmp/app/4	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/5/image	/tmp/app/5	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/6/image	/tmp/app/6	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/7/image	/tmp/app/7	cramfs,iso9660	user,noauto,ro,loop,exec	0	0

This one REAALLLLLY brought things to a screeching halt!  :lolflag:  Lost network connectivity too!

---

