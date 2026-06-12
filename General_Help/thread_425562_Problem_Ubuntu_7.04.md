---
title: "Problem Ubuntu 7.04"
date: 2007-04-27
forum: General Help
---

### Post by Mks1001 on 2007-04-27
Hello.

I installed Ubuntu for about two days ago now, and I love it. But I have a problem. The first time (after installation) I had to install some updates, and I installed a driver for my graphics card (ATI x550). After this i had to reboot.

I ran Ubuntu as usual, but when it was almost done loading, the screen suddenly go black, no signal...
After this point I can't do anything else than rebooting and starting XP again (and ask for help).

Please help me!

---

### Post by taurus on 2007-04-27
Boot into recovery mode from GRUB menu and reconfigure your X again, if you don't have a backup copy of /etc/X11/xorg.conf.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Mks1001 on 2007-04-28
Well Thanks.

I did as you said, but as it was a hell of a lot of questions to answer, I probably did not answer correctly. Because when I tried to start desktop effects, beryl and other stuff, it just wouldnt do it.

Thats why i will try to reinstall it. How do I uninstall it anyway? (Will reinstall form LiveCD)

---

