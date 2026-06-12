---
title: "CLI Resolution"
date: 2015-07-13
forum: General Help
---

### Post by PJs Ronin on 2015-07-13
Have wondered about this for years and never had any success googling for an answer, so here goes.

I have a decent desktop computer, bags of RAM, Intel chipset and Nvidia GeForce GTX650 graphics card running Ubuntu 14.04 (and others).   Everything on the graphics side is great, but when I CTRL-ALT-F1 to get a CLI session the resolution is a pretty chunky 80 columns wide.   Naturally, when doing a sudo apt-get update or sudo apt-get dist-upgrade the text lines break to a new line once the 80 char limit is reached; makes following what's happening difficult.   I did an install of Mate a couple of years ago and noticed that the CLI session for that was a much higher resolution, but I could never figure out why.

Obviously I'm missing something pretty basic here.   Is there a command I can issue to get the CLI session into a higher text mode?

Appreciate assistance.

---

### Post by sudodus on 2015-07-13
Try according to this link

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

particularly this paragraph

[https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions](https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions)

Remember to run

```
sudo update-grub
```

after changing the configuration file

Edit: It should work with the grub menu, but may not work at ***ctrl + alt + F1*** with some of the proprietary nvidia drivers.

---

### Post by PJs Ronin on 2015-07-13
> **sudodus said:**
> Try according to this link

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

particularly this paragraph

[https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions](https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions)
   I've used this for some time and love it.   On my system the Grub splash page (pre Nvidia drivers being loaded) is at the higher resolution, so your comment > Edit: It should work with the grub menu, but may not work at ***ctrl + alt + F1*** with some of the proprietary nvidia drivers. makes sense.

I did a quick test and blew away all Nvidia drivers and sure enough the CTRL+ALT+F1 screen is now at higher resolution.

Many thanks. :)

---

### Post by sudodus on 2015-07-14
You are welcome :-)

If the performance of the graphics for playing video is OK with the free 'nouveau' driver, fine! Otherwise I'm afraid that you have to sacrifice higher quality text screen graphics. I would be happy if someone can chip in and tell us how to get higher quality text screen graphics with nvidia proprietary drivers.

---

### Post by PJs Ronin on 2015-07-14
Video in VLC looks ok, just missing some 'pizazz' I think... will do some experiments.

Edit:   VLC crashed a couple of times and the video just lacked a certain 'pop'.   Back to Nvidia drivers :(

---

