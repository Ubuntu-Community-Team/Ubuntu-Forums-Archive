---
title: "CD Burning not working"
date: 2007-02-06
forum: General Help
---

### Post by Jasper84 on 2007-02-06
I am trying to burn the Efty cd (*.iso), but it wont work. I tried Nautilus, that says: "Error writing to disc"(how usefull). It could open the cd tray, though. Also tried 'Burn' with:
$ burn -I -n ubuntu-*.iso
But it asks: "Error. Please insert a blank CD/DVD." which i already have. (i checked, the computer can at least read from there. Also checked if the command could be changed)
Then i also tried "cdw" but that one just segmentation faults all the time..

By this time i am have nearly upgraded my current system to Efty :-| but i **do** want to be able to burn stuff..

BTW the "official" upgrade method does not work..
gksu "update-manager -c" and clicking upgrade twice gives me GtkView error  [Edit: installing ubuntu-desktop fixed it!].. I dont get it how they missed this, since this isnt a special system at all, just a clean Breezy 6.10 Install upgraded to Dapper 6.03 by following instructions here: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) (i changed sources.list) I am wondering whether they check "oft-used" upgrading paths..

---

### Post by cmost on 2007-02-06
Have you tried other CD burning apps, such as k3b or Gnomebaker?  Also, I can say from experience that upgrading in Ubuntu sucks a big fat one!  I don't care what others will tell you here, upgrade at your own peril!  I think the only way you'll have a trouble-free upgrade is if you left your sources.list file alone and abstained from adding any additional software beyond what might have been included in the vanilla repos.  Otherwise, you're SOL.  A fresh install will give you the least trouble, unfortunately.

---

### Post by Gibbs on 2007-02-06
I use both. Problem is K3B likes to lock up but can erase my CDs whereas Gnomebaker can't erase CDs but doesn't lock up. It's a real pain :p

---

### Post by Jasper84 on 2007-02-07
thanks

---

