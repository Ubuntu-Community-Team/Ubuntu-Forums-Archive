---
title: "&quot;Start&quot; button shows as &quot;Super_L,&quot; doesn't seem to work in Compiz Fusion"
date: 2007-07-08
forum: General Help
---

### Post by messudieh on 2007-07-08
Hi,

First post, might as well make it a difficult one, eh?

The major problem I'm having is with my Microsoft Natural Multimedia Keyboard 1.0A and Compiz Fusion. When I do anything with the start button, fusion doesn't respond to it.

**Things I have Tried:**
-Keyboard Preferences -> Layout Options -> "Super is mapped to the Win-Keys (Default)"
- also in preferences, changing my keyboard layout. I've tried 'Microsoft Wireless Multimedia Keyboard 1.0A' as well as various generic 104 and 105 key layouts.

bringing up xmodmap shows mod 4 as "Super_L (0x7F), Hyper_L (0x80)

Also, in my xorg.conf it always seems to say the same thing even if I change my keyboard:

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Any help would be hugely appreciated.

Also, on a side note, is there any way to not have new windows come up at the very top of my screen? They always come up under the top panel while I'm running compiz (in XGL obviously)

---

### Post by messudieh on 2007-07-09
Bumping it once.

Anyone have any idea? I can't find anything on google or the forums despite tons of searching.

---

### Post by sambehera on 2007-07-21
im having the same problem... will now boot into plain XGL to see if its an XGL-problem or a compiz (fusion) problem... i havent tried changing keyboard layout for it works perfectly in non-XGL sessions (tested with plain KDE)...  so far the only solution ive found is to rebind the shortcuts that used the super(win) key to using "alt" or "control+alt" or "shift+control" or "shift+alt".... i know this is a temporary workaround but i'll try finding if the problem is with XGL or with compiz fusion... and then file a bug report.. 

by the way... are you having problems with your "right alt" key as well?

i have a couple of shortcuts that use alt ... (control+alt+p and control+alt+del) in kde but they dont seem to work when i have compiz fusion running... do you have this problem as well?

---

### Post by messudieh on 2007-07-21
I actually ended up figuring out how to fix the problem, but I forgot to post it. Apparently my super_L key wasn't being mapped right for compiz.

I had to put

```
xmodmap -e 'add mod4 = Super_L' 
```

into the console, and it worked right. After that I just put that command into my startup programs, and it hasn't given me a problem since.

xmodmap also shows mod4 now as 'super_L (0x7f), Hyper_L (0x80) and Super_L (0x7c).

Kinda weird, but it just works now, so I'm not complaining.

---

