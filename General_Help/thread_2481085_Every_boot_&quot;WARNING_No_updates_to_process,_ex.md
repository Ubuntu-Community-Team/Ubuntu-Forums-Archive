---
title: "Every boot: &quot;WARNING: No updates to process, exiting in 10 seconds.&quot;"
date: 2022-11-18
forum: General Help
---

### Post by Paddy Landau on 2022-11-18
Recently, every time I boot, the screen shows all black except for a cryptic message:

WARNING: No updates to process, exiting in 10 seconds.

Unsurprisingly, this sits on the screen for 10 seconds, and then normal boot resumes. This happens before the Grub menu is displayed.

What is this item, and can I stop it from delaying my boot by 10 seconds? After all, if there are no updates, why should I need to know, and why would it give me a WARNING?

The computer runs Ubuntu 22.04, which I installed a few months ago using the full-disk option with LUKS encryption (so, no other OS is on this machine).

I have a suspicion that it's related to fwupdmgr because of the remarkably few (unhelpful) results that Google returns, but I could well be wrong. The machine is a Dell OptiFlex 5480, in case that makes a difference. Firmware updates are installed automatically by the update system.

---

### Post by #&amp;thj^% on 2022-11-18
> **Paddy Landau said:**
> 
I have a suspicion that it's related to fwupdmgr because of the remarkably few (unhelpful) results that Google returns, but I could well be wrong. The machine is a Dell OptiFlex 5480, in case that makes a difference. Firmware updates are installed automatically by the update system.

I'm encrypted as well on zfs format. 
Paddy I come in peace. ;)
This bug is still around, started back with 18.10 when I first noticed it.
My specs are different than yours so proceed with caution.
```
 inxi -SxFx
System:
  Host: me-xbu Kernel: 5.15.0-53-generic x86_64 bits: 64 compiler: gcc
    v: 11.2.0 Desktop: Xfce 4.16.0 tk: Gtk 3.24.23 wm: xfwm dm: LightDM
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required> Chassis: type: 10 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022

```
**And please be sure to have a current updated Bios.
What I ended up doing was:
```
sudo nano /etc/fwupd/uefi_capsule.conf 
```
and un-comment this:
```
# with the UEFI removable path enabled, the default esp path is set to /EFI/boot
# the shim EFI binary and presumably this is $ESP/EFI/boot/bootx64.efi
#FallbacktoRemovablePath=false

# allow ignoring the CapsuleOnDisk support advertised by the firmware
**_DisableCapsuleUpdateOnDisk=true_** #### This Line
```
This has been reported now and since 18.10
I'm interested if this still shows after a reboot.
EDIT:
```
cat  /etc/fwupd/uefi_capsule.conf | grep DisableCapsuleUpdateOnDisk=true 
DisableCapsuleUpdateOnDisk=true

```

---

### Post by Paddy Landau on 2022-11-18
> **1fallen said:**
> Paddy I come in peace. ;)
I wouldn't have thought otherwise! Thanks for joining.
> **1fallen said:**
> ```
sudo nano /etc/fwupd/uefi_capsule.conf 
```
and un-comment this…
Alas, that didn't work. I rebooted twice in case, but it still shows the message.

I've put the file back to what it was.
> **1fallen said:**
> This bug is still around…
Do you have a link to the bug report? I'll upvote it.

---

### Post by #&amp;thj^% on 2022-11-18
> **Paddy Landau said:**
> 

Do you have a link to the bug report? I'll upvote it.
I'll have to dig for it, it's not on this machine and google shows it as early as 17.10.
Paddy I will try to find those links for you, but this case would at least warrant a fresh bug report, the reason being a lot has changed since those releases.
And I'm sure your Bios are at the latest version, they will ask in the report is why I mention it.
```
apt policy fwupd
fwupd:
  Installed: 1.7.9-1~22.04.1
  Candidate: 1.7.9-1~22.04.1
  Version table:
 *** 1.7.9-1~22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.7.5-3 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 https://mirror.vcu.edu/pub/gnu+linux/ubuntu jammy/main amd64 Packages
        500 http://ubuntu.mirrors.pair.com/archive jammy/main amd64 Packages


```

