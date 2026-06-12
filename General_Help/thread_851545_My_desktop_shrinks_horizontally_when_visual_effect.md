---
title: "My desktop shrinks horizontally when visual effects are enabled in ubuntu"
date: 2008-07-06
forum: General Help
---

### Post by trossthree on 2008-07-06
Greetings

I am using the Nvidia Geforce FX 5600 ultra video card and a Westinghouse wide screen LCD monitor. I have my resolution set to 1280x800.

The issue is when I enable the visual effects in Ubuntu/Gnome my desktop shrinks horizontally and part of the desktop is not viewable unless I scroll down with the mouse but the resolution setting remains the same.

Thanks

---

### Post by psyopper on 2008-07-06
Install CompizConfig Settings Manager:
```

sudo aptitude install ccsm

```

Open CCSM at System > Preferences > CompizConfig Settings Manager

In General Options > Display Settings Tab > Outputs

Put a check mark in detect outputs. If that doesn't work then make a manual output 1280x800x0x0.

---

### Post by trossthree on 2008-07-06
Greetings,

I am still having the same problem. I will try to describe it a little better in my original post.

Thanks

---

### Post by trossthree on 2008-07-07
Hello,

Can anyone help?

Thanks

---

### Post by psyopper on 2008-07-13
Could you please post a copy of your /etc/X11/xorg.conf here, between, between code tags.

Thanks!

---

