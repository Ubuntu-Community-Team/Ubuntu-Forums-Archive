---
title: "need help installing compiz fusion"
date: 2008-06-27
forum: General Help
---

### Post by Graffight on 2008-06-27
i'm really new to this, so i don't quite understand the command line, and i have a few questions.

in order to install compiz fusion do i need to download something before running the command line?

if not i'm having an issue with the command line, i get the error below

code:
sudo apt -get -y remove compiz-core desktop-effects
sudo: apt: command not found

i'm not sure if i'm not typing something correctly or what, but it's making me sad :-) 

all help will be greatly appreciated!

---

### Post by Graffight on 2008-06-27
also how do i make those cool box's around the code portions of my post?

---

### Post by Forlong on 2008-06-27
You shouldn't need to install Compiz. It's pre-installed since Feisty (at least if you are running GNOME).

Just go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* and enable them there.


edit: there's a button that looks like a # to use the CODE tag.

---

### Post by Graffight on 2008-06-27
ok...so all that code input i just did was a wast of time :-) well in that case, when i try to apply the effects, it says desktop effects could not be enabled.

---

### Post by Forlong on 2008-06-27
In that case, run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Graffight on 2008-06-27
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon X800
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

________________________________________________________________________________

am i unable to use a Radeon video card?

---

### Post by Graffight on 2008-06-27
by the way that took forever to figure out how to run that...running programs in Linux is dominantly different....fun to learn but different.

---

### Post by Forlong on 2008-06-27
Follow the options the program gives you after this output. Then try again.

---

### Post by Graffight on 2008-06-27
It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist.

Should i skip the blacklist?

---

### Post by Forlong on 2008-06-27
Yeah, I know the output (I wrote it ;)), so did you skip the blacklist?

edit: Ah, OK. Well, it's up to you. There's actually no harm in doing so but **keep in mind that you did it**. If you encounter any system freezes, that's the bug.

---

### Post by Graffight on 2008-06-27
Thanks Man It Worked!!!

---

### Post by Graffight on 2008-06-27
another question...how do i configure the settings for it?

---

### Post by Forlong on 2008-06-27
For Compiz Fusion?
Go here: [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by Graffight on 2008-06-27
that link isn't working :-(

---

### Post by Forlong on 2008-06-28
Please try again, maybe it was down for a short while.

---