---

### Post by Paddy Landau on 2022-11-19
> **1fallen said:**
> … this case would at least warrant a fresh bug report, the reason being a lot has changed since those releases.
When I file the report, I'll post back here with the link.
> **1fallen said:**
> And I'm sure your Bios are at the latest version, they will ask in the report is why I mention it.
I don't know how to check. I'll see if I can find out. It should be, because the BIOS firmware updates are automatic.
> **1fallen said:**
> ```
apt policy fwupd
```
My results are almost the same as yours:
```
fwupd:
  Installed: 1.7.9-1~22.04.1
  Candidate: 1.7.9-1~22.04.1
  Version table:
 *** 1.7.9-1~22.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.7.5-3 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```

---

### Post by Paddy Landau on 2022-11-19
> **Paddy Landau said:**
> When I file the report, I'll post back here with the link.
I've just realised that I don't know where to file the bug report. This isn't to do with Ubuntu, is it?

---

### Post by #&amp;thj^% on 2022-11-19
I just talked with someone who wants to remain UN-named>>>>LOL
He was certain this pertains to Secure Boot and fwupd.
He told me it has to do with UEFI signing, and I told him that you was able to boot to a working desktop.
I left this link/post for him to look at.
So at this point, I guess we wait for better instructions.
For your Bios check with Dell and compare against:
```
inxi -M
Machine:
  Type: Laptop System: LENOVO product: 20BFS3NJ00 v: ThinkPad T540p
    serial: <superuser required>
  Mobo: LENOVO model: 20BFS3NJ00 v: 0B98401 WIN serial: <superuser required>
    UEFI: LENOVO v: GMET91WW (2.39 ) **_date: 06/03/2021_**

```

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> I just talked with someone…
Thank you. I had checked my BIOS against the available Dell BIOS firmware, and my BIOS is indeed up-to-date. I was unaware of the [FONT=courier new]inxi[/FONT] command, which makes it easier as I don't have to reboot into my BIOS!
```
$ inxi --machine
Machine:
  Type: Desktop System: Dell product: OptiPlex 5480 AIO v: N/A
    serial: <superuser required>
  Mobo: Dell model: 05T2V2 v: A00 serial: <superuser required> UEFI: Dell
    v: 1.18.0 date: 09/06/2022
```

---

### Post by #&amp;thj^% on 2022-11-20
Ok Paddy here is the juice, they tell me:
> Yes, it is the BIOS that is giving the kernel information that is incorrect (ie. does not follow the specification).
Can you try:
```
sudo nano /etc/defualt/grub
```
[list]And Add
[*]intremap=no_x2apic_optout nox2apic
[*]Add "acpi=off" if it starts complaining about ACPI stuff[/list]
of course "update-grub"
I have always trusted this guy, so lets see if it holds here.

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> 
[LIST]
[*]And Add
[*]intremap=no_x2apic_optout nox2apic
[*]Add "acpi=off" if it starts complaining about ACPI stuff
[/LIST]
Unfortunately, [FONT=courier new]update-grub[/FONT] refused to run, with and without [FONT=courier new]acpi=off[/FONT], because:
```
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: nox2apic: not found
```
I don't know enough about Grub to mess around with it on my own, but Googling this error, shouldn't it be:
```
[FONT=var(--ff-mono)]GRUB_CMDLINE_LINUX="intremap=no_x2apic_optout nox2apic[/FONT][FONT=var(--ff-mono)]"[/FONT]
```
The current setting is:
```
GRUB_CMDLINE_LINUX=""
```

---

