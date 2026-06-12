---
title: "totem really skippy"
date: 2005-11-01
forum: General Help
---

### Post by matva on 2005-11-01
Totem player is skippy when playing dvds off disks. Anyway to fix this or is there a better dvd playing alternative? I installed all the codecs mentioned in the starter guide... do they include dolbydigital?

---

### Post by l33tc0d34 on 2005-11-01
like penut butter hahaha :KS :KS :KS :KS :KS :KS :KS

---

### Post by drewbie on 2005-11-01
I suggest you look at turning on DMA

i think the command was

sudo hdparm -d1 /dev/hdc

but do a search on the forums for it, this problem has come up many times before

---

### Post by matva on 2005-11-01
dma is on.

---

### Post by eyebrowman92 on 2005-11-01
you have to speed up the dvd drive by typing into a terminal ```
sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf
``` then at the very bottom of the gedit file type > /dev/cdrom {
       dma = on
} thats how i did it

---

### Post by matva on 2005-11-01
ah, well it seems i was mistaken, dma was off. Turned it on and totem no longer skips. I guess dma doesnt stay enabled after reboot or something, cause i remember turning it on yesterday. BTW, i kinda like mplayers style, but it is really slow for me. When i right-click on the screen while watching the video freezes. Also, it doesn't automatically enlarge the video to fit my screen. Any ideas?

---

### Post by eyebrowman92 on 2005-11-01
what do you mean excaclt when you enlarge the video to fit the screen? the screen of totem? the screen of mplayer?

---

### Post by matva on 2005-11-01
i am talking about mplayer. It doesn't zoom so that the video fits the entire screen.

---

### Post by crypticreign on 2005-11-01
[QUOTE=matva]i am talking about mplayer. It doesn't zoom so that the video fits the entire screen.[/QUOTE]

You have your Video display driver (whatever it's called in gmplayer)misconfigured, try setting it to something else.  There should be a bunch listed, try to play a video with each one.  Some will work, some will not.

---

### Post by dtfinch on 2005-11-01
Does 3D work well? If not, you're probably using the vesa driver, in which case it would run very much slower if you ever got it to zoom, if that was the case.

---

