---
title: "Need help with new graphics card purchase please"
date: 2007-01-07
forum: General Help
---

### Post by jimbob on 2007-01-07
I received an Acer AL2416Wd 24" monitor for Christmas which is happily perking along at its native resolution of 1920x1200 out of the vga port on my old Nvidia graphics card.

After much Google-ing around it becomes apparent that by merely purchasing a new graphics adapter with an additional DVI output doesn't guarantee that I can attain this resolution digitally.

Manufacturers seem to be a bit cloudy on their specs by not saying what each individual port can do - only the maximum that the overall card will support.

If there is anyone out there who has an Nvidia chip-based card and is running 1920x1200 out of a DVI port I would really appreciate hearing about your particular hardware before I spend a lot of money on something that doesn't work.

I am not a gamer or anything like that so economy class would be just fine.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-01-15
*** Bump ***   (anybody?)

---

### Post by jimbob on 2007-01-20
Give me enough time and I answer my own post I guess.

After several days of research I ordered a PNY Verto GeForce 6600 AGP8x 256MB DDR Graphics card with  VGA, DVI, and HDTV/S-video outputs. 

After hooking it up via the DVI port to my Acer AL2416WD 24" display I brought up Feisty in single user mode and generated a new xorg.conf file using the dpkg-reconfigure -phigh xserver-xorg command.

I was quite gratified to see that it was still using the nvidia driver (not just nv) when I examined the file so I rebooted in normal mode and voila! a beautiful 1920x1200 DVI resolution at 50Hz.

The only thing I found to be a bit strange is that it no longer identifies the hardware specifically in the xorg file - just calls them "generic monitor" and "generic video card".  What's up with that?

Anyhow I'm gratified that my $$ haven't been spent in vain but to be honest these old eyes can't really see any difference.

Guess I'll play a DVD now and check it out.   Maybe I'll even find a gamer and have him check it out.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

