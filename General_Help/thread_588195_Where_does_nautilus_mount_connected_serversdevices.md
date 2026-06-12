---
title: "Where does nautilus mount connected servers/devices"
date: 2007-10-23
forum: General Help
---

### Post by houchin on 2007-10-23
Hi,

Where does Nautilus mount servers and devices that it shows as icons on the desktop. I was able to "connect to server" and mount an SMB share, which Natilus shows as a path "smb://..."

However, those paths don't work in typical command line apps in the shell. I need the actual path in the file system where I can access that mounted data.

---

### Post by thelinuxguy on 2007-10-23
For devices ... /media ??
Edit: Oopz .. Seems like I got the question wrong...

---

### Post by js_fr on 2007-10-23
I don't think that shares you access via "smb://..." are mounted. It's just an URL like " http://..." or "ftp://..."
Nevertheless, you can get a list of all mounted SMB volumes with ```
sudo mount -l | grep smbfs
``` You can mount smb volumes with "smbmount ..." or "mount -t smbfs ..."

---

### Post by mahousaru on 2007-10-23
By any chance are you trying to save using Thunderbird and FF?  I had the same issue too and it was bleeping annoying.  If you have more then one network share you might be interested in my script.

To get around the issue I mount all my network shares using a script under: 

/home/mahousaru/network

I use a script coz I mount more then one share and I don't like saving my passwords in a text file.

Just add or remove the following line as you wish to accommodate your shares in the main code below.

```

mount -t cifs //$SMBSERVER/mahousaru $MNTPATH/mahousaru -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8

```

Change SMBUSERNAM, SMBSERVER  and MNTPATH to match your own details.  

Run the script with 

sudo scriptname.sh

Make sure that you have created the directories where you want to mount your shares, I guess I could have added a check to see if they exist and create them, but I'm too lasy :p    


```

#!/bin/bash
                                                                                                                             
SMBUSERNAME=mahousaru                                                                                                         
SMBSERVER=server01                                                                                                           
MNTPATH="/home/mahousaru/network"                                                                                                                             

function pause(){                                                                                                            
   read -p "$*"                                                                                                              
}                                                                                                                            
                                                                                                                             
echo -n "Enter password for user $SMBUSERNAME to access server $SMBSERVER > "                                                 
read -s SMBPASSWD                                                                                                            
                                                                                                                             
mount -t cifs //$SMBSERVER/mahousaru $MNTPATH/mahousaru -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8
mount -t cifs //$SMBSERVER/multimedia $MNTPATH/multimedia -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8
mount -t cifs //$SMBSERVER/scratch $MNTPATH/scratch -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8
mount -t cifs //$SMBSERVER/srv $MNTPATH/srv -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8
mount -t cifs //$SMBSERVER/download $MNTPATH/download -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8
mount -t cifs //$SMBSERVER/media $MNTPATH/media -o username=$SMBUSERNAME,password=$SMBPASSWD,uid=$SMBUSERNAME,gid=$SMBUSERNAME,file_mode=0640,dir_mode=0750,iocharset=utf8

echo
echo "Shares mounted:"
echo
echo                                                                                                                         
mount | grep $SMBSERVER                                                                                                      
echo                                                                                                                         
                                                                                                                             
pause 'Press any key to continue''
```

---

### Post by dwanders on 2008-05-07
When I try your command, I get:

mount: wrong fs type, bad option, bad superblock on //$SMBSERVER/SHARE,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

danderso@PC095:/mnt$ dmesg | tail
[ 1377.220508] sd 5:0:0:0: [sdb] Write Protect is off
[ 1377.220514] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1377.220517] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1377.220523]  sdb: sdb1
[ 1377.270838] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 1377.270897] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 9941.306590] audit(1210184514.402:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=13756 profile="/usr/sbin/cupsd" namespace="default"
[13212.482881] audit(1210187788.766:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=14611 profile="/usr/sbin/cupsd" namespace="default"
[16687.640263] CIFS: Unknown mount option isocharset
[16687.640272]  CIFS VFS: cifs_mount failed w/return code = -22

---

### Post by dwanders on 2008-05-07
OOps sorry - needed apt-get install smbfs

its all better now :lolflag:

---

