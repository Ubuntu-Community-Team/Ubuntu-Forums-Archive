---
title: "Installation of mdadm fails"
date: 2018-11-27
forum: General Help
---

### Post by willywortel2 on 2018-11-27
Hi,

In an attempt to restore my data of NAS HDDs I found possible solution on [https://techwiztime.com/guide/synology-nas-data-recovery-ubuntu/](https://techwiztime.com/guide/synology-nas-data-recovery-ubuntu/)
I downloaded Ubuntu ISO and chose to install it on clean USB FAT32. 
Once computer starts I got possibility to chose "try ubuntu" or "install ubuntu". I've chosen "try".
 
In terminal I run "sudo apt-get install mdadm", but it fails and I got:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
   default-mta | mail-transport-agent dracut-core
The following NEW packages will be installed:
   mdadm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/416 kB of archives.
After this operation, 1,235 kB of additional disk space will be used.
Preconfiguring packages ...
debconf: DbDriver "config": could not sync 
/var/cache/debconf/config.dat-new: Input/output error
dpkg: could not open log '/var/log/dpkg.log': Input/output error
dpkg: error processing archive 
/var/cache/apt/archives/mdadm_4.1~rc1-3~ubuntu18.04.1_amd64.deb 
(--unpack):
  unable to sync file '/var/lib/dpkg/[tmp.ci//conffiles]("http://tmp.ci//conffiles")': Input/output 
error
dpkg: error: unable to sync new file '/var/lib/dpkg/status-new': 
Input/output error
W: Could not open file '/var/log/apt/history.log' - OpenLog (5: 
Input/output error)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

What does the error mean?
Is it related to fact I chose FAT32 usb stick?
Any hint?

---

### Post by SeijiSensei on 2018-11-27
If you want to use a USB stick, it needs to be formatted with ext4, not FAT32.  FAT32 doesn't have the filesystem primitives *nix systems expect like permissions, modification dates, etc.

---