### Post by #&amp;thj^% on 2022-11-20
> **Paddy Landau said:**
>  don't know enough about Grub to mess around with it on my own, but Googling this error, shouldn't it be:
```
[FONT=var(--ff-mono)]GRUB_CMDLINE_LINUX="intremap=no_x2apic_optout nox2apic[/FONT][FONT=var(--ff-mono)]"[/FONT]
```
The current setting is:
```
GRUB_CMDLINE_LINUX=""
```

Seems you know more than you thought, and yes it should look exactly like what you show.
I use any parameters in this line though:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash=silent quiet splash"
```
He gave me one more to try if that fails, and in the same place " **mce=off**" 
I'd would only try the single addition with " **mce=off**"  option.
Thanks Paddy for being a great tester here.

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> Seems you know more than you thought…
Thanks, but it was Mr Google who told me!

I tried both of these (separately):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intremap=no_x2apic_optout nox2apic"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intremap=no_x2apic_optout nox2apic mce=off"
```
I didn't use [FONT=courier new]acpi=off[/FONT] because there were no complaints about ACPI.

Alas, neither of them did the trick.

In case you're wondering, I did remember to [FONT=courier new]sudo[/FONT] [FONT=courier new]update-grub[/FONT] each time.

I think that we'll just have to live with the extra 10 seconds each time. Key presses are ignored, but are cached for when the Grub menu appears, which of course could be problematic!

---

### Post by #&amp;thj^% on 2022-11-20
> **Paddy Landau said:**
> 
I think that we'll just have to live with the extra 10 seconds each time. Key presses are ignored, but are cached for when the Grub menu appears, which of course could be problematic!
Yep that sounds like the wisest choice for this.
Again Thanks Paddy for your generosity in trying things out.
Best regards

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> Again Thanks Paddy for your generosity in trying things out.
No problem! Thank you for taking the trouble to investigate it, and thanks to your friend for the suggestions.

---

### Post by Paddy Landau on 2022-11-22
This is interesting…

I have Ubuntu 22.04 on an external USB. It's an emergency system, in case I need something to be able to boot from should the internal disk fail.

I plugged it in and started from it in order to run the updates.

I didn't get the message.

When I finished my updates, I again started from the USB disk, and still no message.

When I restarted from my internal disk, boom, the message reappeared.

I have no clue what might be different, or even what to look at to compare. The file [FONT=courier new]/etc/default/grub[/FONT] is the same on both disks.

---

### Post by maglin2 on 2022-11-22
Any chance this might be signifying failure of the recent UEFI update to version 217 because of incompatible leftover old shim/grub entries on internal drive?
It failed on one of my machines. Turned out that boot/efi still contained a shim from an old Neon install that the new UEFI version took exception to. I removed the offending shim before rebooting though, so I don't know what messages might have appeared if I'd left it.

---

### Post by Paddy Landau on 2022-11-22
> **maglin2 said:**
> Any chance this might be signifying failure of the recent UEFI update to version 217 because of incompatible leftover old shim/grub entries on internal drive?
Sorry, I have no idea if this is the case, or how to check. I don't even know what a shim is!

---

### Post by maglin2 on 2022-11-22
I'm sure you know more than I did before this update appeared (and failed)!
```
$ fwupdmgr get-devices
```
Look for UEFI dbx. If you have version 217 then it's not this.
(This whole idea was far more lateral than logical thinking I should point out).

---

### Post by #&amp;thj^% on 2022-11-22
> **Paddy Landau said:**
> This is interesting&#8230;

I have Ubuntu 22.04 on an external USB. It's an emergency system, in case I need something to be able to boot from should the internal disk fail.

I plugged it in and started from it in order to run the updates.

I didn't get the message.

When I finished my updates, I again started from the USB disk, and still no message.

When I restarted from my internal disk, boom, the message reappeared.

