---
title: "Adding 2nd drive w/Xubuntu already on it"
date: 2017-05-17
forum: General Help
---

### Post by Autodave on 2017-05-17
Ordered new computer: deal too good to pass up. Of course it is coming with Win 10 on it. I would like to remove the HD from this machine and install it alongside the HD in the new machine. Can I do that or do I still have to worry about UEFI on the Win 10 machine?

If I can just install it, I seem to recall that I need to update grub while logged in to the Xubuntu drive, but I also seem to remember that I need to make the Xubuntu drive the first drive (move Win 10 to second drive)?

---

### Post by Dennis N on 2017-05-17
Your Xubuntu disk must have a UEFI install in order to dual boot with UEFI Windows 10 from grub.

Ideally, when you are ready, put the disk in, turn computer on, and press whatever key gets you into the UEFI firmware. In the boot options section, hopefully the UEFI will have detected the new disk, and maybe it will show Xubuntu as a selection in the boot menu. 

If it does, you could configure Xubuntu at this time to have boot priority #1. Then, after exiting UEFI, and if Xubuntu boots up successfully, run sudo update-grub to detect Windows 10. Future startups should then go to Xubuntu grub.

Important: One hopes things go as planned. But, there may be problems that can't be predicted in advance depending on the different computer hardware and nature of the UEFI firmware on the new machine.

---

