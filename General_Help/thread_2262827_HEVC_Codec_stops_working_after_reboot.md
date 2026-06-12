---
title: "HEVC Codec stops working after reboot"
date: 2015-01-27
forum: General Help
---

### Post by Evil Wayz on 2015-01-27
I wanted to watch some tv shows encoded with the newish h.265 codec, so I followed the instructions I found at another website, and it worked fine.  Then I rebooted my computer because the gnome flashback shell crashed and now I only have audio.  This is what I added:

```
sudo apt-add-repository ppa:strukturag/libde265
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gstreamer0.10-libde265
sudo apt-get install vlc-plugin-libde265


```

Would really like to fix this, as I've got ten seasons @ 24 episodes a season to watch.  This error (audio only) appears in Totem and VlC player.

I think the problem is going from the 1 series to 2, but I don't know how to downgrade, already tried purging the repository, and nothing.

---

### Post by mc4man on 2015-01-27
Not sure what you have the 0.10 gstreamer plugin for, totem would have used the 1.0 one.
As far as vlc maybe run it from a terminal & see if it produces any useful info. If not try with some verbosity (vlc -vv

Otherwise vlc that uses libav11 or FFmpeg  can decode most hevc files without the need for a plugin. There are various means for you to achieve that.
Also any recent mpv or mplayer/smplayer packages would work fine.

---

### Post by Evil Wayz on 2015-01-28
Ok, switch VLC's video output to automatic seems to have solved that problem, and adding the gstreamer1.0-libde265 seems to have fixed Totem.  SYnaptic doesn't show anything called libav11 though.

---

### Post by mc4man on 2015-01-28
> **Evil Wayz said:**
> Ok, switch VLC's video output to automatic seems to have solved that problem, and adding the gstreamer1.0-libde265 seems to have fixed Totem.  SYnaptic doesn't show anything called libav11 though.
libav11 isn't in the trusty repo's, you'd need to go to 14.10/15.04 or for trusty a ppa

---

### Post by seeamkhan on 2015-10-12
Thanks for the great solution!! :p
I have tried a lots of solutions but did not work, finally found this one and worked fine.
I am using Ubuntu Gnome 14.04, Gnome shell version 3.10.4.

---

