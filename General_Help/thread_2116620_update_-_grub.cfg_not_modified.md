---
title: "update - grub.cfg not modified"
date: 2013-02-16
forum: General Help
---

### Post by rnerwein on 2013-02-16
hi
today i run an update with a new kernel ( Ubuntu 12.04.2 LTS, kernel 3.2.0-38-generic).
by the side - i did this on feb the 13th too.
my problem is the new kernel isn't shown in "grub.cfg". but for details see the apendix.
and yes - itried update-grub, reboot ... nothing helps.
have a look at the attachement.
up - where is it ? sorry i'll try again.
ciao

---

### Post by rnerwein on 2013-02-16
hope here is my attachement 
ciao

---

### Post by oldfred on 2013-02-16
It says it is updating menu.lst which is grub legacy??

Better to post this and it may help you upgrade fully to grub2 from grub legacy. It you really want grub legacy it will not fix it but will show more details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Impavidus on 2013-02-16
Something similar has happend to me.  New kernels wouldn't appear in the grub legacy menu, although update-grub reported them as detected. Installing grub2 solved the problem. Grub2 can be installed through synaptic and will properly deinstall grub legacy and provide clear instructions on how to migrate.

[http://ubuntuforums.org/showthread.php?t=2098308](http://ubuntuforums.org/showthread.php?t=2098308)

In your case I notice that you update grub legacy (menu.lst) and find out that the new kernel isn't present in the configuration of grub2 (grub.cfg) and the menu. Which grub version do you have according to the menu at boot? Version number should be present on the first line.

And maybe you've multiply Linux versions on your computer. Are you sure this one controls grub?

---

### Post by rnerwein on 2013-02-16
> **oldfred said:**
> It says it is updating menu.lst which is grub legacy??

Better to post this and it may help you upgrade fully to grub2 from grub legacy. It you really want grub legacy it will not fix it but will show more details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
hi
thanks for the answer. but the question is - where does it come from.
1. when i boot i see in the menue:grub2-common  1.99-21ubuntu3.8

2. in /var/log/dpkg.log.1 i see
    2013-01-22 14:02:34 status half-installed grub-common 1.99-21ubuntu3.7
    2013-01-22 14:02:34 status half-installed grub-common 1.99-21ubuntu3.7
    2013-01-22 14:02:34 status unpacked grub-common 1.99-21ubuntu3.8
    2013-01-22 14:02:35 status unpacked grub-common 1.99-21ubuntu3.8

3. update-grub even tells me
    Found GRUB 2: /boot/grub/core.img (see my attachement)

4. and the command: grub --version gives me
     grub (GNU GRUB 0.97)

 5. 12.04.1 LTS was a fresh install and this version, i think, already comes with "grub 2"

 6. i run all updates and always use "apt-get" to get new software-packets
      where does GRUB 0.97 comes from. i wonder too before when i found "menu.lst" in /boot/grub.
 the boot-menue comes from grub2 using grub.cfg

chiao
:confused::confused::confused::confused:

---

### Post by oldfred on 2013-02-16
If you did an install of grub you get grub legacy installed. grub2's package is grub-pc for BIOS and now grub-efi for the new UEFI systems.

Boot-Repair will help you uninstall grub and reinstall grub-pc. Or you can do that manually. Just be sure Internet is working as while grub is uninstalled and before grub2 is successfully downloaded you will not be able to boot.


Chroot not required if you can boot.
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    
HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by grahammechanical on 2013-02-16
Ubuntu 9.10 was the first Ubuntu to get Grub 2 (or 1.95, 1.96 or something like that). If the System was upgraded from 9.04 to 9.10 then the menu.lst remains on the system but is not used. So, an upgrade path from 9.04 to 12.04 and everything in between would still leave menu.lst in place.

But this was a fresh install and I do not see menu.lst on the fresh installs that I have done.

Regards.

---

### Post by rnerwein on 2013-02-17
> **oldfred said:**
> If you did an install of grub you get grub legacy installed. grub2's package is grub-pc for BIOS and now grub-efi for the new UEFI systems.

Boot-Repair will help you uninstall grub and reinstall grub-pc. Or you can do that manually. Just be sure Internet is working as while grub is uninstalled and before grub2 is successfully downloaded you will not be able to boot.


Chroot not required if you can boot.
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    
HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)
hi oldfred 
:p :p :p +1
this was an instruction how it is to make.
here is the output of my /proc/version:
Linux version[COLOR=Red] 3.2.0-38-generic[/COLOR] :p (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #60-Ubuntu SMP Wed Feb 13 13:22:43 UTC 2013
it works out of the box. and oh yes i installed "grub" to get the man pages. (this is a hidden trap ! )
thanks for the instructions
ciao
    richi
p.s. i'll close this thread - but give other people time (2 days) to read the solution - i think i am not alone.

---

