---
title: "[SOLVED] Screen Resolution"
date: 2008-06-05
forum: General Help
---

### Post by underdog512 on 2008-06-05
I have just install the 64-bit version of hardy.  It runs quite nicely but the highest sceen resolution i have available is 1024x768.  

I have an nvidia GeForce 6200 graphics card with the restricted drivers installed.  I have an emachines CRT monitor (don't remember the model no.)

I tried running sudo dpkg-reconfigure xserver-xorg but it only gives me the keyboard options.  I never get the option to set up video.  I even tried editing the xorg.conf file as noted in community documentation to no avail.

Is there any other way to increase the screen resolutions available?

---

### Post by Zorael on 2008-06-05
Can you set it higher in the **nvidia-settings** app? (package of the same name)

If it doesn't even start, you'll need to review that xorg.conf and confirm that it's properly loading the nvidia driver.

---

### Post by underdog512 on 2008-06-05
> **Zorael said:**
> Can you set it higher in the **nvidia-settings** app? (package of the same name)

If it doesn't even start, you'll need to review that xorg.conf and confirm that it's properly loading the nvidia driver.

That did the trick! Thanks!

---

