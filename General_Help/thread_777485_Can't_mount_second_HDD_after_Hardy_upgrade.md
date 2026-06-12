---
title: "Can't mount second HDD after Hardy upgrade"
date: 2008-05-01
forum: General Help
---

### Post by Spindel on 2008-05-01
Firstly sorry if I posted this in the wrong section (I'm a newbie to these forums).

Ok now to my problem

I just upgraded to Hardy from Gutsy and now my second HDD refuses to mount (on which I have my music movies etc.)

The drive shows up under "Places" menu as 41,2 GB-media 
When I try to mount it I get the following message (in swedish I will translate):

"Ogiltig monteringsflagg vid försök att montera volymen"

Translated to english:

"Invalid mounting flag when attempting to mount volume"


This drive worked perfectly right before my upgrade to Hardy and if I go to the folder /media/Nifelheim (which is was the name of the volume before) I see that the folder indicates 1,7 GB of free space (which is about what I had)

So does anyone have any idea what I can/should do (except repartitioning/formating the HDD):(:(

Thanks in advance

---

### Post by danwood76 on 2008-05-01
It might be mounted with odd privaledges.
Can you post your fstab please?

This will dump it to the terminal:
```

cat /etc/fstab

```
also an fdisk list would be nice:
```

sudo fdisk -l

```

---

### Post by Spindel on 2008-05-01
```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=6d9afbe2-1b46-46b4-99cd-184d3f82e793 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9A1C15CE1C15A673 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=D8A4DE95A4DE758A /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=fdd6138d-e1a0-4ae7-8dd4-f08d9b83c08b none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/hdb1	/media/Nifelheim	ext3	defaults	0	

```

```
sudo fdisk -l
```


```
Disk /dev/sda: 41,1 GB, 41174138880 byte
255 huvuden, 63 sektorer/spår, 5005 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xcecccecc

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        2493    20024991    7  HPFS/NTFS
/dev/sda2            2494        5004    20169607+   f  W95 Utökad (LBA)
/dev/sda5            2494        4873    19117318+  83  Linux
/dev/sda6            4874        5004     1052226   82  Linux växling / Solaris

Disk /dev/sdb: 41,1 GB, 41174138880 byte
255 huvuden, 63 sektorer/spår, 5005 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x40184017

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1        5005    40202631   83  Linux

```

I see some lines are in swedish but I hope you can still understand them

---

### Post by danwood76 on 2008-05-01
Right, theres a duplicate entry and an incomplete definition.
If you open up your fstab for editing:
```

sudo gedit /etc/fstab

```
replace the entire contents of the file with this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=6d9afbe2-1b46-46b4-99cd-184d3f82e793 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9A1C15CE1C15A673 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=fdd6138d-e1a0-4ae7-8dd4-f08d9b83c08b none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1	/media/Nifelheim	ext3	defaults	0	0

```

This will mount the folder in /media/Nifelheim on bootup.
Save the file and reboot and see if it works.

---

### Post by Spindel on 2008-05-01
Hey thanks now it works *gives a big kiss*

It just appears as 41,2 GB-media and not the name I gave it (no bigge tho) :confused:

You don't happen to know how to fix that too :p

Now I just need to get kiba-dock to work again and my sound :|

Man Hardy was a messup IMO I had no problems at all going from feisty to gutsy but now nothing works as it should...

Also something fishy going on with the ati-drivers or XGL (or both) can't watch movies in full screen without them being laggy after the update.

But I will search the forum a bit for issues regarding that before making a new thread

---

### Post by danwood76 on 2008-05-01
Remove the xgl xserver. (package name xserver-xgl)
Its not needed and as you say it causes system lag, this is due to it using the processor to gen graphics which the new ati drivers can do ;)


The drive should really be mounting to: /media/Nifelheim which would appear on your desktop as Nifelheim.

You could try cleaning the fstab a bit further.
a cleaner version would look like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
/dev/sda1    /media/hda1     ntfs-3g    defaults     0       1
# 
/dev/sda6    none            swap    sw              0       0

/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1	/media/Nifelheim	ext3	defaults	0	0

```
Just replace your entire fstab as before.
That should work a bit better, I cleaned up some of the mounting options aswell.
Some were a bit out dated.

--edit --

Made a typo on one line :)

---

### Post by Spindel on 2008-05-01
I appriciate all your help but the last version of fstab didn't change anything still shows up as 41,2 GB-media (but as I said really no biggie since I can now access it)


I will just take a chance and ask you about the ati drivers

I need to activate composite in the xorg.conf file again now when uninstalled XGL right?

EDIT:// sorry typo it should say xorg.conf

---

### Post by danwood76 on 2008-05-01
No you dont.
But what I would do is get the ati driver to reconfig it for you, you may have some old options that may cause issues.

Run this command after removing xgl:
```

sudo aticonfig --initial -f

```

That should sort you, then reboot.

---

