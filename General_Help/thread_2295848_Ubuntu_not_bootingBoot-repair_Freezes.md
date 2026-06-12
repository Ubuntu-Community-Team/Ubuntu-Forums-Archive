---
title: "Ubuntu not booting/Boot-repair Freezes"
date: 2015-09-21
forum: General Help
---

### Post by nfmcclure on 2015-09-21
I successfully installed Ubuntu 14.04 alongside Windows 10 and had everything running smoothly.  I was installing the CUDA libraries and the machine froze mid-install.  I proceeded to reboot and nothing happened, the loading screen didn't even come about.  I booted up via live-usb and ran Yann's boot-repair application.  The 'recommended repair' option freezes the whole computer about 1 minute in.

Luckily, it was able to complete the diagnostic ability and here is the output: [http://paste.ubuntu.com/12518875/](http://paste.ubuntu.com/12518875/)

Not sure where to go from here or even what to look up.  I think something got corrupted along the way.  I'm at a point where I don't want to do anything further, at the risk of further damaging the install.

Running gparted from the live usb, results in these partitions:

[TABLE="class: grid, width: 500"]
[TR]
[TD]Partition[/TD]
[TD]File System[/TD]
[TD]Label[/TD]
[TD]Size[/TD]
[TD]Used[/TD]
[TD]Unused[/TD]
[TD]Flags[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]ntfs[/TD]
[TD]WINRE_DRV[/TD]
[TD]1000.00MiB[/TD]
[TD]294.74MiB[/TD]
[TD]705.26MiB[/TD]
[TD]hidden, diag[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]fat32[/TD]
[TD]SYSTEM_DRV[/TD]
[TD]260.00MiB[/TD]
[TD]35.53MiB[/TD]
[TD]224.47MiB[/TD]
[TD]boot, hidden[/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]fat32[/TD]
[TD]LRS_ESP[/TD]
[TD]1000.00MiB[/TD]
[TD]505.38MiB[/TD]
[TD]494.62MiB[/TD]
[TD]hidden[/TD]
[/TR]
[TR]
[TD]/dev/sda4[/TD]
[TD]unknown[/TD]
[TD][/TD]
[TD]128.00MiB[/TD]
[TD]---[/TD]
[TD]---[/TD]
[TD]msftres[/TD]
[/TR]
[TR]
[TD]/dev/sda5[/TD]
[TD]ntfs[/TD]
[TD]Windows8_OS[/TD]
[TD]424.77GiB[/TD]
[TD]58.54GiB[/TD]
[TD]366.23BiG[/TD]
[TD]msftdata[/TD]
[/TR]
[TR]
[TD]/dev/sda8[/TD]
[TD]unknown[/TD]
[TD][/TD]
[TD]1.00MiB[/TD]
[TD]---[/TD]
[TD]---[/TD]
[TD]boot[/TD]
[/TR]
[TR]
[TD]/dev/sda9[/TD]
[TD]ext4[/TD]
[TD][/TD]
[TD]449.86GiB[/TD]
[TD]22.99GiB[/TD]
[TD]426.87GiB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda10[/TD]
[TD]linux-swap[/TD]
[TD][/TD]
[TD]15.92GiB[/TD]
[TD]4.00KiB[/TD]
[TD]15.92GiB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda6[/TD]
[TD]ntfs[/TD]
[TD]LENOVO[/TD]
[TD]25.00GiB[/TD]
[TD]2.80GiB[/TD]
[TD]22.20GiB[/TD]
[TD]msftdata[/TD]
[/TR]
[TR]
[TD]/dev/sda7[/TD]
[TD]ntfs[/TD]
[TD]PBR_DRV[/TD]
[TD]13.63GiB[/TD]
[TD]9.45GiB[/TD]
[TD]4.18GiB[/TD]
[TD]hidden, diag[/TD]
[/TR]
[/TABLE]

I'm more than willing to post more output as required here.  Just let me know the commands I should run.

Thanks!

---

### Post by oldfred on 2015-09-22
You have grub installed to both MBR for BIOS boot and to ESP - efi system partition for UEFI boot. You can only use one or the other.
Since Windows is UEFI, really best to only use UEFI and not use BIOS boot at all. To dual boot with Ubuntu in BIOS, you cannot use grub to dual boot. You only can boot from UEFI boot tab or perhaps one time boot key. You may have to turn on/off UEFI or CSM/BIOS boot mode to boot system installed in that mode.

You also show two efi partitions. sda2 & sda8
While UEFI spec may allow more than one, we have yet to see a system that boots with two efi partitions. Use gparted and remove boot flag form sda8. 
Note that Lenovo has more efi boot files in sda3 labeled LRS_ESP, but it does not have boot flag so not directly seen as the ESP - efi system partition for booting. Not sure how Lenovo uses it, but for its recovery or own system files.

It looks like Boot-Repair or last install has you configured for UEFI boot as now you have the mounting of the efi partition in fstab. With BIOS boot you would not have that.

Can you boot ubuntu entry from UEFI boot tab or one time boot key?
Have you tried adding the entry to BCD as shown at bottom of Boot-Repair's report? Some find that Work around ok. But you boot into Windows and then reboot into grub.

Other work arounds. Most rename bootx64.efi or use rEFInd.
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

Also more details on copying grub to bootx64.efi in link below in my signature.

---

### Post by nfmcclure on 2015-09-23
Thanks for the reply!  I actually got to boot and started the update process from 14.04 to 15.04.  But when I got to 14.10, the OS started to freeze randomly.  Eventually it just booted up to a blank screen with a blinking mouse.  I think something is really wrong, so I decided to format the drive, repartition, and reinstall Ubuntu with 15.04.

Things get strange here, so I'm going to start a different thread because I think this problem is different entirely.

But your advice got the system to boot up!  Thank you for the response!

---

