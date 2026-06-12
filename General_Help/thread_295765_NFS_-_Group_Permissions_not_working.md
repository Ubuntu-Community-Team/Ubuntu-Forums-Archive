---
title: "NFS - Group Permissions not working"
date: 2006-11-08
forum: General Help
---

### Post by luckSpray on 2006-11-08
I'm having the following problem persisting for a long time (I already google'd it and already used the search-function of this forum)...

Server:
My NFS-Server has a directory with following permissions and user informations:
```

owner: root
group: family
drwxrwx---

```
Hence I am member of 'family' I have no problems accessing the directory via ssh.


Client:
The client has the same group 'family' with the same gid as on the server. And I am of course member of the group.

The directory shows up correctly in the filesystem but whenever I try to access it, it says 'Permission denied'.

How the directory shows up:
```

owner: root
group: family
drwxrwx---

```

If I change the owner of the directory to me, it works. What's wrong here?

Thanks in advance.
luckSpray.

---

### Post by boltronics on 2007-02-02
Incredible... it's not just me! This is the weird part though - it's definitely a client-side issue. I have other boxes work perfectly. One old box (upgraded probably all the way from Warty or Hoary) always fails - only on directories where the user has group permissions. Here is the problem in more detail:

On my server (imp - 6.06 Dapper, nfs-kernel-server 1:1.0.7-3ubuntu2):
```

abolte@imp:/usr/local/downloads$ ll
total 36
drwsrws---  6 root files 4096 2007-02-01 23:13 applications
drwsrws---  8 root files 4096 2007-02-02 19:24 distributions
drwsrws---  3 root files 4096 2007-01-19 06:51 documents
drwsrws--- 32 root files 4096 2007-02-01 21:25 drivers
drwsrws--- 16 root files 4096 2007-01-09 18:54 games
drwsrws---  4 root files 4096 2006-11-19 05:16 images
drwsrws---  4 root files 4096 2007-01-13 21:33 movies
drwsrws---  3 root files 4096 2006-11-05 00:15 podcasts
drwsrwsr-x 18 root files 4096 2007-01-13 20:31 updates
abolte@imp:/usr/local/downloads$ ll documents/
total 4
drwsrws--- 5 root files 4096 2006-08-12 14:41 manuals
abolte@imp:/usr/local/downloads$ id
uid=567(abolte) gid=567(abolte) groups=4(adm),5(tty),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),300(movies),301(music),302(files),567(abolte),1001(jbolte)
abolte@imp:/usr/local/downloads$ cat /etc/exports 
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home                192.168.1.0/24(sync,rw,no_root_squash)
/usr/local/downloads 192.168.1.0/24(sync,rw)
/usr/local/music     192.168.1.0/24(sync,rw)
abolte@imp:/usr/local/downloads$ 

```

On my client (vampire - 6.10 Edgy, nfs-common 1:1.0.9-2ubuntu1):
```

abolte@vampire:/mnt/nfs/monsters/imp/downloads$ ll
total 36
4 drwsrws---  6 root files 4096 2007-02-01 23:13 applications
4 drwsrws---  8 root files 4096 2007-02-02 19:24 distributions
4 drwsrws---  3 root files 4096 2007-01-19 06:51 documents
4 drwsrws--- 32 root files 4096 2007-02-01 21:25 drivers
4 drwsrws--- 16 root files 4096 2007-01-09 18:54 games
4 drwsrws---  4 root files 4096 2006-11-19 05:16 images
4 drwsrws---  4 root files 4096 2007-01-13 21:33 movies
4 drwsrws---  3 root files 4096 2006-11-05 00:15 podcasts
4 drwsrwsr-x 18 root files 4096 2007-01-13 20:31 updates
abolte@vampire:/mnt/nfs/monsters/imp/downloads$ ll documents/
ls: documents/: Permission denied
abolte@vampire:/mnt/nfs/monsters/imp/downloads$ ll updates/
total 64
4 drwsrws---  2 root files 4096 2006-07-09 00:07 Apple Mac OS X Combined Update 10.3.9
4 drwsr-sr-x  4 root files 4096 2006-12-18 00:28 Battlefield 2
4 drwsrws---  3 root files 4096 2006-07-26 22:41 Command & Conquer 95
4 drwsrws---  4 root files 4096 2006-07-28 20:48 Command & Conquer - The First Decade
4 drwsr-sr-x  2 root files 4096 2006-12-10 10:48 dansguardian-blacklists
4 drwsrws---  5 root files 4096 2006-07-26 20:19 Dark Reign
4 drwsrws---  2 root files 4096 2006-09-13 08:57 Fear 1.07
4 drwsrws---  2 root files 4096 2006-12-02 10:08 GLQuake 1.1.1.4
4 drwsrws---  2 root files 4096 2006-11-12 01:28 Need for Speed - Most Wanted
4 drwsrws---  2 root files 4096 2006-11-12 01:19 Need for Speed - Underground 2
4 drwsrws---  2 root files 4096 2006-10-15 17:59 Prey 1.2
4 drwsrws---  2 root files 4096 2006-10-01 12:47 Quake 4 v1.3
4 drwsrwsr-x  4 root files 4096 2007-01-13 20:50 Unreal II - The Awakening
4 drwsrws---  7 root files 4096 2006-07-08 00:50 Unreal Tournament 2003
4 drwsrws--- 12 root files 4096 2006-07-08 15:27 Unreal Tournament 2004
4 drwsrws---  2 root files 4096 2006-09-13 20:10 Warcraft 3 - Reign of Chaos Patch v1.20e
abolte@vampire:/mnt/nfs/monsters/imp/downloads$ id
uid=567(abolte) gid=567(abolte) groups=4(adm),6(disk),13(proxy),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),100(users),107(lpadmin),108(scanner),109(admin),300(movies),301(music),302(files),567(abolte)
abolte@vampire:/mnt/nfs/monsters/imp/downloads$

```

