---
title: "Problems with apt-get upgrade error code (2)"
date: 2012-12-29
forum: General Help
---

### Post by thorbs on 2012-12-29
I am getting problems when I try to upgrade

I get the following error,


> ~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc exo-utils libcups2 libcups2:i386 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsimage2:i386 libcupsmime1 libcupsppdc1 libexo-1-0 libexo-common libexo-helpers libpoppler-glib8 libpoppler19 libthunarx-2-0
  poppler-utils thunar thunar-data
23 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6.325 kB of archives.
After this operation, 425 kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.2.0-24': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am not able to install or remove software.

---

### Post by kreggz on 2012-12-29
try

sudo apt-get clean
sudo apt-get update

---

### Post by thorbs on 2012-12-29
Thanks, but I still got the same result.

---

### Post by crk on 2012-12-29
The problem, as I see it, is with your **dpkg** program, and not apt-get. Try running the following command and tell us what you get :

```

$ dpkg --version
```

---

### Post by davidtrounce on 2012-12-29
What are you trying to upgrade exactly? A version? If so, which version from and to?

---

### Post by thorbs on 2012-12-29
When I run the command I get the following result 


> Debian `dpkg' package management program version 1.16.1.2 (amd64).
This is free software; see the GNU General Public License

---

### Post by thorbs on 2012-12-29
I am just trying to install the updates I am getting from ubuntu

---

### Post by Bashing-om on 2012-12-29
thorbs; Hi

In the original output:
> reading files list for package 'linux-headers-3.2.0-24': Input/output errorsuggest to me that the system database has become corrupted.
```
sudo rm /var/lib/apt/lists/* -vf
```removes the database; 
Bring in new scripts that should not be broken and replace it with a new list:
```
sudo apt-get clean
sudo apt-get update
```Now do the updates, see what results:
```
sudo apt-get upgrade
```[INDENT][INDENT][INDENT]just try'n to help <== BDQ
[/INDENT][/INDENT][/INDENT]

---

### Post by thorbs on 2012-12-29
Hi bash-om;

I tried your code but I am still stuck with

> Fetched 6.325 kB in 4min 55s (21,4 kB/s)                                       
Preconfiguring packages ...
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.2.0-24': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)



:-|

---

### Post by Bashing-om on 2012-12-29
thorbs; 

Surprised. OK, I have seen similar error when the partition is full. Let's look:
```
df -h
```If the return is good, not sure at this point how to proceed, will investigate and see.
But I do want to see what headers are installed:
```
dpkg -l | grep linux-headers
```[INDENT][INDENT]puzzle'n things out <== BDQ

[/INDENT][/INDENT]

---

### Post by thorbs on 2012-12-30
Hi Bash, 

checking the disc I got

> df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       129G   55G   68G  45% /
udev            1,5G  4,0K  1,5G   1% /dev
tmpfs           598M  832K  597M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,5G  1,5M  1,5G   1% /run/shm


And checking the headers I got

> $ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-23                 3.2.0-23.36                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic         3.2.0-23.36                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-24                 3.2.0-24.39                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-24-generic         3.2.0-24.39                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-25                 3.2.0-25.40                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-25-generic         3.2.0-25.40                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-26                 3.2.0-26.41                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-26-generic         3.2.0-26.41                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-27                 3.2.0-27.43                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic         3.2.0-27.43                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-29                 3.2.0-29.46                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic         3.2.0-29.46                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-30                 3.2.0-30.48                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic         3.2.0-30.48                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic         3.2.0-34.53                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic         3.2.0-35.55                                       Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.35.40                                       Generic Linux kernel headers


thanks

---

### Post by Bashing-om on 2012-12-30
thorbs;

Sorry I missed your reply, playing catchup now.
1. Disk space looks good.
2. That many old images on your system. Lets get rid of all but the latest 3, bet that will also resolve the update problems if the "bad" header package is gone.
Thus:
The command```
 uname -a
``` in a terminal will tell you which kernel you are running....then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for removal/complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).
Now in terminal update grub:
```
sudo update-grub
```synaptic package manager is no longer installed by default, download and install:
```
sudo apt-get install synaptic
```If all goes well, now what results from the terminal commands ? :
```
 sudo apt-get update
sudo apt-get upgrade
```[INDENT][INDENT]looking good now ? <== BDQ

[/INDENT][/INDENT]

---

### Post by thorbs on 2012-12-31
I got stock allready trying to move old images from my system:

I got the following error

> (Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.2.0-24': Input/output error
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)



happy newyears bash

---

### Post by Bashing-om on 2012-12-31
thorbs; 

Well (not), as the shotgun approach is not effective. What happens if the file is singled out for purging ?
```
sudo apt-get remove --auto-remove linux-headers-3.2.0-24
```see :```
man apt-get
```
may your new year be blessed too < == BDQ

---

### Post by thorbs on 2013-01-03
Hi Bash, 

I tried rm the files seperately, but still got the same result and the same error code.

I also read the manpage.

Is there anything left to try?

---

### Post by Bashing-om on 2013-01-03
thorbs; SHeeesshh,
Don't know at the present time. What we have here is a failure to communicate. I ain't talking to the right component !
I just do not comprehend why such an old header file can be causing such a problem.
While I am looking and thinking ...try this one and see what results:
```
 sudo apt-get dist-upgrade
```By doing an "sudo apt-get dist-upgrade" it will update packages and install new kernels as well as resolve package conflicts.
[INDENT][INDENT]we are not beat yet ==> BDQ

[/INDENT][/INDENT]

---

### Post by thorbs on 2013-01-05
I am afraid I got the same result as with my other approaches. We seem to be a bit stuck :)

---

### Post by Bashing-om on 2013-01-05
@thorbs; 

Yeah I am afraid so, presently my comprehension is lacking. I do not understand how an old system file can cause such a situation. Or, why it pops up now to bite

What happens if you try and (re)install that header file ?
```
sudo apt-get install --reinstall linux-headers-3.2.0-24
```[INDENT]just 'bout the time I think I know something, I find out how little I actually know !
                                             ==> BDQ 
[/INDENT]

---

### Post by thorbs on 2013-01-07
Ok, I did but still same result.

Thanks for the big effort bash. 


I think I am starting to think in reinstall as my system at its present state is not really fully productive. What you think bash time to let it go?

thanks again.


thorbs

---

