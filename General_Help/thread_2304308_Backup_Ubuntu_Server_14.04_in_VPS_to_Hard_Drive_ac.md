---
title: "Backup Ubuntu Server 14.04 in VPS to Hard Drive accesible thru FTP or SSH"
date: 2015-11-25
forum: General Help
---

### Post by Javierhermosa on 2015-11-25
Hi everyone! 

I have searched the forums but I don't seem to find something that really helps me.

I have a 500GB VPS running my company's E-Mail server, Wordpress webpage and owncloud.

Now that everything is up and running, and most important, stable, I would like to start backing it up regularly. 

At home I have an RT-N65U Router running Padavan's firmware with a 4TB Hard Drive attached to it on the USB3 Port. Thanks to this firmware I can connect from the outside world to it using DDNS over protocols FTP and/or SSH.

Now since 4TB is completely overkill (I got the hard drive very cheap), I would like to use this hard drive for backups of the VPS. I was wondering if this is actually possible and secure. 

I have read of rsync and bacula but:

- rsync seems to be oriented for LAN configurations.
- Bacula requires the Client to be running on the Backup storage side, while the server is on the server to be backed up. Although the firmware allows for Entware and it's linux based, I don't think the RT-N65U has the power to be able to run bacula client.

Has anyone experience with this, or is the idea just plainly impossible?

Thanks to everyone for your input!

---

### Post by DigiAngel on 2015-11-25
I backup via rsync/ssh with the below:

rsync -avzAXtE --delete --exclude=/etc/fstab --exclude=/boot --exclude=/opt/bin/termsetup --exclude=/media --exclude=/dev --exclude=/proc --exclude=/sys --exclude=/mnt --exclude=/var/run --exclude=/run --exclude=/tmp --exclude=/etc/udev/rules.d --exclude=/home --exclude=/lib/firmware --exclude=/lib/modules --exclude=/lib/recovery-mode / me@192.168.1.239:/

that should get you started.

---

### Post by mastablasta on 2015-11-26
try rdiff-backup as well.

server / client is also meant as software. you are looking for a push solution that would push data from your server to external drive on router.

---

### Post by TheFu on 2015-11-26
FTP is never secure and should be avoided, even on a LAN. Websearch "stop using ftp" for why.
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

I use rdiff-backup too. It is important to "pull" backups from untrusted systems like a VPS for security reasons. Use key-based authentication for all internet connections, never passwords.  Versioned backups are very important. 

Don't know anything about that router, except to be very careful allowing external storage access for router-connected storage. There have been many, many, many security flaws with similar devices.

---

### Post by Javierhermosa on 2015-11-27
Ok guys, thanks for the input. I have immediately deactivated FTP access from the external world on my router.

I will connect using SFTP only, and will try rdiff-backup :)

I will let you know how it went! 

Oh by the way, I forgot to mention I can also install a VPN server and/or a client on my router. Would that be safer maybe? 

Thank you!!

> **DigiAngel said:**
> I backup via rsync/ssh with the below:

rsync -avzAXtE --delete --exclude=/etc/fstab --exclude=/boot --exclude=/opt/bin/termsetup --exclude=/media --exclude=/dev --exclude=/proc --exclude=/sys --exclude=/mnt --exclude=/var/run --exclude=/run --exclude=/tmp --exclude=/etc/udev/rules.d --exclude=/home --exclude=/lib/firmware --exclude=/lib/modules --exclude=/lib/recovery-mode / me@192.168.1.239:/

that should get you started.

But why would you exclude so many directories? My objective is to be able to restore "the image" back to the VPS and have it in the same state it was when I made the backup... Would that work?

Thanks for your reply :)

---

### Post by TheFu on 2015-11-27
That rsync command could be very dangerous, depending on the remote device.  Review the options and inputs carefully, especially the target location. Certain directories are created only at runtime. Those need to be ignored. It appears the goal for that rsync command is to backup specific things, not everything.

I stopped doing full backups many years ago. Why backup extra 4G of an OS when a new install only takes 15 minutes? Why waste the storage and restore time? Plus image-based backups cannot be efficiently versioned. Versioning is critical to effective backups.  I do image Windows - there isn't any other choice, but with Linux, it isn't necessary. If you want an image, lots of tools do that. dd, ddrescue, partimage, clonezilla, fsarchiver, plus many commercial options. I tend to use rsync for a 1-time "mirror" when moving a system from 1-disk to another, then manually run grub-install and update-grub to make a system that boots. I would not exclude the same directories as shown above, in that situation.

---