As can be seen, the relevant group "302(files)" is exactly the same on both machines.

Another client that works (kraken - 6.10 Edgy, nfs-common 1:1.0.9-2ubuntu1, installed as 6.06 and upgraded) is running the same nfs-common files.

```
abolte@kraken:~$ for file in $(dpkg -L nfs-common) ; do if [ -f ${file} ] ; then md5sum ${file} ; fi ; done > nfs-common.md5
```

Then back on vampire (NFS client with problem):

```
abolte@vampire:~$ scp kraken:~/nfs-*.md5 .
abolte@kraken's password: 
nfs-common.md5                                                                                                                                                                 100% 2107     2.1KB/s   00:00    
abolte@vampire:~$ md5sum -c nfs-common.md5 
/etc/init.d/nfs-common: OK
/sbin/rpc.lockd: OK
/sbin/rpc.statd: OK
/sbin/showmount: OK
/usr/sbin/nfsstat: OK
/usr/sbin/rpc.gssd: OK
/usr/sbin/rpc.idmapd: OK
/usr/sbin/gss_clnt_send_err: OK
/usr/sbin/gss_destroy_creds: OK
/usr/sbin/rpcdebug: OK
/usr/share/nfs-common/conffiles/idmapd.conf: OK
/usr/share/nfs-common/conffiles/idmapd.conf.md5sum: OK
/usr/share/nfs-common/conffiles/nfs-common.default: OK
/usr/share/nfs-common/conffiles/nfs-common.default.md5sum: OK
/usr/share/doc/nfs-common/copyright: OK
/usr/share/doc/nfs-common/README.Debian.nfsv4: OK
/usr/share/doc/nfs-common/changelog.gz: OK
/usr/share/doc/nfs-common/changelog.Debian.gz: OK
/usr/share/man/man5/idmapd.conf.5.gz: OK
/usr/share/man/man8/lockd.8.gz: OK
/usr/share/man/man8/statd.8.gz: OK
/usr/share/man/man8/nfsstat.8.gz: OK
/usr/share/man/man8/showmount.8.gz: OK
/usr/share/man/man8/gssd.8.gz: OK
/usr/share/man/man8/idmapd.8.gz: OK
/usr/share/man/man8/rpcdebug.8.gz: OK
/usr/share/man/man8/rpc.lockd.8.gz: OK
/usr/share/man/man8/rpc.idmapd.8.gz: OK
/usr/share/man/man8/rpc.statd.8.gz: OK
/usr/share/man/man8/rpc.gssd.8.gz: OK
/etc/default/nfs-common: OK
/etc/idmapd.conf: OK
abolte@vampire:~$ 
```

So they all look good.

There's nothing in hosts.allow/hosts.deny on either machine, but I expect it wouldn't be a portmap issue anyway considering it *mostly* works.

Oh - and the mount options on both clients:

Kraken:
```
abolte@kraken:/mnt/nfs/monsters/imp/downloads$ mount | grep imp
imp.monsters:/usr/local/downloads on /mnt/nfs/monsters/imp/downloads type nfs (rw,addr=192.168.1.1)
imp.monsters:/home on /mnt/nfs/monsters/imp/home type nfs (rw,addr=192.168.1.1)
imp.monsters:/usr/local/music on /mnt/nfs/monsters/imp/music type nfs (rw,addr=192.168.1.1)
abolte@kraken:/mnt/nfs/monsters/imp/downloads$
```

Vampire:
```
abolte@vampire:/mnt/nfs/monsters/imp/downloads$ mount | grep imp
imp.monsters:/usr/local/downloads on /mnt/nfs/monsters/imp/downloads type nfs (rw,addr=192.168.1.1)
imp.monsters:/home on /mnt/nfs/monsters/imp/home type nfs (rw,addr=192.168.1.1)
imp.monsters:/usr/local/music on /mnt/nfs/monsters/imp/music type nfs (rw,addr=192.168.1.1)
abolte@vampire:/mnt/nfs/monsters/imp/downloads$
```

Well, that's all I can think of for now. Let me know if anyone's got a hint or would like more information.

---

### Post by PraysToPan on 2007-04-25
Haha, no it isn't just you.  I'm having this problem also.  I posted this bug report about it: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110132](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110132)

Jon

---

### Post by C Shore on 2008-05-25
If you're still looking for help on this:

Edit /etc/default/nfs-kernel-server

to have the line

RPCMOUNTDOPTS="--manage-gids"

and you're set

---

### Post by josir on 2008-06-11
Hi luckSpray, where did you get this information ?

I am trying to learn how to configure NFS with user permissions and I could not find useful sites and docs.

Thanks in advance,
Josir Gomes

---

