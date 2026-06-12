---
title: "Group ownership keeps reverting to libvirtd"
date: 2016-04-29
forum: General Help
---

### Post by CelticWhisper on 2016-04-29
I'm having difficulty setting the group association of a number of files (including my ~/) away from celticwhisper:libvirtd after a botched attempt to set up KVM/virt-manager.  It seems that every time I try to set group ownership to anything other than libvirtd, it instantly reverts back.  This includes running chmod with root permissions via sudo and running chmod as root following an su command to enter a root shell.  Can anyone tell me what I'm doing wrong or not doing that I need to do in order to get these permissions set properly?  It wouldn't be that much of an issue except that I have shell scripts (game installers downloaded from GOG) on an external HDD that won't run and I can't seem to add execute permissions to them no matter what I do.

---

