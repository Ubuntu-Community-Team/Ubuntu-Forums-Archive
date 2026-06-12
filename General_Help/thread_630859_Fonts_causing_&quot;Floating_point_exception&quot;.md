---
title: "Fonts causing &quot;Floating point exception&quot;"
date: 2007-12-03
forum: General Help
---

### Post by panicb on 2007-12-03
I have been using custom fonts lately, which I put in ~/.fonts and use as user.
I didn't have any problems, but after an update today, using those fonts cause any progarm to quit and leaves a message on terminal: "Floating point exception," and nothing else.

At first I thought this was firefox specific, but it was not, because I realized that I use (custom) fonts for Korean and firefox uses that font for pages in Korean.
Another example, is that I used artwiz fonts for xfwm title text, and it started to crash; when I nuked its config and not use artwiz font it's perfectly fine.

Here's how to generate it:
1. open any program: we'll use gedit.
2. go to preferences and make it use a custom font, say, any of artwiz fonts
3. as soon as you click on that on font-select dialog, the program will crash.

Any ideas why custom fonts cause this? It only started to happen after updating my system today.

Xubuntu 7.10


I got these error messages while installing msttcorefonts, I have no idea why this happens.
No luck with google either.


No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.



Update:
More googling, and I found out that this is commonly caused by corrupt font files.
No, the font files are not corrupt, I tried different copies.
Also, I put it in /usr/share/fonts instead of ~/.fonts to see if that was the problem, there was no difference.

I would have to guess that some kind of recent update in certain software is having problem with *.ttc (not *.ttf) files.
By the way, Gulim and Batang are in *.ttc .. it worked normally for years but suddenly it doesn't.

---

### Post by fseto on 2007-12-05
Same problem here too, it's crashing on batang and other .ttc fonts.  Probably related to recent update of libcairo.so.

Bug been reported here:
[https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861)

---

### Post by ayurchen on 2007-12-05
Perhaps this is my case too.

After last security upgrade of libcairo2 just about any GUI  application started to give floating point exception at startup. After reboot I could log in to Gnome session, and panels displayed fine, but no program could be started and eventually panels crashed leaving just empty screen. This happened on both i386 and amd64 machines. I'm using Serene raster fonts from xfonts-bolkhov package for the interface. After rolling back the libcairo2 upgrade everything went back to normal.

So there must be a bug introduced into  libcairo2_1.4.10-1ubuntu4.1.

---

### Post by 2ig2ag on 2007-12-11
I have encountered it too.
What can I do about it before the bug is fixed?

---

### Post by LepeKaname on 2007-12-11
I had the same case with the Update  "libcairo2 1.4.10-1ubuntu4.1" on my Xubuntu 64
I just downgrade it and every was back to normal. 
How to downgrade: go to synaptic and in "Package->Force Version..." and select the old one.
That's all!

---

