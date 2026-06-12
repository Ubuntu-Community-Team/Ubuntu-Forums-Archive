---
title: "Black screen after grub menu, cant boot failsafeX either"
date: 2017-01-11
forum: General Help
---

### Post by JoGiz on 2017-01-11
Since yesterday my Dell Latitude E7450 laptop won't boot any more. It ends up in a black screen (backlight still glows).
I can switch to terminal when the screen is black with CTRL-ALT-F1.
I have not managed to get any further with any tutorials how to solve it online.

There is some packages updated the last time it booted up yesterday. The dpkg.log with changes since it boot last time is attached.
[ATTACH]273140[/ATTACH]

I have also recorded a video how it looks like when booting normally and when nosplash quite is removed from grub boot.
The videos can be found here:
[https://goo.gl/photos/wh1mgryi7tYjgje99](https://goo.gl/photos/wh1mgryi7tYjgje99)

Anyone that can help me get my machine up and running again?
Anything else needed to figure out what is going on?

---

### Post by JoGiz on 2017-01-11
This is the boot.log as well if that gives any good information on what is going on.
[ATTACH]273141[/ATTACH]

---

### Post by JoGiz on 2017-01-11
Oh my, this was embarrassing because it was a small little error I made to a udev file yesterday that I totally forgot about.
Reverted that change and it started to boot up normal again! 
Oh, my.. Half day of my life lost :(

---

