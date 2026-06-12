---
title: "Firefox not taking Gnome Font Settings"
date: 2007-06-03
forum: General Help
---

### Post by Beamerboy on 2007-06-03
First of all this is a Gutsy problem so I am not expecting any official sort of response since gutsy is not released yet, however, I am hoping that some of you who have Gutsy installed might have a solution to this problem.

Since rebooting after installing Gutsy I noticed all the fonts were really small, so I went to System>Preferences>Font and upped the size of them all to 14.

All other apps I have launched have taken the new font sizes with no problem, however, Firefox is only applying "Window Title Font" setting, it is completely ignoring all the other settings (even the menu bar is a tiny font).

As I write this the font in firefox is so small I can barely read it.  Does anyone know how to fix the problem?

Thanks in advance.

Paladine

---

### Post by Beamerboy on 2007-06-03
Problem fixed.  Apparantly Gutsy attempts to detect DPI settings when Xorg launches and it set mine to 75 instead of 96.  Fixed by going into System>Preferences>Font, then click on Details and change the resolution to 96.

Paladine

---

### Post by andoty_jazz on 2007-06-04
@Beamerboy

Your the man.

Thank you so very much.

Well my case is the other way around. I looks kind of big/large in my monitor using 96 resolution. Thank you, i was able to reduce mine.

Are you familiar of the error, still in fonts, were the font's name appends a **Not-Rotated** on it. 

It erritates me when I opened GIMP and almost all of the fonts does have this **Not-Rotated** thing.

e.g: *Arial Not-Rotated* instead of **Arial**. 

If theres anyone who could help, please speak-out. It will be greatly appreciated.

------

P.S. Thanks again Beamerboy.

---

