---
title: "&lt;package name&gt; depends on libxi6; however:   Package libxi6:amd64 is not installed."
date: 2020-06-13
forum: General Help
---

### Post by megatron36 on 2020-06-13
I just upgraded to 20.04 from 18.04 using the recommended path. Previously I did not have a desktop environment installed after the upgrade I used tasksel to select the Ubuntu desktop environment and while desktop works apt errors out with the following now every time I use apt to install anything. The packages like firefox still work but give errors randomly while using them. sometimes it tells me to authenticate and refuses to take any credentials. everything terminal related seems to work fine. Also related, if I try to install any of the java packages and they don't work because of this same error.

I have tried completely uninstalling and reinstalling the all packages as well.

Below is the output I'm getting anytime I run apt, Package libxi6 is installed:


```
# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/29.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package firefox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because MaxReports is reached already
                                                               dpkg: dependency problems prevent configuration of xinput:
 xinput depends on libxi6 (>= 2:1.2.99.4); however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package xinput (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xinput; however:
  Package xinput is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x11-utils:
 x11-utils depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package x11-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird:
 thunderbird depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package thunderbird (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems preveNo apport report written because MaxReports is reached already
                                                                                             No apport report written because MaxReports is reached already
                                                                                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                                                                                         No apport report written because MaxReports is reached already
                                                                                                                                                                                                                                                                                       nt configuration of ubuntu-desktop:
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop-minimal:
 ubuntu-desktop-minimal depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:68.8.0+build2-0ubuntu0.20.04.2); however:
  Package thunderbird is not configured yet.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
 xinput
 xorg
 x11-utils
 thunderbird
 ubuntu-desktop
 ubuntu-desktop-minimal
 thunderbird-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)


# sudo apt-get install libxi6
Reading package lists... Done
Building dependency tree
Reading state information... Done
libxi6 is already the newest version (2:1.7.10-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/29.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
```

---

### Post by Bashing-om on 2020-06-13
megatron36; Hello

As we have:
> 
9 not fully installed or removed.


what results:
```

sudo apt update
sudo apt upgrade
dpkg -l libxi6
sudo apt -f install

```


[INDENT]if the package manager is not happy
[INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT]

---

### Post by megatron36 on 2020-06-14
```
# sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [107 kB]
Ign:4 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge InRelease
Hit:5 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [98.3 kB]
Hit:8 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [102 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [151 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [18.6 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [31.5 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [532 B]
Fetched 616 kB in 1s (951 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
```

```
# sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/29.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package firefox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
 dpkg: dependency problems prevent configuration of xinput:
 xinput depends on libxi6 (>= 2:1.2.99.4); however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package xinput (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xinput; however:
  Package xinput is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x11-utils:
 x11-utils depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package x11-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird:
 thunderbird depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package thunderbird (--configure):
 dependency No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                                                                      No apport report written because MaxReports is reached already
                                                                                                                                                                                                                                                                    No apport report written because MaxReports is reached already
     problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop-minimal:
 ubuntu-desktop-minimal depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:68.8.0+build2-0ubuntu0.20.04.2); however:
  Package thunderbird is not configured yet.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
 xinput
 xorg
 x11-utils
 thunderbird
 ubuntu-desktop
 ubuntu-desktop-minimal
 thunderbird-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
dpkg -l libxi6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version           Architecture Description
+++-==============-=================-============-=================================
iHR libxi6:amd64   2:1.7.10-0ubuntu1 amd64        X11 Input extension library

```
```
# sudo apt -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/29.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xinput:
 xinput depends on libxi6 (>= 2:1.2.99.4); however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package xinput (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because MaxReports is reached already
                                                               dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xinput; however:
  Package xinput is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x11-utils:
 x11-utils depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package x11-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird:
 thunderbird depends on libxi6; however:
  Package libxi6:amd64 is not installed.

dpkg: error processing package thunderbird (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependenNo apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                                                                                                     No apport report written because MaxReports is reached already
                                                                                                                                                                                                   No apport report written because MaxReports is reached already
                                                                                                                                                                                                                                                                 cy problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop-minimal:
 ubuntu-desktop-minimal depends on xorg; however:
  Package xorg is not configured yet.

dpkg: error processing package ubuntu-desktop-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:68.8.0+build2-0ubuntu0.20.04.2); however:
  Package thunderbird is not configured yet.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
 xinput
 xorg
 x11-utils
 thunderbird
 ubuntu-desktop
 ubuntu-desktop-minimal
 thunderbird-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

As you can see regardless of what commands I run it returns back that libxi6 error

---

### Post by ActionParsnip on 2020-06-14
What is the output of:

```

apt-cache policy firefox libxi6

```

Thanks

---

### Post by Impavidus on 2020-06-14
Something went wrong during installation of libxi6, so now that package is half installed and has to be reinstalled:```
sudo apt install --reinstall libxi6
```Maybe it works, maybe it gives us a clue why installation failed.

BTW, the # at the start of your commands suggests that you use a root shell. If you use a root shell, why bother typing sudo?

---

### Post by megatron36 on 2020-06-15
Here is the out-put
$ sudo apt-cache policy firefox libxi6
[sudo] password for sdrago:
firefox:
  Installed: 77.0.1+build1-0ubuntu0.20.04.1
  Candidate: 77.0.1+build1-0ubuntu0.20.04.1
  Version table:
 *** 77.0.1+build1-0ubuntu0.20.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Package                                                                                                                                                                                                                                             s
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     75.0+build3-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
libxi6:
  Installed: 2:1.7.10-0ubuntu1
  Candidate: 2:1.7.10-0ubuntu1
  Version table:
 *** 2:1.7.10-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
        100 /var/lib/dpkg/status

Also I previously ran the reinstall command "sudo apt install --reinstall libxi6" with no luck but I just ran it again and it looks like it might have fixed the problem.
Now I did run sudo apt-get update before hand so maybe it got a different package this time?

$ sudo sudo apt install --reinstall libxi6
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/29.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 225545 files and directories currently installed.)
Preparing to unpack .../libxi6_2%3a1.7.10-0ubuntu1_amd64.deb ...
Unpacking libxi6:amd64 (2:1.7.10-0ubuntu1) over (2:1.7.10-0ubuntu1) ...
Setting up libxi6:amd64 (2:1.7.10-0ubuntu1) ...
Setting up firefox (77.0.1+build1-0ubuntu0.20.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
update-alternatives: using /usr/bin/firefox to provide /usr/bin/gnome-www-browse                                                                                                                                                                                                                                             r (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/firefox to provide /usr/bin/x-www-browser (x                                                                                                                                                                                                                                             -www-browser) in auto mode
Please restart all running instances of firefox, or you will experience problems                                                                                                                                                                                                                                             .
Setting up xinput (1.6.3-1) ...
Setting up x11-utils (7.7+5) ...
Installing new version of config file /etc/X11/app-defaults/Editres ...
Setting up thunderbird (1:68.8.0+build2-0ubuntu0.20.04.2) ...
Setting up xorg (1:7.7+19ubuntu14) ...
Setting up thunderbird-gnome-support (1:68.8.0+build2-0ubuntu0.20.04.2) ...
Setting up ubuntu-desktop-minimal (1.450.1) ...
Setting up ubuntu-desktop (1.450.1) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...

Edit:
Thanks for all of your Help too.

---

### Post by Impavidus on 2020-06-15
No error messages, so it seems to have worked. If everything is OK now, could you mark this thread as solved? Thread tools &#8594; Mark as solved.

---

