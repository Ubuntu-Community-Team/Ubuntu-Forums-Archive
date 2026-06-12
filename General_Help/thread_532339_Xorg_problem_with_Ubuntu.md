---
title: "Xorg problem with Ubuntu"
date: 2007-08-22
forum: General Help
---

### Post by Ozor Mox on 2007-08-22
I've been trying to install Ubuntu on my girlfriend's old Dell Latitude laptop, but when I boot it in to the Live CD, the screen is broken up. As in there are fuzzy and straight sections of desktop that run down the screen and show different areas, so as you move the mouse around, you can often see it twice on different parts of the screen.

Thinking it was a problem with the desktop environment because of the low specs of the laptop, I burnt a Xubuntu disc and tried that, but the problem is identical, so I assume it must be a problem with the Xorg configuration.

Has anyone had a similar problem or any ideas on how I might be able to fix it? I tried to take a screenshot but it came out perfectly normal after I copied it to another computer! If possible I'll try and take a screenshot with a digital camera and post it.

---

### Post by logos34 on 2007-08-22
If 'Safe graphics' option on the menu doesn't work, then try passing a vga boot option to the kernel.
[https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29%7C%28options%29#head-07d4b7411f7da70e337287db9a86ea941038b8b3](https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29%7C%28options%29#head-07d4b7411f7da70e337287db9a86ea941038b8b3)

Or try the text-mode Alternate install cd.

---

