---
title: "installing intel graphics drivers"
date: 2007-05-14
forum: General Help
---

### Post by cptjaben on 2007-05-14
I just got a new computer for my parents. It uses [this motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131041"), the onboard video chipest is Intel GMA 950. I'm wondering how to install the graphics drivers that come built in with the motherboard.  Does anyone know how one might do this?

---

### Post by phidia on 2007-05-14
Have you tried the live cd? Ubuntu does a pretty good job of picking a driver for you and setting that up. But if you have problems give as many specifics as possible and people here will help.

---

### Post by ss87 on 2007-05-14
I have this graphics card on my laptop. As far as I am aware it was found automatically upon installation. The only problem I found was with the screen resolution. I used the 915 fix for that.

---

### Post by cptjaben on 2007-05-14
what's the 915 fix?

---

### Post by ramjet_1953 on 2007-05-15
If you are using Feisty 7.04, just copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video intel[/COLOR]

When it has done its' thing, just re-boot and your optimum video setting should be auto-detected.

Regards,
Roger 8)

---

### Post by albatroz2k on 2007-05-15
I tried this, but I got these results :(

[HTML]
sudo apt-get install xserver-xorg-video intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video is a virtual package provided by:
  xserver-xorg-video-voodoo 1:1.1.0-oubuntu2
  xserver-xorg-video-v4l 1:0.1.1-0ubuntu2
You should explicitly select one to install.
E: Package xserver-xorg-video has no installation candidate[/HTML]

---

### Post by Wim Sturkenboom on 2007-05-15
Not 100% sure (I think there's a dash missing between video and intel), but I think it must be
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by CaptainInsaneO on 2007-06-27
After trying everything I could find on the internet and several books (even the 915 solution), this fixed my res problem with my Dell 2407WFP. Thanks!

---

