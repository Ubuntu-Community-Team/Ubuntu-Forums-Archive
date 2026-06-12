---
title: "How to mount NFS drive?"
date: 2012-12-05
forum: General Help
---

### Post by blnl on 2012-12-05
I just installed Ubutnu 12.04 om my wifes notebook. I'm facing a strange problem that I can't mount my NAS (which is a true NFS export).

The following happens when I try to mount my NAS:
```
vesna@hp8510p:~$ cd /mnt
vesna@hp8510p:/mnt$ sudo mkdir nas
[sudo] password for vesna: 
vesna@hp8510p:/mnt$ ll nas/
total 0
vesna@hp8510p:/mnt$ sudo mount 192.168.1.220:/mnt/HD_a2 nas
mount: wrong fs type, bad option, bad superblock on 192.168.1.220:/mnt/HD_a2,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

vesna@hp8510p:/mnt$ 

```

Can someone please explain what I'm doing wrong here?

I've been using Fedora for many years and I never had this problem. On my Fedora system I mount this very same NAS as follows:
```
[root@dc7100 boris]# cd /mnt
[root@dc7100 mnt]# mkdir nas
[root@dc7100 mnt]# ll nas/
total 0
[root@dc7100 mnt]# mount 192.168.1.220:/mnt/HD_a2/ nas
[root@dc7100 mnt]# ll nas/
total 132
dr-xr-xr-x.  5 boris users  4096 Aug 26 22:21 ARH
dr-xr-xr-x. 11 boris users  4096 Sep 30 10:21 BAK
drwxr-xr-x. 10 boris users  4096 Dec  5 22:39 DAT
drwxr-xr-x. 18 root  root   4096 Nov  3  2011 ffp
-rw-r--r--.  1 root  root  84864 Dec  5 22:38 ffp.log
dr-xr-xr-x. 11 boris users  4096 Nov 14  2011 FIL
drwxr-xr-x.  6 root  root   4096 Oct  9  2011 FTP
-rwxr-xr-x.  1 root  root   1778 Nov 12  2011 fun_plug
drwxr-xr-x. 12 boris users 16384 Dec  3 10:58 TMP
[root@dc7100 mnt]# 

```

Main difference that I observe here is that in Fedora I'm root, while I can't manage to become root in Ubuntu. I never got a chance to setup a root password during the installation.

Can someone show me how to become root in Ubuntu?

Thanks in advance,
Boris

---

### Post by steeldriver on 2012-12-05
have you installed at least the minimal client-side nfs package (nfs-common) on the notebook? I don't think it's installed by default

---

### Post by agillator on 2012-12-05
You shouldn't need to become root; sudo will suffice for almost everything. Ubuntu purposely locks the root account although it does exist. If you insist on accessing the root account, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). There are a lot of other suggestions there, many warnings about the dangers, many reasons you probably don't need to become root and they are all there for a reason. For that reason I will let you read to obtain the necessary command. Just please remember there are two types of people: those who have and those who will. If you have been using Fedora extensively as root you are either very good, very careful, or very, very lucky. 

As to your specific problem, take a look at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and see if that helps.

---

### Post by blnl on 2012-12-06
Thanks guys,

It never occurred to me that NFS client is not installed by default. I see it really as an essential feature.
However, after installing it, I can mount my NAS without problems (even using sudo).

By the way, do not worry about me being root. I am both, careful and I know what I'm doing. It's gonna be be fine ;)

---

