---
title: "Wierd Lockups"
date: 2008-05-07
forum: General Help
---

### Post by W2IBC on 2008-05-07
OK, its totally random and its not a compleate hard lock up but what hapens is

1. firefox freezes alot (FF3b5) just at random and after a few freezes it gets to lockup where i have to force close it. then #2 plays out

2. after said above happens then once FF gives the final lockup. then i cant open anything

system -> quit -> restart is unresponsive and i have to do a hard re-boot.

im wondering if this is a firefox problem or is it a system problem.
and where can i look to find out exactly what is causing this to happen

---

### Post by smartboyathome on 2008-05-07
It sounds like a firefox problem. I have heard of others having this same thing happen to them, and I know it happens to me. Do you have flash installed? If so, are you using flash when this happens?

---

### Post by miwaypet on 2008-05-07
Flash problem. Go to terminal and type:

sudo apt-get remove flashplugin-nonfree; sudo apt-get install flashplugin-nonfree libflashsupport

This helps, but problem may persist. If it dose leave FF3b5 until it is fixed. Don't uninstall it just use another browser. I suggest swift weasle. Get it here: [http://sourceforge.net/project/showfiles.php?group_id=195473]("http://sourceforge.net/project/showfiles.php?group_id=195473") 

Make sure to get the one for your processor! All add-ons will work with it.

FF will be fixed by June.

Hope this helps.

---

