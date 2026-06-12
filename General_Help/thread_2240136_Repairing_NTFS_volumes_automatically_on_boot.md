---
title: "Repairing NTFS volumes automatically on boot"
date: 2014-08-18
forum: General Help
---

### Post by sdetheridge on 2014-08-18
I have an NTFS volume which I'm mounting automatically at boot, and which I would like available at system startup as I run some programs on login that require it.

The fstab entry looks like this:
```
UUID=30EA776CEA772D6A    /home/simon/databank    ntfs    uid=1000,gid=1000    0    1
```

My computer is dual-boot, and often Windows doesn't appear to clean up the volume properly because <insert obligatory disparaging comment about Windows here>

This dumps me to the 'press M to manually fix the problem, or S to skip mounting' screen during boot. I then press M and run ntfsfix manually, and then everyhting boots just fine. Very annoying when I'm trying to remotely reboot my computer.

Is there a way to get ntfsfix to automatically repair the volume when it fails to mount, to work around this issue?

---

### Post by TheFu on 2014-08-18
Managing bad file systems is best handled by the native OS tools - Windows in this case. I'd look for the root cause and try to address that.  Didn't Win8 change the way that file systems were shutdown (or not?). Thought there was a registry hack to make it behave properly. It was big news here during the Win8 beta cycle.

---

### Post by Mark Phelps on 2014-08-18
Win8 changed the default action when choosing "shutdown" in Windows.  Previously, Windows did, in fact, shut down.  But with Win8, it did NOT; instead, it went into a new form of hibernation that leaves ALL the partitions that were accessed while Win8 was running still mounted -- even after "shutdown" was requested.  This was done to support FastStartup -- which was really just a new form of hibernation.  This new hibernation completely blocks the mounting of NTFS volumes previously being used while Win8 was running.

It's not a registry hack to remove this; instead, it's going into Win8 and disabling FastStartup.

---

### Post by sdetheridge on 2014-08-19
Thanks. It still seems a bit odd to me though that certain filesystems will be checked automatically at boot, and there is a program to do this installed. Disabling faststartup sounds like a good idea, but is there any way to do what I want, for the sake of completeness?

---

### Post by TheFu on 2014-08-19
Already tried the ```

errors=remount-ro
```
option inside the fstab?
I've never tried it with NTFS - a foreign file system.  Don't have a clue how to tell it to run a non-standard program either. Sorry.

Also having the mount start later might be a help ... either with a later stage in the fstab settings or by delaying it by using a script to handle it - inside that script, you could force the nftschk tool to run. If you do the 2nd option, be certain to remove it from the fstab.

---

### Post by sdetheridge on 2014-08-21
Yeah, I tried changing the last 1 to a 2, and symlinking ntfsfix to fsck.ntfs, but that didn't do any good. I'm not sure where the magic is that runs fsck.ext2 or whatever is required on ext4 volumes, or how it works... So I'm not sure how to plumb ntfsfix into that process.

Anyone with any ideas on that?

remount-ro isn't really what I want, as I want to have a writeable volume at system startup.

Disabling FastStartup on Win8 goes a long way to alleviate the problem, and I'm pleased with that... But I don't see why Ubuntu can't fix my ntfs volume on startup, if it can fix my ext4 or xfs (or whatever) volume, given that there's a perfectly serviceable tool to do so.

---

### Post by TheFu on 2014-08-21
If a file system is broken, it shouldn't be mounted at all.

**This isn't an Ubuntu issue.** I've never been able to fix any ext2/3/4 partition from Windows, have you?

Why not just mount the partition with the rc.local after running the ntfs fixing thing?

---

### Post by Mark Phelps on 2014-08-21
> But I don't see why Ubuntu can't fix my ntfs volume on startup, Because they're very different filesystems.

Besides, ntfsfix can only fix the most trivial of NTFS problems.  To fix NTFS problems, you need to run Windows utilities -- which you can't do from inside Linux.

---

