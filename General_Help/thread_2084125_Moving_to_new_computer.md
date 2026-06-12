---
title: "Moving to new computer"
date: 2012-11-14
forum: General Help
---

### Post by CyberCowboy on 2012-11-14
I've got a current install of 12.04 X64 bit Ubuntu Server running on a Dell Optiplex 755 Intel Quad Core Core2 setup.  I'd like to move it to a Dell Precision T7500 with as little disruption to the existing structure as possible.

I know Linux has a huge amount of hardware detection it does on bootup, but am I able to move the hard drive from the Optiplex directly into the Precision and call it good (I'm guessing not.) I know that won't work in the Windows world but I also know *nix beats them in almost every category so I"m not sure how likely this is.

If not what is the best way to move installed packages (preferably with existing config if possible) ppa's and such to the new box.

---

### Post by gerowen on 2012-11-14
> **CyberCowboy said:**
> I've got a current install of 12.04 X64 bit Ubuntu Server running on a Dell Optiplex 755 Intel Quad Core Core2 setup.  I'd like to move it to a Dell Precision T7500 with as little disruption to the existing structure as possible.

I know Linux has a huge amount of hardware detection it does on bootup, but am I able to move the hard drive from the Optiplex directly into the Precision and call it good (I'm guessing not.) I know that won't work in the Windows world but I also know *nix beats them in almost every category so I"m not sure how likely this is.

If not what is the best way to move installed packages (preferably with existing config if possible) ppa's and such to the new box.

As long as the processors are similar (both 64 bit, both AMD or both Intel) you should be good to go.  I did this once and on the first boot after moving it, there was a ton of hardware detection, it rebooted, and then it was g2g.

Edit: Any software that you compiled yourself will have to be re-compiled.

---

### Post by Cheesemill on 2012-11-14
It should just work. Even moving between Intel and AMD processors shouldn't be an issue. I've done this with desktop systems more times than I can recall.

The only times you come across problems with moving an OS like this is when you have restricted drivers installed, usuall on a desktop system when moving from Nvidia to AMD graphics for example (but even this isn't really a problem if you remove the restricted drivers first).

---

### Post by CyberCowboy on 2012-11-14
excellent, I'm not sure why I need a home server with (ultimately) 2 xeon quad core processors but since it does do transcoding on the fly I figured it'd be nice to have.

Thanks again.

---

### Post by CyberCowboy on 2012-11-14
Erm didn't realize I hadn't mentioned I was going from a Core2 to a Xeon chip, but from what I'm reading in both your replies that shouldn't be an issue either correct?

---

### Post by Cheesemill on 2012-11-14
That should be fine.

---

