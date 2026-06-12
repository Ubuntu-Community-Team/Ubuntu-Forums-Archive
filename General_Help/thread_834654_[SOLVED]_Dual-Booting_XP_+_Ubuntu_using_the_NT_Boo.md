---
title: "[SOLVED] Dual-Booting XP + Ubuntu using the NT Bootloader"
date: 2008-06-19
forum: General Help
---

### Post by Emarian on 2008-06-19
Well, I was wanting to format my entire disk, install Ubuntu, then install XP and boot Ubuntu using XP's bootloader.

The reasons I want to do this are simple:
1. I'm a perfectionist. I understand that it is easier to install XP first, but I HATE how you can view the older versions of Ubuntu and the recovery versions in the GRUB bootloader, and you have to see this menu to select Windows. I'd rather use the XP Bootloader to run Ubuntu so that I never see GRUB's menu because Ubuntu never detected XP.
2. I rather like the simplicity of XP's bootloader.
3. I love Ubuntu and I understand that it far exceeds XP, but I'm very familiar with the XP boot.ini file and I find it easier to work with.
4. I need XP for gaming and for applications that WINE cannot run.

I was wondering if there is a tutorial for this. I remember finding one from WAY back, but I can't find it again. I've googled so many different things, but it eludes me.

It was something along the lines of backing up GRUB as ubuntu.bin and then inserting ubuntu.bin into the NT Bootloader.

I was wondering if someone could point me to this tut? Or something similar?

EDIT:
I was wondering if this is what I am talking about? I think I found it..

[http://ubuntuforums.org/showpost.php?p=1382776&postcount=5](http://ubuntuforums.org/showpost.php?p=1382776&postcount=5)
I HIGHLY appreciate the help. :D

---

### Post by logos34 on 2008-06-19
> **Emarian said:**
> Well, I was wanting to format my entire disk, install Ubuntu, then install XP and boot Ubuntu using XP's bootloader.

The reasons I want to do this are simple:
1. I'm a perfectionist. I understand that it is easier to install XP first, but I HATE how you can view the older versions of Ubuntu and the recovery versions in the GRUB bootloader, and you have to see this menu to select Windows. I'd rather use the XP Bootloader to run Ubuntu so that I never see GRUB's menu because Ubuntu never detected XP.
2. I rather like the simplicity of XP's bootloader...

Probably nothing anyone says will change your mind, but all of that is easily fixed by [URL="> **Emarian said:**
> Well, I was wanting to format my entire disk, install Ubuntu, then install XP and boot Ubuntu using XP's bootloader.

The reasons I want to do this are simple:
1. I'm a perfectionist. I understand that it is easier to install XP first, but I HATE how you can view the older versions of Ubuntu and the recovery versions in the GRUB bootloader, and you have to see this menu to select Windows. I'd rather use the XP Bootloader to run Ubuntu so that I never see GRUB's menu because Ubuntu never detected XP.
2. I rather like the simplicity of XP's bootloader...

Probably nothing anyone says will change your mind, but all of that is easily fixed by [customizing grub]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") config file /boot/grub/menu.lst.  You can hide it, etc.


> EDIT:
I was wondering if this is what I am talking about? I think I found it..

[http://ubuntuforums.org/showpost.php?p=1382776&postcount=5](http://ubuntuforums.org/showpost.php?p=1382776&postcount=5)
I HIGHLY appreciate the help. :D

yes that's it

funny, I just got done using that command (variation of it, at least) for another linux distro

[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

### Post by Emarian on 2008-06-19
Actually, that looks very interesting. I've scanned the parts about customizing GRUB, and I have another question. I think I'm going to give customizing GRUB a shot so that on the first menu, it says:

Ubuntu Linux
Windows XP Professional

Which is exactly the look I was trying to achieve with the XP bootloader. However, if I could do it with GRUB, it would make me feel more Linux-complete about my computer.

So, I was scanning it, and I have a question.

I see in your example of the menu.lst file, it has the windows entries like this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

I was wondering if I commented out this bit like this:

```
[CODE]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root
```

If it would directly show the XP boot option instead of having to select Other Operating Systems and THEN XP.

Basically, I want to be able to just select XP from the root of the GRUB menu instead of selecting other operating systems and then XP.

Is that how I would achieve that?

Thanks again for your help thus far.

---

### Post by logos34 on 2008-06-19
yes, that's how to do it.  

it's all [here]("http://users.bigpond.net.au/hermanzone/p15.htm") (>'customizing menu.lst')

---

### Post by Emarian on 2008-06-19
Thank you. I couldn't find it, so I had to ask.

I appreciate your help, and I will definitely attempt to configure GRUB so that I can use it instead of the NT Bootloader. (Besides, I hear bad things about it all the time anyways.) Now I can hand Linux and GRUB nearly full control. \\:D/

By the way, did you create that guide? If so, very well done. :biggrin:

*Thanked you*

---

### Post by logos34 on 2008-06-19
> **Emarian said:**
> 
By the way, did you create that guide?

yeah, right, I wish...

---

