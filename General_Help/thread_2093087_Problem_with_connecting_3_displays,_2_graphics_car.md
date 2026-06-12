---
title: "Problem with connecting 3 displays, 2 graphics cards"
date: 2012-12-09
forum: General Help
---

### Post by Kchymet on 2012-12-09
First off, I'm running Ubuntu 12.10 with GNOME3 (I know, I know, terrible...) instead of Unity.

I have a nice setup in my room, 2 monitors running off a GeForce 550Ti, with an HDMI connecting my TV to an ATI Radeon HD 5770. Works great on Windows, not so much on Ubuntu.

Right now the only working displays are connected to the GeForce. The ATI card is detected, but the TV it's connected to doesn't seem to be. When I go to configure displays (through the usual GUI tool), only the 2 monitors connected to the GTX card are displayed. As you can see, both cards are listed with lspci:
```
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]

07:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
07:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)

```

A quick look over at software-properties-gtk additional drivers shows that the GeForce card is running off "X.Org X server -- Noveau display driver from xserver-xorg-video-noveau (open source)" while the ATI card is on "X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)". Having tried several combinations from this list for BOTH cards, switching drivers seems to break GNOME somehow (it reverts to it's classic upper and lower panels on the main monitor without having selected classic mode on the login screen).

I've tried installing drivers directly from AMD and NVIDIA. I've also tried switching one and both monitors to the ATI card (DVI port), which still cannot be detected. It seems to me like the problem is definitely a problem with using the ATI card, but I can't tell why.

The only explanation I can think of is that since the NVIDIA card is using the Noveau driver, the ATI card isn't used because it's supposed to use a different driver, but I don't have much experience with this. What do you guys think?

If you need any more info, just post it and I'll see if I can get it to you.

---

