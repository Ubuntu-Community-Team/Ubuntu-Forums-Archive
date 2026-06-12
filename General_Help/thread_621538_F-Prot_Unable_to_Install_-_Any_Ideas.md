---
title: "F-Prot Unable to Install - Any Ideas??"
date: 2007-11-23
forum: General Help
---

### Post by OzzyFrank on 2007-11-23
I recently tried to install F-Prot antivirus in Gutsy but it seems to have only completed half way, and now whenever I update my system or install new packages the "f-prot-installer" pops up again for another useless attempt at installing itself. I have tried suggested commands like "dpkg --configure f-prot-installer" to no avail. Whether I choose for it to use the downloaded version of "fp-linux-ws.tar.gz" or to download it itself, it claims it can never find it. In case it helps, I'll paste the terminal output from when the installer tried to proceed again during installation of another package, and what follows with the dpkg command above. Hope someone can shed some light on this! I just uninstalled it so I wouldn't keep getting bugged by it every time I get updates, but would like to reinstall it properly if I can. Cheers.

1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up f-prot-installer (0.5.22) ...
installing f-prot
looking for F-prot in /home/ozzman/Downloads/fp-linux-ws.tar.gz
.
fp-linux-ws.tar.gz.md5 was not found. Please identify the 
correct directory and re-run update-f-prot
.
.
fp-linux-ws.tar.gz was not found in /home/ozzman/Downloads/fp-linux-ws.tar.gz. Please
re-run update-f-prot with the correct directory
as argument following the -d option
.
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
ozzman@ozzman-desktop:~$ dpkg --configure f-prot-installer
dpkg: requested operation requires superuser privilege
ozzman@ozzman-desktop:~$ sudo dpkg --configure f-prot-installer
Setting up f-prot-installer (0.5.22) ...
installing f-prot
looking for F-prot in /home/ozzman/Downloads/fp-linux-ws.tar.gz
.
fp-linux-ws.tar.gz.md5 was not found. Please identify the 
correct directory and re-run update-f-prot
.
.
fp-linux-ws.tar.gz was not found in /home/ozzman/Downloads/fp-linux-ws.tar.gz. Please
re-run update-f-prot with the correct directory
as argument following the -d option
.
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer

**[COLOR="Purple"]Here's what I get when I try to install from scratch, and telling it to download the file it needs:[/COLOR]**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  f-prot-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.1kB of archives.
After unpacking 180kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package f-prot-installer.
(Reading database ... 276771 files and directories currently installed.)
Unpacking f-prot-installer (from .../f-prot-installer_0.5.22_i386.deb) ...
Setting up f-prot-installer (0.5.22) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that 
    your computer is connected to the Internet. 
    If you see this error although you are 
    connected, either the server is down or the 
    download location has changed. In the latter
    case you can still download the files manually. 
    Please file a bug report against 
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

