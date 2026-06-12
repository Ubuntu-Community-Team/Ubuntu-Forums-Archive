---
title: "Launching k3b"
date: 2007-10-05
forum: General Help
---

### Post by Rumpty on 2007-10-05
Using Ubuntu Feisty. 

I have been trying k3b. Installed it and all its dependencies, but it has never worked for me. When I try to run it, it freezes the computer at the k3b splash screen.

But just the other day I found, by accident,  that it will launch it there is a CD in the drive. Any old CD will do, apparently. It takes a while, 15secs perhaps, but it does launch, and works.

Any idea what is going on, please? It shouldn't need a disk in the drive to launch, should it?

---

### Post by p_quarles on 2007-10-05
> **Rumpty said:**
> Using Ubuntu Feisty. 

I have been trying k3b. Installed it and all its dependencies, but it has never worked for me. When I try to run it, it freezes the computer at the k3b splash screen.

But just the other day I found, by accident,  that it will launch it there is a CD in the drive. Any old CD will do, apparently. It takes a while, 15secs perhaps, but it does launch, and works.

Any idea what is going on, please? It shouldn't need a disk in the drive to launch, should it?
No, it shouldn't. Try running it from the command line with the command "k3b" and make a note of the errors it gives you. If you post them here, someone might be able to help.

---

### Post by Rumpty on 2007-10-07
> **p_quarles said:**
> No, it shouldn't. Try running it from the command line with the command "k3b" and make a note of the errors it gives you. If you post them here, someone might be able to help.

Here is the last part of the output before the freeze.

/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()

---

### Post by Rumpty on 2007-10-08
The problem seems to be with my CD writer Ricoh MP7240A. With it unplugged from the IDE cable, k3b will open properly. With it plugged in to the IDE cable, K3b freezes at the splash screen.

But if there is a CD in the Ricoh, and it is plugged in of course, k3b will open. 

Can anyone shed any light on this?

One other thing, I see that the command when k3b is launched from the desktop menu is <k3b %U> How does this relate to using just <k3b> from a terminal?

Thanks.

---

