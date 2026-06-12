---
title: "Brightness keys on old laptop"
date: 2015-05-25
forum: General Help
---

### Post by Skyflier on 2015-05-25
Hello, 
I have seen this problem several times, but I cannot find the right solution for it.

I have a quite old laptop here (from 2007) which is intended to be used by my mother. Windows 7 seems to be a little heavy for it so I decided to change it entirely to a Linux laptop. Here are some brief specs:

Intel Core Duo 2.16Ghz
3 GB of RAM DDR2
Intel Graphics GMA945
120GB HDD

My first choice for a distro was obviously Ubuntu 14.04, because it's an LTS and provides support for 5 years. Since my mother only uses the PC for some web and word processing, it seems to be just fine for her.

Now the system runs fine, except for one issue, brightness keys do not work at all. I found out that reverting to Kernel version 3.13 fixes the problem (Ubuntu 14.04.2 comes with 3.16 out of the box).
I would like to fix the issue for the kernel 3.16 and above because if I want to install a newer version of Ubuntu or other distro in the future, kernel versions will be much higher than 3.13. Brightness does work if I pull the slider from the power settings menu, it's just the hotkeys that don't work.

---

### Post by mörgæs on 2015-05-26
Did you try a live boot of 15.04, in which the kernel is 3.19? If the regression has been reported it could be fixed here.

---

### Post by kerry_s on 2015-05-26
what's the make of the laptop ? other users might be using that exact laptop & know the fix.

personally, i think you should have gone with xubuntu if you wanted it to be/feel faster. ubuntu-mate is another good option, but it doesn't shine till 15.04 & you want to use a lts release, so that's out.

those are both easy to setup to feel like windows, so she would have less of a learning curve.

---

### Post by Skyflier on 2015-05-26
> **mörgæs said:**
> Did you try a live boot of 15.04, in which the kernel is 3.19? If the regression has been reported it could be fixed here.
I did yes, I actually tried several flavours such as Lubuntu and Xubuntu 15.04. The issue still persists.

> **kerry_s said:**
> what's the make of the laptop ? other users might be using that exact laptop & know the fix.

personally, i think you should have gone with xubuntu if you wanted it to be/feel faster. ubuntu-mate is another good option, but it doesn't shine till 15.04 & you want to use a lts release, so that's out.

those are both easy to setup to feel like windows, so she would have less of a learning curve.
It's an HP Notebook 530. In my search for issues, the only thing I see is people reporting a problem with the Broadcom Wireless, my model has an Intel Pro Wireless card so that issue doesn't exist.

As for the flavour, yes I do think I will pick either one of Lubuntu or Xubuntu or even Elementary OS Freya for that note. I just want to find the fix for this brightness issue before picking the right distro to go.

---

### Post by Skyflier on 2015-05-27
I have found some solutions, but I had no luck trying them.

First, I found out that from Kernel 3.16 and on, a parameter was changed related to the backlight, in this case, "vide.use_native_backlight=1" which was 0 until 3.15. I tried setting it back to 0 but had no effect.

Then, I tried adding these two parameters to the GRUB command line:

```
acpi_backlight=vendor
acpi_osi=Linux
```

None of these worked. So I tried another fix, creating a 20-intel.conf file with some contents in it, as described here. Now this solution actually worked in Elementary OS Freya (although not perfectly but the hotkeys started to work). In any other distro, such as Ubuntu or Xubuntu it has no affect.

Now the strange thing here is that I see many people solving this issue by using one if these solutions, but this model has some kind of way around that I can't seem to find out. For now, the only fix is by using Kernel 3.13, works but it's not a viable solution.

---

### Post by kerry_s on 2015-05-27
if it was me, i would just create the shortcuts for those keys using xbacklight.

for example: on my hp mini 210 only xubuntu handles the display key(f4) correctly, but i'm using ubuntu-mate now so i just used a keyboard shortcut to get it to open display.

---

### Post by Skyflier on 2015-05-28
> **kerry_s said:**
> if it was me, i would just create the shortcuts for those keys using xbacklight.

for example: on my hp mini 210 only xubuntu handles the display key(f4) correctly, but i'm using ubuntu-mate now so i just used a keyboard shortcut to get it to open display.
Maybe that's the way around. Thanks for the tip :)

---

