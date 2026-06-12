---
title: "resolution not working"
date: 2006-10-31
forum: General Help
---

### Post by bliind on 2006-10-31
Okay, I have an issue. I started messing around with beryl and I somehow lost my 1280*1024 resolution. In an effort to get it back, I played with my xorg.conf, and actually took out all other resolutions from it. However, all the options are still in the Screen Resolution dialog and I still cannot get 1280*1024. Yes, I restarted X, I even rebooted my computer. It's as if my xorg.conf is not being read. Are there other files that influence screen res?

---

### Post by iamhugeinjapan on 2006-10-31
Did you try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can select screen resolutions in that....

---

### Post by bliind on 2006-10-31
> **iamhugeinjapan said:**
> Did you try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can select screen resolutions in that....

No, I didn't. I decided to mess with my xorg.conf manually, and I set the resolution to use, and there is only *one* resolution (1280*1024) in my xorg.conf to use, and despite that fact, I'm in 1024x768, and there are options for 800x600, 640x480, etc in the "Screen Resolution" dialog..

---

### Post by CatKiller on 2006-10-31
> **bliind said:**
> Are there other files that influence screen res?

Yes. The BIOS of your video card.

For your missing resolution, you'll probably want to add the monitor refresh rate ranges to the Monitor section of your xorg.conf.

---

### Post by bliind on 2006-10-31
> **CatKiller said:**
> Yes. The BIOS of your video card.

For your missing resolution, you'll probably want to add the monitor refresh rate ranges to the Monitor section of your xorg.conf.

I did add the monitor refresh rates. Besides the fact, 1280*1024 is the *only* resolution in my xorg.conf - yet my resolution is 1024*768. I see a problem.

1280*1024 WAS working, before I started playing around with Beryl.

---

### Post by bliind on 2006-10-31
I found it out, thanks to the help of Amaranth and #ubuntu-xgl

I needed to have the following option in my xorg.conf:
        Option          "UseEdid" "false"
because otherwise, the card does what the monitor says, and not what the system says. So, anyone else with that problem, that's what you need :]

---

