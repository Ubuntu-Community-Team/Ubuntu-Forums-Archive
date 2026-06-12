---
title: "Screen periodically blanks for a couple of seconds with kernel 6.8.0"
date: 2024-08-14
forum: General Help
---

### Post by Paddy Landau on 2024-08-14
This is frustrating. First, kernel 6.5.0 [removed the ability]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248") to adjust the screen brightness ([my thread]("https://ubuntuforums.org/showthread.php?t=2494260")).

Now, kernel 6.8.0 blanks the screen for a second or two at apparently random times, anywhere between one second and several minutes between each blanking. It did so several times during the time it took for me to write this post!

I haven't been able to find a bug report for this, so I'm wondering if you know anything about it, and if you know of a way to diagnose and fix it, please?
```
$ [COLOR=#0000cd]lsb_release --all[/COLOR]
No LSB modules are available.
Distributor ID:    UbuntuDescription:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
```
```
$ [COLOR=#0000cd]uname --all[/COLOR]
Linux glinda 6.8.0-40-generic #40~22.04.3-Ubuntu SMP PREEMPT_DYNAMIC Tue Jul 30 17:30:19 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```
```
$ sudo lshw -numeric -C display
  *-display                 
       description: VGA compatible controller
       product: CometLake-S GT2 [UHD Graphics 630] [8086:9BC5]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:152 memory:c1000000-c1ffffff memory:d0000000-dfffffff ioport:3000(size=64) memory:c0000-dffff
```
Thank you

---

### Post by currentshaft on 2024-08-14
zx

---

### Post by Paddy Landau on 2024-08-14
> **currentshaft said:**
> Any errors in dmesg or journalctl output when this happens?
I can't see anything in journalctl, but each time it happens, this is what shows in dmesg:
```
[ 7912.265657] usb 1-9: USB disconnect, device number 17
[ 7912.456384] [UFW BLOCK] IN=wlo1 OUT= MAC=cc:d9:ac:5c:ae:40:08:2e:5f:f1:00:63:86:dd SRC=fe80:0000:0000:0000:0a2e:5fff:fef1:0063 DST=fe80:0000:0000:0000:c68a:3c94:7f1b:cbfa LEN=2330 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=3702 DPT=43887 LEN=2290 
[ 7913.557402] usb 1-9: new full-speed USB device number 18 using xhci_hcd
[ 7913.685271] usb 1-9: New USB device found, idVendor=1fd2, idProduct=8105, bcdDevice= 1.00
[ 7913.685275] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7913.685277] usb 1-9: Product: LGDisplay Incell Touch
[ 7913.685278] usb 1-9: Manufacturer: Melfas
[ 7913.690820] input: Melfas LGDisplay Incell Touch as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:1FD2:8105.001F/input/input45
[ 7913.691112] hid-multitouch 0003:1FD2:8105.001F: input,hidraw2: USB HID v1.11 Device [Melfas LGDisplay Incell Touch] on usb-0000:00:14.0-9/input0
[ 7913.691960] hid-generic 0003:1FD2:8105.0020: hiddev1,hidraw3: USB HID v1.11 Device [Melfas LGDisplay Incell Touch] on usb-0000:00:14.0-9/input1
```
Each time, the USB device number (lines 1 and 3) increments by 1, and there are varying numbers of UFW_BLOCK (sometimes just one, sometimes more).

---

### Post by #&amp;thj^% on 2024-08-14
Hi Paddy, have you tried this yet
```
xset -dpms
```
I didn't like kernel 6.8.0  too many oddities, YMMV

---

### Post by Paddy Landau on 2024-08-14
> **1fallen said:**
> Hi Paddy, have you tried this yet
```
xset -dpms
```
I've just run it. I'll report back when either sufficient time has passed to feel confident that it has worked, or the problem recurs.

Do I have to run this each time I reboot, or is it set permanently until I change it back?
> **1fallen said:**
> I didn't like kernel 6.8.0  too many oddities, YMMV
It was part of the standard updates for 22.04 with Pro enabled.

---

### Post by Paddy Landau on 2024-08-14
Unfortunately, [FONT=courier new]xset -dpms[/FONT] hasn't worked :(

---

### Post by currentshaft on 2024-08-14
@

