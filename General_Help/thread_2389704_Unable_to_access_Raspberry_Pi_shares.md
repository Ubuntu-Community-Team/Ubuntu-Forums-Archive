---
title: "Unable to access Raspberry Pi shares"
date: 2018-04-20
forum: General Help
---

### Post by makem2 on 2018-04-20
I have a RPI3 B+ set up on a WiFi  network with a USB SSD drive, have shared the home directories and a folder named 'data' on /media/USBHDD/data.

From windows 10 I can access the folder via Samba but cannot access it from xubuntu.

I have another RPI and was able to access that from xubuntu (It is now offline). I have not made any changes to xubuntu.

When attempting to access the folder the error given is:

Failed to open "WORKGROUP" Failed to retrieve share list from server: No route to host.

I have two PVAs on the network and was able to 'see' them too but now they have disappeared. They were listed separately and also inside the WORKGROUP folder.

The USB drive I am using was previously connected to an earlier RPI and the folders on it were previously set up. This is the only thing I can think of which might prevent the folder appearing as it was not made whilst connected to the current RPI.

The RPI and the SSD are both temporarily powered from the xubuntu USB 3 'Always On' port. Not enough power? (Enough for Windows!)

There is a lot of wood out there but I cannot see it for trees! Any pointer to what is probably an obvious error would be appreciated.
 
```

makem@ssdTOSH:~$ sudo cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
NAME="Ubuntu"
VERSION="16.04.4 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.4 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

```

```

pi@raspberrypi:~ $ sudo smbtree
Enter root's password: 
WORKGROUP
    \\SSDTOSH                ssdTOSH server (Samba, Ubuntu)
        \\SSDTOSH\Canon_MG4200_series    Canon MG4200 series
        \\SSDTOSH\IPC$               IPC Service (ssdTOSH server (Samba, Ubuntu))
        \\SSDTOSH\shares             
        \\SSDTOSH\print$             Printer Drivers
    \\RASPBERRYPI            Samba 4.5.12-Debian
        \\RASPBERRYPI\IPC$               IPC Service (Samba 4.5.12-Debian)
        \\RASPBERRYPI\shares             Data Folder
        \\RASPBERRYPI\print$             Printer Drivers
        \\RASPBERRYPI\homes              Home Directories
    \\0D3B28000000           MG4200 series
        \\0D3B28000000\IPC$               
        \\0D3B28000000\canon_memory       MG4200 series
pi@raspberrypi:~ $ 

```

```

makem@ssdTOSH:~$ sudo smbtree
[sudo] password for makem: 
Enter root's password: 
WORKGROUP
    \\SSDTOSH                ssdTOSH server (Samba, Ubuntu)
        \\SSDTOSH\Canon_MG4200_series    Canon MG4200 series
        \\SSDTOSH\IPC$               IPC Service (ssdTOSH server (Samba, Ubuntu))
        \\SSDTOSH\shares             
        \\SSDTOSH\print$             Printer Drivers
    \\RASPBERRYPI            Samba 4.5.12-Debian
    \\0D3B28000000           MG4200 series
        \\0D3B28000000\IPC$               
        \\0D3B28000000\canon_memory       MG4200 series
makem@ssdTOSH:~$

```

RPI fstab:

```

proc            /proc           proc    defaults          0       0
PARTUUID=46aa400e-01  /boot           vfat    defaults          0       2
PARTUUID=46aa400e-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that

UUID=b3bd607e-3ace-4ef7-8962-95c5326d365e /media/USBHDD ext4 defaults,noatime 0 1

```

RPI /etc/samba/smb.conf:

```

[global]
   workgroup = WORKGROUP
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n$
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
[shares]
  comment = Data Folder
  path = /media/USBHDD/data
  valid users = @users
  force group = users
  browsable = yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = no

```

EDIT: The other machines have 'come back' following a second reboot but the pi is still absent. Maybe this is a RPI problem and not xubuntu.

---

### Post by HermanAB on 2018-04-20
To debug the problem, you need to see the error messages.  To see them , you should use a program called smbclient to connect to the share.

---

### Post by makem2 on 2018-04-20
> **HermanAB said:**
> To debug the problem, you need to see the error messages.  To see them , you should use a program called smbclient to connect to the share.

Thanks for that HermanAB however as it seems to be a problem Pi related I am going to use the recommended NFS system (when I understand it lol.

---

