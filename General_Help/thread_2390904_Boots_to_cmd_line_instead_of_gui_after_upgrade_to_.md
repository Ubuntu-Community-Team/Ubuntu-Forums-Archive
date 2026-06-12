---
title: "Boots to cmd line instead of gui after upgrade to 18.04"
date: 2018-05-03
forum: General Help
---

### Post by g7kse2 on 2018-05-03
Its all been going well for a few years. But recent upgrade from 17.10 to 18.04 now boots to cmd line and requires a cmd line login then a 'startx' to get the gui up and running (which it does fine). I've fiddled around with /etc/default/grub on the GRUB_CMDLINE_LINUX="" line without any success. Any other clues or is it a known issue. I couldn't see much when searching.

---

### Post by oldfred on 2018-05-03
What video card/chip?
What brand/model system?
Upgrade does not reinstall proprietary drivers.
 
I found startx did not give me full gui, I think this is now preferred:
       sudo service lightdm start 


 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by g7kse2 on 2018-05-04
Startx seems to give me what looks like a complete system but i will try the > sudo start service lightdm start

[here is the output from Boot-repair, there's plenty of it]("http://paste.ubuntu.com/p/cTcFCy5qZD/")

---

### Post by g7kse2 on 2018-05-04
oops...that reminded me, i fiddled with something about a year ago and totally forgot abou tiv. lightdm was not selected over gdm3. Solved by reinstalling lightdm and changing the setting from gdm3 to lightdm at the prompt

---

