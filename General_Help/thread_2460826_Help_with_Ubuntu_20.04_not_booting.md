---
title: "Help with Ubuntu 20.04 not booting"
date: 2021-04-19
forum: General Help
---

### Post by vw16v on 2021-04-19
I recently removed xrdp and ssh and after I rebooted it will not load the GUI.

I get to a screen and it shows:
/dev/sda9: clean 327490/458578323 files 

It just hangs at this screen and will not boot. I tried recovery mode and that's not helping. Any ideas what I can try to recover?

Thanks

---

### Post by vw16v on 2021-04-20
I managed to get this fixed by re-installing xrdp and openssh via command line with networking. This all started when I was trying to get xrdp over ssh working. It appears that caused issues with xsession and it couldn't load a GUI. I'm just glad reinstalling those helped!

---

