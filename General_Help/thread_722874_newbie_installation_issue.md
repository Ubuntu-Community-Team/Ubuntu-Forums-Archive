---
title: "newbie installation issue"
date: 2008-03-12
forum: General Help
---

### Post by paulzaplitny on 2008-03-12
not sure where to post this i guess this is the best place. ok i had xp installed on my computer then set up gutsy everything worked good then i had an issue with xp and reinstalled it. after reinstalling it it would boot right into windows. of course being a newbie i thought i had some how deleted my linux install so i reinstalled it. now i have 2 of the same copies of gutsy how can i uninstall the newest install and then still have it boot into where i have the option of selecting ubuntu or windows. any help would be appreciated total newbie with linux.

---

### Post by scragar on 2008-03-12
install gparted```
sudo apt-get install gparted
```then use that(system > administration > partition editor) to remove your extra install.

as for making windows boot first:
```
gksudo gedit /boot/grub/menu.lst
``` will let you edit the config file, you want to increase the default number```
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry

```, so if windows is 4th on the list change it to a 3 etc(list starts at 0, not 1).

---

