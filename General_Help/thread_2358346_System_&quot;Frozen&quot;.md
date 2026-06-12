---
title: "System &quot;Frozen&quot;"
date: 2017-04-12
forum: General Help
---

### Post by Crimple on 2017-04-12
Hi.
I have Xubuntu 16.04.2 (original ISO 16.04) and a week ago installed, on a dedicated partition of the same disk, the Ubuntu Mate 16.04.2 ISO.
Yesterday I booted with Xubuntu and updated it, it updated Grub as well. today I booted with Mate and everything was sort of frozen: mouse clicks would take a long time to produce results, windows took 20 or more seconds to open, unusable. Several reboots and an update didn't help.

Any ideas ?

---

### Post by Bucky Ball on 2017-04-12
My idea would be to reboot, choose the Mate 'Advanced options' (I think) under the first Mate kernel, then choose the second kernel to boot and see if that works better. If so, update that.

As you installed Ubuntu Mate second, that would now have 'control' of the grub. Therefore, any updates in kernel in Xubuntu won't be reflected in your grub list at boot until you update grub in Mate. 

I would do this. Get into Mate, open a terminal and:

```
sudo apt update
sudo apt full-upgrade
sudo update-grub
```

Reboot and see how it goes. You should be on kernel 4.4.0-72 at this point (I am running a fully up dated Xubuntu-core). 

Not sure that the Xubuntu update/upgrade had anything to do with your problems in Mate and not sure doing the above will make any difference, but it will get everything up to date and we can take it from there.

---

### Post by Crimple on 2017-04-12
Nope, couldn't even update Grub, system is somehow corrupted.
I'll just install afresh, no biggie, it wasn't my main OS.

Many thanks for your help.

---

### Post by Bucky Ball on 2017-04-13
If this is resolved to your satisfaction, best to mark as 'Solved' so others don't waste time trying to help, and start a new thread for further issues. (Thread Tools at top right of page or last link in my signature at bottom of post.)

Enjoy and good luck. :)

---

