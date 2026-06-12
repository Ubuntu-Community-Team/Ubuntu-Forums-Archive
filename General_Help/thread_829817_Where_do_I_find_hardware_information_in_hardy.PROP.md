---
title: "Where do I find hardware information in hardy?.PROPER"
date: 2008-06-15
forum: General Help
---

### Post by mark.kristos on 2008-06-15
Re: Where do I find hardware information in hardy?
Quote:
Originally Posted by olskar View Post
run "sudo aptitude install hardinfo" in a terminal.
For some strange reason I think hardwareinfo has been removed by default.
mark@ubuntu-laptop:~$ sudo aptitude install hardinfo
[sudo] password for mark:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be automatically installed:
libsoup2.2-8
The following NEW packages will be installed:
hardinfo libsoup2.2-8
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 337kB of archives. After unpacking 995kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libsoup2.2-8 2.2.105-4 [96.8kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe hardinfo 0.4.2.3-3 [240kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe hardinfo 0.4.2.3-3 [240kB]
Fetched 247kB in 4min49s (853B/s)
Selecting previously deselected package libsoup2.2-8.
(Reading database ... 127073 files and directories currently installed.)
Unpacking libsoup2.2-8 (from .../libsoup2.2-8_2.2.105-4_amd64.deb) ...
Selecting previously deselected package hardinfo.
Unpacking hardinfo (from .../hardinfo_0.4.2.3-3_amd64.deb) ...
Setting up libsoup2.2-8 (2.2.105-4) ...

Setting up hardinfo (0.4.2.3-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
mark@ubuntu-laptop:~$ hardinfo

This adds an icon to System>Preferences> System Profiler and Benchmark

Thumbs up, now we are jammin :guitar:

---

### Post by ibutho on 2008-06-15
If you are not scared of the command line, you can always run "lshw". I've used hardinfo before and I was really impressed.

---

### Post by tommcd on 2008-06-15
In addition to lshw, you can use the standard linux way to get hardware info by typing "lspci -v" in terminal. lspci = list pci devices detected by the system, and the -v switch = verbose; i.e. it gives more info about each device detected.

To find out what drivers are being loaded for your hardware run "lsmod" in terminal.

---

### Post by ibutho on 2008-06-15
Whilst still on the subject, there are several tools I have used over the years. In addition to lspci, there is also "scanpci" which is used to scan pci buses and report info. Another is hwinfo which shows a lot of info about the system.

---

### Post by Pjotr123 on 2008-06-15
This is the one I like best:
Applications - Accessories - Terminal
copy/paste this line: ```
sudo lshw -html > hardware.html
```
press Enter
Your password will remain invisible, not even asterisks, this is normal.

Now you'll have a nice document in your personal folder, named hardware.html.

---

