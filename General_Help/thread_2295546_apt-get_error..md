---
title: "apt-get error."
date: 2015-09-19
forum: General Help
---

### Post by nalkubaxd5 on 2015-09-19
Hello. I have the following error white running "apt-get install httperf":

```
root@nalkubaxd5:~# apt-get install httperfReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
The following NEW packages will be installed:
  httperf
0 upgraded, 1 newly installed, 3 to remove and 28 not upgraded.
118 not fully installed or removed.
Need to get 0 B/73.2 kB of archives.
After this operation, 2574 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66615 files and directories currently installed.)
Removing libglade2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nalkubaxd5:~#
```

Also the "apt-get -f install" don't work:
```
root@nalkubaxd5:~# apt-get -f installReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 3 to remove and 28 not upgraded.
118 not fully installed or removed.
After this operation, 2750 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66615 files and directories currently installed.)
Removing libglade2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nalkubaxd5:~#

```

Any ideas how to fix it?

---

### Post by Bucky Ball on 2015-09-19
First off, you should always do an update before installing a new app. Best practice so you get the latest.

```
sudo apt-get update
```

... or use the Software Updater. By the looks of it, you haven't done an update in quite some time.

```
118 not fully installed or removed.
```

Run these commands, hitting enter after each. Post back any and all errors, please.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Also, which Ubuntu release are you using?

---

### Post by ian-weisser on 2015-09-19
Easy: Create an empty (dummy) file in the expected location for the  package manager to remove. Then run the package management operation  again.
```
touch /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
```

-f won't work for a missing file. Wrong kind of error for it to handle.

A more important question is: Who has been manually deleting files in /usr/share? And why?

---

### Post by nalkubaxd5 on 2015-09-19
Well, there is an error with apt-get autoremove:
```
root@nalkubaxd5:~# apt-get autoremoveReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libglade2.0-cil libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 3 to remove and 28 not upgraded.
3 not fully installed or removed.
After this operation, 2750 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66615 files and directories currently installed.)
Removing libglade2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: error processing libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: error processing libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nalkubaxd5 on 2015-09-19
> **ian-weisser said:**
> Easy: Create an empty (dummy) file in the expected location for the  package manager to remove. Then run the package management operation  again.
Well, I'm kinda dummy in this. Can you explain it? The following packages are: libglade2.0-cil, libgtk2.0-cil, libglib2.0-cil.

> **ian-weisser said:**
> A more important question is: Who has been manually deleting files in /usr/share? And why?
That's also a good question. Maybe i <snipped> up something.

---

### Post by ian-weisser on 2015-09-19
The error message tells you exactly what the problem is.
> **nalkubaxd5 said:**
> E: **File does not exist**: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac

See the problem?
The package manager is simply following a recipe that tells it to delete  that file. It doesn't care about the content of that file.

One simple solution is to create an empty file of the same name using the *touch* command...
```
touch /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
```

...then let the package manager remove it.
```
apt-get autoremove
```

RInse and repeat for each package with a similar error.

---

