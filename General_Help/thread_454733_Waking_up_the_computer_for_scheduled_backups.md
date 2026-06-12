---
title: "Waking up the computer for scheduled backups"
date: 2007-05-25
forum: General Help
---

### Post by Genecks on 2007-05-25
Is it possible to use K/Ubuntu to wake up the computer and make scheduled backups? Is it possible to even make scheduled backups? Is it possible to wake up the computer after I turn it off?

I know I can do these things with Windows XP, but I don't know if I can do them with K/Ubuntu.

---

### Post by dbott67 on 2007-05-25
There are a number of tools that you can use:

**1. Wake-on-LAN**: many newer network cards support this technology and can be remotely "woken up" by sending it a "magic packet".  If you only have one system, this is not the tool.  If you plan on waking up the PC from another location, then there are a number of free W-O-L packages for Windows & Linux.  Ubuntu has a couple of apps in the repositories:
```
dbott@feisty:~$ **sudo apt-cache show etherwake**
Password:
Package: etherwake
Priority: optional
Section: universe/net
Installed-Size: 72
Maintainer: Alain Schroeder <alain@debian.org>
Architecture: i386
Version: 1.09-1
Depends: libc6 (>= 2.3.4-1)
Filename: pool/universe/e/etherwake/etherwake_1.09-1_i386.deb
Size: 9468
MD5sum: 82cac3ff110ca89a15251a100c505f1c
SHA1: 64ba676022ee0187eff5f98346d8ead3ace82b5e
SHA256: 3a4eae2f73a92fc814412b868a9b51180e0a0a7f44a89eac60717e65dcd7e25f
Description: A little tool to send magic Wake-on-LAN packets
 You can wake up WOL compliant Computers which have been powered down to
 sleep mode or start WOL compliant Computers with a BIOS feature.
 .
 WOL is an abbreviation for Wake-on-LAN. It is a standard that allows you
 to turn on a computer from another location over a network connection.
 .
 etherwake also supports WOL passwords.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

dbott@feisty:~$ **sudo apt-cache show wakeonlan**
Package: wakeonlan
Priority: optional
Section: universe/net
Installed-Size: 72
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Daniel Baumann <daniel@debian.org>
Architecture: all
Version: 0.41-6
Depends: perl, perl-modules
Filename: pool/universe/w/wakeonlan/wakeonlan_0.41-6_all.deb
Size: 11032
MD5sum: 6e22287cfdaa0313ba9c194f91c06c2d
SHA1: f939b2580d759b0a5292a681fb3e5f7604555510
SHA256: ac59894b58844211342396301aecbb33912b438e9fd32481f353ee42eaf454ca
Description: Sends 'magic packets' to wake-on-LAN enabled ethernet adapters
 With this package you can remotely wake up and power on machines which have
 motherboards or network cards which support 'Wake-on-Lan' packets.
 .
 The tool allows you to wake up a single machine, or a group of machines.
 .
 You need the MAC addresses of machines to construct the WOL packets, but you do
 not need root privileges to use the program itself as UDP packets are used.
 .
  Homepage: <http://gsd.di.uminho.pt/jpo/software/wakeonlan/>
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

[B]
2. BIOS Setting[/B]: Some system BIOSes support scheduled starts (we've got ~100 Dell OptiPlex computers that have this function).  You can program the computer to boot up at a scheduled time.

**3. cron**: This is the program within linux that allows you to schedule any task to run at any time.  To backup the system, you might write a little **rsync** script that sends modified files across the network to another machine; or use **dd** to copy the entire  disk to another disk; **dump**/**rdump**

If you can provide a little more detail as to your setup and what you're trying to achieve (i.e. backup to tape, CD or DVD; backup to another system; etc.), how many computers are involved, the volume of data, any other relevant data, we may be able  to offer more specific answers.

-Dave

---

