---
title: "mpv movie player and keyboard shortcuts"
date: 2014-11-13
forum: General Help
---

### Post by vasa1 on 2014-11-13
I have mpv version 0.4.2 from the software center. Is it possible to modify its keyboard shortcuts? I find that some of my Openbox (window manager) keyboard shortcuts don't work at all (Super+F normally opens Firefox but does nothing if mpv is running and is in or out of focus) or work differently (Super+DownArrow maximizes the mpv window rather than make it occupy the lower half of my screen).

/home/vasa1/.mpv is empty except for:
# Write your default config options here!

---

### Post by mc4man on 2014-11-13
That version is quite old & outdated so can't say what you can & can't set.
Have a look in /usr/share/doc/mpv/examples/, there should be an input.gz file.
copy to somewhere, extract & read thru

---

### Post by j0sk on 2014-12-10
In home folder I have hidden folder and config-file for keyboard shortcuts:
~/.mpv/input.conf

That way I was able to get G and Y button working again as it worked on mplayer:
g sub_step -1
y sub_step +1

Found it [here]("http://shellscreen.blogspot.fi/2014/11/6-channel-aac-to-ac3-on-fly-encoding-on.html")

---

