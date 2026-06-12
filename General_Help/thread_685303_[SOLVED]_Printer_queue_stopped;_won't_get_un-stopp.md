---
title: "[SOLVED] Printer queue stopped; won't get un-stopped"
date: 2008-02-02
forum: General Help
---

### Post by fizikz on 2008-02-02
I installed the latest HPLIP 2.7.12, and the printer was easily recognized and configured. However, I'm unable to print anything, including the test page. The jobs will go to the queue, but the status stays on "stopped". The printer is an HP L7780.

Here is a recent bit of the error log in /var/log/cups :
```
E [02/Feb/2008:01:55:46 -0500] Creating missing directory "/var/run/cups/certs"
E [02/Feb/2008:02:00:04 -0500] Creating missing directory "/var/run/cups/certs"
E [02/Feb/2008:02:06:37 -0500] [Job 77] No %%BoundingBox: comment in header!
E [02/Feb/2008:02:06:39 -0500] PID 6047 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [02/Feb/2008:02:07:36 -0500] Pause-Printer: Unauthorized
E [02/Feb/2008:02:07:40 -0500] Resume-Printer: Unauthorized
E [02/Feb/2008:02:07:47 -0500] CUPS-Reject-Jobs: Unauthorized
E [02/Feb/2008:02:07:48 -0500] CUPS-Accept-Jobs: Unauthorized
E [02/Feb/2008:02:07:59 -0500] CUPS-Set-Default: Unauthorized
E [02/Feb/2008:02:11:37 -0500] PID 6617 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [02/Feb/2008:02:34:29 -0500] [Job 79] No %%BoundingBox: comment in header!
E [02/Feb/2008:02:34:30 -0500] PID 7969 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!

```

---

### Post by fizikz on 2008-02-02
In trying to solve this problem I came across the following command that might provide some insight:
```
dpkg -l hplip
``` 

Typing that at the terminal gives:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  hplip          0.9.7-4ubuntu1 HP Linux Printing and Imaging System (HPLIP)

```

I'm not sure if that is normal. First, it doesn't seem to indicate that it is installed properly (what does the 'rc' status mean?). Secondly, it shows an older version of hplip (0.9.7-4 ubuntu1) as opposed to the recent 2.7.12 version that I thought I installed.

Any ideas on how to solve this? Everything seems to be fine, except that it wont print... which isn't a particularly useful situation.

---

### Post by fizikz on 2008-02-02
In continuing to try to fix this problem, I tried to install HPLIP (v 0.9.7-4-ubuntu) from Synaptic Package manager (it was previously unselected). The installation failed with error message: 

"E: hplip: subprocess post-installation script returned error exit status 1"

The output on the terminal:
```
Selecting previously deselected package hplip.
(Reading database ... 180563 files and directories currently installed.)
Unpacking hplip (from .../hplip_0.9.7-4ubuntu1_i386.deb) ...
Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail]
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail]
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip

```

If I could get some pointers towards a solution, I would greatly appreciate it.

---

### Post by fizikz on 2008-02-02
In case anyone else encounters this problem, I'll report how I finally resolved this problem.

The installation of hplip (version 2.7.12) goes fine; the problem was in the configuration. When selecting the driver for the device, hp-setup chose an incorrect driver by default, i.e. not the right one for my printer model. I had to choose "manually select" driver, and there I searched in the exhaustive list of models and was happy to find my (recent) printer model listed. After choosing the correct driver, and completing the setup, the test page printed without any problems. :)

---

