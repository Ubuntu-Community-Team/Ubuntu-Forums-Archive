---
title: "Change Resolution on Login Screen?"
date: 2008-05-06
forum: General Help
---

### Post by Tsukura on 2008-05-06
I'm trying to change my login screen background...but it seems the image is too big. The image displays, but it doesn't show up full screen. The bottom and right sides are cut off by a few inches.

On one, the login box can not even be seen.

Where are the images physically located in the file system?
I just dragged the archives to the login theme -> local window.
They all show up, but I can't see where to change the resolution or center/stretch/tile like you can with desktop backgrounds.

My desktop displays fine and I'm running 1280x800 resolution on a 15" laptop.

---

### Post by Tsukura on 2008-05-06
Found it on another site...

Edit your /etc/X11/xorg.conf file:
sudo gedit /etc/X11/xorg.conf

UPDATE (2008.01.29): Only remove all the offending resolutions if you do not plan on ever using them. I removed them all because I never change resolutions. And as Anne suggests in the comments below, changing your “Virtual” line to the correct resolution may also fix your problem. I say “may” because this had no effect in Ubuntu 7.10. It should work in Ubuntu 6.04 and 6.10. Anne suggests:

    Choose the resolution you want for the login (say, 1280 x 1024)
    edit your xorg.conf file.

    In the Section “Screen”, SubSection “Display”, you have two entries:
    Modes and Virtual.

    For the login, X will default to the first resolution defined in the “mode” entry. Thus, you must select the resolution you want (say, “1280×1024@60&#8243;) and move it at the first position.

    Next, the “Virtual” entry is used to have a larger desktop resolution than screen resolution (you can reach the zones “outside the screen” by moving your mouser pointer to the edges). Your Virtual section should have the same size you want for the login resolution (say 1280 1024).

---

