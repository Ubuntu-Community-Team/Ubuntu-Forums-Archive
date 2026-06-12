---
title: "Ubuntu 12.04 - Printer not recognized by USB-HELP!"
date: 2012-11-14
forum: General Help
---

### Post by Daddyo-613 on 2012-11-14
**My Host System:**
O/S:                        Ubuntu 12.04 (precise)
Kernel:                   3.2.0-32-generic-pae
CPU:                       Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
VMWare Player: 5.0.1 build-894247

**My Problem:** My printer is an HP 6P LaserJet parallel printer connected to my system via a USB port using a converter cable.

The system used to recognize my printer but doesn't anymore.
I had uninstalled the printer and now I can't get it back.

**Tests Performed:** I connected a flash drive to the usb port and it is recognized right away so I know the port is working. 

I've been unloading and loading printer related packages without success. I may have removed something need but I can't tell anymore.

I would really like some help to fix this. I know it can be done because this printer connected to a usb port was working before.

---

### Post by offgridguy on 2012-11-14
Please don't take this the wrong way , but is the printer turned on?  I did it myself, couldn't
understand why i was getting no response. :)

---

### Post by Daddyo-613 on 2012-11-14
Thanks for the suggestion. Yes the printer is turned on. It could happen but not this time.

---

### Post by alenis on 2012-11-14
Some printers don't work anymore with Ubuntu. I had the same problem with my Brother MFC8840D and I had to switch to Debian to make it work again, along with my webcam which stopped to work with 12.04 as well.

---

### Post by Daddyo-613 on 2012-11-14
Well interestingly enough this printer "HP 6P LaserJet" did work on my system this morning. I've printed a test page from the printer itself so I know the printer is working.

Somehow, I've changed something since this morning and the system is no longer recognizing this particular printer.

I've been checking out this site [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) but I could use some help interpreting what I'm supposed to do.

Parallel Port Capability seems to be present:

```
~$ lsmod | grep parport_pc
parport_pc             32114  0 
parport                40930  3 parport_pc,ppdev,lp
```

But Autoprobe doesn't seem to exist:
```
sudo cat /proc/sys/dev/parport/parport*/autoprobe*
cat: /proc/sys/dev/parport/parport*/autoprobe*: No such file or directory
```

I think the solution is there somewhere.

---

### Post by pdc on 2012-11-14
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

have you had a read at this wiki

various seemingly useful commands

> [COLOR="Red"]sudo hp-setup[/COLOR]

**Troubleshooting**

> [COLOR="Red"]sudo hp-check -r[/COLOR]

This will summarize any installation errors.

as you would know ........from here..........

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_6p.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_6p.html)

....your printer should work .........

