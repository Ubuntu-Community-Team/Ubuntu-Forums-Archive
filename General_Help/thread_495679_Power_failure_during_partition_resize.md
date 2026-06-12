---
title: "Power failure during partition resize"
date: 2007-07-08
forum: General Help
---

### Post by Loffe_ on 2007-07-08
Hi,

I have a little problem. Or I think it might not be so small after all. I'll start from the beginning...

My home partition was to small so I had to resize it. Using the GParted LiveCD it set off with checking the disk( no error) and then growing the filesystem(ext3).

Then it worst of all things happened. There was a power failure :mad: it came from nowhere. When that happend, I said some words that would probably make my post stuck in the forum filters :p

When I started up the LiveCD again it said my partition was unknown.
And I could not mount it with:
```
mount -t ext3 /dev/sda6 /mnt/try
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
missing codepage or other error

```
Doesn't sound to good, does it?
I realize that all my data might be gone ( I got a backup of most stuff ), but from the growfs man page I read this:
> growfs non-destructively expands a mounted or unmounted UNIX
     file system (UFS) to the size of the file system's slice(s).

Growing the filesystem seems to be a relative easy operation, compared to (re)moving files and more.

As you might have guessed my question follow:
Is there any way to save my beloved partition?
Any way recreate the a ext3 fs without writing zeros to the whole partition?

With hope of a more stable power grid,
Loffe

---

### Post by Happy_Man on 2007-07-08
Sorry..... no. I feel your pain, man, but if it can't access it, you're done. Good thing you had everything backed up......

---

### Post by Loffe_ on 2007-07-08
> **Happy_Man said:**
> Sorry..... no. I feel your pain, man, but if it can't access it, you're done. Good thing you had everything backed up......

I must tell you Happy Man that you were wrong. :D

*Testdisk* was the tool I needed and now my partition is back online again. Thanks to Patrick Verner over at GParted forum for the tip: [http://gparted-forum.surf4.info/viewtopic.php?pid=4151#p4151](http://gparted-forum.surf4.info/viewtopic.php?pid=4151#p4151)

:grin::grin::grin:

- Loffe

---

### Post by Happy_Man on 2007-07-09
> **Loffe_ said:**
> I must tell you Happy Man that you were wrong. :D

*Testdisk* was the tool I needed and now my partition is back online again. Thanks to Patrick Verner over at GParted forum for the tip: [http://gparted-forum.surf4.info/viewtopic.php?pid=4151#p4151](http://gparted-forum.surf4.info/viewtopic.php?pid=4151#p4151)

:grin::grin::grin:

- Loffe
Hey, I'm glad to see that you're up and running again. I don't mind if I'm wrong, at least now I'll know about it for future reference, right? :D

---

