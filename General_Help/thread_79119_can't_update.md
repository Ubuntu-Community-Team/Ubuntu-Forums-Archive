---
title: "can't update"
date: 2005-10-19
forum: General Help
---

### Post by kroiz on 2005-10-19
after a fresh install when I'm trying to get updates I get:
```
E: /var/cache/apt/archives/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb: files list file for package `openoffice.org2-draw' contains empty filename
```

I tried to remove **openoffice.org2-draw** or **ubuntu-desktop** but I always get the same message.

please what can I do?

---

### Post by grj on 2005-10-19
Did you first run:

sudo apt-get update

also you may need to add the lines to your /etc/apt/sources.list
for retrieving updates now that the final release is out.

---

### Post by kroiz on 2005-10-19
[QUOTE=grj]Did you first run:
sudo apt-get update
[/QUOTE]

When I do it now I get this, not sure this is related thought.
```
kroiz@ubuntu-ibm:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:3 http://il.archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://il.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://il.archive.ubuntu.com breezy Release
Hit http://il.archive.ubuntu.com breezy-updates Release
Ign http://il.archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://il.archive.ubuntu.com breezy/main Sources
Hit http://il.archive.ubuntu.com breezy/restricted Sources
Hit http://il.archive.ubuntu.com breezy/universe Packages
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://il.archive.ubuntu.com breezy/main Packages
Hit http://il.archive.ubuntu.com breezy/restricted Packages
Hit http://il.archive.ubuntu.com breezy/multiverse Packages
Hit http://il.archive.ubuntu.com breezy-updates/main Packages
Hit http://il.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://il.archive.ubuntu.com breezy-updates/universe Packages
Hit http://il.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://il.archive.ubuntu.com breezy-updates/main Sources
Hit http://il.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 20.0kB in 5s (3645B/s)
Reading package lists... Done
[COLOR="Red"]W: GPG error: http://il.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/COLOR]

```

> 
also you may need to add the lines to your /etc/apt/sources.list
for retrieving updates now that the final release is out.


I did thru synaptic, as explained in the ubuntu wiki.

---

### Post by kroiz on 2005-10-19
I reinstalled and the problem is gone.

---

