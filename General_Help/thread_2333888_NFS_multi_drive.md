---
title: "NFS multi drive ?"
date: 2016-08-14
forum: General Help
---

### Post by ssmith2 on 2016-08-14
I have recently finished my NFS setup and it has been working so well that I ran out of space (1TB) .  That's not really a problem because I was prepared for it. Its because I'm moving everything off my Windows infrastructure so I can fully migrate to Ubuntu. 

I have put a USB hard drive on the server with an extra 1.5 TB of space and mounted it in a folder on the share.  So my set up is like this

I have shared out a folder from the ubuntu server using NFS called /Shares.

Inside /Shares I have many folders but one of them is called  /Shares/Video/TV Shows (can you guess what's on it ;) ) and that mounts to /dev/sdb1

When I'm using Files or on the terminal directly on the server and browse to /Shares/Video/TV Shows it gives me /dev/sdb1 without a problem however when I use another computer and go to it using NFS, I get the mount directory itself instead of the drive mounted on the directory.

Its probably something very simple that I'm doing wrong.

Does anyone have any advice?

Here's my fstab and exports to show what I mean

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=74f35fcd-ea46-4923-8671-d74f374b2538 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/sdb1 /Shares/Videos/TV\040Shows auto nosuid,nodev,nofail,x-gvfs-show 0 0



and here is my /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/Shares	*(rw)

---

### Post by ssmith2 on 2016-08-14
got it!

the answer was this:

[COLOR=#000000]fstab
[/COLOR]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=74f35fcd-ea46-4923-8671-d74f374b2538 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/sdb1 /Shares/Videos/Shows auto nosuid,nodev,nofail,x-gvfs-show 0 0





[COLOR=#000000]/etc/exports[/COLOR]
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/Shares	*(rw,sync,no_root_squash,subtree_check)
/Shares/Videos/Shows *(rw,sync,no_root_squash,subtree_check)

---

### Post by yancek on 2016-08-14
Your entry in /etc/exports for Share isn't correct and won't do anything.  If you want it to be available on your local network, you can modify the example below to suit your needs changing the IP is that is not what you use and the parameters in parenthesis based on what you need.  Make sure you run exportfs after making the change.

> /mnt/data 192.168.0.0/24(no_root_squash,sync,secure,no_subtree_check,rw) 


---

