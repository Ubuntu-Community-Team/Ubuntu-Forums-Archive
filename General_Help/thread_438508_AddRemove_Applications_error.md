---
title: "Add/Remove Applications error"
date: 2007-05-09
forum: General Help
---

### Post by Jeff311 on 2007-05-09
Hi.  Sorry I am rather new to Ubuntu (and Linux).  When trying to install *some* things through add/remove programs I am getting an error.  Ill use gparted for instance.
> Cannot install 'gparted'

This application conflicts with other installed software. To install 'gparted' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


So I open up Synaptic Packet Manager find gparted and mark for installation... I get the following error.  (I don't know the protocol on showing images so I'll just post to the source.)
[http://img245.imageshack.us/img245/9226/screenshotsynapticam4.png]("http://img245.imageshack.us/img245/9226/screenshotsynapticam4.png")

Is there a quick fix for this, and similar problems I am getting when trying to do the same for other programs?

---

### Post by Jeff311 on 2007-05-09
I should have said that I am running Feisty 7.04

---

### Post by zvacet on 2007-05-10
Install dependencies.

```
sudo aptitude install file_name
```

---

### Post by Jeff311 on 2007-05-11
Thanks a lot.  
Using "sudo aptitude install gparted" worked but when I tried to do it again for another problem there was an error saying something like "can not find a command sudo aptitude" (or something like that, I can't remember it exactly).

Anyone have any idea about how to get everything working correctly?

---

