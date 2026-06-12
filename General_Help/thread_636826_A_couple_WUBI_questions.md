---
title: "A couple WUBI questions"
date: 2007-12-10
forum: General Help
---

### Post by Valok on 2007-12-10
I just finished installing wubi on my computer and I have a few right off the bat questions.

First off, when I was installing WUBI, I got the following error a few times

"hdd error code:0x70
sense_key:0x30
asc:0x11
ascq:0x05"

I'm wondering if this is something that just happens, or if it is something I need to look into and fix.

Also, when I went to the resolution settings, the highest setting I could do was 1024x768 when I know my monitor supports higher resolutions.  Is there something I need to DL or install to modify the resolution settings?

---

### Post by tylerspaska on 2008-01-04
i don't know anything about the error codes, but you can fix the screen resolution by runing:

sudo dpkg-reconfigure xserver-xorg

it will take you though the entire x reconfigure. when you get to the screen resolution page select the options you want to have available with the space bar and then move on.

---

