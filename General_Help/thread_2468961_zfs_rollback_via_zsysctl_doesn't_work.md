---
title: "zfs rollback via zsysctl doesn't work"
date: 2021-11-15
forum: General Help
---

### Post by netwizard.x1 on 2021-11-15
Hello,

I am having problems restoring the snapshot via zsysctl under Ubuntu 21.10. In the issue below I used VMWare, however the problem occurs with every system of mine.
Here I create the snapshot (in german language):
```
user1@vm-07m-ubuntu-2110:~$ zsysctl state save --system -v test1
INFO Anforderung zur Speicherung des aktuellen Systemzustands "test1" 
ZSys fügt automatischen System-Snapshot dem GRUB Menü hinzu
Erfolgreich als "test1" gespeichert
```
```
user1@vm-07m-ubuntu-2110:~$ zsysctl machine show
Name:              rpool/ROOT/ubuntu_px2utz
ZSys:              true
Zuletzt verwendet: aktuell
Verlauf:           
  &#8211; Name:          rpool/ROOT/ubuntu_px2utz@test1
    Erstellt am:   2021-11-10 13:50:18
  &#8211; Name:          rpool/ROOT/ubuntu_px2utz@autozsys_565uhj
    Erstellt am:   2021-11-09 19:57:04
  &#8211; Name:          rpool/ROOT/ubuntu_px2utz@autozsys_exv69c
    Erstellt am:   2021-11-09 19:44:22
Benutzer:
  &#8211; Name:    user1
    Verlauf: 
     - rpool/USERDATA/user1_90dcck@test1 (2021-11-10 13:50:18)
     - rpool/USERDATA/user1_90dcck@autozsys_zapnei (2021-11-09 20:03:27)
     - rpool/USERDATA/user1_90dcck@autozsys_exv69c (2021-11-09 19:44:23)
     - rpool/USERDATA/user1_90dcck@autozsys_sunsgu (2021-11-09 19:42:27)
  &#8211; Name:    root
    Verlauf: 
     - rpool/USERDATA/root_90dcck@test1 (2021-11-10 13:50:18)
     - rpool/USERDATA/root_90dcck@autozsys_exv69c (2021-11-09 19:44:23)
```
After reboot, strangely enough, the first time I don't manage to get into the grub menu and then get stuck entering the password for zfs encryption (but I don't think this has anything to do with the problem, but I wanted to mention it), but then on second reboot I put in grub about "History for Ubuntu 21.10 / Reset to test1 on 10.11.2021 @ 13:50 / Reset system and user data". But after that I now get the following message:

```
You are in emergeny mode. After logging in, type "jounalctl" -xb" to view system logs, "systemctl reboot" to reboot, "systemctl default" or "exit" to boot into default mode.
Drücken Sie die Eingabetaste für Wartungsarbeiten (oder drücken Sie Strg+D, um fortzufahren):
```
The journal shows this error (in german language):
```
zfs-mount-generator failed and you requested a revert:
level=error msg="Konnte Hochfahren nicht sicherstellen: Eingehängter Klon-BootFS-Datensatz, der von initramfs erstellt wurde, hat kein gültiges _suffix (mindestens .*_<onechar>): \"rpool/ROOT/iubuntu_\""
You can reboot on current master dataset to fix the issue
/usr/lib/systemd/system-generators/zfs-mount-generator failed with exit status 1.
```
If I then restart the computer, I can boot Ubuntu 21.10 normally again and the system runs (unresetted) without problems. If I try again to reset the old snapshot via grub I get the following message
```
Command: /sbin/zfs clone -o canmount=noauto -i com.ubuntu.zsys:bootfs=yes -o mountpoint=/ rpool/ROOT/ubuntu_px2utz@test1 rpool/ROOT/ubuntu_
Message: cannot create 'rpool/ROOT/ubuntu_': dataswet already exists
Error: 1
Failed to clone snapshot.
Make sure that the any problems are corrected and then make sure that the dataset 'rpool/ROOT/ubuntu_' exists and is bootable.

BusyBox v1.30.1 (Ubuntu 1:1.30.1-6ubuntu3) build-in shell (ash)
Enter 'help' for a list of build-in commands
(initramfs)
```
I have found the following bug. However, the suggested change in the code does not bring any improvement for me. 
[https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1894329?comments=all](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1894329?comments=all)

Does anyone see the same issue when rollback the zfs snapshot ?

BR

---

### Post by ActionParsnip on 2021-11-15
If you have VMWare then why not snapshot from there? Waaay easier

---

### Post by netwizard.x1 on 2021-11-15
I used VMWare in order to reproduced in in different ways, because when the issue on a real system happened I had to reinstall Ubuntu allover again.

---

