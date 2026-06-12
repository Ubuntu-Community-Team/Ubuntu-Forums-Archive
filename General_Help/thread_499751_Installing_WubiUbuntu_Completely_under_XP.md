---
title: "Installing Wubi/Ubuntu Completely under XP"
date: 2007-07-13
forum: General Help
---

### Post by geekoid on 2007-07-13
Hi Ago and others,

How about this for a suggestion?  When installing Ubuntu, why make the user's machine unusable during a reboot/install?

Why not use QEMU (or similar) to perform the installation during the user's XP session, with the option to boot into the new OS when complete, or to run it under QEMU?

What do you think?  Possible?  Simple?

geekoid

---

### Post by ago on 2007-07-13
Not sure whether you mean running windows under qemu or wubi under qemu. I assume the second case.

The reason I do not like it is that in a VM you always put the hosted OS in a worse spot than the hosting OS:

1 The user does not dedicate the full attention to the new environment. So for instance if you have to do something like sending an email, you generally do not bother to try to do it with a windowed OS, you use the host. In a dual boot, you try to see how you can send an email. 

2. The hosted system is slower and you lose direct hardware access. This means no compiz that for Linux is a strong "selling point" 

3. You need to run the host in order to run the hosted OS in a VM scenario. 

A dual boot is fairer for comparisons, and more captivating. Finally our aim is to be as close as possible to a regular installation, which means dual boot.

Having windows withing Qemu/KVM/Virtualbox inside Ubuntu would be  a completely different story and a most welcome addition IMO ;)... Particularly using [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) or wine package integration...

That said, it is very well possible to have a separate wizard that transforms wubi into a VM environment, but that would likely be a third party app since we will always go for dual boot. With some modifications (use a separate boot disk with grub, kernel and a normal initrd and change fstab) it should be possible to run wubi within colinux / qemu. You might want to use colinux which is generally faster.

---

### Post by tuxcantfly on 2007-07-13
> Why not use QEMU (or similar) to perform the installation during the user's XP session, with the option to boot into the new OS when complete

The idea certainly is possible (from what I see, you're suggesting that we just use a VM for the installation, installing to a raw-formatted virtual disk, adjusting the Lupin code to mount it with an offset so that the qemu-specific stuff is ignored and only the ext3 filesystem is mouunted, then use the standard loopmounted booting approach in a native environment, not VM, afterwards), the major issue is that there would be a major installation speed slowdown; VMs are slower than natively running operating systems (though some VMs, like Colinux, run at practically native speed, so the install speed issue isn't that significant). Besides, Windows wouldn't quite be in a too usable state during the installation anyhow, due to the major disk access which would lead to disk I/O lockups.

Your suggested approach certainly is more user-friendly (could just have the vm running in the background, and all the user sees is a nice progress bar), and possible (explained above), and opens some new possibilities, such as the ability to run the same Ubuntu install in both a VM and in real-mode, like Topologilinux does, but it would lead to a slightly longer installation time; given that users are pretty impatient, and don't seem to be too intimidated by the 2-reboot approach, I think the current method is fine for now. Also, bundling in all that VM software would lead to quite a large increase in size, which we're trying to minimize since we aim to have Wubi included on the Gutsy CD.

If you could suggest any VM software that's FOSS, runs at near-native speed (like Colinux), and has a small size (preferably a MB or less), I'd gladly try to implement it, though; the first impression on reboot is a quite important aspect of the new-user experience...

If the aim is just to reduce the number of reboots and make the installation look nicer, though, the current d-i interface could be substituted with a gtk-framebuffer interface (that's already in debian etch and should be coming to ubuntu soon), and the number of reboots can be reduced by chrooting into the new install immediately following installation rather than rebooting, though of course, that would still not be as user-friendly as the install in VM under Windows and reboot into a loopmounted Ubuntu install approach...

---

### Post by CrazyGuy123 on 2007-07-13
I like the idea of this approach, but I suspect it may not be as easy as it sounds because hardware detection for the host machine can't be done while inside a VM.  The result would be like the very early original versions of wubi where no installation as such was done - just a pre-installed disk image was extracted and used, however that version was plagued with hardware compatibility issues.

---

### Post by ago on 2007-07-13
Hmm I skimmed the original message and missed the installation-inside-VM bit... I do not think that is viable for the reasons exposed by CrazyGuy and Tux.

That should not be much of an issue anyway since:

1. Next release, if based on live CD should be even faster then the current one (since packages are copied and not installed), and you could have a full installation within 5-10 minutes.
2. You will have a nice looking graphical progress bar
3. You might be able to boot straight into the newly installed system (so 1 reboot only).

And hopefully also the download manager will be faster than now.

---

### Post by CrazyGuy123 on 2007-07-15
> **ago said:**
> 
3. You might be able to boot straight into the newly installed system (so 1 reboot only).
.

Off topic for the wubi forum, but since you mentioned it, might it be possible to do this for a conventional liveCD installation as well, maybe even using your code?  That would shave another 30 secs of the standard liveCD installation, and reduce the complexity of having to remove the cd to prevent it booting from it again.

It would also mean you could have a true Ubuntu system working from a blank HD in 0 reboots.

---

### Post by mirak63 on 2007-10-05
colinux is geat but it needs a huge patch to the kernel

the main thing that lacks in colinux is the graphic display.
You need an external X.
It would be perfect if it had a software frame buffer.

---

