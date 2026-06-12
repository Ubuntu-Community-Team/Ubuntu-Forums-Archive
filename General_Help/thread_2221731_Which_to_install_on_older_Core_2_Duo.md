---
title: "Which to install on older Core 2 Duo?"
date: 2014-05-03
forum: General Help
---

### Post by mlepage on 2014-05-03
I have an older laptop, Core 2 Duo, 2.2 GHz, 3 GB RAM, with a fast SSD drive and an NVIDA GPU (8400M GS).

I would like to install an LTS (sole OS) and keep it that way until the hardware dies. It will be used mostly for light use: web, email, flash games. Maybe eventually it will run a light Windows in VirtualBox, but not initially.

My choice is between the older 12.04 or the newer 14.04, and between 32-bit and 64-bit.

For hardware of that era, which would be best to install? 64-bit Trusty Tahr? 32-bit Precise Pangolin? Or another combination.

It might help if a bit of reasoning is provided. Such as "14.04 64-bit won't work well on Intel Core 2 Duo because of XYZ..."

---

### Post by LastDino on 2014-05-03
Ubuntu LTS 14.04 Or Xubuntu 14.04 if you like older light desktop look.

Your hardware is way above minimum, I'm using P4 single core and both; Ubuntu and Xubuntu runs well ^^

I would generally go with x32 but you can go with x64 if you're actually going to use any x64 bit application. You see, 32 bit applications use little bit more resource on 64 bit OS (from my observations) and if you've no plans to use any 64 bit apps, stick with x32 :3

---

### Post by ibjsb4 on 2014-05-03
Sounds like to me that you could run any flavor of buntu on that.  If you burn a live dvd, you would get the option of trying it out without installing.  It is of course slower this way, but gives you a test drive :)

---

### Post by tgalati4 on 2014-05-03
I would stick with 64-bit, since most applications are built to 64-bit addressing.  Yes, 64-bit uses more RAM because the addressing takes up more space, but any new debian packages or new applications will be built with 64-bit.  I would only install 32-bit on really old hardware that has only a 32-bit processor.  Many older Xeon processors are 32-bit, for instance.  Then you have no choice.

---

### Post by monkeybrain20122 on 2014-05-03
With that kind of specs you can run full blown Ubuntu without any problem.

---

### Post by Yellow Pasque on 2014-05-03
64-bit, because you have more than enough RAM and it will make virtualization faster.

---

### Post by mlepage on 2014-05-03
Sounds like 64-bit 14.04 is the way to go then. Thanks.

---

### Post by pfeiffep on 2014-05-03
I running 14.04 on my old Dell (specs in sig). Since Unity 3d was really sluggish I installed gnome flash back /  metacity. Breathed new life into the old girl!

---

