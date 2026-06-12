---
title: "GRSYNC Help"
date: 2007-09-19
forum: General Help
---

### Post by strange_cathect on 2007-09-19
Someone asked this question in January, but there was no reply.  I'll try again:

I'm using GRSYNC to make a backup of my /home folder to another hard drive on my machine.  However, I just created a fileserver with samba shares and would like to recover the space on my local machine and do automatic backups to the networked storage.  But GRSYNC doesn't seem to let me backup to anything that is not local.

Is there a solution for this?

---

### Post by tgalati4 on 2007-09-19
There are several ways to do this.

I loaded FUSE which is a type of secure network transfer protocol, then put the following in my /etc/fstab.

sshfs#tgalati4@homeserver:/mnt/hdd5/Lsongs /home/tgalati4/Lsongs fuse rw,nosuid,
nodev,max_read=65536,user=tgalati4 0 0

You have to load FUSE on both machines, then create a local directory to receive the mount (Lsongs, in this case).  So I am creating a local mount point to receive the remote mount through fuse.

Assuming both directories exist and FUSE exists on both machines, then it will show up when you reboot.

A simpler method is to use SAMBA:  (put in your /etc/fstab)

//192.168.1.102/mnt/hd2/1 /mnt/dynebolic smbfs rw 0 0

Create a local mountpoint (dynebolic, in this case) and link it with the remote directory using smbfs.  

If it's a local network with no wireless, then you can do a similar thing with NFS--network file system.

As long as it's a locally-seen mountpoint, then most applications (including xmms) will be able to see the remote files.

---

