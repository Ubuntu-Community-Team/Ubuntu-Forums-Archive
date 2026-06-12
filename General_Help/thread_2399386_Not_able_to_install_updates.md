---
title: "Not able to install updates"
date: 2018-08-24
forum: General Help
---

### Post by linuxyogi on 2018-08-24
How to solve this ?

I have done

```
sudo apt-get clean 
``` and

```
sudo rm -r /var/lib/apt/lists/* 
```

but problem remains.

```
$ sudo apt update 
[sudo] password for ubuntu: 
Get:1 http://in.archive.ubuntu.com/ubuntu bionic InRelease [242 kB]            
Get:2 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:3 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:4 http://in.archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]  
Get:5 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1,019 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1,007 kB] 
Get:7 http://in.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]  
Get:8 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Get:11 http://in.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [9,184 B]
Get:12 http://in.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages [9,156 B]
Get:13 http://in.archive.ubuntu.com/ubuntu bionic/restricted Translation-en [3,584 B]
Get:14 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:15 http://in.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8,531 kB]
Err:16 http://APT.spideroak.com/ubuntu-spideroak-hardy release InRelease       
  Could not connect to APT.spideroak.com:80 (74.126.144.80), connection timed out
Get:17 http://in.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4,941 kB]
Get:18 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Get:19 http://in.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons [2,151 kB]
Get:20 http://in.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8,420 kB]
Get:21 http://in.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages [144 kB]
Get:22 http://in.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
Get:23 http://in.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
Get:24 http://in.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Get:25 http://in.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 48x48 Icons [8,931 B]
Get:26 http://in.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:27 http://in.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [271 kB]
Err:27 http://in.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages   
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:270872 [weak]
   - SHA256:b152c1d28cb1bc2362ac18b36a7bf617c31fd6c905898eda8851c24e2189aee1
   - SHA1:dc2c6b3bef755a7e1bd834137043e1f7b2e6aea6 [weak]
   - MD5Sum:7378cf644297c969abe33596045e21df [weak]
  Hashes of received file:
   - SHA256:8af24f14f122ab7a1346179f80d89f65eb8cd932f915a4225c7ef86a15692815
   - SHA1:0eb28a818c8b7c87d3f04ce30a71ff6a0ea7acd6 [weak]
   - MD5Sum:b9bb7dfc18f0e2e85b608b9a0d733e98 [weak]
   - Filesize:270872 [weak]
  Last modification reported: Fri, 24 Aug 2018 12:59:29 +0000
  Release file created at: Fri, 24 Aug 2018 12:59:21 +0000
Get:28 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [301 kB]
Get:29 http://in.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [114 kB]
Get:30 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [138 kB]
Get:31 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [31.4 kB]
Get:32 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [53.7 kB]
Get:33 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [172 kB]
Get:34 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [172 kB]
Err:34 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
  
Get:35 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [79.6 kB]
Get:36 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [153 kB]
Get:37 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [155 kB]
Get:38 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [2,704 B]
Get:39 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages [2,704 B]
Get:40 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en [1,136 B]
Get:41 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:42 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]
Get:43 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1,789 B]
Get:44 http://in.archive.ubuntu.com/ubuntu bionic-security/main i386 Packages [127 kB]
Get:45 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages [157 kB]
Get:46 http://in.archive.ubuntu.com/ubuntu bionic-security/main Translation-en [60.5 kB]
Get:47 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:48 http://in.archive.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]
Get:49 http://in.archive.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]
Get:50 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [56.9 kB]
Get:51 http://in.archive.ubuntu.com/ubuntu bionic-security/universe i386 Packages [56.7 kB]
Get:52 http://in.archive.ubuntu.com/ubuntu bionic-security/universe Translation-en [33.4 kB]
Get:53 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [6,820 B]
Get:54 http://in.archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,090 B]
Get:55 http://in.archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [11.3 kB]
Get:56 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages [1,608 B]
Get:57 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1,444 B]
Get:58 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [996 B]
Fetched 42.7 MB in 1min 29s (479 kB/s)                                         
Reading package lists... Done
W: Failed to fetch http://APT.spideroak.com/ubuntu-spideroak-hardy/dists/release/InRelease  Could not connect to APT.spideroak.com:80 (74.126.144.80), connection timed out
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-i386/by-hash/SHA256/b152c1d28cb1bc2362ac18b36a7bf617c31fd6c905898eda8851c24e2189aee1  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:270872 [weak]
    - SHA256:b152c1d28cb1bc2362ac18b36a7bf617c31fd6c905898eda8851c24e2189aee1
    - SHA1:dc2c6b3bef755a7e1bd834137043e1f7b2e6aea6 [weak]
    - MD5Sum:7378cf644297c969abe33596045e21df [weak]
   Hashes of received file:
    - SHA256:8af24f14f122ab7a1346179f80d89f65eb8cd932f915a4225c7ef86a15692815
    - SHA1:0eb28a818c8b7c87d3f04ce30a71ff6a0ea7acd6 [weak]
    - MD5Sum:b9bb7dfc18f0e2e85b608b9a0d733e98 [weak]
    - Filesize:270872 [weak]
   Last modification reported: Fri, 24 Aug 2018 12:59:29 +0000
   Release file created at: Fri, 24 Aug 2018 12:59:21 +0000
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-amd64/by-hash/SHA256/2176764ea0a9f7a411be49343b6f91495de4945bce8cfc9c7146984dd313dbeb  
W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by TheFu on 2018-08-24
To start, perhaps removing a hardy repo would help?  Seems a little old.

---

### Post by ajgreeny on 2018-08-24
Have you actually tried running ```
sudo apt upgrade
``` command following your problems with the **update** command?

Most of the repos seem to have updated OK, not the hardy ones of course, so you may get all the packages that are able to be upgraded.
If there are continual problems with miss-matches of the hash-sums you may also find it worth using other repository archives, eg the main repos instead of your in.archive version.

---

### Post by linuxyogi on 2018-08-25
All seems okay today.

```
$ sudo apt update 
[sudo] password for ubuntu: 
Hit:1 http://in.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Hit:4 http://APT.spideroak.com/ubuntu-spideroak-hardy release InRelease        
Get:5 http://in.archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Fetched 247 kB in 1s (222 kB/s)                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.


