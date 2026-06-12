---
title: "dist-upgrade: EFI directory not found error processing package grub-efi-amd64-signed"
date: 2018-02-10
forum: General Help
---

### Post by arto-o-makkonen on 2018-02-10
Hi,

My updates in Ubuntu LTS 16.04 stopped working, possibly after a Windows10 update.

```
$ sudo apt-get dist-upgrade 
Luetaanpakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteidenpuu       
Luetaan tilatiedot... Valmis       
Käsitellään päivitystä... Valmis
0päivitetty, 0 uutta asennusta, 0 poistettavaa ja 0päivittämätöntä.
2 ei asennettu kokonaan taipoistettiin.
Toiminnon jälkeen käytetään 0  t lisäälevytilaa.
Haluatko jatkaa? [K/e] k
Tehdään asetuksia:grub-efi-amd64-signed (1.66.16+2.02~beta2-36ubuntu3.16)...
Installing for x86_64-efi platform.
**grub-install:virhe: cannot find EFI directory.**
**dpkg: errorprocessing package grub-efi-amd64-signed (--configure):**
 aliprosessikomentotiedosto post-installation asennettu palautti virhetilakoodin1
Tehdään asetuksia: shim-signed (1.33.1~16.04.1+13-0ubuntu2)...
Installing for x86_64-efi platform.
[B]grub-install:virhe: cannot find EFI directory.
dpkg: error processing packageshim-signed (--configure):[/B]
 aliprosessikomentotiedosto post-installation asennettu palautti virhetilakoodin1
Käsittelyssä tapahtui liian montavirhettä:
 grub-efi-amd64-signed
 shim-signed
**E:Sub-process /usr/bin/dpkg returned an error code (1)**
```

Myhard drive configuration is as follows:

```
$ sudo fdisk-l
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type:gpt
Disk identifier: [XXXX]

Laite          Start      Loppu   Sektorit  SizeTyyppi
/dev/sda1        2048    1333247   1331200  650M Windows recoveryenvironment
/dev/sda2     1333248    1865727    532480  260M EFI System
/dev/sda3    1865728    2127871     262144  128MMicrosoft reserved
/dev/sda4     2127872 11135862431111458372  530G Microsoft basic data
/dev/sda5  11135877121115541503    1953792  954M Windows recoveryenvironment
/dev/sda6  1115541504 1167970303  52428800   25G Linux filesystem
/dev/sda7  11679703041184747519   16777216    8G Linux-sivutus
/dev/sda8 1184747520 1453182975  268435456  128G Linuxfilesystem
/dev/sda9  1920847872 1953513471   3266560015,6G Microsoft basic data
```

Note that the grub worksjust fine in boot and Ubuntu starts normally. It is only the updatesthat do not work anymore.

I'm stuck and would hate tore-install - help needed!

---

### Post by oldfred on 2018-02-10
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Report will have lots of details.
First then to check is if UUID in fstab of ESP - efi system partition matches what your sda2 partition.

Or maybe you need repairs on sda2.
       
 [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by arto-o-makkonen on 2018-02-11
Here's the BootInfo summary report link [http://paste.ubuntu.com/=QpzyrB7BKk/](http://paste.ubuntu.com/=QpzyrB7BKk/) 

For some reason /boot/efi seems to have been commented out in /sda6/etc/fstab: 
# /boot/efi was on /dev/sda2 during installation
#UUID=EE10-4B61  /boot/efi       vfat    defaults        0       1

---

### Post by oldfred on 2018-02-11
Not another HP. :(

You do need to uncomment the mount of the ESP - efi system partition in your fstab.
Boot-Repair normally comments out the one with 0077 and adds a new one with defaults. That is to make it easy to update entries in ESP.
With 14.04 Ubuntu used defaults, but changed to 0077, I assume for security reasons. I do change mine to defaults as I want ease of change, but may later change back to 0077 for security. 

You need to turn Windows fast start up off. Grub/Linux NTFS driver will not see nor mount the NTFS partition(s) that are hibernated.
Note that Windows updates may turn fast start up back on.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

If you run Boot-Repair it will add a new grub entry 25_custom with all the HP .efi files. Those are for HP's tools, but really do not need to be in grub.
Many edit or comment out the 25_custom entries.

HP is not UEFI dual boot friendly. It violates UEFI standard that says NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager". But many work arounds. But not using the "ubuntu" entry that you should be able to use as a default.
Workarounds also in link in my signature below.
Many use the fallback or hard drive boot entry which still works. Some that use Windows mostly use an entry in Windows BCD that reboots system on uses UEFI one time reboot. Some just use the UEFI boot menu which seems to work as one time entry, each time.
Some add rEFInd another boot menu or boot manager. UEFI is a boot manager & grub is both a boot manager (menu) and boot loader.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
      
 HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)

Boot-Repair now does the copy.
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by arto-o-makkonen on 2018-02-11
Oldfred - thanks, uncommenting the /boot/efi line in fstab has solved the issue!

I will also apply some of the other tips & tricks you have shared but now closing this thread as solved.

---

