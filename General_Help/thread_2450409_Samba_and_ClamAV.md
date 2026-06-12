---
title: "Samba and ClamAV"
date: 2020-09-13
forum: General Help
---

### Post by toad007toad007 on 2020-09-13
Hello all,

First off I am running Ubuntu Server 20.04 on an Intel NUC with two external 10TB drives in RAID 1 for backup purposes and for hosting my Nextcloud instance. I have my Samba share setup and it is communicating with other computers on the network just fine and they are able to read/write. However, I am trying to get the virusfilter vfs module for Samba to work with ClamAV. I followed the vfs_virusfilter manpage on the Samba doc webpage to set the parameters for the module in the smb.conf file. I have tried placing the parameters in both the [Global] section, as well as in the share section under my share. It doesn't seem to do anything no matter where I place it. I have it set to rename the file upon detection. The socket path for clamav is correctly set in the smb.conf file. I do have the vfs modules package installed through apt-get, and the virusfilter.so is indeed on my system (/usr/lib/x86_64-linux-gnu/samba/vfs/virusfilter.so). Has anyone gotten this combination to work? I mean, I can just use clamdscan and schedule a regular scan on my share, but I would rather have on access scanning enabled if I can, although it would slow-down my writes into the share via Timeshift system backup running on my desktop.

Here is my share config in case anything stands out...

[shared]
  path = /mnt/raid1/shared
  comment = Samba share on NUCNAS
  vfs objects = virusfilter
  virusfilter:scanner = clamav
  virusfilter:socket path = /var/run/clamav/clamd.ctl
  virusfilter:scan on open = yes
  virusfilter:scan on close = no
  virusfilter:max file size = 100000000
  virusfilter:min file size = 10
  virusfilter:infected file action = rename
virusfilter:rename prefix = virusfilter.
  virusfilter:rename suffix = .infected
  virusfilter:infected file command = echo -e "Subject: Samba: Virus Found\nFound virus during on-access scanning of Samba share." | ssmtp "***********@gmail.com"
  virusfilter:scan error command = echo -e "Subject: Samba: Scan Error\nScan error  during on-access scanning of Samba share." | ssmtp "***********@gmail.com"
  guest ok = yes
  sharename = shared
  browsable = yes
  writable = yes
  read only = no
  create mask = 0775
  directory mask = 0775

Note: I will be disabling guest access and using authentication. I only went with guest access for testing to get it initially up and running.

Thanks to anyone that may be able to help!

---

