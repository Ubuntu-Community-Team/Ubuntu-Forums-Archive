---
title: "Blurry text on Ubuntu 20.04"
date: 2021-08-25
forum: General Help
---

### Post by dialyt-7 on 2021-08-25
I installed Ubuntu to dual-boot with Windows 10 on my ThinkCentre M720t. Text on Ubuntu is not sharp and hurts my eyes after a while. On the same monitor, Windows 10 is sharp. Two screen grabs of the same website text on both OS revealed what I call chromatic aberration: there is a blue shadow to the right of every character on Ubuntu. I've tried Gnome Tweaks font settings, nothing works. Please help me improve the font sharpness. I am a Linux newbie, I can do basic tasks on the Terminal. My monitor is a hi-res monitor (3840 x 2160) but even on my alternative 1920 x 1080 monitor, the text is still blurred.

---

### Post by Impavidus on 2021-08-26
"Not sharp and hurts my eyes" isn't very objective. It's a bit hard to interpret.

That blue shadow is the result of [subpixel rendering]("https://en.wikipedia.org/wiki/Subpixel_rendering"). Suppose the anti-aliasing algorithm decides that the black part of a letter should occupy the left 2/3 of a particular pixel, followed by white background. The rightmost 1/3 of the pixel on your screen is blue, so to make that part of the pixel light up, the entire pixel made blue. But maybe that's wrong on your screen. Try tweaking the anti-aliasing settings for text rendering. It must have a setting for subpixel order.

You didn't show us your screenshots of text rendered in Windows versus Ubuntu.

---

### Post by dialyt-7 on 2021-08-26
Hi, please see attached. One of the same website section on Windows and Ubuntu. The other is a screenshot of the settings app in Ubuntu showing malformed characters. The pics don't really convey what I'm describing very well. :-/ 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289051&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289052&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289053&stc=1[/IMG]

---

### Post by Autodave on 2021-08-26
I see no difference at all: even zooming in.  I see that this has an onboard graphics card.  Have you added another graphics card by chance?

---

### Post by dialyt-7 on 2021-08-26
Yes, it doesn't show up in those files. But the problem is clear on my system. The Ubuntu text is soft and a bit fuzzy. I read online that this is a common issue, but I see no solution. The graphics are Intel UHD 630 built-in to Core i7; no additional graphics card has been installed.

---

### Post by Impavidus on 2021-08-26
There is a slight difference. If I zoom in on the Ubuntu screenshot, I can see some colouration. That must be the effect of subpixel rendering. Subpixel rendering appears to be off in Windows. I can't say where you find the settings for that in Ubuntu; in Xubuntu it's in settings &#8594; appearance &#8594; fonts. On your system, it must be set to RGB from left to right. Maybe that's wrong. Can you figure out the correct order for your screen?

Difficult to say what's wrong with your final screenshot. It seems antialiasing is off, but there are jpeg compression artefacts making it hard to see. Better to save screenshots in png format.

---

### Post by dialyt-7 on 2021-08-26
Hinting and anti-aliasing on or off, it makes no difference.

---

