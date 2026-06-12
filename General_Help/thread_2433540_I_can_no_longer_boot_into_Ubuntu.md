---
title: "I can no longer boot into Ubuntu"
date: 2019-12-20
forum: General Help
---

### Post by stanthemanalreadyused on 2019-12-20
I figure this will be difficult to explain, but here goes...
My ageing PC (circa 2008 Dell XPS 1st gen i7) has two disks, which I boot into Linux or Windows 10 via the BIOS boot (I hit F12). Has worked for a very long time.
Recently, as of three/four months ago,  I have found that I can no longer boot into Ubuntu which is on the secondary disk, I get the GRUB primary boot menu, but when I select Ubuntu, the PC just eventually hangs (the fans slow down, then speed up, then slow down, then up..., then the monitor goes into power-save mode, then nothing).
So I created various Boot disks, from ISO's, from Windows and find that booting from these CD's:
SystemRescueCD v6 does exactly the same thing as the Linux HardDisk.
Ubuntu 18.04 LTS [LEFT][COLOR=#222222][FONT=Verdana]does exactly the same thing as the Linux HardDisk.
Ubuntu 16.04 also [LEFT][COLOR=#222222][FONT=Verdana]does exactly the same thing as the Linux HardDisk, thinking that an earlier version would work.
But, Hiren's Rescue CD v15 DOES boot OK. Doing a disk check with this reports no issues.
The BIOS on my PC has a diagnostics function, mostly memory checks that take a long time, but all pass.
I have also wanted to try to boot Centos too, but the issue here is that the current Centos version requires dual layer DVD's which I don't have, I'm not even sure if my DVD will create them. Downloading and burning this stuff takes a very long time!
So, basically, why does Windows 10 boot fine, but not Ubuntu?
Thanks, any ideas welcome[/FONT][/COLOR][/LEFT][B][I][U][SUB][SUP]
[/SUP][/SUB][/U][/I][/B][/FONT][/COLOR][/LEFT]

---

### Post by cpt-ankitsharma on 2019-12-20
It seems to me that either your grub menu is corrupt or overwritten. OR your secondary disc is full. 

You have two options here:

1. Try to repair grub from within windows. 
2. Wipe off the secondary drive from windows first and then try to do a fresh install.

I dont think the problem is with BIOS.

---

### Post by oldfred on 2019-12-20
If you can boot Ubuntu or some other Linux you should be able to run this. And then it may show some issues.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by stanthemanalreadyused on 2019-12-21
So having spent some time on this today, I can't boot Ubuntu install DVD's 18.04 and 16.04, Ubuntu mini.iso on a memory stick and Centos 7.6 DVD. I can however boot SystemRescueCD v6, and of course Windows 10. All the methods that don't boot will boot to GRUB, then hang afterwards, the mini USB just eventually hangs after printing a screen full of 1's with spaces in between. All failures require a hard reboot. I have no idea, other than something hardware related that causes the Kernel to hang, the kernel being the common denominator. I shall try these DVD's and memory stick in another PC (I have an ancient, but reliable and slow Dell laptop) tomorrow, that I think will prove a hardware issue, of some kind, that doesn't affect Windows.

---

### Post by oldfred on 2019-12-21
If you can get to grub menu, remove quiet splash if using UEFI or boot parameters if using BIOS.
This is how to add nomodeset which may be your issue also. Often starting to boot or just booting to grub, is a video issue. What video do you have?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by stanthemanalreadyused on 2019-12-22
Thankyou OldFred for the advice. Adding nomodeset to the boot options allows the system to boot, with very low resolution, but it boots :-) !
I have a Radeon 5770, and for a few weeks I have experienced flickering for a few minutes after startup, I thought this was the monitor, or its maybe unrelated.
Still doesn't explain why Windows works.

I was hoping to re-install Ubuntu on the standalone disk, before sorting out the video issue, but the installation GUI does not allow you to get at/to the necessary buttons at his screen resolution, so it's impossible to proceed!

---

### Post by oldfred on 2019-12-22
I thought nomodeset was just for nVidia?
And that AMD just worked.

In my notes from others on AMD, the newer versions use AMDGPU. And can add an AMDGPU-PRO
       Older cards use the default Radeon  driver.

---

### Post by stanthemanalreadyused on 2019-12-23
When adding nomodeset I get an this error at boot:
[LEFT][COLOR=#242729][FONT=Consolas][drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
Apparently UMS was replaced by KMS, since 10 years ago, after my PC (12-13yrs!) came into being.
I looked here: [https://askubuntu.com/questions/827678/no-ums-support-in-radeon-module-error-when-booting-to-the-ubuntu-16-04-1-insta](https://askubuntu.com/questions/827678/no-ums-support-in-radeon-module-error-when-booting-to-the-ubuntu-16-04-1-insta)
Thanks for the pointer though, it's probably time to upgrade to a newer machine rather than messing around with a newer video card, although I am somewhat stuck without Linux.
[/FONT][/COLOR][/LEFT]

---

