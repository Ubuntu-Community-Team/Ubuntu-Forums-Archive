---
title: "[SOLVED] dual-boot question"
date: 2007-10-17
forum: General Help
---

### Post by sbussy89 on 2007-10-17
I just put ubuntu on my laptop, and im dual-booting with vista.  for some reason, two ubuntu's show on my boot selector, but only one of them works.  how can i remove the one that doesnt work???  ps ill admit im a total newb so i need this really dumbed-down

---

### Post by vasiliymeshko on 2007-10-17
Most likely the two different  "ubuntu's" are two different kernels. If you want to remove one that does not work, you can search for it in Synaptic and uninstall from there (It will also clean up the boot menu for you).

---

### Post by louieb on 2007-10-17
The second one is for single user recovery mode. If you mean by not working you don't get a GUI thats right. It does not have a GUI. When you select it you should get something like this: 
```
**root@whitebox:~#** 
```

And all is well.  Sort of like booting to Windows recovery mode.

---

### Post by sbussy89 on 2007-10-17
actually i think it is 2 different kernels... i have two ubuntu's and 2 recovery modes, the first pair says 2.6.20-16 and the second pair says 2.6.20-15

---

### Post by Scroobytec on 2007-10-17
> **vasiliymeshko said:**
> Most likely the two different  "ubuntu's" are two different kernels. If you want to remove one that does not work, you can search for it in Synaptic and uninstall from there (It will also clean up the boot menu for you).

Yes you have two kernels - the 2.6.20-15 one is the previous Feisty kernel which upgraded to 2.6.20.16. How you get rid of it I am not sure, you can try vasiliymeshko's suggestion

> Most likely the two different "ubuntu's" are two different kernels. If you want to remove one that does not work, you can search for it in Synaptic and uninstall from there (It will also clean up the boot menu for you).

It may work.

---

### Post by sbussy89 on 2007-10-17
but the thing is the 15 is the one that works, and the 16 gives me an error saying:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?" Y/N"

Except being the total newb that i am i would have absolutely no idea how to diagnose the problem... i was just gonna get rid of the 16 since the 15 works but if its the upgraded version idk if i should

---

