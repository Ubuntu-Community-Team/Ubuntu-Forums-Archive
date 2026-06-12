---
title: "Install a Windows alongside Ubuntu and not the other way"
date: 2007-11-15
forum: General Help
---

### Post by The Joe on 2007-11-15
Well it's a commonly asked question, but for Christmas I've heard talk of an External Hard Drive, I don't really want to wait this long. ^^

Well I have a gaming machine for older games but I would like to dual boot XP on this PC and I've heard of troubles when doing it when Ubuntu is already installed.

So how can I install XP and keep Ubuntu/GRUB and not lose either, of course.

I just thought I'd check first. (I did search, they were all dead topics)

---

### Post by taurus on 2007-11-15
When you install windows, GRUB will be gone from MBR since windows will replace it with it own bootloader.  Therefore, you need to reinstall GRUB if you want to boot Ubuntu again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by The Joe on 2007-11-15
So Ubuntu will be completely untouched? I just need to reinstall GRUB. Got it.

Thanks a lot taurus.

---

