---
title: "Making space on boot"
date: 2008-05-30
forum: General Help
---

### Post by shieldw0lf on 2008-05-30
So, I'm running Ubuntu Hardy.  I upgraded my distribution from Gutsy, and I've got the Ubuntu Studio metapackage installed.  I've got an 86MB dedicated boot partition.

I tried to do an update, and it failed because my boot partition is full.  When I look in there, I find a bunch of what I presume to be different kernels, all 8 mb in size, labelled 

initrd.img-X.X.XX-XX-suffux

I've got 2.6.22-14-generic, 2.6.24-16 generic, 2.6.24-16-rt, 2.6.24-17-generic, 2.6.24-17-rt, and a bunch of .bak files as well.

I'm not sure how to go about safely removing some of these.  I've never gotten the machine to successfully boot with the real time kernels, so my first inclination would be to remove all of those, and any older ones that may be safe.

Can anyone tell me how I go about safely removing these?

---

### Post by EXCiD3 on 2008-05-31
You can remove old kernels with Synaptic if you want. Just search and then remove/purge the ones you dont want.

Once you do that run this to update grub automatically for you:```
sudo update-grub
```

---

