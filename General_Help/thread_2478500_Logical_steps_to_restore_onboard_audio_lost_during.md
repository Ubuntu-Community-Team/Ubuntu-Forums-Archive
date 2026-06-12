---
title: "Logical steps to restore onboard audio lost during LTS upgrade?"
date: 2022-08-28
forum: General Help
---

### Post by ozark_hillbilly on 2022-08-28
Hello,

Is there a logical series of steps to take in determining why the onboard audio 
no longer works after upgrading to the latest LTS version? I went from 20.04 to 22.04 LTS.
I am hoping something was modified that I can correct in Terminal mode.
Note: 
sudo apt-get install --reinstall alsa-base pulseaudio
sudo alsa force-reload 
had no impact on problem. 

kernel info;
ed@ed-G41MT-S2PT:/$ uname -a
Linux ed-G41MT-S2PT 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


From the Desktop Settings:

Under Settings > Sound

Input
Input Device
---------------------------------- [dashed line]


Configuration line is blank (no options)

*********************************************

Not sure alsa-base.conf is the problem area so I 
included it here:

etc/modprobe.d/alsa-base.conf:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

******************************************************

ed@ed-G41MT-S2PT:/$ sudo lspci
[sudo] password for ed: 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)

---

### Post by &amp;KyT$0P# on 2022-08-28
> **ozark_hillbilly said:**
> kernel info;
ed@ed-G41MT-S2PT:/$ uname -a
Linux ed-G41MT-S2PT 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

That's an unusual kernel version for 22.04.  You should have at least 5.15.something

Are you able to boot into a 5.15.x kernel at the GRUB menu?

---

### Post by ozark_hillbilly on 2022-09-02
halogen2,

I do not know how to boot up on specific kernel versions at the Grub menu but I am going to research how.
Does it matter which 5.15.x I go with?
And if I find it corrects my audio issues what is the process to permanently assign a new kernal to your OS?

---

### Post by &amp;KyT$0P# on 2022-09-02
> **ozark_hillbilly said:**
> Does it matter which 5.15.x I go with?

For simplicity and security I would suggest just going with the latest stock Ubuntu 5.15 kernel (5.15.0-47-generic at time of writing), unless you have a specific reason otherwise.

You should be able to install it by installing the package [FONT=Courier New]linux-generic[/FONT] .  But since you didn't get the newer kernel during your upgrade to 22.04, maybe first check the output of
```
apt-cache policy linux-generic
```

> And if I find it corrects my audio issues what is the process to permanently assign a new kernal to your OS?

By default it will default to booting the highest installed kernel version.  If you're asking this question, most likely you didn't alter this setup.  So if the installation of 5.15 kernel succeeds, this assignment should happen automatically while installing 5.15 kernel.

---

### Post by ozark_hillbilly on 2022-09-11
halogen2,

here is output:

```

ed@ed-G41MT-S2PT:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 5.15.0.46.46
  Candidate: 5.15.0.47.47
  Version table:
     5.15.0.47.47 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
 *** 5.15.0.46.46 100
        100 /var/lib/dpkg/status
     5.15.0.25.27 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
ed@ed-G41MT-S2PT:~$ 

```

I will attempt to install linux-generic next.

edit - I had to restart upon returning to my computer as it went it into shutdown mode after I left it while it was
 installing the "linux-generic" package. Upon reboot I selected Advanced Ubuntu options during startup. 
All the listed kernels to choose from were the older 5.13.xx.xx versions. Not sure why. ???

Attached is screenshot of updated /newly installed kernel according to synaptic package manager.
Not sure why this new verson is not listing under Advanced Ubuntu options on bootup.

---

### Post by &amp;KyT$0P# on 2022-09-11
What is output of
```
dpkg-query -l | grep -i -P 'linux.*5.15.0-47'
```

For reference, this is what it looks like on my system and what it should look like -
```
$ dpkg-query -l | grep -i -P 'linux.*5.15.0-47'
ii  linux-headers-5.15.0-47                       5.15.0-47.51                                                          all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-47-generic               5.15.0-47.51                                                          amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-image-5.15.0-47-generic                 5.15.0-47.51                                                          amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                          5.15.0-47.51                                                          amd64        Linux Kernel Headers for development
ii  linux-modules-5.15.0-47-generic               5.15.0-47.51                                                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-47-generic         5.15.0-47.51                                                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP

```

---

### Post by ozark_hillbilly on 2022-09-11
here ya go:

