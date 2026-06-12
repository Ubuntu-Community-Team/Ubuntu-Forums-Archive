---
title: "startx gives &quot;No screens found&quot;"
date: 2007-10-20
forum: General Help
---

### Post by Wlo on 2007-10-20
Hiya.

I'm fairly new to Linux and am having a problem starting Xwin since upgrading my graphics card.  I wonder if someone could help.

I've upgraded my graphics card to an ATI Sapphire Radeon 2600, and since doing so Xwindows won't start.  When I run startx I get "no screens found".  I downloaded the Linux driver from ATI and from reading some old forum posts I've gone through dpkg-reconfigure but I still get the same thing.

I'm not sure if I needed to do something else after installing the driver.  Like I say, I'm new to this.

I'm running Ubuntu 7.04 and my monitor's a Dell 2407 widescreen.  My xorg.conf and the log file output (split into 2 as exceeded upload size) are posted below.

If someone could point me at what to try next I'd be really grateful.

Thanks loads!

Wlo.

---

### Post by LanDan on 2007-10-20
Xorg is still using you are using your old graphics card.

to re-configure Xorg do the following

sudo dpkg-reconfigure xserver-xorg

and just go with all the defaults given

---

### Post by Wlo on 2007-10-20
Hiya.

> **LanDan said:**
> sudo dpkg-reconfigure xserver-xorg

and just go with all the defaults given

I've tried that already from reading some old forum posts.  Still get the same thing.

Any other ideas?

Wlo

---

### Post by LanDan on 2007-10-20
sorry should have read a bit more carefully.

do you have "xorg-driver-fglrx" installed?

---

### Post by Wlo on 2007-10-20
> **LanDan said:**
> do you have "xorg-driver-fglrx" installed?

"apt-get install xorg-driver-fglrx" tells me I already have latest version.  I think I may have installed it the other night after trawling the forums.  The later it got the more drunk I was though so it's a bit hazy.  What does that do?

Thanks :>.

Wlo.

---

### Post by Wlo on 2007-10-20
Does "no screens found" suggest a video card problem or a monitor problem?

---

### Post by LanDan on 2007-10-20
you might be right on the monitor thing and i think it could be something as simple as your refresh rates.

do still have some documentation on your monitor around somewhere, oherwise a look up in google with your model might give you some idea

---

### Post by Wlo on 2007-10-20
Hiya.

> **LanDan said:**
> you might be right on the monitor thing and i think it could be something as simple as your refresh rates.

do still have some documentation on your monitor around somewhere, oherwise a look up in google with your model might give you some idea

Thanks.  I did find some refresh rate settings for it on google previously.

Well, the good news is I've managed to get x to start just now.  Selected the Vesa driver and it's running.

Hmmm... seems strange when I had the exact driver for my card from ati.  I still don't think I know what's going on.  lol.  Ah well.

Thanks for your help.

Wlo.

---

### Post by LanDan on 2007-10-20
vesa is pretty generic and will not give you the best result (although at least some)

try changing these
HorizSync	30-130
VertRefresh	50-160

to

HorizSync	 30 - 81
VertRefresh	56 - 76

---

