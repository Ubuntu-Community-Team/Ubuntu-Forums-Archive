---
title: "Target filesystem doesn't have /sbin/init"
date: 2006-11-12
forum: General Help
---

### Post by Rette on 2006-11-12
A couple days ago my GRUB decided to stop working. I dual boot windows XP, and my dad tried booting "Windows 2000/NT/XP"(I'm not even sure why that's there) rather than "Windows XP Media Center" that he usually uses. Grub started giving my a cryptic "error 17", and didn't even let me get to the GRUB menu to select an OS to boot.

So, I decided to reinstall GRUB. Rather than doing it the smart way, I went the lazy way and installed ubuntu on an extra partition I had. Now GRUB was working, and so was windows. But, when I try to boot Ubuntu, I get the following error;

```
mount: Mounting /dev/hda4 on /root failed: No such device

//This repeats for several devices

mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

After this, I get a command line of some sort.

I'd rather not have to reinstall ubuntu, so I was hoping someone would have some idea as to what I've done. I should also mention, I do have access to all the files on my ubuntu partition (through the second ubuntu install I did to reinstall GRUB).

---

