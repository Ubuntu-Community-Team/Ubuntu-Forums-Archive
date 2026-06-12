---
title: "DPKG HANG with erp5-slapos package"
date: 2014-09-29
forum: General Help
---

### Post by BKk64bp on 2014-09-29
I have installed erp5-slapos package on Ubuntu 10.04 server. The installation generated errors. When I try to force remoe it I get these errors:
```
dpkg: error processing package erp5-slapos (--remove):
 subprocess installed pre-removal script returned error exit status 127
chown: cannot access ‘/opt/erp5-5.4.7-rc0/instance-root/default/var/run/mysqld.sock’: No such file or directory
chmod: cannot access ‘/opt/erp5-5.4.7-rc0/instance-root/default/var/run/mysqld.sock’: No such file or directory
chown: cannot access ‘/opt/erp5-5.4.7-rc0/instance-root/supervisord.socket’: No such file or directory
```

I tried

dpkg --remove --force-remove-reinstreq erp5-slapos
also
apt-get install --reinstall dpkg

DPKG asks to do a
dpkg --configure -a

which always brings back the subprocess that hangs DPKG 
It's a cacth 22

Tried also to kill the process group but this will kill DPKG and it will not work without
dpkg --configure -a

which brings the loop again

How can I stop this loop tu uninstall erp5-slapos?

---

### Post by Bashing-om on 2014-09-29
BKk64bp; Hi !
This:
> 
You have searched for packages that names contain erp5-slapos in suite(s) lucid, all sections, and all architectures.

Sorry, your search gave no results

says you did not install from the ubuntu software repository, thus 'dpkg' is not tracking it, and it is not in the package manager's data base.
Maybe a hard row to hoe to remove it ? .. How did you install it ? Did the author offer any guidance on a removal procedure ?

[INDENT][INDENT]that cat may get skinned
[INDENT][INDENT][INDENT][INDENT]leaving claw marks behind
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-09-29
> **BKk64bp said:**
> How can I stop this loop tu uninstall erp5-slapos?

Well, you should ask wherever you got the package from.
It's not Ubuntu software, it's *their* responsibility to provide support to their broken package.

The errors involve missing files. So one way to break the loop is to create dummy files for the uninstall script to remove.
```
touch /opt/erp5-5.4.7-rc0/instance-root/default/var/run/mysqld.sock
touch /opt/erp5-5.4.7-rc0/instance-root/supervisord.socket
```

Another way is to force dpkg to delete the package record from it's database without deleting any of the files( --force-remove-reinstreq). Then you clean up the files manually. Not recommended until you have tried everything else - I consider it the nuclear option; it can have fallout.

---

### Post by BKk64bp on 2014-10-13
I made the dummy files. No luck. DPKG still cannot configure the package. Also --force-remove-reinstreq gives conflict error because of the hang "configure" thing. So my best shot was to delete the package folder. Now I have thousands of chown error when I did 
dpkg --force-remove-reinstreq -r erp5-slapos
after that returned:

> dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 erp5-slapos

chown errors show up everytime I install a new package

Is there a way to kill this post-installation script?

Thanks for trying to help, I am trying to talk with the package people with no response so far.

---

### Post by ian-weisser on 2014-10-13
The postinstall script should be at /var/lib/dpkg/info/erp5-slapos.postinst

Please show us the contents of the file.

---

### Post by BKk64bp on 2014-10-14
[SOLVED]

Thanks Ian, in the meantime I have found what I needed here:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

As I don't need the package in this server anymore I fixed dpkg removing all erp5-slapos package info files:

> cd /var/lib/dpkg/info
sudo rm erp5-slapos.*

Then

> sudo dpkg --remove --force-remove-reinstreq erp5-slapos

---

