---
title: "Trouble with tahoma font"
date: 2006-12-04
forum: General Help
---

### Post by Zoef on 2006-12-04
Hi All,

I imported tahoma.ttf and tahomabd.ttf from windows and put it in /usr/share/fonts/truetype/msttcorefonts (which I already installed successfully).

Strange thing is that I can use tahoma perfectly well as root, but under my own login tahoma  seems to be broken...  

[ATTACH]20554[/ATTACH]

And in the fonts directory tahoma appears with a kind of 'faulty' icon...
[ATTACH]20555[/ATTACH]

I rebuilt the fonts cache and even restarted the system.

Why is this happening? (I'm on Edgy)

---

### Post by yabbadabbadont on 2006-12-04
Try creating a .fonts directory in your home directory and copying the files there.  It should show up correctly then.

---

### Post by coffeecat on 2006-12-04
Can't explain why it's broken, but I can describe an easier way of installing fonts with Gnome, which seems to be little known. And I've installed Tahoma and other fonts this way with no problem.

Go to System > Preferences > Fonts. Click on the 'Details' button, and then on the 'Go to Font Folder' button. Simply drag and drop whichever .ttf files you want installed into the Nautilus window that has opened. I used to think that you had to restart the Xserver, but the last time I did this the fonts were available for use immediately.

Suggest you delete the .ttf files you have already installed and rerun fc-cache before you do this.

---

### Post by Zoef on 2006-12-04
I already tried dropping them in /home/<user>/.fonts, logged on again but it made no difference.  I got the faulty icons also in this .fonts dir.:(

---

### Post by yabbadabbadont on 2006-12-04
Apparently, they aren't valid font files...  perhaps they became corrupted when you copied them to your Ubuntu system?  From where did you obtain them and how did you get them to your system?

---

### Post by yopnono on 2006-12-04
Check the permission on them

---

### Post by Zoef on 2006-12-04
Solved it!

Indeed they seemed to be corrupted.  I first copied them from a mounted win XP volume and they became corrupted.  Later I actually booted windows and put the files on a USB stick and replaced them in /usr/share/fonts/truetype/msttcorefonts.  

But from a previous experiment, the bad ones were still left in /usr/share/fonts/truetype/custom as well.  Removed them there, fc-cache -f -v 
and fixed!

Still don't understand why it worked as root...  Should be that the .../custom dir wasn't considered by root.

Thanks for the hints!

---

### Post by flipkick on 2007-11-16
> **yopnono said:**
> Check the permission on them

That worked for me as well.

---

