---
title: "How Do I Resize Home Without Losing Home?"
date: 2007-09-02
forum: General Help
---

### Post by SuperMike on 2007-09-02
I'm one of these people who believes that all Linuxes should stick /home on a separate partition than / in order to facilitate easier upgrades.

I have a question, though. Do you know if I can resize my /home partition, giving it unused space from /, without losing / or /home?

Second question. If you know how, and if it works, then is there a speed impact physically on the drive by my action? I mean, if I resize, does that mean that EXT3 technically creates a link on the drive that causes it to keep jumping over to / to find where /home has been extended? I want to extend home, yes, but not at the detriment of performance.

Oh, and if you need to know the version I'm running, it's Feisty Fawn. I configured it with the default of EXT3 instead of ReiserFS, in case anyone wants to know that too.

Thanks in advance.

---

### Post by vanadium on 2007-09-02
With gparted, partitions can be resized: you can shrink / and enlarge /home without loosing data. You should always have a backup of your data, though.

---

### Post by Happy_Man on 2007-09-02
I think if you want to resize a partition, it doesn't have to wipe it. 

To actually go about doing that, boot up a Feisty liveCD, and go to System --> Administration --> GNOME Partition Editor. Apply your changes there, and reboot into your main system. 

I don't think there will be a performance reduction, but if there is, it really should be minor.

---

### Post by merlinus on 2007-09-02
Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Otherwise you will run into mounted partition problems, and you will never be able to resize / since that is where you are working.

-merlin

---

