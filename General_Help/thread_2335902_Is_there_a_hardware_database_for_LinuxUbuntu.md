---
title: "Is there a hardware database for Linux/Ubuntu?"
date: 2016-09-02
forum: General Help
---

### Post by moma on 2016-09-02
Hello,
I just bought a new laptop on which I installed Ubuntu 16.10.  The laptop is:
Toshiba Satellite P50 with Intel Core i7-6700HQ CPU,  16GB RAM, 1TB hard drive + 128GB SSD drive.

I am very pleased with this hardware and Ubuntu boots & runs blazingly fast due to SSD drive. It boots into the desktop in 5 secs.
I disabled the Secure Boot in the settings (F2) before installing Ubuntu. 

I had no problems what-so-ever during the installation.  
To boot from a USB-pen, one has to press F12 at the boot to see a list of boot options , hard drives and USB-pens.

I noticed that this laptop has three USB3 ports, but no USB2 ports (for my old mouse).
Luckily I had a small multi USB-adapter in the house.

**Is there a hardware database where I can submit the laptop info?**

-----
BTW: Acer Aspire was not good.
I bought first an Acer Aspire laptop with pre-installed Windows 10, but it was very slow in my opinion. It took several minutes to load to the Windows 10.
Also,  I had problems with the UEFI-bootloader / Secure Boot on the Acer laptop. I installed Ubuntu on it, but I could not make Ubuntu's boot-menu to appear.  It always _[U]**[U]slowly but surely_**[/U][/U] went to the Windows.
Also, the function keys (like F2, F12) where not accurately detected at the boot of Acer Aspire!  I had to restart and retry several times before I managed to get to the setup screen (F2) or system's boot menu(F12). 
Also the Acer Aspire logo was lingering and floating on the screen suspiciously long time and I totally lost my hair .   \

**** YOU ACER !   WHY AREN'T YOU TESTING OR CERTIFYING YOUR HARDWARE FOR LINUX. 
YOU WERE WASTING MY TIME !^%#$

I returned the Acer Aspire laptop back to the shop. The Portuguese Worten.pt shop let me exchange the Acer Laptop to Toshiba Satellite. I am happy now. 
Thanx.

---

### Post by ian-weisser on 2016-09-02
Canonical maintains a database of tested hardware, including both full systems and lots of individual components: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/) 
The checkbox-ng package will run a series of hardware tests, and automatically submit the results to the Canonical database.
Checkbox-ng will not accept manual 'machine incompatible with Linux' reports. Those would be easy for trolls to spoof.

---

### Post by 1clue on 2016-09-02
Does Toshiba still have the problem with overheating?

I've had 2 different Toshiba laptops which both ran full-cpu all the time and I could never get the fans working right.

It was a power management issue.

---

### Post by moma on 2016-09-02
Boa noite e obrigado.
Ok, i have now run the checkbox-qt and it seemed to succeed (except one test that failed) .

However, the program did not do anything when I tried to save the results to a file.  It probably has a small bug. Nevertheless the checkbox is an interesting test suite.
[[img]http://bildr.no/thumb/RDR1UmYr.jpeg[/img]](http://bildr.no/view/RDR1UmYr)
---

@1clue:
I have not yet experienced overheating on this computer.  It runs Ubuntu 16.10 (I installed from the latest, daily iso).
One of the system tests (memory check with load/unload mem to the swap space) made this system to struggle, the fans ignited and the desktop froze for a minute or two.

I will now put a Memory and CPU monitor (applet) to the system tray. The Ubuntu's System Monitor is also useful.

About the GTP:
Yes, I saw the GPT option in the BIOS/EFI setup, but I did not know what it meant. Thanks for informing.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

ps. Audio-recorder is now available for Ubuntu 16.10.  Bem-vindos !
[https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

---

### Post by moma on 2016-09-03
EDIT:
I made changes to the partitioning where I moved /home, /tmp and /var to the spinning hard drive.
The static system partition "/" remains on the solid state drive. This reduces possible wear and tear on the SSD material.  However, I have no previous experience on this matter!

The partitioning is now:
"**/**"  :  system partition on the SSD drive, 50GB.
**/home** : on the spinning hard drive, 100GB.
**/tmp** :  on the spinning hard drive, 25GB.
**/var** : on the spinning hard drive, 30GB.

Observations:
The startup-boot time is now longer, approx 10 secs.
The fans are now working **more frequently**, but this is not yet a problem.  Maybe the spinning hard drive has its own cooler fan?

About IPV6 in Ubuntu 16.10:
In earlier Ubuntu versions I had to **disable** IPV6 in the Network connections dialog. Otherwise some programs could not find or resolve IP-addresses and web-browser simply displayed "Resolving address...." forever. This issue has been fixed in Ubuntu 16.10.  There is no need to disable the IPV6 anymore. It is also possible that my Portuguese net provider has done some improvements on their routers and servers.

---

