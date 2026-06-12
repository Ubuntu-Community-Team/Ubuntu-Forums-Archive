---
title: "How to use a higher resolution than the ones listed in the dropdown menu?"
date: 2007-08-04
forum: General Help
---

### Post by rainwalker on 2007-08-04
I'm setting up my sister's Insprion 7500 laptop with a fresh install of Feisty, and one of the things I'm trying to do is set the screen resolution at (Dell's weird choice of) 1450x1024. Right now, the highest one available is 1024x768. 
I added 1450x1024 to the list of resolutions in the xorg.conf file, but it still doesn't appear in the dropdown.
I've read about a "dpkg-reconfigure xserver-xorg" command, but I'm not sure about the stuff it asks about; I just want to change the resolution.
Any help would be great, thanks!

---

### Post by walkerk on 2007-08-04
> **rainwalker said:**
> I'm setting up my sister's Insprion 7500 laptop with a fresh install of Feisty, and one of the things I'm trying to do is set the screen resolution at (Dell's weird choice of) 1450x1024. Right now, the highest one available is 1024x768. 
I added 1450x1024 to the list of resolutions in the xorg.conf file, but it still doesn't appear in the dropdown.
I've read about a "dpkg-reconfigure xserver-xorg" command, but I'm not sure about the stuff it asks about; I just want to change the resolution.
Any help would be great, thanks!

what kind of video does her dell have? I suspect Intel.

whats the output of:
```
lscpi | grep Intel
```


if it is an intel video you can try out the intel video driver:
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by rainwalker on 2007-08-04
> 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
That's not the output of the command you asked, but that's the video card.

---

### Post by walkerk on 2007-08-04
> **rainwalker said:**
> That's not the output of the command you asked, but that's the video card.

oh.. an ATI. Don't have an ATI card so I'll be of no help. Sorry. Someone will step in.

---

### Post by rainwalker on 2007-08-04
Alright, well thanks anyway :)

---