---

### Post by #&amp;thj^% on 2024-08-14
> **Paddy Landau said:**
> 

It was part of the standard updates for 22.04 with Pro enabled.

I know :)
I quickly jumped to kernel 6.10, and you know I'm not suggesting that you do though.
I'm not sure a bug report would matter at this point: [https://duckduckgo.com/?q=+Screen+periodically+blanks+for+a+couple+of+seconds+with+kernel+6.8.0+&t=newext&atb=v358-1&ia=web](https://duckduckgo.com/?q=+Screen+periodically+blanks+for+a+couple+of+seconds+with+kernel+6.8.0+&t=newext&atb=v358-1&ia=web)
If I understand the buzz lately (and it is just hearsay currently) they are thinking 6.9 will land in jammy at a later time. For now we battle on. :)

Thanks for trying xset though, and I hope it was used in a X-Session and not wayland.

---

### Post by Paddy Landau on 2024-08-14
> **currentshaft said:**
> The UFW line is benign (a device on your local network is doing service discovery).
Thank you.
> **currentshaft said:**
> This is a laptop screen, right? Are there any available firmware updates with "fwupdmgr install"?
No, this is a desktop, OptiPlex 5480 AIO All-In-One. It has a touchscreen.

There are no pending fwupdmgr updates. I have had several since I first purchased the machine. The last update was five days ago:
```
$ fwupdmgr get-history
OptiPlex 5480 AIO
&#9474;
&#9492;&#9472;System Firmware:
  &#9474;   Device ID:          a45df35ac0e948ee180fe216a5f703f32dda163f
  &#9474;   Previous version:   1.32.0
  &#9474;   Update State:       Success
  &#9474;   Last modified:      2024-08-09 13:32
  &#9474;   GUID:               f5d534f4-f4c3-4821-a863-285d9dd3e013
  &#9474;   Device Flags:       • Internal device
  &#9474;                       • Updatable
  &#9474;                       • System requires external power source
  &#9474;                       • Supported on remote server
  &#9474;                       • Needs a reboot after installation
  &#9474;                       • Reported to remote server
  &#9474;                       • Cryptographic hash verification is available
  &#9474;                       • Device is usable for the duration of the update
  &#9474; 
  &#9492;&#9472;OptiPlex 5480 AIO:
        New version:      1.33.0
        Remote ID:        lvfs
        Release ID:       95125
        Summary:          Firmware for the Dell OptiPlex 5480 AIO
        License:          Proprietary
        Size:             23.7 MB
        Created:          2024-07-04
        Urgency:          Critical
        Vendor:           Dell
        Description:      
        Dell Technologies highly recommends applying this important update as soon as possible. The update contains critical bug fixes and changes to improve functionality, reliability, and stability of your Dell system. It may include security fixes and other feature enhancements.
```

---

### Post by Paddy Landau on 2024-08-14
> **1fallen said:**
> I quickly jumped to kernel 6.10, and you know I'm not suggesting that you do though.
Well, I could try! I don't know how to install it on 22.04, though.
> **1fallen said:**
> I'm not sure a bug report would matter at this point: [https://duckduckgo.com/?q=+Screen+periodically+blanks+for+a+couple+of+seconds+with+kernel+6.8.0+&t=newext&atb=v358-1&ia=web](https://duckduckgo.com/?q=+Screen+periodically+blanks+for+a+couple+of+seconds+with+kernel+6.8.0+&t=newext&atb=v358-1&ia=web)
None of those seems to relate to my problem.
> **1fallen said:**
> If I understand the buzz lately (and it is just hearsay currently) they are thinking 6.9 will land in jammy at a later time. For now we battle on. :)

Thanks for trying xset though, and I hope it was used in a X-Session and not wayland.
Yes, X11. Wayland isn't ready for me yet — it can't do what I need it to do.

---

### Post by #&amp;thj^% on 2024-08-14
> **Paddy Landau said:**
> Well, I could try! I don't know how to install it on 22.04, though.

Nope I wouldn't, I know how you run your systems, and this would just turn into a royal pain in the derrière...lol
If your serious I can help, but think logically, and not with your feelings. ;)
> **Paddy Landau said:**
> 
None of those seems to relate to my problem.
Oh thats just a taste of the bugs filed against it.
> **Paddy Landau said:**
> 
Yes, X11. Wayland isn't ready for me yet &#8212; it can't do what I need it to do.
No disagreement here....:)

