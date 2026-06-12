---
title: "grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist."
date: 2016-06-09
forum: General Help
---

### Post by Abdessalem on 2016-06-09
[COLOR=#111111][FONT=Ubuntu]I am trying to install grub2 from a live CD of lubuntu 16.04, I am following [/FONT][/COLOR][this tutorial]("https://www.youtube.com/watch?v=ajs9rO5upZA")[COLOR=#111111][FONT=Ubuntu], after I mounted the [/FONT][/COLOR]/dev/sda1[COLOR=#111111][FONT=Ubuntu] in the mnt folder using this commands

[/FONT][/COLOR]```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
```
[COLOR=#111111][FONT=Ubuntu]Then changing the root directory :

[/FONT][/COLOR]    ```
sudo chroot /mnt
```
[COLOR=#111111][FONT=Ubuntu]But when try installing grub using sudo grub-install /dev/sda I get this error :[/FONT][/COLOR]
```
sudo: unable to resolve host ubuntu
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist.   Please specify --target or --directory.
```
[COLOR=#111111][FONT=Ubuntu]I tried turning off the uefi mode from bios but I think that my bios version doesn't even support it because it is from 2005[/FONT][/COLOR]

---

### Post by oldfred on 2016-06-09
Easier just to use Boot-Repair.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

The chroot reinstall of grub was if major issues, normally just a reinstall of grub would work.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader
[/URL]
 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]
[/URL] If you want to chroot:
      
 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by CantankRus on 2016-06-09
**Edit:** More comprehensive answer above by oldfred

Try [**_[COLOR="#B22222"]Boot-Repair[/COLOR]_**]("https://help.ubuntu.com/community/Boot-Repair")
You can install it from your liveCD. See the section  "**2nd option : install Boot-Repair in Ubuntu**"

---

### Post by Abdessalem on 2016-06-10
Thank you very much, it worked for me  :) !

---

### Post by parker-hugh on 2016-06-27
> **Abdessalem said:**
> Thank you very much, it worked for me  :) !
I'm having the same problem with my ChaletOS 16.04 install on my new DELL Inspiron 5559 laptop which boots with UEFI.

What was it that worked for you.  could you show me the steps as I am quite new to linux and have limited tech knowledge. Thanks.

---

### Post by oldfred on 2016-06-27
@parker-hugh
While to a new user boot issue may seem similar, but almost always something different and better to start your own thread.
But you have newer Dell and not Ubuntu. 

Ubuntu forums does have sub-forums for other Linux distributions.
Do not know what your ChaletOS is based on?
[http://ubuntuforums.org/forumdisplay.php?f=446](http://ubuntuforums.org/forumdisplay.php?f=446)

---

### Post by parker-hugh on 2016-06-28
> **oldfred said:**
> @parker-hugh
While to a new user boot issue may seem similar, but almost always something different and better to start your own thread.
But you have newer Dell and not Ubuntu. 
Hi oldfred, thanks for responding. you are right, I have a different laptop and a different OS, so things will almost certainly be different.  It turns out that there is a bug in the ChaletOS installation ISO that wasn't picked up prior to release. 
> **oldfred said:**
> Ubuntu forums does have sub-forums for other Linux distributions.

Thanks also for the link to 'Ubuntu/Debian BASED' Sub-Forum. I managed to fix the problem by installing boot-repair.  The problem I had with installing ChaletOS was near the end, it kept failing with message....
```
Installing the 'grub2' package, GRUB installation failed. The  'grub-efi-amd64-signed' package failed to install into /target/. Without  the GRUB boot loader, the installed system will not boot.
```
I thought it best to create a post on the ChaletOS forums [http://chaletos.4rumer.com/t265-installing-the-grub2-package-grub-installation-failed](http://chaletos.4rumer.com/t265-installing-the-grub2-package-grub-installation-failed)  where I asked if there was any way to avoid the GRUB error, but it turns out grub-repair is the only option till the ISO is fixed.  Unless you have seen anything on my post that can be fixed without using boot-repair.

> **oldfred said:**
> Do not know what your ChaletOS is based on?
[http://ubuntuforums.org/forumdisplay.php?f=446](http://ubuntuforums.org/forumdisplay.php?f=446)
 Here are some details of my ChaletOS install....
```
chris@DELL-CHALETOS:~$ uname -a        # 20/06/2016
Linux DELL-CHALETOS 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
chris@DELL-CHALETOS:~$ 

chris@DELL-CHALETOS:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
chris@DELL-CHALETOS:~$ 

chris@DELL-CHALETOS:~$ echo $XDG_CURRENT_DESKTOP
XFCE
chris@DELL-CHALETOS:~$ 
```
...so it's based on Xfce desktop.  Thanks again for your feedback oldfred, your input is always appreciated.

---

