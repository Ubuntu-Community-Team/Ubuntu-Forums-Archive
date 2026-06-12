---
title: "package manager trouble"
date: 2007-06-22
forum: General Help
---

### Post by Lukeg on 2007-06-22
I recently tried to install a driver for my printer (Brother MFC 8500).  The driver was in a debian .deb file which I downloaded from Brothers website.  The installation did not complete successfully, citing a few errors (some files not existing, ect.).

However, then whenever I tried to install/upgrade *any* package, I received various error messages:

Adept Manager:
```
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
```

Synaptic (gives me the error message immediately after starting):
```
E: The package cupswrappermfc8500 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

I tried to reinstall it and got:
```

Reading database ... 214846 files and directories currently installed.)
Preparing to replace cupswrappermfc8500 1.0.2-1 (using .../cupswrapperMFC8500-1.0.2-1.i386.deb) ...
Unpacking replacement cupswrappermfc8500 ...
(Noting disappearance of mfc8500lpr, which has been completely replaced.)
/var/lib/dpkg/info/mfc8500lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing /home/luke/Desktop/cupswrapperMFC8500-1.0.2-1.i386.deb (--install):
 subprocess post-removal script (for disappearance) script returned error exit status 127
Errors were encountered while processing:
 /home/luke/Desktop/cupswrapperMFC8500-1.0.2-1.i386.deb
```

At this point I did some searching and found [the followin]("http://ubuntuforums.org/showthread.php?t=458098&highlight=package+manager+broke&page=2")g (which worked):
> 1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "virtualbox" you should find the following lines:
Package: virtualbox
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save

You should now be able to use synaptic again!
(I of course replaced "virtualbox" with the package in question)

As I said, this solved my problem, but it seems alittle blunt.  I must be missing something, is there an easier way to solve these problems in the future?  I also tried "sudo dpkg --force-remove-reinstreq --remove" to no avail.

---

### Post by RAH66 on 2007-06-25
:D I had exactly the same problem with synaptic with a half installed virtual box infact.

You are right this is a bit blunt so everytime a installation fails or something does this mean I have to go through this again? 

Anyway after reading what you said I decided to report the issue...

---

### Post by RAH66 on 2007-06-25
Hectic I saw that this issue kills any package manager (software update, synaptic, add remove gees...

---

### Post by canrith on 2007-06-26
I have been fighting with the Adept Manager. It is giving me the following error message:

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I don't see that there are multiple processes running. Looked in the Process table and only adept_notifier looked likely. Shutting it down has no effect and rebooting has no effect. I would appreciate any suggestions. Thanks

---

### Post by dabl on 2007-06-26
```
sudo dpkg --configure -a
```  :D

---

### Post by canrith on 2007-06-27
Thanks. It's amazing how simple it is if you know the code! :p

---

