---
title: "Ubuntu 8.04 + Compiz Fusion + Firefox = Crash?"
date: 2008-06-05
forum: General Help
---

### Post by tab1293 on 2008-06-05
Hey guys, I am running Ubuntu 8.04 and have a NVidia 8600GT 512MB. I am using the Ubuntu proprietary driver. I installed compiz fusion but I have some problems. Whenever I am in firefox (either ff3 or ff2, I have tried both), Ubuntu will crash after about 3 to 5 minutes of browsing. This crash will happen when I click any kind of link. When Ubuntu crashes, nothing will respond including the mouse and the keyboard. The only way to get out of it is to do a hard power off. 

This crash only seems to occur when advanced desktop effects is enabled. I don't have any plugins installed in firefox including flash. 

Does anyone know how I can fix this problem?

---

### Post by jpeddicord on 2008-06-05
This isn't necessarily a fix, but when your desktop freezes, try pressing Ctrl+Alt+Backspace to reset the X display and take you back to the login screen. Most likely it's a bad Nvidia driver, but I'm not the graphics driver expert.

---

### Post by tab1293 on 2008-06-05
I tried that and that didn't work. Nothing responds.

Also I just found out its not compiz (or at least I don't think), my system just crasehd in firefox without compiz running.

EDIT: Maybe somebody should move this thread since its not compiz anymore.

---

### Post by cmileto on 2008-06-06
Is this an overheating problem? Perhaps clean out all the heatsinks inside the machine.
Otherwise, what are you seeing in the logs?

---

### Post by nickdbliss on 2008-06-06
Maybe its ur driver. These closed driver are not always fully compatible. I installed ATI driver and it was making a mess on my laptop. Using open source driver since then and having DRI and desktop effects enabled. Everything is working great. Cheers.

---

### Post by jtrindle on 2008-06-06
Check your free memory with top -n 1

My system acted like this until I re-enabled swap after upgrading from 7.10 to 8.04.

---

### Post by tab1293 on 2008-06-06
Ok, thanks for the replies. 

1) My computer is not overheating, I am almost 100% sure of that.
2) How would you use the top command if my system is frozen?
3) I will try the open source drivers but I hear they can't really compare to the Nvidia drivers.

Are you sure it might not be a problem with firefox? Because it only seems to freeze if FF. 

Thanks.

---

