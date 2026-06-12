---
title: "Firefox 3.0 RC1 and youtube"
date: 2008-05-21
forum: General Help
---

### Post by clef360 on 2008-05-21
I've just upgraded firefox 3.0 rc1 from b5 and when I try to open a youtube video, the browser automatically quits. I had it working before upgrading, and all other flash including movies such as metacafe works fine. Has anyone else had this problem?

---

### Post by strabes on 2008-05-21
Please search the internet and these forums before posting a question. Firefox's instability with flash in hardy is due to its pulseaudio integration. Remove the package "libflashsupport", restart firefox, and you should be good to go.```
sudo aptitude remove libflashsupport
```

---

### Post by clef360 on 2008-05-22
> **strabes said:**
> Please search the internet and these forums before posting a question. Firefox's instability with flash in hardy is due to its pulseaudio integration. Remove the package "libflashsupport", restart firefox, and you should be good to go.```
sudo aptitude remove libflashsupport
```

I posted a new topic because I hadn't found anything about instability after switching to rc1 from beta. I tried your suggestion, and now I have no sound in flash. I tried reinstalling that package, and still no sound. I guess ubuntu really isn't ready for the mainstream, huh. It's just so frustrating. It took me hours just to get my rear speakers working. Subwoofer still not working. It's so disheartening to see the video and not hear any sounds again.

---

### Post by clef360 on 2008-05-22
Someone please help me. I am going crazy trying to find a fix for this. I'm not using alsa.

---

### Post by clef360 on 2008-05-22
It used to only crash occasionally. Now it never crashes but there is also never any sound. I wish I wish I wish it would just crash again. I promise that I will paypal $10 to whoever can solve my sound problems! Seriously! Not a scam!!! Just desperate! I am BEGGING.

---

### Post by desertboy on 2008-05-22
Maybe not ideal solution can't you just remove firefox 3 and install firefox 2. Then hold off upgrading to 3.0 until it goes final and these issues are resolved.

I had firefox crashing horribly whenever I tried to access Youtube but removing that package solved my problems and I still have sound.

The one thing I've done that most people probably haven't is change my sound preferences.

---

### Post by tvst on 2008-05-22
Try this
1) make sure everything is installed: sudo apt-get install pulseaudio libflashsupport
2) go to "system > preferences > sounds" and make everything "pulseaudio"
3) close firefox and any other sound-using program
4) go to the terminal and enter: sudo pkill -9 pulseaudio
5) then start pulseaudio again by entering: pulseaudio -D
6) start firefox, go to a flash website and see what happens. If things work, you don't have to do any of this again when you reboot. If there's still no sound, please post the result of the following command: cat /proc/asound/cards

---

