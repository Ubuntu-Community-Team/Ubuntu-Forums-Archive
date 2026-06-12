---
title: "Ubuntu 12.10 Software Center and Software Updater started _not_ working"
date: 2013-05-07
forum: General Help
---

### Post by harlequin_ on 2013-05-07
Hi all,

I'm really not sure what caused it, but today I realized that I cannot launch  Software Center and Software Updater either from the launcher or the terminal. Nevertheless, "sudo apt-get update/upgrade/install" all seem to be working fine.

I am attaching the error I get when I try to run ```
software-center
``` in the terminal.

```
 Traceback (most recent call last):
  File "/usr/bin/software-center", line 36, in <module>
    from softwarecenter.utils import (
  File "/usr/share/software-center/softwarecenter/utils.py", line 19, in <module>
    import dbus
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 16, in <module>
    from xml.parsers.expat import ExpatError
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 36, in <module>
    from softwarecenter.utils import (
  File "/usr/share/software-center/softwarecenter/utils.py", line 19, in <module>
    import dbus
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt
```

What can be the issue? Does it have something to do with a broken Python library, or? 
Thanks in advance.

---

### Post by matt_symes on 2013-05-07
Hi

> **harlequin_ said:**
> Hi all,

I'm really not sure what caused it, but today I realized that I cannot launch  Software Center and Software Updater either from the launcher or the terminal. Nevertheless, "sudo apt-get update/upgrade/install" all seem to be working fine.

I am attaching the error I get when I try to run ```
software-center
``` in the terminal.

```
 Traceback (most recent call last):
  File "/usr/bin/software-center", line 36, in <module>
    from softwarecenter.utils import (
  File "/usr/share/software-center/softwarecenter/utils.py", line 19, in <module>
    import dbus
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 16, in <module>
    from xml.parsers.expat import ExpatError
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 36, in <module>
    from softwarecenter.utils import (
  File "/usr/share/software-center/softwarecenter/utils.py", line 19, in <module>
    import dbus
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: XML_SetHashSalt
```

What can be the issue? Does it have something to do with a broken Python library, or? 
Thanks in advance.

You have a broken python installation there.

I assume this returns nothing

```
strings /usr/lib/python2.7/lib-dynload/pyexpat.so | grep "XML_SetHashSalt"
```

Is this a 32 bit installation as on my 64-bit installation there is no *pyexpat.so* ?

Instead i have *pyexpat.x86_64-linux-gnu.so* and that contains the XML_SetHashSalt as confirmed using strings.

An apt-file search shows that *pyexpat.x86_64-linux-gnu.so *is in the package libpython2.7-stdlib so you may want to see if this is the same on your system and reinstall that package.

For apt-file

```
sudo apt-get install apt-file
```

```
apt-file update
```

```
apt-file search <package_name>
```

That may give you a place to diagnose what went wrong.

As for what happened to it... have you added/removed any software sources recently and installed any new software ?

You may want to look at your software sources

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Post them back here if you like.

Kind regards

---

### Post by harlequin_ on 2013-05-07
Hi, thanks for your reply! I have ```
x86_64 x86_64 x86_64 GNU/Linux
```.

```
string /usr/lib/python2.7/lib-dynload/pyexpat.so | grep "XML_SetHashSalt"
``` does return something :-)
```
No command 'string' found, did you mean:
 Command 'strings' from package 'binutils' (main)
 Command 'strings' from package 'binutils-multiarch' (universe)
 Command 'spring' from package 'spring' (universe)
string: command not found
```

I tried 

```
less /usr/lib/python2.7/lib-dynload/pyexpat.so | grep "XML_SetHashSalt"
"/usr/lib/python2.7/lib-dynload/pyexpat.so" may be a binary file.  See it anyway?
```

I installed apt-file and the following two return nothing (I searched under /, though I don't know if it's relevant)

```
apt-file search pyexpat.x86_64-linux-gnu.so
apt-file search libpython2.7-stdlib
```