### Post by Skyflier on 2015-06-03
Well, just tried today performing the suggestion made by setting a custom shortcut to xbacklight but found a worse problem, the system does not recognize the FN+F5/F6 key combination in kernel 3.16 and up, hence the issue with the brightness. Therefore I cannot even set the shortcuts. 
I'm currently using Linux Mint 17.1 Cinnamon on this laptop, but I tried other distros with different desktops to see if any has a workaround.
This issue is really strange, I have a friend also with an old HP laptop from 2007 which has the exact same issue.

---

### Post by kerry_s on 2015-06-04
> **Skyflier said:**
> Well, just tried today performing the suggestion made by setting a custom shortcut to xbacklight but found a worse problem, the system does not recognize the FN+F5/F6 key combination in kernel 3.16 and up, hence the issue with the brightness. Therefore I cannot even set the shortcuts. 
I'm currently using Linux Mint 17.1 Cinnamon on this laptop, but I tried other distros with different desktops to see if any has a workaround.
This issue is really strange, I have a friend also with an old HP laptop from 2007 which has the exact same issue.

have you tried setting the keyboard layout ?

---

### Post by Skyflier on 2015-06-04
> **kerry_s said:**
> have you tried setting the keyboard layout ?
Well, tried that but with no luck, none of the Hewlett Packard models makes the FN+F5/F6 keys to be mapped.

However in more research, I found that by using the xev -showkey command to see the keycodes, I get this when I press fn+f5/f6

```
keycode 465 inserted
keycode 465 released
```
It shows for both combinations, so it means there is a conflict with these keys being recognized as the same keycode.
I don't know if I'm right but that's how it looks like.

---

### Post by kerry_s on 2015-06-04
check in your bios, on mine it has a option to flip the fn keys. maybe if you flip it it might be detected correctly.
i hope you have that setting. good luck, fingers crossed.

---

### Post by Skyflier on 2015-06-04
It has an option to swap the Fn with the Ctrl key.
Tried it and it maps the Fn key as Ctrl and allows me to set it as Ctrl+F6 and Ctrl+F7

If this is what you mean then it is a good trick.

---

### Post by kerry_s on 2015-06-04
> **Skyflier said:**
> It has an option to swap the Fn with the Ctrl key.
Tried it and it maps the Fn key as Ctrl and allows me to set it as Ctrl+F6 and Ctrl+F7

If this is what you mean then it is a good trick.

hmm, not exactly how mine works. on mine if i enable then i have to press fn to access the media(?) keys, disabled puts the f1->f12 as the main keys. so for example: i can just press alt+f2 to get the run command, instead of alt+fn+f2

oh well

---

### Post by Skyflier on 2015-06-04
> **kerry_s said:**
> hmm, not exactly how mine works. on mine if i enable then i have to press fn to access the media(?) keys, disabled puts the f1->f12 as the main keys. so for example: i can just press alt+f2 to get the run command, instead of alt+fn+f2

oh well
My current laptop from 2014 has that function, I can change the way media keys work but Linux distros deal well with the way it is (it's also an HP laptop btw).

Well I don't think this issue has a proper fix for it. The laptop is old and I have to stick up to either use kernel version 3.13 or set a Ctrl+F5/F6 shortcut to xbacklight in newer versions. We are only hitting walls with our heads with no real results. Since this laptop is not intended to be used by me it doesn't need to have this issue properly fixed.
Thanks for all the help you gave me and if someone finds a fix I will let you know or someone posts it here.

---

### Post by kerry_s on 2015-06-04
if it's not for you, just add the brightness applet. :)
makes it very easy to see & adjust.

personally, i set mine & don't move it after that. i put it on 50% on ac, an auto adjust on battery.

---

### Post by stanleyp2 on 2015-06-10
[COLOR=#000000][FONT=Times New Roman]P75-A:~$ sudo dd if=/dev/tty of=/sys/class/backlight/intel_backlight/brightness 

2000

<ctrl><d>  not visible

0+1 records in

0+1 records out

5 bytes (5 B) copied, 4.88619 s, 0.0 kB/s
brightness on *my* ubuntu 15 toshiba haswell varies correctly as required.    



[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][/FONT][/COLOR]

---

### Post by Skyflier on 2015-06-11
I found some partial fix for this problem. If I susped the PC, and then turn it back on, brightness keys then start working.
Really strange but it works, tested in many distros. Weird.

---

