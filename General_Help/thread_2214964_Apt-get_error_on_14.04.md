---
title: "Apt-get error on 14.04"
date: 2014-04-04
forum: General Help
---

### Post by Saint Angeles on 2014-04-04
I've been using Trusty since the first Beta was released and I've finally ran into my first problem. It has been extremely stable for me but now I get this error when I try to [FONT=courier new]apt-get dist-upgrade[/FONT]:


[FONT=courier new]The following packages have unmet dependencies:[/FONT]
[FONT=courier new] isc-dhcp-client : Depends: isc-dhcp-common (= 4.2.4-7ubuntu9) but 4.2.4-7ubuntu10 is installed[/FONT]
[FONT=courier new]E: Unmet dependencies. Try using -f.[/FONT]


I try [FONT=courier new]apt-get -f install[/FONT] and I am met with this:


[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree       [/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]Correcting dependencies... Done[/FONT]
[FONT=courier new]The following extra packages will be installed:[/FONT]
[FONT=courier new]  isc-dhcp-client[/FONT]
[FONT=courier new]Suggested packages:[/FONT]
[FONT=courier new]  avahi-autoipd[/FONT]
[FONT=courier new]The following packages will be upgraded:[/FONT]
[FONT=courier new]  isc-dhcp-client[/FONT]
[FONT=courier new]1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/FONT]
[FONT=courier new]1 not fully installed or removed.[/FONT]
[FONT=courier new]Need to get 0 B/640 kB of archives.[/FONT]
[FONT=courier new]After this operation, 1,024 B of additional disk space will be used.[/FONT]
[FONT=courier new]Do you want to continue? [Y/n] y[/FONT]
[FONT=courier new](Reading database ... 143468 files and directories currently installed.)[/FONT]
[FONT=courier new]Preparing to unpack .../isc-dhcp-client_4.2.4-7ubuntu10_amd64.deb ...[/FONT]
[FONT=courier new]/var/lib/dpkg/tmp.ci/preinst: 17: /var/lib/dpkg/tmp.ci/preinst: Syntax error: "fi" unexpected (expecting "then")[/FONT]
[FONT=courier new]dpkg: error processing archive /var/cache/apt/archives/isc-dhcp-client_4.2.4-7ubuntu10_amd64.deb (--unpack):[/FONT]
[FONT=courier new] subprocess new pre-installation script returned error exit status 2[/FONT]
[FONT=courier new]Errors were encountered while processing:[/FONT]
[FONT=courier new] /var/cache/apt/archives/isc-dhcp-client_4.2.4-7ubuntu10_amd64.deb[/FONT]
[FONT=courier new]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]


I am at a loss. Has anybody else experienced this error?

---

### Post by Saint Angeles on 2014-04-04
[IMG]http://i.imgur.com/l1IxvFe.png[/IMG]

---

### Post by knightscove on 2014-04-04
Yes, I'm getting the same error. -f option does not fix it

---

### Post by Wzrd1 on 2014-04-04
Same problem here, when I use the apt-get -f install, I get this:
apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  isc-dhcp-client
The following packages will be upgraded:
  isc-dhcp-client
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
34 not fully installed or removed.
Need to get 0 B/625 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 664067 files and directories currently installed.)
Preparing to unpack .../isc-dhcp-client_4.2.4-7ubuntu10_i386.deb ...
/var/lib/dpkg/tmp.ci/preinst: 17: /var/lib/dpkg/tmp.ci/preinst: Syntax error: "fi" unexpected (expecting "then")
dpkg: error processing archive /var/cache/apt/archives/isc-dhcp-client_4.2.4-7ubuntu10_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/isc-dhcp-client_4.2.4-7ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Update: isc-dhcp-client_4.2.4-7ubuntu11 is out, looks like that is working OK.
One test machine out of four had this problem, now the update is going through.

---

### Post by Saint Angeles on 2014-04-04
Well damn, what are we to do?

---

### Post by Saint Angeles on 2014-04-04
okay i think -f works now so this issue is over... for now

---

### Post by QIII on 2014-04-04
Ran into this earlier tonight and just did -f a couple of times and it automagically worked ...

Except that I completely lost sound in Kubuntu.  Wheee!

---

### Post by jacqueline-patricia on 2014-04-04
With -f you mean apt-get dist-upgrade -f?
Problem still exists, I still get isc-dhcp-client_4.2.4-7ubuntu10. I guess I have to wait until the mirror is synced.

---

### Post by NKK on 2014-04-04
Changing to main update server fixed the issue. So, indeed,  you have to wait until your mirror is synced, or switch to main one.

---

### Post by Balachmar on 2014-04-04
Hi all,

It is generally more useful to file bugs on launchpad.
I just did so myself. Please add extra information there. This will help developers to fix the problem more quickly.
And make sure you click on also affects me, that will bring it to their attention.
(no need for +1 in the comments)
And the link to the bug:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1302394](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1302394)

---

### Post by ajgreeny on 2014-04-04
I have just updated my Lubuntu 32bit, which included an update of isc-dhcp-client with no problem, so as you suspect this was probably related to the phased updates that are going on at the moment where not everything is released to all mirrors at the same time.

See [URL="https://wiki.ubuntu.com/PhasedUpdates"]https://wiki.ubuntu.com/PhasedUpdates
[/URL]
PS:
I am using the UK mirrors.

---

### Post by jacqueline-patricia on 2014-04-04
Thanks, just clicked on 'also affects me'.

---

### Post by danijel00 on 2014-04-04
Here it says that the problem has been fixed, and patch released

[https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1302300/comments/7](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1302300/comments/7)

but I don't know how to get the patch or fix my installation?

EDIT: got it - sudo apt-get update and then sudo apt-get install -f

---

### Post by bapoumba on 2014-04-04
dist-upgrading when repos are being populated during a beta is calling for such issues.

Anyway, an update/upgrade should be enough to get you the working version.

Edit: I'm running the upgrade now (was not around when the faulty package was pushed), we'll see.
Edit2 : looks okay to me.
```
isc-dhcp-client:
  Installed: 4.2.4-7ubuntu11
  Candidate: 4.2.4-7ubuntu11
```

---

