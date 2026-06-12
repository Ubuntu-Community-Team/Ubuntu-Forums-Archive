---
title: "Better fonts/font rendering?"
date: 2008-04-25
forum: General Help
---

### Post by ShadowGray on 2008-04-25
There has one thing that has bugged me with Linux and Ubuntu all along... the fonts.  Maybe its just me, but the font rendering in Linux seems scratchy, especially compared to Mac or even Windows.  Even if I turn on font aliasing and upgrade to other fonts, it's still pretty bad.  Is there any way I can render fonts the way Mac does or have similar looking fonts?  Is there a how-to out there for this?

---

### Post by Ub1476 on 2008-04-25
I would install the package "ubuntu-restricted-extras" if I were you. It has a few fonts, especially for web pages which makes them look better.

Sometimes it's just the theme you're using which doesn't look very good with certain fonts.. Can you post a screenshot?

---

### Post by nge on 2008-04-25
I found that using the advanced settings (Details button) that, **subpixel smoothing** with **slight hinting** is the best. All the four defaults are rather .. ugly? 

And, oh, probably your LCD screen's pixel order is not RGB, too.

---

### Post by ShadowGray on 2008-04-25
I'm just using the standard Tango theme with subpixel rendering... maybe it's just the fonts that come with Ubuntu?

I don't know... ever since I used a mac I just love how the fonts look compared to everything else.

---

### Post by JacksonDane on 2008-04-25
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

I follow those steps after every install.

---

### Post by Ub1476 on 2008-04-25
Well, there's no problem to make Ubuntu look like OS X. Just search around on gnome-look. There's several fine fonts there (Kurier for instance).

---

### Post by amoun on 2008-08-25
Just to say I agree on this font issue. I'm a newbie here with Linux and installed Ubuntu 6 as a dual boot on my six year old Laptop (Dell 4150 XPSP2) and Ubuntu 8.0.4 on my new eeePc 900, which had Xandros.

The fonts are terrible although usable with fiddling with the options.

In windows I never needed any options, antialiasing or smudging or whatever and the font was perfect in any size with the default screen resolution.

Ubuntu, *I've no idea on other linux distros*, just can't seem to do fonts well.

Still I'm going to stick at Ubuntu as I like the idea.

It would be good to know why this has always been a problem.

TTF fonts are supposed to be vector based and should be drawn via a 'programme' that knows what screen resolution is being used and then calculates the pixels to be highlighted. Clearly the font renderer in Ubuntu can't do that.

:(

---

### Post by benny bronx on 2008-08-25
Have you tried enabling autohinting using "sudo dpkg-reconfigure fontconfig-config" My Ubuntu installs default to native and look scratchy and washed out until I enable autohinting.

Edit: I use: Autohinting, LCD smoothing-always, bitmap fonts-no.

---

### Post by Brebs on 2008-08-25
> **amoun said:**
> Clearly the font renderer in Ubuntu can't do that.
Wrong. See [thread](http://www.fedoraforum.org/forum/showthread.php?t=186789) and [massive Gentoo fonts thread](http://forums.gentoo.org/viewtopic-t-511382.html) to see the customization possible.

The problem is people ;)  Get the fonts looking perfect for one guy, and the next guy thinks they look terrible.

---

### Post by lavadisco on 2008-08-30
> **benny bronx said:**
> Have you tried enabling autohinting using "sudo dpkg-reconfigure fontconfig-config" My Ubuntu installs default to native and look scratchy and washed out until I enable autohinting.

Edit: I use: Autohinting, LCD smoothing-always, bitmap fonts-no.

Wow. This made all the difference for me.

---

### Post by dpj23 on 2008-08-30
I installed the liberation font set released by RedHat...  This is a great set of fonts that I have made all my defaults

---

