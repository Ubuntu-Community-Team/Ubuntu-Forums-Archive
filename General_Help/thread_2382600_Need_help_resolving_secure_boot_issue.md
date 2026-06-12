---
title: "Need help resolving secure boot issue"
date: 2018-01-15
forum: General Help
---

### Post by mikejmc3 on 2018-01-15
Computer: HP Pavilion Notebook Model 15-p043cl
OS: Lubuntu 17.10

I removed Windows from my HP notebook and installed Lubuntu 17.10 a while back. I encountered some issues changing the boot order (not sure if this has anything to do with the Ubuntu 17.10 BIOS bug or not), but when I went researching resolutions when I discovered this problem, one recommendation I found was to disable secure boot, which I did. Now it won't boot up anymore. Ugh.

When I turn on the computer, I see a black screen for 1-2 seconds, and then a blue screen that says: "ERROR Verification failed: (15) Access Denied. [OK]." When I press enter, I then see another message that says, "Failed to load image: access denied. start_image() returned access denied." After that, it returns to a black screen and does nothing else.

What I want to do is either find a way to get into the BIOS settings so I can change the boot order and do a fresh OS install (I have not been able to boot from either USB or the DVD-ROM drive) or else bring up GRUB and resolve this secure boot predicament I find myself in. The usual boot keystrokes for HP notebooks DO NOT work (e.g., pressing ESC to pause startup and choose advanced boot options or pressing F10 to see BIOS settings) -- pressing those during the initial black screen only writes a message to the lower-left corner of the screen such as "ESC...Pause Startup" but does nothing else beyond that.

Is there anything else I can do to get back into GRUB and/or my BIOS settings so I can figure out a way to boot this thing up?

---

### Post by oldfred on 2018-01-15
Separate from newer issues with some Insyde UEFI, mostly Lenovo are similar issues with many systems.
You can try a full system shutdows. Remove battery if laptop and hold power switch for 10 sec to drain all power. So system then is doing a total "cold" boot not a warm reboot. You need to press correct keys to then get into BIOS to change settings.

HPs also have other issues, they violate UEFI spec that says NOT to use description as part of boot.
And of course only valid description is "Windows Boot Manager". Many work arounds depending on configuration.

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

Before Boot-Repair did copy of shimx64.efi to use the "fallback" or hard drive entry, many HP users manually copied files.
       
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by mikejmc3 on 2018-01-16
Thanks for the reply. I have tried a number of measures, including pulling the battery and holding the power button to reset the internal CMOS battery. Unfortunately, that did not result in any changes. I also tried creating an HP BIOS recovery USB using the tool on the HP support site. According to HP's documentation, that can be used even if the BIOS is corrupted, but BIOS recovery fails. The HP BIOS recovery documentation does state plainly that it works for Windows only (why the OS would matter for a BIOS recovery, I can't say, but that's their story). I also tried Ultimate Boot CD. When I put that in the DVD-ROM drive and start the computer, I can hear the drive spin, but nothing different happens.

Unfortunately, I cannot copy, move, or alter any EFI, etc. files because my computer literally does nothing expect flash a black screen for a brief moment, and then cut to a blue screen with an error message--that's it. No GRUB menu, no follow-up menu after the error message. Nothing. 

I was hoping there might be some other key that might be helpful. I have tried both holding the right shift key and spamming it when turning on the computer, but neither results in any difference in behavior. And as I previously stated, the usual keys that I would press at startup to bring up BIOS options, such as ESC or F10, don't seem to function. Of course, I have previously set my GRUB timeout to 0 and have fast boot enabled, so I'm probably painted into a corner here. Open to any other suggestions. I would much prefer to avoid taking this thing apart and, say, trying to boot up with the hard drive disconnected.

If there are any other suggestions on keystrokes or other boot disc options besides the one I have tried, I'd love to hear suggestions. Thanks again!

---

### Post by oldfred on 2018-01-16
With fast boot on, you often do not have time to press any key.
Fast boot assumes your entire configuration is identical to previous boot, so it skips all the updates and immediately jumps to starting to boot.
Same with grub at 0 sec.
My motherboard as a fast start setting that lets me set it to 3 sec and same with grub at 3 sec, so I have time if quick to press keys.
Besides the full power down or cold boot, are jumper pins on motherboard. But you need to check manual to find correct pins.
Or remove motherboard coin battery. But that will reset everything on UEFI/BIOS back to defaults. I always save list of settings I have changed as my old system on every BIOS update reset system, so I needed to know what to reset. With UEFI some settings on UEFI update are saved.

Grub does remember key press. And bottom (maybe) entry is an entry is a system setup or firmware option. That should get you into UEFI.
Try pressing down arrow several times, and see if you get different results.

---

### Post by mikejmc3 on 2018-01-22
Thanks for the suggestions. I tried pressing the down arrow, and that did not result in any changes to behavior. 

As for other suggestions, this is a notebook computer, not a desktop, so I assume chances are slim that I will see jumper pins on my motherboard if I tear this thing apart. I'm loathe to do that anyway, but it sounds like there is no other option to force my computer to display either a UEFI options menu or GRUB given the configuration and current status. Appreciate you taking the time to offer some ideas.

---

### Post by oldfred on 2018-01-22
This seems be be somewhat different instructions.

[https://support.hp.com/us-en/product/hp-pavilion-15-p000-notebook-pc-series/6936226/model/7155656/document/c03515402](https://support.hp.com/us-en/product/hp-pavilion-15-p000-notebook-pc-series/6936226/model/7155656/document/c03515402)

---

