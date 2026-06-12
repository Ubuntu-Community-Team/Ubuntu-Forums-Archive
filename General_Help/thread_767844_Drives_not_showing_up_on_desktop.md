---
title: "Drives not showing up on desktop"
date: 2008-04-25
forum: General Help
---

### Post by LavosPhoenix on 2008-04-25
My other drives are not showing up by default on the desktop as they did with 7.10. File System, and Home are there, just my other drives are not. All of the drives are in fact being mounted properly. xubuntu 7.10 live CD displays the icons just fine, 8.04 does not. What was changed between versions that no longer causes the other drives to be shown on the desktop, and how can I fix this?

---

### Post by HunterThomson on 2008-04-25
Can you be more specific? What drives do you have? What drives are not showing? What drives are showing strange and how?

---

### Post by LavosPhoenix on 2008-04-25
I have a 200GB ext3 drive and a 300GB NTFS formatted drive mounted with ntfs-3g of which both icons are not showing up on the desktop as they had just done a couple of hours ago before the upgrade. I just thought of an idea though, Did Ubuntu/Xubuntu get rid of the wierd UUID wierdness in the fstab?

Here's my fstab...

# /dev/sdc1
UUID=0ad5e7cb-9f4d-43fc-9aba-5afec67b351a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8458464F58463FE2 	/media/Que	ntfs	defaults,umask=007,gid=46	0	1

# /dev/sdb1
# UUID=1E60C54460C5237F /media/Super     ntfs    defaults,umask=007,gid=46 0       1
#/dev/sdb1	/media/Super	ext3	defaults,errors=remount-ro 0 1
UUID=3115c999-0c07-404c-b9d7-5609f91914dd	/media/Super	ext3	defaults,rw,auto,user	0	0

# optical drive
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by LavosPhoenix on 2008-04-25
Oh, and I did an upgrade from my preexisting xubuntu 7.10 install.

---

### Post by LavosPhoenix on 2008-04-26
Well, I've been able to create desktop links to the drives mounted in /media, however I still cannot get hal-mtab or whatever is necessary to automagically obtain the drives allowing for the icons to appear on the desktop...

---

### Post by lunnjd on 2008-04-29
Bump.

Any help on this would be greatly appreciated as I have the same exact problem.:cry::cry:

---

### Post by LavosPhoenix on 2008-04-30
Yeah, and unlike other people's problems, as noted in the threads below, my drives are mounted in /media, and are noted in the fstab as such.

[http://ubuntuforums.org/showthread.php?t=766496](http://ubuntuforums.org/showthread.php?t=766496)
[http://ubuntuforums.org/showthread.php?t=771057](http://ubuntuforums.org/showthread.php?t=771057)

---

### Post by ryanhaigh on 2008-04-30
What application is used to display the icons on xubuntus desktop, i know in ubuntu/gnome there is a gconf setting for nautilus to display volumes on the desktop but im not sure if that would be relevant to xfce/xubuntu.

Anyway for gnome/nautilus run gconf-editor, browse to apps>nautilus>desktop and enable volumes_visible

---

### Post by mkarnicki on 2008-05-01
This is so bothersome.. my drives are mounted under /media and they won't appear on the desktop until I click them (=mount) via Places -> Removable media -> xyz

---

### Post by lunnjd on 2008-05-02
mkarnicki, I think you are using Gnome desktop (Ubuntu)? In that case maybe you need to check that fstab is mounting your drives/partitions. I don't know for sure, because I don't use Ubuntu. This posting is about the problem in Xubuntu 8.04.

---

### Post by mkarnicki on 2008-05-03
Oh.. thanks lunnjd ^^ I'll check that.

---

### Post by mkarnicki on 2008-06-13
I'm not continuing my last post so that you guys can see my new reply:

My problems where solved using Storage Device Manager (I don't remember if I found it in Synaptic or Add/Remove, but you'll manage). I played with it around and now when I boot I already have my partitions mounted, these which I want, and nicely show up on my desktop.

Solved!

---

### Post by Andreas1 on 2008-07-03
> **LavosPhoenix said:**
> My other drives are not showing up by default on the desktop as they did with 7.10. File System, and Home are there, just my other drives are not. All of the drives are in fact being mounted properly. xubuntu 7.10 live CD displays the icons just fine, 8.04 does not. What was changed between versions that no longer causes the other drives to be shown on the desktop, and how can I fix this?

bump

i am using thunar in gnome, and as far as i know in xfce thunar is also responsible for the desktop, so this is one and the same problem, and so far there has been no solution. thunar does not show any internal drives (except for filesystem) in its sidebar or on the xfce desktop.
i use hardy, and my ntfs drive is in fstab, anyway, i do not think this problem is related to fstab, it is somehow related to thunar, nautilus for example does display the same drives properly.

edit: maybe i should mention that thunar does display external drives, which makes this either an odd combination or a bug.

---

