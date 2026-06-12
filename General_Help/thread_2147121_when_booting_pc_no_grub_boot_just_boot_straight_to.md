---
title: "when booting pc no grub boot just boot straight to windows"
date: 2013-05-20
forum: General Help
---

### Post by snowlizard31 on 2013-05-20
I just installed ubuntu 12.04 lts on my pc and as soon as it restarted instead of going to the grub menu it boots straight to windows. I've shut down my computer and turned back on serveral times but still no grub menu. I was thinking that maybe it was my tv (Using my TV as a monitor) but i tried moving the arrow keys up and down to delay the automatic boot but that seems to do nothing. If I press F2 or F11 I go straight to my motherboard menu. My motherboard is an AsRock pro3.

---

### Post by oldfred on 2013-05-20
With new motherboard like that you have both UEFI and BIOS modes. Did you install Ubuntu in the same mode as Windows? Best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by snowlizard31 on 2013-05-21
Thanks man I was beginning to think it was a problem with my TV. So I guess the problem was that the grub boot img wasn't being found?

 [http://paste.ubuntu.com/5685937/](http://paste.ubuntu.com/5685937/)

for some reason the forums not letting me mark this as solved? Or maybe I can find the option.

---

### Post by oldfred on 2013-05-21
So was it just that grub was not installed to the MBR and not any video related issue.

See my signature and version with screen shots:
       Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

