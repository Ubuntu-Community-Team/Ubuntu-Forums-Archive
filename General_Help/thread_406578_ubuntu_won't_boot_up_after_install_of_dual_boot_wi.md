---
title: "ubuntu won't boot up after install of dual boot with vista"
date: 2007-04-11
forum: General Help
---

### Post by brokerer on 2007-04-11
After installing vista after ubuntu and doing the instructions from [http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux). Vista works fine but when i try to boot up in ubuntu i get to the splash screen and eventually after waiting forever it takes me to this terminal like busy box v1.1.3 thing... Can anyone help me please?

---

### Post by zvacet on 2007-04-11
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")

---

### Post by brokerer on 2007-04-11
I have my ubuntu partition installed on /dev/sda1 so i followed the grub steps with root (hd0,0) and setup (hd0) and i get the same problem

---

### Post by mikawber on 2007-04-21
> **brokerer said:**
> I have my ubuntu partition installed on /dev/sda1 so i followed the grub steps with root (hd0,0) and setup (hd0) and i get the same problem

I'm having the same exact problem. Anybody know what to do? Please help!

---

### Post by Jump on 2007-04-21
This not be what you want to hear, but what I did to get Feisty and Vista in dual boot was to install vista first and then install Feisty on another partiion. Everything was added to Grub automatically and I was good to go. I did the same for my laptop by installing XP first, then Vista, then Feisty. Now I boot any of the three and I didn't have to do anything special.

---

