---
title: "AIGLX Problem"
date: 2006-08-23
forum: General Help
---

### Post by Sirin on 2006-08-23
Hello, I am trying to use AIGLX. I followed every step on this page: [http://www.ubuntuforums.org/showthread.php?t=145068&highlight=XGL+COmpiz](http://www.ubuntuforums.org/showthread.php?t=145068&highlight=XGL+COmpiz), but when I start up GDM, it just shows a frozen screen of my wallpaper with my mouse (which I can't move). I can hear the drum sound of the login page, and I can enter my username and password (even though I can't see it), press enter, and hear the login sound, but only 2 seconds later, I'm taken back to the login page, with the same screen as before (the wallpaper). It seems to only happen when I edit /etc/gdm/gdm.conf-custom to add

```
[servers]
0=aiglx 

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
```

My card is an Intel Integrated i810 82865G.

---

