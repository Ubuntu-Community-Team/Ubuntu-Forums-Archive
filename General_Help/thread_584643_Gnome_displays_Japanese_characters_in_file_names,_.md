---
title: "Gnome displays Japanese characters in file names, but not Greek characters?"
date: 2007-10-21
forum: General Help
---

### Post by mchnhed on 2007-10-21
Hello all,

I have installed support for multiple languages, but for some reason Gnome doesn't display (nor has it ever displayed) Greek characters in the file names. The weird part is that it displays Japanese characters fine, just not Greek characters. What happens is that Gnome displays a file that was named with Greek characters (in Windows) as all question marks, like this: "??????.mp3".

Just in case it matters, the relevant files are being stored on a FAT32 partition.


:confused:  I see that similar posts have not had any responses in the past. Hopefully I receive a response this time! Any advice in this matter would be much appreciated!

---

### Post by gmaniac on 2007-10-21
If I understanf correctly the problem is with the fat32 and not with your 
linux partition (you can see the greek names fine in the linux partition correct ??)

Hmm well the way you mount the partition is important but i don't know
if it's the only thing to configure.
I don't remember what settings i used with fat32 but I found this

/dev/hda1  /mnt/windows  vfat  **defaults,codepage=737,iocharset=iso8859-7   0   0**

(important options marked in bold) but that should only give you access to the greek and english filenames and not the others.

First try this though
/dev/hda1  /mnt/windows  vfat ** defaults,iocharset=utf8   0   0**

if it's not already there.

BTW You have japanese and greek files?? You are multi-talented aren't you??:)

---

### Post by mchnhed on 2007-11-20
OK, here's a more specific description of the problem: I can create and read file names in Greek and Japanese from within Windows (and save them to a FAT32 partition), but then when I login to Ubuntu the file names are just all question marks. Now that I think about it, this happens with accented characters for file names in Italian and Spanish as well. The weird thing is that when I create a file with special characters from within Ubuntu, and save it on the same FAT32 partition, it retains the name just fine.

Is this because I'm working with a FAT32 partition? Should I just backup my files and convert the partition to NTFS, now that Gutsy Gibbon has full read-write support for NTFS? Or is there something else going on here?

For the record, here's what my /etc/fstab looks like in case any experts see anything out of wack that could be throwing me off:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5b632f2f-d8aa-44c3-ab38-79a4a1a08fbb /               ext3    defaults,errors=remount-ro 0  $
# /dev/sda5
UUID=9a2ee237-a09e-4b23-8f3e-13844ed0538b none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda2       /mnt/condiviso  vfat    umask=000,auto,user,noexec,rw,sync      0       0

```

---

