---
title: "Problem Booting Ubuntu"
date: 2007-07-08
forum: General Help
---

### Post by Prima Facie on 2007-07-08
When I turn off my computer and turn it on again, in the loading screen that says Ubuntu, it loads only half way and goes instantly to a black screen and stays there. How can this problem be resolved?

---

### Post by Happy_Man on 2007-07-08
Didn't you already post this a few hours ago? Instead of making a whole new thread, just bump your original.

---

### Post by Prima Facie on 2007-07-08
I really do need some help and am receiving none.

---

### Post by merlinus on 2007-07-08
Your problem may be related to any number of things, especially your video card.

If you post complete details of your hardware and what flavor of ubuntu you are using, if you are dual-booting with windows (and which flavor), if you are using grub, etc., help might be more forthcoming.

-merlin

---

### Post by Prima Facie on 2007-07-08
I am using Ubuntu Feisty. I have a 2.80 GHz Intel processor, a 128mb ATi graphics card, and 512mb of RAM. With regard to the requirements to run Ubuntu, that I think more than satisfies them. I am using Grub, and am not dual-booting with Windows. Windows Vista was my previous OS and I completely wiped it out to install Ubuntu. So what is the problem with this?

---

### Post by Prima Facie on 2007-07-08
Please, I really need help!

---

### Post by merlinus on 2007-07-08
ATI cards and Feisty are problematic, so that is most likely your difficulty.  You will probably need to install the correct drivers, or use the default vesa one until then.

At the grub menu, have you tried safe mode?

-merlin

---

### Post by Prima Facie on 2007-07-08
> **merlinus said:**
> ATI cards and Feisty are problematic, so that is most likely your difficulty.  You will probably need to install the correct drivers, or use the default vesa one until then.

At the grub menu, have you tried safe mode?

-merlin

Recovery mode? What do I do there to resolve the problem? I'm completely new to Ubuntu...

---

### Post by confused57 on 2007-07-08
Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:
```
sudo dpkg-reconfigure xserver-xorg
```

You can probably just go with the default for most screens, but select "vesa" for your video driver...once you've completed reconfiguring your xserver, enter:
```
startx
```
or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

---

### Post by Prima Facie on 2007-07-08
Problem persists.

---

### Post by confused57 on 2007-07-08
Try the "ati" driver...does the live cd boot correctly?  If it does, then open a terminal in the live cd(Applications---Accessories---Terminal), then see what driver the live cd is using:
```
gedit /etc/X11/xorg.conf
```

---

### Post by Prima Facie on 2007-07-08
Uses vesa driver. But I don't think it has anything at all to do with the ATI card.

I've just discovered something. When I turn off the computer and turn it on, I press Esc to access the menu and choose the first option (not recovery mode) and the system boots normally. But if I boot it without doing that, it goes to a black screen... What could it be causing this?

---

### Post by Arrdee on 2007-07-08
Definitely sounds like some sort of GRUB error. If you could, go through the options for boot and find the ones that do *not* work - it sounds like GRUB is by default loading an option that isn't working very well?

---

### Post by confused57 on 2007-07-08
> **Prima Facie said:**
> Uses vesa driver. But I don't think it has anything at all to do with the ATI card.

I've just discovered something. When I turn off the computer and turn it on, I press Esc to access the menu and choose the first option (not recovery mode) and the system boots normally. But if I boot it without doing that, it goes to a black screen... What could it be causing this?
Good find...you're right, it doesn't appear to be an ATI problem and as Arrdee mentioned, it seems to be grub related.
Please post the output of your menu.lst:
```
gedit /boot/grub/menu.lst
```
and
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by Prima Facie on 2007-07-08
Actually, the problem seems to have magically resolved itself... Everything is working well.

---

### Post by confused57 on 2007-07-08
> **Prima Facie said:**
> Actually, the problem seems to have magically resolved itself... Everything is working well.
Glad it's working...go figure.

---

### Post by Prima Facie on 2007-07-09
It's acting up just the same again.

---

### Post by mikeyman on 2007-07-20
I have a similar problem with an HP/Compaq NC8430 laptop with and ATI video card. The issue is that even with the VESA drivers, the boot screen is blank until the GDM or KDM starts up and the proprietary ATI drivers load. (this was accomplished by running in text mode and installing the proper FGLRX ATI drivers).This is just with 7.04...a live cd with the previous version seems to work fine (as does PCLinux). Kinda makes me think it is a kernel thing. Try booting with an older version.

---

