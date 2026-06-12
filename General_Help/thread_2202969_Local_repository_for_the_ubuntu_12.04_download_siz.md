---
title: "Local repository for the ubuntu 12.04 download size"
date: 2014-02-01
forum: General Help
---

### Post by niraj2 on 2014-02-01
HI

  I have installed the ubuntu server 12.04 and creating a local repository for the  ubuntu 12.04.

when I run the following command its gives the following output  in output showing the 108 GB download so it will download the that much data ???

If yes then If I want to decreasing the size of it would it possible ??? 



maven@lb2:~$ sudo apt-mirror /etc/apt/mirror.list
[sudo] password for maven: 
Downloading 84 index files using 20 threads...
Begin time: Fri Jan 31 22:33:35 2014
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Fri Jan 31 22:34:08 2014


Proceed indexes: [SSSPPP]


108.4 GiB will be downloaded into archive.
Downloading 105358 archive files using 20 threads...
Begin time: Fri Jan 31 22:34:21 2014
[20]...

---

### Post by mikewhatever on 2014-02-01
The size can probably be reduced by removing some of the repositories, but first, you'll have to show us what they are.
It seems to me the content of /etc/apt/mirror.list config file is essential here, and you've probably just forgot to add it. Please do so.

---

### Post by niraj2 on 2014-02-01
Hi

Please find the details of mirror.list

deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse
#deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-proposed main restricted universe multiverse
#deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse


deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse
#deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-proposed main restricted universe multiverse
#deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse


clean [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu)
~

---

### Post by mikewhatever on 2014-02-01
Thanks.
You can try and comment out all the deb-src packages if you don't need access to the source code, or the universe repository, etc. It looks like Precise has lots of packages available.

---

### Post by btindie on 2014-02-01
Have you looked at [apt-cacher-ng]("http://www.unix-ag.uni-kl.de/~bloch/acng/") ? It'd save you having to download 10's of GB of data as it just acts as a caching proxy so you only get what you need.

To use it on a client, you just need to
> Specify the caching machine as HTTP Proxy for APT, e.g. putting a line like the following into a file like /etc/apt/apt.conf.d/02proxy:
Acquire::http { Proxy "http://CacheServerIp:3142"; };

---

### Post by niraj2 on 2014-02-02
Hi

  My only purpose is to all my user with ubuntu 12.04  will get the all required update from local repository. If I comment the deb-src it will not affected the user update ???

---

### Post by varunendra on 2014-02-02
> **niraj2 said:**
> My only purpose is to all my user with ubuntu 12.04  will get the **[COLOR="#0000CD"]all required update[/COLOR]** from local repository. If I comment the deb-src it will not affected the user update ???

"All required updates" is the keyword. Source packages are rarely needed. A normal installation of packages only needs the binary (.deb) packages. Source code is only needed, as far as I know, if you need to compile the binary yourself with some changes/modifications in the source.

The 'proposed' and 'backports' repositories are already commented out, so nothing to add there.

I remember the default offline repository size (without the deb-src repos) for 9.04 (Jaunty) being about 28 GB, and the same for 10.04 (Lucid) being about 37 GB. The size of deb-src is obviously bigger than the binary packages. So I believe just commenting out the deb-src repositories would bring down the size to less than half of its current estimate, that is, less than 54 GB. That should be able to provide everything that a normal user would ever want from 12.04.

**PS:**
Depending upon the availability of time you have, you may as well just select ALL the packages manually in Synaptic Package Manager that you think your users may ever want/need. They will automatically select their dependencies. Then when you click "Apply" button, check the checkbox that says "Download the packages only". This will download all the packages with dependencies into your /var/cache/apt/archives directory. Then you may use AptOnCD to create offline repository DVDs (ISOs, that you may burn to DVDs or directly use as Repositories) from these packages. This will work as a complete source as long as the users don't update their software cache with online repositories, and need only those packages that are available within these DVDs.

It's a perfect and cheapest (in terms of required download) solution if you know the needs of your users. Otherwise just disable the deb-src ones, and go with the standard solution.

---

### Post by niraj2 on 2014-02-03
Hi Varun

Thank you for details response. Let me disable the deb-src as I dont required now and then try the same.

---

### Post by varunendra on 2014-02-03
If you are in India or Australia, you may get a [12-DVD pack]("http://www.zyxware.com/requestcd/%252Fresults/field_distribution_name%3A%22Debian%22?page=1&title=&distribution_name=Ubuntu") of full repositories (main, universe, multiverse and restricted) from [Zyxware]("http://www.zyxware.com/requestcd") for a marginal amount (Rs.400/- for Ubuntu 12.04, Rs.700/- for a 16-DVD pack of 13.10).

The 12.04 pack states the size of the repositories to be 45 GB. They charge extra for shipping (can be reviewed on the order page), but is still cheaper if time and/or bandwidth is more valuable for you.

**PS:**
They currently seem to list only the latest release for latest packages, but based on a previous personal experience (when I ordered a pack for Jaunty), you may talk to them over telephone to create a set with latest packages for whatever release you want. This is probably their default way of working - they create repositories when a package is ordered, so it is automatically the latest, but it'd be a good idea to confirm that over telephone if you consider ordering a set.

**PPS:**
Also note that any offline repository, be it the one you create yourself, the AptOnCD one, or the above ones from Zyxware or anyone else, would only be reliable as long as your users don't update their software cache online. Once the software list gets updated with the online one, the package manager may want to not install the outdated offline packages, and IF *some* packages were updated from the online ones as well, it is possible for the offline repositories to become totally useless unless you could revert to old packages, purging the updated ones.

This is not usually a problem but it is a possibility you should be aware of. If you are not sure, it may be a good idea to keep a system backup handy, maybe an incremental one using rsync.

---

