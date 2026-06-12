---
title: "Very serious problem with Ubuntu"
date: 2007-11-21
forum: General Help
---

### Post by benniebrown07 on 2007-11-21
For no particular reason my mozilla will close and i cant install things and then when I try to open programs it'll say starting program and it'll never open. Then I'd restart it and it'll try and start ubuntu but it loads halfway and goes to a black screen with this on it:

/dev/sda2 contains a file system with erros, check forced.
/dev/sda2:
Inodes that were part of a corrupt orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e without -a or -p options)
fsck died with exit status 4
[failed]
*An automatic file system check (fsck) of the root filesystem.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the
root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance; press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@bennie-desktop:#

When I put in fsck it like goes through some commands and ask me to to choose Fix y/n and when I hit y to all of them and it finally says *****REBOOT LINUX*****
and I just hit control alt delete and it restarts.

But now my pc started off like before with mozilla closing and not starting again, other programs not starting or installing and I resarted it thinking ill run fsck but this time it says something different and it wont start up from the hard drive but i've got the cd I installed Ubuntu with and Im on that (Thank God).
Anyone know why these things could be happening maybe a virus or something any one know of a way to fix this? Any information you have is greatly appreciated.
Thanks in advance, Bennie Brown

---

### Post by EspressoRulz on 2007-11-21
I would start by running diagnostics on your memory and hard disk and let us know how that goes.

Take a look at "Ultimate Boot CD".  If you are not familiar with it, check out the sourceforge page at -->  [http://ubcd.sourceforge.net/]("http://ubcd.sourceforge.net/download.html")

---

### Post by stunner on 2007-11-21
Sounds like a dying harddrive...

For the mozilla/other programs problem, what is the output if you launch them from gnome-terminal?

---

### Post by EspressoRulz on 2007-11-21
That was what I was leaning towards but I have seen very weird errors with failing memory also causing the same behavior - corrupted writes to HD.

General rule, if you need to run fsck more than twice and it still complains, then be safe and replace the HD.

---

### Post by stunner on 2007-11-21
> **EspressoRulz said:**
> That was what I was leaning towards but I have seen very weird errors with failing memory also causing the same behavior - corrupted writes to HD.


Interesting - good to know.

---

### Post by benniebrown07 on 2007-11-22
i have another 80 gb Western Digital harddrive but it has stuff downloaded on it all ready (i was using it as a slave on my old pc) how do I go about setting up linux on it?

---

### Post by Sef on 2007-11-22
> That was what I was leaning towards but I have seen very weird errors with failing memory also causing the same behavior - corrupted writes to HD.

To check your ram, do a mem86test.   If I believe it is located in GRUB.

---

