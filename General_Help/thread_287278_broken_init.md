---
title: "broken init"
date: 2006-10-28
forum: General Help
---

### Post by mnp5 on 2006-10-28
Hello --

I posted a longer version of this earlier but I'm not getting any replies.  Here's the brief version, then:

1) After upgrading to Edgy, I can only boot up using the default, packaged kernel (2.5.17-10-386).  This seems to be because the init process doesn't start when my legacy (read: custom) kernels are called from grub.

2) I've updated the initrd.imgs for all of the kernels in question, but initrd is irrelevant for my custom kernels since they're monolithic and don't use any modules.

3) I installed the 2.6.17.13 sources from the edgy package that provides them and then copied over my old kernel .config from one of my custom kernels (it was 2.6.17.9, just for the record).  On compile, the same init problem persists.

4) And, of course, I've updated grub manually (grub-install hd0 and the like) after editing the config files.  There is _no_ difference between how different kernels are called in /boot/grub/menu.lst.

W-T-F.  Anyone got any insight on this?

Best,
mnp5

---

### Post by mnp5 on 2006-10-28
Ensure that "Inotify file change notification support" is enabled in your kernel.

Thanks for nothing, forums! :) :)

---

### Post by Blutack on 2006-10-28
Give us a chance!  Anyway it's your own fault for grubbing around too much...thats what gentoos for :-)

---

