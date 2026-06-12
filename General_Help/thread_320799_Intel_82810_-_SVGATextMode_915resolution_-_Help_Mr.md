---
title: "Intel 82810 - SVGATextMode 915resolution - Help Mr. Wizzard!"
date: 2006-12-17
forum: General Help
---

### Post by emarkay on 2006-12-17
This is going to sound whiny, but can someone assist me in getting my graphics set up.  I have read a few posts on this issue, and nothing seems to be working.

On boot I get a message that neither the SVGATextMode, and the 915resolution are configured, thus they are not being loaded.

I have an Intel 82810E DC-133 on board graphics controller.  Xorg.conf is using driver "i810".  (It's unique, and yes evidently, well supported in Linux. )

I have a Viewsonic E771-4 monitor.

The current screen setting I have is 1024 x 768, with a FH of 60.06kHz and FV of 75.12 Hz at 16bpp.  This is what I would like to see in all modes.

The monitor supports FH from 30 to 70kHz and a FV of 50 to 120Hz.
The 82810 card supports up to 1280 x 1024 at 8, 16& 24bpp with 60, 72, 75, 85 & 100 (8& 16bpp only) Hz refresh.
BTW, for this card, the 3D features are available ONLY at 16bpp.

There are no Googled reference for the Intel chipset settings for SVGATextMode.

My xorg.conf, for 16bpp, lists these available modes:
"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480".

Also, where, for for 915resoution, do I find  my "XRESO" and my "YRESO"?

In trying to run/configure  915resolution, I get this:
sudo 915resolution 45 1024 768 16

"Intel 800/900 Series VBIOS Hack : version 0.5.2
Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 71248086
Please report this problem to [email]stomljen@yahoo.com[/email]"

Which I did a week ago but have had no responses.
I also was told by a prompt to use VBETOOL.  it's there, but what is it?

So you see there's a number of issues and, well, I am confused...

---

### Post by WorLord on 2006-12-18
I'm a little confused by this post.  What exactly are you trying to do here?

---

### Post by emarkay on 2006-12-18
confirm that I have the graphics set up for maximum speed of display.

There is a substantial difference here in page display times in programs between Ubuntu and Windows98 for the same content.  The error messages I am getting seem to indicate that while I may be in a SVGA mode (and because I can not adjust the resolution settings in GRUB with the "VGA=xxx" setting) the graphics display here is not optimized.

---

### Post by emarkay on 2007-02-01
I have since reinstalled Dapper, and things seem a bit faster, but would still like to know what is the optimal settings - but I'll leave that for someone else to worry about - marking this'n "resolved"...  :)

---

