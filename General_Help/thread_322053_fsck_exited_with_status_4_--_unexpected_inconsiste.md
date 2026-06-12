---
title: "fsck exited with status 4 -- unexpected inconsistencies"
date: 2006-12-19
forum: General Help
---

### Post by Mau on 2006-12-19
My system started to act weird (Thunderbird wouldn't let me compose new mail messages), so I backed up and restarted my system.  During the bootup, I was greeted with:

```

/dev/hda1 contains a f ile system with errors, check forced.
/dev/hda1
Inodes that were part of a corrupted orphan linked list found.

/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (i.e., without -a or -p options)
fscked died with exit status 4.

[fail]

* An automatic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintence mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintence, press CONTROL+D
to determine the maintence shell and restart hte system.
bash: no job control in this shel
bash: groups: command not found
bash: lesspipe: command now found
bash: dircolors: command now found

```
and then I have a command prompt as root.

I'm currently downloading the Ubuntu live CD on my Mac to run fsck manually, but can anyone tel me what "Inodes that were part of a corrupted orphan linked list found." means?

I think this might be related to a DVD that I had (full of pictures) and I was having trouble with getting it to eject (I had to eject it several times).    Perhaps the system still thinks the DVD is mounted?

Does this look serious? I have a backup of everything, but I would like to know if I should prepare my system for disaster. ](*,)

---

