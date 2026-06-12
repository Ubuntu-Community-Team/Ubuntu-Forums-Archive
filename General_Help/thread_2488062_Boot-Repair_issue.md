---
title: "Boot-Repair issue"
date: 2023-06-21
forum: General Help
---

### Post by cpjet64 on 2023-06-21
I have a ubuntu 22 server hyper v VM at home that I use to host a website for some gaming friends and there was a power spike and outage that cooked some of my servers. I was able to restore everything else from backups but the backups for this particular server were corrupted. I tried using boot repair installed on a livecd and it keeps prompting for adding repos for grub and the kernel. Please see [https://paste.ubuntu.com/p/qjYFxs6d2N](https://paste.ubuntu.com/p/qjYFxs6d2N) and screenshots listed below. Really hoping one of the wizards on here can help me magic this server back online. Please and thank you in advance!!

[https://prnt.sc/7UlXnYEyNtXs](https://prnt.sc/7UlXnYEyNtXs)
[https://prnt.sc/JqExBNdf8WMC](https://prnt.sc/JqExBNdf8WMC)
[https://prnt.sc/iZ92ZTMprGpp](https://prnt.sc/iZ92ZTMprGpp)
[https://prnt.sc/JRo7RU5XD0DN](https://prnt.sc/JRo7RU5XD0DN)
[https://prnt.sc/AWJoCphxBgYj](https://prnt.sc/AWJoCphxBgYj)
[https://prnt.sc/8tMmwZz1hF4T](https://prnt.sc/8tMmwZz1hF4T)
[https://prnt.sc/-eH2HpxGmhtd](https://prnt.sc/-eH2HpxGmhtd)
[https://prnt.sc/KYA5qGr27sRB](https://prnt.sc/KYA5qGr27sRB)

EDIT: Adding in the error screen when I try booting the VM which is why I started trying boot-repair in the first place. 
[https://prnt.sc/YM9FAL4cEA-u](https://prnt.sc/YM9FAL4cEA-u)

---

### Post by MAFoElffen on 2023-06-22
I'm surprised it got that far...

Look at this:
```

===================================== UEFI =====================================

BIOS/UEFI firmware: Hyper-V UEFI Release v4.0(4.0) from Microsoft Corporation
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: [COLOR=#ff0000]0001[/COLOR]
Timeout: 0 seconds
BootOrder: [COLOR=#ff0000]0001,0003,0005,0000[/COLOR]
Boot0000* EFI Network    AcpiEx(VMBus,,)/VenHw(9b17e5a2-0891-42dd-b653-80b5c22809ba,635161f83edfc546913ff2d2f965ed0e8d04e340598f5e4f8386a6c0a64a6ae9)/MAC(000000000000,0)/IPv4(0.0.0.00.0.0.0,0,0)
Boot0001* EFI SCSI Device    AcpiEx(VMBus,,)/VenHw(9b17e5a2-0891-42dd-b653-80b5c22809ba,d96361baa104294db60572e2ffb1dc7f130f2c2f0dd8724b9fbb74d9e4a877f3)/SCSI(0,0)
Boot0002* FrontPage    MemoryMapped(11,0x100000,0x5dffff)/FvFile(4042708a-0f2d-4823-ac60-0d77b3111889)
[COLOR=#ff0000]Boot0003* ubuntu    HD(1,GPT,7d051ba2-699b-48e5-aebf-25b40bee2f21,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi)[/COLOR]
Boot0004* FrontPage    MemoryMapped(11,0x100000,0x5dffff)/FvFile(4042708a-0f2d-4823-ac60-0d77b3111889)
Boot0005* EFI SCSI Device    AcpiEx(VMBus,,)/VenHw(9b17e5a2-0891-42dd-b653-80b5c22809ba,d96361baa104294db60572e2ffb1dc7f130f2c2f0dd8724b9fbb74d9e4a877f3)/SCSI(0,1)

```
I would change it, booted from a Live ISO image, by first confirming what you see there...
```

sudo efibootmgr -v

```
Look at the Boot order line... Then what they mean underneath that. I would probably change that to
```

sudo efibootmgr -o 0003,0001,0005,0000

```
Next question, which was unclear, what point does does it stop in the boot process?

---

### Post by cpjet64 on 2023-06-22
OK so I did what you suggested and tried booting again but that had no effect. I also re-enabled UEFI boot on the VM settings. 
The last part of my original post I added in a screenshot of when the boot process stops. 
The boot process starts when I start the VM and on its own stops at that screenshot. 

Sorry if I am misunderstanding you my knowledge of Linux systems at this level is quite limited outside of what I can google. 

After making those changes I tried using boot-repair again to no success and this is the paste for it. [https://paste.ubuntu.com/p/FZN28rYTZR/](https://paste.ubuntu.com/p/FZN28rYTZR/)

---

### Post by cpjet64 on 2023-06-22
Here is the screenshot for the current HyperV settings for boot order. [https://prnt.sc/-9DJefb0WPAU](https://prnt.sc/-9DJefb0WPAU)

---

### Post by MAFoElffen on 2023-06-22
So you said this was cause during a power spike/outage issue right?

First I would do
```

sudo su
modprobe dm-mod  
vgscan --mknodes
vgchange -ay
lvscan
fsck /dev/ubuntu-vg/ubuntu-lv

```
To ensure that the filesystem is okay...

If it didn't find any errors, I would reinstall fresh, then restore your app's, config's and data.

Why?
> 
The libseccomp library provides an easy to use, platform independent, interface to the Linux Kernel's syscall filtering mechanism.

That is pretty 'deeply' ingrained in the system base...

---

### Post by cpjet64 on 2023-06-22
So the filesystem is ok and its mountable but when I click through the different folders there seems to be a ton of files missing. Most of my data is there still though so I might try copying as much as I can to a external source. Is it possible to just take the libseccomp library from a working install and paste it into place? Also I uploaded a video showing everything I have mentioned so far. [https://youtu.be/tWTmWwB8krg](https://youtu.be/tWTmWwB8krg)

---

### Post by MAFoElffen on 2023-06-22
From being booted from the LiveCD ISO, if you mounted and chrooted into the installed system, then did
```

sudo apt install --reinstall seccomp libseccomp2 libseccomp-dev

```
That should reinstall that. You might give that a try. But that assumes that 'that' is the only problem there. Like yoou said, there seems to be other files missing right?

---

### Post by MAFoElffen on 2023-06-22
Overnight, I was thinking about the didferent things that could have happened if something like this happens. Oe possibility is that you said you restored from backups, right? If in the backup or restore process, if it didn't carry over the correct permissions of that, then it might get that error...

So the challenge would be to find and display that for each instance that it might be installed to... So I came up with this:
```

mafoelffen@Mikes-B460M:~$ [COLOR=#ff0000]sudo find / -iname libseccomp.so* 2> /dev/null -exec ls -la {} \; -exec file {} \;[/COLOR]
-rw-r--r-- 1 root root 125360 Mar 17  2022 /usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3
/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5e29725d7f0bd8cb9a04f40eb45d6b75ca6bfbd2, stripped
lrwxrwxrwx 1 root root 19 Nov 18  2022 /usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.3
/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.3
lrwxrwxrwx 1 root root 19 Mar 11 10:06 /var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.4
/var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.4
lrwxrwxrwx 1 root root 19 Mar 11 10:06 /var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so -> libseccomp.so.2.5.4
/var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so: symbolic link to libseccomp.so.2.5.4
-rwxr-xr-x 3 root root 132384 Dec 31  1969 /var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so.2.5.4
/var/lib/flatpak/runtime/org.freedesktop.Sdk/x86_64/22.08/3715fe3720da094e879065c1e579b6a85e3d236f6af3d00afa4ed7c9dfcfc2cb/files/lib/x86_64-linux-gnu/libseccomp.so.2.5.4: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5a2885a1a68d1dbb813bcaebbe534a45087d23de, stripped
-rwxr-xr-x 3 root root 132384 Dec 31  1969 /var/lib/flatpak/runtime/org.freedesktop.Platform/x86_64/22.08/fbf27ccac0fa9bcbf428ed8669caf1304e3e0a2d238808abb9543f2edcad57a9/files/lib/x86_64-linux-gnu/libseccomp.so.2.5.4
/var/lib/flatpak/runtime/org.freedesktop.Platform/x86_64/22.08/fbf27ccac0fa9bcbf428ed8669caf1304e3e0a2d238808abb9543f2edcad57a9/files/lib/x86_64-linux-gnu/libseccomp.so.2.5.4: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5a2885a1a68d1dbb813bcaebbe534a45087d23de, stripped
lrwxrwxrwx 1 root root 19 Mar 11 10:04 /var/lib/flatpak/runtime/org.freedesktop.Platform/x86_64/22.08/fbf27ccac0fa9bcbf428ed8669caf1304e3e0a2d238808abb9543f2edcad57a9/files/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.4
/var/lib/flatpak/runtime/org.freedesktop.Platform/x86_64/22.08/fbf27ccac0fa9bcbf428ed8669caf1304e3e0a2d238808abb9543f2edcad57a9/files/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.4
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/core20/1950/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.1
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.1
-rw-r--r-- 1 root root 133568 Nov 19  2021 /snap/core20/1950/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=80108cfbe42d83a2ed67ea79fd131058f300833d, stripped
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/core20/1891/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.1
/snap/core20/1891/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.1
-rw-r--r-- 1 root root 133568 Nov 19  2021 /snap/core20/1891/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1
/snap/core20/1891/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=80108cfbe42d83a2ed67ea79fd131058f300833d, stripped
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so -> libseccomp.so.2.5.1
/snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so: symbolic link to libseccomp.so.2.5.1
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.1
/snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.1
-rw-r--r-- 1 root root 133568 Nov 19  2021 /snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1
/snap/gnome-3-38-2004/140/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=80108cfbe42d83a2ed67ea79fd131058f300833d, stripped
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so -> libseccomp.so.2.5.1
/snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so: symbolic link to libseccomp.so.2.5.1
lrwxrwxrwx 1 root root 19 Nov 19  2021 /snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.1
/snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.1
-rw-r--r-- 1 root root 133568 Nov 19  2021 /snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1
/snap/gnome-3-38-2004/137/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=80108cfbe42d83a2ed67ea79fd131058f300833d, stripped
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so -> libseccomp.so.2.5.3
/snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so: symbolic link to libseccomp.so.2.5.3
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.3
/snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.3
-rw-r--r-- 1 root root 125360 May 15 22:53 /snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3
/snap/gnome-42-2204/105/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5e29725d7f0bd8cb9a04f40eb45d6b75ca6bfbd2, stripped
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so -> libseccomp.so.2.5.3
/snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so: symbolic link to libseccomp.so.2.5.3
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.3
/snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.3
-rw-r--r-- 1 root root 125360 Jun  2 10:54 /snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3
/snap/gnome-42-2204/111/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5e29725d7f0bd8cb9a04f40eb45d6b75ca6bfbd2, stripped
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/core22/634/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.3
/snap/core22/634/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.3
-rw-r--r-- 1 root root 125360 Mar 17  2022 /snap/core22/634/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3
/snap/core22/634/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5e29725d7f0bd8cb9a04f40eb45d6b75ca6bfbd2, stripped
lrwxrwxrwx 1 root root 19 Mar 17  2022 /snap/core22/750/usr/lib/x86_64-linux-gnu/libseccomp.so.2 -> libseccomp.so.2.5.3
/snap/core22/750/usr/lib/x86_64-linux-gnu/libseccomp.so.2: symbolic link to libseccomp.so.2.5.3
-rw-r--r-- 1 root root 125360 Mar 17  2022 /snap/core22/750/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3
/snap/core22/750/usr/lib/x86_64-linux-gnu/libseccomp.so.2.5.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=5e29725d7f0bd8cb9a04f40eb45d6b75ca6bfbd2, stripped

```
That would show all instances, the permissions of, and where the symbolic links point to... Still thinking on this for you.

Of course from the LiveCD ISO (since it doesn't boot), to run that query, you would either have to chroot ito the installed VM, or mount it from the Live Image Environment, and change the find command to start the search from that mount point, instead of from "/"...

---

