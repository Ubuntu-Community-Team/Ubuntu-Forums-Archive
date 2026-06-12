---
title: "Black dots in upper left area"
date: 2008-05-06
forum: General Help
---

### Post by Packrat73 on 2008-05-06
I updated from 7.10 to 8.04. Have Compiz enabled and it works fine. But I see some black dots in the upper area on the applications button and right below it. Anyone else having this issue.

This is on a Dell Inspiron 1420 and I have the Nvidia driver installed.

---

### Post by BandD on 2008-05-06
Is it like a square selection box?  If so, it is a known bug in gnome.   I can't find the bug report right now, but it was filed over three years ago and nothing has been done to address it.  Seeing as how it is only cosmetic, the priority isn't really very high.

If it's not that, can you post a screenshot of it?

---

### Post by Packrat73 on 2008-05-06
> **BandD said:**
> Is it like a square selection box?  If so, it is a known bug in gnome.   I can't find the bug report right now, but it was filed over three years ago and nothing has been done to address it.  Seeing as how it is only cosmetic, the priority isn't really very high.

If it's not that, can you post a screenshot of it?



Here is the screenshot, see the black dots? They get worse when you put a mouse over them.

---

### Post by BandD on 2008-05-06
Ok, well that is a different bug than the one I was thinking of.  If you hide the panel to the right of the screen, are the dots still there?  To enable hiding right-click on a blank area of your top panel and click Properties.  Then mark "Show hide buttons" and click the newly displayed button to the far-top-right.  

Also try making something fullscreen, a movie, or slideshow, etc.

If the dots are still there then there is either something wrong with your monitor, or your graphics card.  That's a very strange issue you're having.

---

### Post by Packrat73 on 2008-05-07
well I know its not either as It works flawless in vista and it was fine in 7.10
I am thinking of the Nvidia Driver problem.

Huron also killed my sound card. I think it might be the ICH chipset problem

---

### Post by Karibbe on 2008-05-13
I have the same problem, but it did not appear right after upgrading to 8.04. I did the upgrade a couple of weeks ago and the dots appeared last night. I have a Dell XPS m1530 with an nVidia GeForce 8600M GT.

---

### Post by marty19 on 2008-05-13
I have exactly the same problem. It started when i upgraded to Hardy. I also have GF8600 GT. Black dots are there after every start of Ubuntu, but if I restart X server, they suddenly disappear..

---

### Post by four2theizz0 on 2008-06-05
I have the exact same problem.  I have been using hardy for a few weeks without this incident.

I just recently updated everything and I noticed the kernel upgraded to 2.6.24.18 and I had been setting mine to 2.6.24.16 because of the suspend/hibernate issue.

The first time it booted into .18 the dots were there, and now after switchign back to .16 as default they are there now

interstingly enough as im typing this on another comp with the laptop next to me...the screen went dark for the screensave to come on and i moved the mouse for it and the dots were gone when the scren came back up

odd

oh ya, brand new sony vaio sz-vgn780 with nvidia 8400

---

### Post by four2theizz0 on 2008-06-05
I have the exact same problem.  I have been using hardy for a few weeks without this incident.

I just recently updated everything and I noticed the kernel upgraded to 2.6.24.18 and I had been setting mine to 2.6.24.16 because of the suspend/hibernate issue.

The first time it booted into .18 the dots were there, and now after switchign back to .16 as default they are there now

interstingly enough as im typing this on another comp with the laptop next to me...the screen went dark for the screensave to come on and i moved the mouse for it and the dots were gone when the scren came back up

odd

..and then i try to click arounda nd they come back

oh ya, brand new sony vaio sz-vgn780 with nvidia 8400

---

### Post by four2theizz0 on 2008-06-05
I read on another forum that it had to do with the human theme.  I changed that and logged out and back in...and voila the dots appear to be gone
...for now


I will advise itf they come back when restarting

---

### Post by Anxiety35 on 2008-06-13
This just started happening for me today. I've been running 8.04 since the day it came out.

