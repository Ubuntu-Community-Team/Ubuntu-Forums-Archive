---
title: "OS stops working after a day"
date: 2016-02-23
forum: General Help
---

### Post by crip720 on 2016-02-23
I have an Acer E 15 laptop with an Intel N3530 cpu, HD graphics, and a WD 1tb hard drive.  I am using Ubuntu 15.10 upgraded from 15.04.  The OS seems to stop working after about a day of use.  I do not think it is a freeze up, but more like the hard drive loses power for a second or two.  The day after the upgrade the system would stop every hour or two, so I disable/deleted the intel drivers downloaded in 15.04 and disable the additional driver.  This got the system to last for more than 24hrs.  On start up I do have 4 lines that says something about i2c device not detected(?), but everything else is a green OK.  Had this problem on 15.04, but only every 2 or 3 weeks.  I am using 14.04 on a external Seagate hard drive and do not have this problem. The temps are in the 40s.  Can you give me any help to fix this?  Thank you, Colin.

---

### Post by sandyd on 2016-02-23
Run
```

cat /var/log/dmesg | more
```

Are there any errors there?
If so, please post them here.

---

### Post by crip720 on 2016-02-23
These are the lines I found.  I hope this is what you wanted.  Sorry for the format.    13.874247] i2c_hid i2c-SYN1B7E:01: failed to retrieve report from device.  13.708852] lp: driver loaded but no devices found. 13.552666] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0 . 13.417379] dw_dmac INTL9C60:00: invalid resource. 
 2.263592] usb: failed to peer 1-2-port1 and usb2-port1 by location (1-2-por
t1:none) (usb2-port1:usb1-port1)
[    2.263607] usb 1-2-port1: failed to peer to usb2-port1 (-16)
[    2.263611] usb: port power management may be unreliable
[    2.263882] usb: failed to peer 1-2-port2 and usb2-port1 by location (1-2-por
t2:none) (usb2-port1:usb1-port1)
[    2.263890] usb 1-2-port2: failed to peer to usb2-port1 (-16)
[    2.264157] usb: failed to peer 1-2-port3 and usb2-port1 by location (1-2-por
t3:none) (usb2-port1:usb1-port1)
[    2.264165] usb 1-2-port3: failed to peer to usb2-port1 (-16)
  1.662154] r8169 0000:01:00.1: can't disable ASPM; OS doesn't have ASPM cont
rol
 1.654972] ahci 0000:00:13.0: controller can't do DEVSLP, turning off
1.493259] [Firmware Bug]: battery: (dis)charge rate invalid.  1.471067] ACPI PCC probe failed.
1.471058] PCCT header not found.   1.447310] i8042: PNP: PS/2 appears to have AUX port disabled, if this is in
correct please boot with i8042.nopnp
 
 1.438803] hpet: number irqs doesn't agree with number of timers.    1.410000] [Firmware Bug]: No valid trip found
[    1.410060] GHES: HEST is not enabled!   0.758516] Trying to unpack rootfs image as initramfs...
 0.606182] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
 0.606171] \_SB_.PCI0:_OSC invalid UUID .           0.212282] PCI: Using host bridge windows from ACPI; if necessary, use "pci=
nocrs" and report a bug
        0.211149] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_
] (20141107/hwxface-580)
[    0.211162] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_
] (20141107/hwxface-580)
        0.050135] Ignoring BGRT: invalid status 0 (expected 1)
       0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!                                                    
 0.000000] AGP: No AGP bridge found.      0.000000] x86/hpet: Will disable the HPET for this platform because it's no
t reliable
 0.000000] No NUMA configuration found.

---

### Post by crip720 on 2016-02-25
Is there any logs that will be able to be read after a hard restart.  I think I read a post that journal(?) log can be set to do this.  I would need instructions on how to do this.  Thank you, Colin

---

### Post by crip720 on 2016-03-10
I did an experiment and did a dd copy of 15.10 to another hard drive.  Still have the problem, so I guess it must be something to do with the OS. Could there be driver problem?  I did have to blacklist a couple of drivers to let 15.04(upgraded to 15.10) to do a restart.

---

### Post by oldfred on 2016-03-10
Do not know if your chip has this issue?
 Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 
      
 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

---

### Post by crip720 on 2016-03-10
I have booted into a 3.19 kernel to see if that will help.  This seems to be the easies solution right now.  Do not seem to have any 4.1s(deleted?).  Will let you know in a couple of days if this helps.  Thank you for pointing out the info.  Colin.

---

### Post by Bucky Ball on 2016-03-10
*Thread moved to **General Help**.*

---

### Post by crip720 on 2016-03-14
I have been reading up on the info, and it seems like the best bet is to add 
intel_idle.max_cstate=1. I am guessing that this is added to GRUB_CMDLINE_LINUX_DEFAULT. Is this the place to add this?
Thank you, Colin

---

### Post by oldfred on 2016-03-15
Yes, but it will increase power use.

       sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by crip720 on 2016-03-17
Tried the intel cstate=1 and OS only lasted about an hour. cstate=2 only lasted about 5 or 10 minutes.  Plain kernel 4.2 gives me about 12 to 24 hours, kernel 3.19 gives about 2 days. 15.04 used to last about 2 weeks.  Have read that kernel 4.1   is a working option, but do not know if it will be a problem to use.  Thank you, Colin

---

### Post by crip720 on 2016-03-28
Have also tried cstate=0, lasted about 12hrs.  On my etc/default/grub I have the line grub_cmdline_linux_default, where I add the cstate section after quiet splash, but I also have a line under it that says grub_cmdline_linux with only (" ").  Do I do anything with this line?  Quiet splash does not seem to work(still have all the lines of code showing for booting.  Most instructions only mention the linux_default line.  Thank you, Colin.

---

### Post by oldfred on 2016-03-29
There is normal mode & recovery mode settings.

 [https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX

[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by crip720 on 2016-03-29
I think I will leave this question go for now, seeing it is something that Intel and the kernel devs have to work out.  Can you tell me why quiet splash is not working in normal mode?  I have it listed the default grub and have updated grub a few times.  Thank you, Colin.

---

### Post by oldfred on 2016-03-30
I have seen quiet splash not work because of typos, but otherwise it normally works.
Or sudo update-grub has not been run to include in actual copy of grub.cfg used to boot.

---

### Post by crip720 on 2016-04-20
I did a clean vanilla install of 16.04 beta. With the 4.4 kernel was getting a hard freeze about every hour.  Added the intel cstate=1 to grub config and system has been up for three days.  I am going mark this as solved for now.  Thanks to all who helped.  Colin

---

