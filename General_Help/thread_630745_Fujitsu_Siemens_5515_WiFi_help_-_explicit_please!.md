---
title: "Fujitsu Siemens 5515 WiFi help - explicit please!"
date: 2007-12-03
forum: General Help
---

### Post by Geoffduke on 2007-12-03
I am a total newbie to Linux and Ubutnu 7.1 and want to use the inbuilt WiFi module.  It works perfectly okay with a Zydas dongle but Fujitsu-Siemens seem to be somewhat Linux unfriendly.
Trying desperately to understand the syntax and precisely what is required to implement the guidance below ***  Also if this can be run as a script - albeit I don't know the language or the syntax to do this yet.

Can I just enter into a terminal window exactly as I have shown below or do I need to prefix every line with sudo?   I really don't know.  I will know at some point I am sure but just want to get the box up and running and can learn in the fulness of time.

sudo /etc/modprobe.d/blacklist
blacklist ath_prc
blacklist sis190
modprobe -r ath_pci
modprobe -r sis190
cd /etc/modprobe.d/
make uninstall
tar -xzf ndiswrapper-1.48.tar.gz 
make
make install
depmod -a
ndiswrapper -i desktop net5211.inf
ndiswrapper -i desktop sisgbe.inf
ndiswrapper -l
modprobe ndiswrapper
dmesg
ifconfig
ndiswrapper -m
cd /etc/modules/ndiswrapper

really quite lost on what is needed in the last bit apart from reboot; and is the above interpretation  and syntax correct and going to work?



***


HOW-TO: Fujitsu-Siemens ESPRIMO Mobile Wifi+Ethenet setup with ndiswrapper in Feisty
 
SiS191 Gigabit Ethernet (PCI ID: 1039:0191) and Atheros wireless (PCI ID: 168c:001c) hardware are not supported by Ubuntu Feisty Desktop after installation because it tries to use Atheros Madwifi drivers (<http://madwifi.org/>;) and Sis190/191 linux drivers ([www.sis.com](www.sis.com) <http://www.sis.com>;). After an update of these drivers the cards still not work.

I WORKAROUND the problem with ndiswrapper 1.48 built from source (it is designed for wirless NICs but it's so good that it can drive that wired NICs too!!).

Steps:
- blacklist "ath_pci" and "sis190" modules in /etc/modprobe.d/blacklist
- Unload those modules with "modprobe -r"

- Download the windows XP drivers of the cards from fujitsu-siemens ("WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g" and "SiS 196"), extract the directories with the .inf file and copy them to your laptop home (maybe using an USB stick).

- Download and copy to your laptop home the ndiswrapper 1.48 tarball (from <http://ndiswrapper.sourceforge.net/>;)
- Unpack it with "tar -xzf" and remember to "make unistall" (to delete the ndiswrapper module shpped with Feisty) before "make" and "make install".

- Refresh module dependecy file with depmod -a

- Install both drivers using "ndiswrapper -i <path to windows driver .inf file>" (net5211.inf and sisgbe.inf).
- verify that "ndiswrapper -l" return:

net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
sisgbe : driver installed
device (1039:0191) present (alternate driver: sis190)

- Load ndiswrapper module with "modprobe ndiswrapper" and see with "dmesg" if drivers load successfully.

- Now "ifconfig" must show two new devices: wlan0 and wlan1. Configure them with Gnome network manager or with the tools you prefer and test your connection.
- Once you are satisfied, write ndiswrapper module configuration with "ndiswrapper -m" and add "ndiswrapper" to the list of modules to load at startup (/etc/modules).
- Reboot

- EOF

Any help appreciated....Geoff.

---

### Post by Tollkirk on 2008-01-01
I too am in desperate need for the details for this fix (having completely wiped Vista off my machine inadvertently, and now finding myself with no way of connecting to the Internet!) I also need to know where to get the .inf/.sys files as they don't appear to be on the driver disk that came with the machine.

---

### Post by bilbophile on 2008-01-05
You can find FS Drivers here: [http://support.fujitsu-siemens.com/com/support/downloads.html]("http://support.fujitsu-siemens.com/com/support/downloads.html").

I have tried ndiswrapper and I am in the situation shown here: [SIS191 Gigabit LAN card not working/compatible with ubuntu 7.04?Can't access Internet]("http://ubuntuforums.org/showpost.php?p=3999959&postcount=24"), although I am on a Fujitsu-Siemens ESPRIMO Mobile v5535, which officially came with Linux (i.e. with a DVD with a two-year old version of Knoppix, unable to recognise even the sound card).

---

### Post by the_sorrow on 2008-01-05
GeoffDuke, Yes you must use the sudo command to make it work, or simply type
sudo -s 
to work as root and no more sudo needed.

Tollkirk, .inf and .sys are created after you install the driver on a windows machine, they are compressed in one single .exe file in your driver cd, do it in someone else computer (with windows) then copy the files and you are done.

---

