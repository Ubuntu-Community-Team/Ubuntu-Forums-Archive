---
title: "Nvidia drivers monitor refresh rate"
date: 2007-03-08
forum: General Help
---

### Post by stchman on 2007-03-08
Hello all, I have Edgy running on a PC with a CRT.  The problem is that I updated the drivers of the nvidia video card and now my refresh rate is stuck on 85Hz.  My monitor has issues with a refresh that high.  I usually keep the refresh at 72Hz.  Is there a way to fix this?  I am going to assume I need to edit the xorg.conf file.

The video card is a GeForce 5700 Ultra AGP.

Here were the commands I used to install nvidia drivers (gotten from the edgy wiki)

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

I believe that the commands installed the 87.76 nvidia driver.


Thanks

---

### Post by christhemonkey on 2007-03-08
Try running: 
```
gksudo nvidia-settings 
```

Although, i cant remember if the 8xxx series of nvidia drivers have refresh rate changing support from their GUI...

---

### Post by stchman on 2007-03-09
> **christhemonkey said:**
> Try running: 
```
gksudo nvidia-settings 
```

Although, i cant remember if the 8xxx series of nvidia drivers have refresh rate changing support from their GUI...

I can find no way to adjust monitor refresh at all.

---

