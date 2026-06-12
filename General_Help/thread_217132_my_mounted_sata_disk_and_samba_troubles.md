---
title: "my mounted sata disk and samba troubles"
date: 2006-07-16
forum: General Help
---

### Post by OrganicPanda on 2006-07-16
hey all, this strikes me as a weird problem, i set up my sata partition to mount as follows: (its /dev/sda2)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       			<dump>  <pass>
proc            /proc           proc    defaults        			0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 		0       1
/dev/sda2       /files     	vfat    defaults,utf8,umask=000	 	0       0
/dev/sda1       /footage        ntfs    defaults,nls=utf8,umask=007,gid=46 	0       1
/dev/hdb2       /ubuntu510      ext3    defaults        			0       2
/dev/hdb1       /windowsxp      ntfs    defaults,nls=utf8,umask=007,gid=46 	0       1
/dev/hdb3       none            swap    sw              			0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     			0       0

```

and i have my samba shares going a bit like this: (i refer to public as the first share and files as the second)

```

[public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[files]
  comment = Files
  path = /home/files
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

```

and those two share fine, no problems untill i change my /dev/sda2 (files) sata partition from:

```

/dev/sda2 /files vfat   etc ...

```to:```

/dev/sda2 /home/files vfat   etc ...

```
in fstab so that it will mount all my files into /home/files and then in turn will be shared through samba, sadly this is not the case, when i do this the first share works still but /home/files is not accesible, whats the deal with that?

if anybody can shed light on this situation i would be very happy, 
cheers all,
panda

---

### Post by OrganicPanda on 2006-07-18
so nobody can tell me why i cant mount a partition and then share it via samba, this situation cant be specific to me

regards, panda

---

### Post by RojCowles on 2006-08-14
> **OrganicPanda said:**
> so nobody can tell me why i cant mount a partition and then share it via samba, this situation cant be specific to me

regards, panda

I know its bad etiquette to say "Me Too" but ... me too :(

I think it must be a more common issue as I found another reference to it on the linux.samba newsgroup from a Fedora Core 4 user and I have the problem on my FC5 box.

The symptoms are if I mount a SATA partition to a directory that I'm sharing using Samba then that share becomes unshareable from Windows or Linux boxes, i.e. /smbshare is the mount point for the SATA drive and I have an [smbshare] in my smb.conf file.

umount /smbshare # unmount SATA partition so /smbshare is an empty directory on my IDE drive

mount -v -t cifs -o user=<user> server002:/smbshare /mnt/server002/samba
password:*******

# mount successful
umount /mnt/server002/samba

mount /smbshare # mount partition from SATA drive
mount -v -t cifs -o user=<user> server002:/smbshare /mnt/server002/samba
password:*******
Can' find path //server002/smbshare trying upper case
can't find path //SERVER002/SMBSHARE
mount error 6 = ...

I get a similar path not found/permission denied error trying to map these Samba shares from my Windows XP box. 

Nothing much in the log files, other than some Permission Denied messages, though I do see an odd Permission Denied for the machine specific /usr/local/samba/var/%m.log files, which is odd as the smb daemons are running as root and the directory has 777 permisions so there shouldn't be any usual file access issues.

Heres what I think are the relevant details about my box

Mobo/CPU: PC Chips M789 + 800MHz Via C3
SATA controller: Syba 2 port SATA 150 controller, Silicon Image 3512 chipset
IDE HD: 40Gb Maxtor
SATA HD: 250Gb Western Digital RE16 SATA II

OS: Fedora Core 5, Kernel 2.6 latest kernel as of yesterday
Samba: 3.0.23 (I think)

My plan is to crank up the Samba logging level and try to connect a few more times, hopefully getting something enlightening in the /var/log/messages or /var/log/samba/*.log logs, then try some of the other troubleshooting tips I've seen. If nothing I'll try signing up to the Samba mailing list and see if I can find anything in the archives or start pestering the real Samba gurus.

Sound like a plan ?

--
Roj

---

### Post by OrganicPanda on 2006-08-16
Ok I fixed my problem by randomly copying someone elses smb.conf file and adapting it to my machine, it works like a treat, here it is:

```

[global]
    ; General server settings
    netbios name = ubuntu_desktop
    server string =
    workgroup = workgroup
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[dvd]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes

[files]
    path = /files
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = panda
    force group = panda

[footage]
    path = /footage
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = panda
    force group = panda

```

Ok so the 'files' share is on my sata drive but mounted at /files in fstab with:

```

/dev/sda2       /files     	vfat    defaults,utf8,umask=000	 	0       0

```

I also had to add panda from group panda to the samba users list but to be honest I cant remember the command for doing that, hope some of this is useful to you as it fixed my problem.

---

### Post by RojCowles on 2006-08-18
Fixed mine too. Fedora Core 5 has the SELinix (Security Enhanced ?) Linux package installed. Read about it on another forum and just had to configure SELinux not to protect the SMBD and NMBD daemons and I was able to mount/map the Samba partitions for my SATA drive locally and on my Win XP box without a problem.

--
Roj

---

