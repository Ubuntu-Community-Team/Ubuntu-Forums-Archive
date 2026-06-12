---
title: "Unable to upgrade from 14.04.4 to 16.04."
date: 2016-08-23
forum: General Help
---

### Post by Shadow aok on 2016-08-23
Hello,

I am having an issue with an Ubuntu server 14.04.4 AMD 64 inside a lxc container (but not related to lxc).
I was wondering why on this specific container i was unable to do a  successfull upgrade to 16.04 (i'm ending with sysv kroken, missing  binaires like shutdown, halt,  ....) so after restoring a backup, i  checked if everything was fine with this install.

The release upgrade issue is not the point, i'll try again after fixing what i describe below.

I found out that libc-bin was broken and fixed it by reinstalling it.
But every time i ran a "dpkg-reconfigure -a", it ends with libc-bin being broken again.

This install basically only runs request-tracker, apache2, fetchmail and mysql.
I haven't been able to find in any logs why it was like this.

```
$ dpkg-reconfigure libc-bin
/usr/sbin/dpkg-reconfigure: libc-bin is broken or not fully installed

$ apt-get install --reinstall libc-bin
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1 165 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 30932 files and directories currently installed.)
Preparing to unpack .../libc-bin_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc-bin (2.19-0ubuntu6.9) over (2.19-0ubuntu6.9) ...
Processing triggers for ca-certificates (20160104ubuntu0.14.04.1) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Processing triggers for initramfs-tools (0.103ubuntu4.4) ...
Setting up libc-bin (2.19-0ubuntu6.9) ...

$ dpkg-reconfigure libc-bin

$ dpkg-reconfigure -a
...

 * Stopping authentication failure monitor fail2ban                                                                                                                                                           [ OK ]
 * Starting authentication failure monitor fail2ban                                                                                                                                                           [ OK ]
 * Stopping mail retriever agent:                                                                                                                                                                             [ OK ]
update-rc.d: warning:  stop runlevel arguments (none) do not match fetchmail Default-Stop values (0 1 6)
 * Starting mail retriever agent:                                                                                                                                                                             [ OK ]
Regenerating fonts cache... done.
update-initramfs: deferring update (trigger activated)
apache2_invoke fcgid: already enabled
 * Restarting web server apache2                                                                                                                                                                              [ OK ]
apache2_invoke perl: already enabled
 * Restarting web server apache2                                                                                                                                                                              [ OK ]
/usr/sbin/dpkg-reconfigure: libc-bin is broken or not fully installed
```

Any idea ?

Thanks.

---

### Post by Bashing-om on 2016-08-23
Shadow aok; Hello;

Maybe compare what is installed for libc-bin as to what should be ?

What should be:
```

apt list libc-bin

```

And what is and what the system is looking for:
```

apt-cache policy libc-bin

```

[INDENT][INDENT]strange things do happen
[/INDENT][/INDENT]

---

### Post by Shadow aok on 2016-08-23
Looks good to me.

```
~# apt list libc-bin
Listing... Done
libc-bin/trusty-updates,trusty-security,now 2.19-0ubuntu6.9 amd64 [installed]

~# apt-cache policy libc-bin
libc-bin:
  Installed: 2.19-0ubuntu6.9
  Candidate: 2.19-0ubuntu6.9
  Version table:
 *** 2.19-0ubuntu6.9 0
        500 ftp://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ trusty-updates/main amd64 Packages
        500 ftp://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.19-0ubuntu6 0
        500 ftp://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ trusty/main amd64 Packages
```

---

### Post by Bashing-om on 2016-08-23
Shadow aok; Yeah ..

Agreed .// looks good to me also . TBH I had expected a PPA to be in the way . Not so .

When we do a number like this:
```

sudo apt install --reinstall libc-bin

```

does the system scream an holler ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by Shadow aok on 2016-08-23
Not at all, everything is fine.

```
# apt install --reinstall libc-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1 165 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 30932 files and directories currently installed.)
Preparing to unpack .../libc-bin_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc-bin (2.19-0ubuntu6.9) over (2.19-0ubuntu6.9) ...
Processing triggers for ca-certificates (20160104ubuntu0.14.04.1) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Setting up libc-bin (2.19-0ubuntu6.9) ...
```

dpkg.log
```
2016-08-23 18:18:28 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:29 status triggers-pending ca-certificates:all 20160104ubuntu0.14.04.1
2016-08-23 18:18:29 startup archives unpack
2016-08-23 18:18:30 upgrade libc-bin:amd64 2.19-0ubuntu6.9 2.19-0ubuntu6.9
2016-08-23 18:18:30 status half-configured libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:30 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:30 status half-installed libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:31 status half-installed libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:32 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:32 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:33 trigproc ca-certificates:all 20160104ubuntu0.14.04.1 20160104ubuntu0.14.04.1
2016-08-23 18:18:33 status half-configured ca-certificates:all 20160104ubuntu0.14.04.1
2016-08-23 18:18:33 status installed ca-certificates:all 20160104ubuntu0.14.04.1
2016-08-23 18:18:34 startup packages configure
2016-08-23 18:18:34 configure libc-bin:amd64 2.19-0ubuntu6.9 <none>
2016-08-23 18:18:34 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:34 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:35 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:35 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:35 status unpacked libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:35 status half-configured libc-bin:amd64 2.19-0ubuntu6.9
2016-08-23 18:18:36 status installed libc-bin:amd64 2.19-0ubuntu6.9
```

---

### Post by Bashing-om on 2016-08-23
Shadow aok; Uh Huh ;

Looks good to me . Is the system happy now ?
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

Maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Shadow aok on 2016-08-23
```
# dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 module-init-tools    transitional dummy package (module-init-tools to kmod)
 libjson0:amd64       JSON manipulation library (transitional package)
```

Fixing ....

```
# apt install --reinstall module-init-tools libjson0:amd64
# dpkg -C
```

Looks good to me, thanks.

---

### Post by Bashing-om on 2016-08-23
Shadow aok; Hey ...

All setting pretty now ?

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Shadow aok on 2016-08-23
Well, let's wait tomorrow so i'll try again to upgrade to 16.04, as i was thinking maybe that was the root cause of the upgrade failure and i will tell you :)

---

### Post by Bashing-om on 2016-08-23
Shadow aok; Ho Kay .

As close to default as you can get for the online release upgrade . That do include reverting any proprietary graphic's driver .

[INDENT][INDENT]keep it in the family
[/INDENT][/INDENT]

---

### Post by Shadow aok on 2016-08-24
Nope, upgrade still fails, i created a bug report here :
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1616368](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1616368)

and a topic here :
[https://ubuntuforums.org/showthread.php?t=2334975&p=13535285#post13535285](https://ubuntuforums.org/showthread.php?t=2334975&p=13535285#post13535285)

---

