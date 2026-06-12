---
title: "HFS+ drive mounting problems, filesystem corruption"
date: 2007-07-10
forum: General Help
---

### Post by wgscott on 2007-07-10
I've installed all of the Ubuntu packages with "hfs" in the title.

I've formatted an external drive on OS X (tried both ppc and intel) and the drive automounts under /media, but it is read-only.

If I manually mount it using the "mount" command, I get the same result at any mount point.

Then I tried this:

```

zsh-% sudo hpmount /dev/sdd3 /mnt/tmp
*** Warning: You are about to open '/dev/sdd3' for writing ***
*** Do you really want to do that ? (y/n) ***
y
hpmount: /dev/sdd3: This is not a HFS+ volume (Unknown error 4294967295)
zsh-% 


```

Mounting fails, and the filesystem on the drive becomes corrupted.  It is no longer recognized by either Ubuntu or my Mac OS X machines.

Fortunately, I had no data on it (one test file).

I can mount the drive on my Mac and export the thing via NFS to the linux machine, but I would rather not do it that way.

Any other optinons?

All I want is a drive that is r/w for both machines.

---

### Post by ronocdh on 2007-07-10
You would probably have much better luck if you posted something like this in the Apple Intel forum. ;) Try formating an HFS+ drive in OS X, but make sure you disable journaling. This will enable Ubuntu to write to it as well as read from it. On top of that, remember in OS X to set the permissions such that "others" can r/w. If you forget, you can change them in Ubuntu as root, but rebooting to OS X will change them back, which is annoying. HTH!

---

### Post by wgscott on 2007-07-10
Actually, if all that is required (apart from permissions) is to turn off disk journaling, you just answered my question.  Thanks!!

This would also explain my other observation, that a similarly-formatted disk I created a few years ago does work. (This one was formatted before Apple implemented journaling).

[I didn't post to the Mac intel forum because this is just a question about a disk that was formatted using a Mac OS X machine (most recently ppc, although I did try both), but the problem is with respect to an (X)ubuntu i386 PC operating system, not an Ubuntu OS running on an intel Mac.]

Edit:  for the benefit of anyone else reading this, you can turn off disk journaling (while on OS X, not Ubuntu) like this:

```
sudo /usr/sbin/diskutil disableJournal /Volumes/MyDisk 
```

and turn it back on (while on OS X, not Ubuntu)  like this:

```
sudo /usr/sbin/diskutil enableJournal /Volumes/MyDisk 
```

---

### Post by wgscott on 2007-07-10
Just to clarify, turning off disk journaling was indeed the problem.  (Even with non-relaxed permissions, "sudo touch foo" allows me to create a file).

Again, many thanks.

---

