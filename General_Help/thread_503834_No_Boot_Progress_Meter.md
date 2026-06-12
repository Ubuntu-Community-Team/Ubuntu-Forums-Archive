---
title: "No Boot Progress Meter"
date: 2007-07-18
forum: General Help
---

### Post by mojohn on 2007-07-18
Hello. I just did a fresh install of Feisty on my Dell Inspiron 1100 laptop. I previously ran Dapper.

When I installed Feisty on my desktop machine, I get the nice progress meter letting me know how the boot is progressing. However, on my laptop, I get nothing but a black screen until I'm presented with the logon screen for username and password. 

Based on another thread, I tried sudo dpkg-reconfigure usplash-theme-ubuntu, but that didn't work. Any guidance on how I activate the progress meter?

Thanks, Mojohn

---

### Post by Antimatter47 on 2007-07-25
I just fixed this on an inspiron 1100 by changing the GDM memory in the BIOS from 1MB to 8MB.

---

### Post by Crafty Kisses on 2007-07-25
> **mojohn said:**
> Hello. I just did a fresh install of Feisty on my Dell Inspiron 1100 laptop. I previously ran Dapper.

When I installed Feisty on my desktop machine, I get the nice progress meter letting me know how the boot is progressing. However, on my laptop, I get nothing but a black screen until I'm presented with the logon screen for username and password. 

Based on another thread, I tried sudo dpkg-reconfigure usplash-theme-ubuntu, but that didn't work. Any guidance on how I activate the progress meter?

Thanks, Mojohn

You can try booting in verbose mode to see what's actually happening, hope this helps.

---

