---
title: "Ubuntu Server 12.04 Samba 4 AC DC Share Issue"
date: 2013-09-02
forum: General Help
---

### Post by Luke_KOtarba on 2013-09-02
Hello all I am new to this forums so I hope I am posting in the correct section.

I setup Samba 4 Server on my box and I can add computer to the domain and create users but I am unable to see or access share folders.

[B]my smb.conf

[/B]> 
# Global parameters
[global]
        workgroup = SKYPHOTOBOOTH
        realm = skyphotobooth.com
        netbios name = ZEUS
        server role = active directory domain controller
        security = user
        wins support = yes
        dns forwarder = 192.168.135.50
        dns forwarder = 8.8.8.8
# added after to see if works
        unix extensions = no
        map to guest = Bad User
        wide links = yes
#oplocks = no
        socket options = IPTOS_LOWDELAY TCP_NODELAY SO_KEEPALIVE
        write cache size = 2097152
        use sendfile = true
        getwd cache = yes
        public = yes
# END Addistions

[netlogon]
        path = /usr/local/samba/var/locks/sysvol/skyphotobooth.com/scripts
        read only = No
[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No
[Users]
directory_mode: parameter = 0700
read only = no
path = /mnt/Hard_Drives/data/Samba_Users
csc policy = documents

[Media]
    comment = Ubuntu File Server Share
    path = /mnt/Hard_Drives/data/Media
    read only = yes
available = yes
browseable = yes
writable = no
guest ok = yes
printable = no
locking = no
strict locking = no
wide links = yes
~



> 
/mnt/Hard_Drives/data
[drwxr-xr-x 6 root   root    4096 Sep  1 14:16 ./
drwxr-xr-x 3 root   root    4096 Sep  1 13:10 ../
drwxr-xr-x 2 nobody nogroup 4096 Sep  2 07:50 Media/
drwxr-x--- 2 root   root    4096 Sep  1 13:12 Samba_Backup/
drwxrws--- 2 root   users   4096 Sep  1 13:13 Samba_Users/
drwxr-xr-x 2 root   root    4096 Aug 31 15:56 User_Data/


[B]Testparm Output
[/B]> Load smb config files from /usr/local/samba/etc/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[netlogon]"
Processing section "[sysvol]"
Processing section "[Users]"
Processing section "[Media]"
Loaded services file OK.
Server role: ROLE_ACTIVE_DIRECTORY_DC
Press enter to see a dump of your service definitions



Thank you all in advance with any help I googled for the past two days and just hitting myself in the head.

---

### Post by prodigy_ on 2013-09-02
What OS do you have on the client? What error message do you get if you try to access the share using UNC path (e.g. **\\192.168.0.1\share_name**)?

---

### Post by Luke_KOtarba on 2013-09-02
I am using Windows 7 Pro 64 bit. 

When I try to map **[\\192.168.135.50\Media]("file://\\192.168.135.50\Media")  -- It worked this time.** I swear I tried that like 20 times. 

Thank You So much for the help.

Issue Resolved

---

### Post by Bucky Ball on 2013-09-02
Good news. Please mark thread as solved by following the thread in my signature. Good luck. ;)

* Update: Oh, you just did! Cheers, carry on ...

---

