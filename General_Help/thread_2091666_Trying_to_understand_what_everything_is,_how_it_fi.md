---
title: "Trying to understand what everything is, how it fits together, how to fix an issue"
date: 2012-12-05
forum: General Help
---

### Post by koalaJason on 2012-12-05
Im a bit exasperated from going over alot of data so what follows will probably sound retarded. This is what Ive figured out from staring at these forums / wikipedia and google all day. PLEASE correct me where Im wrong, or add pertinent info!!

Ok, GNOME is just how the desktop looks, its a 'skin' that can be switched. Unity is the default skin for 12.04. GNOME and Unity dont care what driver you use for your video card. If youre having problems with an ancient nvidia driver, digging into GNOME or Unity isnt going to help. I have no idea how to switch between GNOME and Unity (although I did install GNOME)

Nouveau is a catch-all for graphics drivers : if you dont have a video driver installed, this will run the video. I have no idea how to check if nouveau is 'running' or how to 'run' it. I have no idea how to switch to / from it.

Jockey is a built in program that makes it easy *cough* to switch drivers. It does not work with all drivers.

Nvidia does not currently have drivers for the geforce fx 5300. If you have 2 monitors, the best you can get is the same image on both monitors with the settings->Displays telling you that you are using a pink screened laptop.

---

### Post by Rebelli0us on 2012-12-05
You didn't ask a question! 

Ubuntu no longer uses gnome, if you prefer gnome just install Linux Mint MATE version 14, it includes NVIDIA driver so you won't have to do anything else.

---

### Post by jerome1232 on 2012-12-05
> **Rebelli0us said:**
> You didn't ask a question! 

Ubuntu no longer uses gnome, if you prefer gnome just install Linux Mint MATE version 14, it includes NVIDIA driver so you won't have to do anything else.

Errrr, ummmmmmm. Yes, it does use Gnome, it always has. It just uses Unity as a shell instead of Gnome3's default gnome-shell as a shell.

This thread doesn't really have a request for support of any type, did you have a particular problem you need help with OP (original poster)?

---

### Post by koalaJason on 2012-12-06
Im hoping for clarification that what Im learning is accurate. I feel like Im missing big important pieces related to the above  mentioned stuff. If you see inacurate information, or would like to expand on any of it, please tell me.

---

### Post by jerome1232 on 2012-12-06
> **koalaJason said:**
> Im hoping for clarification that what Im learning is accurate. I feel like Im missing big important pieces related to the above  mentioned stuff. If you see inacurate information, or would like to expand on any of it, please tell me.

"Gnome" is a desktop environment, it's not just a skin, it also a suite of applications and libraries to make a unified look and feel. Similarly KDE, XFCE, and LXDE are all desktop environments with their own suites of applications, libraries, and ways of doing things.

Nouveau is an open source driver for Nvidia graphics cards, it works well with 2d, but 3d isn't well supported. If you need opengl support you would want to use nvidia's drivers, which are provided by the additional drivers tool (aka jockey).

5300 FX would likely be supported by the legacy nvdia driver, nvidia-173 I think it is called.

---

### Post by NightsShadeQueen on 2012-12-09
And if you're trying to use Gnome and not Unity, it's a choice at login. Click the Ubuntu login next to your username.

[http://www.khattam.info/howto-install-gnome-shell-gnome-3-in-ubuntu-11-10-oneiric-ocelot-2011-10-22.html](http://www.khattam.info/howto-install-gnome-shell-gnome-3-in-ubuntu-11-10-oneiric-ocelot-2011-10-22.html)

for images.

---

