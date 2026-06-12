---
title: "dialup modem problem"
date: 2008-02-17
forum: General Help
---

### Post by chakravarty on 2008-02-17
I am a newbie to linux. I installed ubuntu 7.10 on my laptop hp comaq 6710s.dialup net work  not working with gkppp or kppp. wvdial config says modem not found.please help me.give details of supported drivers for my laptop to use dialup m Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008
 scanModem update of:  2008_02_10
The modem symbolic link is /dev/modem -> ttySL0

 There are no blacklisted modem drivers in /etc/modprobe*  files 

The Advanced Linux Sound Architecture (ALSA) packages providing audio support, 
also includes drivers for some modems. The ALSA diagnostics are written during 
bootup to /proc/asound/ folders.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAjudge.tgz

The ALSA verion is 1.0.14
The modem cards detected by "aplay -l"  are:
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe4504000 irq 16


 The modem codec file for the the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Generic 11c1 Si3054
Address: 1
Vendor Id: 0x11c11040
Subsystem Id: 0x103c1378
Revision Id: 0x100200

 The audio card hosts a softmodem chip:  0x11c11040

 The softmodem chip 0x11c11040 is not yet supported under Linux.
 Code must be developed by manufacture LSI Inc.
 See details in [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg00915.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg00915.html)
 Read InfoGeneral.txt about alternatives modem hardware.
USB modem not detected by lsusb
For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	103c:30c0	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 16:       1488       1713   IO-APIC-fasteoi   uhci_hcd:usb1, yenta, HDA Intel, i915@pci:0000:00:02.0
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   15.544000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.544000] PCI: Setting latency timer of device 0000:00:1b.0 to 64


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===




Predictive diagnostics for card in PCI bus 00:1b.0:
	Modem chipset  detected on
CLASS="Class 0403: 8086:284b"
NAME="Audio device: Intel Corporation 82801H "
PCIDEV=8086:284b
SUBSYS=103c:30c0
SUBven=103c
IRQ=16
SLMODEMD_DEVICE=hw:0,6
IDENT=Agere_11c11040_chip_is_not_supported
SoftChip=11c11040
CODECd=11c11040
HDA=8086:284b
Driver=snd-hda-intel
SOFT=8086:284b.HDA

 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:284b Audio device: Intel Corporation 82801H
      Primary PCI_id  8086:284b
    Subsystem PCI_id  103c:30c0 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	Agere_11c11040_chip_is_not_supported

----------------end Softmodem section --------------

Writing Intel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 

Compressed files at: /usr/src/sl-modem.tar.bz2


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-05 01:27 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2008-02-17 14:40 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
odem.explain me step by step installation of drivers and configuration.Iam furnishing scan modem details

---

### Post by ketetefid on 2008-04-05
Hello,
I'm a gentoo user but have the same problem.
I registered here to request you if you got any information regarding installing this modem, I (and many others) would be glad to be informed. I'm heavily searching to solve the problem but yet in vain. Please keep investigating. If you have any comment or idea please state.
Thanks to every linux user,
PS I own a Toshiba a215 s5818 which has the same modem. Everything works but the sh!t modem.

---

### Post by s3a on 2008-04-05
I don't know about gentoo at all but honestly I haven't read your whole post chakravarty because it was too long lol but download the modem driver in my signature and then install it. Then go to System--->Administration---->Network then right click on your dial-up icon and click properties, tick the box that says to enable this connection then enter all of your information on each tab (for modem port I have /dev/modem/) then click OK then tick the box next to the dial-up icon and it should dial on gutsy in my experience. But if it doesn't, you probably need a FULL restart.

Tell me if it works!

Ketetefid, I'm sorry I have never used anything other than Windows or Ubuntu...

P.S.
You don't need gppp or kppp.

---

