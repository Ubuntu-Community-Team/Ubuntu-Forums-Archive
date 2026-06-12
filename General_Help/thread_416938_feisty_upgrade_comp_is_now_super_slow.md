---
title: "feisty upgrade: comp is now super slow"
date: 2007-04-21
forum: General Help
---

### Post by jexdawg13 on 2007-04-21
my computer isn't exactly top of the line, but it ran 6.10 decently.

after upgrading to feisty, it's now very noticeably slower. my music (through rhythmbox) never used to skip - now when i go to a new website in swiftfox my entire system will hang, my music will stop, and my computer will basically freeze for 2 or 3 seconds.  as far as programs and compatibility, everything still works, it's just a lot slower. i've tried switching from bash to dash and back a few times, but it doesn't seem to help.

when i open something like the gimp, and look at my system monitor panel app, the whole thing turns a solid black.. my resources are 100% taken from opening one program. i only have 512 mb ram, but still, the gimp shouldn't gimp out my computer.

i'll be happy to provide any additional information, and any feedback at all is welcomed.


thanks in advance.

---

### Post by Gathalimay on 2007-04-21
Yeah. . .same thing happens here. It happens with Rhythm box and Totem. Amarok no longer asks to install the codecs and no music plays on it whatsoever. Please help ](*,)

---

### Post by BrokeBody on 2007-04-21
I know it's a bit dumb question, but... Did you set up your swap partition? :)

---

### Post by Gathalimay on 2007-04-21
Yes. . .

I started using ubuntu since Edgy. . .I didn't know what I was doing when I first did it so I tried installing without setting the swap. It forces you to make a swap. I looked it up and found out what it was.

If I remember correctly, a good size was double the amount of RAM you have. I have 768 but I put 2 gigs in for swap. That should be fine (that's what I had before)

---

### Post by Ziggy72 on 2007-04-21
If your installation of Dapper worked ok then I'm pretty sure that some compatibility issues arose during your upgrading process. Personally I now never use upgrades - always a fresh install. I would suggest you start again with a fresh install otherwise you're likely to create another problem when (if) you solve your current dilemma.

---

### Post by FluffyElmo on 2007-04-21
Try running *sudo apt-get update* and then *sudo apt-get dist-upgrade*, repeat the dist-upgrade until there is nothing to be done. In the past it has taken me two or three updates until everything could be resolved. I'd also suspect your xorg.conf, it's possible that your video driver was reset when upgrading so it's probably worth downloading and reinstalling the commercial driver for your chipset.

A few other thoughts, Try running *top* from a terminal to see if any processes are using an excessive amount of CPU or RAM. Check your disk drives to make sure DMA and 32bit support are enabled, for instance *sudo hdparm /dev/hda*. Check the output of *dmesg* right after boot to see if there are any errors, it's probably worth posting the output of dmesg here so people know what you're running. 

Also, *GKrellM * will give much more detailed reports than top or system monitor. It may be worth installing if you think it may be hardware driver related and want to narrow things down. Search the forum for instructions, it's not too difficult but  it takes a few steps.

---

