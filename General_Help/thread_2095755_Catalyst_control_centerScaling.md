---
title: "Catalyst control center/Scaling?"
date: 2012-12-17
forum: General Help
---

### Post by m3t4lm4n222 on 2012-12-17
Hi I am using Ubuntu with my 50" HDTV and even though my resolution is set to the correct 1920 x 1080 the image is not scaled correctly. Nearly the whole taskbar/launcher and time/sound/info bars are not visible.

How would I go about installing Catalyst control center so I can scale the image correctly. I am using a HD 5450 for my video card. Any PPA's for installing catalyst?

---

### Post by m3t4lm4n222 on 2012-12-17
also having issues w/ HDMI audio

---

### Post by m3t4lm4n222 on 2012-12-17
No one knows how to install Catalyst control center on ubunu?? I'm realluy dstucvk ehres

---

### Post by lakerssuperman on 2012-12-17
The control center should be installed with the Catalyst driver.  You should install Synaptic Package Manager.  Open a terminal and type "sudo apt-get install synaptic".  Then run Synaptic.  Go to the Settings menu and then click on Repositories.  When the dialog pops up, click on the additional drivers tab.  This should list all available proprietary drivers that can be used with your system.  Select one of the Catalyst options.  There should be regular Catalyst and the Catalyst (fglrx-updates) options.  The updates is usually newer so I would go for that one.  Once you reboot you should be able to access the Control Center from the Dash and find the scaling options under the display options.

This is valid for 12.10.  If you are running 12.04 or earlier, then the extra drivers section is a separate program which can be run by typing "drivers" into the Dash.

I should mention that some tv's don't accurately report themselves as such and in that case the Control Center doesn't give you the scaling options.  Most of the time, however, if it's a decent brand it isn't an issue.

---

### Post by QIII on 2012-12-17
Easier still than the bother of installing Synaptic:

```
sudo apt-get install fglrx fglrx-amdcccle
```

```
sudo aticonfig --initial
```

```
sudo reboot
```

---

### Post by lakerssuperman on 2012-12-17
100% easier.  I just thought it might be easier to have Synaptic there to change the driver or uninstall it if necessary with a gui.  Some people get squirmy about the command line.  Either way,  hope he can get his picture scaled correctly.

---

### Post by m3t4lm4n222 on 2012-12-18
It's stuck @ 80% for some reason.

80% [5 fglrx 67.7 MB/79.4 MB 84%]

---

### Post by m3t4lm4n222 on 2012-12-18
OK so I got CCC and now I can't figure out how to scale it. Theres no DTV tab because it detects my TV as a projector!@@ FFS

---

### Post by m3t4lm4n222 on 2012-12-18
Any ideas on how to properly scale the image.

---

### Post by lakerssuperman on 2012-12-18
[https://bbs.archlinux.org/viewtopic.php?id=146103](https://bbs.archlinux.org/viewtopic.php?id=146103)

Seems people had success with this.

---

