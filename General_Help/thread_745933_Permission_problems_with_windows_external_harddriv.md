---
title: "Permission problems with windows external harddrive"
date: 2008-04-05
forum: General Help
---

### Post by Blacklife08 on 2008-04-05
i have a WD Passport that was last used on a windows machine
I am currently unable to write from it, and when i try to change the permissions it reverts them back
sorry, noob question, but can anyone help?
thanks!

---

### Post by bren on 2008-04-05
yeh, check the drive format 

it is probably NTFS

Ubuntu can read NTFS but to write you must (extremely easily) install a driver

search for ntfs-3g elsewhere on this forum....  it could be the following or similar

sudo apt-get install ntfs-3g ntfs-config

then run ntfs-config once (appears in Applications -> System i think)

Then your probs are over.

I think this driver will be included by default in Hardy Heron (the next Ubuntu version) so this fix should only be needed for the short term

bren

---

