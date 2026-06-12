---
title: "Curlftpfs in fstab problem"
date: 2013-01-29
forum: General Help
---

### Post by Ugo40 on 2013-01-29
Hi. I'm using curlftpfs to mount an ftp server in my filesystem. This works very well when I mount it manually after startup (mount -a). I've added this mount to fstab but ubuntu halts during startup saying it cant be mounted. When I press M and try to mount it manually it seems to me that the network is not initialized yet.
How can I solve this?

---

### Post by adam.stokes on 2013-01-29
Posting your fstab would help. Without looking at that though are you using the _netdev option? This should allow the network share to come up after the network is initialized.

---

### Post by Ugo40 on 2013-01-29
Thanks for the reply. That solved it:D
This is my fstab: 
curlftpfs#[ftp://ftpuser:passw@server](ftp://ftpuser:passw@server) /mnt/ftpbackup fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto,utf8,_netdev  0   1

---

### Post by fedleo on 2013-05-15
Hi there, 
I know this thread is old but I'm experiencing the same problem with Ubuntu Gnome 13.04. 
I can mount manually my ftp folder using curlftpfs but I can't mount it with Fstab during boot due to network not ready as reported on my error log. 
Don't know why but the option _netdev is considered invalid, even when I try with mount -a. 
Any tips? Thanks.

---

### Post by oliverh on 2013-07-08
Hi,

I'm having the exact same problem mounting an ftp - same issue on boot, this time in xubuntu 13.04. Any ideas?

My fstab: curlftpfs#user:pass@ftp.server.com/public_html /mnt/ftp/servername fuse rw,uid=500,allow_other,user,auto 0 1

Thanks in advance!

Oliver

ps. sorry for the thread revival...

---

### Post by oliverh on 2013-07-08
Whoops, that was meant to be user : pass...

---

