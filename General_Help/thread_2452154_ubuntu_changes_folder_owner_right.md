---
title: "ubuntu changes folder owner right"
date: 2020-10-17
forum: General Help
---

### Post by alain.roger on 2020-10-17
Hi,

i have a weird behavior on my laptop. e.g. i created mounted points in /mnt using:
```

sudo mkdir /mnt/nas
sudo chown alain:users /mnt/nas
```

Next i mount the NAS shared folder to /mnt/nas and it works great.

After a random time, ubuntu changes /mnt/nas owner rights to 'root' and therefore my shared folder is not available anymore.

How is it possible ? What is the reason ?

thx

---

### Post by Morbius1 on 2020-10-17
A mount always replaces the permissions of the mount point with whatever the permissions are on the thing being mounted.

If it was an ext4 partition for example whatever the permissions are on the partition before it's mounted will replace the permissions of the mount point after the mount.

A CIFS mount on the other hand always replaces the mount point permissions with root after the mount. Easily fixed if this is the case.

In either case it is not at some random time it is immediate.

---

### Post by alain.roger on 2020-10-17
I use NFS as CIFS stopped to work :( since upgrade to 20.04. I used CIFS for 4 years now without having this issue with another nas, but with QNAP i do not know why it does not work, so i use NFS.
with CIFS i used to have in fstab:
```
 //QNAP/Homes/alain     /mnt/qnap        cifs vers=2.1,x-systemd.automount,x-systemd.device-timeout=60,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```
I mount shared directories at boot with fstab, so how can i fix owners rights after mounting the shared folders if owner is changed to root:root ?
i do not want to manually run sudo chown alain:alain /mnt/qnap

---

### Post by Morbius1 on 2020-10-17
I truly do not understand your post.

You say you no longer use CIFS but your mount in fstab is using CIFS.

In any event that line in fstab will mount with owner = whoever uid=1000 is and I'm assuming that is you and with group = users. It would be better if you were to add the nounix option to your list however since you are specifying file_mode / dir_mode:
```
 //QNAP/Homes/alain     /mnt/qnap        cifs vers=2.1,x-systemd.automount,x-systemd.device-timeout=60,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,nounix,file_mode=0775,dir_mode=0775 0 0
```

And you can't run **sudo chown alain:alain /mnt/qnap **on an cifs mount after it is mounted. It will have no affect. If it does the share is not mounted.

---

### Post by alain.roger on 2020-10-17
I just wrote down, how i mounted previously using CIFS in /etc/fstab. But I had some issues with /mnt owner rights. So i decided to try NFS as:

QNAP:/Homes/alain        /mnt/qnap                   nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

---

### Post by Morbius1 on 2020-10-17
My suggestion is to edit the title of your original post and add "NFS" so the people who know it can answer it.

The last time I used NFS Eisenhower was still a cadet at West Point.  I'm guessing it has changed a bit since then.

---

### Post by alain.roger on 2020-10-18
I just would like to understand something. I learnt that SMB/CIFS are mainly used when server/client are a mix of WIndow and Linux and NFS is used for Linux/Linux (server/client).
So why are you not using anymore NFS ? What's wrong with NFS (except low security AFAIK)

---

### Post by Morbius1 on 2020-10-18
The little corner of the asylum that I'm responsible for is mostly MacOS and Linux with a couple of Win10 boxes for extra spice.

Windows uses SMB. MacOS has used their own home grown version of samba by default since Mavericks ( 2013 ? ). Linux has the samba client - or  at least a samba client library - installed by default and CIFS is embedded in the Linux kernel. It's the only thing all of these OS's have in common.

None of that makes Samba better or faster or sexier than NFS or SFTP or any other protocol. It's just what I am used to using.  

If you are using NFS it would help your cause to mention that in your title so that the NFS experts can assist you. I'm not one of them.

---