```


```
$ sudo apt upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-mutter-2 gnome-shell gnome-shell-common libmutter-2-0 mutter
  mutter-common
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,220 kB of archives.
After this operation, 260 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 213520 files and directories currently installed.)
Preparing to unpack .../0-mutter-common_3.28.3-2~ubuntu18.04.1_all.deb ...
Unpacking mutter-common (3.28.3-2~ubuntu18.04.1) over (3.28.2-2~ubuntu18.04.1) ...
Preparing to unpack .../1-gir1.2-mutter-2_3.28.3-2~ubuntu18.04.1_amd64.deb ...
Unpacking gir1.2-mutter-2:amd64 (3.28.3-2~ubuntu18.04.1) over (3.28.2-2~ubuntu18.04.1) ...
Preparing to unpack .../2-libmutter-2-0_3.28.3-2~ubuntu18.04.1_amd64.deb ...
Unpacking libmutter-2-0:amd64 (3.28.3-2~ubuntu18.04.1) over (3.28.2-2~ubuntu18.04.1) ...
Preparing to unpack .../3-gnome-shell_3.28.3-0ubuntu0.18.04.2_amd64.deb ...
Unpacking gnome-shell (3.28.3-0ubuntu0.18.04.2) over (3.28.2-0ubuntu0.18.04.1) ...
Preparing to unpack .../4-gnome-shell-common_3.28.3-0ubuntu0.18.04.2_all.deb ...
Unpacking gnome-shell-common (3.28.3-0ubuntu0.18.04.2) over (3.28.2-0ubuntu0.18.04.1) ...
Preparing to unpack .../5-mutter_3.28.3-2~ubuntu18.04.1_amd64.deb ...
Unpacking mutter (3.28.3-2~ubuntu18.04.1) over (3.28.2-2~ubuntu18.04.1) ...
Processing triggers for gconf2 (3.2.6-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Setting up mutter-common (3.28.3-2~ubuntu18.04.1) ...
Processing triggers for libglib2.0-0:amd64 (2.56.1-2ubuntu1) ...
Setting up gnome-shell-common (3.28.3-0ubuntu0.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Setting up libmutter-2-0:amd64 (3.28.3-2~ubuntu18.04.1) ...
Setting up gir1.2-mutter-2:amd64 (3.28.3-2~ubuntu18.04.1) ...
Setting up mutter (3.28.3-2~ubuntu18.04.1) ...
Setting up gnome-shell (3.28.3-0ubuntu0.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
```

The hardy repo is automatically added when I install SpiderOak.

Thanks for your replies.

---

### Post by TheFu on 2018-08-25
Sometimes repos are unavailable.
I would check that the spideroak repo is correct for the current release in their documentation and with their support team. It could be fine or they could just not have bothered to correct their installer.

---

### Post by linuxyogi on 2018-08-25
> **TheFu said:**
> Sometimes repos are unavailable.
I would check that the spideroak repo is correct for the current release in their documentation and with their support team. It could be fine or they could just not have bothered to correct their installer.

I think its fine

[https://spideroak.com/faq/what-are-the-apt-sources-lines-for-spideroak](https://spideroak.com/faq/what-are-the-apt-sources-lines-for-spideroak)

---

### Post by TheFu on 2018-08-25
But [http://apt.spideroak.com/ubuntu-spideroak-hardy](http://apt.spideroak.com/ubuntu-spideroak-hardy) returns a 404 error for me.  The link you posted is deprecated, BTW.
[https://spideroak.support/hc/en-us/articles/115001893103-What-Are-the-Apt-Sources-Lines-for-SpiderOak-](https://spideroak.support/hc/en-us/articles/115001893103-What-Are-the-Apt-Sources-Lines-for-SpiderOak-) is the new one ... 
It does say the same repo URL and also says
> Despite its poorly chosen name that suggests otherwise, the Ubuntu repository is in fact for the current version of Ubuntu.

I don't know what's up with the 404 error. Maybe they are looking at the user-agent?

---

### Post by linuxyogi on 2018-08-25
> **TheFu said:**
> But [http://apt.spideroak.com/ubuntu-spideroak-hardy](http://apt.spideroak.com/ubuntu-spideroak-hardy) returns a 404 error for me.  The link you posted is deprecated, BTW.
[https://spideroak.support/hc/en-us/articles/115001893103-What-Are-the-Apt-Sources-Lines-for-SpiderOak-](https://spideroak.support/hc/en-us/articles/115001893103-What-Are-the-Apt-Sources-Lines-for-SpiderOak-) is the new one ... 
It does say the same repo URL and also says


I don't know what's up with the 404 error. Maybe they are looking at the user-agent?

I think so coz  I am using the same repo for a long time with different versions of Ubuntu.

---