I have no clue what might be different, or even what to look at to compare. The file [FONT=courier new]/etc/default/grub[/FONT] is the same on both disks.
Is secure boot enabled? that would be one of the differences, IE:
```
me@me-ThinkPad-T540p:~$ nala show fwupd
Package: fwupd
Version: 1.7.9-1~22.04.1
Architecture: amd64
Installed: yes
Priority: optional
Essential: no
Section: admin
Source: fwupd
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian EFI <debian-efi@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 6.9 MB
Provides: fwupdate
Depends: 
  libfwupd2 (= 1.7.9-1~22.04.1)
  libfwupdplugin5 (= 1.7.9-1~22.04.1)
  libc6 (>= 2.34)
  libcurl3-gnutls (>= 7.63.0)
  libefiboot1 (>= 37)
  libglib2.0-0 (>= 2.70.0)
  libgnutls30 (>= 3.7.3)
  libgudev-1.0-0 (>= 165)
  libgusb2 (>= 0.3.8)
  libjcat1 (>= 0.1.4)
  libjson-glib-1.0-0 (>= 1.5.2)
  libmbim-glib4 (>= 1.26.0)
  libmbim-proxy
  libmm-glib0 (>= 1.18)
  libpolkit-gobject-1-0 (>= 0.99)
  libqmi-glib5 (>= 1.18.0)
  libqmi-proxy
  libsmbios-c2
  libsqlite3-0 (>= 3.6.1)
  libsystemd0
  libtss2-esys-3.0.2-0 (>= 2.3.1)
  libxmlb2 (>= 0.3.2)
  shared-mime-info
Recommends: 
  python3
  bolt
  dbus
  secureboot-db
  udisks2
  fwupd-signed
Suggests: gir1.2-fwupd-2.0
Replaces: fwupdate, gir1.2-dfu-1.0, libdfu-dev, libdfu1
[B]Conflicts: fwupdate-amd64-signed, fwupdate-arm64-signed, fwupdate-armhf-signed, fwupdate-i386-signed
Breaks: fwupdate (< 12-7), gir1.2-dfu-1.0 (< 0.9.7-1), libdfu-dev (< 0.9.7-1), libdfu1 (< 0.9.7-1)
Homepage: https://github.com/fwupd/fwupd[/B]
Download-Size: 2.6 MB
APT-Sources: http://us.archive.ubuntu.com/ubuntu/ jammy-updates/main amd64 Packages
Description: Firmware update daemon
 fwupd is a daemon to allow session software to update device firmware.
 You can either use a GUI software manager like GNOME Software to view and
 apply updates, the command-line tool or the system D-Bus interface directly.
 Firmware updates are supported for a variety of technologies.
 See <https://github.com/fwupd/fwupd> for details
Notice: There are 1 additional records. Please use the '-a' switch to see them.
```
EDIT: Look here as well:
```
me@me-ThinkPad-T540p:~$ dpkg -l | grep grub-efi
ii  grub-efi-amd64-bin                                          2.06-2ubuntu10                          amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 modules)
ii  grub-efi-amd64-signed                                       1.182~22.04.1+2.06-2ubuntu10            amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
me@me-ThinkPad-T540p:~$ apt-cache search grub-pc
grub-legacy-ec2 - Handles update-grub for ec2 instances
grub-pc - GRand Unified Bootloader, version 2 (PC/BIOS version)
grub-pc-bin - GRand Unified Bootloader, version 2 (PC/BIOS modules)
grub-pc-dbg - GRand Unified Bootloader, version 2 (PC/BIOS debug files)
multiboot - The Multiboot specification
me@me-ThinkPad-T540p:~$ 


```
and:
```

efibootmgr --version
version 17

```

---

### Post by Paddy Landau on 2022-11-23
> **1fallen said:**
> Is secure boot enabled?
My results from all of those are identical to yours. Secure boot is enabled in the BIOS.

---

