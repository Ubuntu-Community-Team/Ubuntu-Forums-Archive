---
title: "[SOLVED] Where can I find the installation instructions for Nvidia drivers for 13.04?"
date: 2013-04-25
forum: General Help
---

### Post by icfantv on 2013-04-25
I just finished setting up 13.04 and for the most part it's stable.  I am noticing some video issues (random/occasional black screen, window contents being replace by a giant, pixellated clock, etc..) and noticed that I don't have the Nvidia drivers installed.  Can somone please point me to installation/setup instructions for these drivers?

---

### Post by pqwoerituytrueiwoq on 2013-04-25
There is a bug with the nvidia driver on the stock kernel, i suggest using the mainline kernel 3.8.8 or 3.9rc8
to install the driver run
```
sudo apt-get install nvidia-313-updates nvidia-settings-313-updates
```

Mainline kernel installer:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
older version attached here
[http://ubuntuforums.org/showthread.php?t=2137026](http://ubuntuforums.org/showthread.php?t=2137026)

---

### Post by martin851 on 2013-04-25
Do you think your solution worked for me ? I cannot start 13.04. after i installed NVidia drivers, i purged NVidia in recovery mode but that did not helped (broken Unity/Compiz).
Here is detailed description : [http://askubuntu.com/questions/285571/ubuntu-13-04-fail-to-start-after-installing-nvidia-drivers-vostro-laptop](http://askubuntu.com/questions/285571/ubuntu-13-04-fail-to-start-after-installing-nvidia-drivers-vostro-laptop)

What i should check in the startup logs (syslo/boot etc...) to provide more informations ?

---

### Post by pqwoerituytrueiwoq on 2013-04-25
i told you to install the mainline kernel for a reason, that it why

---

### Post by icfantv on 2013-04-26
i'm assuming i can safely ignore this warning?

```

Warning:
  linux-image-extra-3.8.9-030809-generic_3.8.9-030809.201304260102_amd64.deb is missing
  It was probally merged with linux-image-3.8.9-030809-generic_3.8.9-030809.201304260102_amd64.deb
  If you get broken packages run this command to fix it: (Save it somewhere, just to be safe)

```

I did save off that command (just to be safe).

---

### Post by icfantv on 2013-04-26
Looks like everything appears to be working correctly and I see the nvidia kernal module loaded (it's 9MB, that seems huge but I guess it's ok).

Is there anything I can do to "test" it (other than using my system normally) to make sure stuff is behaving appropriately?

Thanks for your help.

---