And here's the list for my software sources:

```
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:deb http://nl.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list:deb http://archive.canonical.com/ quantal partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ quantal partner
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu quantal main
```

I tried to reinstall Python with ```
sudo apt-get --reinstall install python
``` but it did not help either.
By the way, just to be complete: I cannot launch Software Center but I can launch Software Updater for a couple of seconds. Then it directly quits without displaying any error before I can do anything.

Thank you for trying to help. Let me know if I can help with any further input.

---

### Post by matt_symes on 2013-05-07
Hi

Typo on my part. Should have beens

```
strings ... | grep ...
```

See if it contains XML_SetHashSalt.

I'll read through the rest of your post.

**EDIT:**

> I tried

An .so file is a binary file so viewing them using less will not shed much light.

On my system ```
apt-file search pyexpat.x86_64-linux-gnu.so
``` returns

```
libpython2.7-stdlib: /usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so
python2.7-dbg: /usr/lib/debug/usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so
```

Do you have that library installed on your system ?

Can you post the output of

```
cat /etc/ld.so.conf{,.d/*}
```

What does this return

```
dpkg -l libpython2.7-stdlib
```

You may be looking to install just that package so this may be what you need.

```
sudo apt-get --reinstall install libpython2.7-stdlib
```

but i would hold off running that command for a moment.

What does this return

```
apt-file search pyexpat.so
```

Can you also post the output of this command

```
cat /etc/lsb-release
```

I'll look through your sources in a moment.

**EDIT2:**

Your sources look alright to me at the moment

> I tried to reinstall Python with

```
sudo apt-get --reinstall install python
```

You may have to specify the version of python to install.

My system may be different to yours as we may be on different versions so it'll be interesting to see what version of Ubuntu you have installed - your sources say quantal but it's worth double checking. Was this a fresh install or an upgrade ?
 

Kind regards

---

### Post by harlequin_ on 2013-05-07
Dear Matt, thanks a lot for your throughout analysis and efforts, it means a lot and is what makes Ubuntu a great community. But the system with the problem is my work system and I will not be able to login to that system until next Monday (we've got some holidays here and since our genius admins think the only way to ensure security is to block incoming ssh request...). I'll report on Monday about the feedback you provided. Many thanks.

---

### Post by harlequin_ on 2013-05-14
Dear Matt, apologies for my late response. Below I tried to correspond to your comments.

```
strings /usr/lib/python2.7/lib-dynload/pyexpat.so | grep "XML_SetHashSalt" 
``` returns ```
XML_SetHashSalt
```

```
apt-file search pyexpat.x86_64-linux-gnu.so
``` does not return anything.

```
cat /etc/ld.so.conf{,.d/*}
``` returns the below:
```
include /etc/ld.so.conf.d/*.conf

# Multiarch support
/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu
/lib/i686-linux-gnu
/usr/lib/i686-linux-gnu
# libc default configuration
/usr/local/lib
# Multiarch support
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/mesa
```

```
dpkg -l libpython2.7-stdlib
``` returns ```
dpkg-query: no packages found matching libpython2.7-stdlib
```

```
sudo apt-get --reinstall install libpython2.7-stdlib
``` returns 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libpython2.7-stdlib
E: Couldn't find any package by regex 'libpython2.7-stdlib'
```

```
apt-file search pyexpat.so
``` returns 
```
python2.7: /usr/lib/python2.7/lib-dynload/pyexpat.so
python2.7-dbg: /usr/lib/debug/usr/lib/python2.7/lib-dynload/pyexpat.so
```

finally 
```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
```

> Was this a fresh install or an upgrade ?: I think this was a fresh install, but honestly I cannot be sure because I just found a 12.04 cd lying on my desk. I googled it to see whether there's a way to tell but no obvious hits at the first sight. Is this information any useful for solving the issue?

Cheers

---

### Post by matt_symes on 2013-05-14
Hi

> strings /usr/lib/python2.7/lib-dynload/pyexpat.so | grep "XML_SetHashSalt"

returns 

XML_SetHashSalt

Interesting. Your problem may be with libexpat.so

On my system pyexpat.x86_64-linux-gnu.so links into libexpat.so.1 and that contains XML_SetHashSalt and if libexpat.so.1 does not contain XML_SetHashSalt then you would get the error you see.

```
matthew-S206:/home/matthew/useful_commands_dir % ldd /usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so
        linux-vdso.so.1 =>  (0x00007fffafffe000)
        **libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fed34526000)**
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fed34309000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fed33f40000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fed3497a000)
matthew-S206:/home/matthew/useful_commands_dir % 
```

```
matthew-S206:/home/matthew/useful_commands_dir % strings /lib/x86_64-linux-gnu/libexpat.so.1 | grep XML_SetHashSalt
XML_SetHashSalt
matthew-S206:/home/matthew/useful_commands_dir % 
```

I think this may be where your problem lies.

What does this return ?

```
dpkg -l | grep libexpat


