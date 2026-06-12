---
title: "NFS in Gutsy"
date: 2007-10-18
forum: General Help
---

### Post by arbulus on 2007-10-18
I've just upgraded to Gutsy and it seems to have interfered with NFS.  I have a directory that is set to mount over NFS at boot, but now it won't mount on boot.  I can manually mount it once I'm up and running and everything will be just fine, But I don't understand why it has stopped mounting on boot.

Anyone else having this problem or have any idea how to solve it?

---

### Post by Spenzer4Hire on 2007-10-18
I'm on a fresh install of Gutsy and mounting an NFS share in fstab works just fine for me.  Surprisingly, it even works when I connect over Wi-fi, which doesn't connect until after login.  What does your /etc/fstab look like?  You said you can mount once you login, so I'm guessing you have nfs-common installed.

---

### Post by buntunub on 2007-10-18
Hmm.. Sounds like you told the upgrader to overwrite your fstab?

---

### Post by arbulus on 2007-10-18
The line for the mount is still in the fstab.  Here's what it looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=965d8970-a9c5-4788-bf61-6c6312b1ae80 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ffc96b89-8eb2-4a35-a62b-e8ea04ed6ffc /boot           ext3    defaults        0       2
# /dev/sda4
UUID=faaf1d85-15fb-4f0d-91ea-097de6915a74 /home           ext3    defaults        0       2
# /dev/sda3
UUID=b935d3a8-2a44-476e-b44a-5c7f7d07fd41 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#ExternalHD
192.168.1.201:/media/ExternalHD /home/dave/ExternalHD	nfs	rw,hard,intr	0	0
```

The last line is the one for the nfs mount.  To answer spenzer4hire's question: nfs-common is installed.  I've also checked my hosts.deny and hosts.allow files and they are correct.

---

### Post by beermad on 2007-10-20
Same problem on my system. Looks like something's broken somewhere in Gutsy, as it worked perfectly before the upgrade.

As an interim fix, you can stick the following line in /etc/rc.local

mount -a

which will at least make sure your NFS filesystems get mounted.

---

### Post by dibble5504 on 2007-10-20
I thought that I had the same problem, but mine would not mount using "sudo mount -a" either.

I checked the firewall logs on the server and found a load of entries blocking UDP traffic.  I copied the TCP rules for ports 32765-32769 to UDP as well and mounting was fine.  Not sure if Gutsy uses UDP rather than TCP now for these ports???

Paul

---

### Post by arbulus on 2007-10-20
> **dibble5504 said:**
> I thought that I had the same problem, but mine would not mount using "sudo mount -a" either.

I checked the firewall logs on the server and found a load of entries blocking UDP traffic.  I copied the TCP rules for ports 32765-32769 to UDP as well and mounting was fine.  Not sure if Gutsy uses UDP rather than TCP now for these ports???

Paul


How do I do what you did?

---

### Post by arbulus on 2007-10-20
Ok, so I just decided to start fresh and install Gutsy from scratch and everything seems to work fine now.

---

### Post by nix4me on 2007-10-20
Try to reinstall nfs and portmap with synaptic.

nix4me

---

### Post by alef13 on 2008-03-05
Gutsy includes a manpage for nfs explaining many possible ways to set up fstab, etc. It's nfs(5).
From the manual:

Here is an example from an /etc/fstab file for an NFSv3 mount over TCP.

```
server:/usr/local/pub    /pub   nfs    rsize=32768,wsize=32768,timeo=14,intr
```

Here  is an example for an NFSv4 mount over TCP using Kerberos 5 mutual authentication.

```
server:/usr/local/pub    /pub   nfs4   proto=tcp,sec=krb5,hard,intr
```

---

### Post by fragos on 2008-03-06
Works fine for me.  If the systems use DCHP to a router  for a NAT address, that address isn't always the same.  For example my 1st booted desktop always gets 192.168.1.100 but my laptop which also connect to other WiFi networks will attempt to use the last IP it used regardless of which network it was issued from.  If that IP is already in use it will ask for a new IP which will then be it's default to try to connect with the next time.  Check the IP to see if it's different than you expect.

---

