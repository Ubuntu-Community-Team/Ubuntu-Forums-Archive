---
title: "error processing archive /var/cache/apt/archives/libjpeg62-turbo-dev_1%3a1.3.1-12_amd"
date: 2020-02-27
forum: General Help
---

### Post by thecowmilk on 2020-02-27
Hello all, I have Ubuntu 18.04 LTS and today after a normal `dist-upgrade` Ubuntu is not installing correctly ```
libjpeg62-turbo-dev:amd64 (1:1.3.1-12
```

As you can see in title that's the error it shows to me. I ran also `sudo apt --fix-broken install` but it gives me the same error. Let me paste the whole output of my terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libicu64 libjpeg-turbo8-dev
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libjpeg62-turbo-dev
The following NEW packages will be installed:
  libjpeg62-turbo-dev
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/455 kB of archives.
After this operation, 2.802 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 219059 files and directories currently installed.)
Preparing to unpack .../libjpeg62-turbo-dev_1%3a1.3.1-12_amd64.deb ...
Unpacking libjpeg62-turbo-dev:amd64 (1:1.3.1-12) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg62-turbo-dev_1%3a1.3.1-12_amd64.deb (--unpack):
 trying to overwrite '/usr/include/jpeglib.h', which is also in package libjpeg-turbo8-dev:amd64 1.5.2-0ubuntu5.18.04.3
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg62-turbo-dev_1%3a1.3.1-12_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help would be very appreciated :D

---

### Post by deadflowr on 2020-02-27
Where is that package even coming from?
It doesn't seem to exist in Ubuntu.
Is it from a PPA?

---

### Post by thecowmilk on 2020-02-27
Idk tbh... I have only two PPA on my sources.list
One is PHP and the other is:

[http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) bionic InRelease

---

### Post by deadflowr on 2020-02-27
Looks like the same (more or less) issue as this unresolved(?) thread:
[https://ubuntuforums.org/showthread.php?t=2315301]("https://ubuntuforums.org/showthread.php?t=2315301")
Not sure what to go with it, but perhaps you can glean something from it.

---

### Post by thecowmilk on 2020-02-27
> **deadflowr said:**
> Looks like the same (more or less) issue as this unresolved(?) thread:
[https://ubuntuforums.org/showthread.php?t=2315301](https://ubuntuforums.org/showthread.php?t=2315301)
Not sure what to go with it, but perhaps you can glean something from it.

I see, well that didn't exactly resolved my problem :/. Idk if this help but in my Ubuntu has shown an icon which says: "Error BrokenCount > 0"

Also thank you so much for your attention though, if you want you can share this thread to your friends if they have any idea. Thanks :D

---

### Post by thecowmilk on 2020-02-28
Okay I have solved this problem myself and I did it in this way:

When running "sudo apt upgrade" it outputs me the error above. So I decided to install them manually. At first I tried to install manually "libjpeg-dev_1.3.1-12_all.deb" but I had this output:

" dependency problems prevent configuration of libjpeg-dev: libjpeg-dev depends on libjpeg62-turbo-dev (>= 1:1.3.1-12); however:
  Package libjpeg62-turbo-dev:amd64 is not installed."

So I went to this page: [https://packages.debian.org/sid/amd64/libjpeg62-turbo/download](https://packages.debian.org/sid/amd64/libjpeg62-turbo/download) and downloaded the dependency from there and installed it from running: sudo dpkg -i libjpeg62-turbo_1.5.2-2+b1_amd64.deb"

Also make sure you will do a backup of " /var/lib/apt/lists/" and then remove it: "sudo -r /var/lib/apt/lists/* -vf" then make "sudo apt update" and install them manually again. Thanks :D

---

