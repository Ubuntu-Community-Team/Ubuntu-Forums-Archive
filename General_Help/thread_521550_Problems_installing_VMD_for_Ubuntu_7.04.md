---
title: "Problems installing VMD for Ubuntu 7.04"
date: 2007-08-09
forum: General Help
---

### Post by pinkieinc on 2007-08-09
Hi

I am a new user and I'm trying to download and run VMD. However, my console window briefly pops up and then immediately disappears. One possible way to troubleshoot is to type the command yum install compat-libstdc++-33. But that is the command for Fedora Core 5. Does anyone know how to do this for Ubuntu? I'm getting the following error messages:

administrator@pinkieinc:~$ yum install compat-libstdc++-33
Warning, could not load sqlite, falling back to pickle
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
Traceback (most recent call last):
  File "/usr/bin/yum", line 27, in <module>
    yummain.main(sys.argv[1:])
  File "/usr/share/yum-cli/yummain.py", line 75, in main
    base.getOptionsConfig(args)
  File "/usr/share/yum-cli/cli.py", line 170, in getOptionsConfig
    self.doConfigSetup(fn=opts.conffile, root=root)
  File "/var/lib/python-support/python2.5/yum/__init__.py", line 82, in doConfigSetup
    self.conf = config.yumconf(configfile=fn, root=root)
  File "/var/lib/python-support/python2.5/yum/config.py", line 271, in __init__
    self.yumvar['releasever'] = self._getsysver()
  File "/var/lib/python-support/python2.5/yum/config.py", line 383, in _getsysver
    idx = ts.dbMatch('provides', self.getConfigOption('distroverpkg'))
TypeError: rpmdb open failed



Please let me know.

Thanks!

Pinkie

---

### Post by Claus7 on 2007-10-31
Hello,

this might help you 
[http://ubuntuforums.org/showthread.php?t=598518&highlight=vmd](http://ubuntuforums.org/showthread.php?t=598518&highlight=vmd)

Regards!

---

