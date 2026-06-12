---
title: "Lubuntu 18.10 title bar size"
date: 2018-11-09
forum: General Help
---

### Post by mickeyluv on 2018-11-09
I'm new to this OS having previously been a Windows user and I'm having trouble resizing the title bar - it's very large compared to the rest of the screen. My screen font is fine though, and if I right click and undecorate the window it's better, but I then lose the control buttons on the upper right. Can someone help me with this? I've searched for a specific answer to this but nothing I've come across has worked.



[ATTACH=CONFIG]281594[/ATTACH]

---

### Post by Autodave on 2018-11-09
Some specs on your machine may help someone give you an answer. Especially if you know what video card is in it.  Did you install any driver for the video?  If so, what one and where did you get it?

---

### Post by Dennis N on 2018-11-09
Could be caused by using too large a font for window title - check size in:

Menu > Preferences > LXQt Settings > Openbox Settings > Font > Active window title

---

### Post by mickeyluv on 2018-11-09
That did it - thanks. I'd looked at that setting earlier but hadn't realized that the minimum font size (6pt) could be overriden. My install needs 3pt and it works fine, though I think there's something amiss between the scaling of the font for the title bar and the rest of the system where the fonts displayed are correct. My thought was if it was a display driver issue then it would all be wrong.

The machine I have Lubuntu running on is an old Toshiba Satellite Pro A100 with an Intel video board. In Windows this uses the Intel Graphics Media Accelerator universal driver. I previously did a search on the Intel site for a Linux version of this and it states that the installed driver that comes with the OS should be used. I checked the installed values and the size and refresh rates are correct for my monitor (though there's no bit-depth stated).

Anyhow, apart from tweaking the font rendering to get it sharper overall I'm pretty happy with how it looks. I don't think the font rendering is quite as sharp as with Windows but I can put up with that in exchange for leaving Windows behind.

---

