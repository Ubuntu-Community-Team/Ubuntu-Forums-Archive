---
title: "Tearing in Ubuntu 14.04 on integrated graphics"
date: 2016-06-09
forum: General Help
---

### Post by nester17 on 2016-06-09
Hello,

I posted a thread on this in December 2015 that can be found here.

[http://ubuntuforums.org/showthread.php?t=2307118](http://ubuntuforums.org/showthread.php?t=2307118)

I used a program made by [COLOR=#DD4814][mc4man]("http://ubuntuforums.org/member.php?u=320715") [/COLOR] to rewrite the xorg.conf with a tearfree option file every time I switched between graphics. It worked at first but now whenever I switch to my Integrated Intel Graphics I get tearing. I have no tearing when I switch to my nvidia card in PRIME profiles.

I'm thinking maybe the problem is that there's no xorg.conf file when I have Intel graphics switched on (Only a xorg.conf.xxxxxxxx file)

It's possible for me to use my graphics card but I would prefer to use Intel graphics most of the time for many reasons (power consumption, less heat, etc.)

How can I get my integrated graphics to be "TearFree" like my graphics card is?

Thanks.

---

### Post by mörgæs on 2016-06-09
With a processor that new I would not expect 14.04 to work. Better to begin with a fresh install of 16.04.

---

### Post by nester17 on 2016-06-10
It was working fine before but it seems like something changed somehow, and newer versions of ubuntu would still have compositing right?

---

### Post by mörgæs on 2016-06-10
Yes, Ubuntu has composing but X/Lubuntu don't. Please try a selection of them and post the results.

---

### Post by nester17 on 2016-06-12
> **mörgæs said:**
> Yes, Ubuntu has composing but X/Lubuntu don't. Please try a selection of them and post the results.

Surely there's a workaround I can use to circumvent this problem. That's what I'm looking for.

---

### Post by mc4man on 2016-06-12
Typically there should be no tearing with Intel, still isn't here with both Haswell & Skylake. (Skylake is just on 16.04, Haswell has both 14.04.1 & 16.04

As far as hacking around tearing with nvidia mobile chips that would get much more problematic with mesa 11 as Ubuntu has disabled sna, have you happened to upgrade your mesa to the lts~wily in 14.04?

Otherwise you could search out how to add an xorg.conf for Intel, many users of clutter need to do that. How that would work with nvidia-prime & gpu-manager no idea, possibly not well..

Could go something like this though do search... - 
create /etc/X11/xorg.conf.d/20-intel.conf

(- sudo mkdir -p /etc/X11/xorg.conf.d && sudo nano /etc/X11/xorg.conf.d/20-intel.conf

put in - 
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option "TearFree" "true"
EndSection
```
Save - (on keyboard, ctrl+o enter ctrl+x
Reboot & see
(when booting to Intel by default tearfree is disabled, no clue why.. though never mattered here. With above file you'd get what's shown in screen for better or worse.

---

### Post by nester17 on 2016-06-12
> **mc4man said:**
> Typically there should be no tearing with Intel, still isn't here with both Haswell & Skylake. (Skylake is just on 16.04, Haswell has both 14.04.1 & 16.04

As far as hacking around tearing with nvidia mobile chips that would get much more problematic with mesa 11 as Ubuntu has disabled sna, have you happened to upgrade your mesa to the lts~wily in 14.04?

Otherwise you could search out how to add an xorg.conf for Intel, many users of clutter need to do that. How that would work with nvidia-prime & gpu-manager no idea, possibly not well..

Could go something like this though do search... - 
create /etc/X11/xorg.conf.d/20-intel.conf

(- sudo mkdir -p /etc/X11/xorg.conf.d && sudo nano /etc/X11/xorg.conf.d/20-intel.conf

put in - 
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option "TearFree" "true"
EndSection
```
Save - (on keyboard, ctrl+o enter ctrl+x
Reboot & see
(when booting to Intel by default tearfree is disabled, no clue why.. though never mattered here. With above file you'd get what's shown in screen for better or worse.

That did the trick, thanks for your help for the second time now. I'm still not sure why I started to get tearing with my intel chip though.

---

