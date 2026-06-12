---
title: "ttf-mscorefonts-installer error"
date: 2016-12-27
forum: General Help
---

### Post by zkab on 2016-12-27
I have 16.04.1 LTS and when I try to reinstall ttf-mscorefonts-installer I get errors:

```
~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 29,5 kB of archives.
After this operation, 0 B of additional disk space will be  sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 29,5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://se.archive.ubuntu.com/ubuntu xenial/multiverse amd64 ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29,5 kB]
Fetched 29,5 kB in 0s (318 kB/s)                     
Preconfiguring packages ...
(Reading database ... 247065 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Err:1 http://downloads.sourceforge.net/corefonts/andale32.exe
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch https://vorboss.dl.sourceforge.net/project/corefonts/the fonts/final/andale32.exe  404  Not Found

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...used.
Get:1 http://se.archive.ubuntu.com/ubuntu xenial/multiverse amd64 ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29,5 kB]
Fetched 29,5 kB in 0s (318 kB/s)                     
Preconfiguring packages ...
(Reading database ... 247065 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Err:1 http://downloads.sourceforge.net/corefonts/andale32.exe
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch https://vorboss.dl.sourceforge.net/project/corefonts/the fonts/final/andale32.exe  404  Not Found

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
```

What is wrong ?

---

### Post by howefield on 2016-12-27
The script that the the package runs in order to download the fonts from the sourceforge server is broken. I'd suggest purging the 3.4 version of the package that you are trying to install and instead install the 3.6 version.

```
sudo apt purge ttf-mscorefonts-installer
```

```
wget [http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb](http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb) -P ~/Downloads
```

will download the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by zkab on 2016-12-27
Thanks

---

### Post by m3asmi-gmail on 2017-01-03
Thanks

---

### Post by stormhike on 2017-01-27
Many thanks howefield, good post.

---

### Post by howefield on 2017-01-27
> **zkab said:**
> Thanks

> **m3asmi-gmail said:**
> Thanks

> **stormhike said:**
> Many thanks howefield, good post.

Cool, you are all welcome. :)

---

