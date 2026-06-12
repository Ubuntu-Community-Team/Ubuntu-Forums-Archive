---
title: "Missing /usr/sbin/tzconfig"
date: 2007-12-31
forum: General Help
---

### Post by ufpost on 2007-12-31
Hello - 

     While attempting to execute "sudo apt-get upgrade" (immediately after "sudo apt-get update"), I receive the following:
> ubuntu@ubuntu-laptop:/var/lib/dpkg/info$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools initscripts
The following packages will be upgraded:
  clamav clamav-base clamav-freshclam libclamav2 libgd2-noxpm libsmbclient
  linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic samba-common smbclient wine
11 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/39.7MB of archives.
After unpacking 1495kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Setting up tzdata (2007j-1etch1) ...
Running 'tzconfig' to set this system's timezone.
/var/lib/dpkg/info/tzdata.postinst: line 27: /usr/sbin/tzconfig: No such file or directory
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu-laptop:/var/lib/dpkg/info$ 

As given above, the /usr/sbin/tzconfig file is missing. After browsing the forums, I attempted to execute "sudo dpkg-reconfigure tzdata" However, I receive the following error message:
> /usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed

I have also attempted "sudo apt-get install tzdata" Unfortunately, apt-get wants to run /usr/sbin/tzconfig before completing the installation. If I try to remove the tzdata package, apt-get wants to remove a series of critical packages. 

In reviewing my apt\term.log file, the log on 2007-12-30 shows an entry to update the tzdata package. The apt-get utility had not previously attempted to execute tzconfig prior to this log entry, and has errored out since (thereby preventing the upgrade or installation of any packages whatsoever):
> Preparing to replace tzdata 2007j-0ubuntu0.7.10 (using .../tzdata_2007j-1etch1_all.deb
)


It seems odd that the 0ubuntu0.7.10 version would be overridden by the 1etch1_all version since all enabled entries in my /etc/apt/sources.list file point to gusty repositories, except the following:

> deb [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free
deb-src [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free


I have disabled all the gusty backport apt-get sources. 

Any suggestions? 

Thanks!

---

### Post by dcstar on 2007-12-31
> **ufpost said:**
> 
..........
It seems odd that the 0ubuntu0.7.10 version would be overridden by the 1etch1_all version since all enabled entries in my /etc/apt/sources.list file point to gusty repositories, except the following:

```
deb ftp://ftp.au.debian.org/debian stable main contrib non-free
deb-src ftp://ftp.au.debian.org/debian stable main contrib non-free
```

I have disabled all the gusty backport apt-get sources. 

Any suggestions? 

Thanks!

You have non-Ubuntu repositories in your system, this sort of thing causes the exact sort of problems you are now experiencing.

Remove the Debian repositories and then reinstall the Ubuntu version of all the packages in your system from those bad repositories.

Ubuntu <> Debian, Ubuntu is **based** on Debian but with differences.

---

### Post by ufpost on 2008-01-01
Thanks - in case others find a similar situation, I used the following to clear-up the mess:

> sudo dpkg -i --force-downgrade tzdata_2007j-0ubuntu0.7.10_all.deb

Here, tzdata_2007j-0ubuntu0.7.10_all.deb is the previous package provided by running:

>  dpkg -s tzdata

I then removed the aforementioned sources from the /etc/apt/sources.list file. 

Working fine...may recommend a redundancy in the packages to pre-clear distros (or the main branches therefrom).

---

### Post by PA28 on 2008-01-02
I'm having the same problem.

For me, **dpgk -s tzdata** returns:

Package: tzdata
Status: install ok half-configured
Priority: required
Section: libs
Installed-Size: 5768
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Architecture: all
Version: 2007k-0ubuntu0.7.04
Config-Version: 2007j-0ubuntu0.7.10
Replaces: libc0.1, libc0.3, libc6, libc6.1, locales
Description: ........

I've tried running these two commands with no luck.
[B]sudo dpkg -i --force-downgrade tzdata_2007j-0ubuntu0.7.10_all.deb
sudo dpkg -i --force-downgrade tzdata_2007k-0ubuntu0.7.04_all.deb[/B]

They both return something similar to:

dpkg: error processing tzdata_2007k-0ubuntu0.7.04_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 tzdata_2007k-0ubuntu0.7.04_all.deb

I'm not quite sure where to go from here, so any ideas or help would be much appreciated.

Thanks in advance,
PA28

---

### Post by PA28 on 2008-01-06
I've solved the above problem. Should anyone have the same issue this is how I fixed it.

First, I found a copy of the latest version of tzdata. In my case it was **tzdata_2007k-0ubuntu0.7.10_all.deb**. I downloaded the copy to my home folder, and ran the following commands.

[B]cd
sudo dpkg -i tzdata_2007k-0ubuntu0.7.10_all.deb[/B]

The reason why this command wasn't working in my previous post was that I had cleared my APT cache. Therefore even though my working directory was APT archive (which was correct), the tzdata package the dpkg command was looking for wasn't there.... therefore command failed.

By the way, should anyone need a copy of tzdata, I got mine from the Internode Mirror (Australia).
[http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/t/tzdata/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/t/tzdata/)

All the best,
PA28

---

