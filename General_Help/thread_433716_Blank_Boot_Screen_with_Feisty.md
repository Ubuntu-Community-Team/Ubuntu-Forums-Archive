---
title: "Blank Boot Screen with Feisty"
date: 2007-05-05
forum: General Help
---

### Post by Astronomy_Nick on 2007-05-05
Hi there,

I recently formatted my linux partition and installed Feisty from a Live CD. Previous to this I had run Dapper with no problems. Feisty seems to be working great, all except the boot screen. Under Dapper I had the Ubuntu logo under which the boot processes would scroll through. Now, under Feisty I just get a blank screen (blank rather than no signal) until the user login menu appears. Obviously this doesn't stop me doing anything in Ubuntu, but it is a minor annoyance that I would like to get sorted.

I'm running an Intel Integrated Graphics card (Intel 82845G Graphics) and was wondering whether there was a setting I needed to play with in the xorg.conf file or something like that, though I can't see anything obvious in the manual?

Any advice would be very much appreciated

AN

---

### Post by phidia on 2007-05-05
The usplash "lives" in /usr/lib/usplash see if you have a usplash-artwork.so there.

---

### Post by Astronomy_Nick on 2007-05-05
Thanks for replying Phidia - I do have the file usplash-artwork.so in that folder - any suggestions?

---

### Post by Thingymebob on 2007-05-05
check that the entry for ubuntu in /boot/grub/menu.lst looks something like:
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30 ro quiet **splash**
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
```
The splash argument is what forces the splash screen to display.

You may also need to pass a vga mode to the kernel to force a compatible mode (add vga=??? from the list below)
```

 Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
  -------+--------------------------------------------------------------
 16 bits |            785     788      791
 24 bits |            786     789      792
```

---

### Post by Astronomy_Nick on 2007-05-06
Thanks for the reply Thingymebob. I checked my menu.lst file and the default kernal does have the splash argument in:

```
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e43da836-5aa6-493d-b9c9-65e44ce95bc1 ro quiet splash
```

I tried passing a vga argument to it by adding vga=792 at the end of the above line but on booting I got a warning saying that *the argument I had tried to pass was invalid, press <return> to select a valid argument or press <esc> to wait 30 seconds....*

(The message was cut off as it went off the side of my monitor!)

On pressing return I was given a list of options each one consisting of a **hex code** and then a **rowxcolumn** option (e.g. 80x25) that corresponded with the hex code (e.g. 0F05). I picked one, entered it and pressed return but the computer basically shut down.

It seems like I can't find a valid mode for my monitor - it is a widescreen so I run at 1440x900 when in Ubuntu but I've never had a problem with it displaying at 1024x768 or even 800x600 when booting. Any idea what value I could try passing?

---

### Post by WirelessMike on 2007-05-11
> **Thingymebob said:**
> check that the entry for ubuntu in /boot/grub/menu.lst looks something like:
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30 ro quiet **splash**
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
```
The splash argument is what forces the splash screen to display.

You may also need to pass a vga mode to the kernel to force a compatible mode (add vga=??? from the list below)
```

 Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
  -------+--------------------------------------------------------------
 16 bits |            785     788      791
 24 bits |            786     789      792
```

EXCELLENT!!!

This worked perfectly for me.  I simply put in vga=792 in front of "ro quiet splash" and it's worked ever since.

Like so:
>  /boot/vmlinuz-2.6.20-15-generic root=UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30 vga=792 ro quiet splash

I guess I should add that I use a standard 19" Acer LCD monitor and an ATI X700 256M graf

:KS

---

