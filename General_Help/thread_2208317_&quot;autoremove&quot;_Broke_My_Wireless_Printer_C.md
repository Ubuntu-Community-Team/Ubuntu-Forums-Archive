---
title: "&quot;autoremove&quot; Broke My Wireless Printer Connection?"
date: 2014-02-27
forum: General Help
---

### Post by Akacheebe on 2014-02-27
Early this week I posted another thread dealing with multiple kernels being updated each time and update was released.  Here is that thread

[http://ubuntuforums.org/showthread.php?t=2206912&highlight=akacheebe2](http://ubuntuforums.org/showthread.php?t=2206912&highlight=akacheebe2)

At that time I did run "autoremove" but it didn't take out any of the 3.2.0 kernel stuff but it did break my netspeed applet.  Later in that thread I did get some info that worked to remove 3.2.0 and in the end I did upgrade to kernel 3.11.0.  Right after that there was a problem with this computer accessing the network but some time later that day that problem fixed itself and I thought all was well.  

Well, this morning I paid a bill online and then tried to print out the receipt only to find out there is no printer installed?  We use an HP 6500 wireless printer connected to out network via a Cradlepoint MBR1000 router and the printer was working fine before the "autoremove" or the kernel updates.

FYI, I have 3 Ubuntu 12.04 computers on this network that were all upgraded to 3.11.0 and neither of the other two have a problem with the printer so I guess that leaves the "autoremove" function as the culprit that broke my printer driver.

I am able to ping that printer from terminal but it doesn't show up when I try to install it??  

There's so much "Print" stuff that shows up in Synaptic that I'm afraid to mess with anything there.

So can someone tell me how to reinstall the print driver or whatever is  needed so the print function on this computer will work again?  

Thanks

---

### Post by Akacheebe on 2014-02-27
Here's some additional data on this network printing problem.

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 32.8 MB/40.5 MB of archives.
After this operation, 31.3 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-security/main openjdk-6-jre-headless amd64 6b30-1.13.1-1ubuntu2~0.12.04.1 [32.8 MB]
Fetched 17.7 MB in 4min 6s (71.9 kB/s)                                                                                                                               
(Reading database ... 923556 files and directories currently installed.)
Preparing to replace icedtea-6-jre-cacao 6b27-1.12.6-1ubuntu0.12.04.4 (using .../icedtea-6-jre-cacao_6b30-1.13.1-1ubuntu2~0.12.04.1_amd64.deb) ...
Unpacking replacement icedtea-6-jre-cacao ...
Preparing to replace openjdk-6-jre-lib 6b27-1.12.6-1ubuntu0.12.04.4 (using .../openjdk-6-jre-lib_6b30-1.13.1-1ubuntu2~0.12.04.1_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
Preparing to replace icedtea-6-jre-jamvm 6b27-1.12.6-1ubuntu0.12.04.4 (using .../icedtea-6-jre-jamvm_6b30-1.13.1-1ubuntu2~0.12.04.1_amd64.deb) ...
Unpacking replacement icedtea-6-jre-jamvm ...
Preparing to replace openjdk-6-jre-headless 6b27-1.12.6-1ubuntu0.12.04.4 (using .../openjdk-6-jre-headless_6b30-1.13.1-1ubuntu2~0.12.04.1_amd64.deb) ...
Unpacking replacement openjdk-6-jre-headless ...
Preparing to replace openjdk-6-jre 6b27-1.12.6-1ubuntu0.12.04.4 (using .../openjdk-6-jre_6b30-1.13.1-1ubuntu2~0.12.04.1_amd64.deb) ...
Unpacking replacement openjdk-6-jre ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up cups (1.5.3-0ubuntu5.1) ...
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up openjdk-6-jre-headless (6b30-1.13.1-1ubuntu2~0.12.04.1) ...
Installing new version of config file /etc/java-6-openjdk/security/java.security ...
Installing new version of config file /etc/java-6-openjdk/security/java.policy ...
Setting up openjdk-6-jre-lib (6b30-1.13.1-1ubuntu2~0.12.04.1) ...
Setting up icedtea-6-jre-cacao (6b30-1.13.1-1ubuntu2~0.12.04.1) ...
Setting up icedtea-6-jre-jamvm (6b30-1.13.1-1ubuntu2~0.12.04.1) ...
Setting up openjdk-6-jre (6b30-1.13.1-1ubuntu2~0.12.04.1) ...
Errors were encountered while processing:
 cups
 printer-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Akacheebe on 2014-03-01
OK, so I finally got this all figured out, and thanks for the help!;)

---

### Post by monkeybrain20122 on 2014-03-01
How? It is good etiquette to post your solution when you figure something out in case it may help others. ;)

---

