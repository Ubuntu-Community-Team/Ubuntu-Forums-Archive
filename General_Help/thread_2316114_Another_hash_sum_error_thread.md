---
title: "Another hash sum error thread"
date: 2016-03-05
forum: General Help
---

### Post by vasa1 on 2016-03-05
On running *sudo apt-get update* I've started seeing this:```
...
Fetched 9,376 kB in 1min 49s (85.6 kB/s)                                       
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Running```
sudo rm -rf /var/lib/apt/lists/*
```as suggested [here]("http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error"), for example, followed by *sudo apt-get update* didn't fix it.

Switching from *main* to a local mirror also didn't fix it.

If I go into *Software sources* and untick the "partner" entry, I don't get the message/error.

How can I tell which software, if any, on my system is from the *partner* repository?

Edit:> The Canonical Partner repository offers some proprietary applications that don't cost any money to use but are closed source. They include software like Skype, Adobe Reader and Adobe Flash Plugin. Software in this repository will appear in Ubuntu Software Center search results but won't be installable until this repository is enabled.Source: [https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html)

---

### Post by QDR06VV9 on 2016-03-05
Per say i don't know of a command that will be that discrete..
But maybe some of these might be of use
```
dpkg -s <package> - allows you to find the version of that you have installed. (source)
  apt-cache showpkg <package> - will show a list of Versions of the package available. For each version, the source of the package, in the form of an index file name, will be given.
```
If you want to find the source of the package that's currently installed, you'll need the output of dpkg -s <package>. Otherwise, you can simply look at the newest version output by 
```
apt-cache showpkg <package>.
```
> Example:

$ dpkg -s liferea
Package: liferea
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 760
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1.6.2-1ubuntu6
...

$ apt-cache showpkg liferea
Package: liferea
Versions: 
1.6.2-1ubuntu6.1 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages
                  MD5: 557b0b803b7ed864e6d14df4b02e3d26

1.6.2-1ubuntu6 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages
                  MD5: 557b0b803b7ed864e6d14df4b02e3d26
But i am sure you probably already knew about those.
One other thing to try is Changing the source of the Update Server maybe to Main or the closest to where you are but Main works well for me.
Kind Regards

---

### Post by vasa1 on 2016-03-05
Hi runrickus, I wonder if [vrms]("http://ubuntuforums.org/showthread.php?t=2285306&p=13315333#post13315333") provides that same information in some mysterious way.

On my system, I get:```
09:37 AM ~ $ vrms
        Non-free packages installed on vasa1-Inspiron-1545

libfdk-aac0                         Fraunhofer FDK AAC Codec Library - runtime files

         Contrib packages installed on vasa1-Inspiron-1545

b43-fwcutter                        utility for extracting Broadcom 43xx firmware
firmware-b43-installer              firmware installer for the b43 driver

  1 non-free packages, 0.1% of 1543 installed packages.
  2 contrib packages, 0.1% of 1543 installed packages.
09:37 AM ~ $ 
```

Anyway, my "hash sum mismatch" problem went away this morning but not before delivering a parting kick:```
Fetched 1,956 kB in 23s (81.9 kB/s)                                            
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages  Bad header line [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
06:34 AM ~ $ 

```And I do normally use the "main" server but I checked a couple of other servers across the world as well. The same issue persisted.

From what I read, this is just one of those things that go away if ignored ;)

---

### Post by sammiev on 2016-03-06
> **vasa1 said:**
> From what I read, this is just one of those things that go away if ignored ;)

I have seen that message many of times. Usually it goes away within a few hours.

I hope it works out for you.

---

### Post by vasa1 on 2016-03-06
> **sammiev said:**
> I have seen that message many of times. Usually it goes away within a few hours.

I hope it works out for you.

This is the first time it happened since I started using Linux with 11.04. So I panicked.

Next time, I'll be "cool" :)

---

