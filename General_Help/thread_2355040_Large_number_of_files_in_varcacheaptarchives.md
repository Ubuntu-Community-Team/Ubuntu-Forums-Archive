---
title: "Large number of files in /var/cache/apt/archives"
date: 2017-03-08
forum: General Help
---

### Post by raleigh3 on 2017-03-08
I noticed about 217 Mb of .deb files here.

```
/var/cache/apt/archives
```

What are they used for ?

Thanks.

---

### Post by howefield on 2017-03-08
That folder is where the deb packages are downloaded to when you install an application or update the system.

---

### Post by deadflowr on 2017-03-08
^That.
It also allows you to easily purge the package and reinstall without the need to re-download the whole thing again.
You can run two different commands to clear it out, if you want.
```
sudo apt-get clean
``` 
will clear the folder out completely.
And
```
sudo apt-get autoclean
```
will clear out any packages for versions of software no longer the version installed (or software no longer installed at all) on the system, so
let's say you have firefox packages for firefox 48 49 50 and 51, and th newest version is 51, the autoclean command clears out those older version (48 49 50), 
but version 51 will remain.
If that makes sense.

---

### Post by vasa1 on 2017-03-09
> **howefield said:**
> That folder is where the deb packages are downloaded to when you install an application or update the system.

I have a thread about apt and apt-get here: [https://ubuntuforums.org/showthread.php?t=2319347](https://ubuntuforums.org/showthread.php?t=2319347)

In post #8 there, I posted about apt, *when default settings are used*, automatically removing debs from cache if the installation is successful.

Have things changed since then (April 2016)?

I just used the default settings to run```
sudo apt install aha
```which is a tiny package.

```
apt-cache policy aha
aha:
  Installed: 0.4.8-1
  Candidate: 0.4.8-1
  Version table:
 *** 0.4.8-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

There's no trace of its deb in */var/cache/apt/archives*.

---

### Post by howefield on 2017-03-09
> **vasa1 said:**
> In post #8 there, I posted about apt, *when default settings are used*, automatically removing debs from cache if the installation is successful.

Not sure if it has changed, I made a note to investigate how it is supposed to work a while back but it's hasn't been important enough for me to find the time as yet.

I installed from a daily image (7th March) of Zesty two days ago, immediately after the install I run..

```
sudo apt purge ubuntu-software gnome-software thunderbird && sudo apt autoremove
```

And then installed packages totalling around 190MB.

Run a apt upgrade yesterday and all that is in the /var/cache/apt/archives/ is those updates from yesterday.

```
ls /var/cache/apt/archives/
gir1.2-pango-1.0_1.40.4-1_amd64.deb     libpango-1.0-0_1.40.4-1_amd64.deb       libpangoxft-1.0-0_1.40.4-1_amd64.deb
intel-microcode_3.20161104.1_amd64.deb  libpangocairo-1.0-0_1.40.4-1_amd64.deb  lock
iucode-tool_2.1.1-1_amd64.deb           libpangoft2-1.0-0_1.40.4-1_amd64.deb    partial
```

---

### Post by raleigh3 on 2017-03-09
Thanks for all the responses.

---

