---
title: "problem with executing .rpm files and installation scripts aka .pl files"
date: 2006-07-20
forum: General Help
---

### Post by qrm on 2006-07-20
Hi!

Im running ubuntu dapper drake and have encountered some problems. First of all I cannot execute .run files 
[```
aadam@atsimasin:~/Desktop$ sudo sh VMware-workstation-5.5.1-19175.i386.rpm
VMware-workstation-5.5.1-19175.i386.rpm: VMware-workstation-5.5.1-19175.i386.rpm: cannot execute binary file
aadam@atsimasin:~/Desktop$ 


```

```

aadam@atsimasin:~/Desktop$ sudo chmod +x VMware-server.rpm
aadam@atsimasin:~/Desktop$ sudo sh VMware-server.rpm
VMware-server.rpm: VMware-server.rpm: cannot execute binary file

```

When i try to dl a packed source code and try to execute .pl files i get the following:

```
aadam@atsimasin:~/Desktop/vmware-distrib$ sudo sh vmware-install.pl
vmware-install.pl: line 8: use: command not found
vmware-install.pl: line 14: use: command not found
vmware-install.pl: line 17: my: command not found
vmware-install.pl: line 18: my: command not found
vmware-install.pl: line 19: my: command not found
vmware-install.pl: line 20: my: command not found
vmware-install.pl: line 21: my: command not found
vmware-install.pl: line 22: my: command not found
vmware-install.pl: line 23: my: command not found
vmware-install.pl: line 24: my: command not found
vmware-install.pl: line 25: my: command not found
vmware-install.pl: line 26: my: command not found
vmware-install.pl: line 27: my: command not found
vmware-install.pl: line 28: my: command not found
vmware-install.pl: line 31: my: command not found
vmware-install.pl: line 34: my: command not found
vmware-install.pl: line 38: my: command not found
vmware-install.pl: line 39: my: command not found
vmware-install.pl: line 40: my: command not found
vmware-install.pl: line 41: my: command not found
vmware-install.pl: line 42: my: command not found
vmware-install.pl: line 43: my: command not found
vmware-install.pl: line 44: my: command not found
vmware-install.pl: line 46: my: command not found
vmware-install.pl: line 47: my: command not found
vmware-install.pl: line 48: my: command not found
vmware-install.pl: line 49: my: command not found
vmware-install.pl: line 50: my: command not found
vmware-install.pl: line 53: sub: command not found
vmware-install.pl: line 54: undef: command not found
vmware-install.pl: line 55: undef: command not found
vmware-install.pl: line 56: undef: command not found
vmware-install.pl: line 57: undef: command not found
vmware-install.pl: line 58: undef: command not found
vmware-install.pl: line 60: syntax error near unexpected token `INSTALLDB,'
vmware-install.pl: line 60: `  open(INSTALLDB, '<' . $gInstallerMainDB)'

```

Ive been googling around and I found this thread in the arcives of ubuntu forums: [http://www.ubuntuforums.org/archive/index.php/t-25258.html](http://www.ubuntuforums.org/archive/index.php/t-25258.html)

There is a post referring to the system not being able to find perl > apt-get install build-essential

That's the bare minimum for compiling packages. That doesn't explain why your system wasn't finding perl, though.

Ive installed gcc and build-essential and it doesnt seem to help. I can run .run files though like tremulous-1.1.0-installer.x86.run and everything installs just fine. Also i can run .sh files just fine from my konsole. I was able to install vmware server previously and now when i try to uninstall it I get the following errors:

```
aadam@atsimasin:~$ sudo sh /usr/bin/vmware-config.pl
/usr/bin/vmware-config.pl: line 8: use: command not found
/usr/bin/vmware-config.pl: line 23: use: command not found
/usr/bin/vmware-config.pl: line 24: package: command not found
/usr/bin/vmware-config.pl: line 26: my: command not found
/usr/bin/vmware-config.pl: line 30: syntax error near unexpected token `('
/usr/bin/vmware-config.pl: line 30: `sub new() {'
aadam@atsimasin:~$ sudo sh /usr/bin/vmware-uninstall.pl
/usr/bin/vmware-uninstall.pl: line 8: use: command not found
/usr/bin/vmware-uninstall.pl: line 11: use: command not found
/usr/bin/vmware-uninstall.pl: line 14: my: command not found
/usr/bin/vmware-uninstall.pl: line 15: my: command not found
/usr/bin/vmware-uninstall.pl: line 16: my: command not found
/usr/bin/vmware-uninstall.pl: line 17: my: command not found
/usr/bin/vmware-uninstall.pl: line 18: my: command not found
/usr/bin/vmware-uninstall.pl: line 19: my: command not found
/usr/bin/vmware-uninstall.pl: line 20: my: command not found
/usr/bin/vmware-uninstall.pl: line 21: my: command not found
/usr/bin/vmware-uninstall.pl: line 22: my: command not found
/usr/bin/vmware-uninstall.pl: line 23: my: command not found
/usr/bin/vmware-uninstall.pl: line 24: my: command not found
/usr/bin/vmware-uninstall.pl: line 25: my: command not found
/usr/bin/vmware-uninstall.pl: line 28: my: command not found
/usr/bin/vmware-uninstall.pl: line 31: my: command not found
/usr/bin/vmware-uninstall.pl: line 35: my: command not found
/usr/bin/vmware-uninstall.pl: line 36: my: command not found
/usr/bin/vmware-uninstall.pl: line 37: my: command not found
/usr/bin/vmware-uninstall.pl: line 38: my: command not found
/usr/bin/vmware-uninstall.pl: line 39: my: command not found
/usr/bin/vmware-uninstall.pl: line 40: my: command not found
/usr/bin/vmware-uninstall.pl: line 41: my: command not found
/usr/bin/vmware-uninstall.pl: line 43: my: command not found
/usr/bin/vmware-uninstall.pl: line 44: my: command not found
/usr/bin/vmware-uninstall.pl: line 45: my: command not found
/usr/bin/vmware-uninstall.pl: line 46: my: command not found
/usr/bin/vmware-uninstall.pl: line 47: my: command not found
/usr/bin/vmware-uninstall.pl: line 50: sub: command not found
/usr/bin/vmware-uninstall.pl: line 51: undef: command not found
/usr/bin/vmware-uninstall.pl: line 52: undef: command not found
/usr/bin/vmware-uninstall.pl: line 53: undef: command not found
/usr/bin/vmware-uninstall.pl: line 54: undef: command not found
/usr/bin/vmware-uninstall.pl: line 55: undef: command not found
/usr/bin/vmware-uninstall.pl: line 57: syntax error near unexpected token `INSTALLDB,'
/usr/bin/vmware-uninstall.pl: line 57: `  open(INSTALLDB, '<' . $gInstallerMainDB)'

```

Im quite an newbie in linux but i have a feeling that something in my compilers or whatever they are called is messed up. I havent downloaded any other .rpm packages nor .pl files to execute but im pretty sure I would have the same problem with those.

Thanks in advance

---

### Post by taurus on 2006-07-20
I don't think that is how you run .rpm!  Why don't you convert it to .deb with alien and install it, .deb, with dpkg!

```

sudo apt-get install alien
alien VMware-workstation-5.5.1-19175.i386.rpm
sudo dpkg -i VMware-workstation-5.5.1-19175.i386.deb

```

---

### Post by Paerez on 2006-07-20
ok first off, rpm files are not runnable files, they are red hat's package file (like a deb). So if you have xyz.rpm, do this:
```
alien xyz.rpm
dpkg -i xyz.deb
```
alien makes a deb from an rpm. You may have to install alien, it is in the repos.

As for the perl file, you would just need perl:
```
sudo apt-get install perl
```

good luck.

---

### Post by goobers on 2006-07-20
as far as i know you can open rpms directly in ubuntu, what you can do is this: (make sure you have the universe repositories enabled in synaptic package manager)

```

sudo apt-get install alien
sudo alien -k name-of-rpm-file.rpm

```

---

### Post by Ramses de Norre on 2006-07-20
This will do the trick:
```
sudo aptitude update && sudo aptitude install alien
sudo alien -i VMware-workstation-5.5.1-19175.i386.rpm
```
An .rpm isn't the same as a .run, .rpm is a package format like .deb but created by red hat (rpm= red hat package managing or something like that).

EDIT: man, I posted way too late:D

---

### Post by qrm on 2006-07-20
thanks a lot for these tips :) . Ill try them out as soon as I can but there still exists the problem with .pl files :/

---

### Post by Paerez on 2006-07-20
I mentioned installing perl to fix that. Can you post like the first couple lines from a pl file? Just type:
```
head vmware-install.pl
```

---

### Post by qrm on 2006-07-20
the first lines from .pl are

```
#!/usr/bin/perl -w
# If your copy of perl is not in /usr/bin, please adjust the line above.
#
# Copyright 1998 VMware, Inc.  All rights reserved.
#
# Tar package manager for VMware

use strict;

# Use Config module to update VMware host-wide configuration file

```

I tried to install perl, just in case i didnt have it:

```
aadam@atsimasin:~$ sudo apt-get install perl
Reading package lists... Done
Building dependency tree... Done
perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Im about to test converting the .rpm-s to debian packages with alien, wish me luck :)

---

### Post by Paerez on 2006-07-20
lets see if perl is the problem, try this:
```
/usr/bin/perl --version
```
if that doesn't work, type:
```
whereis perl
```
if "/usr/bin/perl" is not on the list, you need to change the first line of the script.

---

### Post by qrm on 2006-07-20
/usr/bin/perl --version gives me the following:

```
This is perl, v5.8.7 built for i486-linux-gnu-thread-multi
(with 1 registered patch, see perl -V for more detail)

Copyright 1987-2005, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using `man perl' or `perldoc perl'.  If you have access to the
Internet, point your browser at http://www.perl.org/, the Perl Home Page.

```

and whereis perl :

```
perl: /usr/bin/perl /etc/perl /usr/lib/perl /usr/bin/X11/perl /usr/local/lib/perl /usr/share/perl /usr/share/man/man1/perl.1.gz
```

so i guess perl is in the correct directories:???:

---

### Post by Paerez on 2006-07-20
ok so if you install it via the rpm->deb method does that work? After installing the debs you need to run the vmware config program. I don't remember what its called but I think you just type "sudo vmware-config.pl".

---