### Post by Paddy Landau on 2022-11-23
> **maglin2 said:**
> ```
Look for UEFI dbx. If you have version 217 then it's not this.
I have UEFI dbx version 238.
[CODE]&#9474; &#9492;&#9472;UEFI dbx:
&#9474;       Device ID:        *<snip>*
&#9474;       Summary:          UEFI revocation database
&#9474;       Current version:  238
&#9474;       Minimum Version:  238
&#9474;       Vendor:           UEFI:Linux Foundation
&#9474;       Install Duration: 1 second
&#9474;       GUIDs:            *<snip>*
&#9474;       Device Flags:     • Internal device
&#9474;                         • Updatable
&#9474;                         • Supported on remote server
&#9474;                         • Needs a reboot after installation
&#9474;                         • Only version upgrades are allowed
&#9474;                         • Signed Payload
```

---

### Post by maglin2 on 2022-11-23
I'm afraid that's plumbed the depths of my knowledge (and dragged a lot of line along the seabed). Both my machines are at 217, with no further update being offered.

---

### Post by Paddy Landau on 2022-11-23
> **maglin2 said:**
> Both my machines are at 217, with no further update being offered.
I run this command before I run my updates:
```
fwupdmgr --force refresh
```
It might help you. [FONT=courier new]fwupd[/FONT] is a system that supports automatic firmware updates using a centralised repository called LVFS (Linux Vendor Firmware Service). Most major vendors use it.

[Notes from]("https://blogs.gnome.org/hughsie/2022/04/28/fwupd-1-8-0-and-50-million-updates/") the dev.

---

