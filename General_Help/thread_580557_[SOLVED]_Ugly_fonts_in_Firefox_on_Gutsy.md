---
title: "[SOLVED] Ugly fonts in Firefox on Gutsy"
date: 2007-10-18
forum: General Help
---

### Post by jordon on 2007-10-18
I upgraded to Gutsy today, and my choices of fonts for Firefox have been overridden. I can't seem to change them back. Before, my sans-serif and serif fonts were the Bitstream fonts (or DejaVu, same thing), and now they seem to be Ubuntu's ugly defaults, "Serif" and "Sans."

Here's what the sans-serif font looks like in Gutsy:
[http://www.theworldofstuff.com/shared/fontexample.png](http://www.theworldofstuff.com/shared/fontexample.png)

Here's what it used to look like:
[http://www.theworldofstuff.com/shared/fontexample2.png](http://www.theworldofstuff.com/shared/fontexample2.png)

Can anyone help?

---

### Post by FredB on 2007-10-19
Modify your fonts in Edit / Preferences dialog box in firefox.

---

### Post by Jolly-Swagman on 2007-10-19
OR you may want to try,

Open terminal & enter the following comands

sudo aptitude update

sudo aptitude install msttcorefonts

When done log-out then log -back in the fonts should change


Hope this may be of some help.

---

### Post by karhulitos on 2007-10-19
I noticed the very same, font is ugly. Wonder why was it changed during the upgrade?

---

### Post by bluedeep on 2007-10-19
Me too, fonts are very ugly and badly... On Feisty fonts was perfect!

---

### Post by FredB on 2007-10-19
Just see my answer a few message higher. Firefox uses its own fonts settings. 

It is maybe to big to be seen ?!

---

### Post by hugmenot on 2007-10-19
Okay, Sans or Serif are nothing but aliases for DejaVu/Vera, which in turn are mostly identical. The change you see is due to different hinting modes. You can set thos in the Font Preferences.

---

### Post by secretkeeper81 on 2007-10-19
> **Jolly-Swagman said:**
> OR you may want to try,

Open terminal & enter the following comands

sudo aptitude update

sudo aptitude install msttcorefonts

When done log-out then log -back in the fonts should change


Hope this may be of some help.

I have the msttcorefonts installed.

This doesn't seem to be the problem, and no matter what I choose in the Font Preference Tab, the fonts displayed in the webpage never change..

---

### Post by jordon on 2007-10-19
> **hugmenot said:**
> Okay, Sans or Serif are nothing but aliases for DejaVu/Vera, which in turn are mostly identical. The change you see is due to different hinting modes. You can set thos in the Font Preferences.

Thanks very much for clearing that up. I set the hinting to "None" and all is well now.

---

### Post by jspangler on 2007-10-19
> **jordon said:**
> Thanks very much for clearing that up. I set the hinting to "None" and all is well now.

Ahhh! Thank you. I've been trying to make my fonts look good all day. I wonder why the default full hinting look so crappy.

---

### Post by karhulitos on 2007-10-23
Darn.. please help me to get that too. Font Preferences where? Couldn't find one in FF nor in system menu. I know I'm blind but please help me..

---

### Post by jspangler on 2007-10-23
karhulitos,

If you're using Gutsy, go to System > Preferences > Appearance.

Then click on the "Fonts" tab.

Then click "Details".

Under "Hinting", click "none"

---

### Post by Derspankster on 2007-10-23
Read these posts with interest. I've never been satisfied with fonts in Linux. I have toyed with my fonts for a long time, downloaded the mscorefonts, changed hinting, shut it off - you name it.  As much as I like Ubuntu, fonts are still not up to Windows standards. This is important too - after all, you're looking at the screen if you're on the computer. 

I'm looking forward to the day that Linux fonts look as good as Windows - or OSX for that matter.

So, for me, this issue remains Unsolved.

---

### Post by karhulitos on 2007-10-23
> **jspangler said:**
> karhulitos,
If you're using Gutsy, go to System > Preferences > Appearance.
Then click on the "Fonts" tab.
Then click "Details".
Under "Hinting", click "none"

Thanks man, now fonts look as blurry as they used to be, heh. Perhaps the latter poster is correct in his opinion!

---

### Post by hugmenot on 2007-10-23
> **Derspankster said:**
> So, for me, this issue remains Unsolved.

Hehe. No, it's solved because it looks better now than Windows.

---

### Post by derixc on 2008-02-12
I actually use the Segoe UI font and I think it's much nicer. I also made a screenshot of the google button. see the difference.

[http://ubuntusite.com/fix-get-best-firefox-font-linux/](http://ubuntusite.com/fix-get-best-firefox-font-linux/)

---

### Post by Joor on 2008-02-13
I tried everything..but omg my eyes! - its actually so bad im thinking about going back to windows :(
It cant be right there is no fix for these blurry fonts ?

---

