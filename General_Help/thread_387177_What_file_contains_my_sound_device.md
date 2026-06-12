---
title: "What file contains my sound device?"
date: 2007-03-18
forum: General Help
---

### Post by escape on 2007-03-18
Where is the file for my sound device?

I'm trying to get vwmare to recognize my sound card so that it can be used on my windows xp guest OS. However, autodetect doesn't work, and I'm not sure where I'd otherwise look for it. Nothing in /dev/snd seems to do the trick. Where can I find the device, so I may point vmware to it? I'm using integrated sound (AC'97/ICH6) on the motherboard of my thinkpad T43. 

Thanks!

---

### Post by zvacet on 2007-03-18
etc/X11/xorg.conf

---

### Post by total wormage on 2007-04-11
ehm, i don't know if you got this problem already fixed, but i bumped into this thread while trying this myself

i got sound in vmware to work with vmware tools installed (in vmware goto the VM menu, and click on install vmware tools..)
without running any guest OS-es I went to VM -> Settings and added a soundcard (using autodetect)
i had to turn of all my programs that made sound before running vmware (like amarok / gxine etc) before getting any results

hope that did the job
good luck ;]

---

