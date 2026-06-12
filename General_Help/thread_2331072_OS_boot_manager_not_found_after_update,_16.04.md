---
title: "OS boot manager not found after update, 16.04"
date: 2016-07-18
forum: General Help
---

### Post by xadder on 2016-07-18
I have had a clean install of 16.04 working on my HP x360 for a couple of months, but after a software update yesterday (which asked for a reboot) I get:

Boot device not found
please install an operating system on your hard disk
Hard disk (3F0)

After which the system just hangs. Now, if I re-start and enter the bios, I can get things working using a series of steps for the boot device (choosing <ubuntu>, then some <grub...> option.  

Other info:

In the boot screen I also see that I am using UEFI, with the Boot order showing:

USB diskette on key/USB Hard Disk
OS Boot manager
USB CD/DVD ROM drive
! USB network adapter

If I try to choose OS Boot manager though, I get: "OS Boot Manager is not found"

There is also a "Legacy Boot Order", but attempting to enable that gave "Changing this setting may make the system unable to boot the OS. Do you want to make this change". I have no idea if this is safe to try or not.

Help appreciated!

---

### Post by oldfred on 2016-07-18
Do not use legacy, that is CSM/BIOS/Legacy. And if your install is UEFI it will not work.

Best to see all details, you can run from install, if you can boot or from live installer:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by xadder on 2016-07-18
Thanks. I ran the boot-repair, and get the following:

[http://paste2.org/z2M0eyA7]("http://paste2.org/z2M0eyA7")

Just a little more info (which may be obvious from this report), but I have only Xubuntu installed, no interest in Windows.

---

### Post by oldfred on 2016-07-18
HP has not been dual boot friendly. Not sure what you had before, but there are many work arounds to get HP's to boot.
But HP violates UEFI spec that says not to use description as part of boot. And only valid description is "Windows Boot Manager".

So one work around when only booting Ubuntu is to rename boot entry for shim to Windows. Then boot Windows but really shim/grub.
Other work around is to create the fallback/hard drive boot entry. I generally do that also, but my system boots ubuntu entry ok.

       
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1, otherwise additional parameters required.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Best to backup ESP - efi system partition, your sda1 before any changes.

You may want to run Boot-Repairs fixes. One of the fixes is to reset entry in fstab to allow updates to /EFI/ubuntu. Entry is 0077 which prevents changes, but older versions used defaults which still works and allows changes.
      ```
 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat [COLOR=#ff0000]   defaults[/COLOR]        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 

    
     
```
But you need your UUID, if you manually change it. And you have to reboot to have it work. I found the sudo mount -a while you should run to verify no edit isssues, does not change the permissions until you reboot.

Dual booters have to use the fallback/hard drive entry.
 [http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by xadder on 2016-07-19
Thanks again! 

I'll wait a week or so until I'm back at work before trying any of that stuff, so I have my office PC handy to check your instructions and to have a browser handy to look after any hurdles. The odd thing is that I have had Xubuntu installed (as only OS) since April and this problem just started after the last software update (17th Jul). Looking at my /boot directory, I see that the likely culprit is the vmlinuz-4.4.0-31-generic.efi.signed file:

$ls -lt  | head -6
total 267096
drwxr-xr-x 5 root root     4096 jul 18 15:42 grub
-rw------- 1 root root  7049432 jul 17 11:07 vmlinuz-4.4.0-31-generic.efi.signed
-rw-r--r-- 1 root root 36182965 jul 17 11:07 initrd.img-4.4.0-31-generic
-rw-r--r-- 1 root root  1240067 jul 13 03:59 abi-4.4.0-31-generic
-rw-r--r-- 1 root root   189558 jul 13 03:59 config-4.4.0-31-generic

For the next week I can boot by entering bios, choosing EFI, ..., ubuntu, shimx64 and this seems to to work fine. (Or do a lot of suspending, but that causes some other minor issues.)
Thanks again!

---

### Post by xadder on 2016-08-04
Quick update. For no reason I can think of, my PC now boots into Xubuntu again without any problems. I assume one of the updates over the last week changed something again....!

---

