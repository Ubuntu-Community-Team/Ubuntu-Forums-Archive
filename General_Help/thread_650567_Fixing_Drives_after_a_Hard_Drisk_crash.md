---
title: "Fixing Drives after a Hard Drisk crash"
date: 2007-12-26
forum: General Help
---

### Post by tpdasf on 2007-12-26
I have 2 hard drives in this computer

1: 80GB drive with Ubuntu Feisty Fawn on it
2: 120GB with Windows XP

It was set up so that GRUB would start and I would get to choose whether to boot into Ubuntu or Windows.

Recently, after the computer being off for a week, I booted up and got a Disk read error when trying to boot into Ubuntu. I still see the GRUB menu though, so booting into Windows works fine.

Now, I want to remove the Linux Drive to replace it later, but meanwhile use the Windows drive.

The problem is, When I remove the Linux drive, I can't boot into the windows one, I always get an error when trying to boot (I guess it requires GRUB?)

So my question is, how do I get the Windows drive to boot without having the old Linux Drive connected?

Thanks

---

### Post by Ocxic on 2007-12-26
remove your drive, then place your windows install disk into your computer and boot into recovery mode and run "fixmbr" that will replace grub with the windows boot loader, and you'll be able to boot without the Ubuntu drive

---