....you presumably have hplip installed [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by Daddyo-613 on 2012-11-14
Thanks to PDC for the message.

The "sudo hp-setup" opens a GUI to detect a usb or network printer etc.

The "sudo hp-check -r" command produced some interesting results which I've posted below. They are lengthly but seem to confirm that the required files are present.

```
~$ sudo hp-check -r

HP Linux Imaging and Printing System (ver. 3.12.10a)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2011-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux stephen-P5K-Office 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 12.04

Checking Python version...
OK, version 2.7.3 installed

Checking PyQt 4.x version...
OK, version 4.9.1 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.5.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 1.0.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.12.10a currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.10a

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-3.12.10a
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.12.10a
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade=true
last_upgraded_time=1352394638
pending_upgrade_time=0
latest_available_version=3.12.10a

[scan_plugins]
bb_marvell.so=Present
bb_soapht.so=Present
bb_soap.so=Present

[fax_plugins]
fax_marvell.so=Present

[print_plugins]
lj.so=Present

[settings]
systray_visible=1
systray_messages=0

[last_used]
device_uri="hp:/usb/HP_LaserJet_Professional_P1606dn?serial=000000000QQ014T9SI1c"
printer_name=
working_dir=.

[commands]
scan=/usr/bin/xsane -V %SANE_URI%

[refresh]
rate=30
enable=false
type=1

[polling]
enable=false
interval=5
device_list=

[fax]
voice_phone=
email_address=


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
lpstat
------
Type: Unknown
Device URI: No destinations added.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

-----------
| SUMMARY |
-----------

No errors or warnings.


```

Could it be that I have to load something that reports to the system that I have a serial or parallel port even if its only emulated?

---

### Post by pdc on 2012-11-14
is there anything in this thread of help to you?

[http://vanilla.slitaz.org/index.php?p=/discussion/416/help-parallel-port-1-not-listed-in-cups/p1](http://vanilla.slitaz.org/index.php?p=/discussion/416/help-parallel-port-1-not-listed-in-cups/p1)

---

### Post by Daddyo-613 on 2012-11-14
PDC:

I opened the page you referred to above and executed the commands here are the results:

```
~$ lsmod | grep lp
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
``````
~$ dmesg | grep par
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] vt handoff: transparent VT on vt#7
[    0.373295] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.000060] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   13.850034] type=1400 audit(1352940809.290:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=448 comm="apparmor_parser"
[   13.850448] type=1400 audit(1352940809.290:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=448 comm="apparmor_parser"
[   13.850685] type=1400 audit(1352940809.290:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=448 comm="apparmor_parser"
[   14.537200] ppdev: user-space parallel port driver
[   14.572623] type=1400 audit(1352940810.014:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=847 comm="apparmor_parser"
[   14.573150] type=1400 audit(1352940810.014:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=847 comm="apparmor_parser"
[   14.697805] type=1400 audit(1352940810.138:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=893 comm="apparmor_parser"
[   14.698231] type=1400 audit(1352940810.138:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=893 comm="apparmor_parser"
[   14.698471] type=1400 audit(1352940810.138:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=892 comm="apparmor_parser"
[   14.698480] type=1400 audit(1352940810.138:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=893 comm="apparmor_parser"
[   14.701608] type=1400 audit(1352940810.142:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=896 comm="apparmor_parser"
``````
~$ ls -l /proc/sys/dev/parport/parport*/autoprobe*
ls: cannot access /proc/sys/dev/parport/parport*/autoprobe*: No such file or directory

``````
~$ lpinfo -v
network https
network lpd
direct hp
network ipp
network http
network ipp14
network socket
network beh
network ipps
network smb
direct hpfax
```~$ /usr/lib/cups/backend/parallel and sudo /usr/lib/cups/backend/parallel
and they both brought me back to the command line.

I presume that this tells me that "lp", "parport" and "parport_pc" modules are loaded but that there is no physical parallel port detected on my machines. This makes sense since I don't have a physical parallel port and my parallel printer is connected to my system through a parallel to usb cable.

Is this of any help?

---

### Post by pdc on 2012-11-14
others are reporting similar problems .......

eg Mr P's posts near the end of this Mint thread (Mint is derived from ubuntu)

[http://forums.linuxmint.com/viewtopic.php?f=51&t=109243](http://forums.linuxmint.com/viewtopic.php?f=51&t=109243)

and here

[http://forums.linuxmint.com/viewtopic.php?f=51&t=116453](http://forums.linuxmint.com/viewtopic.php?f=51&t=116453)

........I do not have the solution .......

---

### Post by Daddyo-613 on 2012-11-14
There is a solution. I think!

Using hp-setup or the GUI version when you select "add printer" the is the option to "Enter URI" and on the right hand side of the dialogue box is "Enter device URI"
if you type in "parallel:/dev/usb/lp0", without the quotes of course, the forward button is enabled and then you can move through the next pages to select your printer by manufacturer and model. Select the recommended driver and the parallel printer using a usb parallel adapter cable is now installed on your system.

I still can't print to the printer but at least its installed.

I'm going to reboot my system now and see if it works.

I'll post back and let you know.

---

### Post by Daddyo-613 on 2012-11-27
**[SOLVED] There is hope for all.** It took me some time but I found a solution. I've taken the time to set out what worked for me so that others who may have a similar problem can get some ideas about what to do. If you have a problem and you do find a solution please take the time to post your findings to help others in the linux community. Try to be as precise and organized as you can. Not everyone will have the same knowledge as you about how to do things. Helping each other is what this forum is all about.

The issue for me was how to get an old HP 6P parallel printer connected to a USB port with a parallel-to-USB adapter cable to be recognized by my system so that the appropriate printer drivers could be installed. I don't have a physical parallel port on my system. I'm running Ubuntu 12.04.

**First Check USB Port:** Check that the USB port you're using is functioning. You can plug something else, a thumb drive for instance, into the USB port and see if you can access it. If you can the USB port is active. If not try another USB port until you find one that works.

**Second Check the Printer:** Make sure that the printer is on, connected and is functioning (ie print a test page from the printer itself).

**Third Check Parallel Port Modules are Loaded:** This is the meat of the issue.

**Step 1.**  Open a terminal (Ctrl+Alt+T on most systems) and check if the lp, ppdev, and parport_pc kernel modules are loaded. Cut and paste or type the following command in your terminal window and press enter:

```
$ lsmod | grep par
```If the modules are loaded you should see something like:

```
parport_pc             32114  0 
parport                40930  3 parport_pc,ppdev,lp

```If the modules are loaded you can check if you system can now recognize that you have a parallel port connected to a USB. On my machine in look like this:
```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 004 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
```then go to Step 2. 

**If the modules aren't loaded** you can load the modules with the following commands if you have root access. In your terminal window enter the following commands in sequence. When you enter the first command, you'll be prompted to put in your password. Enter your password and hit <enter>. There's no fan fair. You'll just see the $ prompt on the next line. Enter the next command etc:

```
$sudo modprobe lp 
``````
$sudo modprobe ppdev 
``````
$sudo modprobe parport_pc
```**NOTE:** After you enter these commands you can check to make sure the modules are loaded using the ”lsmod” and the “lsusb” commands above. Then go to Step 2.

**Step 2.   Check if the kernel detected the parallel port during boot up:**

**Important:** To complete this Step 2. and test whether the modules are being loaded each time you boot your machine you must first **TURN YOUR PRINTER ON AND MAKE SURE IT IS CONNECTED TO THE USB PORT THEN REBOOT YOUR COMPUTER LEAVING YOUR PRINTER ON AND CONNECTED.**

When you boot back up, open a terminal again and type the following command:

```
$ dmesg | grep par
```What you should see a lot of details outputted to your terminal window. Look through the clutter for lines like this:

```
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] vt handoff: transparent VT on vt#7
[    0.374209] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.992060] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 

[   14.950117] ppdev: user-space parallel port driver
[  15.010464] type=1400 audit(1353886652.457:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=903 comm="apparmor_parser"
[  15.011324] type=1400 audit(1353886652.457:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=903 comm="apparmor_parser"
[   15.213334] type=1400 audit(1353886652.661:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=954 comm="apparmor_parser"

[74574.820030] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vmnet(O) vsock(O) vmci(O) vmmon(O) rfcomm bnep bluetooth vesafb **parport_pc ppdev** binfmt_misc nvidia(P) usblp snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw asus_atk0110 snd mac_hid soundcore snd_page_alloc **lp parport** firewire_ohci usbhid firewire_core hid crc_itu_t atl1 pata_jmicron usb_storage
```**Note:** I've left some clutter in the output above but I've taken most of it out so that you can get a feel for what I mean without having to scroll through too much stuff. I've marked a reference to the parallel models in bold type. Each machine is going to be a little different. You just want to see something that references the modules. Try the “lsmod” and “lsusb” commands above and if you see the modules listed, you should be good to go.

**Step. 3 Initialize your Printer:** Open up the printer interface. In Ubuntu 12.04, if you're using the Unity interface, there's a launcher panel on the left hand side of your screen. Click on the <Dash Home>  icon at the top of the launcher panel (it's the button with the Ubuntu logo on it). In the dialogue box that opens start typing “printer” and when the printing icon appears, click on it. If your printer isn't showing, click on “add printer” and allow your system enough time to detect your printer. If your printer is listed on the next screen click on it and the drivers will be automatically installed.

If that doesn't work you might want to install “hplip” either using the “synaptic package manager” or by opening a terminal and typing in the following command and hitting <enter>:

```
$ sudo apt-get install hplip
```Try initializing your printer again. If your printer still isn't listed then try rebooting with your printer on and connected and then see if your system recognizes your printer. 

** A very helpful Ubuntu WIKI can be found here:**  [https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)    


To find out if your printer gets detected by CUPS (Common Unix Printing System) use the following command:

```
$ lpinfo -v
```**A helpful discussion about CUPS can be found at:** [http://ubuntuforums.org/showthread.php?t=894223&page=3](http://ubuntuforums.org/showthread.php?t=894223&page=3)

This post is already a bit too long so I won't go into the CUPS issues I had, but, I can tell you that they all can be solved. I now have an old HP 6P parallel printer connected to a local USB port working on my Ubuntu 12.04 that I can access either directly or using CUPS. 

Just to make it more interesting, I've also installed a guest virtual machine running Windows XP using free VMWare Player 5.0.1 build-894247software.  Now in VMWare Player 5.0, because of the “ThinPrint” feature included in the Player,  I'm able to print to my old HP printer from either my Ubuntu host system or the XP guest machine without having to switch any printer controls. Sweet.

Don't give up. Keep looking and good hunting.

---

