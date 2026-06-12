---
title: "Superkey/Winkey not working on Logitech dinovo edge keyboard"
date: 2007-10-25
forum: General Help
---

### Post by kooldino on 2007-10-25
So I have one of these fancy Logitech Keyboards:

[IMG]http://www.finalsense.com/news/image/desktop/logitec-dinovo.jpg[/IMG]

However, I can't get my superkey (winkey) working to save my life.  

I tried running "setxkbmap -model pc105 -layout us -variant basic" as found in another thread, but it didn't help.

---

### Post by kooldino on 2007-10-26
bump

---

### Post by voidmain on 2007-10-26
> **kooldino said:**
> bump

This is a known issue with Gnome. I've been tracking it down for around 2 hours now. No luck. The issue is that the win-key is mapped to both Super+l and Mod4. I think someone set this up to have a "windows menu" type of behavior when you hit the win-key, but it also doesn't allow the win-key to be used with any other keys. Lame.

---

### Post by kooldino on 2007-10-27
I probably should have mentioned that I'm on kubuntu w/ KDE.

I want the superkey to work so I can use it with compiz for a shortcut key for things, but it just refuses to work.

---

### Post by kooldino on 2007-10-31
Ok, I got it working.  In the KDE System Settings menu, I went to (of all places) "Regional and Language" > Keyboard layout 

I checked "Enable Keyboard Layouts" and forced it to "Generic 105 Key"

---

### Post by 3ntity on 2007-11-08
> **kooldino said:**
> Ok, I got it working.  In the KDE System Settings menu, I went to (of all places) "Regional and Language" > Keyboard layout 

I checked "Enable Keyboard Layouts" and forced it to "Generic 105 Key"Wow... that would have taken me a while to figure out ;)

That worked marvelously, thanks :)
**edit** forgot to say, i had this with a much more basic logitech keyboard than the diNovo, which is definitely sleek ;)

---

