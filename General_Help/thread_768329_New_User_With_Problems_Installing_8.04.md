---
title: "New User With Problems Installing 8.04"
date: 2008-04-26
forum: General Help
---

### Post by SamuelRSmith on 2008-04-26
I'm trying to be a new user to ubuntu, as the Vista SP1 "update" (term used lightly) has left me without sound, and this has finally pushed me over the edge to try something new.

So I downloaded 8.04 Ubuntu for AMD64 systems, created the disc, and booted the system from the disc.

Before installing, I decided to check the disc integrity, but I hit a little snag: when I went to load into the interrity checker two progress bars loaded up, with the second one being slightly lower, and slightly further to the right than the main progress bar, after about 20 seconds, the system rebooted itself.

Determined to get this to work, I tried it several times, and I also tried booting into the Live CD thing, and I had the same problem. Then, to check the disc, I placed the disc into another machine, and the disc integrity checker functioned correctly.

I have decided against downright installing Ubuntu as I fear that it could have other, negative effects on my system and maybe (for some unknown reason) uninstall Vista (which I am intending to keep for gaming and homework purposes). I have also decided not to use Wubi for the same reason.

My specs are:
Processor: AMD Athlon 64 X2 Dual Core Processor 5600+ 2.8GHz
BIOS: Pheonix AwardBIOS v6.00PG
Chipset: nForce 500
RAM: 4gb @ 800MHz
HDD: 500gb
GFX: nVidia 8800gt 512mb

I hope that's enough for you guys to help me out with my situation.

Thanks in advance,
Samuel

---

### Post by overdrank on 2008-04-26
> **SamuelRSmith said:**
> I'm trying to be a new user to ubuntu, as the Vista SP1 "update" (term used lightly) has left me without sound, and this has finally pushed me over the edge to try something new.

So I downloaded 8.04 Ubuntu for AMD64 systems, created the disc, and booted the system from the disc.

Before installing, I decided to check the disc integrity, but I hit a little snag: when I went to load into the interrity checker two progress bars loaded up, with the second one being slightly lower, and slightly further to the right than the main progress bar, after about 20 seconds, the system rebooted itself.

Determined to get this to work, I tried it several times, and I also tried booting into the Live CD thing, and I had the same problem. Then, to check the disc, I placed the disc into another machine, and the disc integrity checker functioned correctly.

I have decided against downright installing Ubuntu as I fear that it could have other, negative effects on my system and maybe (for some unknown reason) uninstall Vista (which I am intending to keep for gaming and homework purposes). I have also decided not to use Wubi for the same reason.

My specs are:
Processor: AMD Athlon 64 X2 Dual Core Processor 5600+ 2.8GHz
BIOS: Pheonix AwardBIOS v6.00PG
Chipset: nForce 500
RAM: 4gb @ 800MHz
HDD: 500gb
GFX: nVidia 8800gt 512mb

I hope that's enough for you guys to help me out with my situation.

Thanks in advance,
Samuel

HI and welcome, Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by SamuelRSmith on 2008-04-26
I don't know what a 'checksum' is, so I just followed the steps.

And apparantly, the MD5 check sums are the same.

---

### Post by GuitarRocker2562 on 2008-04-26
Wubi can't unistall or mess up your Vista, it is your best bet.The problem you describe sounds like something that can be from your video card, which one are you using?

---

### Post by SamuelRSmith on 2008-04-26
@GuitarRocker2562

I'm using an nVidia 8800gt.

---

### Post by GuitarRocker2562 on 2008-04-26
that sounds like your problem, unfortunately I don't do anything graphics intensive, so I have some crappy intel card, I can't help you out in this feild. However, I am sure someone can.

---

### Post by SamuelRSmith on 2008-04-26
I would of thought that the newer cards would have been fine with it, though, and that older cards would be the ones with the problem. Is there something I'm missing, here?

Oh, and if I use Wubi, and it is the graphics card, will the problems persist after I've installed Ubuntu, or will it then load specialised drivers, or something?

---

### Post by overdrank on 2008-04-26
> **SamuelRSmith said:**
> I would of thought that the newer cards would have been fine with it, though, and that older cards would be the ones with the problem. Is there something I'm missing, here?

Oh, and if I use Wubi, and it is the graphics card, will the problems persist after I've installed Ubuntu, or will it then load specialised drivers, or something?

Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet and add add vga=771 or you may try 775. Then press enter.

---

### Post by SamuelRSmith on 2008-04-26
> **overdrank said:**
> Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet and add add vga=771 or you may try 775. Then press enter.
Just tried that, 771 had exactly the same problem. 775 completly crashed the system.

---

### Post by overdrank on 2008-04-26
> **SamuelRSmith said:**
> Just tried that, 771 had exactly the same problem. 775 completly crashed the system.

Ok did you try with just removing the quiet splash and see any errors?

---

### Post by SamuelRSmith on 2008-04-26
> **overdrank said:**
> Ok did you try with just removing the quiet splash and see any errors?
OK, just tried that.

The only things that I could see (most of the stuff was happening too fast for me) that looked like errors were:

"Driver 'sd' needs updating", with some text following that and
"Driver 'sr' needs updating", also with some text following that

---

