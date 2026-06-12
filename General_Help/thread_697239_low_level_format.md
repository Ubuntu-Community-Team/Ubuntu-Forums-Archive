---
title: "low level format"
date: 2008-02-14
forum: General Help
---

### Post by Riffer on 2008-02-14
[SIZE="2"] Well after much tweaking , installing, uninstalling both correct and incorrect apps and programs its time to do a complete reinstall of Ubuntu.  And I figure its time to get rid of Windows and reformat my HD.

So my question.. how can I do a low level format, fdisk etc. of my HD using only Linux tools  I know how to do this using Dos and the like, but at this point I would like to try/learn how it is done in Linux.                                                                                                                    [/SIZE]

---

### Post by Riffer on 2008-02-14
[SIZE="2"]Thinking about it I guess I could use the LiveCd and choose the "use entire disk" option in the install sequence.  But will that rewrite the MBR?  Also I like to partion my HD into 3 or 4 partions and I would like to do that ahead of the install.                                                                                           [/SIZE]

---

### Post by farruinn on 2008-02-14
I'm not sure you need to do a "low level" format ([google define: low level format]("http://www.google.com/search?hl=en&q=define%3A+low+level+format&btnG=Google+Search")). When you do the installation you'll come to the step for partitioning the drive. Just select the option to use the entire drive and it should wipe all your current partitions and create the appropriate ones for Ubuntu.

Good luck and congrats on making this decision!

Edit:
Looks like you replied to yourself before I got mine in :D

The "use entire disk" is indeed what I was talking about. If you want to make your own partitions you can do that as well of course. Just make sure you give yourself enough room on all the partitions.

---

### Post by pointone on 2008-02-14
I'm assuming you mean **high**-level formatting. [Low level formatting]("http://en.wikipedia.org/wiki/Disk_formatting#Low-level_formatting_.28LLF.29_of_hard_disks") is a bit more involved.

Using the installer's "entire disk" option will format the entire disk and give you the option of overwriting the MBR. fdisk is also included on the live CD.

*EDIT*

Bah... too slow!

---

### Post by Riffer on 2008-02-15
[SIZE="2"]You're right its really not a low level format.  Just showing my age and back in the day when a complete wipe of the HD (including) MBR was called a low level format.
                                                                                         [/SIZE]

---

### Post by SpaceTeddy on 2008-02-15
back to the topic - i use Boot and Nuke to wipe HD's clean. Runs from a live cd and leaves nothing on the drive... as far as i have found out anyway :)

read more here [http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

---

### Post by randy78 on 2008-02-15
+1 for DBAN :)

---

### Post by Cadmus on 2008-02-15
I hear good things about DBAN, for the sake of diversity though I'll point out you can use a Knoppix livecd and the 'wipe' command which while slower is a pretty solid shredding of a disk.

---

### Post by Riffer on 2008-02-16
[SIZE="2"]Thanks for your replies.  I'll check out DBAN for sure.[/SIZE]

---

