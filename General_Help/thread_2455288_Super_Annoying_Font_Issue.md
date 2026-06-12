---
title: "Super Annoying Font Issue"
date: 2020-12-16
forum: General Help
---

### Post by acodeacola on 2020-12-16
Okay,

So I have a bunch of fonts I use for designing, that I copied into /usr/share/fonts when installing a fresh copy of Ubuntu 20.04.

Now I am having this incredibly annoying issue that won't go away. This issue is random, and I can't seem to pinpoint what's causing it.

It seems like on a daily basis the fonts on my system get corrupted and turn into squares.

The only away I can get rid of this is by running fc-cache in terminal

sudo fc-cache -vrf

However, the font issue will return after restart, or after running some applications (none of which are the same each time).

I have also tried resetting font permissions, and a have even went as far as installing a copy of ubuntu in a vm and copying out the entire /usr/share/fonts folder to replace the one I have.

NOTHING i do seems to permanently resolve the issue. I would prefer to fix this issue without a complete system wipe as I setting up all my software for development takes forever.

A screenshot is attached showing what the issue looks like. As you can see it's a huge issue.

Any help with this issue would be greatly appreciated.

[ATTACH=CONFIG]287562[/ATTACH]

---

### Post by HermanAB on 2020-12-16
My guess is that you have too many fonts and too little RAM.

Anyhoo, in my experience, it is not much use having a fancy font that your intended audience doesn’t have.

---

### Post by acodeacola on 2020-12-17
I'm not actually using that many fonts roughly 20 to 30 fonts, and the fonts are used in digital media so I am unsure why some else would need the font. Anyway regardless I have a descent system, and never had this issue when i was running Manjaro Linux. This seems to be an Ubuntu related issue.

Anyway my system is an 10th Gen i7 6 core with 32GB of RAM and an nVidia 2080 video card. It's not a weak system by any means.

---

### Post by GhX6GZMB on 2020-12-17
I suspect it's a user/group and permissions problem. You need to think about how to organize your fonts. I do it like this:

Global fonts are in /usr/share/fonts/truetype or /usr/share/fonts/opentype, each font in an additional subdirectory, eg, /usr/share/fonts/truetype/Garamond

All directories and fonts should have root:root as owner, permission 755 for the directories, 644 for the font files.

For local fonts, it's the same layout with the fonts placed in $HOME/.local/share/fonts with the same subdirectories as above.

Same permissions, but "user":"group" as owner.

After arranging the font files, run:

sudo fc-cache -f -v

Hope this helps.

---

### Post by ajgreeny on 2020-12-17
Are these ttf fonts, or some other font filetype that is not compatible with Linux?  Where did these fonts come from?

I also recall seeing something many years ago that showed that certain WM Themes could cause this sort of display problem, particularly in Libreoffice

---

### Post by GhX6GZMB on 2020-12-17
> **ajgreeny said:**
> Are these ttf fonts, or some other font filetype that is not compatible with Linux?  Where did these fonts come from?


Good point. Only truetype and opentype fonts are supported nowadays, type1 fonts are basically dead. But I'm not sure if that's the issue here. The fonts work until a reboot, which to my mind wouldn't fit this scenario.

---

### Post by acodeacola on 2020-12-17
> **ml9104 said:**
> I suspect it's a user/group and permissions problem. You need to think about how to organize your fonts. I do it like this:

Global fonts are in /usr/share/fonts/truetype or /usr/share/fonts/opentype, each font in an additional subdirectory, eg, /usr/share/fonts/truetype/Garamond

All directories and fonts should have root:root as owner, permission 755 for the directories, 644 for the font files.

For local fonts, it's the same layout with the fonts placed in $HOME/.local/share/fonts with the same subdirectories as above.

Same permissions, but "user":"group" as owner.

After arranging the font files, run:

sudo fc-cache -f -v

Hope this helps.

This is absolutely what i needed. Thank you so much, my issue seems to be resolved now even after restart.

---

### Post by GhX6GZMB on 2020-12-18
Glad it worked.
One thing you need to know when doing this, is that you lose synchronization with the install database (Synaptic, Muon, whichever). 
But as you spoke of copying the fonts in your OP, this was already the case.

---

