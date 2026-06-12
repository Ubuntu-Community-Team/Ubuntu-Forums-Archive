---
title: "HP L1925 and Xorg.conf help"
date: 2007-07-10
forum: General Help
---

### Post by xterm on 2007-07-10
Hello all

I bought a new monitor (a hp L1925 19"). 

Now, I can only choose 800x600px 60Hz. Can anyone tell me how to configure x11.org monitor settings to match my new monitor. 

Have anyone got this to work at 1280x1024 75Hz?

What settings should I specify?

---

### Post by hashimoto on 2007-07-10
Get the technical details of your monitor (supported resolutions, refresh rates etc) and head this way: [http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)

---

### Post by xterm on 2007-07-10
Yeah

If I only knew "the technical details" of my monitor and how to translate them into xorg.conf values. What I realy want the answer to is my second question: 

> Have anyone got this to work at 1280x1024 75Hz?

and how did they config their "monitor" section in xorg.conf?

---

### Post by xterm on 2007-07-10
I can add that I have tried to reconfigure x11 with 
```
sudo dpkg-reconfigure xserver-xorg
```

but that only caused the screen to go nuts. I ended up with a reboot without X and restore the xorg.conf file from a backup...

---

### Post by xterm on 2007-07-10
does this help?

[http://reviews.cnet.com/lcd-monitors/hp-l1925/4507-3174_7-21244851.html](http://reviews.cnet.com/lcd-monitors/hp-l1925/4507-3174_7-21244851.html)

---

### Post by hashimoto on 2007-07-11
> **xterm said:**
> Yeah

If I only knew "the technical details" of my monitor and how to translate them into xorg.conf values. What I realy want the answer to is my second question: 



and how did they config their "monitor" section in xorg.conf?

How about HP:

[http://h10010.www1.hp.com/wwpc/uk/en/sm/WF10a/20491-156249-156249-156249-172197-735521.html](http://h10010.www1.hp.com/wwpc/uk/en/sm/WF10a/20491-156249-156249-156249-172197-735521.html)

Then do ```
sudo dpkg-reconfigure xserver-xorg
```
and select advanced when asked so you can fill in the correct refresh rates.

---

