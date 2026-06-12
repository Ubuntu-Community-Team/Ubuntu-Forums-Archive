---
title: "Edgy gets the Grub menu wrong"
date: 2006-12-20
forum: General Help
---

### Post by daz4126 on 2006-12-20
Hi everybody,

I have just done a clean install of edgy today and found that I got an 'Error 17 -  can't mount partition' message, when I tried to boot into my Ubuntu partition on hard drive b from Grub.

I booted into the live CD and had a look at my menu.lst file and the problem was that my Ubuntu partition was listed as hd(0,0) when it should have been hd(1,0) - even though I specified hdb in the installation process.

Changing this had the desired effect of making it work, but when I booted into edgy it ran some updates, some of which were to the kernel. The 'automagic' thing that updates your menu.lst file to reflect these changes put the mistake back in again, so I had to fix it again.

Does anybody know how I can 'tell' Ubuntu that it is actually installed on hd(1,0) and not hd(0,0)?

thanks,

DAZ

---

### Post by maxamillion on 2006-12-20
```
sudo update-grub
```

That should fix the issue, post back if it does not.

---

### Post by daz4126 on 2006-12-20
Thanks for that maxamillion, I won't be able to test until I do an update and automagic does it's stuff, but will let you know if it doesn't work.

thanks again,

DAZ

---

