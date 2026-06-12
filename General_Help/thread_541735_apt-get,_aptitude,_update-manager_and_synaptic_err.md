---
title: "apt-get, aptitude, update-manager and synaptic errors"
date: 2007-09-03
forum: General Help
---

### Post by aGoY on 2007-09-03
Hello everyone,

I'm a Ubuntu Feisty Fawn user since 8 months more less.. all goes perfect for this time, but yesterday I had an error (caused by the instalation of VMWare Workstation 6)..:mad: VMWare WS 6 works good but it missed up apt-get, synaptic, aptitude, the update-manager.. all the programs that are used for install/remove other programs were f-u-c-k-e-d.. :/

I don't know how to solve this problem, any method to reinstall the apt-get system or something like that?

(Screenshoots of my problem at the bottom of the thread, the selected text)

The screenshoots are in Spanish, sorry, but translated tells more less this, and sorry for my english, I'm from Spain too:

[SIZE="5"]Couldn't start the info of the packages[/SIZE]

An imposible problem to fix ocurred when the information of the packages were starting.

Please, inform this as an error in the package <<update-manager>> and include the next message error:

'E:The package vmwareworkstation need to be reinstalled, but the archive for him it's not found.'

If anyone could tell me how to solve this problem.. I can't install or remove any program! ](*,)


Greetings, aGoY.

---

### Post by garas on 2007-09-03
try to remove this package, and then reinstall this package if you need it
$ LC_ALL=en_US sudo aptitude remove vmwareworkstation
or if fails
$ LC_ALL=en_US sudo dpkg -D111 -r vmwareworkstation
and post output of second command

---

### Post by aGoY on 2007-09-03
Remember that my Ubuntu system is in spanish, and in the commands you told me is en_US, is this right for my system? Or I have to use my local settings (I think it's es_ES)

Doing LC_ALL=en_US sudo aptitude remove vmwareworkstation  || terminal log:

```
agoy@agoy-pc:/$ LC_ALL=en_US sudo aptitude remove vmwareworkstation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  amsn 
The following packages have been kept back:
  flashplugin-nonfree 
The following packages will be REMOVED:
  vmwareworkstation 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcllib (>= 1.8) but it is not installable
        Depends: libsnack2 (>= 2.2.9) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libsnack2 [2.2.10~jc-ubuntu3 (feisty)]
tcllib [1.8-1 (feisty)]

Score is -90

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  libsnack2 tcllib 
The following packages have been kept back:
  flashplugin-nonfree 
The following NEW packages will be installed:
  libsnack2 tcllib 
The following packages will be REMOVED:
  vmwareworkstation 
0 packages upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/2641kB of archives. After unpacking 11.0MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 37, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.5/locale.py", line 476, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "es_ES:es:en_GB:en",
        LC_ALL = "en_US",
        LANG = "es_ES.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing vmwareworkstation (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 vmwareworkstation
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcllib (>= 1.8); however:
  Package tcllib is not installed.
 amsn depends on libsnack2 (>= 2.2.9); however:
  Package libsnack2 is not installed.
dpkg: error processing amsn (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn
```

Doing LC_ALL=en_US sudo dpkg -D111 -r vmwareworkstation:

```
agoy@agoy-pc:/$ LC_ALL=en_US sudo dpkg -D111 -r vmwareworkstation
D000001: deferred_remove package vmwareworkstation
D000001: checking dependencies for remove `vmwareworkstation'
dpkg: error processing vmwareworkstation (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 vmwareworkstation
```


I tried to uninstall vmwareworkstation by using a PERL script that comes with the vmwareworkstation package, but it says:

```
agoy@agoy-pc:~/Desktop$ sudo /home/agoy/Desktop/vmware-distrib/bin/vmware-uninstall.pl
Uninstalling the tar installation of VMware Workstation.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop VMware Workstation's services.

```

Is there any form to kill a service? 

Thanks :)

---

### Post by garas on 2007-09-03
try to get vmwareworkstation
 .deb and install it using dpkg.

if it is in repositories, use $ aptitude download vmwareworkstation

---

### Post by aGoY on 2007-09-03
There aren't any vmwareworkstation.deb.. There is a vmwareworkstation.rpm, and I tried to change to .deb with alien but it gives me a corrupted .deb :/.

Any other form? I tried to install vmwareworkstation (with the official perl script but it fails :/)..

---

### Post by garas on 2007-09-04
try
# dpkg --purge --force-all vmwareworkstation

[http://www.linuxquestions.org/questions/showpost.php?p=2446348&postcount=7](http://www.linuxquestions.org/questions/showpost.php?p=2446348&postcount=7)

---

### Post by aGoY on 2007-09-05
> **garas said:**
> try
# dpkg --purge --force-all vmwareworkstation

[http://www.linuxquestions.org/questions/showpost.php?p=2446348&postcount=7](http://www.linuxquestions.org/questions/showpost.php?p=2446348&postcount=7)

You are the best garas! I was thinking of reinstalling Ubuntu.. :/

I made sudo dpkg --purge --force-all vmwareworkstation, and later sudo apt-get install -f because the update-manager told me that.. and now it is solved! :)

Thanks a lot!

@Admins or moderators: Close the thread :P.

---

