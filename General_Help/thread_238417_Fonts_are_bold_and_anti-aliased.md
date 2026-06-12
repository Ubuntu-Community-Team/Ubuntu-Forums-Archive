---
title: "Fonts are bold and anti-aliased"
date: 2006-08-17
forum: General Help
---

### Post by Mau on 2006-08-17
I ran an upgrade last night and when I booted the computer up this morning all my fonts are looking slightly odd.  It seems that they were all anti-aliased and things are "bolder."  Anyways, it just doesn't look pretty.

My font settings are set to:

Application font - Sans, 10, normal
Document font - Sans, 10, normal
Desktop font - Sans, 10, normal
Window title font - Sans, 10, normal
Fixed width font, monospace, 10, normal.

What gives?

---

### Post by junior aspirin on 2006-08-17
yar i got the same prob.

these packages were updated...```
Upgraded the following packages:
cgwd (0.53) to 0.55
cgwd-themes (0.9) to 0.11
gnome-terminal (2.14.2-0ubuntu1) to 2.14.2-0ubuntu2
gnome-terminal-data (2.14.2-0ubuntu1) to 2.14.2-0ubuntu2
imagemagick (6:6.2.4.5-0.6) to 6:6.2.4.5-0.6ubuntu0.1
libcairo2 (1.2.0-0ubuntu1quinn2) to 1.2.2-0ubuntu1
libdrm2 (2.0+cvs20060625) to 2.0.2+cvs20060815
libfreetype6 (2.1.10-1ubuntu2.2) to 2.2.1-0ubuntu1
libgl1-mesa (6.5.1-cvs20060628) to 6.5.1+cvs20060815
libgl1-mesa-dri (6.5.1-cvs20060628) to 6.5.1+cvs20060815
libglu1-mesa (6.5.1-cvs20060628) to 6.5.1+cvs20060815
libkrb53 (1.4.3-5) to 1.4.3-5ubuntu0.1
libmagick9 (6:6.2.4.5-0.6) to 6:6.2.4.5-0.6ubuntu0.1
libvte-common (1:0.12.2-0ubuntu1) to 1:0.12.2-0ubuntu2
libvte4 (1:0.12.2-0ubuntu1) to 1:0.12.2-0ubuntu2
mesa-utils (6.5.1-0ubuntu16) to 6.5.1+cvs20060815
python-vte (1:0.12.2-0ubuntu1) to 1:0.12.2-0ubuntu2
realplay (10.0.7-0.0.0.5.ubuntu0.1) to 10.0.7-0.0.0.5.ubuntu0.2
```

my guess its to do with either libcairo2 or libfreetype6.

but not sure.

---

### Post by Mau on 2006-08-17
I just tried to remove libcairo2, but apt wanted to remove practically every application... so didn't do that! ;)

I then tried to remove libfreetype6, but I have unmet dependencies on cupsys missing poppler-utlis and xpdf-utilis.  When I do an apt-get update, I fail to connect to security.ubuntu.com.  Is that mirror down?

---

### Post by TheFifth on 2006-08-17
I've noticed this too.  I will say though that I kinda like it!  On my laptop it has made the text look far better and more readable, sort of like cleartype does on XP.  I dont think the fonts have actually got any bigger, but they definitely look a little bolder and more anti-aliased.

I do agree though that it doesn't look so good on my desktop machine.  So if this is a mistake and it gets fixed, can I request that there is an option to keep the fonts like this as I'd definitely want to keep it on my laptop.

---

### Post by crackseller on 2006-08-17
Same problem here. It's looks really weird. I hope there's a solution to this soon. I can't stand the way the fonts look now.

---

### Post by everdred on 2006-08-17
This is happening to me too. Certain things look better this way, but on the whole, most don't and I'd certainly like to go back to the "right" way.

---

### Post by Mau on 2006-08-17
Ok, this is starting to look like a packaging problem on Ubuntu's end rather than my end with all these reproductions.  Who maintains "fonts"?

---

### Post by kpkeerthi on 2006-08-17
May be its a good idea to post this problem in [Repository Support Forum]("http://www.ubuntuforums.org/forumdisplay.php?f=41"). Just a thought.

---

