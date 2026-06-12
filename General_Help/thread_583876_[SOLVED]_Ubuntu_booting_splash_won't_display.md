---
title: "[SOLVED] Ubuntu booting splash won't display"
date: 2007-10-20
forum: General Help
---

### Post by What_the_deuce on 2007-10-20
Hi there

More of an irritation than an issue

When booting the familiar orange progress bar won't display. for some odd reason, it will display on a secondary monitor, but then that secondary monitor will fail to work after login

Anyway, thats not the issue. The issue is how do i tell the graphical loading screen to display on my primary monitor, since its a laptop. 

This is in Gusty, BTW

Graphics card is an ATI 200m, if that helps

Thanks very much guys!

---

### Post by avik on 2007-10-20
Something similar is happening to me.  I can't see the loading bar because the refresh rate seems to incorrect.  After some searching, I found that the resolution in my /etc/usplash.conf file is incorrect.  After changing it, ran:

```
sudo dpkg-reconfigure usplash
```

I'm not sure if this works.  I'll get back to you if it does.

---

### Post by xlegendarylinkx on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a known issue, and the remedy, pulled from [this]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930") site: Comment #11:

I was having the same issue with the black screen Dell that has a ati x1400 video card and widescreen lcd (1440x900) and was able to fix the problem using the steps below.

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `*`
(Replace * with the part that shows up in grub menu list i.e. 2.6.17.10-generic)


This should work for ANY brand of computer with an ATI chipset.

---

### Post by avik on 2007-10-20
> **xlegendarylinkx said:**
> This should work for ANY brand of computer with an ATI chipset.

Well, in my case, I have an NVIDIA chipset, but I'll have to see if the above method has any impact when I actually turn off my computer.

---

### Post by What_the_deuce on 2007-10-21
Solved, heres how

```
sudo gedit /etc/usplash.conf
```

Changed the resolution to match my monitor, then

```
sudo dpkg-reconfigure usplash
```

Thanks very much you guys!

---

### Post by avik on 2007-10-21
Confirmed.  Works great for me as well.

---

