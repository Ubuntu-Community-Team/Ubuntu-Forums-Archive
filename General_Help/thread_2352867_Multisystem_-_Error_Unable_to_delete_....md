---
title: "Multisystem - Error: Unable to delete: ..."
date: 2017-02-16
forum: General Help
---

### Post by theonlytalkinggoat on 2017-02-16
I have been using the program Multisystem for a while and it has never given me any issues, until my thumb drive started going out, today. In the middle of making a Windows 10 entry, it decided to poop the bed and crash the program. Whenever I re-launched the program, it was giving me the error, unable to delete: autorun.ini ... etc. To solve this problem, in my home directory, I ran ```
grep -r multisystem .
``` and found /tmp/multisystem/ After inspecting that folder, I found an exact copy of the ISO and figured it had probably mounted the image, there. I ran ```
mount | grep tmp
``` and sure enough ```
Win10_1511_1_English_x64.iso on /tmp/multisystem/multisystem-mountpoint-iso type udf (ro,uid=1000)
``` After running a umount on the iso, ```
 umount /home/(username)/Downloads/Win10_1511_1_English_x64.iso
``` everything worked fine. 

Hope this helps someone.

---