I installed a few packages today such as StartUpManager and some numlock thing. Nothing to do with any visuals though. When I restarted, the problem was there.

I get the dots (one pixel tall, two wide. Exactly like Packrat but less dense) all the way across the top menu bar, even if I hide it. They occasionally flash away when I change the focus of windows or when some compiz effect goes over them.

---

### Post by Addie MacGruer on 2008-09-24
I got these as well - Hardy Heron, Q6600, Nvidia 8800GT, compiz; exactly like PackRat73's pattern.  Caused by the choice of vga= line in my kernel parameters.  Did sudo vim /boot/grub/menu.lst, changed my kernel line from:

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet

to

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet vga=773

They're all gone.  They also disappear if you restart X with ctrl-alt-backslash, or if you change to a tty and back - ctrl-alt-F1 ctrl-alt-F7, say.

Addie.

---

### Post by listdata on 2008-10-14
> **Addie MacGruer said:**
> I got these as well - Hardy Heron, Q6600, Nvidia 8800GT, compiz; exactly like PackRat73's pattern.  Caused by the choice of vga= line in my kernel parameters.  Did sudo vim /boot/grub/menu.lst, changed my kernel line from:

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet

to

kernel /boot/vmlinuz-2.6.24-19-generic root=... ro quiet vga=773

They're all gone.  They also disappear if you restart X with ctrl-alt-backslash, or if you change to a tty and back - ctrl-alt-F1 ctrl-alt-F7, say.

Addie.

I had the same issue -- Nvidia 8800GTS on Xubuntu 8.04.1. Apparently it is not a Desktop issue only present on Gnome, since I had the same thing happen on my XFCE desktop. Just like you, it was because of the **vga=** option in /boot/grub/menu.lst's kernel options. (But unlike your situation, I had put in a vga= option where there was none before, so I could use TTY with a higher resolution than the default one).

I switched my vga= setting from a 24-bit one to an 8-bit one (same resolution), and now the dots are gone. (Get hwinfo, and do **hwinfo --framebuffer** to see your supported options and use a smaller bit option). To illustrate, here was my hwinfo --framebuffer output:

```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.FMoox01sR1A
  Hardware Class: framebuffer
  Model: "NVIDIA G80 Board - p356h00 "
  Vendor: "NVIDIA Corporation"
  Device: "G80 Board - p356h00 "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcb000000-0xcbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

And then I changed my vga= from vga=0x0369 to vga=0x0368.

---

### Post by donkihote on 2009-06-01
it happened to me on Jaunty and my laptop Toshiba A215 ATI x1200, and <ctrl><alt> F1 then <ctrl><alt>F7 works to me. Thanks

---

### Post by ruru on 2009-06-29
Thanks for the tip. I had the same problem, and changing from the Human theme (to Clearlooks) seems to have gotten rid of the dots for me as well.

---

### Post by ruru on 2009-06-29
Actually - the dots just came back (under Clearlooks) - so I changed back to Human and logged in fresh - now they're gone. It seems as if just changing the window decorations resets something. 
I have come across this problem before and it is very inconsistent (probably why the bug still exists).

---

### Post by ruru on 2009-08-29
I have noticed that simply logging out of the session and logging back in again cures the problem for me 100% of the time. 

I have submitted a bug report about this: [Bug 421048]("https://bugs.launchpad.net/bugs/421048")

---

### Post by lesnoland on 2010-06-07
i get the same error on 10.04, my problem was fglrx, i updated to latest version from ati, 10.5, and now the dots dissapeared.

---

### Post by Tibb on 2013-03-24
I had exactly the same problem constantly since several years with different Ubuntu versions and different nvidia drivers.

After adding agp=off to the GRUB_CMDLINE_LINUX_DEFAULT in the grub config the strange black dots problem is completely gone! :-)

...maybe this helps someone too.

---

### Post by oldos2er on 2013-03-24
Old thread closed.

---

