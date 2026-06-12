---
title: "ENVY problems"
date: 2007-09-08
forum: General Help
---

### Post by randommanaki on 2007-09-08
Hello, i am extremely new to linux so i installed ubuntu. After fighting through a few problems, i got through to ubuntu and decided to install envy's drivers. After doing so, i restarted like it told me to and i now have only a black screen after the Ubuntu load screen. The system working light is constantly on, if that helps, but the black screen just stays. Any help would be appreciated. Thanks!

---

### Post by Crafty Kisses on 2007-09-08
> **randommanaki said:**
> Hello, i am extremely new to linux so i installed ubuntu. After fighting through a few problems, i got through to ubuntu and decided to install envy's drivers. After doing so, i restarted like it told me to and i now have only a black screen after the Ubuntu load screen. The system working light is constantly on, if that helps, but the black screen just stays. Any help would be appreciated. Thanks!

It sounds like you might have to reconfigure your X server, you can do this by,
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by randommanaki on 2007-09-08
i've tried reconfiguring the xserver, but there are a few questions i am unsure about, regarding the video and monitor (nv? nvidia? vega?) like i said, i'm completely new to this, and if it helps at all, even when i first tried to install/start ubuntu, i had to start in safe graphics mode. Now even that doesn't work. My laptop is an ASUS G2S, with an 8600M GT. Thanks for the try though

EDIT: i tried something i read in another forum, but it actually destroyed grub, which kinda freaked me out until i deleted and reinstalled linux. Now i am at a fresh linux install with the tty: job control unavailable problem, and if i fix that with modprobe piix, it loads but Xserver fails. I will try envy again, but i have a feeling something else is wrong.

---