```

ed@ed-G41MT-S2PT:~$ dpkg-query -l | grep -i -P 'linux.*5.15.0-47'
ii  linux-headers-5.15.0-47                       5.15.0-47.51                            all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-47-generic               5.15.0-47.51                            amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-image-5.15.0-47-generic                 5.15.0-47.51                            amd64        Signed kernel image generic
ii  linux-modules-5.15.0-47-generic               5.15.0-47.51                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-47-generic         5.15.0-47.51                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ed@ed-G41MT-S2PT:~$ 

```

But this is not appearing under Advanced Ubuntu options during bootup sequence...???

Looks like yours except for the Libc-dev line....

---

### Post by &amp;KyT$0P# on 2022-09-11
Please post the output from running this command in Terminal -
```
sudo update-grub
```

Are you dual booting another Linux distro on this computer?

---

### Post by ozark_hillbilly on 2022-09-11
```

ed@ed-G41MT-S2PT:~$ sudo update-grub
[sudo] password for ed: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-47-generic
Found initrd image: /boot/initrd.img-5.15.0-47-generic
Found linux image: /boot/vmlinuz-5.15.0-46-generic
Found initrd image: /boot/initrd.img-5.15.0-46-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
done
ed@ed-G41MT-S2PT:~$ 

```

No sir, I am not dual booting with any other OS.

---

### Post by &amp;KyT$0P# on 2022-09-11
As far as I can tell, that worked and if you reboot, your GRUB should boot by default into 5.15.0-47-generic kernel **and** have an entry for that kernel under "Advanced options for Ubuntu".  If it still doesn't, and if your Ubuntu is installed in EFI mode, maybe check the EFI boot order? -
```
efibootmgr -v
```

---

### Post by ozark_hillbilly on 2022-09-11
Evidently I am not set up for EFI:

```

ed@ed-G41MT-S2PT:~$ sudo apt install efibootmgr
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  efibootmgr
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 29.8 kB of archives.
After this operation, 93.2 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 efibootmgr amd64 17-1ubuntu2 [29.8 kB]
Fetched 29.8 kB in 2s (12.4 kB/s)   
Selecting previously unselected package efibootmgr.
(Reading database ... 214696 files and directories currently installed.)
Preparing to unpack .../efibootmgr_17-1ubuntu2_amd64.deb ...
Unpacking efibootmgr (17-1ubuntu2) ...
Setting up efibootmgr (17-1ubuntu2) ...
Processing triggers for man-db (2.10.2-1) ...
ed@ed-G41MT-S2PT:~$ efibootmgr -v
EFI variables are not supported on this system.
ed@ed-G41MT-S2PT:~$ 

```

I will try to reboot and see if 5.15 is an option....
After latest reboot I went to Advanced Options and the kernel options remain unchanged.
5.13.0-28 generic is latest one.
Crud, I was hoping to get over this hump. We know 5.15 is supposedly installed but the boot sequence
is not seeing the change. ....arghhhhh.... :(

edit - I ran the needrestart -kr l command and the screenshot is attached.

---

### Post by &amp;KyT$0P# on 2022-09-11
Apparently the GRUB instance your computer is booting is not the one controlled by your Ubuntu 22.04.  Sorry I have no idea how this could even happen in a single-boot system and I don't know how to troubleshoot this further on a BIOS system :(

---

### Post by ozark_hillbilly on 2022-09-11
Would updating the GRUB boot loader under the Recovery Menu have any effect?
I get this message:
"Continuing will remount your /filesystem in read/write mode and mount any other file system
 defined in etc/fstab. Continue Yes  No?"

I was unsure and aborted that action. Is it okay/safe to update the boot loader?

I also ran the steps from here to install kernel 5.15.47:

[https://www.how2shout.com/linux/how-to-change-default-kernel-in-ubuntu-22-04-20-04-lts/](https://www.how2shout.com/linux/how-to-change-default-kernel-in-ubuntu-22-04-20-04-lts/)

Everything went off w/o a hiccup. But still no change.

---

### Post by &amp;KyT$0P# on 2022-09-12
> **ozark_hillbilly said:**
> I also ran the steps from here to install kernel 5.15.47:

The instructions on that site are dangerous to production systems in most cases, and they don't warn you about the dangers.  I would recommend reversing whatever you did before you fix the real underlying problem.

> Everything went off w/o a hiccup. But still no change.

Since your Ubuntu 22.04 is not in control of GRUB, installing kernels **will not help** at this point.  The kernel to try is already installed and installed correctly.  This is a GRUB problem.

---

