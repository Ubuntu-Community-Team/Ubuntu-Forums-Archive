---
title: "Samba Share help"
date: 2014-03-31
forum: General Help
---

### Post by Harold_Roberts on 2014-03-31
Somebody Please help me with this. I have been beating my head against the wall trying to figure out why this will not work.

I installed samba and libpam-smbpasswd on my system.  This is my smb.conf file

```
workgroup = ROBERTS
server string = %h server (Samba, Ubuntu)
interfaces = lo eth0
bind interfaces only = true
security = user
map to guest = Bad User
guest account = nobody

[Movie_Collector]
path = /media/hroberts89436/NetworkCon/Movie Collector
# available = yes
read only = no
browseable = yes
# public = yes
# writable = yes
guest ok = yes

[Calibre]
path = /media/hroberts89436/NetworkCon/Calibre
available = yes
read only = no
browseable = yes
public = yes
writable = yes
guest ok = yes
guest only = yes
create mask = 777
directory mask = 777
```

I can see the folders from this ubuntu machine, another ubuntu machine, 2 windows 8, and 1 windows xp machine.  However when I click on the folder I get the following error:

"Failed to mount Windows share: Permission denied"

Can someone please let me know what I am doing wrong here.  Yes these are guest shares.  I don't need them secured I just need access to these folders from other locations.

The permissions on the directories themselves are root:root 777 on one and hroberts89436:hroberts89436 777 on the other.  all of the folders and files inside permissions are hroberts89436:hroberts89436 700

Thanks in advance for anyhelp on this.

---

### Post by Harold_Roberts on 2014-03-31
Ok trying to read and learn things here. I have come across info stating that my fstab file may be the problem.  here is my fstab file for you to see as well

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=dad91f3e-e012-4e9e-98ad-301a954f8244 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=08ed60e1-757f-4f96-9c2a-83672d6df6eb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/disk/by-uuid/11275378-0529-4d95-946d-72b9b0db9038 /media/hroberts89436/HR1 ext4 rw,user,auto,exec,async 0 0
/dev/disk/by-uuid/f2ed82fc-3bec-47d8-a33a-79931b1a71a1 /media/hroberts89436/HR2 ext4 rw,user,auto,exec,async 0 0
/dev/disk/by-uuid/745a7412-c173-452a-b9ad-552da8aa3a11 /media/hroberts89436/HR3 ext4 rw,user,auto,exec,async 0 0
/dev/disk/by-uuid/d38b0253-7d50-4828-a885-aeb6671222bc /media/hroberts89436/Music auto rw,user,auto,exec,async 0 0
/dev/disk/by-uuid/a1c74ca4-0993-4057-b8e6-11b34753b71a /media/hroberts89436/NetworkCon auto rw,user,auto,exec,async 0 0
/dev/disk/by-id/wwn-0x5000c500141abbdd-part1 /media/hroberts89436/FreeAgent auto rw,user,auto,exec,sync 0 0
/dev/disk/by-id/usb-WDC_WD25_00JB-00GVA0_A344081C8E17-0:0-part1 /media/hroberts89436/HR_USB_2 ntfs rw,user,auto,exec,sync,nofail 0 0
/dev/disk/by-id/usb-WDC_WD25_00JB-00GVA0_F9360783B4FC-0:0-part1 /media/hroberts89436/HR_USB_1 ntfs rw,user,auto,exec,sync,nofail 0 0
/dev/disk/by-uuid/9828DA2728DA0462 /media/hroberts89436/DDrive auto rw,auto,exec,async,user 0 0

```

All of these drives with the exception of Free Agent, and the 2 labeled HR_USB_# are sata or esata drives.

Thanks again for any help

---

### Post by Morbius1 on 2014-03-31
Take a look at the permissions of the parent folder of your mount points:
```
ls -dl /media/hroberts89436
```
It will come back with something that makes no sense:
> drwxr-x---+ 3 root root 4096 Mar 31 07:03 /media/hroberts89436
It appears at first glance that not even hroberts89436 has access to the folder until you notice the "+" at the end. That indicates an ACL is controlling permissions. So find out what the Access Control List permissions are on that folder:
```
getfacl -t /media/hroberts89436
```
You should see that aside from root the only person gaining access to that folder and anything beyond it is hroberts89436. Since the remote user is not hroberts89436 you will get a "Failed to mount Windows share: Permission denied" error.

**** That directory and it's permissions are created and controlled by the system automatically so the simplest thing to do in this case since all your shares allow guest access is to make the guest user appear to be hroberts89436 - [COLOR=#0000cd]*for those shares*[/COLOR]. For example:
> [Movie_Collector]
path = /media/hroberts89436/NetworkCon/Movie Collector
# available = yes
read only = no
browseable = yes
# public = yes
# writable = yes
[COLOR=#0000cd]**force user = hroberts89436**[/COLOR]
guest ok = yes
Then restart smbd.

 **** Another alternative is to change the mount point to one level up from where it is now. So instead of:
**/media/hroberts89436/NetworkCon**
Have it mount to:
**/media/NetworkCon**

Then change the paths to all your shares in smb.conf.

---

### Post by Harold_Roberts on 2014-03-31
Thank you very much 

I fixed my mount points.  Thats better. didn't like it the other way anyways. I used the force user option on my calibre share.  that works now, but the other share does not work.  Instead of using the force user option could you tell me what the proper way to do things would be for these.  This im sure will help me with my LPIC Level 1 exam as well.

Again thanks for pointing me in the right direction

---

### Post by Morbius1 on 2014-03-31
*** I don't know what "the other share does not work" means.

*** I don't know what the word "proper" means in this context but given the requirements:
> The permissions on the directories themselves are root:root 777 on one  and hroberts89436:hroberts89436 777 on the other.  all of the folders  and files inside permissions are hroberts89436:hroberts89436 700
And anonymous guest write access choices are limited and they both entail the guest appearing to be hroberts89436. You can do this in your share definitions explicitly:
```
force user = hroberts89436
```
Or implicitly:
```
guest ok = no
valid users = hroberts89436
```
The latter would require all your clients to pass your credentials to access your share and it's contents.

---

### Post by Harold_Roberts on 2014-03-31
That makes sense.  I guess what I am trying to learn is, can I change the permissions on all folders, files, and even the drive itself, to make using the force user option no longer necessary?

---

### Post by Morbius1 on 2014-03-31
Anything is possible if you dig deep enough.

If the goal is to maintain a credetial-less guest share you can go 

from one extreme: Rely on the default samba guest user account and set ownership of the shared folder and everything in it to that guest user. You will have to uninstall libpam-smbpass , remove any users you've added to the samba password database, never ever create a share that requires credntials, and make sure all files added to that share are through Samba. 

To the other extreme: Use bindfs to take absolute control of the shared folders permissions such that anyone accessing the shared folder will have access to everything in the shared folder. At that point no one can change permissions. Not you. Not Samba. Not even root.

And no doubt a few things in between those two extremes.

---

### Post by Harold_Roberts on 2014-04-04
Morbius1.

Thank you very much for your help in understanding samba shares.

---

