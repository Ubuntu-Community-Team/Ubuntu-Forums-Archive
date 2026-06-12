---
title: "What is the choice to simple workstation for video editing ? BTRFS or Reiser4 ?"
date: 2020-08-08
forum: General Help
---

### Post by aug7744 on 2020-08-08
For an system where will be used for internet, video editing and few others simple softwares what file system is the choice for automatic file compression ? BTRFS or Reiser4 ?
Thanks very much for your reply.

---

### Post by HermanAB on 2020-08-08
XFS was designed for graphical work stations and it still good for that.  However, you will find that the effect of the file system on performance is extremely minimal due to faster hardware these days.  The available RAM is the real limiting factor.

---

### Post by aug7744 on 2020-08-08
Thanks very much for that detail that remember the powerful SGI computers.
An amazing age where was an dream to use super computer only available in graphics workstations.
Well I wait to use file compression and avoid journaling.

---

### Post by SeijiSensei on 2020-08-08
My experience with XFS was that if the machine lost power for any reason, I would lose data.  I just ext4 for everything.

---

### Post by kneutron on 2020-08-08
--If your experience with XFS was more than ~2 years ago, you might want to give it another chance. Don't have a REF, but I saw a couple of months ago that they submitted a code fix for that issue.  Coincidentally - just last night, I restored an ext4 root **fsarchiver** backup to xfs on the fly (see ' man fsarchiver ') and the *only* change that was needed was ext4 -> xfs in /etc/fstab. Booted right up, so if you want to convert a system or VM to test it, that's the easiest way I know of.  Was able to restore it from another distro in a triple-boot environment, but it's also doable from System Rescue CD. Have a super grub disk ISO handy just in case.

--At any rate, we've gone slightly OT -- submitter's original question was "[SIZE=4]what file system is the choice for automatic file compression[/SIZE]" and XFS currently does not support that**.  IMHO if you want reliable automatic file compression, use **ZFS** with lz4.  Setting up a single-disk or mirror ZFS is easy, so I won't get into that.

** [https://en.wikipedia.org/wiki/XFS#Features](https://en.wikipedia.org/wiki/XFS#Features)

---

### Post by SeijiSensei on 2020-08-08
> **kneutron said:**
> --If your experience with XFS was more than ~2 years ago, you might want to give it another chance. 
Yes it was longer than that. I don't really care to change at this point. As I said ext4 is more than sufficient for my needs.

---

### Post by aug7744 on 2020-08-13
Thanks for all replies :)

---

