---
title: "[SOLVED] File corruption?"
date: 2007-07-11
forum: General Help
---

### Post by Radicc on 2007-07-11
I was decided to go ahead an get the update for openoffice today or at least I thought I would.  I ended up getting an error when it tried to install the update about not being able to backup some file and wouldn't install.  
This error for anybody who is interested in that part:
> 
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/12.0MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 116463 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 unable to make backup link of `./usr/lib/openoffice/share/config/soffice.cfg/modules/schart/menubar/menubar.xml' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyway upon going to check whats up with this file I noticed that it seems to have gotten clobbered to the point that I don't know how to fix it.  The files permissions and owner and group are complete gibberish and I can't manipulate it with anything I have tried.  All the sudo command options I have tried to remove or modify the file result in access denied.  



> 
drwxr-xr-x  2 root    root       4096 2007-07-11 19:37 .
drwxr-xr-x  6 root    root       4096 2006-10-25 09:28 ..
?--x-----x 78 8192066 8257613 4456515 1970-02-25 22:08 menubar.xml


root owns the directory still so I would figure that I could sudo rm the file or something but had no such luck.
even more odd when I tried sudo touch menubar.xml it created a new file with the same name that is owned by root and I can't delete it either.

> drwxr-xr-x  2 root    root       4096 2007-07-11 19:47 .
drwxr-xr-x  6 root    root       4096 2006-10-25 09:28 ..
-rw-r--r--  1 root    root          0 2007-07-11 19:47 memubar.xml
?--x-----x 78 8192066 8257613 4456515 1970-02-25 22:08 menubar.xml


Suggestions welcome.

---

### Post by Radicc on 2007-07-13
Well I have managed to fix the problem on my own.  In my case I booted to the live cd and forced a scan of the file system using "sudo e2fsck -f /dev/sda1".  
Corrupted file gone.  Hope this helps someone else out.

---

