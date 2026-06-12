---
title: "[SOLVED] File not found"
date: 2007-09-04
forum: General Help
---

### Post by MoebusNet on 2007-09-04
I'm trying to install the Citrix ICA Client software on my Dapper desktop (yes I know it isn't supported, but my problem isn't due to the software package).

I've downloaded the ICAClient-10.6-1.i386.rpm package, following this guide for Dapper - [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

I've installed alien to convert the rpm to a deb. But when I try to use alien I get this -
me@my-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@my-desktop:~$ alien ICAClient-10.6-1.i386.rpm
Must run as root to convert to deb format (or you may use fakeroot).
me@my-desktop:~$ fakeroot alien ICAClient-10.6-1.i386.rpm
File "ICAClient-10.6-1.i386.rpm" not found.
me@my-desktop:~$

I can see the rpm package on my desktop, pull up the properties, etc.

What am I doing wrong here?

Thanks in advance

---

### Post by cookies on 2007-09-04
> **MoebusNet said:**
> I'm trying to install the Citrix ICA Client software on my Dapper desktop (yes I know it isn't supported, but my problem isn't due to the software package).

I've downloaded the ICAClient-10.6-1.i386.rpm package, following this guide for Dapper - [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

I've installed alien to convert the rpm to a deb. But when I try to use alien I get this -
me@my-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@my-desktop:~$ alien ICAClient-10.6-1.i386.rpm
Must run as root to convert to deb format (or you may use fakeroot).
me@my-desktop:~$ fakeroot alien ICAClient-10.6-1.i386.rpm
File "ICAClient-10.6-1.i386.rpm" not found.
me@my-desktop:~$

I can see the rpm package on my desktop, pull up the properties, etc.

What am I doing wrong here?

Thanks in advance

cd Desktop

Then try your command.

---

### Post by MoebusNet on 2007-09-04
Thanks!

---

### Post by MoebusNet on 2007-09-04
Would you be willing to venture a recommendation to deal with this?

me@my-desktop:~/Desktop$ fakeroot alien ICAClient-10.6-1.i386.rpm
Warning: Skipping conversion of scripts in package ICAClient: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
icaclient_10.6-2_i386.deb generated
me@my-desktop:~/Desktop$ sudo dpkg -i icaclient-10.0-2.i386.deb
Password:
dpkg: error processing icaclient-10.0-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 icaclient-10.0-2.i386.deb
me@my-desktop:~/Desktop$

---

### Post by MoebusNet on 2007-09-04
Doh! Read the eroor message dummy!! (to myself)

me@my-desktop:~/Desktop$ fakeroot alien --scripts ICAClient-10.6-1.i386.rpm
icaclient_10.6-2_i386.deb generated
me@my-desktop:~/Desktop$ sudo dpkg -i icaclient_10.6-2_i386.deb
Selecting previously deselected package icaclient.
(Reading database ... 74007 files and directories currently installed.)
Unpacking icaclient (from icaclient_10.6-2_i386.deb) ...
Setting up icaclient (10.6-2) ...

Now all I have to do is track down that pesky libmotif3...

---