```

```
ldd /usr/lib/python2.7/lib-dynload/pyexpat.so
```

EDIT:

And finally this.

```
find /lib -name "libexpat.so.1" -exec bash -c "strings {} | grep XML_SetHashSalt" \;
```

Kind regards

---

### Post by harlequin_ on 2013-05-21
Hi again Matt, below are the commands you suggested and their results. I hope this helps:

```
dpkg -l | grep libexpat
ii  libexpat1:amd64                           2.1.0-1ubuntu1                            amd64        XML parsing C library - runtime library
ii  libexpat1:i386                            2.1.0-1ubuntu1                            i386         XML parsing C library - runtime library
ii  libexpat1-dev                             2.1.0-1ubuntu1                            amd64        XML parsing C library - development kit

ldd /usr/lib/python2.7/lib-dynload/pyexpat.so
    linux-vdso.so.1 =>  (0x00007ffff3dee000)
    libexpat.so.1 => /usr/local/lib/libexpat.so.1 (0x00007fc60399b000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fc60377e000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc6033be000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fc6031a8000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fc603dee000)

find /lib -name "libexpat.so.1" -exec bash -c "strings {} | grep XML_SetHashSalt" \;
XML_SetHashSalt
XML_SetHashSalt

```

Thanks!

---

### Post by harlequin_ on 2013-05-27
bump..

-edit-
I solved the problem by following [http://ubuntuforums.org/showthread.php?t=2094005](http://ubuntuforums.org/showthread.php?t=2094005) and doing the following:
```

cd /usr/local/lib
sudo mv libexpat.so.1 libexpat.so.1.BAK
```

and now -I guess- I  have libexpat.so.1 pointing to the right place

```
ldd /usr/lib/python2.7/lib-dynload/pyexpat.so
    linux-vdso.so.1 =>  (0x00007fffaa378000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f5c0980e000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f5c095f1000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f5c09231000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f5c0901b000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f5c09c61000)
```

Cheers

-edit 2-
Well, I forgot to report in the first edit that the issue is solved: update-manager and software-center working properly

---

### Post by matt_symes on 2013-05-27
Hi

Excellent news. :)

I'm glad you got it sorted and the solution makes a lot of sense in relation to the problem.

> libexpat.so.1 => /usr/local/lib/libexpat.so.1

^^ an unusual location of the library. Did you compile any software or install an software manually ?

Sorry i did not get back to you but i have not been on the forums much over the last couple of weeks or so.

Kind regards

---

### Post by harlequin_ on 2013-05-28
Hi Matt, no problems, you helped more than you should've probably! I'm not 100% sure if I've made any manual installations. But notice that the OP in the link I pasted above starts with

> Hello,

I upgraded to 12.10 recently, and am now experiencing problems with Software Updater

which indeed is what I did recently too. So I'm suspecting the problem originates from a 12.04 to 12.10 upgrade. But again, not with 100% certainty. 

Best regards

---

