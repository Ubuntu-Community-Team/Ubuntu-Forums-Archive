---
title: "want to put windows back on a 10G partition"
date: 2007-09-09
forum: General Help
---

### Post by yuvlevental on 2007-09-09
I really like ubuntu, but there are some windows apps I really miss. I want to put windows xp back on a 10G partition. I want to use the recovery CD that came w/my laptop. How do I do this?

Thanks,
Yuvlevental

---

### Post by yuvlevental on 2007-09-09
anyone?

---

### Post by Arwen on 2007-09-09
I really think 10GB is small space for XP,I once installed it in 13GB and was too slow.You only have ubuntu now right?
What are the apps?You didn't find any linux equivalent?

---

### Post by yuvlevental on 2007-09-09
i have magix music maker, and a couple games, i couldn't find a good music-making alternative that is native/runs under wine, and i really like the games. I don't think it will be slow, as I have 1.1 G of RAM, so anyway, how do u do it?

---

### Post by Arwen on 2007-09-09
I wish I could help you more but the only thing I can tell you is that with the recovery cd that came with my ACER laptop,I can only "recover" XP,that is to say "fix a corrupted installation" not to install XP from the beginning.Maybe you should check out your laptop's manufacturer site for a guide or sth.

---

### Post by yuvlevental on 2007-09-09
mine can do a complete reinstallation with all the drivers and such. So i want to create 10GB of space for windows, and create a dual-boot menu. How do I do it?

Thanks,
Yuvlevental

---

### Post by merlinus on 2007-09-09
Maybe something here will help:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by Arwen on 2007-09-09
You'll need [Gparted Live CD]("http://gparted.sourceforge.net/") ro resize ubuntu partition,then you format in NTFS and primary partition the unallocated space that's left,you install XP by the CD you have and then you'll probably have to reinstall GRUB cause windows' bootmanager writes on top of it and you won't be apble to log in ubuntu.Of course it would be more simple if you deleted ubuntu and install XP first and then ubuntu but it's not that you want I suppose.Make sure you have backed up your data.
**I strongly recommend you waited for other suggestions,I haven't tried anything like that before.


#I didn't see the link earlier,it's exactly what you need!

---

### Post by atlfalcons866 on 2007-09-09
install your windows on virtualbox

---

### Post by HermanAB on 2007-09-09
If you try to make a dual boot system then you have to install Windows FIRST, since if you install Windows second, it will eat your boot loader and then you won't be able to boot Linux anymore.

As a previous poster suggested, install Virtualbox/Qemu/VMware and install Windoze in that.  That way, you can run Windows in a window concurrently with Linux.  Dual booting is rather yesteryear.  Virtualization is the future.

Cheers,

H

---

### Post by merlinus on 2007-09-09
If you use the link I provided in my earlier post, you will be able to install windows after linux, and then easily reinstall grub.

Not all apps will run in a vm.

---

