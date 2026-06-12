---
title: "Windows 8 missing from boot menu after reinstalling Ubuntu 12.10"
date: 2013-02-09
forum: General Help
---

### Post by pavirad on 2013-02-09
I installed Ubuntu 12.10 in my  new Windows 8 pre-installed Toshiba Satellite L875D laptop. After the installation I ran the following commands and got Windows 8 in the boot menu along with Ubuntu.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
  boot-repair


After this I was playing with display driver options and had to reinstall Ubuntu. I did a reinstall on top of the existing install. Again after the install I ran the above set of commands to get Windows 8 back in boot menu. But this time it did not work and I'm kind of stuck with it. 



Log URL [http://paste.ubuntu.com/1630727/](http://paste.ubuntu.com/1630727/)



Please help! Thanks in advance.

---

### Post by oldfred on 2013-02-09
Welcome to the forums.

I am not sure how you reinstalled but you overwrote the entire Windows install. Only the efi partition still has the Windows boot files, but no MSR, no Windows main partition, no Windows recovery partition, and no vendor recovery partition to restore Windows. 

Did you make backups of Windows before installing? Or the Vendor DVDs to restore Windows? The only other option is to call the vendor and order the DVD set. Usually just a nominal charge, some may have a way to download.

---

### Post by pavirad on 2013-02-09
:( I feared so. Thank you for the reply.

I had recovery USB created. I will proceed with that.

---

### Post by oldfred on 2013-02-09
Original post was in wrong thread.

I do not have any examples of Toshiba systems that have worked. Not sure if they just work or if the fall into the category of difficult to get to work well.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Other systems that have worked.
       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

            Dell XPS13 Details on how to install - UEFI and Intel SRT  in Post #10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

    
       [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557)

---

