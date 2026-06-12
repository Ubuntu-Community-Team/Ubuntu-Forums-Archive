---
title: "Installation/boot problem."
date: 2014-08-05
forum: General Help
---

### Post by Faizal_Baito on 2014-08-05
Hello there, 

So yeah, I'm new here at linux's world.

Here's what happened,
I dual booted ubuntu 14.04.1 with windows 7, everything was okay.
Then I decided to try linux mint 17. During mint's installation the installer crashed (Which is a common bug/problem they say) which made my windows 7 don't boot.
After hours of trying to fix it, I accidentaly formatted my partition of windows 7.
From there, I decided to clean install ubuntu by unnallocating/deleting all my partitions.
Installation of ubuntu was doing fine until a system crash happened which froze my laptop and made me force shutdown it and try again.
Now 2nd try of installation finished fined, I rebooted, then shutdown my laptop at ubuntu's virtual os and then removed my usb (by the way all installation was done using usb)
Anyway, here's where I am stuck. It keeps showing me this error msg. "Gave up waiting for root device......"

So here's what I have:

Sony Vaio E-Series VPCEH26EA

A usb flashdrive with ubuntu's image

500GB of my laptop's unnallocated space

I can only use my Vaio through ubuntu on my flashdrive :(

Any help would be appreciated, I have searched for hours in google before posting this, so yeah, this is my only chance to get my laptop fixed.

I don't need windows as I lost every file and the os. I just want to get my laptop running with ubuntu since it's what I have at hand.

---

### Post by sudodus on 2014-08-06
Welcome to the Ubuntu Forums :-)

If you intend to boot only Ubuntu 14.04.1 (not dual boot with Windows), and you know that Ubuntu works in the computer, I suggest that you make it as simple as possible.

0. Boot into the UEFI - BIOS menus and set the computer in ***BIOS alias CSM mode*** if it is (was) in UEFI mode. This is important, if you want it to be easy.

1. Boot Ubuntu from your flashdrive, [I][B]Try Ubuntu
[/B][/I]
2. Start ***gparted ***and create an MS-DOS partition table. 'Device' -- 'Create Partition Table' -- Apply

3. Start the installer (the icon in the top left corner of the desktop screen).

4. ***Install to the whole drive*** and let Ubuntu do the partitioning automatically.

-o-

If you want something more advanced for example a separate home partition or a data partition or if you want a GUID partition table, GPT, or even want to run in UEFI mode, please tell us! There are many people here, who are able to help you.

---

### Post by oldfred on 2014-08-06
Is system UEFI or just BIOS?
How you boot install media is how it will install.
And have you set UEFI/BIOS to AHCI mode, some with IDE and just / (root) & swap have had similar issues.
Often better to use a smaller / of 20 or 25GB and separate /home or /mnt/data partition(s).

Many Sony's in UEFI mode only want to boot Windows. But that is more an issue with newer systems that had Windows 8 pre-installed and in UEFI boot mode.

---

