---
title: "[SOLVED] microcode.ctl won't install"
date: 2008-01-19
forum: General Help
---

### Post by mzembe on 2008-01-19
For some reason I can't get the microcode_ctl utility to work on gutsy. Adept and apt complain:
> root@m70-numbar1:/home/brian# apt-get install microcode.ctl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  microcode.ctl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.8kB of archives.
After unpacking 123kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package microcode.ctl.
(Reading database ... 90536 files and directories currently installed.)
Unpacking microcode.ctl (from .../microcode.ctl_1.17-1_i386.deb) ...
Setting up microcode.ctl (1.17-1) ...
udev active, devices will be created in /dev/.static/dev/
dpkg: error processing microcode.ctl (--configure):
 subprocess post-installation script returned error exit status 20
Errors were encountered while processing:
 microcode.ctl
E: Sub-process /usr/bin/dpkg returned an error code (1)


I downloaded the microcode from urbanmyth and copied it to /usr/share/misc/intel-microcode.dat to see if I could just run with my other boot rules for this runlevel.. I'm new to this udev stuff and, although the utility is kind of installed, 'microcode_ctl -u' complains:
> microcode_ctl: writing microcode (length: 357376)
microcode_ctl: cannot open /dev/cpu/microcode for writing errno=2 (No such file or directory)
I guess I will will have to find out what udev stuff there is in /etc, or mknod it, or something...

---

### Post by mzembe on 2008-01-21
You have to insert the microcode kernel module before installing the package. Also, it is not persistent, you have to issue a ```
ln -s /etc/init.d/microcode.ctl /etc/rc2.d/S96microcode.ctl
``` and add the line "microcode" to /etc/modules. The microcode still needs to be downloaded separately from [intel]("http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=microcode&x=26&y=14&lang=eng&MissingSearchTxt=Please+enter+a+valid+product+name%2C+filename+or+product+ID+%23.") and copied/renamed to /usr/share/misc/intel-microcode.dat

---

