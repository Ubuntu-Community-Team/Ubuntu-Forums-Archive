---
title: "Can’t get Ubuntu to boot on Ryzen 5 3600 with Tomahawk B450 Motherboard"
date: 2020-10-24
forum: General Help
---

### Post by twogod3 on 2020-10-24
Hello everyone, I’m kinda new to Linux and I’m really tired of Windows so I decided to try Ubuntu, but I keep getting the error “amd-vi completion-wait loop timed out.” I have tried to modify the boot and add “apci=off” but that didn’t fix it. If there’s anyone who could help it would be greatly appreciated.

---

### Post by dino99 on 2020-10-25
you might check the 'secure boot' inside the uefi/bios and turn it off if not already done.
[https://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/](https://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/)

---

### Post by twogod3 on 2020-11-24
I have tried that already and for some reason my pc is still not able to boot the latest version of Ubuntu or even some of the older versions

---

### Post by Goettschwan on 2020-11-24
Hi, i recently switched to a tomahawk B550 with Ryzen 5 3600 and it runs great, I didn't have to do anything. I run 20.04LTS.
How did you install ubuntu, or are you trying to boot from installation CD or USB?

---

### Post by oldfred on 2020-11-24
Have you updated UEFI and if SSD, SSD firmware?

Some issues are common by Brand across multiple models.
Some issues are common by chip set/CPU across multiple brands.

These may offer some suggestions.
MSI TRX40 PRO WiFi Motherboard
[https://askubuntu.com/questions/1269853/ubuntu-boot-failure-on-amd-threadripper-3960x-cpu](https://askubuntu.com/questions/1269853/ubuntu-boot-failure-on-amd-threadripper-3960x-cpu)

Asrock B450 UEFI & Driver update to stop flickering.
[https://pcpartpicker.com/b/t4KBD3](https://pcpartpicker.com/b/t4KBD3)
Asrock B450M Steel Legend - turn UEFI Secure Boot off
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)
Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

MSI B450 Tomahawk Max & MSI Nvidia GTX 1080 TI UEFI update & defaults
[https://ubuntuforums.org/showthread.php?t=2450961](https://ubuntuforums.org/showthread.php?t=2450961)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)

---

### Post by Yellow Pasque on 2020-11-25
First, Update the BIOS/EFI.
If you still have issues, try disabling "SVM Mode" in your EFI to work around the issue. It's not ideal to keep SVM disabled if you run VM's, but maybe it will allow you to install Ubuntu and then you can turn it back on.

---

### Post by TheFu on 2020-11-25
I don't have a Ryzen 3xxx or MSI motherboard.  Mine is a Ryzen 2600 and Asus ROG.

Definitely ensure you have the most recent BIOS update.

If you have more than 2 sticks of matched RAM, you may find they are not really the same speeds.  I've had to relax some memory speed settings and increase the volts a tad to get 4 sticks working.  Using the DOCP (AMD's term for XMP) memory profile doesn't always work. I'm running 3200 Mhz RAM at 2800Mhz to get a stable system.  

I've not seen the issue with SVM disabled.  To me, if SVM didn't work, I'd not have any reason to keep that system.

Getting a Ryzen system to boot and getting a system to be stable were all about the RAM settings for me.  Instability would show up hours, even days later.
```
$ uptime 
 09:36:47 up 7 days, 11:08,  4 users,  load average: 11.73, 11.97, 11.38
```
It is a busy system. All 12 threads (6-cores), working hard.

---

### Post by hamzee110 on 2021-08-03
[COLOR=#000000][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=&amp]Running 3600 + B450 Gaming Plus. Works with Ubuntu 18.04. Doesn't boot 19.04. I tested with a few of the latest BIOS versions from MSI (newest one dated 08/30) and none seem to have the fix for rdrand implemented yet. It looks like Ubuntu 19.10 should have the systemd workaround / fix but it would be nice to see the [AMD ]("https://finalratings.com/best-b550-motherboard-for-amd-ryzen-5-3600/")fix implemented on these motherboards as well.
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by oldfred on 2021-08-03
@hamzee110
If you have a specific issue please start your own thread.
But both 19.04 and 19.10 are obsolete. 18.04 is now newer.

Ubuntu 18.04.5 LTS released Aug 14, 2020
[https://lists.ubuntu.com/archives/ubuntu-announce/2020-August/000260.html](https://lists.ubuntu.com/archives/ubuntu-announce/2020-August/000260.html)
Ubuntu ubuntu-18.04.4 - Fourth 18.04 point release, with 19.10 kernel
Ubuntu 18.04.3 LTS Released - Switches To Using 19.04's Linux 5.0 HWE - Aug 2019

With new hardware better to use 20.04 LTS and if very new hardware you may need newest kernel & drivers in 21.04.

Ubuntu 19.04 support ended on January 23, 2020. 
19.10 EoL - July 17, 2020 Support ended

---

