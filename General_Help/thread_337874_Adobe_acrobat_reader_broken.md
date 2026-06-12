---
title: "Adobe acrobat reader broken?"
date: 2007-01-13
forum: General Help
---

### Post by guy.murray on 2007-01-13
Hi,
   yesterday evening I did a system upgrade when prompted. One of the upgrades was Adobe Acrobat Reader. Ever since it won't run. A process appears but nothing is displayed on the screen.

Running it from the BASH prompt results in the following...

expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error

endlessly until Ctrl Cing out of it.

As I was writing this a new upgrade appeared and I assumed that this was fixed, but noooo!

Tried uninstalling and reinstalling without solving problem.

Has anyone else had this problem, or is it just me?

Guy

---

### Post by guy.murray on 2007-01-13
The thick plottens!

I have an older machine also with Ubuntu 6.10, in fact installed from the same CDROM. Both are up to date, though the older machine has less software installed.

The curious thing is that not only does the acrobat reader work fine, but Add/Remove Applications offers an earlier version than the other machine.

How come they are different?

---

### Post by Ramses de Norre on 2007-01-13
Different sources? (backports and such)

---

### Post by guy.murray on 2007-01-14
Further attempts.

Uninstalled it and used the Automatix "Acrobat reader and firefox plugin" instead, result:

[COLOR="Red"]FATAL ERROR: Acrobat Reader
An apt-based error occurred and installation was unsuccessful[/COLOR]

Using apt-get from the BASH prompt gives the following...

sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevent-execflow-perl airstrike-common libfame-0.9 libintl-perl libpvm3
  libevent-rpc-perl gtk2-ex-formfactory-perl lsdvd anyevent-perl gocr
  libevent-perl libnetpbm10
Use 'apt-get autoremove' to remove them.
Suggested packages:
  acroread-plugins mozilla-acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.9MB of archives.
After unpacking 56.0MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  acroread
Install these packages without verification [y/N]? y
Selecting previously deselected package acroread.
(Reading database ... 120053 files and directories currently installed.)
Unpacking acroread (from .../acroread_7.0.9-0.1_i386.deb) ...
Setting up acroread (7.0.9-0.1) ...

guy@linuxbox:~$ 

Fine, except it doesn't work!

Guy

---

### Post by chintana on 2007-01-17
> **guy.murray said:**
> Hi,
Running it from the BASH prompt results in the following...

expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error

endlessly until Ctrl Cing out of it.


Solution is here -> [http://remi.collet.free.fr/index.php?2007/01/10/273-acrobat-reader-709-et-fedora-core-6](http://remi.collet.free.fr/index.php?2007/01/10/273-acrobat-reader-709-et-fedora-core-6)

Works fine on six dot ten.

---

### Post by LxP on 2007-01-28
Thanks chintana!  This worked well for me on Edgy.  I did change one of the lines slightly though, because on my system the acroread script lives in /usr/**lib**/Adobe/Acrobat7.0/bin (and not /usr/**local**/Adobe/Acrobat7.0/bin).

---

