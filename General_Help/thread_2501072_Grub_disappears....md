---
title: "Grub disappears..."
date: 2024-09-22
forum: General Help
---

### Post by sinanb on 2024-09-22
Hello,
I am using a dual boot Lenovo ThinkPad E595, with Ubuntu 24.04.1 LTS and Win11. Past few days I mostly used Win11 and hibernated the machine when I wasn't going to use it. Last night I tried to boot Ubuntu restarting the computer but the computer booted into Windows as if there was not Ubuntu installed. 
Any idea what might have happened? 
sinanb

---

### Post by ajgreeny on 2024-09-22
If you hibernated Windows it would not go through the usual startup/boot processes but would simply restart Windows from where you left it.

I haven't used Windows except as a virtual machine for nearly 20 years but perhaps hibernating Windows that one time re-enables fast-start again meaning that dual boot from Grub is no longer a possibility. 

Wait for others who know Windows better than me to answer, but check to see if your Windows system has fast-start enabled and if so, disable it.

---

### Post by tea for one on 2024-09-22
> **ajgreeny said:**
> If you hibernated Windows it would not go through the usual startup/boot processes but would simply restart Windows from where you left it.
Yes, this could well be the culprit.

Power on the PC and tap F12 - do you see Ubuntu in the PC boot menu?

---

### Post by oldfred on 2024-09-22
Also, if Windows did an update, it probably reset itself to first in UEFI boot order. Grub on major update does the same thing, sets itself as first in boot order.

And Windows updates may turn fast startup on and/or update UEFI firmware which may reset to defaults. Recheck settings in both UEFI & Windows.

---

### Post by sinanb on 2024-09-23
Hi *ajgreeny,* *tea for one *and *oldfred*, 

Thanks to all of you for the replies. 
I disabled the fast startup (which I don't remember turning on) and checked F12 boot options to see Ubuntu there. Booted into Ubuntu, everything works fine. Then restarted and was carried to the Windows environment with no sign of GRUB. Rebooted into Ubuntu and went to the "Advanced options for Ubuntu" (or something like that, at the bottom of GRUB boot options), checked the boot sequence in BIOS to see Win11 is #1 and Ubuntu as #2, changed the boot sequence. Voila! Back to normal. 
Using hibernating did not cause problems previously but may be it was the problem. I think it was an update as *oldfred* mentioned, even though I did not face such a issue. Anyways, I won't use hibernation for a while to see how things go.
Thanks to all of you again.
sinanb

---

### Post by Rubi1200 on 2024-09-23
In order to help others who may have faced this issue, please mark your thread as Solved.

You can do this using the Thread Tools at the top of your original post.

Thanks.

---

