---
title: "Old linux-header source files"
date: 2021-10-26
forum: General Help
---

### Post by bilkay on 2021-10-26
Is there any  earthly reason for keeping them in my system (in /usr/src)?

---

### Post by ajgreeny on 2021-10-26
No real point keeping any header packages for which you do not have the same version kernel, but do not simply delete them; you should uninstall the **linux-headers** packages with the same version number.

You may also find that command ```
sudo apt autoremove
``` offers to uninstall those packages.

---

### Post by bilkay on 2021-10-26
When I try to remove the packages, apt says they're not installed. What's the danger in just deleting them? They're taking up over 300 MB of disk space.

---

### Post by Bashing-om on 2021-10-26
bilkay; Hey

There is indeed a manual method to remove orphan files.
One must make is so that /usr/src/, /lib/modules/, and /boot/ all agree - and then heal the package manager.

See: [http://ubuntuforums.org/showthread.php?t=2174867](http://ubuntuforums.org/showthread.php?t=2174867)
as an example of the how-to.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by ajgreeny on 2021-10-26
Can you please tell us the Ubuntu version you're using and then show us the full terminal output plus the commands used to remove the header packages.

A possibility is that you have retained the configurations for those headers so it may help to make sure you use the purge commands when removing them.

When I see a new kernel has arrived, and being a bit OCD about my system, I always run command ```
sudo apt purge *5.4.0-##*
```for the third kernel version that I no longer need. That completely removes everything related to that version of kernel including headers, modules and tools packages that are installed, including their configuration files.

You may find **synaptic** is a good way to search those header packages as it shows absolutely everything, and if you search simply using the specific kernel version number it may allow you to remove configurations you didn't even know were still present in the system.  You can also filter the search with the Status filter in the left hand pane and find all retained configurations.

---

### Post by bilkay on 2021-10-26
Now that you mentioned it, I see that /lib/modules also has a ton of old stuff. All told, it's almost a gig of disk space.

---

### Post by bilkay on 2021-10-26
> **ajgreeny said:**
> Can you please tell us the Ubuntu version you're using and then show us the full terminal output plus the commands used to remove the header packages.

18.04

```
root@Laptop:/# apt purge *4.15.0-101
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-tools-4.15.0-101' for glob '*4.15.0-101'
Note, selecting 'linux-cloud-tools-4.15.0-101' for glob '*4.15.0-101'
Note, selecting 'linux-headers-4.15.0-101' for glob '*4.15.0-101'
Package 'linux-cloud-tools-4.15.0-101' is not installed, so not removed
Package 'linux-headers-4.15.0-101' is not installed, so not removed
Package 'linux-tools-4.15.0-101' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
```

```
root@Laptop:/usr/src# ls
linux-headers-4.15.0-101          linux-headers-4.15.0-159-generic
linux-headers-4.15.0-106          linux-headers-4.15.0-161
linux-headers-4.15.0-109          linux-headers-4.15.0-161-generic
linux-headers-4.15.0-112          linux-headers-4.15.0-54
linux-headers-4.15.0-115          linux-headers-4.15.0-55
linux-headers-4.15.0-122          linux-headers-4.15.0-58
linux-headers-4.15.0-123          linux-headers-4.15.0-60
linux-headers-4.15.0-126          linux-headers-4.15.0-62
linux-headers-4.15.0-128          linux-headers-4.15.0-64
linux-headers-4.15.0-129          linux-headers-4.15.0-65
linux-headers-4.15.0-130          linux-headers-4.15.0-66
linux-headers-4.15.0-132          linux-headers-4.15.0-69
linux-headers-4.15.0-134          linux-headers-4.15.0-70
linux-headers-4.15.0-135          linux-headers-4.15.0-72
linux-headers-4.15.0-136          linux-headers-4.15.0-74
linux-headers-4.15.0-137          linux-headers-4.15.0-76
linux-headers-4.15.0-139          linux-headers-4.15.0-88
linux-headers-4.15.0-140          linux-headers-4.15.0-91
linux-headers-4.15.0-140-generic  linux-headers-4.15.0-96
linux-headers-4.15.0-142          linux-headers-4.15.0-99
linux-headers-4.15.0-159          rtlwifi-new-0.6
```

---

### Post by ajgreeny on 2021-10-26
The command ```
dpkg -l linux-headers*
``` will show us exactly the situation and status of all the header packages installed in your system.

As an example here's what I see.
```
dpkg -l linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version      Architecture Description
+++-==============================-============-============-========================================================
un  linux-headers                  <none>       <none>       (no description available)
un  linux-headers-3.0              <none>       <none>       (no description available)
ii  linux-headers-5.4.0-88         5.4.0-88.99  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-88-generic 5.4.0-88.99  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-89         5.4.0-89.100 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-89-generic 5.4.0-89.100 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
un  linux-headers-686-pae          <none>       <none>       (no description available)
un  linux-headers-amd64            <none>       <none>       (no description available)
ii  linux-headers-generic          5.4.0.89.93  amd64        Generic Linux kernel headers

```
You can do the same for the linux-modules packages
```
dpkg -l linux-modules*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version      Architecture Description
+++-====================================-============-============-==============================================================
ii  linux-modules-5.4.0-88-generic       5.4.0-88.99  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-89-generic       5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-88-generic 5.4.0-88.99  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-89-generic 5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
```

**ii** at the beginning of a line means the package is fully installed, 
**un** means it is fully uninstalled including configurations, and from memory (I do not have any such packages) 
**ur** means the package is removed but configurations remain.

---

### Post by bilkay on 2021-10-26
```
root@Laptop:~# dpkg -l linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
un  linux-headers                   <none>               <none>               (no description available)
un  linux-headers-3.0               <none>               <none>               (no description available)
un  linux-headers-4.10.0-28-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-101-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-106-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-109-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-112-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-115-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-122-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-123-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-126-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-128-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-129-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-130-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-132-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-134-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-135-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-136-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-137-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-139-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-140-generi <none>               <none>               (no description available)
un  linux-headers-4.15.0-142-generi <none>               <none>               (no description available)
ii  linux-headers-4.15.0-159        4.15.0-159.167       all                  Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-159-generi 4.15.0-159.167       amd64                Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-161        4.15.0-161.169       all                  Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-161-generi 4.15.0-161.169       amd64                Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
un  linux-headers-4.15.0-54-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-55-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-58-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-60-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-62-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-64-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-65-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-66-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-69-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-70-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-72-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-74-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-76-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-88-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-91-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-96-generic <none>               <none>               (no description available)
un  linux-headers-4.15.0-99-generic <none>               <none>               (no description available)
un  linux-headers-686-pae           <none>               <none>               (no description available)
un  linux-headers-amd64             <none>               <none>               (no description available)
ii  linux-headers-generic           4.15.0.161.150       amd64                Generic Linux kernel headers
ii  linux-headers-generic-hwe-16.04 4.15.0.161.150       amd64                Generic Linux kernel headers (dummy transitional package)
```

---

### Post by ajgreeny on 2021-10-26
That's not helping much so I am baffled as to why you have all those header files still showing in /usr/src

This what my system shows from that command.
```
ls /usr/src
acpi-call-1.1.0/ 
libdvd-pkg/        
linux-headers-5.4.0-88/  
linux-headers-5.4.0-88-generic/        
linux-headers-5.4.0-89/  
linux-headers-5.4.0-89-generic/        
tp_smapi-0.43/
```

---

### Post by bilkay on 2021-10-27
> **ajgreeny said:**
> That's not helping much so I am baffled as to why you have all those header files still showing in /usr/src

I'm baffled too. I guess I'll just delete them - and the modules.

---

### Post by rsteinmetz70112 on 2021-10-27
Most of those kernel headers appear to be very old, possibly from previous version of Ubuntu.

I has something similar and was able to remove all of the old versions with no apparentl lii effects..

---

