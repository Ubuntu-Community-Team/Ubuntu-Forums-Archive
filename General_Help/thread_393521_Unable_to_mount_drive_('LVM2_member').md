---
title: "Unable to mount drive ('LVM2_member')"
date: 2007-03-25
forum: General Help
---

### Post by mattyp1 on 2007-03-25
I accidently killed kubuntu edgy trying to upgrade to feisty beta. I have installed ubuntu edgy on a separate drive in hopes of getting at my data and I cannot mount my main partition. This means over 15 years of data (pictures, videos, music, etc...) is all inaccesible and I fear it's lost. Please help!
Here are some details:

Gparted tells me my drive (/dev/sda6) has an unknown filesystem and an LVM flag. It also provides warnings stating it is unable to detect filesystem. I believe the filesystem was JFS or XFS so 

I tried adding to fstab:

**/dev/sda6 /home/multimedia jfs user,rw,owner 0 2**

This resulted in:
[B]
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

dmesg| tail results in :

[B][17179784.480000] NET: Registered protocol family 31
[17179784.480000] Bluetooth: HCI device and connection manager initialized
[17179784.480000] Bluetooth: HCI socket layer initialized
[17179784.504000] Bluetooth: L2CAP ver 2.8
[17179784.504000] Bluetooth: L2CAP socket layer initialized
[17180781.528000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180781.612000] ISO 9660 Extensions: RRIP_1991A
[17180787.076000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17180787.076000] md: bitmap version 4.39
[17181107.560000] JFS: nTxBlock = 8192, nTxLock = 65536[/B]

I have also tried  sudo mount -t auto /dev/sda6 /home/multimedia
but receive this:

**mount: unknown filesystem type 'LVM2_member'**

Any assistance would be greatly appreciated. i have seen some similar posts but they all seem to pertain to ntfs partitions.

---

### Post by kefkakiller on 2007-03-27
I am experiencing similar symptoms, so hopefully some guru can help us both.

My setup consists of three 250MB drives in a single logical volume with a JFS filesystem. 

lvscan, pvscan, and vgscan all show everything in my setup. 
lvdisplay shows the LV status as available. The only thing that might be fishy is that it shows the # open as zero, or is that because it isn't mounted. Pvdisplay and vgdisplay both look correct (well, vgdisplay also shows open LVs as zero).

I found this link ([http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)) to be very helpful, but I just don't know enough about lvm to really know what the problem is. Hopefully someone can help.

---

### Post by mattyp1 on 2007-03-29
Well I figured it out, thanks to SuSE 10.2. It looks like the LVM was automatically named (by Ubuntu) /dev/Ubuntu and I was trying to mount the physical drive /dev/sda6. SuSE auto-detected and all I had to do was set a mount point upon SuSE install. Once my backup finishes I am going to install Ubuntu (my preferred OS) and try to prove the theory out.

Phew - that was close, I'll be getting a network storage device soon ;)

kefkakiller - I wish I could help you out... You can try installing SuSE 10.2 ([http://en.opensuse.org/Released_Version](http://en.opensuse.org/Released_Version)) to see if you can access it there, remember you will have to define the mount point and make sure you custom partition so you don't delete anything. There are pros and cons to each OS. IMHO, Ubuntu is better because of the repositories and package manager. SuSE looks a little cleaner and seems to auto-detect well, plus it has YaST. Regardless, I only used SuSE to debug and will switch back when my backup is complete.

Hope this helps you out, if I think of or stumble across anything I will let you know.

Good luck!

---

### Post by kefkakiller on 2007-03-29
I figured it out. 

The problem started when I did a hard reboot, it's a headless machine and I was having network connectivity issues so I couldn't ssh into it and I'm too lazy to hook up a monitor and keyboard.

Well apparently JFS doesn't like hard reboots, but a simple fsck fixed the problem and I was able to mount it fine after running that.

I'm glad to hear your problems sorted themselves out as well.

---

