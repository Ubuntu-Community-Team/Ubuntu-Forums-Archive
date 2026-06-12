---
title: "Troubles with ISO mounting"
date: 2014-11-08
forum: General Help
---

### Post by AyazeTC on 2014-11-08
mount -o loop -t iso9660 /home/ayazetc/BaldursGate/iso-bg1.iso /mnt/iso

from the hour of researching i've been doing, that's what i thought would work.

it doesn't.

My process was this: I downloaded Baldur's Gate

I used WinRAR under wine to extract the rar files... and rearchive them as isos (ykno the r00, r34, that stuff? I was told i only have to do the first rar, which is what i did.)

Aaaand i tried mounting it.

A

Lot.

my current issue is that 9660 is a read-only filesystem, and my machine doesn't recognize 13490.

---

### Post by QIII on 2014-11-08
Hello!

From what site did you download it?  There might be a problem with the files on that site.

---

### Post by yancek on 2014-11-08
If you are loop mounting with the command above you do not need the "-t iso9660".
You indicate "it doesn't work" which is a pretty vague statement.  What exactly happens.


> my current issue is that 9660 is a read-only filesystem, and my machine doesn't recognize 13490. 		

Any iso9660 will be read only,  what's the problem with that?  Do you want to edit it.  And how does "13490" fit into this picture?

---

### Post by AyazeTC on 2014-11-08
@Qlll

theisozone. I got Fallout off of there once at it worked beautifully.

---

### Post by AyazeTC on 2014-11-08
The exact error:

mount: block device /home/ayazetc/BaldursGate/iso-bg1.iso is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(dont know how to format text in a code box)

---

### Post by bapoumba on 2014-11-09
We have found no evidence you can get this game for free. Thread closed.

---

