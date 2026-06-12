---
title: "Grub question"
date: 2004-11-15
forum: General Help
---

### Post by drunken-wallaby on 2004-11-15
Hi there. I have a question concerning the grub bootmanager. The bootloader is installed in the masterbootrecord of /dev/hda and I currently have installed win2000 and ubuntu on /dev/hda. In the grub bootscreen I can choose the operation system that I want boot into. No problems so far.

However, for various reasons (work related) I have to install win xp. I own a second hard drive /dev/hdb where I want to install windows xp to. I am quite sure that xp overrides the masterbootrecord while installing xp. Is there a way to install windows xp without reinstalling both win 2000 and ubuntu and being able to choose which os I want to boot into at the splash?

Thanks a lot for your help :)

---

### Post by DougC on 2004-11-15
Hi,

I use the the NT bootloader to start grub. Some people may see this as the long way round, but I find it works well.

Have a look at this site for more info:

```
http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html
```

D

---

### Post by az on 2004-11-15
Can you disable hda in your bios?  

Just a shot in the dark here, since I never have used windows XP.

Maybe you can disable your first hard drive, install XP and then re-enable it and boot from grub.  You will have to edit your menu.list in /boot/grub and add an entry for Windows XP.  Perhaps this will work...

---

### Post by wazoo42 on 2004-11-15
I agree with azz, just disable hda during the xp install.  Then edit menu.lst to add xp.  Make sure to use the map option.

---

### Post by drunken-wallaby on 2004-11-15
Hi DougC, azz and wazoo42 :) thanks a lot for your hints and tips. Disabling /dev/hda while installing xp on my second hd should work. I should have thought about this method by myself, anyway. I'll try and post here if it worked or not.

---

