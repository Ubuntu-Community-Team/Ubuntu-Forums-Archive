---
title: "Cannot mount ntfs drives to anyone but root."
date: 2020-09-23
forum: General Help
---

### Post by ukfliers on 2020-09-23
After a disastrous incident I had to re-install Ubuntu 20.04.1 LTS. I have several ntfs drives connected but I need to access them using ftp. What I have done so far...
installed vsftpd - it is active and working. But I cannot access them as permission is denied. I have tried changing config file per suggestions, none work. Here is my file...

listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
force_dot_files=YES
pasv_min_port=40000
pasv_max_port=50000
user_sub_token=$robert
local_root=/home/robert/media

It restarted fine, but no luck accessing with client.

The other part to this is all drives mounted either by auto mount or manually are owned by root and I can't change it. The mount points were created by me and show that in permissions until they are mounted then permissions change to root and I am locked again.

I chown the mounted drive and it doesn't work. If it would mount to specific user then ftp may work (hoping).

I am no Linux expert so I am asking for some guidance here

Thanks in anticipation.

---

### Post by CelticWarrior on 2020-09-23
The drives may need error correction and that can be achieved only with Windows tools.

---

### Post by ukfliers on 2020-09-23
Thanks 4 the reply, but they r good and I can write to them on the Ubuntu machine, create directories and the like but not thru ftp.

---

### Post by CelticWarrior on 2020-09-24
> **ukfliers said:**
> Thanks 4 the reply, but they r good and I can write to them on the Ubuntu machine, create directories and the like but not thru ftp.

That doesn't mean much. Often you can use NTFS partitions in Linux almost as if there's nothing wrong with them but in reality there are and when mounted in Windows it complains and offers error correction. That said I'm not sure if and how it would impact network operations. What I know is using NTFS in Linux is always a very bad idea, unless as a shared data partition in dual-boot in which case you would have Windows to correct them if needed.

---

