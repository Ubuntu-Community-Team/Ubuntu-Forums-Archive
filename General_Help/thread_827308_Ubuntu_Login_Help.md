---
title: "Ubuntu Login Help"
date: 2008-06-12
forum: General Help
---

### Post by mikkenzi on 2008-06-12
Hi all,
I have Installed the new Ubuntu 8. After I installed it, I had 4 different choices of Ubuntu at the boot. Sometime afterwards, I was prompted to update. Now, I have 6 or 8 different options and they are all different versions with different numbers after them... I don't understand much but are these installed simultaneously on my PC? Can I remove some of them or no? What are they?
Thanks for the help!

---

### Post by MaxNorris on 2008-06-12
> **mikkenzi said:**
> Hi all,
I have Installed the new Ubuntu 8. After I installed it, I had 4 different choices of Ubuntu at the boot. Sometime afterwards, I was prompted to update. Now, I have 6 or 8 different options and they are all different versions with different numbers after them... I don't understand much but are these installed simultaneously on my PC? Can I remove some of them or no? What are they?
Thanks for the help!

I'm guessing you're looking at various version of the Kernel, and possibly other OS's you may have installed.  By default, when the kernel gets updated, it just tacks on a new entry on the boot menu.  Comes in handy if you run into troubles and need to boot into a previous version.

You can edit your /boot/grub/menu.lst file and comment out/remove the older entries if you want.  Personally, I just add the "hiddenmenu" option and set a timeout of say three seconds.  Pretty clean on the looks, but still have the option of getting the full menu before it actually boots if the need arises.

---

### Post by mikkenzi on 2008-06-12
So these previous versions are all in my PC? They have not been removed? If I update again and if there is another version, chances are that I will continue getting entries right?
I have only vista and this makes only one options but all the rest are Ubuntu... And I have installed Ubuntu only once. Afterwards, I updated it... but that's about all :) That's why I didn't understand why so many kernel versions...

---

### Post by forestpixie on 2008-06-12
They are different kernels - as they get updated you get new ones added - it is probably best to have a current and previous but you can remove others if you want.

Each one is in fact a pair - one of which is a recovery option.

As they get installed the numbers increase

kernel 2.6.24-19
kernel 2.6.24-18

You can easily remove them - but they aren't doing any damage as they are.

---

### Post by ibuclaw on 2008-06-12
Yeah, I suppose automatically removing the kernels once your done with them should really be a new feature with Ubuntu.

But, ah well. It is simple enough to remove them yourself.

If you want guidance, if you post the outputs of these commands, that would be great:
```
uname -r
```
and
```
dpkg -l | grep linux-image-2.6.24
```

Regards
Iain

---

