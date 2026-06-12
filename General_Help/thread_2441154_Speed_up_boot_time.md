---
title: "Speed up boot time"
date: 2020-04-19
forum: General Help
---

### Post by garudaone on 2020-04-19
Hello. I came across this thread and I saw that Ubuntu was classified as a "Resource Hog". What steps can additionally be taken to counter that on my end? I am also new to Linux and do suffer from this issue as well.

---

### Post by coffeecat on 2020-04-20
Welcome to the forum.

Post moved to its own thread. Please start your own threads.

---

### Post by Artim on 2020-04-20
Which version you "should" use depends on your hardware.  If you have 16 GB of RAM or something like that, for example, Ubuntu is fine for that.  I use Xubuntu for my modest little 'puter with 8GB of RAM and it's solid and fast.  The more "lightweight" the desktop, the quicker the machine.  But increasingly true also is the choice of *applications* matters as much or more than the desktop environment.  LibreOffice is a "resource hog" compared to Abiword + Gnumeric, for example.  Lubuntu is a nice mix of lightweight apps on a lightweight desktop environment for older, more modest machines.

---

### Post by speartip on 2020-04-20
"Resource Hog" compared to what? I've tried numerous Distro's & Ubuntu is no more a resource hog than any other Gnome based Distro. If you want something a bit lighter try Xubuntu. Even Kubuntu is a lot lighter these days & you can still have all the fancy effects you want. Resource usage is subjective. It all depends on the specs of your device.

---

### Post by garudaone on 2020-04-20
Thank you Artim & Speartip for the insight!I will look into Xbuntu!

---

### Post by VMC on 2020-04-20
Funny thing I realized regarding "resource hog" fixation that I have read for years. Both Ubuntu, budgie-ubuntu both appear to be using a lot of memory, compared to X,L,Kubuntu. Those three are way lighter in terms of memory usage. Running "vmstat -s" and comparing all 5 systems it would seem that both budgie, and ubuntu wouldn't run so well. The reverse is true on my system. For example Firefox pops up immediately on Ubuntu, but I see it "painted" on the other three. GHOSTERY reflects the speed difference!

---

### Post by HermanAB on 2020-04-20
You could use Xubuntu for a much faster desktop experience, or if you are only worried about boot time, the best solution is not to reboot - use suspend.

I think that Linux desktop developers should occasionally boot up OpenBSD or Slackware, to see how much their code affects system performance.  The difference is quite scary.

---

### Post by Artim on 2020-04-21
It also helps boot time if you "un-check" services you're not using.  On my desktop, for example, I'm not using any Bluetooth devices, so there's no need to load that at startup.  That helps speed up boot-up time as well.
Here's my Xubuntu Startup options (pictured).

---

### Post by ActionParsnip on 2020-04-21
If you already have ubuntu installed, you can run:

sudo apt-get update
sudo apt-get install xfce4

log off, then log in to the new XFCE session.

---

### Post by garudaone on 2020-04-21
Thank you all!! Many thanks to Coffeecat, Artim, Speartip, VMC, HermanAB, & Action Parsnip! I will be trying these and also sharing some this newfound knowledge with my classmates! Thank you for all your help! Cheers!

---

