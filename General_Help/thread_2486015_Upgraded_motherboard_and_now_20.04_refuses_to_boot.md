---
title: "Upgraded motherboard and now 20.04 refuses to boot"
date: 2023-04-18
forum: General Help
---

### Post by lasivian on 2023-04-18
I am getting these errors and I do not know how to proceed.

[https://imgur.com/a/n6fo3kK](https://imgur.com/a/n6fo3kK)

Thanks

---

### Post by yancek on 2023-04-18
Just a guess here since all the errors refer to ACPI.  Do you have an option to enable ACPI in the BIOS?  If you do, enable it and try again.

Have you been able to try the suggestions in the error message to log in to a terminal to view system logs, etc.?
Is this an EFI install of Ubuntu and is Ubuntu the only OS installed?

---

### Post by MAFoElffen on 2023-04-18
I have questions based on your title: "Upgraded motherboard and now 20.04 refuses to boot"

So this computer had Ubuntu 20.04 running fine. You upgraded the motherboard. Now it will not boot, showing ACPi errors.

What motherboard is it? What upgrades did you do?

---

### Post by lasivian on 2023-04-18
> **MAFoElffen said:**
> I have questions based on your title: "Upgraded motherboard and now 20.04 refuses to boot"

So this computer had Ubuntu 20.04 running fine. You upgraded the motherboard. Now it will not boot, showing ACPi errors.

What motherboard is it? What upgrades did you do?

The motherboard died, so we used components from another system. The board is an MSI B360 Gaming Plus MS7B22. It was running fine in a Windows 10 computer. We upgraded the bios to the latest version, nothing changed and no new settings popped up.

We are thinking about doing a new install on a new SSD and just moving things, but we don't know how to move the software raid we had.

---

### Post by lasivian on 2023-04-18
> **yancek said:**
> Just a guess here since all the errors refer to ACPI.  Do you have an option to enable ACPI in the BIOS?  If you do, enable it and try again.

Have you been able to try the suggestions in the error message to log in to a terminal to view system logs, etc.?
Is this an EFI install of Ubuntu and is Ubuntu the only OS installed?

There do not seem to be any meaningful options for ACPI. Only two useless ones like changing the power like blinking.

I don't know if this is an EFI or how to check that. It does come up with Grub on boot if that helps.

---

### Post by #&amp;thj^% on 2023-04-18
> **lasivian said:**
> 
I don't know if this is an EFI or how to check that. It does come up with Grub on boot if that helps.
two ways to see that:
```
ls /sys/firmware/efi
config_table  esrt              fw_vendor      runtime      systab
efivars       fw_platform_size  mok-variables  runtime-map
```

```

me on Tue Apr 18 at 11:40 AM in /etc/apt/sources.list.d branch: (HEAD) 
>> sudo efibootmgr
[sudo] password for me: 
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0003,0001,2001,2002,2003
Boot0000* ubuntu
Boot0001* ubuntu
Boot0003* kaisen
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network



```
Or one more:
```
sudo dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.70 by INSYDE Corp.

```

---

### Post by lasivian on 2023-04-18
> **1fallen said:**
> two ways to see that:
```
ls /sys/firmware/efi
config_table  esrt              fw_vendor      runtime      systab
efivars       fw_platform_size  mok-variables  runtime-map
```

```

me on Tue Apr 18 at 11:40 AM in /etc/apt/sources.list.d branch: (HEAD) 
>> sudo efibootmgr
[sudo] password for me: 
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0003,0001,2001,2002,2003
Boot0000* ubuntu
Boot0001* ubuntu
Boot0003* kaisen
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network



```
Or one more:
```
sudo dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.70 by INSYDE Corp.

```

ls cannot access. So I am guessing it does not exist.

---

### Post by MAFoElffen on 2023-04-18
This will tell what mode it is booted as, but also what it is capable of...
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmidecode -t 0,1,4

```
Confirmed that motherboard manual says the only BIOS Settings that are settable for ACPI are:
```

ACPI Settings
   Sets ACPI parameters of onboard power LED behaviors. Press Enter to enter the sub-menu.

     Power LED [Blinking]
       Sets shining behaviors of the onboard Power LED.
     [Dual Color] The power LED turns to another color to indicate the S3 state.
       [Blinking] 
       The power LED blinks to indicate the S3 state.

     CPU Over Temperature Alert [Auto]
       Enables or disables the CPU overheating alert when CPU temperature is over 80 degrees centigrade.

```

---

### Post by MAFoElffen on 2023-04-18
I looked up the errors and found this:
```

[0.392600] ACPI BIOS Error (Bug): Could not resolve symbol [\_SB.PAGD.STA._OSI], AE_NOT_FOUND (20201113/psargs-330)
[0.395125] ACPI Error: Aborting Method \_SB.PAGD.STA due to previous error  (AE_NOT_FOUND) (20201113/psargs-529)
[0.462711] ACPI BIOS Error (Bug): Could not resolve symbol [\_SB.PAGD.STA._OSI], AE_NOT_FOUND (20201113/psargs-330)
[0.462733] ACPI Error: Aborting Method \_SB.PAGD.STA due to previous error  (AE_NOT_FOUND) (20201113/psargs-529)
[0.520375] ACPI BIOS Error (Bug): Could not resolve symbol [\_SB.PAGD.STA._OSI], AE_NOT_FOUND (20201113/psargs-330)
[0.520401] ACPI Error: Aborting Method \_SB.PAGD.STA due to previous error  (AE_NOT_FOUND) (20201113/psargs-529)
[0.710064] Initramfs unpacking failed: Decoding failed
[2.759141] tpm tpm0: tpm_try_transmit: send(): error -62
[2.759176] tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling inst
[3.708294] ACPI BIOS Error (Bug): Could not resolve symbol [\_SB.PAGD.STA._
[3.708385] ACPI Error: Aborting Method \_SB.PAGD.STA due to previous error
[3.734529] ACPI BIOS Error (Bug): Could not resolve symbol [\_SB.PAGD.STA._
[3.734567] ACPI Error: Aborting Method \_SB.PAGD.STA due to previous error
/dev/nvme0n1p2: clean, 283295/61022208 files, 9573235/244059136 blocks

```
Looks familiar doesn't it?

Was with Ubuntu 20.04, and was told that: 
> 
Generic answer: this is a normal error when hardware is too new for the kernel. The BIOS is reporting info the kernel did not expect when probing it.

What I posted as queries would have shed some light on this... Still do them please.

Try to boot it from an Ubuntu 22.04.2 Installation LiveUSB and see if it boots...

---

### Post by lasivian on 2023-04-18
> **MAFoElffen said:**
> 
Try to boot it from an Ubuntu 22.04.2 Installation LiveUSB and see if it boots...

We can get it to boot from a new install of 22.04.2 that we made with a LiveUSB. But the issue with that is that we can't get the raid to re-assemble on that install.

[https://ubuntuforums.org/showthread.php?t=2486058](https://ubuntuforums.org/showthread.php?t=2486058)

Stuck between two problems and can't fix either one of them, lol.

I guess i'll focus on the raid since I don;t have any clue how to update a kernel without being able to boot the OS.

Thanks.

---

### Post by MAFoElffen on 2023-04-18
Followed your link to your other thread to help you there...

---

