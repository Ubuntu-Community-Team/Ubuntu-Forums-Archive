---
title: "PPA and Cache"
date: 2017-05-09
forum: General Help
---

### Post by anon_private on 2017-05-09
I understand that when I install a new PPA the apt cache needs to be updated. Where is the apt cache?

---

### Post by deadflowr on 2017-05-09
The cache is updated whenever you successfully run *sudo apt-get update*.

---

### Post by anon_private on 2017-05-09
Where is the cache?

---

### Post by ian-weisser on 2017-05-09
The package database ("apt cache") is located in /var/lib/dpkg and /var/lib/apt

WARNING: DO NOT attempt to change, update, nor 'fix' the package database manually.
Doing so may break your system quite horribly.

---

### Post by deadflowr on 2017-05-09
/var/lib/apt/lists contains the updated Packages files, which contain the updated information on the available packages for all archives you use.
Again, this is updated whenever you run the apt-get update command successfully.
At the end of *man apt-cache* it reads as:
> FILES
       /etc/apt/sources.list
           Locations to fetch packages from. Configuration Item:
           Dir::Etc::SourceList.

       /etc/apt/sources.list.d/
           File fragments for locations to fetch packages from. Configuration
           Item: Dir::Etc::SourceParts.

       /var/lib/apt/lists/
           Storage area for state information for each package resource
           specified in sources.list(5) Configuration Item: Dir::State::Lists.

       /var/lib/apt/lists/partial/
           Storage area for state information in transit. Configuration Item:
           Dir::State::Lists (partial will be implicitly appended)

If that helps

---

### Post by anon_private on 2017-05-10
> **deadflowr said:**
> /var/lib/apt/lists contains the updated Packages files, which contain the updated information on the available packages for all archives you use.
Again, this is updated whenever you run the apt-get update command successfully.
At the end of *man apt-cache* it reads as:


If that helps


That does look like the cache.

I expected to see a folder labelled cache.

---

### Post by vasa1 on 2017-05-10
> **ian-weisser said:**
> The package database ("apt cache") is located in /var/lib/dpkg and /var/lib/apt

WARNING: DO NOT attempt to change, update, nor 'fix' the package database manually.
Doing so may break your system quite horribly.
+1.

This cache isn't like other caches that one may clean out.

---

### Post by deadflowr on 2017-05-10
> **anon_private said:**
> That does look like the cache.

I expected to see a folder labelled cache.

There is.
But it's related to the downloaded packages you installed your applications from.
That's in /var/cache/apt/archives.

To note: apt-get stores the packages in here until you clean it out either *apt-get clean* (which wipes it all out) or with *apt-get autoclean* (which only removes those packages which the system deems obsolete; packages that have newer versions already installed, or packages you may have removed and no longer installed)

The newly minted apt command, such as *sudo apt update*, or *sudo apt install <package>* sets it so that the cache archive folder only holds the packages until the packages is successfully installed, and then it removes it. Or at least that's the default setting in Ubuntu.

So if you run apt with instead of apt-get, expect that folder to remain, mostly empty.

hope that adds something useful.

---

### Post by vasa1 on 2017-05-10
> **anon_private said:**
> That does look like the cache.

I expected to see a folder labelled cache.
In the context of apt update, that isn't the case. Read [https://debian-handbook.info/browse/stable/sect.apt-cache.html](https://debian-handbook.info/browse/stable/sect.apt-cache.html) for more:> The apt-cache command can display much of the information stored in APT's internal database. This information is a sort of cache since it is gathered from the different sources listed in the sources.list file. This happens during the apt update operation.
So, to repeat, in this context, don't expect to see a folder named cache. The cache in */var/cache/apt/archives* is entirely different functionally as explained in the previous post.

Just as an example, I ran *sudo apt-get update* and then checked to see what changed in the folders mentioned by ian-weisser:```
$ sudo apt-get update
[sudo] password for vasa1: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release               
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]           
Get:6 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]          
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [530 kB] 
Hit:8 http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/peek-developers/stable/ubuntu xenial InRelease      
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [461 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [8,932 B]
Fetched 1,204 kB in 4s (261 kB/s)                            
Reading package lists... Done
$ find /var/lib/apt/lists /var/lib/dpkg -mmin -5 -type f
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-amd64_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-updates_InRelease
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages
find: &#8216;/var/lib/apt/lists/partial&#8217;: Permission denied
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages
$ 

```

---

