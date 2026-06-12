---
title: "Resolution on Radeon 7000 -&gt; LCD-tv"
date: 2006-08-28
forum: General Help
---

### Post by 99nvbjed on 2006-08-28
When I connect my Ubuntu-machine to my LCD-tv I can't get any higher resolutions then 1280x768. The native resolution on the LCD is 1366x768.

I tried to edit the /etc/X11/xorg.conf by adding the 1366x768 resolution but it did'nt work. When I looked at the log-file /var/log/Xorg.0.log I get the folloing messege:

"Warning: Mode 1366x768 is out of range" 
"Warning: Valid Modes must be between 320x200 - 1280x768"

It seems that the Radeon is locked on 1280x768 as the highest resolution. In windows, however, I can set the resolution to 1368x768 (close enough to 1366) using PowerStrip, so the card clearly supports higher resolution.

Is there a way to bypass the preidentified max-resolution? I really don't want to use Windows on my HTPC!! :confused:

---

