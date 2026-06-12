---
title: "dual booting gentoo"
date: 2007-06-17
forum: General Help
---

### Post by Tyke91 on 2007-06-17
now that i'm comfortable in Ubuntu (not expert, but i can find my way around and I'm not scared of it) I'd like to try out Gentoo to see what the difference is for myself. I'm thinking of working on ubuntu and messing around with gentoo. anyway, now that my windows is completely dead and gone (accidentally wiped it and i dont feel like reinstalling) I'm going to try.


are there any installation issues that i need to watch out for with gentoo? will grub automatically reconfigure its self? will it need another swap file? etc...

---

### Post by confused57 on 2007-06-17
> **Tyke91 said:**
> now that i'm comfortable in Ubuntu (not expert, but i can find my way around and I'm not scared of it) I'd like to try out Gentoo to see what the difference is for myself. I'm thinking of working on ubuntu and messing around with gentoo. anyway, now that my windows is completely dead and gone (accidentally wiped it and i dont feel like reinstalling) I'm going to try.


are there any installation issues that i need to watch out for with gentoo? will grub automatically reconfigure its self? will it need another swap file? etc...
Here's how to boot multiple Linux OS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You can always reinstall Ubuntu's grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I haven't installed Gentoo with the 2007 live cd, so I'm not sure if there is an option of where to install grub...I've installed Gentoo a couple of times with the mini-cd, which requires manually creating the grub.conf entries and grub's IPL could be installed to the mbr or to the root partition.

---

### Post by Tyke91 on 2007-06-17
i've just done it, and apparently, gentoo installs grub, but only gives you the gentoo option. im going to try to reconfigure since my gentoo install seems to be going haywire.

---

