---
title: "Issue with boot loader. Slow . Ubuntu 18.04"
date: 2018-08-22
forum: General Help
---

### Post by infernalzeus on 2018-08-22
The boot loader, when asked to boot into ubuntu . Gives some errors and takes about half a minute before exiting, maybe more
Running on ubuntu 18.04.1 dual booted with windows 10 on inspiron 15 5577

Error image - 
[https://drive.google.com/file/d/1IAKl9qFSCiA-ATXOge0X_ZAzAzs-LO4_/view?usp=drivesdk](https://drive.google.com/file/d/1IAKl9qFSCiA-ATXOge0X_ZAzAzs-LO4_/view?usp=drivesdk)

---

### Post by oldfred on 2018-08-22
Have you updated UEFI from Dell?
And many Dell with SSD need SSD firmware updated also.
Note UEFI update will reset many UEFI parameters to defaults. You need to reset them. 
UEFI Secure Boot off, allow USB boot, drives set to AHCI, maybe others.

You can attach screenshots here with Forum's advanced editor and paperclip icon. 
Then I do not have to create a google account to see your error.

Is your system Intel or Amd?

       Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

While different models issues are often common across many models of same brand.
       
 Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)

---

### Post by infernalzeus on 2018-08-23
Hi
The uefi bios was updated last week as i was having an audio issue after the dual booting.
My laptop is not amd. It is an nvidia gtx 1050 with intel i7
The only issue for me is that the so called loading takes a lot of time. The functionality of the OS seems fine to me, as i dont experience anything that might be Happening in the backend

---

### Post by infernalzeus on 2018-08-23
[ATTACH=CONFIG]280826[/ATTACH][ATTACH=CONFIG]280826[/ATTACH]sorry for the poor picture quality

also my secure boot is disabled

---

### Post by oldfred on 2018-08-23
Have you installed the nVidia driver from Ubuntu repository?
Or if you installed incorrect one, did you purge before installing correct one?

       [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 
   If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Some have had slow boot where UUID in fstab was incorrect. Usually caused by reformatting a partition. It then has to time out.
Or system is looking for hardware you do not have. One user had floppy drive turned on in BIOS and system could not find it since he did not have one.
 
More to confirm configuration:
      
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by infernalzeus on 2018-08-24
Hi
I was facing lot more issues with 18. 04 such as completely getting disconnected from the LAN and wireless network. I tried many solutions that were there on the forums and otherwise, none of them seemed to work
it was getting little frustrating for me so I downgraded to 16. 04 lts as right now it is the most stable version in the market
Thanks anyway :)
I can still continue to run 18. 04 on a virtual machine and try to do some bug testing on it

---

