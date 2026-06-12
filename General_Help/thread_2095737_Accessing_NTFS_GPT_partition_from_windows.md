---
title: "Accessing NTFS GPT partition from windows"
date: 2012-12-17
forum: General Help
---

### Post by sirbow2 on 2012-12-17
I followed [this guide]("http://blog.elsdoerfer.name/2010/05/21/booting-ubuntu-karmic-and-windows-7-from-a-gpt-partition-using-bios/") to install Windows 7, win8, ubuntu and will install OS X on my pc. basically, its getting around windows' whining about installing on a GPT partition. see here for more details on my process: [http://dduino.blogspot.com/2012/12/quad-booting-windows-78-os-x-and-ubuntu.html](http://dduino.blogspot.com/2012/12/quad-booting-windows-78-os-x-and-ubuntu.html)
Note: i havn't installed OSX yet and neither Chameleon, so i use grub still.

The issue is that i cant access the unformatted (eventually OSX), Ubuntu and Data partitions from win 7 & 8. in disk management, they all show up as a combined 600GB unformatted region. Ubuntu, of course, has no issue. I have run the gptsync program as said in the guide which should solve the problem. yet win7 + 8 still work which means something weird is going on.

EDIT: oops, attached the pic

---

### Post by sirbow2 on 2012-12-19
i think i can do this now? bump :P

---

### Post by Bashing-om on 2012-12-20
sirbow2; Hi !

How bout thinking like so:
Ubuntu can and does read windows partitioning/formatting (ntfs); but windows does not play so nice with ubuntu in that windows does not read the ext4 file system format that ubuntu uses.

Is this in relation to what you are thinkin' ???

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by sirbow2 on 2012-12-20
but i find it strange that the NTFS partition isnt read either. they seem to be lumped together in a unallocated section to windows.

ive been reading this: [http://www.tomshardware.com/forum/237634-50-accessing-files-created-ubuntu-ntfs-drive-windows](http://www.tomshardware.com/forum/237634-50-accessing-files-created-ubuntu-ntfs-drive-windows)
 and think i might need to check permissions of the disk or check integrity.

---

### Post by Bashing-om on 2012-12-20
Hate to say "I do not know" bad response ! But, windows is not my forte - to say the least.
Wait for others more versed in windows to respond ( I will continue to monitor this thread).

[INDENT]not much else to say at this time < == BDQ

[/INDENT]

---

