---
title: "[SOLVED] Broken pakage - mfc8440lpr"
date: 2007-06-29
forum: General Help
---

### Post by altonbr on 2007-06-29
[QUOTE=update-manager]**Could not initialize the package information**

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.'[/QUOTE]
[QUOTE=synaptic]**An error occured**

The following details are provided:
> E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/QUOTE]
[QUOTE=aptitude (update)]E: I wasn't able to locate a file for the mfc8440lpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?[/QUOTE]
[QUOTE=gdebi]**Could not open 'mfc8440lpr-1.1.2-1.i386.deb'**
The package might be corrupt or you are not allowed to open the file. Please check the permissions of the file.[/QUOTE]
[QUOTE=dpkg]user@host:~$ sudo dpkg -i mfc8440lpr-1.1.2-1.i386.deb 
Selecting previously deselected package mfc8440lpr.
(Reading database ... 
dpkg: serious warning: files list file for package `mfc8440lpr' missing, assuming package has no files currently installed.
165873 files and directories currently installed.)
Preparing to replace mfc8440lpr 1.1.2-1 (using mfc8440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8440lpr ...
dpkg: error processing mfc8440lpr-1.1.2-1.i386.deb (--install):
 trying to overwrite `/usr/local/Brother/inf/setupPrintcap', which is also in package brmfcfaxlpd
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
[/QUOTE]

mfc8440lpr is a package for my Brother MFC-8440 - driver are here: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I'm not sure what has happened with the Debian file, but it never installed properly (looks corrupt): ([http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) - search for 'MFC-8440' - mfc8440lpr-1.1.2-1.i386.deb)

So now I can't upgrade or anything, can any advise on how to rid of this problem?

---

### Post by altonbr on 2007-06-29
help! -- maybe this problem isn't so "general".

---

### Post by altonbr on 2007-07-02
bump :(

---

### Post by altonbr on 2007-07-04
bump.

---

### Post by altonbr on 2007-07-04
Apparently I can't edit my post so:

[QUOTE="sudo dpkg"]user@host:~$ sudo dpkg -i mfc8440lpr-1.1.2-1.i386.deb 
(Reading database ... 
dpkg: serious warning: files list file for package `mfc8440lpr' missing, assuming package has no files currently installed.
165873 files and directories currently installed.)
Preparing to replace mfc8440lpr 1.1.2-1 (using mfc8440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8440lpr ...
dpkg: error processing mfc8440lpr-1.1.2-1.i386.deb (--install):
 trying to overwrite `/usr/local/Brother/inf/setupPrintcap', which is also in package brmfcfaxlpd
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr-1.1.2-1.i386.deb
[/QUOTE]

[QUOTE="sudo aptitude"]user@host:~$ sudo aptitude purge brmfcfaxlpd 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libcamel1.2-10 libedataserver1.2-9 libegroupwise1.2-13 
  libexchange-storage1.2-3 libgd2-xpm libpng12-dev python-launchpad-bugs 
  vmware-server-kernel-modules-2.6.20-16 
The following packages have been kept back:
  app-install-data-commercial evolution-data-server 
  evolution-data-server-common file gnome-btdownload libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 
  libexif12 libkrb53 libmagic1 libnautilus-burn4 libpng12-0 libxvidcore4 
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-386 linux-libc-dev 
  linux-restricted-modules-2.6.20-16-386 linux-restricted-modules-common 
  mplayer nautilus-cd-burner nvidia-glx peerguardnf update-manager 
  update-manager-core xscreensaver-data xscreensaver-gl 
The following packages will be REMOVED:
  brmfcfaxlpd{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 38 not upgraded.
Need to get 0B of archives. After unpacking 115kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the mfc8440lpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
[/QUOTE]

---

### Post by altonbr on 2007-07-05
Sorry, but I'm desperate.

---

### Post by mikaelsnavy on 2007-07-05
i get the same thing with another package!

EDIT: I fixed it by downloading and trying to install the package again about 7 times.
The last time, it worked.

---

### Post by altonbr on 2007-07-06
> **mikaelsnavy said:**
> i get the same thing with another package!

EDIT: I fixed it by downloading and trying to install the package again about 7 times.
The last time, it worked.

Ha, I wish that worked... I'm not allowed to install anything. It either says I don't have the permissions (even when using sudo or gksu), or that the package is broken (any package that is).

---

### Post by grekei on 2007-07-06
dont know if this helps but I had a problem with a broken package stuck in synaptic and could not do anything without an error message.It turned out the problem was not the package itself.The solution attached worked fine:

  Talking  Re: broken synaptic package manager
OK, it is obvious that taskjuggler is the problem and all of the above help was fruitless.

Open a console and type in the following:

Code:

sudo gedit /var/lib/dpkg/status


Search through the file for any reference to taskjuggler and CAREFULLY delete all of that entry.

Save the file

Code:

sudo apt-get update

Your problem should now be solved, as Synaptic can no longer see this errant package and as disk space is taken up, it will be over-written.

Regards,
Roger
__________________
There are only two things in life that are mandatory.
Birth and Death.
Everything else is optional.
Ubuntu User #10495 

Using this option you can see any broken packages and cut them out.In my case the package was "Taskjuggler".Hope it can help

Cheers Grekei

---

### Post by altonbr on 2007-07-06
> **grekei said:**
> dont know if this helps but I had a problem with a broken package stuck in synaptic and could not do anything without an error message.It turned out the problem was not the package itself.The solution attached worked fine:

  Talking  Re: broken synaptic package manager
OK, it is obvious that taskjuggler is the problem and all of the above help was fruitless.

Open a console and type in the following:

Code:

sudo gedit /var/lib/dpkg/status


Search through the file for any reference to taskjuggler and CAREFULLY delete all of that entry.

Save the file

Code:

sudo apt-get update

Your problem should now be solved, as Synaptic can no longer see this errant package and as disk space is taken up, it will be over-written.

Regards,
Roger
__________________
There are only two things in life that are mandatory.
Birth and Death.
Everything else is optional.
Ubuntu User #10495 

Using this option you can see any broken packages and cut them out.In my case the package was "Taskjuggler".Hope it can help

Cheers Grekei

Amazing, just amazing! Thank you so much! It worked :D

---

