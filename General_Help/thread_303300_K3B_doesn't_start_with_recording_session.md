---
title: "K3B doesn't start with recording session"
date: 2006-11-20
forum: General Help
---

### Post by Manny73 on 2006-11-20
I'm using Ubuntu 6.06 without any problems expect recodring a CD.

After starting K3B an error message is displayed:
> cdrecord = 2.6.8
Since Linux kernel 2.6.8 cdrecord *Solution*: Use K3bsetup to solve this Problem

I try to run K3bsetup using root privileges but the setup tool doesn't start:
> WARNING: Could not find module 'k3bsetup2'

> ls -l /dev/hdd ->
brw-rw-rw- 1 root cdrom 22, 64 2006-10-25 12:25 /dev/hdd 

> -rwxrwxrwx  1 root   root      31128 2004-08-13 10:17 cdparanoia
-rwxrwxrwx  1 root   cdrom       133 2006-04-12 09:32 cdrecord

My user account is a member of the group **cdrom**.

Are there any suggestions how to solve my problem.

---

### Post by DigitalAxis on 2006-11-20
Just checked my system; try running k3bsetup instead.  I guess someone removed the '2'

---

### Post by Manny73 on 2006-11-20
> **DigitalAxis said:**
> Just checked my system; try running k3bsetup instead.  I guess someone removed the '2'
I run k3bsetup but it tries to start k3bsetup2.

---

### Post by DigitalAxis on 2006-11-20
I wonder... copy and paste this into some kind of command line:

gksu kcmshell k3bsetup2

---

### Post by DigitalAxis on 2006-11-20
Or... it may even be a menu entry in Gnome, perhaps something you could even get to from k3b itself?

---

### Post by Manny73 on 2006-11-20
At the moment I'm not in front of my computer. I'll try it later today and get back with the result.

---

### Post by Manny73 on 2006-11-21
I tried to run
> sudo gksu kcmshell k3bsetup2 and received the following output:

> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kcmshell (kdelibs): WARNING: Could not find module 'k3bsetup2'.


---

### Post by Manny73 on 2006-11-22
No suggestions how to solve my problem?

---

### Post by AdrianoBandeira on 2006-11-29
The is on the device /dev/sg0...
Make the following...

cd /dev
sudo mv sg0 sg0_old
sudo ln -s cdrom sg0


Now you can open the K3B....:)

---

