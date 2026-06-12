---
title: "Blurry fonts in Hardy in some applications"
date: 2008-04-26
forum: General Help
---

### Post by werg on 2008-04-26
Particularly in the terminal and amsn. The fonts in the terminal (and in amsn) used to be crisp and clear in Gutsy. Now that I've upgraded to Hardy, they're blurry and washed out.

What happened?

---

### Post by srwalter on 2008-04-28
> **werg said:**
> Particularly in the terminal and amsn. The fonts in the terminal (and in amsn) used to be crisp and clear in Gutsy. Now that I've upgraded to Hardy, they're blurry and washed out.

What happened?

Seeing this here, too.

---

### Post by danbuter on 2008-04-28
I'm not sure, but I notice it as well. I don't use standard fonts, so it's not as bad, though.

---

### Post by danbuter on 2008-04-28
There is a bug report here, feel free to add your specifics. Currently the devs don't think it's an issue.

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/85932](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/85932)

---

### Post by danbuter on 2008-04-28
double post

---

### Post by srwalter on 2008-04-29
Fixed it by removing /etc/fonts/conf.d/53-monospace-lcd-filter.conf; can also be fixed be using the ~/.fonts.conf file in the bug report.

---

### Post by jcornwall on 2008-04-29
I had to follow this:

[http://johan.kiviniemi.name/blag/2008/01/12/ubuntu-hardy-fonts/](http://johan.kiviniemi.name/blag/2008/01/12/ubuntu-hardy-fonts/) (without the Xresources thing, that just made everything ugly)

Then remove /etc/fonts/conf.d/53-monospace-lcd-filter.conf and make sure 10-sub-pixel-rgb.conf was used (it was 10-no-sub-pixel.conf on installation). The downside to this is that the terminal font rendering speed is substantially reduced from Gutsy on NVIDIA cards.

(There's an experimental acceleration feature for this in the latest NVIDIA beta drivers. It works but turning it on breaks Compiz performance.)

---

### Post by werg on 2008-05-07
^^^

Thank you very much for the solution. But now the fonts are jaggy. :confused:. It seems unaffected by the font rendering I choose through the appearance preferences. How can I change this?

---

