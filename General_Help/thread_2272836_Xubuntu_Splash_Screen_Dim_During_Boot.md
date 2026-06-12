---
title: "Xubuntu Splash Screen Dim During Boot?"
date: 2015-04-08
forum: General Help
---

### Post by ProjectKITT on 2015-04-08
Hi all,

I'm running Xubuntu 14.10 on an Acer Aspire D270, and for some reason the Xubuntu splash screen (after the GRUB menu) is extremely dim. I can brighten it with the function keys, and it changes to full brightness at about the last fraction of a second that the splash screen is visible. Any ideas about how to correct this? I would love for my Xubuntu to look polished and clean :) 

Thank you in advance!
-ProjectKITT

---

### Post by Keith_Helms on 2015-04-09
There are a lot of threads about backlight problems on various Acer laptops.   Take a look at this one and see if it helps:

[http://askubuntu.com/questions/195011/how-do-i-adjust-the-screen-brightness-on-an-acer-aspire-one-d270](http://askubuntu.com/questions/195011/how-do-i-adjust-the-screen-brightness-on-an-acer-aspire-one-d270)

---

### Post by ProjectKITT on 2015-04-09
> **Keith_Helms said:**
> There are a lot of threads about backlight problems on various Acer laptops.   Take a look at this one and see if it helps:

[http://askubuntu.com/questions/195011/how-do-i-adjust-the-screen-brightness-on-an-acer-aspire-one-d270](http://askubuntu.com/questions/195011/how-do-i-adjust-the-screen-brightness-on-an-acer-aspire-one-d270)

Hi Keith,

Thank you for the reply. Unfortunately that is not the problem I'm having (my FN keys work fine during and after boot). I have already looked all over Google for a solution and only found one thread that described the same problem: [http://ubuntuforums.org/showthread.php?t=2139456](http://ubuntuforums.org/showthread.php?t=2139456), but there was no solution.

Basically, the screen brightness works as it should with the exception of it being extremely dim during the splash screen. I imagine there would be some setting that controls the default value before the OS loads, but I know nothing about it.

---

### Post by Keith_Helms on 2015-04-09
You could try explicitly setting the brightness to some level at startup.

Edit the following file
```
gksudo gedit /etc/rc.local
```

and add a line to explicitly set the brightness
```
echo X > /sys/class/backlight/intel_backlight/brightness
```

Where X is a number.  This assumes your system has an intel backlight.   See what directory(ies) are under /sys/class/backlight.  Under that directory should be a field named "max_brightness".  Cat that to see what range of values you could use for X.   On my system, max brightness is 1054, so I could set X to between 0 (totally dark) and 1054.

---

### Post by ProjectKITT on 2015-04-09
Awesome, that sounds like it would be a great solution. So I checked the backlight folder, and there are two directories - acpi0 (max brightness 9) and psb-bl (max brightness 100). I have 9 brightness settings as I try it now, so I'm assuming acpi0 is the one it's using. Would it use the other during boot, or what else would it be for?

Thanks again, I'll let you know how it works!
-ProjectKITT

---

### Post by Keith_Helms on 2015-04-09
psb-bl might be related to the chipset or video card.  Try setting the  brightness under the acpi directory.  If that doesn't work for some  reason, you can try this procedure and then attempt to set the brightness under psb-bl.

```
1. gksudo gedit /etc/default/grub
2. Find the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add  acpi_backlight=vendor in the quotes.   There are other options that might affect the backlight such as video.use_native_backlight=1 but I'd  start with the first one.
3. Save the file and run sudo update-grub and then reboot.
```

Configuring  the backlight should be simple, but there seems to be many options in  many different places that can sometimes affect it.

---

### Post by ProjectKITT on 2015-04-11
Ah, no luck with acpi0 but I'll try your second suggestion. It's funny that there are so many things that could affect it!

---

### Post by Keith_Helms on 2015-04-12
My system has hit a Linux bug where the backlight function keys only work about two-thirds of the time after I boot.  It seems to be related to ACPI.  Fortunately the brightness applet on the task bar always works.  I tried multiple different suggestions on various postings and none of them fixed it completely.  Hopefully your situation is different.

---

### Post by ProjectKITT on 2015-04-22
Yeah, I don't have any problems with the function keys (in fact, those are the only things that *do* always work) but I updated the GRUB like your second suggestion and hopefully that will work. Is the FN key problem a common bug, or is yours different from most?

---

### Post by Keith_Helms on 2015-04-23
I don't know how common it is.   There are a lot of postings about various problems with backlight controls.  I have seen a couple of bug threads on the launchpad site that seem to be the exact same problem I'm having, where the Fn-f8 and Fn-f9 keys on a Sager/Clevo laptop do not (always) work.   One of the threads (#806032) claims the problem was fixed back in 2013.  The other thread (#1218547) seems to have just died out in Feb. of last year without any fix reported.   Since I discovered how to add the brightness app to the Xubuntu taskbar and that always seems to work I haven't pursued a fix to the hotkey problem any further.

---

### Post by ProjectKITT on 2015-04-24
No luck with acpi_backlight=vendor; I'll probably just search Google again and see what I can find but the curious thing was that my FN stopped working when that added (the brightness message thing would show up, but the setting would not actually change). I removed it and now the FN keys are working again. That may not be your problem, and I know you said you aren't really pursuing it anymore, but I thought I'd mention it because I found it curious.

---

### Post by ProjectKITT on 2015-04-30
Solved! Coincidentally enough, the solution to a different problem corrected it (no splash screen): [http://ubuntuforums.org/showthread.php?t=2271368&p=13256374#post13256374](http://ubuntuforums.org/showthread.php?t=2271368&p=13256374#post13256374)

Simply add this line to the GRUB:
```
GRUB_GFXPAYLOAD_LINUX=auto
```

I may or may not re-comment the GRUB_GXFMODE=1024x480 line (I uncommented it to get the splash screen to show up in the first place), just to see of only the GFXPAYLOAD line is needed. But at least now it works :D

---

