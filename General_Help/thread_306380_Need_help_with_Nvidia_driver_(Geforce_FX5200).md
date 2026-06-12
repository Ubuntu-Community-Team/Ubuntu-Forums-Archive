---
title: "Need help with Nvidia driver (Geforce FX5200)"
date: 2006-11-24
forum: General Help
---

### Post by gorkur on 2006-11-24
I'm feeling extremely stupid asking for help with this, but I've tried everything I can think of and searched the forums like a maniac :cry:

My problem is this:

I've been trying to install the Nvidia drivers for my Geforce FX5200 (128 MB) card, with no luck. First I tried the howto for Edgy (since I was running Edgy then) which resulted in the Xserver not running so I restore my backed up xorg.conf, then I tried installing from the repos (even tried both the latest AND the legacy drivers). But, as I said, with no luck so far. 

Now I feel I've hit the wall and have absoloutely no clue what to try next :confused:

I'm running Dapper. Specs are
AMD Athlon 2.2Ghz
768 MB RAM
Geforce FX5200 128 RAM
Ubuntu Dapper

Sorry for being an annoying noob btw ;)

---

### Post by taurus on 2006-11-24
Try something like these from a terminal, Applications -> Accessories -> Terminal.

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```
Then, log out and at which point, you should see nVidia logo against white background.  If not, reboot...

---

### Post by rocknrolf77 on 2006-11-24
Don't forget to check out envy at [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by gorkur on 2006-11-24
> **rocknrolf77 said:**
> Don't forget to check out envy at [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Ok, utils like this one just need to be advertized more! :D

Thank you dearly :D

---

### Post by taurus on 2006-11-24
> **gorkur said:**
> Ok, utils like this one just need to be advertized more! :D

Thank you dearly :D
Actually, it is a sticky in Multimedia & Video, [http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)...

---

### Post by fragos on 2006-11-25
Installing nvidia-glx with Synaptic does what you need to use the FX5200 in a single step.

---

