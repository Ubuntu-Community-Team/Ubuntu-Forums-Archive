---
title: "move root partition, is it safe?"
date: 2019-01-10
forum: General Help
---

### Post by matrooswolf on 2019-01-10
Hi,

I have a dual boot installation and have to give more space to Windows (sdb3) who is eating space up. This is my setup (see picture).
[img]https://i.imgur.com/knUuMt8.png[/img]

Is it safe to shrink the Ubuntu root partition (sdb5) from the left, so as to free space between Windows 10 (sdb3) and Ubuntu 18.04 (sdb5) ? And then increase the Windows partition. It probably is, but I don't want to mess things up, so I need some reassurance ;) I never use Windows, that's why I didn't give it much space...

And is it safe to do this with GParted from within Ubuntu 18.04 (fully updated)? Or should I do it from a live cd?

And does anybody know what that sdb4 Windows partition is doing at the end? I think Windows needs it, but I don't know why.

(Yes, it's a very small ssd disk, 128GB, courtesy of my work, which wouldn't pay for a bigger one.)

Any advice is welcome

---

### Post by CatKiller on 2019-01-10
> **matrooswolf said:**
> Is it safe to shrink the Ubuntu root partition (sdb5) from the left, so as to free space between Windows 10 (sdb3) and Ubuntu 18.04 (sdb5) ?

When you try it, you'll find that you can't actually do it that way. What you can do is shrink the partition from the right and then move it to the right.

> And is it safe to do this with GParted from within Ubuntu 18.04 (fully updated)? Or should I do it from a live cd?

Again, when you try it you'll find that you can't. You can't change a partition that's mounted, and if you unmount it you can't run the programs off it. It will work from the live cd.

Moving Linux partitions around is generally fine. Make backups anyway. 

> And does anybody know what that sdb4 Windows partition is doing at the end? I think Windows needs it, but I don't know why.

My guess would be a recovery image to nuke the hard drive and install a fresh copy of Windows.

---

### Post by matrooswolf on 2019-01-10
Hi CatKiller,
Thank you. That clears things up.
> When you try it, you'll find that you can't actually do it that way. What you can do is shrink the partition from the right and then move it to the right.
I didn't know that. So thanks.
> My guess would be a recovery image to nuke the hard drive and install a fresh copy of Windows. 
I thought so too, but there's nothing on it, just a log file of 18MB. Still, I'm not going to mess with it. I don't trust Windows ;)

---

