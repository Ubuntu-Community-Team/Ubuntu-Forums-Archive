---
title: "Problems with formatting/burning DVD-RW using dvd+rw-tools"
date: 2006-11-11
forum: General Help
---

### Post by jbla00 on 2006-11-11
I get errors when I try to format or burn DVD-RW. Here is some output from the programs i use
[INDENT]
root@pc-one:~# dvd+rw-mediainfo /dev/hdc
INQUIRY:                [LITE-ON ][DVDRW SOHW-1673S][JS01]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         14h, DVD-RW Sequential
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     4.0x1385=5540KB/s@[0 -> 0]
 Speed Descriptor#0:    00/0 R@3.2x1385=4432KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       33h, DVD-RW book [revision 3]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Last border-out at:    0*2KB=0
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: reserved/damaged
 Number of Tracks:      0
READ CAPACITY:          0*2048=0
root@pc-one:~#
root@pc-one:~#
root@pc-one:~# dvd+rw-format -blank=full /dev/hdc
* DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
* 4.7GB DVD-RW media in Sequential mode detected.
* blanking .:-[ READ TRACK INFORMATION failed with SK=3h/ASC=57h/ACQ=00h]: Input/output error
root@pc-one:~#
[/INDENT]

I've tried two different media, and they are both brand new. I get the same errors on both media.

I have no problems burning CDs in the same drive.

Running Edgy updated from Dapper.

Can anyone help?

---

### Post by kazuya on 2006-12-06
Somebody did this. I do not know if it would help you though.:

Formatting dvd-rw doesn't work in nautilus 

--------------------------------------------------------------------------------

Hi,

I use nautilus to write my discs.
this is what works:

- writing cd-r: works
- writing cd-rw:works
- blanking cd-rw: works
- writing dvd-r:works
- writing dvd-rw:works
- formatting dvd-rw:doesn't work

I don't have dvd+r and dvd+rw so i couldn't test them.

The problem is that when i insert a dvd-rw that is not empty, try to write to it and tell nautilus to erase the existing data, it will give me "error writing to disc" and the dvd still contains the old data. When not needing to erase the old data(blank dvd-rw or dvd-r) nautilus writes the disc without problems.

I've installed gnomebaker to see if the problem existed there.
After selecting "format dvd-rw" in gnomebaker it seems to erase the disc and completes without an error message but the disc is not blanked at all.

If i run "dvd+rw-format -blank /dev/dvd" in the terminal the disc gets formatted perfectly!
If this works than why aren't nautilus and gnomebaker able to format the disc?

grtz
hesoez

---

### Post by Charles2008 on 2008-01-19
why can't I just add data to an existing cd rw or dvd rw instead of erasing the entire disk?


I am used to being able to do this in xp.


Thanks,


Charles

---

### Post by logos34 on 2008-01-19
oops. delete

---

### Post by logos34 on 2008-01-19
> **Charles2008 said:**
> why can't I just add data to an existing cd rw or dvd rw instead of erasing the entire disk?


I am used to being able to do this in xp.


Thanks,


Charles

> **growisofs -M /dev/dvd /more/files**

see

man growisofs

---

### Post by Charles2008 on 2008-01-19
-( unable to open64("/dev/dvd/more/files",O_RDONLY): No such file or directory

This is the output I get when I tried tried that command.


thanks,


Charles

---

### Post by logos34 on 2008-01-19
need to run it as root

**sudo **growisofs...

---

### Post by heindsight on 2008-01-19
> **Charles2008 said:**
> -( unable to open64("/dev/dvd/more/files",O_RDONLY): No such file or directory

This is the output I get when I tried tried that command.


thanks,


Charles

There should be a space after /dev/dvd and /more/files doesn't mean you should literally type /more/files, it means you should list the paths to all the files you want to add to the DVD.

for example if you want to add all files in your Desktop directory and all files in a directory called Music (in your home directory) to a dvd, use:
```
growisofs -M /dev/dvd ~/Desktop/* ~/Music/*
```

> **logos34 said:**
> need to run it as root

**sudo **growisofs...

afaik growisofs doesn't require root access. I think all that's needed is that you user belongs to the cdrom group.

---

### Post by logos34 on 2008-01-19
> **heindsight said:**
> There should be a space after /dev/dvd ...

afaik growisofs doesn't require root access. I think all that's needed is that you user belongs to the cdrom group.

I didn't see he had left out the space, you're right.  I thought it was complaining about permissions...

---

### Post by Charles2008 on 2008-01-19
I am trying to write to my DVD-RAM drive which the system picks up as a DVD +-R CD RW drive writing to a CD-RW.


This is the output trying to copy the Documents folder " growisofs -M /dev/dvd ~/Documents/* 
:-( unable to open64("/dev/dvd",O_RDONLY): No such file or directory



Thanks,

Charles

---

### Post by heindsight on 2008-01-19
> **Charles2008 said:**
> I am trying to write to my DVD-RAM drive which the system picks up as a DVD +-R CD RW drive writing to a CD-RW.


This is the output trying to copy the Documents folder " growisofs -M /dev/dvd ~/Documents/* 
:-( unable to open64("/dev/dvd",O_RDONLY): No such file or directory



Thanks,

Charles

OK, usually /dev/dvd is a link to your DVD device. You'll need to find out which device file points to your DVD writer. You can do that with the command:
```
sudo lshw -C disk
```
Look for your DVD writer in the output. There should be a logical name for the device (on my machine it is /dev/hdb). Use that logical name instead of /dev/dvd in the command line.

I find it rather strange that /dev/dvd doesn't exist on your system though. Usually udev creates this link automatically.

---

### Post by Charles2008 on 2008-01-19
On my device it was /dev/dvd1.  

It worked first with the growisofs -Z command to add data to a blank DVD then it added data when I used the growisofs -M command.

Can the command growisofs also be used to write to a CD RW in the same way as writing to a DVD RW.  My DVD device is also a CD RW drive as well.  I also have another CD RW drive on the computer as well.

Thanks,

Charles

---

### Post by logos34 on 2008-01-19
yeah, odd there's no 'dvd' symlink in /dev

> **Charles2008 said:**
> Can the command growisofs also be used to write to a CD RW in the same way as writing to a DVD RW.

use **cdrecord** 

[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)
(-> multisession)

---

