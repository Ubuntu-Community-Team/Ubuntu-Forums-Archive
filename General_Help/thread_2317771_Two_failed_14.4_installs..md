---
title: "Two failed 14.4 installs."
date: 2016-03-19
forum: General Help
---

### Post by ex-para on 2016-03-19
I have used Linux since Ubuntu 8 LTS and installed many times on different computers dual boot with no problems until 14.04 LTS and twice tried installing on two computers with problems both times. The first time just about every thing was wrong including Vista is now unusable and I have yet to put the whole thing right. The second one a brand new Toshiba Satellite with Win10 is more important but again the install went wrong as so far into it an error came up with an option to ignore or re-enter, I ignored which was most likely was my mistake. The install went ahead and looked OK but when finished and rebooted did not boot up and caused big problems with Win10 which took several hours to fix. 

Two things I did on both failed attempts was re-size the drive when the option came up and I wonder if this was the problem. The first one I am not bothered about as I could try a re-install but at the moment I have working as a  server and it seem to be doing the job. The Toshiba has no CD slot but I have external one and I got into BIOS  OK using the power button while pressing ESC and then  F12 with just USB and the Drive to change, but now this will not work at all as it boots strait to Windows every time. I would still like to try to sort it out but not getting into BIOS is kind of limiting my efforts so if anyone has any suggestions about any part of my problem please let me know.

---

### Post by oldfred on 2016-03-19
Best to have one thread on each system, if that is what you want. Then also include in title brand/model system.

For Toshiba, that should be an UEFI install. And some UEFI have fast boot which is different than fast start up in Windows. Fast boot is also a Windows requirement to speed booting of Windows. It assumes no changes to hardware or configuration, and if everything is the same it just reboots without taking time to scan system for hardware. But often then you do not have time to get into UEFI to change settings or get system to recognize changes. Some have to totally power down, including removing battery if laptop, and hold power switch for 10 secv or so, then cold boot and immediately press correct key to get into UEFI/BIOS. Others have to jumper pins on motherboard or even remove coin battery on motherboard to totally reset. And then all changes to UEFI revert to default. Also a UEFI update from vendor reverts to default so keep track of changes. In my UEFI systems I have had anywhere from a few to many settings to change.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

Always best to use Windows own tools to shrink Windows NTFS partitions and reboot immediately so Windows can run its chkdsk. It always requires a chkdsk after a resize. But do not create partitions with Windows. And Linux NTFS driver will not mount Windows that is hibernated nor needs chkdsk. Grub will also not boot systems needing chkdsk or are hibernated. Best to have Windows repair disk or know how to use Windows repair console. With UEFI you can still directly boot Windows from UEFI boot menu or one time boot key, if fast boot is not so fast as to prevent pressing key.

---

### Post by ex-para on 2016-03-20
Thanks for the reply, I will have to carefully digest what you have told me plus shown me and when I think I am ready I will attempt the fix then come back to the forum.

---