### Post by maglin2 on 2022-11-23
Thanks, but it still says 
```
Devices with the latest available firmware version:
 &#8226; UEFI dbx
```
(My understanding was that the force option only has effect if the last check was less than 24 hours ago).
Update to 217 dbx was quite recent. Neither machine is dual booted with Windows, so I can't personally see a lot of benefit for me in these revocation database updates, which as I've understood it are to keep Microsoft happy.
(Edit: I can't find 238 in LVFS. This is all that shows up  [https://fwupd.org/lvfs/devices/org.linuxfoundation.dbx.x64.firmware](https://fwupd.org/lvfs/devices/org.linuxfoundation.dbx.x64.firmware) )
Anyway, all this is off-topic wrt your initial post, apologies.

---

### Post by #&amp;thj^% on 2022-11-23
> **Paddy Landau said:**
> I run this command before I run my updates:
```
fwupdmgr --force refresh
```
It might help you. [FONT=courier new]fwupd[/FONT] is a system that supports automatic firmware updates using a centralised repository called LVFS (Linux Vendor Firmware Service). Most major vendors use it.

[Notes from]("https://blogs.gnome.org/hughsie/2022/04/28/fwupd-1-8-0-and-50-million-updates/") the dev.

I have to agree with maglin2 i have the same report and I can't for the life of me find the version you seem to have:
Mine:
```
&#9472;UEFI dbx:
&#9474;       Device ID:        <snip>
&#9474;       Summary:          UEFI revocation database
&#9474;       Current version:  217
&#9474;       Minimum Version:  217
&#9474;       Vendor:           UEFI:Linux Foundation
```
and current with:
```
Devices with the latest available firmware version:
 • UEFI dbx

```
I see secure boot is enabled on your end and most likely why you see this "WARNING: No updates to process, exiting in 10 seconds."
If you were to disable secure boot (**_and I know you won't_**) that message would disappear. (not meant in any sort of bad reference)

---

### Post by maglin2 on 2022-11-23
> **1fallen said:**
> I can't for the life of me find the version you seem to hav**_e_**

Perhaps Version 238 might be in -remote lvfs-testing (as opposed to Stable)? I have no intention of enabling it to find out though.

---

### Post by #&amp;thj^% on 2022-11-23
> **maglin2 said:**
> Perhaps Version 238 might be in -remote lvfs-testing (as opposed to Stable)?**_ I have no intention of enabling it to find out though._**
+1
I'm already pushing my skill-set with this beast I'm running currently.
```
cat /etc/os-release && inxi -SzCzGz -j
PRETTY_NAME=**"Rolling Rhino Remix"**
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04 (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
System:
  **Kernel: 6.0.8-060008-generic arch: x86_64 bits: 64 Desktop: Xfce v: 4.17.1**
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1584 min/max: 1400/3000 cores: 1: 1397 2: 1400 3: 1400
    4: 1400 5: 1397 6: 1400 7: 3000 8: 1400 9: 1400 10: 1673 11: 1750 12: 1400
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 515.65.01
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: amdgpu,nvidia
    unloaded: fbdev,modesetting,nouveau,vesa dri: radeonsi
    gpu: amdgpu,nvidia,nvidia-nvswitch resolution: 1: N/A 2: 1920x1080~120Hz
  API: OpenGL v: 4.6 Mesa 22.2.1 renderer: RENOIR (renoir LLVM 15.0.2 DRM
    3.48 6.0.8-060008-generic)
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile


```

---

### Post by Paddy Landau on 2022-11-24
> **maglin2 said:**
> Perhaps Version 238 might be in -remote lvfs-testing (as opposed to Stable)?
If that is the case, I wouldn't know how I ended up with it. I haven't at any stage knowingly enabled non-stable features.
> **1fallen said:**
> If you were to disable secure boot … that message would disappear.
Well, I tried. I disabled Secure Boot and restarted, but the message still remains. So, it's not that. (I re-enabled Secure Boot afterwards.) In any case, I rather suspect that this isn't to do with Secure Boot itself, because it's warning that there are no updates, not that there's a problem with Secure Boot. The question is, updates to what?

I ran two commands from one of the posts:
```
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```
and
```
$ inxi -SzCzGz -j
System:
  Kernel: 5.15.0-53-generic x86_64 bits: 64 Desktop: GNOME 42.5
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
CPU:
  Info: 8-core model: Intel Core i7-10700T bits: 64 type: MT MCP cache:
    L2: 2 MiB
  Speed (MHz): avg: 4388 min/max: 800/4500 cores: 1: 4386 2: 4405 3: 4388
    4: 4395 5: 4400 6: 4326 7: 4487 8: 4463 9: 4399 10: 4353 11: 4399 12: 4401
    13: 4341 14: 4355 15: 4212 16: 4512
Graphics:
  Device-1: Intel CometLake-S GT2 [UHD Graphics 630] driver: i915 v: kernel
  Device-2: Sunplus Innovation Integrated_Webcam_FHD type: USB
    driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CML GT2)
    v: 4.6 Mesa 22.0.5
Swap:
  ID-1: swap-1 type: partition size: 1.91 GiB used: 0 KiB (0.0%)
    dev: /dev/dm-2

```
I haven't the foggiest why you all have version 217 while I have version 238. Maybe different vendors release versions at different times? I'm with Dell; perhaps Dell released this version sooner? I'm guessing, because this is an area in which I have practically zero knowledge. I have been racking my brains as to how my system might be different, but I just don't know.

It's interesting that booting from my USB drive instead of the internal drive doesn't show this message. I ran [FONT=courier new]fwupdmgr get-devices[/FONT] from it, and unsurprisingly, it shows the same results — version 238.

---

### Post by maglin2 on 2022-11-24
Since version downgrades don't seem to be permitted with the UEFI dbx  that's apparently not an option to explore.
It does look like something might be setting a flag to tell the machine to boot to to firmware updater, which is then disappointed because it finds nothing to update. What and why is well outside my scant understanding.
Firmware updater hasn't somehow got promoted in BIOS boot order has it?

---

### Post by Paddy Landau on 2022-11-24
> **maglin2 said:**
> Firmware updater hasn't somehow got promoted in BIOS boot order has it?
The order in my BIOS, from top to bottom, is:

[LIST]
[*]ubuntu
[*]Onboard NIC(IPV4)
[*]Onboard NIC(IPV6)
[*]Linux Firmware Updater
[/LIST]
So, no, it's at the bottom.

This message started to show recently. I don't remember how recently exactly, as my memory isn't the best.

---

### Post by #&amp;thj^% on 2022-11-24
> **Paddy Landau said:**
> 
I haven't the foggiest why you all have version 217 while I have version 238. Maybe different vendors release versions at different times? I'm with Dell; perhaps Dell released this version sooner? I'm guessing, because this is an area in which I have practically zero knowledge. I have been racking my brains as to how my system might be different, but I just don't know.

It's interesting that booting from my USB drive instead of the internal drive doesn't show this message. I ran [FONT=courier new]fwupdmgr get-devices[/FONT] from it, and unsurprisingly, it shows the same results &#8212; version 238.
It pertains to UEFI, this has had my full attention since you posted your thread, I do believe this is to be a Vendor specifiable application, (Dell) but from the friends I'm associated with Dell machines 3 out of 6 show your same version "238" the other 3 show "217".
As a tester it is a real pain in the butt to enable secure boot as many times as I install, remove, and install others. (That should be understandable as my choice) 
I took a fresh install of a Arch based Distro and ran my firmware updates, It first showed 
```
"Plugin" : "uefi_dbx",
                               "VersionOld" : "77",
```
And after the update I ended still with 217
```
fwupdmgr report-history
Target:                  https://fwupd.org/lvfs/firmware/report
Payload:                 {
                           "ReportVersion" : 2,
                           "MachineId" : "d777639f452d1691d80bfebc9f1407cc57f3a65f6beedc200e3c4fdee646ed08",
                           "Metadata" : {
                             "DistroId" : "endeavouros"
                           },
                           "Reports" : [
                             {
                               "Checksum" : "174ef97cefdf50dc850a8b75abcae55ac50bb7ee",
                               "ReleaseId" : null,
                               "Protocol" : "org.uefi.dbx",
                               "UpdateState" : 2,
                               "Guid" : [
                                 "c6682ade-b5ec-57c4-b687-676351208742"
                               ],
                               "Plugin" : "uefi_dbx",
                               [B][COLOR="#FF0000"]"VersionOld" : "77",
                               "VersionNew" : "217",[/COLOR][/B]
                               "Flags" : 541065507,
                               "Created" : 1669329405,
                               "Modified" : 1669329864,
                               "Metadata" : {      }
                             }
                           ]
                         }
Proceed with upload? [Y|n]: 

```
The 10 seconds delays shows on waiting for Disks as well, So I'm sticking to my first guess UEFI looking for bad and new device signatures. And that is exactly what it should do.
Paddy I really like the fact you are so attentive to your system, and what it tells you.
My Old adage if it's not broke don't fix it. :)

---

### Post by Paddy Landau on 2022-11-25
> **1fallen said:**
> It pertains to UEFI, … I do believe this is to be a Vendor specifiable application, (Dell) but from the friends I'm associated with Dell machines 3 out of 6 show your same version "238" the other 3 show "217".
That's really interesting. I suspected this, and it seems that your experience supports the idea.
> **1fallen said:**
> ```
fwupdmgr report-history
```
When I run that command, all that it responds is:
```
No reports require uploading
```
> **1fallen said:**
> The 10 seconds delays shows on waiting for Disks as well, So I'm sticking to my first guess UEFI looking for bad and new device signatures. And that is exactly what it should do.
Again, interesting. Could it be to do with the fact that I installed Ubuntu with full-disk encryption (LUKS + LVM), because at the time of the message, the disk is still locked? Obviously, the EFI System Partition and [FONT=courier new]/boot[/FONT] aren't encrypted, but the rest of the disk is.

That might explain why booting from my USB disk doesn't give this message, because it's unencrypted.
> **1fallen said:**
> Paddy I really like the fact you are so attentive to your system, and what it tells you.
Thank you. I thought that most people did this!
> **1fallen said:**
> My Old adage if it's not broke don't fix it. :)
Wise words. I'll leave it thus unless advised otherwise.

