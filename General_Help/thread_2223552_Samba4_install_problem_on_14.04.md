---
title: "Samba4 install problem on 14.04"
date: 2014-05-11
forum: General Help
---

### Post by asatbluesboy on 2014-05-11
Mine was running fine on 13.10 until I updated it a few days ago. I was affected by that issue regarding the samba4 package (wouldn't install. Period), but otherwise it worked fine before the update. Now I can't even install anything else since Samba is broken and the terminal will give me
```
gustavo@gustavo-Studio:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba-libs
The following NEW packages will be installed:
  samba-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
Need to get 0 B/4.099 kB of archives.
After this operation, 18,3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 455042 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb ...
secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
http://bugs.debian.org/726472
/var/lib/samba:
total 2208
drwxr-xr-x  8 root root         4096 Jan  8 17:33 .
drwxr-xr-x 79 root root         4096 Mai  9 11:45 ..
-rw-------  1 root root       421888 Jan  8 10:05 account_policy.tdb
-rw-------  1 root root          696 Jan  8 10:05 group_mapping.tdb
drwxr-x---  2 root root         4096 Fev 27 18:05 ntp_signd
-rw-------  1 root root       421888 Jan  8 10:06 passdb.tdb
drwxr-xr-x 10 root root         4096 Jan  8 10:05 printers
drwxr-xr-x  6 root root         4096 Fev 27 18:05 private
-rw-------  1 root root       528384 Jan  8 10:05 registry.tdb
-rw-------  1 root root       430080 Jan  8 10:05 secrets.tdb
-rw-------  1 root root       421888 Jan  8 10:05 share_info.tdb
drwxr-xr-x  3 root root         4096 Jan  8 10:00 sysvol
drwxrwx--T  2 root sambashare   4096 Jan  8 10:05 usershares
drwxr-x---  2 root root         4096 Jan  8 17:33 winbindd_privileged


/var/lib/samba/private:
total 10472
drwxr-xr-x 6 root root    4096 Fev 27 18:05 .
drwxr-xr-x 8 root root    4096 Jan  8 17:33 ..
-rw------- 1 root root 1286144 Jan  8 10:00 hklm.ldb
-rw------- 1 root root 1286144 Jan  8 10:00 idmap.ldb
srwxrwxrwx 1 root root       0 Fev 27 18:05 ldapi
drwxr-x--- 2 root root    4096 Fev 27 18:05 ldap_priv
-r--r--r-- 1 root root     166 Jan  8 17:33 named.conf.update
-rw------- 1 root root 1286144 Jan  8 10:00 privilege.ldb
-rw------- 1 root root     696 Jan  8 17:33 randseed.tdb
-rw------- 1 root root 4251648 Jan  8 10:00 sam.ldb
drwx------ 2 root root    4096 Jan  8 10:00 sam.ldb.d
-rw------- 1 root root     696 Fev 27 18:05 schannel_store.tdb
-rw------- 1 root root 1286144 Jan  8 10:00 secrets.ldb
-rw------- 1 root root     696 Jan  8 10:00 secrets.tdb
-rw------- 1 root root 1286144 Jan  8 10:00 share.ldb
drwxr-xr-x 3 root root    4096 Jan  8 17:33 smbd.tmp
drwxr-xr-x 2 root root    4096 Jan  8 17:33 tls
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
when I try to fix it.

If I try to do anything else - for instance, do an autoremove - I get
```
gustavo@gustavo-Studio:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 python-samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-dsdb-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-vfs-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 winbind : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by bab1 on 2014-05-11
> **asatbluesboy said:**
> Mine was running fine on 13.10 until I updated it a few days ago. I was affected by that issue regarding the samba4 package (wouldn't install. Period), but otherwise it worked fine before the update. Now I can't even install anything else since Samba is broken and the terminal will give me
```
gustavo@gustavo-Studio:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba-libs
The following NEW packages will be installed:
  samba-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
Need to get 0 B/4.099 kB of archives.
After this operation, 18,3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 455042 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb ...
secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
http://bugs.debian.org/726472
/var/lib/samba:
total 2208
drwxr-xr-x  8 root root         4096 Jan  8 17:33 .
drwxr-xr-x 79 root root         4096 Mai  9 11:45 ..
-rw-------  1 root root       421888 Jan  8 10:05 account_policy.tdb
-rw-------  1 root root          696 Jan  8 10:05 group_mapping.tdb
drwxr-x---  2 root root         4096 Fev 27 18:05 ntp_signd
-rw-------  1 root root       421888 Jan  8 10:06 passdb.tdb
drwxr-xr-x 10 root root         4096 Jan  8 10:05 printers
drwxr-xr-x  6 root root         4096 Fev 27 18:05 private
-rw-------  1 root root       528384 Jan  8 10:05 registry.tdb
-rw-------  1 root root       430080 Jan  8 10:05 secrets.tdb
-rw-------  1 root root       421888 Jan  8 10:05 share_info.tdb
drwxr-xr-x  3 root root         4096 Jan  8 10:00 sysvol
drwxrwx--T  2 root sambashare   4096 Jan  8 10:05 usershares
drwxr-x---  2 root root         4096 Jan  8 17:33 winbindd_privileged


/var/lib/samba/private:
total 10472
drwxr-xr-x 6 root root    4096 Fev 27 18:05 .
drwxr-xr-x 8 root root    4096 Jan  8 17:33 ..
-rw------- 1 root root 1286144 Jan  8 10:00 hklm.ldb
-rw------- 1 root root 1286144 Jan  8 10:00 idmap.ldb
srwxrwxrwx 1 root root       0 Fev 27 18:05 ldapi
drwxr-x--- 2 root root    4096 Fev 27 18:05 ldap_priv
-r--r--r-- 1 root root     166 Jan  8 17:33 named.conf.update
-rw------- 1 root root 1286144 Jan  8 10:00 privilege.ldb
-rw------- 1 root root     696 Jan  8 17:33 randseed.tdb
-rw------- 1 root root 4251648 Jan  8 10:00 sam.ldb
drwx------ 2 root root    4096 Jan  8 10:00 sam.ldb.d
-rw------- 1 root root     696 Fev 27 18:05 schannel_store.tdb
-rw------- 1 root root 1286144 Jan  8 10:00 secrets.ldb
-rw------- 1 root root     696 Jan  8 10:00 secrets.tdb
-rw------- 1 root root 1286144 Jan  8 10:00 share.ldb
drwxr-xr-x 3 root root    4096 Jan  8 17:33 smbd.tmp
drwxr-xr-x 2 root root    4096 Jan  8 17:33 tls
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
when I try to fix it.

If I try to do anything else - for instance, do an autoremove - I get
```
gustavo@gustavo-Studio:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 python-samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-dsdb-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-vfs-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 winbind : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

Samba on Ubuntu 13.10 is Samba v3.6 and Samba on Ubuntu 14.04 is v4.1  I think you will need to purge all the Samba3 and Samba4.  On Ubuntu 14.04 I would start with ```
sudo apt-get purge samba
``` and then use autoremove.

If successful you can then install on Ubuntu 14.04 version 4.1 Samba with ```
sudo apt-get install samba
```

---

### Post by asatbluesboy on 2014-05-13
Thanks a lot for the quick response! Still:

```
gustavo@gustavo-Studio:~$ sudo apt-get purge samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 python-samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-dsdb-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-vfs-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 winbind : Depends: samba (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
           Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I see the same message whenever I try to install anything (like the Flash plugin, which is also broken).

So I tried to download a DVD image last night, and it doesn't work! I used the same DVD brand I used to burn the other versions, burnt it twice, but it will hang when I tell it to install. With a USB stick (via UNetbootin) it kinda works, but will hang in the middle of the process. I'm wondering whether I could downgrade until things are more stable.

---

### Post by bab1 on 2014-05-13
> **asatbluesboy said:**
> Thanks a lot for the quick response! Still:

```
gustavo@gustavo-Studio:~$ sudo apt-get purge samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 python-samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-dsdb-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 samba-vfs-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
 winbind : Depends: samba (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
           Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I see the same message whenever I try to install anything (like the Flash plugin, which is also broken).

So I tried to download a DVD image last night, and it doesn't work! I used the same DVD brand I used to burn the other versions, burnt it twice, but it will hang when I tell it to install. With a USB stick (via UNetbootin) it kinda works, but will hang in the middle of the process. I'm wondering whether I could downgrade until things are more stable.

I think that part of the install problem is that the install script looks to see what is already installed and makes some install decisions.  Either way (downgrade or not) this action may be what is causing the install problems.

I suggest you first format the the disk by removing any current partitions and start over.  Recreate at least one new partition and then format it.  Then try the install.  I think 14.04 is stable enough for most use.  I don't think the problems you are having are not really due to the version you are using.

---

### Post by skestle on 2014-05-14
Note in your logs (it took me ages to spot it with the file listings)

> secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
Follow those instructions and retry.

And bab1, for goodness sake

> [COLOR=#000000]I suggest you first format the the disk[/COLOR]

Really? Isn't this "Windows advice"?

---

### Post by redmk2 on 2014-05-15
> **skestle said:**
> Note in your logs (it took me ages to spot it with the file listings)
>  secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
Follow those instructions and retry. 


And bab1, for goodness sake
[QUOTE]
I suggest you first format the the disk


Really? Isn't this "Windows advice"?[/QUOTE]
I think it's just good advice whether it's Windows or Linux.   A disk with a partition with a blank filesystem is the surest way to have success installing any OS.

This  > [COLOR="#0000FF"]I suggest you first format the the disk by removing any current partitions and start over.[/COLOR]
Eliminates this> [COLOR="#FF0000"]it took me ages to spot it with the file listings[/COLOR]

The OP is looking for a quick way to reinstall without the install script finding the original failed upgrade.  Why track down these types of insidious problems when you can recreate the filesystem on a partition in less that 5 minutes and have the installed OS running in less than 1/2 hour.  I don't see a  need to waste the time.

---

### Post by mastablasta on 2014-05-15
> **asatbluesboy said:**
> Thanks a lot for the quick response! Still:

```
 winbind : Depends: samba (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not going to be installed

```




strange naming since 14.04.1 is not out yet.

> 
I see the same message whenever I try to install anything (like the Flash plugin, which is also broken).

So I tried to download a DVD image last night, and it doesn't work! I used the same DVD brand I used to burn the other versions, burnt it twice, but it will hang when I tell it to install. With a USB stick (via UNetbootin) it kinda works, but will hang in the middle of the process. I'm wondering whether I could downgrade until things are more stable.

i only saw sintaller fail when there was not enough ram available. ther eis no downgrade. only instaling older version.

you can also reinstall 14.04. or try to resolve dependecy issues.

---

