---
title: "Boot from second HDD if first is not found"
date: 2019-04-26
forum: General Help
---

### Post by macros333 on 2019-04-26
Hello,
I have an SSD with Windows 10 installed that I can connect/disconnect with a switch on my PC case. I thought it would be an easy task to setup the system to boot from the Windows SSD if it is connected and if disconnected boot from the second SSD with Linux. Sadly I ran into some problems.

I tried putting Windows on top of the boot list in GRUB but if I disconnect the drive GRUB fails to boot anything. 

Error-massage (German):
```
Sowohl Vorgabe- als auch Alternativeinträge konnten nicht gebootet werden 
```
translated from German to English:
```
Neither default nor alternative entries could be booted
```

Is it possible to specify a secondary boot device in GRUB? 


I am using Kubuntu 19.04

Thank you for your help.

---

### Post by oldfred on 2019-04-26
If UEFI, you probably have only one ESP - efi system partition for booting from both drives.
Most UEFI also lose UEFI settings if a drive is disconnected, but often auto find Windows but not Ubuntu.

With both drives plugged in:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by macros333 on 2019-04-27
> If UEFI, you probably have only one ESP - efi system partition for booting from both drives.
Most UEFI also lose UEFI settings if a drive is disconnected, but often auto find Windows but not Ubuntu.
I first thought I could configure it in UEFI, like I used to do it in BIOS, but as you said it doesn't work like that way anymore. That is why I thought I have to do it in GRUB.

> Please copy & paste link to the Boot-info summary report
[http://paste.ubuntu.com/p/C5m3wMxy2Y/](http://paste.ubuntu.com/p/C5m3wMxy2Y/)

---

### Post by oldfred on 2019-04-27
You only have BIOS installs. Even if hardware is newer UEFI.

With multiple drives do not run any autofix with Boot-Repair as that will install grub to MBR of every drive. But you want to keep Windows boot loader in MBR of sda and grub only in MBR of sdd.

With BIOS installs you should then be able to choose which Legacy/BIOS/CSM entry to boot.
Is sdd an external drive? 
You may also need to turn on allow USB boot or full USB support or similar setting to allow USB booting.
With UEFI Secure Boot default is not to allow USB boot as not secure. But you have to have Secure Boot off to boot in BIOS mode.
But separate setting for USB may still need to be changed.

You also have Windows fast start up on. That sets hibernation flag on all NTFS partitions.
If you want to read/write into NTFS partitions you must turn fast start off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by macros333 on 2019-05-01
> **oldfred said:**
> 
With BIOS installs you should then be able to choose which Legacy/BIOS/CSM entry to boot.

I can choose which device I want to boot, but if I disconnect the primary boot device (windows SSD) the bios sets the secondary (Linux SSD) as the primary boot device. If I reconnect the first SSD (Windows) it sets it as the secondary boot device and boots Linux. 

> Is sdd an external drive? 
No

> You may also need to turn on allow USB boot or full USB support or similar setting to allow USB booting.
With UEFI Secure Boot default is not to allow USB boot as not secure. But you have to have Secure Boot off to boot in BIOS mode.
But separate setting for USB may still need to be changed.

I have USB booting enabled and I can boot from USB (I installed Kubuntu from USB), but both drives are SATA.

> 
You also have Windows fast start up on. That sets hibernation flag on all NTFS partitions.
If you want to read/write into NTFS partitions you must turn fast start off.
Thank you! I had problems with writing on  my NTFS drives and couldn't figure out why. With fast boot disabled writing works again.

---

### Post by oldfred on 2019-05-01
It may just be your UEFI as UEFI is somewhat better at remembering settings.
And UEFI loses a disconnected drive, but with UEFI usually finds Windows when reconnected. With BIOS not sure.
UEFI is only emulating BIOS, so how it gets implemented can vary.

Note that Windows 10 may turn fast start up back on with updates.

---

