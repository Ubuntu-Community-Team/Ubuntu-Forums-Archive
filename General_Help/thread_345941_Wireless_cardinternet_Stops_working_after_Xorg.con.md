---
title: "Wireless card/internet Stops working after Xorg.conf change"
date: 2007-01-25
forum: General Help
---

### Post by nuggetz on 2007-01-25
Just as the subject says, if I install the nvidia driver, I can't get online. Its weird becuase i can still use the iwlist command to see my wireless router. So is this a bug?

---

### Post by riven0 on 2007-01-25
Can you try changing your graphics driver back to the open source one and see if you can get on the net after that? Just open your xorg.conf file and change the Driver section from **"nvidia"** to **"nv"**.

---

### Post by nuggetz on 2007-01-25
Forgot to mention that. The old xorg.conf allows me to get online without a problem. I just move it back and restart gdm and it works. Anyone have ideas? I kinda need both since i'm attempting to get beryl installed.

---

### Post by dannyboy79 on 2007-01-25
well if you have restricted drivers for your wireless I think you need to install them again after you do the nvidia install. if your wireless was working out of hte box than I would find out what chipset your wireless card is and then see if you can try a different module or driver to get it to work.

---

### Post by nuggetz on 2007-01-25
Ok, seriously tho. The Cisco Aironet 350 works out of the box. I have no idea where to find an alternate driver to try and reload once I make the change from NV to NVIDIA in xorg.conf. I still dont understand what the driver has to do with my video card. Why would just switching to a nvidia driver totally hose my Aironet card which functions perfectly? And the best is that it still functions somewhat afterwards. I'm able to scan the wifi network and the meter still shows excellent signal strength.

---

