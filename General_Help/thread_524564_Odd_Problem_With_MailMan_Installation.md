---
title: "Odd Problem With MailMan Installation"
date: 2007-08-13
forum: General Help
---

### Post by pgupta on 2007-08-13
Hi,

I'm a very new Ubuntu user -- I'm quite familiar with Gentoo and FC, but I've run into an odd snag when apt-get'n mailman.

Here is the error I am getting when I try to remove the mailman package (I've lost the errors it initially gave me when installing)...

```

root@oprah:~# apt-get remove mailman
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxmlsec1 libmono-security1.0-cil openoffice.org-style-default intltool-debian libmono-sharpzip0.84-cil libxmlsec1-openssl libbtctl4 libglib1.2
  libmono-sqlite1.0-cil libxt-java libxml-perl libmono-system-web1.0-cil libxmlsec1-nss po-debconf gettext libmono1.0-cil libmono-data-tds1.0-cil
  libmono-system-data1.0-cil libmeanwhile1 libmyspell3c2 pmount libgnomebt0 libopenobex1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mailman
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 40.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 99358 files and directories currently installed.)
Removing mailman ...
 * Stopping Mailman master qrunner mailmanctl                                                                                                                 Traceback (most recent call last):
  File "/usr/lib/mailman/bin/mailmanctl", line 107, in <module>
    from Mailman import Utils
  File "/usr/lib/mailman/Mailman/Utils.py", line 351, in <module>
    def MakeRandomPassword(length=mm_cfg.MEMBER_PASSWORD_LENGTH):
AttributeError: 'module' object has no attribute 'MEMBER_PASSWORD_LENGTH'
                                                                                                                                                       [fail]
invoke-rc.d: initscript mailman, action "stop" failed.
dpkg: error processing mailman (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/var/lib/mailman/bin/list_lists", line 47, in <module>
    from Mailman import MailList
  File "/usr/lib/mailman/Mailman/MailList.py", line 45, in <module>
    from Mailman import Utils
  File "/usr/lib/mailman/Mailman/Utils.py", line 351, in <module>
    def MakeRandomPassword(length=mm_cfg.MEMBER_PASSWORD_LENGTH):
AttributeError: 'module' object has no attribute 'MEMBER_PASSWORD_LENGTH'
Traceback (most recent call last):
  File "/usr/lib/mailman/bin/update", line 50, in <module>
    from Mailman import Utils
  File "/usr/lib/mailman/Mailman/Utils.py", line 351, in <module>
    def MakeRandomPassword(length=mm_cfg.MEMBER_PASSWORD_LENGTH):
AttributeError: 'module' object has no attribute 'MEMBER_PASSWORD_LENGTH'
Traceback (most recent call last):
  File "/var/lib/mailman/bin/list_lists", line 47, in <module>
    from Mailman import MailList
  File "/usr/lib/mailman/Mailman/MailList.py", line 45, in <module>
    from Mailman import Utils
  File "/usr/lib/mailman/Mailman/Utils.py", line 351, in <module>
    def MakeRandomPassword(length=mm_cfg.MEMBER_PASSWORD_LENGTH):
AttributeError: 'module' object has no attribute 'MEMBER_PASSWORD_LENGTH'
 * Site list for mailman (usually named mailman) missing.
 * Please create it; until then, mailman will refuse to start.
Errors were encountered while processing:
 mailman
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@oprah:~#

```

I am at a total loss here -- do any of you have an idea of how to resolve this issue?  I am not actually trying to remove mailman, I just need to install and configure it correctly...


THANKS!

---

### Post by PaulFr on 2007-08-13
I would suggest to run ```
sudo apt-get update
sudo apt-get autoremove
```first to clean up packages that can be removed. Now, if all you want is to reconfigure mailman,```
sudo dpkg-reconfigure mailman
```

---

### Post by pgupta on 2007-08-13
```

root@oprah:~# dpkg-reconfigure mailman
 * Stopping Mailman master qrunner mailmanctl                                                                         Traceback (most recent call last):
  File "/usr/lib/mailman/bin/mailmanctl", line 107, in <module>
    from Mailman import Utils
  File "/usr/lib/mailman/Mailman/Utils.py", line 351, in <module>
    def MakeRandomPassword(length=mm_cfg.MEMBER_PASSWORD_LENGTH):
AttributeError: 'module' object has no attribute 'MEMBER_PASSWORD_LENGTH'
                                                                                                               [fail]
invoke-rc.d: initscript mailman, action "stop" failed.
root@oprah:~#

```


that command seems to fail too =\

---

### Post by PaulFr on 2007-08-13
Looks like mailman was not configured properly, so it does not know how to shutdown any running processes. The one possibility I can suggest is ```
sudo dpkg-reconfigure --force mailman
```.

---

### Post by pgupta on 2007-08-13
That fails as well -- same kind of problem.

mm_cfg.py is actually empty -- not by my doing, but it is.  I imagine this probably has something to do with it?

---

### Post by pgupta on 2007-08-13
Would it be easy to force the removal of this package?   :confused:

---

### Post by PaulFr on 2007-08-13
I installed the source for mailman (using **cd /usr/src; sudo apt-get source mailman** and the default mm_cfg.py file seems to have only one line ```
from Defaults import *
``` and the MEMBER_PASSWORD_LENGTH is defined as 8 in Defaults.py. You may want to check this.

---

### Post by pgupta on 2007-08-14
That's the weirdest thing -- my mm_cfg.py didn't even have that line.  once I added it, things started working again and I could remove the package -- I'm going to try to reinstall it now.

btw, THANKS!  Seriously.   :KS

---

### Post by brainbuzz on 2007-09-29
I had the same error on a server running on debian etch. A symlink python in /usr/bin/ to /usr/bin/python2.4 solved it.

---

