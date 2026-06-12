---
title: "A series of escalating issues"
date: 2017-03-07
forum: General Help
---

### Post by howlingkestrel on 2017-03-07
I'm posting this on the general forum because it covers a variety of issues and I'm not sure where it really belongs.  For the last couple of months I've been using Ubuntu mate on a desktop PC and up until a couple of weeks ago it worked fine. However, I then installed a new graphics card, which caused some issues temporarily whilst I was installing new drivers, though it eventually worked fine. However, since then, I've had a series of problems which have escalated to the point that I can no longer get my PC to work properly.

Initially, it would occasionally crash, and booting normally would feed into a black screen, from which I would be unable to access anything. I would have to boot from recovery, which would take a while, but would eventually give a normal session at the end of it. I once had to reinstall the graphics drivers, but it otherwise worked fine. 

Yesterday, however, the power cut out whilst the computer was running when I tripped over the lead, and now the computer is behaving strangely. At first, it would only boot into a low resolution, and it seemed like I needed to reinstall the graphics drivers, as other programmes that relied on things like glx wouldn't work. As such, I tried to reinstall the drivers through the method I had previously used through a virtual console, as the NVIDIA drivers require the X server to not be running. However, when I used sudo service lightdm stop as I had in the past, this resulted in all of the virtual consoles giving no video output, whilst the X server session on f7 worked as normal. I found this really weird, so I decided to try to reinstall the OS.

When I tried to reinstall from a USB, it fed me into a black screen unless I used the nomodeset option. Doing so allowed me to run the installer, which worked without problems, until it came to reboot. Instead of rebooting immediately, it would sit on a screen that said Ubuntu Mate whilst an empty console ran in the background. Eventually the computer rebooted, but now has a resolution of 640x480, which is the only option in the displays menu. It's also set to a 73Hz refresh rate. I thought the graphics card might have been fried, but the HDMI cable giving the current output is still plugged into the card.

The main issue now is that the installation didn't automatically install wireless drivers, even though the installation session had access to wireless internet. This means that I can't currently install anything, and my accommodation gives me no access to a wired connexion. I thought I would be able to take the necessary drivers from my laptop with a USB, which lead me to discover my next issue. 

When trying to connect a USB device with a FAT partition to the computer, it fails to mount, saying that the mount process:
               > exited with non-zero exit status 32: mount:wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error 
Using information I found online, I tried to mount by running 
               >  sudo mount -t vfat /media/MyUSB
Which instead gave the error that this could not be found in fstab. As such I created a location in fstab for it as
                > UUID=AB63-4777   /media/MyUSB   vfat   defaults   0    0
After doing so, trying to mount through terminal gives the error
                wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error

I can't find anything else I can try online, so I was wondering if anyone could give me a bit of help on this? Just about anything would be greatly appreciated.

Here are the outputs of lspci    > 00:0.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)

 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
 00:02.0 Display Controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
 00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
 00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
 00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2(rev 04)
 00:1.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
 00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 1 (rev c4)
 00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 4 (rev c4)
 00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 5 (rev c4)
 00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 6 (rev c4)
 00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 7 (rev c4)
 00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI express Root Port 8 (rev c4)
 00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1(rev 04)
 00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
 00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
 01:00.0 VGA compatible controller: NVIDIA Corporation GP107 (rev a1)
 01:00.1 Audio device: NVIDIA Corporation Device 0fb9 (rev a1)
 03:00.0 SATA controller: ASMedia Technology Ince. ASM1062 Serial ATA Controller (rev 01)
 04:00.0 Ethernet controller: Broadcom Limited NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
 05:00.0 PCI bridge: ADMedia Technology Inc. ASM1083 PCIe to PCI Bridge (rev 03)
 07:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
 08:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

and the dmesg | tail    > [ 1840.105316] audit: type=1400 audit(1488937058.693:157): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0

 [ 1840.769084] FAT-fs (sdc1): IO charset iso8859-1 not found
 [ 1845.105284] audit: type=1400 audit( 1488937063.693:158): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1846.105240] audit: type=1400 audit( 1488937064.693:159): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1848.105235] audit: type=1400 audit( 1488937066.693:160): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1850.105220] audit: type=1400 audit( 1488937058.693:161): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1903.570343] FAT-fs (sdc1): IO charset iso8859-1 not found
 [ 1907.104944] audit: type=1400 audit( 1488937125.693:162): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1912.104902] audit: type=1400 audit( 1488937130.693:163): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 [ 1912.107090] audit: type=1400 audit( 1488937130.693:164): apparmor=”DENIED” operation=”connect” profile=”/usr/sbin/ntpd” name=”/run/dbus/system_bus_socket” pid=1357 comm=”ntpd” requested_mask=”wr” denied_mask=”wr” fsuid=110 ouid=0
 
 
from trying to mount, in case these might give some insight into what's happened.

---

### Post by QIII on 2017-03-07
Hello!

It is best to post one clearly defined subject per thread.  Laundry-list posts become confusing quickly as people stumble over each other trying to answer different things.

What one item would you like help with in this thread?  

For other items, start new threads.

---

### Post by Bucky Ball on 2017-03-07
Welcome. What QIII said. Also, for future reference, you're heading in the right direction, but whatever tags you have around the terminal output, replace them with ```
 tags instead. :)

Do this. Open a terminal. This command:

[CODE]sudo blkid
```

You will be asked for your password. It will be invisible. This is how it should be (security thing). See your USB listed there? Yes? It should be /dev/sdc or sdd or something like that. If so, make a directory, this for example:

```
sudo mkdir /mnt/USB
```

Now, whatever /dev/sd* (sde for example) your USB is, use that in this command:

```
sudo mount /dev/sd* /mnt/USB
```

You should now find the contents of the USB listed in /mnt/USB folder.

The reason the other commands you were using didn't work is probably because you copied the command verbatim and didn't replace with YOUR details. 

```
sudo mount -t vfat /media/MyUSB 
```

Do you even have a directory/mountpoint at /media/MyUSB ???

---

### Post by howlingkestrel on 2017-03-08
Thanks for the help and the advice. In the end I managed to fix almost everything by reinstalling without swap space. The only issue I have remaining is that I seem to be unable to stop the Lightdm service from running. I switch to the first virtual console with ctl+alt+f1, and then run ```
 sudo lightdm service stop 
```.

However, instead of ending the lightdm service, this instead results in a weird thing where parts of the desktop start bleeding through behind and in front of the console, and moving the mouse uncovers progressively more of it until just the standard login window is visible. I need to end X server in order to install my graphics drivers - is there some other way to do this?

---

### Post by deadflowr on 2017-03-08
Your command is all backwards, and probably not effective on your system anyway.
Try
```
sudo systemctl restart lightdm
```
if on Ubuntu 16.04or 16.10
or
```
sudo restart lightdm
```
on Ubuntu 14.04 (perhaps also 12.04)
or
```
sudo service lightdm restart
```
on 12.04 (perhaps also 14.04)
> I need to end X server in order to install my graphics drivers - is there some other way to do this?
What graphics card is it?
You should use Ubuntu's driver installation program.

(Typically you can find the driver installation program in software and Updates (even in mate)
Marked as Additional Drivers.
This applications will list any drivers you can install, beyond the open-source drivers already installed.
If your system cannot run any closed source drivers then it will not list anything.

---

### Post by howlingkestrel on 2017-03-08
It's an NVIDIA card that the update centre wasn't detecting - it only ever lists the Intel processor for proprietary drivers. The installer available for download from their website won't run whilst an X server is running. I was going to reinstall, but just getting the command the right way round seems to have fixed all of the other issues I was having - thank you so much!

---

