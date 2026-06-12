---
title: "F6 Options"
date: 2012-12-15
forum: General Help
---

### Post by anon_private on 2012-12-15
It usually takes a few attempts before I can successfully boot the Lubuntu 12.04 LiveCD.

Would disabling nacpi, noapic, nolapic, or nodmraid be likely to help?

In addition, I someetimes get the mouse pointer freezing and sometimes everything freezes, again would disabling any of these options be likely to help?

Thanks

---

### Post by ibjsb4 on 2012-12-15
It's the live CD, you can try it.  Also can try nomodeset.  Could be an issue with your video driver.

---

### Post by anon_private on 2012-12-15
> **ibjsb4 said:**
> It's the live CD, you can try it.  Also can try nomodeset.  Could be an issue with your video driver.

Thank you.

What does nomodeset do?

Best wishes.

A

Ps. I use Nvidia Geforce 730 turboforce 256MB dvi/vga output with fxs-video output. Is there an issue with this card?

---

### Post by ibjsb4 on 2012-12-16
nomodeset and others

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Bucky Ball on 2012-12-16
Disabling those? They shouldn't be enabled unless you have added them to the kernel line.

When you hit the menu list after boot go to the kernel you want to boot, hit 'e' to edit it, find the line that ends in 'splash' or 'quiet splash' or something like that and add 'nomodset' to the end of that line after a space.

Follow instruction at bottom of page to save and exit. If that works, let us know and we can make it permanent (this fix won't stick on reboot).

---

### Post by anon_private on 2012-12-16
> **Bucky Ball said:**
> Disabling those? They shouldn't be enabled unless you have added them to the kernel line.

When you hit the menu list after boot go to the kernel you want to boot, hit 'e' to edit it, find the line that ends in 'splash' or 'quiet splash' or something like that and add 'nomodset' to the end of that line after a space.

Follow instruction at bottom of page to save and exit. If that works, let us know and we can make it permanent (this fix won't stick on reboot).


I think that the nomodset should be placed before -- on the line

---

### Post by Bucky Ball on 2012-12-16
> **anon_private said:**
> I think that the nomodset should be placed before -- on the line

Nope. On the kernel line that ends with 'quiet splash', 'quiet' or just 'splash'. That's it. 

If it works it then needs to be added, in the same position, to the grub/default file. ;)

---

### Post by anon_private on 2012-12-17
> **Bucky Ball said:**
> Nope. On the kernel line that ends with 'quiet splash', 'quiet' or just 'splash'. That's it. 

If it works it then needs to be added, in the same position, to the grub/default file. ;)

The line ends: quiet splash --

Surely -- marks the end of the line, hence nomodset should be placed thus: quiet splash nomodset --

---

### Post by ibjsb4 on 2012-12-17
This is the way my 12o4 looks

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""

I would change:
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"

And update grub

```
sudo update-grub
```

Bottom of post #1

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by anon_private on 2012-12-18
I don't think I have this GRUB folder.

I am runnung LUBUNTU from a pendrive

Thanks

---

### Post by ibjsb4 on 2012-12-18
> **anon_private said:**
> I don't think I have this GRUB folder

/etc/default/grub ?

---

### Post by anon_private on 2012-12-18
Thank you.

Yes, it is there, and it is the same as your original file.

I found the revelation interesting when I used /

I saw all the folders and wondered what they are used for. Is there a tutorial around.

Best wishes.

A

Ps. I would like to understand this system a lot better than I do.

---

### Post by ibjsb4 on 2012-12-18
For how to use the terminal this one is excellent.

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+how+to&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+how+to&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Is this solved?

---

### Post by Bucky Ball on 2012-12-18
> **anon_private said:**
> ... hence nomodset should be placed thus: quiet splash nomodset

Yep, exactly what I'm saying ...

---

### Post by Bucky Ball on 2012-12-18
> **ibjsb4 said:**
> /etc/default/grub ?

You don't need to go there yet. You want to see if it works first by adding to the end of the line described at boot first before changing that file. ;)

---

