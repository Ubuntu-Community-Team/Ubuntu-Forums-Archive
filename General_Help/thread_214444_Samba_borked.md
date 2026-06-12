---
title: "Samba borked"
date: 2006-07-12
forum: General Help
---

### Post by cleentrax on 2006-07-12
Yesterday, I tried to create a shared folder for the  first time, and got a samba error. Today, there were Samba updates, and now something is seriously broken. I can't fix it with apt-get -f or synaptic...
```
sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 127115 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I fix this? Thanks!

---

### Post by Isntitknoying on 2006-07-12
I haven't tried to create a shared folder, but my Samba also crapped out today after updates. I just found this tip in a post from a couple of weeks ago, and it worked out for me. 

first delete files:

sudo rm /etc/rc3.d/K09samba

sudo rm /etc/rc2.d/K09samba

and than:

sudo apt-get remove samba

and new installation:

sudo apt-get install samba

Hope this helps.

---

### Post by siriusfox on 2006-07-12
That did it for me. I was having the same problem as the first poster.

The only difference was Insted of K09samba it was S91samba. Still, removing from rc3.d, and rc2.d and runing aptget did it.

Thanks.
-siriusfox

---

### Post by cleentrax on 2006-07-12
Genius. That fixed it. Thanks. Now, if I can actually get a shared folder visible on the network I'll be a happy Ubuntu camper!

---

### Post by Bokonon on 2006-07-12
Gosh this seems like a windows style fix.  (uninstall/reinstall)

I hope this trend doesn't continue.  ;)

---

### Post by tassoman on 2006-07-13
Isn't needed to windozing on ubuntu, just edit the symlink:

[http://ubuntuforums.org/showpost.php?p=1249897&postcount=3](http://ubuntuforums.org/showpost.php?p=1249897&postcount=3)

---

### Post by celem on 2006-07-13
Fixed it for me also. I remember having to do this once before, during the Dapper beta days. A recurring theme?

---

### Post by simonn on 2006-07-13
> **celem said:**
> A recurring theme?

Yep, if you do not **completely remove** a package.

See Section 3.2 of the Synaptic Package Manager Manual, but, in a nutshell, removing a package rather than completely removing it (or using the --purge apt-get option) will leave everything in /etc.

---

