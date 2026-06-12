---
title: "samba connect to xp"
date: 2007-12-08
forum: General Help
---

### Post by reader4 on 2007-12-08
I know there are a lot of samba questions out there (I have spent several hours browsing them) but I haven't been able to crack this nut.  I am running Ubuntu 7.10 on my laptop, Win XP on my desktop at home.  I have samba setup on Ubuntu and folders shared in XP.  The problem is that I cannot browse my desktop XP share from Ubuntu.  I can browse Ubuntu from XP, and I can see the XP share server when I use "network:///" in Nautilus, but regardless of what method I try, I get:

$sudo smbclient -d 3 -W Laptop //192.168.0.2/Share
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.0.3 bcast=192.168.0.255 nmask=255.255.255.0
added interface ip=192.168.242.1 bcast=192.168.242.255 nmask=255.255.255.0
added interface ip=172.16.61.1 bcast=172.16.61.255 nmask=255.255.255.0
Client started (version 3.0.26a).
Connecting to 192.168.0.2 at port 445
timeout connecting to 192.168.0.2:445
Connecting to 192.168.0.2 at port 139
timeout connecting to 192.168.0.2:139
Error connecting to 192.168.0.2 (Operation already in progress)
Connection to 192.168.0.2 failed (Error NT_STATUS_ACCESS_DENIED)


Any ideas?  This seems to be something wrong on the XP side, but I cannot find anything - firewall is open (and I've tried it turned off), sharing is on, the folders are shared, etc.

---

### Post by jpietari on 2007-12-09
I'm not a Linux expert.  I have the same setup and tried the exact same thing as you and it worked.  All I did was make sure that my smb.conf file contained the Windows Workgroup name.


jpietari@jpietari-desktop:~$ sudo smbclient -d 3 -W danielle //192.168.1.101/Jamie
[sudo] password for jpietari:
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.1.102 bcast=192.168.1.255 nmask=255.255.255.0
Client started (version 3.0.26a).
Connecting to 192.168.1.101 at port 445
Password: 
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[DANIELLE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []
unix_clean_name []

---

### Post by reader4 on 2007-12-09
Hmmm, very frustrating.  I re-setup XP networking with a new workgroup name, just to see, and still get the same results.  The problem must be with the XP machine, because I also have an XP virtual machine on the Ubuntu computer and can connect just fine between the two.  I now notice that I cannot see the XP share in Nautilus when I use "network:///" > "Windows Network" > "WORKGROUP".  I can only see the Ubuntu machine.

---

