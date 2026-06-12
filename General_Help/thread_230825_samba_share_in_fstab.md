---
title: "samba share in fstab"
date: 2006-08-06
forum: General Help
---

### Post by involutaryhaxor on 2006-08-06
Here's what I want to do:

I want to add a samba share into my /etc/fstab so that every single time I start up my system, I have the share mounted. 

I have no clue what I am doing so if you could, I would need step by step details, what I need to apt-get and the whole bit, i am already able to get to the share by the network places thing.

the share is at "\\192.168.0.3\webserver" 
let's say the user is "user"
and the pass is "pass"
and I want to mount it at "/webserver"
and be able to have all users read and write to it

thanks in advance

---

### Post by fourchannel on 2006-08-06
This took me a while to figure out but here's how I setup mine.

Your /etc/fstab file is world readable so you do not want to put a password in there. instead you could do a setup like this.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
//lmwire/limewire       /mnt/network/lmwire_smb smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
``` 
I have a samba share on my LimeWire computer (its a family comp where anyone can download stuff), that I mount at boot time. but notice that in the options in fstab use a "credentials=/root/.smbcredentials" file. That file is readable only by root and holds the username and password.

the /root/.smbcredentials file:
```
username=name
password=pass
``` 
after creating the .smbcredentials make sure to protect the files, by running these commands. ```
sudo chown root:root /root/.smbcredentials
sudo chmod 0600 /root/.smbcredentials
``` 
If you can already browse network shares then you already have the required installed software (I think). If not you need to ```
sudo apt-get install samba-common
``` 
and one final thing....
init mounts your network shares *directly* after your interfaces come up. and sometimes the script has finished but the actual network cards is still initializing. So usually about 50% of the time i started my computer, my samba share failed to mount "no route to host" it would say.

So then you need to open up "/etc/init.d/mountntfs.sh"
```
sudo gedit /etc/init.d/mountnfs.sh
``` see where I added the line "sleep 4" in my script. This has worked wonders to ensure that it mounts 100% of the time.
```
#
# mountnfs.sh   Now that TCP/IP is configured, mount the NFS file
#               systems in /etc/fstab if needed. If possible,
#               start the portmapper before mounting (this is needed for
#               Linux 2.1.x and up).
#
#               Also mounts SMB filesystems now, so the name of
#               this script is getting increasingly inaccurate.
#
# Version:      @(#)mountnfs.sh  2.86-5  10-Sep-2004  miquels@cistron.nl
#

####### to give eth0 a chance to warm up :)
sleep 4
``` 
and then you should be rockin out with some auto mounting samba shares. =D

---

