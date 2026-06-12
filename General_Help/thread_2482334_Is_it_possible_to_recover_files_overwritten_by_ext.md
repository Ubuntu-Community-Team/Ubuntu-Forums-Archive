---
title: "Is it possible to recover files overwritten by ext4?"
date: 2022-12-28
forum: General Help
---

### Post by empleat on 2022-12-28
I accidentally overwritten one of my flash drives with Ubuntu live USB, filesystem ext4. I might already messed this up: I tried from being annoyed quickly TestDisk to recover filesystem, it found previous EFI GPT partition (or rather filesystem?) it seems which was created in Windows! But than I realized it doesn't support ext4 for recovery of deleted files from reading manual...

There wasn't anything so important, but multiple interesting things I can't find anymore if this is goner.

Is there any chance to recover this? USB drive is now inaccessible from windows, so I doubt I can recover it there!

I will avoid further write on the drive ATM...

Thanks I have chronic pain and I don't have strength nor time to be solving this right now!

PS: this isn't time pressing, but if anyone gave me tutorial if this can be done easily from Windows/Linux I would appreciate it :)

---

### Post by dragonfly41 on 2022-12-28
You might try installing R-Linux on Windows. This reads ext4 files and has some recovery options to try.

Also read here for other options in testdisk  ..

[https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=8048](https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=8048)

These are long shots.

---

### Post by oldfred on 2022-12-29
If you installed the ISO, that amount of data at beginning of drive is gone.
Deeper search with testdisk often shows files, for all formats. That will include full file name. You have to then copy to another device.

If testdisk deeper search does not work then photorec can be used. It scans filesystem for anything that looks like a file. But does not recovery full filename, just files by type. I had saved some text files many times and photorec found all of them. Took a long time to sort thru them to figure out which was which and then compare to figure out which was more complete or newer. You have to have another drive large enough for all the recovered data. Both improved backups and added file name for my text files at beginning of file.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Some have posted that if NTFS, Windows tools (most paid) can work better.

---

