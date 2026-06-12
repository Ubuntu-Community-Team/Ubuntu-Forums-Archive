---
title: "Shares-admin Read Only UNCHECKED but folder still read only on other machines. How?"
date: 2015-05-06
forum: General Help
---

### Post by 777funk on 2015-05-06
I have a few shared folders that ARE read-only (checked) and a few that are NOT checked. For some reason no other machines are able to access these folders. I have 2 Xubuntu machines on this network and both have the same problem.

Why is this?

---

### Post by 777funk on 2015-05-06
anyone have an idea on this?

---

### Post by yancek on 2015-05-06
You neglected to mention which operating system you have on the "other machines".  If they are windows systems, that is expected behavior in a default install although it can be changed.  If the other machines are Linux, you will need to give more information such as what steps you have taken to share, installing nfs for example.

---

### Post by 777funk on 2015-05-06
Thanks, and it's on Ubuntu and Windows machines (and Android).

---

### Post by Morbius1 on 2015-05-07
I don't understand the nature of the problem. Is it that you cannot "see" the Xubuntu machines or is it that you can't access the shared folders on the Xubuntu machine?

Anyway, post the output of the following command so we can at least see how you are set up:
```
testparm -s
```

---

### Post by 777funk on 2015-05-07
They are showing up and I can access them. They're just *read only*.  I can't modify the files from the other networked machines (Ubuntu,  Windows, and Android). So it's a problem on the Xubuntu machine that's  sharing the files/folders.

I have two Xubuntu machines on this  network and both have the same problem. I share and uncheck "read only"  and I still can't modify the files from the other machines on the  network.



Here's the testparm result:

> Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Vids]"
Processing section "[My Documents]"
Processing section "[Music]"
Processing section "[Pics]"
Processing section "[Taxes]"
Processing section "[Nick]"
Processing section "[Ashley's Backup]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Vids]
    path = /mnt/Win_D_Data/Docs/Vids
    guest ok = Yes

[My Documents]
    path = /mnt/Win_D_Data/Docs/My Documents
    guest ok = Yes

[Music]
    path = /mnt/Win_D_Data/Docs/Music
    guest ok = Yes

[Pics]
    path = /mnt/Win_D_Data/Docs/Pics
    guest ok = Yes

[Taxes]
    path = /mnt/Win_D_Data/Docs/My Documents/Nick/Work/Financial Records/Taxes
[SIZE=4]**    read only = No**[/SIZE]
    guest ok = Yes

[Nick]
    path = /home/nick/Desktop/Win_D_Data/Docs/My Documents/Nick
    guest ok = Yes

[Ashley's Backup]
    path = /home/nick/Desktop/Win_D_Data/Docs/Ashley's Backup
[SIZE=4]**    read only = No**[/SIZE]
    guest ok = Yes



Note the read only = No status. For some strange reason, they're still not writable.

---

### Post by Morbius1 on 2015-05-07
What are the permissions on the  /mnt/Win_D_Data directory:
```
ls -dl  /mnt/Win_D_Data
```
And how are you mounting this partition:
```
cat /etc/fstab
```

---

### Post by 777funk on 2015-05-07
Here's that:
drwxrwxrwx 1 root root 4096 May  6 11:40 /mnt/Win_D_Data

I have it mounted like this:
UUID=xxxxxxxxxxxxxxxx /mnt/Win_D_Data ntfs users,defaults 0 0

I also have the folders shared on the boot drive (Xubuntu) that are not sharing

---

### Post by Morbius1 on 2015-05-07
I actually don't see anything wrong with any of that. The only odd thing is how you "nested" your shares. For example:

This will allow read only:
> [My Documents]
    path = /mnt/Win_D_Data/Docs/My Documents
    guest ok = Yes
This will allow write:
> [Taxes]
    path = /mnt/Win_D_Data/Docs/My Documents/Nick/Work/Financial Records/Taxes
[SIZE=4]**    read only = No**[/SIZE]
    guest ok = Yes

If you try to write to /mnt/Win_D_Data/Docs/My Documents/Nick/Work/Financial Records/Taxes through the [My Documents] share it will fail but if you try to write through the [Taxes] share you will succeed.

And to be honest I don't know what to make of these:
> [Nick]
    path = /home/nick/Desktop/Win_D_Data/Docs/My Documents/Nick
    guest ok = Yes

[Ashley's Backup]
    path = /home/nick/Desktop/Win_D_Data/Docs/Ashley's Backup
[SIZE=4]**    read only = No**[/SIZE]
    guest ok = Yes
Is that the same "WIn_D-Data" that's under /mnt? What are these symlinks or something? Those make no sense to me.

I should have shut down many hours ago so it's likely I'm missing something but your partition is mounted with 777 permissions allowing everyone free access so the only gate is the share definition.

---

