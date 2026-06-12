---
title: "Problem with accents on characters"
date: 2007-09-16
forum: General Help
---

### Post by Zuinig on 2007-09-16
I've been using Xubuntu 6.06.1 LTS for a couple of weeks now, and I'm quite excited about it, especially after having "restyled" the desktop. However, there's still a problem that I haven't managed to solve, even after doing all kinds of Internet searches and trying stuff out: getting accents like ' " and ^ on letters.

What I want is just the same as I'm used to in Windows: typing the accent, and then when one types the letter, the accent automatically is placed on the character.

In Xubuntu 6.06.1 there's no GUI based tool for this yet, and yes, I've found the xorg.conf file and tried out some changes:

like:
Option "XkbLayout" "us"
Option "XkbVariant" "apostrophe"

or:
Option "XkbLayout" "us"
Option "XkbVariant" "apostrophe"
Option "XkbVariant" "intl"

or:
Option "XkbLayout" "en_US"
Option "XkbOptions" "apostrophe"

Saved the file, rebooted, but this all doesn't work. Only the American flag-button on the toolbar has changed into "UN..". 

I think pressing the accent key without seeing anything appear initially is called the "dead key". And the keyboard layout in Windows is named "US International" (in the Netherlands, which is where I'm from, we're used to the Qwerty American keyboard).

Can anyone help me out?

Thanks,
Zuinig, The Netherlands

---

### Post by jamvegan on 2007-09-16
The replies in [this thread]("http://ubuntuforums.org/showthread.php?t=534008") talk about some ways to get those characters--though not the way that you want to do it.

---

### Post by Zuinig on 2007-09-16
Thanks, I know how to get the characters the unicode-way, but I do a lot of writing and what I really want is the dead key thing with US International.

I've tried this:
Option "XkbLayout" "us"
Option "XkbVariant" "intl"


Saved it, rebooted, no results, at first at least. Although what did work was the command 
setxkbmap -model pc104 -layout us -variant intl

But maybe this had to do with the way I rebooted, because all of a sudden now it works. Possibly, when you close down (power off) your PC completely, it reboots differently compared to just doing a "Restart". Maybe that caused the setting not to be loaded.

Anyway, it's solved now; another step taken on the way to becoming an Ubuntu convert!

---

