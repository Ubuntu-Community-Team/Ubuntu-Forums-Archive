---
title: "Can't install Samba"
date: 2014-08-19
forum: General Help
---

### Post by kiwipenguin on 2014-08-19
Hello,

I get an error message when trying to install Samba.
Does anyone have any suggestions as to how can I solve this problem?
Thanks.

I am using 11.10 but will update as soon as I can back-up my data using wifi (USB ports don't work).

In terminal, when I type [FONT=courier new]sudo apt-get install samba[/FONT] I get the following output:

[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree       [/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]The following package was automatically installed and is no longer required:[/FONT]
[FONT=courier new]  libutouch-geis1[/FONT]
[FONT=courier new]Use 'apt-get autoremove' to remove them.[/FONT]
[FONT=courier new]Suggested packages:[/FONT]
[FONT=courier new]  openbsd-inetd inet-superserver smbldap-tools ldb-tools[/FONT]
[FONT=courier new]The following NEW packages will be installed[/FONT]
[FONT=courier new]  samba[/FONT]
[FONT=courier new]0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=courier new]Need to get 7,990 kB of archives.[/FONT]
[FONT=courier new]After this operation, 23.0 MB of additional disk space will be used.[/FONT]
[FONT=courier new]WARNING: The following packages cannot be authenticated![/FONT]
[FONT=courier new]  samba[/FONT]
[FONT=courier new]Install these packages without verification [y/N]? y[/FONT]
[FONT=courier new]Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates/main samba i386 2:3.5.11~dfsg-1ubuntu2.3[/FONT]
[FONT=courier new]  404  Not Found [IP: 91.189.88.153 80][/FONT]
[FONT=courier new]Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-security/main samba i386 2:3.5.11~dfsg-1ubuntu2.3[/FONT]
[FONT=courier new]  404  Not Found [IP: 91.189.88.153 80][/FONT]
[FONT=courier new]Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.5.11~dfsg-1ubuntu2.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.5.11~dfsg-1ubuntu2.3_i386.deb)  404  Not Found [IP: 91.189.88.153 80][/FONT]
[FONT=courier new]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT]
[FONT=courier new]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT]
[FONT=courier new]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT]
[FONT=courier new]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT]

---

### Post by ubudog on 2014-08-19
Ubuntu 11.10 went end-of-life May 2013 I believe, and that's probably why you can't reach the repos.

I'd recommend installing a supported Ubuntu version (like 14.04) and then setting up Samba.

---

### Post by kiwipenguin on 2014-08-19
Thanks ubudog.
Although your suggestion is a simple way to fix the problem, I am reluctant to install any newer version of Ubuntu until I can back-up my hard drive.
And, because my computer will not detect any external drives, I am looking for other ways to do a back-up. Using wifi via Samba is one option.
As yet I am not aware of any other method...

---

### Post by ubudog on 2014-08-19
If you have another Linux box, you could back up your data to it using rsync.  On the other Linux box, just set up an ssh server (openssh-server package in Ubuntu), and copy your data on over.

Connecting the two computers by Ethernet would be ideal, as doing this over wifi will take much longer.

A simple command to backup your home directory would be:
```
rsync -av --progress /home user@ipaddress:/backup/
```

As always, make sure your backup is there and works before deleting anything.

Hope that helps you!

---

