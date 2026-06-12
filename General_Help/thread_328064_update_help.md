---
title: "update help"
date: 2006-12-30
forum: General Help
---

### Post by estewart on 2006-12-30
Hi, My updates stopped working, the results of sudo apt-get install -f are.
stewart@stewart-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
6 not fully installed or removed.
Need to get 0B/29.9kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 191060 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
stewart@stewart-desktop:~$ 

Anybody know what's up or how to fix? Ed

---

### Post by ajgreeny on 2006-12-30
Just out of interest, I note you used the lower case "y" as your "yes".

[I] Do you want to continue [Y/n]? y
[/I]
  Does this matter?  I always thought linux was case sensitive, so I wonder if this was part, or all, of your problem.

---

### Post by estewart on 2006-12-30
I'll try that>>>

---

### Post by estewart on 2006-12-30
That didn't help.

stewart@stewart-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
6 not fully installed or removed.
Need to get 0B/29.9kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 191060 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
stewart@stewart-desktop:~$

---

