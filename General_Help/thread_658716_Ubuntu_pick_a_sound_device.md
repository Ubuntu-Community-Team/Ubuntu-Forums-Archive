---
title: "Ubuntu pick a sound device"
date: 2008-01-04
forum: General Help
---

### Post by Holonet on 2008-01-04
Ubuntu (7.10) seems to have a mind of its own when it comes to my sound devices.  I have a Gigabyte motherboard with Realtek on-board sound.  Since that is not sufficient for my needs, I also have a SoundBlaster Live! card, which I have hooked up to speakers.  The problem is, whenever Ubuntu boots up, it picks one or the other to pump my sound out of, regardless of settings.  It appears to be completely random, so much as I can tell.  The only way to correct this is either switch where I plug my cables to the back of my computer, or reboot until it "picks" the sound device I want.  Anyone know what the devil's going on? :mad:

---

### Post by yabbadabbadont on 2008-01-04
There is no guarantee in what order the hardware will be detected and the modules loaded...  which you have discovered.  The simplest thing to do, is to disable the on-board sound card in your BIOS.  (assuming that you don't use it)  That is what I ended up doing.  There is another way to handle it with a proper alsa config in your modprobe.conf, but I'm not running Ubuntu at the moment, so I can't walk you through it.  Basically though, you can specify which alsa modules are designated as sound card 1 and which are sound card 2.  That way it doesn't matter which order the modules get loaded.

---

### Post by Holonet on 2008-01-04
Thanks.  I disabled it in BIOS.  I was thinking I had missed a preferred device setting somewhere, but I guess they just haven't implemented that in Ubuntu yet.

---

### Post by ~LoKe on 2008-01-05
> **Holonet said:**
> Thanks.  I disabled it in BIOS.  I was thinking I had missed a preferred device setting somewhere, but I guess they just haven't implemented that in Ubuntu yet.

I really wish there was a GUI for this, as you can do it with modprobe and just need a GUI to list your cards and allow you to pick one and choose its index.  I just keep rebooting until my onboard takes the lead.

---

### Post by yabbadabbadont on 2008-01-05
```
alias snd-card-0 snd-emu10k1
alias snd-card-1 snd-ens1371
options snd cards_limit=2
```
This is the type of thing you need to configure in modprobe.conf

Your specific alsa modules will differ of course.

---

### Post by ~LoKe on 2008-01-05
Hm...what would I write in if I wanted my Intel card as default?
> [00:34:13 loke]$ asoundconf list
Names of available sound cards:
Intel
CMI8738MC6

---

### Post by yabbadabbadont on 2008-01-05
> **~LoKe said:**
> Hm...what would I write in if I wanted my Intel card as default?

Use lsmod to find the list of loaded modules.  Then look for snd-* to see if you can recognize the correct one.  Otherwise you would need to look it up on the alsa projects website.  They have a nice table showing all the modules and supported cards.

Edit: By the way, I really like the new avatar.

---

### Post by yabbadabbadont on 2008-01-05
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

There are three different modules, depending upon chipset.

---