---

### Post by #&amp;thj^% on 2024-08-14
Well I also call you an experienced buntu user, so have a look.

You need to go here: [https://kernel.ubuntu.com/mainline/v6.10.5/](https://kernel.ubuntu.com/mainline/v6.10.5/)
Download all in the red square (Screenshot), make a folder named "kernels" or what you want to call it, place all the downloaded kernels there in that new folder.

Now CD to that location ie:
```
cd /Downloads/kernels
```

Now install them in one shot:
```
sudo dpkg -i *.deb
```

with this method you can easily remove them when finished testing.

---

### Post by Paddy Landau on 2024-08-14
> **1fallen said:**
> You need to go here…
Thank you. Unfortunately, it has errors with unmet dependencies.
```
**dpkg:** dependency problems prevent configuration of linux-headers-6.10.5-061005-generic:
 linux-headers-6.10.5-061005-generic depends on libc6 (>= 2.38); however:
  Version of libc6:amd64 on system is 2.35-0ubuntu3.8.
 linux-headers-6.10.5-061005-generic depends on libelf1t64 (>= 0.144); however:
  Package libelf1t64 is not installed.
 linux-headers-6.10.5-061005-generic depends on libssl3t64 (>= 3.0.0); however:
  Package libssl3t64 is not installed.
```
Those packages aren't available on 22.04.

Oh well. I have uninstalled the 6.10 kernel for now.

---

### Post by argguy on 2024-08-23
Hi, I was facing the same problem and solved it by disabling the touchscreen in the BIOS. When a patch is released might re-enable it, never use it anyway.

---

### Post by Paddy Landau on 2024-08-23
> **argguy said:**
> Hi, I was facing the same problem and solved it by disabling the touchscreen in the BIOS. When a patch is released might re-enable it, never use it anyway.
Thank you. When I saw your answer, I first tried disabling the touchscreen in the software (using xinput), because I do occasionally like to use the touchscreen, but unfortunately that didn't work.

I've disabled it in the BIOS now, and so far it's holding. We'll see what happens. I haven't yet had time to test kernel 6.10.

Are you also using Dell, or do you have a different device?

---

### Post by Paddy Landau on 2024-08-23
Ugh. Disabling the touchscreen in the BIOS hasn't helped. :(

---

### Post by suto-norbert on 2024-08-26
Exact same problem! I use Zorin OS, (based on Ubuntu 22.04) and these issue happen latest kernel update (6.5 to 6.8)

My device a HP Elitebook 840 G3. I use it with a Dell External monitor, with Displayport output.

---

### Post by suto-norbert on 2024-08-26
> **Paddy Landau said:**
> Thank you. Unfortunately, it has errors with unmet dependencies.
```
**dpkg:** dependency problems prevent configuration of linux-headers-6.10.5-061005-generic:
 linux-headers-6.10.5-061005-generic depends on libc6 (>= 2.38); however:
  Version of libc6:amd64 on system is 2.35-0ubuntu3.8.
 linux-headers-6.10.5-061005-generic depends on libelf1t64 (>= 0.144); however:
  Package libelf1t64 is not installed.
 linux-headers-6.10.5-061005-generic depends on libssl3t64 (>= 3.0.0); however:
  Package libssl3t64 is not installed.
```
Those packages aren't available on 22.04.

Oh well. I have uninstalled the 6.10 kernel for now.


If you have a experimenter, you able to try these kernel: [https://github.com/zabbly/linux](https://github.com/zabbly/linux)

It make a ex-canonical employee. He made a lot of kernel version to 22.04 ubuntu. for example 6.6 or 6.10. One thing, if you use these type of kernel, you need to disable secure boot! (if you dont do these before :) )

more info: [https://stgraber.org/2023/08/24/stable-linux-mainline-builds/](https://stgraber.org/2023/08/24/stable-linux-mainline-builds/)

> So I started taking the latest stable bugfix release of the mainline kernel, generate a configuration that&#8217;s very close to an Ubuntu generic kernel, cherry-pick a few small changes that aren&#8217;t upstream yet and then build that and push it to my machines.

---

### Post by Paddy Landau on 2024-08-26
> **suto-norbert said:**
> If you have a experimenter, you able to try these kernel: [https://github.com/zabbly/linux](https://github.com/zabbly/linux)
Thank you. I've installed these (it's a pity that I have to disable Secure Boot). I'll report back tomorrow whether or not it works.

---

### Post by suto-norbert on 2024-08-26
> **Paddy Landau said:**
> Thank you. I've installed these (it's a pity that I have to disable Secure Boot). I'll report back tomorrow whether or not it works.

Try these:

[https://github.com/berglh/ubuntu-sb-kernel-signing](https://github.com/berglh/ubuntu-sb-kernel-signing)

---

### Post by Paddy Landau on 2024-08-27
> **suto-norbert said:**
> Try these:

[https://github.com/berglh/ubuntu-sb-kernel-signing](https://github.com/berglh/ubuntu-sb-kernel-signing)
Thank you for that. I've been looking through the instructions. Please forgive my obvious ignorance here; I'm not entirely sure that I've correctly understood them.

Here is the process that I believe I should follow. Please let me know what needs to change.

[LIST=1]
[*]Download the entire folder from [this sbin]("https://github.com/berglh/ubuntu-sb-kernel-signing/tree/main/sbin") into a new folder somewhere in my home.
[*]Make the .sh files executable.
[*]Run mok-setup.sh as sudo, answering the prompts.
[*]Follow the instructions for [manual signing]("https://github.com/berglh/ubuntu-sb-kernel-signing?tab=readme-ov-file#manually-signing-a-kernel").
[/LIST]
I'm testing this in a VM before running it live. My live machine is 22.04, but the VM is 24.04.

At step 3, I get an error: mok-setup.sh complains that I don't have fwts installed. But, when I try to install it, it fails. Here's the full text:
```
$ sudo apt install fwtsReading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-6.8.0-40 linux-headers-6.8.0-40-generic linux-image-6.8.0-40-generic linux-modules-6.8.0-40-generic linux-modules-extra-6.8.0-40-generic linux-tools-6.8.0-40 linux-tools-6.8.0-40-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  fwts-efi-runtime-dkms libfdt1 libfwts1 libfwtsacpica1 libfwtsiasl1
The following NEW packages will be installed:
  fwts fwts-efi-runtime-dkms libfdt1 libfwts1 libfwtsacpica1 libfwtsiasl1
0 upgraded, 6 newly installed, 0 to remove and 9 not upgraded.
Need to get 1,250 kB of archives.
After this operation, 3,887 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 libfwtsiasl1 amd64 24.01.00-0ubuntu4 [393 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 libfwtsacpica1 amd64 24.01.00-0ubuntu4 [304 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu noble/main amd64 libfdt1 amd64 1.7.0-2build1 [20.1 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 libfwts1 amd64 24.01.00-0ubuntu4 [130 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 fwts-efi-runtime-dkms amd64 24.01.00-0ubuntu4 [24.2 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 fwts amd64 24.01.00-0ubuntu4 [378 kB]
Fetched 1,250 kB in 4s (316 kB/s)
Selecting previously unselected package libfwtsiasl1.
(Reading database ... 222143 files and directories currently installed.)
Preparing to unpack .../0-libfwtsiasl1_24.01.00-0ubuntu4_amd64.deb ...
Unpacking libfwtsiasl1 (24.01.00-0ubuntu4) ...
Selecting previously unselected package libfwtsacpica1.
Preparing to unpack .../1-libfwtsacpica1_24.01.00-0ubuntu4_amd64.deb ...
Unpacking libfwtsacpica1 (24.01.00-0ubuntu4) ...
Selecting previously unselected package libfdt1:amd64.
Preparing to unpack .../2-libfdt1_1.7.0-2build1_amd64.deb ...
Unpacking libfdt1:amd64 (1.7.0-2build1) ...
Selecting previously unselected package libfwts1.
Preparing to unpack .../3-libfwts1_24.01.00-0ubuntu4_amd64.deb ...
Unpacking libfwts1 (24.01.00-0ubuntu4) ...
Selecting previously unselected package fwts-efi-runtime-dkms.
Preparing to unpack .../4-fwts-efi-runtime-dkms_24.01.00-0ubuntu4_amd64.deb ...
Unpacking fwts-efi-runtime-dkms (24.01.00-0ubuntu4) ...
Selecting previously unselected package fwts.
Preparing to unpack .../5-fwts_24.01.00-0ubuntu4_amd64.deb ...
Unpacking fwts (24.01.00-0ubuntu4) ...
Setting up libfwtsiasl1 (24.01.00-0ubuntu4) ...
Setting up libfwtsacpica1 (24.01.00-0ubuntu4) ...
Setting up libfdt1:amd64 (1.7.0-2build1) ...
Setting up fwts-efi-runtime-dkms (24.01.00-0ubuntu4) ...
Loading new fwts-efi-runtime-dkms-24.01.00 DKMS files...
Error! No write access to DKMS tree at /var/lib/dkms
dpkg: error processing package fwts-efi-runtime-dkms (--configure):
 installed fwts-efi-runtime-dkms package post-installation script subprocess returned error exit status 1
Setting up libfwts1 (24.01.00-0ubuntu4) ...
**dpkg:** dependency problems prevent configuration of fwts:
 fwts depends on fwts-efi-runtime-dkms (= 24.01.00-0ubuntu4); however:
  Package fwts-efi-runtime-dkms is not configured yet.


**dpkg:** error processing package fwts (--configure):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.12.0-4build2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for libc-bin (2.39-0ubuntu8.3) ...
Errors were encountered while processing:
 fwts-efi-runtime-dkms
 fwts
[COLOR=#FF0000]**E:**[/COLOR] Sub-process /usr/bin/dpkg returned an error code (1)
```
Do you know how I can fix this, please?

---

### Post by Paddy Landau on 2024-08-27
> **suto-norbert said:**
> If you have a experimenter, you able to try these kernel: [https://github.com/zabbly/linux](https://github.com/zabbly/linux)
I have good news!

This kernel fixes the blanking problem.

It also fixes a [probably-related problem]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248"), where the brightness controls are broken ([forum thread]("https://ubuntuforums.org/showthread.php?t=2494260")).

Thank you so much for pointing this out to me.

---

### Post by suto-norbert on 2024-08-27
Well, i try it Zorin 17.1 (based on ubuntu 22.04) and work well.

First i run mok-setup.sh (it warning that need to install fwts, but i able to install it without any problem with "apt install fwts") 

After i configure the auto sign with "Automated signing of all installed kernels" and lastly i run the manual sign with already install 6.10 zabbly kernel:

```
sudo sbsign --key "/var/lib/shim-signed/mok/MOK-Kernel.priv" --cert "/var/lib/shim-signed/mok/MOK-Kernel.pem" --output "/boot/vmlinuz-6.10.6-zabbly+" "/boot/vmlinuz-6.10.6-zabbly+"
```

I found a topic that somebody say that need to create a "/var/lib/dkms" folder if it not exist... please try to check, that folder are exist or not.

---

### Post by Paddy Landau on 2024-08-28
> **suto-norbert said:**
> need to create a "/var/lib/dkms" folder if it not exist... please try to check, that folder are exist or not.
Thank you. The folder does exist.

I did use "apt install fwts", and that's what gave the error. I'll have to see if there's another way for me to do it.

---

### Post by Paddy Landau on 2024-08-28
I have reported this [bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.8/+bug/2078054").

If it affects you, please **vote for it** (log in and select the green writing at the top left).

---

### Post by Paddy Landau on 2024-08-28
> **suto-norbert said:**
> i able to install it without any problem with "apt install fwts")
If I ignore the errors, and make a small modification to mok-setup.sh, then it works in the VM for 24.04.

On 22.04, it had no errors, and it's working now.

 Thank you for your advice.

---

### Post by suto-norbert on 2024-08-28
Glad to hear :)

I also vote the bug, i hope it will fixed soon.

---

### Post by Paddy Landau on 2024-08-29
> **suto-norbert said:**
> I also vote the bug, i hope it will fixed soon.
So do I, but knowing Canonical, I won't hold my breath.

---

### Post by Paddy Landau on 2024-08-30
Aargh! The solution from Zabbly no longer works after the latest update :(

---

