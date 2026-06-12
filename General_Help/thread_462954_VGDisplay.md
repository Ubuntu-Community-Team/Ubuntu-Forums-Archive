---
title: "VGDisplay"
date: 2007-06-03
forum: General Help
---

### Post by pstather on 2007-06-03
Hi guys,

Not sure if this has already been asked, but I will ask anyway.

I am trying to load Logical Volume Management through Webmin but it is saying that I need vgdisplay but I can't seem to find it.

Does anyone know where I can get it.

I searched for it through synaptic but it isn't there, i also tried apt-get install vgdisplay but it isn't there either.

I would appreciate any help.  Thanks

---

### Post by fanatik on 2007-06-04
$ sudo aptitude install lvm2

vgdisplay is part of the lvm package.

---

### Post by pstather on 2007-06-05
I installed this and it is still now saying

"No program 'vgdisplay' found for your current version of LVM"

---

### Post by BillyBuerger on 2007-08-04
Just installed webmin on my recent build and got the same error.  After some searching, I found that supposedly, the links to the lvm commands are incorrect.  Running these commands to update the links seems to have worked for me...

sudo cd /sbin
sudo ln -s /lib/lvm-200/ /lib/lvm-0

---

