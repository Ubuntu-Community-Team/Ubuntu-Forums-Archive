---
title: "[SOLVED] How to Format a New USB Hard Disk"
date: 2014-02-09
forum: General Help
---

### Post by Iggy64 on 2014-02-09
I have received the gift of a WD My Passport Ultra 1TB USB hard disk.  When I mount it, my file manager (SpaceFM) tells me I have 931.1GB of 931.5 free.  I see 6 folders and one file of Windows-related backup software, instruction manuals, etc.  Wondering why I only see 931GB on a 1TB drive, I surfed the web and found an enormous volume of discussions on the write-protected hidden partition WD has put onto this disk.  Apparently, it is supposed to be a "Virtual CD" for God knows what.  No one seems to know what to do to get rid of this annoyance, but most of the writers are trying to accomplish this in Windows, to use the disk in Windows.

If I run udisks --dump, it lists:

/dev/sdb   1,000,170,586,112 bytes  My Passport 0820
/dev/sdb1  1,000,169,537,536

If I run gnome-disk-utility, I get the same numbers as above.

Neither udisks nor the disk utility shows me a 930GB partition.

As a relative noob, I am at a loss as to what to do.  I would like to format the drive as one single 1TB ext4 partition.  I have no use for any WD software.  I know how to back things up by myself, when I want, how I want.

Do I need to delete the existing partion(s) first?  The Disk Utility is showing me a 1TB partition, but my file manager is showing me a 930GB partition.  Which one would I be deleting?  And what about the hidden partition?

I'm reluctant to just go ahead and reformat, for fear I will end up with only 930GB and then not know how to ever recover the missing storage.  I have no clue as to how Linux will deal with the hidden partition.

Not the end of the world, obviously.  But an opportunity to learn some new stuff here.

Thanks for any guidance.

---

### Post by bc.haynes on 2014-02-09
I have a 500 Gb HDD. Ubuntu shows it as 465 Gb. It's all in the way manufacturers and resellers figure their bytes. Take a trillion (1000000000000) bytes and divide it by 1024 (one kilobyte) and you will get the actual bytes on the HDD. Sorry, but I have forgotten why you divide by 1024....my mind don't recall very well.

---

### Post by Iggy64 on 2014-02-09
Thanks to BCH for reminding me about the way bytes are counted.  I'm used to working with much smaller drives (shows how old I am) where the difference between "promised" and "actual" bytes is not so great.  The bigger the drive, the bigger the disparity.  

A good reference is here:

[http://www.tweakandtrick.com/2013/07/lost-storage-space.html](http://www.tweakandtrick.com/2013/07/lost-storage-space.html)

So, a 1TB drive delivers only 931GB.

I guess this means my new Western Digital HD does NOT have the hidden partition everyone has been buzzing about for the last couple of years.  I just see one partition, and the file manager shows it to be 931GB, which is evidently the correct size.

Thanks for getting me back on the right track.

---

### Post by Iowan on 2014-02-09
I can never remember which is which - so i gotta look it up ([Gibibyte]("http://en.wikipedia.org/wiki/Gibibyte"))
a gigabyte (GB) is1000^3
a gibibyte (GiB) is 1024^3

---

