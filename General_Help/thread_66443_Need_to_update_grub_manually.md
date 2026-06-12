---
title: "Need to update grub manually"
date: 2005-09-17
forum: General Help
---

### Post by lexter on 2005-09-17
Hi,

I recently changed a setting in my menu.lst and (stupid me) didn't make a backup of that file before, then ran update-grub. Now Ubuntu doesn't boot anymore (kernel panic). I changed the menu.lst back using a LiveCD and rebooted. This doesn't work since I can't run update-grub anymore, I start it on the mounted harddisk but it tries to modify the settings of the LiveCD and not the ones on my harddisk. How can I manually change the grub settings to the values I set in the menu.lst?
I can't find anything on Google with regard to this problem, please help!

Thanks,
lexter

EDIT: Ok, I figured it out myself. Obviously, everything that update-grub does is to change some settings in the menu.lst below the settings I changed manually. I changed those settings manually, too, and now everything works fine again.

---

