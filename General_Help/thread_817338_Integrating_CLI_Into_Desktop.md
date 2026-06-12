---
title: "Integrating CLI Into Desktop"
date: 2008-06-03
forum: General Help
---

### Post by azurepancake on 2008-06-03
Just recently I've seen many screen shots of Linux desktops with the CLI looking almost "integrated" into the desktop. It is completely transparent and lacks the "minimize, maximize, close window" bar.

I'm curious of how to do this. Is there a configuration file for gnome-terminal that I can edit to achieve this effect? I'd appreciate any advice!

Thanks!

---

### Post by john6six on 2008-06-03
Here's a link to the process I used.

[http://ubuntuforums.org/showthread.php?t=535098&highlight=gnome-terminal+--window-with-profile%3Dtrans](http://ubuntuforums.org/showthread.php?t=535098&highlight=gnome-terminal+--window-with-profile%3Dtrans)

---

### Post by azurepancake on 2008-06-03
Thanks a lot, this is exactly what I was looking for! Now I just need to get Compiz working correctly. When in use it totally bogs down my system.

---

### Post by Forlong on 2008-06-04
Do you have Xgl installed (you can use [http://ubuntuforums.org/showthread.php?t=799070]this]("http://ubuntuforums.org/showthread.php?t=799070") to check).

---

### Post by azurepancake on 2008-06-04
> **Forlong said:**
> Do you have Xgl installed (you can use [http://ubuntuforums.org/showthread.php?t=799070]this]("http://ubuntuforums.org/showthread.php?t=799070") to check).

Welp, when I first tried to use Compiz-Fusion I simply typed "compiz" into the CLI and got the following output:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

So after this I actually did use Compiz-Check and it gave me straight "OKs". I noticed in the output it stated "Checking for Xgl: not present" so I decided to install Xgl.

After that was done, I rebooted and logged into a very sluggish desktop! So I removed Xgl. 

The only thing I think of is that my video card isn't being used to it's maximum potential. The card is a Radeon x1600 and I am using the restricted drivers.

---

