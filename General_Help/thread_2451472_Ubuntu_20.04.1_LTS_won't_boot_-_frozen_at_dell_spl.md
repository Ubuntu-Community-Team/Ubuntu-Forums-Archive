---
title: "Ubuntu 20.04.1 LTS won't boot - frozen at dell splash screen"
date: 2020-10-05
forum: General Help
---

### Post by scrawl2 on 2020-10-05
hoping i can signal-boost a post i made on askubuntu yesterday, or get an answer here. [post link]("https://askubuntu.com/questions/1279995/ubuntu-20-04-1-lts-wont-boot-frozen-at-dell-splash-screen")

post text:

dell xps 15 7590 (Core i7-9750H) (NVIDIA GeForce GTX 1650, 4 GB, GDDR5)


ubuntu 20.04.1 LTS (laptop shipped with win10 - wiped windows and installed ubuntu ~1 month ago)


bios version 1.8.1


as of 5 days ago laptop boot freezes at dell splash ("ubuntu" never appears at the bottom). only difference between this boot and last successful one was that i had a hdmi connecting laptop to a monitor this time (never connected previously, during boot or otherwise). have been trying to repair this weekend with no joy. 


thru `Esc` -> `Advanced options for Ubuntu` i can boot recovery mode just fine. the os partition seems okay. 


dell pre-boot diagnostics returns all-clear, but then says "no bootable device" when it tries to boot. 


there are many posts here regarding boot issues. i've tried what i can to no avail. things i have tried:


[LIST]
[*] booting older kernels (5.4.0-45-generic and 5.4.0-42-generic)
[*] disabling secure boot (BIOS system info says "signed firmware update is enabled" so i didn't expect this to work. also there's been no bios update since ubuntu install)
[*] disabling all options in bios boot order (ubuntu, ubuntu firmware updates, windows boot manager), created new boot option for shimx64.efi, then rebooting
[*] replacing "quiet splash" with "nomodeset" in /etc/default/grub (i've read about nvidia issues)
[*] boot repair from usb, "recommended" option. only difference now is on boot dell logo appears, disappears for 3 seconds, reappears. [pastebin results]("http://paste.ubuntu.com/p/N2hMcJQXmn/"). i also ran the "boot info summary" option (after "recommended"... my mistake) and have [this pastebin]("http://paste.ubuntu.com/p/Z2CqxnK72f/")
[*] in recovery mode i checked /var/log/dmesg and syslog for *obvious* signs of error. they might as well be written in klingon! :-)
[*] in recovery mode i tried updating grub bootloader, tho i think boot repair already did this
[*] from usb "Try Ubuntu", i checked filesystem:
[/LIST]


```
sudo fdisk -l
Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem


sudo fsck -f /dev/nvme0n1p2
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)


Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure```
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/nvme0n1p2: 288820/15597568 files (0.8% non-contiguous), 5256908/62383360 blocks
```

any help would be appreciated. if there's more info required let me know. i could reinstall the os again but i want to know why this happened and how to prevent it in the future


output of ```
lspci -k | grep -EA3 'VGA|3D|Display' 
```:



```
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
        DeviceName: Onboard IGD
        Subsystem: Dell UHD Graphics 630 (Mobile)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
--
01:00.0 3D controller: NVIDIA Corporation TU117M [GeForce GTX 1650 Mobile / Max-Q] (rev a1)
        Subsytem: Dell TU117M [GeForce GTX 1650 Mobile / Max-Q]
        Kernel driver in use: nvidia
        Kernal modules: nvidiafb, nvidia_drm, nvidia
```

edit: formatting

---

### Post by dragonfly41 on 2020-10-05
Another Dell user here.

Your EFI partition is listed here

sudo fdisk -l
Device           Start       End   Sectors  Size Type
**/dev/nvme0n1p1**    2048   1050623   1048576  512M **EFI** System
/dev/nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem

I would boot up a LiveUSB again (Try Ubuntu) and use GParted to inspect the EFI partition in /dev/nvme0n1p1

As a "get out of jail card", while you are running LiveUSB I would try installing rEFInd which installs alongside your normal boot. 


[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

[https://www.rodsbooks.com/refind/installing.html#packagefile](https://www.rodsbooks.com/refind/installing.html#packagefile)

See reference here ...

$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind

Quote:
The PPA version asks if you want to install rEFInd to your ESP. (Chances are you want to respond affirmatively.)

at this point in installation define the path to your ESP.                /dev/nvme0n1p1

Now to give an example I am on Dell 3268 and I now install EFI partition in every version of Ubuntu I install. This is so I can boot these individually when required. But you seem to have just one ESP partition previously used by Windows?.

It should look like this ..

/boot/efi
/boot/grub

Now in /boot/efi/

there is seen ..

Boot
Dell
refind
tool
ubuntu


and inside the newly installed refind is

> drivers_x64
> icons
> keys
BOOT.CSV
refind_x64.efi
refind.conf

The important files you will be using are

refind_x64.efi
refind.conf



refind_x64.efi is the loader

and later you might tweak refind.conf to customise themes.

Reboot and look for refind_x64.efi in the grub menu to boot up rEFInd.

---

### Post by scrawl2 on 2020-10-05
hey @dragonfly41

thanks for the quick reply. i'll try this later and report back. regarding this:

 [COLOR=#000000] > But you seem to have just one ESP partition previously used by Windows?.[/COLOR]

I followed the instructions on the Ubuntu website to install as single-boot. if the current ESP partition wasn't rewritten/recreated over the old one, then a) i did something wrong, or b) i don't know... i haven't done this before! :-)

---

### Post by dragonfly41 on 2020-10-05
i admit that this is an outlier suggestion .. usually sudo update-grub does the job but you can't get into your OS so that is why I suggest rEFInd. It should not affect anything, only adding another boot option.

---