---

### Post by #&amp;thj^% on 2022-11-25
> **Paddy Landau said:**
> 
When I run that command, all that it responds is:
```
No reports require uploading
```


This "**fwupdmgr report-history**" will only show right after firmware has been updated only.

> **Paddy Landau said:**
> Could it be to do with the fact that I installed Ubuntu with full-disk encryption (LUKS + LVM), because at the time of the message, the disk is still locked? Obviously, the EFI System Partition and [FONT=courier new]/boot[/FONT] aren't encrypted, but the rest of the disk is.

That might explain why booting from my USB disk doesn't give this message, because it's unencrypted.

After you now pointing to that difference I'm in favaor of this theory as well, :
```
fwupdmgr get-blocked-firmware
There are no blocked firmware files

```
```
&#9500;&#9472;System Firmware:
&#9474; &#9474;   Device ID:          a45df35ac0e948ee180fe216a5f703f32dda163f
&#9474; &#9474;   Summary:            UEFI ESRT device
&#9474; &#9474;   Current version:    1497841719
&#9474; &#9474;   Minimum Version:    1380122624
&#9474; &#9474;   Vendor:             LENOVO (DMI:LENOVO)
&#9474; &#9474;   **_Update State:       Success_**
&#9474; &#9474;   GUIDs:              be248459-caf2-4b09-af02-69b6a49974c1
&#9474; &#9474;                       230c8b18-8d9b-53ec-838b-6cfc0383493a &#8592; main-system-firmware
&#9474; &#9474;   Device Flags:       &#8226; Internal device
&#9474; &#9474;                       &#8226; Updatable
&#9474; &#9474;                       &#8226; System requires external power source
&#9474; &#9474;                       &#8226; Needs a reboot after installation
&#9474; &#9474;                       &#8226; Cryptographic hash verification is available
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update

```
> **Paddy Landau said:**
> Thank you. I thought that most people did this!

