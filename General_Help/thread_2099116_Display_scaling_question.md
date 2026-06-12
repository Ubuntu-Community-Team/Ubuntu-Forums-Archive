---
title: "Display scaling question"
date: 2012-12-28
forum: General Help
---

### Post by DaveBaxter on 2012-12-28
Hi, sorry if this has been answered elsewhere (I did search but couldn't find a solution).

I'm currently dual booting Windows 7 & Ubuntu 12.10 on my laptop, (ASUS x54c with Intel GFX).
When i have my laptop at home I connect it to my 32" 1080p LCD via HDMI and in doing so I have the following problem.

My TV automatically displays the image at 1080p which makes all of the icons and text to small for my eyes, (I realise I can increase font sizes etc but then I have to resize them when I switch back to my laptops display)

Now under Windows 7 I can render the display at my laptops native resolution 1366x768 and then scale it to 1080p which results in a perfectly sharp mirror of my laptops display.

However under Ubuntu I can either output at 1080p (not an option for me) Or mirror the laptops display which results in icon sizes, fonts etc being identical to my laptops display which is what I want, But it's blurry as hell and looks awful.

tldr; I'm looking for a way to output the display to my TV at 1366x768 and then scale it to 1080p rather than outputting directly at 1080p or filling a 1080p screen with an unscaled 1366x768 image.

This is the only thing stopping me from leaving Windows behind. :-k

---

### Post by DaveBaxter on 2013-01-05
Hope-full BUMP :D

---

### Post by pqwoerituytrueiwoq on 2013-01-05
try setting the resolution to 1366x768
i don't know which GPU driver you are using, so i cant say more (open source, AMD, nVidia)

---

### Post by DaveBaxter on 2013-01-05
> **pqwoerituytrueiwoq said:**
> try setting the resolution to 1366x768
This makes everything really blurry and ugly. (Win 7 creates a 1366x768 image in the center of a 1080p screen and then scales it to fill the screen)<--- this is what i want Ubuntu to do.

> **pqwoerituytrueiwoq said:**
> i don't know which GPU driver you are using, so i cant say more (open source, AMD, nVidia)

Intel

---

### Post by pqwoerituytrueiwoq on 2013-01-05
[http://linux.die.net/man/4/intel](http://linux.die.net/man/4/intel)
maybe something useful here
i am sleepy and don't feel like experimenting
this is something i would like to know myself (for my mom)

---

### Post by DaveBaxter on 2013-01-05
> **pqwoerituytrueiwoq said:**
> [http://linux.die.net/man/4/intel](http://linux.die.net/man/4/intel)
maybe something useful here
i am sleepy and don't feel like experimenting
this is something i would like to know myself (for my mom)

Unfortunately, the info in that link is beyond me. I want to make a switch to full time Linux, But not badly enough to learn what all of that means.....

Guess I'll have to carry on dual booting.

---

### Post by DaveBaxter on 2013-01-19
I have marked this as solved.

It turns out that when I output a non standard HD resolution to my TV via HDMI, The TV sets ridiculous Gamma/Black level settings for the input.

After a bit of fiddling with settings I now have a perfect mirrored display at 1366x768 on my TV. :D

---

