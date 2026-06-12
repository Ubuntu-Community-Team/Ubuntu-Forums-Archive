---
title: "Blurry fonts in Firefox"
date: 2006-10-27
forum: General Help
---

### Post by SlayerMan on 2006-10-27
Hi all,

I just did a fresh install of Edgy. Everything's fine (amazing how fast it boots), but the fonts in Firefox are all blurry. The problem only applies to Firefox, all other apps, including GNOME, display fine.

Any suggestions?

Kind Regards

Steffen

---

### Post by jd65pl on 2006-10-27
I think a few people may have experienced this, why not check Launchpad to see if there is an error report for it? Or search the forums to see if anyone has a solution yet?

---

### Post by speedsix on 2006-10-27
The fonts in Edgy FF just look ugly to me, kinda chunky and yes, not quite as sharp.

---

### Post by Choad on 2006-10-27
turning on sub-pixel hinting works... im not sure what the cpu-cost will be?

---

### Post by SlayerMan on 2006-10-28
Yes, it seems that enabling strong hinting solves the problem. I'm wondering why I have this problem on edgy. On dapper, I didn't have to change any font settings to get a clear display.

Nevertheless, Edgy is great :) The only thing missing now is better integration of KDE apps (fonts, colors etc.) into the GNOME desktop, but that's a different subject.

---

### Post by graigsmith on 2006-10-28
> turning on sub-pixel hinting works.

not for me.  the fonts are still ugly, and mismatched from what gnome desktop uses.

---

### Post by Choad on 2006-10-28
> **graigsmith said:**
> not for me.  the fonts are still ugly, and mismatched from what gnome desktop uses.
tough break, you did rstart firefox yeah?

if you do this in XFCE you will have to apply the fix detailed here [http://www.ubuntuforums.org/showthread.php?t=246111&highlight=xubuntu+fonts+size](http://www.ubuntuforums.org/showthread.php?t=246111&highlight=xubuntu+fonts+size) because of a bug in XFCE

it happens every time u turn on sub-pixel hinting afaict

---

### Post by ajm2005 on 2006-10-28
Sometimes deleting .font.conf in your home directory fixes this.

Another option is to install Windows fonts (some of which are designed to be displayed on the screen and therefore look better). If you have access to a Windows XP or server 2003 installation, copy the contents of the font folder to your ubuntu installation. (Put them in the .fonts folder in your home directory). (Press control-H to reveal the hidden .font folder).

I find the most useful windwows font is Tahoma (which is used as the system font for menus, etc. by windows). I have this as my ubuntu system font (choose by going to system>preferences>font then choosing tahoma for all options except the monospace font).

You can also choose tahoma for menus, etc. within Firefox.

You sometimes have to restart applications or even log out and log back in for font changes to fully take effect.

Tahoma and Verdana were specially designed for the screen and don't tire the eyes too much.

---

### Post by Beernut on 2006-10-28
I had an issue with Dapper and blurry fonts just upgraded to Edgy and no problems.  However just thought I would mention it, the problem was the refresh rate was wrong it was set to 65 and my monitor needed 75.  It's a Viewsonic LCD.  Seemed to be more noticable for whatever reason in Firefox.

---

### Post by graigsmith on 2006-10-28
oh, restarting firefox after turning on subpixel worked.  what if i dont want to use subpixel rendering?  i can see the color fringes on it. and it bugs me.

---

### Post by Bear Knuckle on 2006-12-15
> **ajm2005 said:**
> Sometimes deleting .font.conf in your home directory fixes this.

This helped for me. Thank you!

---

### Post by NeoChaosX on 2006-12-15
> **graigsmith said:**
> oh, restarting firefox after turning on subpixel worked.  what if i dont want to use subpixel rendering?  i can see the color fringes on it. and it bugs me.

There should be options on what kind of hinting you want (RGB or BGR). Try changing those options and see if that gets rid of the color fringes.

---

