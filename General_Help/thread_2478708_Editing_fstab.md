---
title: "Editing fstab"
date: 2022-09-02
forum: General Help
---

### Post by paulies on 2022-09-02
Hi,

I have 2 Ubuntu machines and created a network share and for days I have tried to mount the share but I never had write privilages after mounting but after days of googling and evetually finding the command that works I can seem to convert to automount with fstab.

The command that works is [HTML]sudo mount -t cifs -o username=paul,password=password,rw,nosuid,uid=1000,iocharset=utf8 //192.168.0.99/usb5 /mnt/usb5[/HTML] if I use this perfect but everything I try in fstab comes up with errors etc. 

Can anybody point me in the right direction please x.

Thanks Paul

---

### Post by TheFu on 2022-09-02
```
sudo mount -t cifs -o username=paul,password=password,rw,nosuid,uid=1000,iocharset=utf8 //192.168.0.99/usb5 /mnt/usb5
```
becomes
```
//192.168.0.99/usb5   /mnt/usb5  cifs    username=paul,password=password,rw,nosuid,uid=1000,iocharset=utf8    0   0 
```
for use in the fstab file.

Use **sudoedit** to edit almost any system file, except the sudoers or passwd. Those two files have special commands (look them up) which validate syntax before saving.

BTW, putting credientials into the fstab is poor security.  There is an option to specify a credentials file which can be read by the systemd-mount process (because it runs as root).

credentials=/etc/usb5-credentials would be an example.  Then put the credentials into that file:
```
username=xxxxxxx
password=yyyyyyyyyyyyyy534%#$#@45432%$
```
Then run 
```
sudo chown root:root /etc/usb5-credentials 
sudo chmod 700 /etc/usb5-credentials 
```
To prevent normal users from ready the logins.

If you are doing storage sharing between Unix systems or a NAS, CIFS is a poor choice. Use NFS instead. There are many reasons, but mainly because NFS is system-to-system, not username-to-system.

BTW, you may not want to mount the storage under /mnt/ either.  That location is for temporary administrative use according to the Linux File System Hierarchy Standards.  Google will find that document easily.

---

### Post by paulies on 2022-09-03
> **TheFu said:**
> ```
sudo mount -t cifs -o username=paul,password=password,rw,nosuid,uid=1000,iocharset=utf8 //192.168.0.99/usb5 /mnt/usb5
```
becomes
```
//192.168.0.99/usb5   /mnt/usb5  cifs    username=paul,password=password,rw,nosuid,uid=1000,iocharset=utf8    0   0 
```
for use in the fstab file.

Use **sudoedit** to edit almost any system file, except the sudoers or passwd. Those two files have special commands (look them up) which validate syntax before saving.

BTW, putting credientials into the fstab is poor security.  There is an option to specify a credentials file which can be read by the systemd-mount process (because it runs as root).

credentials=/etc/usb5-credentials would be an example.  Then put the credentials into that file:
```
username=xxxxxxx
password=yyyyyyyyyyyyyy534%#$#@45432%$
```
Then run 
```
sudo chown root:root /etc/usb5-credentials 
sudo chmod 700 /etc/usb5-credentials 
```
To prevent normal users from ready the logins.

If you are doing storage sharing between Unix systems or a NAS, CIFS is a poor choice. Use NFS instead. There are many reasons, but mainly because NFS is system-to-system, not username-to-system.

BTW, you may not want to mount the storage under /mnt/ either.  That location is for temporary administrative use according to the Linux File System Hierarchy Standards.  Google will find that document easily.

Thankyou very much for the reply and helpng me fix my problem and improving on it to, Im pretty new to Linux and when googling things they come up with a way of getting things to work even if not the correct way and the /mnt i never knew but have corrected it :)

Thankyou

---

### Post by paulies on 2022-09-03
Just to add I've just rebooted and the drive doesnt mount but I get no errors when saving the file if I   mount -a it works.

Got to be something simple.

---

### Post by TheFu on 2022-09-03
> **paulies said:**
> Just to add I've just rebooted and the drive doesnt mount but I get no errors when saving the file if I   mount -a it works.

Got to be something simple.

I don't use the fstab for network storage. I use autofs NFS, CIFS and all USB connected devices, since they aren't always connected. There are other reasons.
Have you looked through the mount options available in the fstab, mount, and mount.cifs manpages?  Learning to use manpages is a basic skill.

---

