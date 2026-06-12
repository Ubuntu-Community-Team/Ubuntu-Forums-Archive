---
title: "Removing Windows from a dual-boot setup"
date: 2008-05-30
forum: General Help
---

### Post by dorkdork777 on 2008-05-30
I've been dual-booting for quite some time now, and I've decided that to make more room for my Ubuntu partitions, I should do a fresh reinstall of Windows XP to easily get rid of the crap I don't use on it.

I'm aware of most of the steps I'll need to take to get that far, like reinstalling GRUB to the MBR post-install, but my Windows partition is flagged as 'boot' - does that mean anything? Will I need to set another partition as 'boot' before I can proceed with the wipe-and-reinstall? Or will it be fine anyway?

Thanks a lot! :)

EDIT: Just found a post saying WXP makes the install partition 'boot' automatically. I'm going to try it now, then mark this as 'solved' if it's OK.

---

### Post by WRDN on 2008-05-30
If you reinstall Windows XP on the same partition, I dont think you need to worry about boot flags.

---

### Post by geo909 on 2008-05-30
Just one thing:

I would strongly advise you to use a program like [clonezilla]("http://www.clonezilla.org/") live to backup your disk first. In case there's a problem you can restore it like it was before and try again. It's really easy and fast, you should give it a try. You can ask if you need any help with this.

Also, you may find [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") helpful for reinstalling grub .

---

