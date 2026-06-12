---
title: "Permanently mounting NAS share"
date: 2015-10-17
forum: General Help
---

### Post by Calvin_Scott on 2015-10-17
Hello,

I have a WD MyCloud NAS with ~3TB of data on it that I would really like to back up. My backup solution doesn't work directly with the MyCloud so I installed it on an Ubuntu computer, which should allow me to mount the network drive, map it to the filesystem as a folder and back it up that way. Ideally it would still be mounted as such after restarting said Ubuntu computer. 

I attempted to follow the instructions at [http://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04](http://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04) but in the Connect to Server dialog I got the message "this file server type is not recognized" when trying to mount as an nfs share, even after running sudo apt-get install nfs-common.

On browsing the network, I can see the NAS and it seems to work (albeit slowly, but I have no idea what kind of performance I should expect) but in properties it says it's mounted as an AFP share (I may have done that, it's not the first time I've tried to connect to this particular NAS and I don't perfectly recall everything I did last time).

What am I doing wrong, and how do I get this fairly important data backed up properly?




Also where are the forum post guidelines? I assume they exist but they're not stickied. Let me know if I missed any relevant information. Thanks!

(Unrelated: Why is Network Attached Storage a suggested tag when it's too long for the 18-character tag limit?)

---

### Post by steeldriver on 2015-10-17
I think only very recent versions of gvfs support NFS mounts via the file manager --> [https://mail.gnome.org/archives/gvfs-list/2015-March/msg00000.html](https://mail.gnome.org/archives/gvfs-list/2015-March/msg00000.html)

To use the more traditional mount mechanism, you would first need to check that an NFS filesystem is in fact being exported e.g.

```

showmount -e <address of NAS>

```

(if it's a Windows-targeted product, it may only provide SAMBA/CIFS and AFP connectivity by default); then either mount it temporarily using something like

```

sudo mount -t nfs <address of NAS>:/<share name>/ /mnt

```

or persistently by adding an equivalent entry to your /etc/fstab file

---

### Post by Devon_suz on 2015-11-02
Ubuntu 15.10 The share mounted fine using files but when I tried to use the above suggestion

I put the proper internal ipaddress in place of <ipaddress> I also tried the name of the NAS which I put in /etc/hosts, I also tried adding username= <my username> and password=<password> ( which it really hated)

sudo mount -t nfs <ipaddress>:/volume1/Data /mnt/nas 
mount.nfs: access denied by server while mounting <ipaddress>:/volume1/Data
ls -ls of /mnt is:
drwxr-xr-x 3 root root 4096 Nov 2 23:04 nas

I tried mounting it in /etc/fstab
//<nas name lowercase>/<sharename/ /mnt/nas cifs credentials=/home/<myhome>identials,iocharset=utf8,sec=ntlm 0

I also tried putting the IP address instead of the name

sudo mount -a
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

mount .cifs states 
       credentials=filename
           specifies a file that contains a username and/or password and optionally the name of the workgroup.
           The format of the file is:


                         username=value
                         password=value
                         domain=value


           This is preferred over having passwords in plaintext in a shared file, such as /etc/fstab. Be sure
           to protect any credentials file properly.

---

