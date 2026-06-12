---
title: "External Hard drive corrupted?"
date: 2007-04-06
forum: General Help
---

### Post by kewldude606 on 2007-04-06
I'm running Dapper right now and was copying some files off of a USB hard drive.  I wanted to plug the hard drive into another USB port in hopes of the transfer going faster so I did a Control-C on the copy in the terminal window and got the standard prompt again.  Then I went to the desktop, right clicked on the drive, and hit eject.  When that completed, I unplugged the drive and plugged it into a different port.

Now, when it comes up in Nautilus, all of the file names are seemingly random unicode characters and I can't even get to most of my files.

What should I do to get my data back?  Is it possible to do so?

Thanks,
Dan

---

### Post by kidders on 2007-04-07
Hi there,

This is highly unusual ... especially since, in Linux, copying really means copying (ie there shouldn't be any writing going on). :-(

If this happened to me, the very first thing I would do is check my system logs for errors. It is possible that some sort of (relatively serious) problem was triggered by something innocent you did. If so, the messages will help to get an idea of what went wrong, and whether there is a flaw in any part of your operating system.

In the meantime, it's important not to try to write to your device. Only attempt to mount it in read only mode, to avoid causing any further damage. Ideally (assuming it's small enough) you would take a disk dump right away, and then run a recovery tool (eg **fsck**) on it.

---

