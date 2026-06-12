---
title: "Need Help With Nvidia Install After Compiling New Kernel"
date: 2008-05-05
forum: General Help
---

### Post by Brando569 on 2008-05-05
Hi, I compiled 2.6.25 from source last night and all went well, I'm using it right now, but it wont let me install the newest nvidia driver from source. I've tried using the nvidia installer and doing it manually and they both give me this error (theres more if anyone wants to see it):

```
/usr/src/modules/nvidia-new-kernel/nv/nv-vm.c:363: error: implicit declaration of function ‘global_flush_tlb’
make[3]: *** [/usr/src/modules/nvidia-new-kernel/nv/nv-vm.o] Error 1
make[2]: *** [_module_/usr/src/modules/nvidia-new-kernel/nv] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2

```

---

### Post by Brando569 on 2008-05-28
i still need help with this, someone? anyone??

---

### Post by sdennie on 2008-05-28
Which version of the nvidia drivers are you using?  The newest stable driver, 173.14.15 (released today) compiles fine against 2.6.25.4.

---

### Post by Brando569 on 2008-05-29
it installed fine, but it completely screwed X up, at first it would be fine but when Kwin was switched to Compiz-Fusion (automatically) it would just give me a grey desktop nothing else would appear only the cursor. I rebooted and then X wouldnt work at all it gave me the "no screens found (actually screens were found but the configs werent usable)" error. I tried restoring Xorg.conf from a backup and that didnt fix anything. It seems to be a problem with 2.6.25, the nvidia driver, and compiz-fusion. the nv driver works fine with 2.6.25 though. 

Also I dont have any sound in 2.6.25 kde says it cant find my mixer, i dont know if you can help me with that or not.

---

### Post by sdennie on 2008-05-29
Your custom kernel won't have the nvidia kernel module so, you'll need to download that from nvidia (a new version of the nvidia driver was released yesterday and works with 2.6.25).

If you don't have any sound, it's possible that you didn't build the kernel module for your sound card.  It's also possible that 2.6.25 uses a different mixer channel on your card in 2.6.25 (it does for me).  I'm not sure how you'd change that in KDE though.

Edit:
Didn't read closely enough.  When you install the driver, I recommend answering "yes" to the final question and letting the installer setup your card.

---

