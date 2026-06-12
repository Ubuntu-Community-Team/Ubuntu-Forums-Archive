---
title: "What's WRONG with Ubuntu Edgy?!!!"
date: 2007-03-14
forum: General Help
---

### Post by ubunTux on 2007-03-14
Oh well! Got headaches about this one...

I've been using Ubuntu Linux for quite sometime now. Started with Warty, 'til now that I'm using Edgy. I haven't gone into issues at the late versions, until now with Edgy.

First, why can't I see the mounted volumes at my Desktop? I believ they are mounted coz I can access the mounted partitions if I browse /media using nautilus. One more thing is, via gconf-editor and going to apps/nautilus/desktop, volumes_visible is ticked. What seems to be the problem?

Another issue I encounter is whenever I plug a USB Flash Drive or a USB External HDD, they aren't automatically mounted, unlike before with Dapper. Why do I have to manually mount USB drives, via console/terminal? What's wrong with Ubuntu Edgy?!!!

Please, someone explain and help me resolve this issue.

Thanks in advanced! God bless you all!


.edit
Oh! And one more thing... There are times that when I run an application, it won't load. And when I do **ps -A**, at the terminal I see bug-budy and gnome_segv2. When I **killall bug-buddy**, I will be logged out of ubuntu and can use it again. What the hell is the problem with bug-buddy? Why does it hangs up my PC?!



.ubuntux

---

### Post by Jose Catre-Vandis on 2007-03-14
A simple answer, though not helpful, is that I do not know. It must be a local problem with your machine otherwise everyone else on Edgy would be having the same problem. Have you been upgrading or done a clean install? Do you have the Edgy Live CD to test for these errors without installing? What does your /etc/fstab file look like?

---

### Post by Smuve on 2007-03-14
Your hotplugging issues may have something to do with your removable media settings.
System > Preferences > Removable Media and Storage Devices

---

### Post by ubunTux on 2007-03-15
> **Jose Catre-Vandis said:**
> A simple answer, though not helpful, is that I do not know. It must be a local problem with your machine otherwise everyone else on Edgy would be having the same problem. Have you been upgrading or done a clean install? Do you have the Edgy Live CD to test for these errors without installing? What does your /etc/fstab file look like?

I always make a clean install... How can I use the Live CD to test for errors?

Here's what my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=b7188eaf-ed79-491d-adde-f51126f69b78 /               reiserfs defaults        0       1
# /dev/hdc1
UUID=0bd6e31e-a3c0-4241-b162-987591214ad9 /boot           ext2    defaults        0       2
# /dev/hdc5
UUID=0bb15dd9-fe29-4e67-a851-92b0ed6abd04 /home           reiserfs defaults        0       2
# /dev/hdc6
UUID=DA32-E48F  /media/fat32_hdd vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=54B8D14FB8D1306A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=60685FBF685F9320 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=BA20B06F20B0346B /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc2
UUID=b13c0acb-2f16-4580-86c4-911d483d5fc0 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```



.ubuntux

---

### Post by ubunTux on 2007-03-15
> **Smuve said:**
> Your hotplugging issues may have something to do with your removable media settings.
System > Preferences > Removable Media and Storage Devices

Here's what I have...

[Checked]
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

[Unchecked]
Auto-run programs on new drives and media
Auto-open files on new drives and media



.ubuntux

---

### Post by Nythain on 2007-03-15
ok, kind of a stupid and overly obvious so probably useless suggestion... have you check out the section (i dont know hwere cause i run kde) where you can select to show mounted device icons on the desktop to make sure they are on???

---

