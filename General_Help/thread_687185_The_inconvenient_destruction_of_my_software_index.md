---
title: "The inconvenient destruction of my software index"
date: 2008-02-04
forum: General Help
---

### Post by pundip on 2008-02-04
In an attempt to install cinelerra I have managed to trash my software index. News of this hit me when I tried to run the update manager only to receive the following error.

"It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. 

It was the use to the word "impossible" that set off the alarms. Anyway as expected sudo apt-get install -f didn't work and here is the output:

```

maneesh@deepthought:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmpeg3hv
The following NEW packages will be installed:
  libmpeg3hv
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0B/114kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 151054 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maneesh@deepthought:~$ 

```

sudo aptitude purge cinelerra found a rather long winded way to say "no joy" here is the output:

```

maneesh@deepthought:~$ sudo aptitude purge cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libpulse0 
The following packages have been kept back:
  app-install-data-commercial audacity 
The following packages will be REMOVED:
  cinelerra{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 23.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 150770 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_AU.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
maneesh@deepthought:~$ 
maneesh@deepthought:~$ sudo apt-get install -f
[sudo] password for maneesh:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
maneesh@deepthought:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmpeg3hv
The following NEW packages will be installed:
  libmpeg3hv
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0B/114kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 151054 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maneesh@deepthought:~$ sudo aptitude purge cinelerra
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
maneesh@deepthought:~$ sudo aptitude purge cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  libquicktimehv 
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libpulse0 
The following packages have been kept back:
  app-install-data-commercial audacity 
The following packages will be REMOVED:
  cinelerra{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 23.6MB will be freed.
The following packages have unmet dependencies:
  libquicktimehv: Depends: libmpeg3hv but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libquicktimehv

Score is 119

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libpulse0 
The following packages will be automatically REMOVED:
  libquicktimehv 
The following packages have been kept back:
  app-install-data-commercial audacity 
The following packages will be REMOVED:
  cinelerra{p} libquicktimehv 
0 packages upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 27.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 151050 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_AU.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libquicktimehv:
 libquicktimehv depends on libmpeg3hv; however:
  Package libmpeg3hv is not installed.
dpkg: error processing libquicktimehv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libquicktimehv
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
maneesh@deepthought:~$ 

```

I am running ver 7.10 kernel 2.6.22-14-generic gnome desktop. Any help here would be welcome because at this stage I am totally lost.

---

### Post by pundip on 2008-02-04
Just an update the command sudo dpkg --configure -a does nothing at all. Just returns the prompt.

---

### Post by @profix on 2008-06-10
Hi there, I have same problem with cinelerra and dependencies.
I dont know how to solve it. Now I cannot install any other software because of error with libquicktimehv which depends on libmpeg3hv. :(

"apt-get -f install" does not solve this

I try to remove/reinstall the packages/cinelera to fix it but without any result.

Is there anybody who know how to fix this problem ?

PS: same version as reported in previous post - 7.10 ubuntu desktop with gnome.

---

### Post by @profix on 2008-06-10
Maybe I found the solution. But still dont understand it.

apt-get purge libquicktimehv
ends with 
E: Sub-process /usr/bin/dpkg returned an error code (1)

so, somewhere on the net I read that if I edit "set -e" to "set -x", I see more info when dpkg runs /var/lib/dpkg/info/cinelerra.postrm

I edit the /var/lib/dpkg/info/cinelerra.postrm, change is from "set -e" to "set -x"

when I run apt-get purge libquicktimehv again, it writes info about cinelerra.postrm run (as expected), and ends with
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libvmware-vix.so.0 is not a symbolic link

Last line is another problem with vmware, but there is no problem with dpkg errors ( :confused: but :) ) .

Then I run apt-get purge cinelerra and it ends with info about cinelerra is not installed and cannot be removed.

But... 

I can do apt-get install samba after this, which is the thing, that I cannot do before problems with cinelerra.

Its not a good solution, but for me, it unblock installation of other software.

---

