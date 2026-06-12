---
title: "Not able to install the ttf-mscorefonts-installer package on UbuntuGNOME 16.04"
date: 2016-07-06
forum: General Help
---

### Post by cdysthe on 2016-07-06
Hi,

I am trying to install the ttf-mscorefonts-installer package on UbuntuGNOME 16.04

I get the following errors in the terminal when trying to install:

ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 1s (111 kB/s)                                                                
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe) [554 kB]
Fetched 554 kB in 2s (205 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe) [168 kB]
Fetched 168 kB in 0s (222 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arialb32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)      
  The HTTP server sent an invalid Content-Range header
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/comic32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [http://superb-sea2.dl.sourceforge.net/project/corefonts/the](http://superb-sea2.dl.sourceforge.net/project/corefonts/the) fonts/final/comic32.exe  The HTTP server sent an invalid Content-Range header

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...

Later I get a popup with this message daily:

Failure to download extra data files
The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.
ttf-mscorefonts-installer
The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

I need those fonts so I was hoping someone could help me out.

---

### Post by grahammechanical on 2016-07-06
Did you prefix the command with sudo? Did you accept the Microsoft End User License Agreement (EULA)?

---

### Post by QDR06VV9 on 2016-07-06
Try this:
```
sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*
```
Followed by:
```
sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
```
And post back any errors.

---

### Post by Impavidus on 2016-07-06
> **cdysthe said:**
> The HTTP server sent an invalid Content-Range header

E: Download Failed

Could be a server error. Try again later. First run runrickus's commands for cleanup, just to be sure.

---

