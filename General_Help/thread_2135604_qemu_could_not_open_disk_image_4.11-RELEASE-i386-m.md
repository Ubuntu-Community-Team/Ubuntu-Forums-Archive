---
title: "qemu: could not open disk image 4.11-RELEASE-i386-miniinst.iso"
date: 2013-04-14
forum: General Help
---

### Post by flatman123 on 2013-04-14
Hello,

first I would like to thank you for taking the time and view my Thread.

I've been at this for over 6 hours.I have Ubuntu installed Via VirtualBox on a Window 7 system.....

within Ubuntu i'm trying to install JunOS.. Everything was ok up until I tried booting Qemu using the iso image of FreeBSD...I get the following error message:



root@jeffm-VirtualBox:/# qemu -boot d -hda olive.img -cdrom ~/4.11-RELEASE-i386-miniinst.iso
qemu: could not open disk image olive.img
root@jeffm-VirtualBox:/# 


I also tried this syntax:

root@jeffm-VirtualBox:/# qemu -m 256 -hda olive.img -cdrom 4.11-RELEASE-i386-miniinst.iso -boot d -localtimeqemu: could not open disk image olive.img
root@jeffm-VirtualBox:/# 


I have the iso file located here:

root@jeffm-VirtualBox:/media# ls
***4.11-RELEASE-i386-miniinst.iso***  VBOXADDITIONS_4.1.6_74713


I'm not sure what to do next..Please help..I really wanna get my JunOS studies started.

Much appreciated.

---

