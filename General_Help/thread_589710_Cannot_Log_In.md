---
title: "Cannot Log In"
date: 2007-10-24
forum: General Help
---

### Post by whittler on 2007-10-24
Hi There,

Today when I attempted to log in, I got beyond the log-in screen, the music played, my desktop displayed, then a retro-stripey pattern formed on my screen and it reverted back to the log-in screen. This is persisting.

I can log-in using a GNOME failsafe session.

I am using Ubuntu 7.04. My machine has 256 Mb of RAM (so it should be enough). It had been loading without a problem when I loaded it a couple of months ago.

Any help would be appreciated.

Thanks

---

### Post by Qwerty_ on 2007-10-24
Do you know what graphics card you have?

Have you installed the restricted drivers?

System>Administration>Restricted Drivers Manager.

---

### Post by whittler on 2007-10-24
Hi,

It does not have a graphics card. It uses on-board graphics. I don't know how to get information about the on board graphics.

When I attempted to install the restricted drivers, it popped a message that my hardware does not need the restricted drivers.

---

### Post by taurus on 2007-10-24
You could be running out of disk space.  At the GUI login screen, press <Ctrl><Alt>F2 and login into a virtual console with your username and password.  Then at the prompt, post the output of this command.

```
df -h
```

---

### Post by whittler on 2007-10-24
It has become worse. Now I cannot even log-in failsafe mode.

The hard-drive is almost empty. I have hardly any data on the disk.

---

### Post by whittler on 2007-10-25
Hi,

My system is still foobar. Any ideas out there?

Cheers

---

### Post by whittler on 2007-10-25
There once was a man from Nantucket

---

### Post by taurus on 2007-10-25
Can you boot your machine with the LiveCD?  If you can, then open a terminal and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by whittler on 2007-10-26
I turned on the PC today and the problem has gone. I cannot explain it.

My guess is as follows - I swap between two PCs with a KVM switch. Each is set to a different screen resolution. When Ubuntu came on, it had a GUI meltdown by trying to dynamically change screen resolutions.

I came to this conclusion because it works when I kick off the Ubuntu box first. It only packs it in when Ubuntu comes on second (and I swap to it from my other PC).

---

### Post by whittler on 2007-10-27
My apologies for this. But the problem is back. Here is the output of **sudo fdisk -l**:

> Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by taurus on 2007-10-27
How about 

```
df -h
```

---

### Post by whittler on 2007-10-27
Output of df -h is:

> Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
tmpfs                 252M   12K  252M   1% /tmp

---

### Post by taurus on 2007-10-27
Are you running that command from the LiveCD?  If you are, try to boot your machine into recovery mode from GRUB menu and run that command again.

---

### Post by whittler on 2007-10-27
OK. Done. Forgive any typo's. I had to hand type it:

> 
Filesystem      Size      Used      Avail     Use%      Mounted on
/dev/sda1      36G       2.6G      31G        8%          /
varrun            252M     104K     252M      1%         /var/run   
varlock           252M          0K     252M      0%         /var/lock
procbususb    252M         88K     252M      1%       /proc/bus/usb
udev              252M         88K     252M      1%       /dev
devshm          252M         0K     252M      0%       /dev/shm
lrm                  253M         33M    219M      14%    /lib/modules/2.6.20-16-generic/volatile


---

### Post by taurus on 2007-10-27
If you want to know what onboard graphic card do you have, run

```
lspci
```

---

### Post by whittler on 2007-10-27
The output from lspci is:
> 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


---

### Post by whittler on 2007-10-27
Aint it purrrrty:

[IMG]http://i167.photobucket.com/albums/u122/sixesallround/screenDeath.jpg[/IMG]

---

