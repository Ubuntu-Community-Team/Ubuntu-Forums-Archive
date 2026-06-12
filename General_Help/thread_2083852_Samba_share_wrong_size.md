---
title: "Samba share wrong size"
date: 2012-11-13
forum: General Help
---

### Post by Forbees on 2012-11-13
running 12.04, have a RAID-5 with 4TB for holding my files. trying to move 900gigs from my windows machine to the samba share i set up inside the RAID.

i get an error saying it only has enough room for 2gigs. on the ubuntu machine the raid is empty, and checking the folder properties of the share show that it has 4TB free


here's my samba.conf which is pretty much a copypasta from the forums

```

[global]
    ; General server settings
	netbios name = Yuki
	server string = 
	workgroup = WORKGROUP
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

;	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Desktop]
	path = /home/nagato/Desktop
;	writeable = no
;	browseable = yes
	valid users = Forbees

[Public]
	path = /media/ServerData/Public
	writeable = yes
;	browseable = yes
	valid users = Forbees

```

the RAID-5 is mounted in /media/ServerData - automatically done from Gnome Disk Utility, the samba share is set up from the Samba gui in the software center. chmod 0777 on /media/ServerData/Public - where i'm trying to move the files

all i can find on the forum is the same problem and no answer, on google i can only find people trying to use a root path as a share 


tl:dr have 4tb of data for samba - windows only see's 2Gig

---

### Post by dcstar on 2012-11-14
> **Forbees said:**
> running 12.04, have a RAID-5 with 4TB for holding my files. trying to move 900gigs from my windows machine to the samba share i set up inside the RAID.

i get an error saying it only has enough room for 2gigs. on the ubuntu machine the raid is empty, and checking the folder properties of the share show that it has 4TB free
...........
all i can find on the forum is the same problem and no answer, on google **i can only find people trying to use a root path as a share **


tl:dr have 4tb of data for samba - windows only see's 2Gig

Which is because you should **never, ever** use /media for mounts. That is a System Folder for removable and temporary media that the System controls, not you.

Create a separate mount point and then set it up in /etc/fstab so things mount correctly.

---

### Post by madverb on 2012-11-14
Absolute bull. You can use /media to mount your drives. The only reason it might not be a great idea is if you have a drive labelled with the same name as the directory you mount your drive.

What filesystem have you used on the RAID partition? Also, why did you use RAID5? That is a mistake. RAID5 is legacy and you shouldn't use it.

---

### Post by Forbees on 2012-11-18
i didn't chose /media for the mount - Gnome Disk Utility did

i'm using Raid5 because i have 3 2TB drives - before i my last machine failed horribly i was up to 2.5TB of data and i want to stick with some form of redundancy 


i have another 2TB seagate drive i was thinking of using for a RAID10, but i found out the hard way seagate + RAID = fail as soon as plugged in. i've gone through 5 warrenty's with seagate and every drive they've sent me has failed within minutes of rebuilding an Array. check the seagate forums - it's a common problem :-/. 

that being said is the reason i have to start over. while dealing with seagates warranty crap another drive failed so i lost everything except what was on a recently formatted external. i was able to recover 900Gigs off it and need to get it on my RAID 




::frustration face::

i'll try making a folder in /mnt/ to mount it to, i can see how that could be the problem but i'm not convinced yet

---

### Post by Forbees on 2012-11-20
so it WAS /media


remounted in /mnt and everything seems fine. already did an fstab edit so i don't have to worry about Gnome Disk Utility auto mounting it back in /media

---

