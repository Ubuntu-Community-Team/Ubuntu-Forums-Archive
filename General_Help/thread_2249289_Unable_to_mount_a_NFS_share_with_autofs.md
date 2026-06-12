---
title: "Unable to mount a NFS share with autofs"
date: 2014-10-20
forum: General Help
---

### Post by nyoka2 on 2014-10-20
Hi all,

I have a NFS mount which I can mount manually using mount:

```
root@localhost httpd]# mount -t nfs 192.168.56.102:/share /sharedir
[root@localhost httpd]# ls /sharedir/
New Text Document.txt  roldy.pem
```

However, I can't mount this share using autofs.

Here are the contents of my /etc/auto.master file:

```
/mymount /etc/auto.direct --timeout=60
```

Here are the contents of my /etc/auto.direct file:

```
share -fstype=nfs,rw,soft,intr 192.168.56.102:/share
```

---

### Post by papibe on 2014-10-21
Hi nyoka2. Welcome to the forum ):P

A few thoughts, the dir /mymount should exist, but /mymount/share should not (ghosting is enable by default).

If that does not work, please try to force the mounting:
```
cd /mymount/share

ls
```
and then post any error you got plus the output of this command:
```
tail /var/log/syslog
```
Regards.

---

### Post by nyoka2 on 2014-10-21
Hi Papibe,

Thank you so much for taking the time to respond to my question. I really appreciate your help with this.

> A few thoughts, the dir /mymount should exist, but /mymount/share should not (ghosting is enable by default).

I can confirm that the /mymount directory is empty:

```
[root@localhost ~]# ls -lrt /mymount/
total 0

```

Please see below for the contents of /var/log/messages after restarting autofs:
```

ct 21 18:10:56 localhost systemd: Starting Automounts filesystems on demand...
Oct 21 18:10:56 localhost systemd: Started Automounts filesystems on demand.
Oct 21 18:11:15 localhost chronyd[683]: Selected source 130.102.2.123
```

I then restarted autofs again and am still unable to access /mymount:

```
Oct 21 18:12:10 localhost systemd: Stopping Automounts filesystems on demand...
Oct 21 18:12:10 localhost automount[2559]: umount_autofs_indirect: ask umount returned busy /mymount
Oct 21 18:12:12 localhost systemd: Starting Automounts filesystems on demand...
Oct 21 18:12:12 localhost systemd: Started Automounts filesystems on demand.
```

LSOF output for /mymount:

```
[root@localhost ~]# lsof | grep /mymount
bash      2466                root  cwd       DIR               0,37         0      22473 /mymount
automount 2605                root   16r      DIR               0,37         0      22473 /mymount
automount 2605 2606           root   16r      DIR               0,37         0      22473 /mymount
automount 2605 2607           root   16r      DIR               0,37         0      22473 /mymount
automount 2605 2610           root   16r      DIR               0,37         0      22473 /mymount
automount 2605 2613           root   16r      DIR               0,37         0      22473 /mymount
automount 2605 2614           root   16r      DIR               0,37         0      22473 /mymount
```

Any help or guidance you can provide would be greatly appreciated. Thank you for your expertise and time.

---

### Post by papibe on 2014-10-22
I may be mistaken, but I think ' ls /mymount/' won't activate the mount, you should either 'ls /mymount/share' or 'cd /mymount/share'.

Does that make a difference?

Also, try restarting your autofs service after making changes to the autofs files.
```
sudo service autofs restart
```
Let us know how it goes.
Regards.

---

