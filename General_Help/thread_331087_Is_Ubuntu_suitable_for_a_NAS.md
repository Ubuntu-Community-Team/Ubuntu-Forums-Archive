---
title: "Is Ubuntu suitable for a NAS ?"
date: 2007-01-04
forum: General Help
---

### Post by BooToo on 2007-01-04
Hi,
I am new and a pure advanced windows user who wants to do the switch to the Linux world...

I have been looking at the UBUNTU world for some time now and today, I have an opportunity to use it as the OS of my new DIY NAS box.

I have reviewed some of the post related but still have unanswered questions :confused: 

_Main Requirement :_
- What UBUNTU version should I take ? 
- A small OS (to be stored on a USB key plugged on a USB port so max should be 2 Gig) 
- An easy additionnal packages/software installation (click the icon like windows)
- A web admin interface to control the NAS from another PC
- SAMBA, FTP, Apache, MySQL, Mail Server capable
- Raid 5 stable & strong ](*,) software management (Hot plug, rebuild array and increase array size whithout recreating from scratch in particular)
- Wide range of hardware support (promise SATA controlers & Nforce 4 in particular)
- Regular bug fixes
- Sleeping mode hard drive management

All the multimedia side is irrelevant as I am looking for a rock stable always on server.

Thank you for your feedback & experience.
If I go for UBUNTU, I will write a full "who to build you DIY NAS" for this forum to share my experience.

---

### Post by chrsjav on 2007-01-18
[FreeNAS]("http://www.freenas.org/") may be what you are looking for.  Though it is still technically beta, most users consider it stable.

>  FreeNAS support in the current release:

    * Filesystem: UFS, FAT32, EXT2/EXT3, NTFS (limited read-only)
    * Protocol: CIFS (samba) , FTP, NFS, SSH, RSYNC and AFP
    * Hard drive: ATA/SATA, SCSI, USB and Firewire
    * GPT/EFI partitionning for hard drive bigger than 2TB
    * Networks cards: All supported by FreeBSD 6 (including wireless card!)
    * Boot from USB key
    * Hardware RAID cards: All supported by FreeBSD 6
    * Software RAID 0, 1 and 5
    * Management of the groups and the users (Local User authentication and Microsoft Domain)

---

### Post by Johan! on 2007-01-18
> **BooToo said:**
> 
_Main Requirement :_
- What UBUNTU version should I take ? **6.06 for stability, 6.10 for newer packages**
- A small OS (to be stored on a USB key plugged on a USB port so max should be 2 Gig) 
- An easy additionnal packages/software installation (click the icon like windows)**Try the server installation, if you want a user interface install xfce**
- A web admin interface to control the NAS from another PC **Try webmin**
- SAMBA, FTP, Apache, MySQL, Mail Server capable **A server installation can do this**
- Raid 5 stable & strong ](*,) software management (Hot plug, rebuild array and increase array size whithout recreating from scratch in particular) **Don't know about that**
- Wide range of hardware support (promise SATA controlers & Nforce 4 in particular) **Works fine here (ASUS A8N-E, Promise Ultra 100 TX-2)**
- Regular bug fixes **Ubuntu is updated regularly**
- Sleeping mode hard drive management **hdparm can do that**


I hope this will help

---

