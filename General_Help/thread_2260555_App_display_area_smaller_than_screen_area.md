---
title: "App display area smaller than screen area"
date: 2015-01-12
forum: General Help
---

### Post by DuckHook on 2015-01-12
I support Linux installations for some friends and family, but in all my years doing so, have not run across anything like this one. Googling was singularly unhelpful, returning hits mostly having to do with changing monitor resolutions, which is NOT the following problem:

A family member has Lubuntu 14.04 installed and has monkeyed around with some settings but no longer remembers what she did. The result is a working display area that does not fit her screen area/monitor resolution. Screenshot attached below. There is a border of white space on three sides that now intrude into her screen. Note LxPanel is fine and stretches across the full horizontal width at bottom. Also, the mouse travels into this white space. But app display boundaries end at start of white space, app windows will only display and can only be manipulated inside wallpapered area and desktop icons will not "stick" outside of it either, so the problem is not just undersized wallpaper. Setting wallpaper to any stretch or tile configuration doesn't do a thing.

Lubuntu does not have a *monitors.xml* file in *~/.config* nor anywhere else, it seems, so I'm stumped. Things already tried:

1. No setting in *Openbox Configuration Manager* to adjust display area. Changing to a different theme doesn't fix.
2. *Monitor Settings* shows nothing out of the ordinary and the correct 1920x1080 resolution.
3. *xrandr* shows nothing out of the ordinary (as expected, since mouse travel covers all of screen and LxPanel is fine).
4. LxPanel settings all look like they are default.
5. Booting into guest session yields a proper desktop with display extended fully to all edges.
6. xorg.conf does not exist and I lacked the time to create and configure one.

Some things provisionally ruled out:

1. Unlikely to be the driver&#8213;not if guest session is working fine, mouse travel is fine, LxPanel is fine, etc.
2. Unlikely to be global xorg settings either for same reasons as above.

Therefore, likely an LXDE setting, but which one? And if so, where, and how do I get at it?

Unfortunately, I had limited time on site and have no access to her machine at the moment, so cannot try out anything further for some days.

As always, all suggestions/insights appreciated.

---

### Post by vasa1 on 2015-01-12
>  1. No setting in Openbox Configuration Manager to adjust display area. 
What about the "margins" tab in ObConf?

In ~/.config/openbox/lubuntu-rc.xml, I have:
```
  <!-- You can reserve a portion of your screen where windows will not cover when
     they are maximized, or when they are initially placed.
     Many programs reserve space automatically, but you can use this in other
     cases. -->
  <margins>
    <top>0</top>
    <bottom>0</bottom>
    <left>0</left>
    <right>0</right>
  </margins>

```

---

### Post by DuckHook on 2015-01-12
Should have mentioned that I also checked margins, but only graphically. They are all set to 0 ("zero"). I will check them again in actual conf file when I have the chance to get back to her machine.

Thanks for reminder.

---

### Post by vasa1 on 2015-01-12
> **DuckHook said:**
> Should have mentioned that I also checked margins, but only graphically. They are all set to 0 ("zero"). I will check them again in actual conf file when I have the chance to get back to her machine.

Thanks for reminder.
If they are all set to zero in ObConf, that should also reflect in lubuntu-rc.xml.

Could you also open a terminal and run **openbox --reconfigure**? If there isn't a problem, you should just get back the prompt. If there is a parsing error, you'll get a pop-up. If there is a parsing error, it's *possible* that Openbox won't read lubuntu-rc.xml correctly.

Other troubleshooting options would be to try a new user or to log into Openbox. All the best!

---

### Post by DuckHook on 2015-01-12
My understanding is that if it's margins, she would still be able to move windows into the space: windows just won't start up or maximize into them. But in her case, the space is entirely off limits, and even the background wallpaper won't extend into them. In a perverse way, it's actually a rather fascinating breakage because I didn't know that desktop/window managers could even *do* that. Behaves almost as a window within a window. I thought maybe the sync between display size and screen size in X was broken, but this would have affected LxPanel too. All very odd.

Will try resetting openbox and post the results in a few days.

---

### Post by vasa1 on 2015-01-13
> **DuckHook said:**
> My understanding is that if it's margins, she would still be able to move windows into the space:...
I just checked that. You're right. Hope you find a solution!

---

