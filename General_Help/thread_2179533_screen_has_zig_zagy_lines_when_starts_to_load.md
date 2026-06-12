---
title: "screen has zig zagy lines when starts to load"
date: 2013-10-08
forum: General Help
---

### Post by kiddcanuk on 2013-10-08
I install Kubuntu 13.0.4. Login screen comes on. Put in pass and it starts to load. Screen goes black, comes back on. Continues to load for about 5 seconds and freezes with lines. I was wondering if it is the driver for the graphics that it does not like? I am using a on board graphics. Here is my MOB: ASUS M2N-MX SE. CPU: AMD Athlon 64 X2 Dual Core. RAM 2GB.

If you need more info please just let me know.

Thanks in advance. O:)

---

### Post by VMC on 2013-10-08
Yes, its the driver. What video chip do you have. I get that display on first boot only. So I found a way around it.
When I first boot Kubuntu, I add '*nomodeset*' at the end of the '*linux*' line. After that I remove the '*nomodeset*' line and it boots up normal.

edit: OK, this is your onboard display '[COLOR=#333333][FONT=Arial]NVIDIA GeForce 6100 + nForce 430', which is very similar to mine.[/FONT][/COLOR]

---

### Post by kiddcanuk on 2013-10-09
Ok,
I am a Noob so you will have to tell step by step on how to do this. If you could please. :)

---

### Post by VMC on 2013-10-10
When you see the grub menu and the correct Kubuntu that you usually boot from. Type '**e**' to edit, then using down-arrows go to line that has '**linux**' in the beginning. Go to the end of that line, type a space and then '**nomodeset**', then push **F10**.

After boot, your resulation will be dimished. Then you should be able to reboot normally after that.

---

### Post by kiddcanuk on 2013-10-10
Ok I will give it a shot. I will let you know. Thanks for your help.

---

### Post by kiddcanuk on 2013-10-10
ok update. I did what you said to do and still the same problem. :(

---

### Post by VMC on 2013-10-10
We almost have the same hardware (look at mine below), and that works for me. Although, I haven't tried 13.04 - I don't think. I am using 13.10.
On first boot I always get the distorted video, unless I boot first time using 'nomodeset', then on subsequent boots it works fine.

By the way, when you used 'nomodeset' set, did it appear normal? If not, then you have another issue.

---

### Post by kiddcanuk on 2013-10-10
Are you running on 32Bit or 64Bit? Or does it matter? Maybe I am doing something wrong when I did the nomodeset.

---

### Post by VMC on 2013-10-11
I'm using 64bit. Make sure to use ***nomodeset*** without any accompanying quotes.
Example:
```
linux /vmlinuz root=UUID=477a4b76-aab5-48e8-a21d-44a1cb0af163 ro splash quiet nomodeset
```

---

### Post by kiddcanuk on 2013-10-12
Hi,
ok here is what I am doing. See if I am following the right steps and at the right place.

GNU GRUB Version 2.00-13ubuntu3

Kubuntu GNU/Linux
Advanced options for Kubuntu GNU/Linux
Memory test (memtest86+)
Memory test (memtest86, serial console 115200

Is this where I should be? In this menu.

I hit E key.
I see  setparams `Kubuntu GNU/Linux`    (This is the first line.)
Is it there where I add or make the changes?

---

### Post by VMC on 2013-10-12
Yes, the advance options is for 'recovery'. 
So push the '**e**' key on the first stanza, then using the arrow keys go down until you find the line that starts with '**linux**', then push the '**End**' key on your keyboard, then push the space bar, and finally type '**nomodeset**' without quotes. Then push the '**F10**' key.

---

### Post by kiddcanuk on 2013-10-14
Here is what I see in GRUB:

setparams 'Kubuntu GNU/Linux'

recordfaill
           load_video
           gfxmode $linux_gfx_mode
           insmod gzio
           insmod part_msdos
           insmod ext2
           set root='hd0 ,msdos1 '
           if [ x$feature_platform_search_hint = xy ] ; then
             search --no-floppy --fs-uuid --set=root --hint-bios=hd0 ,ms\
  dos1 --hint-efi=hd0 ,msdos1 --hint-barmetal=achi0 ,msdos1  a2688fc9-3\
  293-4199-8225-c1e635ad511c
               else
                  serach --no-floppy --fs-uuid --set=root a2688fc9-3293-4199\-8225-c1e635ad511c

This is what I see on my screen. Hope this makes it clearer.

---

### Post by VMC on 2013-10-14
Somethings wrong with your output. Copy and paste the contents of "/boot/grub/grub.cfg" .  Please put the results between "[CODE]" tags.

---

### Post by kiddcanuk on 2013-10-15
FYI I finally got it. But don't ask how. I booted up and it worked.(without making any changes) So I when into Applications And then Clicked Additional Drivers. It told me that a driver was not activated. So out of the this choose the first one and activated it. Downloaded the driver and in stalled it and works perfect now. So I would like to thank you for your help and I appreciated very much. Again Thanks!

---

### Post by VMC on 2013-10-15
Was the additional drivers nvidia? I'm guessing so. From a terminal typing 'lsmod|grep nouveau' will tell you.
We have almost identical hardware, but I don't need nvidia drivers. Kubuntu is the only ubuntu product that works
 without nvidia drivers.

If your satisfied with results, please mark as solved at the top of page.

---

### Post by adam-k-wise on 2013-10-16
i have the same problem. I get the message "this driver is active but not in use"

---

