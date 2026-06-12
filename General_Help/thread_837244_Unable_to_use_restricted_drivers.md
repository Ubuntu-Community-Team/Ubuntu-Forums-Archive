---
title: "Unable to use restricted drivers"
date: 2008-06-22
forum: General Help
---

### Post by timo.jazo on 2008-06-22
I installed Ubuntu with all updates. It works fine, but when I want to turn Desktop effects on, it turns my resolution on 860 X 640 (i think so). I fixed that, but now, when I try to turn RESTRICTED DRIVERS on, it doesnt. So I cant turn desktop effects on. Now Im using VGA driver. Can anyone help??

---

### Post by psyopper on 2008-06-22
What video card are you using?

---

### Post by timo.jazo on 2008-06-23
NVIDIA Geforce 7 (i think)

---

### Post by psyopper on 2008-06-24
What version of the Kernel are you running? This is easy to find out - open a terminal and type
```

uname -r

```

Write this down, or keep the terminal open so you can see the output. Next, open:

System > Administration > Synaptic Package Manager

Scroll down the list until you find "linux-restricted-modules". You are looking for the one that has the same name as the kernel you are running. For instance, on my computer...

```
~$ uname -r
2.6.24-19-386

```

So I would "Mark for Installation" the item in Synaptic named:

linux-restricted-modules-2.6.24-19-386

Once this is finished you should be able to open the Restricted Drivers Manager to enable your video card. If this still doesn't work then you can manually download the drivers for your card. In Synaptic (same as above) you want:

nvidia-glx-new

Once that downloads and installs try the restricted drivers manager again to enable your card.

Let us know how it works out!

---

### Post by timo.jazo on 2008-06-24
Thanks, that worked. I updated the kernel to 2.6.24.19 and then I enabled the drivers. Realy thanks.

---

