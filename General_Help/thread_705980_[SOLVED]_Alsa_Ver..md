---
title: "[SOLVED] Alsa Ver."
date: 2008-02-23
forum: General Help
---

### Post by Fred_E _krugar on 2008-02-23
How can I find out exactly what version of ALSA drivers I am running.

---

### Post by FuturePilot on 2008-02-24
```
apt-cache policy alsa-base
```
Should do the trick unless you've compiled them yourself.

---

### Post by Fred_E _krugar on 2008-02-24
Now the question is I just tried to update it to 1.0.16 and it still shows 1.0.14, what do ya think I did wrong? 
I could have swore I did it right :/ :(

---

### Post by FuturePilot on 2008-02-24
How did you try to upgrade it? Compiling it? If you compiled ALSA then apt will not be aware of that.

---

### Post by Fred_E _krugar on 2008-02-24
Yeah I compiled it, I just wanted reassurance that it was installed.

Ok this is what happened. I reinstalled Ubuntu 7.10 But I wanted the new Kernel so I compiled it and am now using 2.6.24.2. At first I had no sound at all after the Kernel upgrade. So I compiled the ALSA ver. 1.0.16 so I could use my new soundcard latter. 

So I guess the ALSA drivers are installed seeing how I now have sound,but I just wanted to be sure.

---

### Post by FuturePilot on 2008-02-24
Yeah, if you didn't have sound before but have sound after, most likely you have installed it correctly. It's just that apt does not keep track of stuff you compile and install.

---

### Post by Fred_E _krugar on 2008-02-24
Rgr. Thanks for the info.

---