Not near enough do though, so i look at it like this "prevention is 99% of the cure" :)

---

### Post by Paddy Landau on 2022-11-26
Thank you, @1fallen.

I also get "There are no blocked firmware files".

But, on looking again at the firmware, I see that I have *two* "UEFI Device Firmware" entries listed.
```
$ fwupdmgr get-devices
OptiPlex 5480 AIO
<snip>
&#9500;&#9472;UEFI Device Firmware:
&#9474;     Device ID:          <snip>
&#9474;     Summary:            UEFI ESRT device
&#9474;     Current version:    240
&#9474;     Minimum Version:    240
&#9474;     Vendor:             DMI:Dell Inc.
&#9474;     Update State:       Success
&#9474;     GUID:               <snip>
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Needs a reboot after installation
&#9474;                         • Device is usable for the duration of the update
&#9474;   
&#9492;&#9472;UEFI Device Firmware:
      Device ID:          <snip>
      Summary:            UEFI ESRT device
      Current version:    355479849
      Minimum Version:    355479849
      Vendor:             DMI:Dell Inc.
      Update State:       Success
      GUID:               <snip>
      Device Flags:       • Internal device
                          • Updatable
                          • System requires external power source
                          • Needs a reboot after installation
                          • Device is usable for the duration of the update
```
What is the significance of that, do you know?

---

### Post by #&amp;thj^% on 2022-11-26
> **Paddy Landau said:**
> 
What is the significance of that, do you know?
That's a good question, and I don't want to guess and look a fool. (more than usual anyway :) )
I'll see if I can dig into that...and it just may be a expanded look at the UEFI firmware. (Guessing)

---

### Post by Paddy Landau on 2023-09-06
Update: This appears to be unrelated to Ubuntu. I found a [newer report]("https://github.com/fwupd/fwupd/issues/5938"), and I hope to get an answer there.

---

### Post by #&amp;thj^% on 2023-09-07
> **Paddy Landau said:**
> Update: This appears to be unrelated to Ubuntu. I found a [newer report]("https://github.com/fwupd/fwupd/issues/5938"), and I hope to get an answer there.

Nice of you to include the link, I've been curious on this one since you first posted.
On the sideline watching.

---

