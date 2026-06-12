---
title: "irda-utils error on install"
date: 2008-03-06
forum: General Help
---

### Post by geliovson on 2008-03-06
Hi,

I'm a new Ubuntu user (mt laptop was formally a Windows XP machine). So far I've been able to find answers to almost any problem I've encountered except for the use of my built-in IrDA.

I've contacted the laptop producer to find out what chipset the Ir device is but to no avail.  Similarly, I've tried commands such as:
> findchip -l -v

which gave me very little of value:
[INDENT]~$ findchip -l-v
SMC
NSC
WINBOND[/INDENT]

Upon installing irda-utils there was a failure which I cannot figure out how to solve. The same error (see quoted text below) occurs every time I do an update or install a new application. It is as follows:
> $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up irda-utils (0.9.18-6ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/
udev active, devices will be created in /dev/.static/dev/
Starting IrDA service: irattachUsage: irattach <dev> [-d dongle] [-s] [-b] [-v] [-h]
       <dev> is tty name, device name or module name
Dongles supported :
        esi
        tekram
        actisys
        actisys+
        girbil
        litelink
        airport
        old_belkin
        ep7211
        mcp2120
        act200l
        ma600
        toim3232

invoke-rc.d: initscript irda-utils, action "start" failed.
dpkg: error processing irda-utils (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 irda-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone offer me some advice?

Thanks in advance

---

