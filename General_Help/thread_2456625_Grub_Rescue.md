---
title: "Grub Rescue"
date: 2021-01-15
forum: General Help
---

### Post by SpikeLS6 on 2021-01-15
My PC was OFF when my UPC battery failed. However, when I booted up the screen came up into "grub rescue>" mode.

grub rescue> set yields:
cmdpath=(hd0)
lang=
locale_dir=
prefix=(hd0,msdos1)/boot/grub
root=hd0,msdos1
secondary_locale_dir=

I tried grub rescue> intmod normal:
  error: symbol 'grub_calloc' not found
I tried grub rescue> boot
  error: you need to load the kernel first (I believe the latest kerrnel is linux 5.8.0-38 generic)

I am unable to get to the regular Terminal screen to update or upgrade Grub.

---

### Post by oldfred on 2021-01-15
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2021-01-15
If you are getting grub rescue it is because the grub configuration file can't be found.  When you boot, enter the command below and try it

.>  grub> configfile (hd0,msdos1)/boot/grub/grub.cfg

If that fails, make not of the exact error and post back.

---

### Post by SpikeLS6 on 2021-01-15
Need help with Oldfred's PPA and other requests.

Tried configfile (hd0,msdos1)/boot/grub/grub.cfg:
  Unknown command 'configfile'.

---

### Post by oldfred on 2021-01-15
I do not know difference but grub rescue> and grub> are different errors.

Best just to run Boot-Repair and post link to its Summary Report.

---

### Post by SpikeLS6 on 2021-01-15
I finally got Boot Repair to run out of the Grub Rescue> Safe file. The Paste file is at: [https://paste.ubuntu.com/p/RWhX8TDRvp/](https://paste.ubuntu.com/p/RWhX8TDRvp/)

I have not run the Repair part until I hear from the forum.

---

### Post by grahammechanical on 2021-01-15
You have two hard drives - sda has windows on it - sdb has Ubuntu on it. Make sure that the BIOS utility is giving sdb the boot priority. At the Grub menu select Advanced Options for Ubuntu. Then select a Linux kernel with Recovery mode.

At the recovery menu select Network to set up an internet connection. Then select Root. That will give you a root shell prompt where you can run

```
update-grub
grub-install /dev/sdb
```

When finished type exit to get back to the recovery menu and select Resume to load Ubuntu with a low resolution open source video driver. If you get that far - reboot to load Ubuntu with your normal video driver.

See how that goes.

Regards

---

### Post by oldfred on 2021-01-15
Do not run autofix from Boot-Repair as it installs grub to MBR of all drives.
You really want Windows boot loader in MBR of sda.

Only use Boot-Repair's advanced mode, and choose an operating system and drive to install boot loader into.
Boot-Repair may install a Windows type (syslinux) boot loader to sda & grub to MBR of sdb.
Otherwise use your Windows repair/recovery flash drive to install a Windows boot loader to sda.

You have older BIOS/MBR configuration.
While you have to have MBR for Windows to boot in BIOS mode, I suggest planning to convert any new or reformatted drive that is just Linux or data to gpt.
That is more a longer term planning. But I started converting to gpt in 2010.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by SpikeLS6 on 2021-01-16
I went completely through grahammechanical's suggestions and the PC came up correctly. I then did a Restart and several turn OFF and turn ON boots. The PC seems to be functioning normally.

I will go through oldfred's reference posts to learn more about GPT. I did not use the Boot Repair Tools boot repair recommendations; only the Boot-Info Summary Report. If I need to use the Boot Repair Tool, please let me know.

I will show this issue as SOLVED.  Thank you!

---

### Post by oldfred on 2021-01-16
Grub only boots working Windows.
So best to have Windows boot loader in the Windows drive and set Ubuntu drive as default boot.
When Windows does not work you then from BIOS can directly boot Windows and maybe repair it. 
Still best to have a Windows repair/recovery flash drive for Windows.

Windows fast start up is often turned back on with updates which sets hibernation flag. 
Then grub also will not boot it.

---

### Post by SpikeLS6 on 2021-01-16
I will look into a windows 10 boot loader USB. I also have to learn about the gpt which I had never heard of. More home work to do.  Thank you.

---

### Post by oldfred on 2021-01-16
I started converting to gpt in 2010.
I converted one drive and installed Ubuntu on it. With BIOS it has to have a bios_grub partition. My Windows XP was on a MBR partitioned drive.
I also used gpt on all new flash drives. larger ones with full Ubuntu install.

Then when Windows required vendors to use UEFI/gpt I started to make new drives gpt but with both the bios_grub and an ESP. Only one or other actually required. But if converting a drive from BIOS to UEFI, you then do not have to totally repartition. There is a conversion tool.
Windows in BIOS boot mode, must be MBR partitioned, so it cannot be converted, unless you do a total new install.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by SpikeLS6 on 2021-01-16
Lots more reading to do! Thank you.

---

