---
title: "Ubuntu won´t boot after Windows update"
date: 2022-07-15
forum: General Help
---

### Post by 16fo12 on 2022-07-15
When I installed Ubuntu a year ago, I created a partition (alas) on which I kept Windows, just in case. I've been booting in Windows extremely rarely because I work from Ubuntu only. Two days ago (alas again) I booted in Windows and naturally a ton of updates were waiting for me. So I did the updates choosing "Update and shut down". After that shutdown, however, both Windows and Ubuntu are failing to boot. Windows freezes in "Preparing Automatic Repair" and Ubuntu mostly just gives a black screen (sometimes it says "TPM interrupt not working, polling instead) although I did reach the purple screen twice, managed to enter my password but then it froze.

In UEFI, the computer (HP Zbook mobile workstation, i7) passes the system fast test, on the extensive test it passes the short DST check but freezes on the optimized DST check.

A boot through advanced Ubuntu options/recovery mode also doesn't work (it runs for a while giving error messages like kernel panic, etc. and then freezes).

I've created a live USB stick (which works, I've just used it to install Ubuntu on another computer) but also that won't boot, not even in the safe graphics mode, it starts booting and then freezes. (I've disabled Fast Boot in UEFI).

Is there any way this can be solved? I haven't done a back-up in a week and if nothing else I'd like to recover some of the data from that disk.

Thank you very much for your time.

---

### Post by yancek on 2022-07-15
Generally, some major windows updates will turn hibernation on again and will move windows to first boot in the BIOS firmware but your case seems unusual in that you cannot boot windows either.  You might check the TPM (Trusted Platform Module) in your BIOS firmware to see if it is on or off.  On my HP laptop, windows 10 won't boot if it is off but Ubuntu does.  The TPM option should be under Security in the BIOS.  Not sure this will solve your problem though.

WHich windows version do you have, windows 10/11?  Ubuntu version?  You mention UEFI, are both Ubuntu and windows installed UEFI?  If so, do you have problems selecting both from the EFI menu in the BIOS firmware Boot Options?  Are you seeing these errors booting from the UEFI firmware options or do you see a Grub menu?

If you can't solve this problem, please go to the site below using the Ubuntu USB and download and run boot repair.  Use the 2nd option described  on that page and select the option to Create BootInfo Summary and post the link you get when it finishes here.  Do NOT try to make any repairs as that may make things worse.  If you post the link here, members will be able to view the output which will contain details on your booting>

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 16fo12 on 2022-07-15
Yancek, thanks for the reply.

I disabled TPM, Ubuntu did not freeze immediately but froze a second later. In general, depending of the various booting attempts (simple Ubuntu boot, advanced options/recovery mode, live USB), the booting will start but then freeze.

I have Windows 10, Ubuntu 20.04. Both are visible from UEFI and I can push them up and down in the boot order, that works. I see, however, also the Grub menu and the errors I have been describing happen when I boot from a Grub menu.

I'd gladly download boot repair but I cannot boot even from Ubuntu USB, that freezes too. The farthest I got was to get it to start booting in safe graphics mode but then that froze too.

---

### Post by kurt18947 on 2022-07-15
If you can't boot from the installed hard drive and can't boot from a live USB I wonder if you have a hardware problem. Do you have access to a Windows install disc or USB? Just to see if one of those will boot? Or perhaps another Linux distro USB, maybe Fedora I think that uses a different installer than Ubuntu and its derivatives.

---

### Post by oldfred on 2022-07-15
Windows updates may also do an UEFI update.
That can reset UEFI back to defaults.
Double check Secure Boot, AHCI and any other settings you have to have.
You may have an UEFI setting that says Allow USB boot or full USB support. A UEFI Secure system does not allow USB boot.
If fast start up is on, so you do not have time to press any key to get into UEFI, and do not have USB boot, even repairing a Windows system could be difficult. (Full power down & cold boot may allow getting into UEFI, but my new system even has that as a setting). 

My old Asus motherboard had 7 settings I had to redo after every UEFI update.
My new MSI motherboard, turned UEFI Secure Boot (a Windows setting) back on, even though I have no Windows.

---

### Post by 16fo12 on 2022-07-17
Ok, I tried what [**[COLOR=#000000]kurt18947[/COLOR]**]("https://ubuntuforums.org/member.php?u=1447222") suggested - it wouldn´t boot from a Windows USB, also it didn´t boot from a Fedora USB. It's always the same, I can reach Grub, I can play with BIOS, it starts booting, then it freezes. This morning for the first time I managed to log into Ubuntu after I reset all the BIOS settings, it seemed like it was working I launched Thunderbird then the screen started flashing and the computer froze again. I couldn't log in again. I took the SSD out, managed to recover all the data, restored it on another computer and formatted the SSD, erasing the Windows partition. I put the formatted SSD back into the computer, inserted a live Ubuntu USB and still it won't boot. It starts booting, then it freezes. When I tried to boot in the safe graphics mode I got "Kernel panic - not syncing - fatal exception". When I tried again I got "kernel stack is corrupted in: vt_console_print+0x48a/0x4e0". Any ideas?

---

### Post by oldfred on 2022-07-17
That sounds more like a corrupted flash drive.
I might download ISO again, and use different flash drive.

If newer system, you may need 22.04, to have latest kernel & drivers to support newer hardware.

---

### Post by 16fo12 on 2022-07-19
oldfred, thanks for the reply. In the end I don't know what it was, I'm guessing it was some graphics driver incompatibility, but the problem has been solved. I turned the computer off and held the power button pressed for 15s. On restart it tried to install Windows and failed partitioning the disk. Then I inserted the live Ubuntu USB, the same one I had used before, and this time it installed Ubuntu without any problems.

---

