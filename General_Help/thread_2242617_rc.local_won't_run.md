---
title: "rc.local won't run"
date: 2014-09-02
forum: General Help
---

### Post by ..jeff.. on 2014-09-02
Hi,

My rc.local won't run as a service / at any of the run levels, but when I execute it after I log in, it works. To restate, when I reboot, I expect this command: "echo hi > /dev/shm/test" to create a file /dev/shm/test, but it doesn't. When I sudo /etc/rc.local, it creates the file (and the mount when I uncomment it). Sample of that in the 3rd code snippet below.

I have no idea what to look at/for anymore, so any direction is really appreciated.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
# exec 2> /tmp/rc.local.log
# exec 1>&2
# set -x
/bin/echo hi > /dev/shm/test

# /bin/mount -t vboxsf -o rw,uid=1000,gid=1000 Ramdisk /mnt/Ramdisk
exit 0

```


I tried removing and adding the service back, no luck.
```
jeff@Nazara:/dev/shm$ sudo update-rc.d -f rc.local remove
 Removing any system startup links for /etc/init.d/rc.local ...
   /etc/rc0.d/K20rc.local
   /etc/rc1.d/K20rc.local
   /etc/rc2.d/S20rc.local
   /etc/rc3.d/S20rc.local
   /etc/rc4.d/S20rc.local
   /etc/rc5.d/S20rc.local
   /etc/rc6.d/K20rc.local
jeff@Nazara:/dev/shm$ sudo update-rc.d rc.local defaults
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rc.local Default-Stop values (none)
 Adding system startup for /etc/init.d/rc.local ...
   /etc/rc0.d/K20rc.local -> ../init.d/rc.local
   /etc/rc1.d/K20rc.local -> ../init.d/rc.local
   /etc/rc6.d/K20rc.local -> ../init.d/rc.local
   /etc/rc2.d/S20rc.local -> ../init.d/rc.local
   /etc/rc3.d/S20rc.local -> ../init.d/rc.local
   /etc/rc4.d/S20rc.local -> ../init.d/rc.local
   /etc/rc5.d/S20rc.local -> ../init.d/rc.local


```

and after a reboot:

```
jeff@Nazara:/dev/shm$ ls | grep test
jeff@Nazara:/dev/shm$ sudo /etc/rc.local
[sudo] password for jeff: 
jeff@Nazara:/dev/shm$ ls | grep test
test
jeff@Nazara:/dev/shm$ 
```

The goal is to get the mount command to work, but I'm stuck at echo'ing hi. The mount is commented out above, so that shouldn't be causing any issues.

I tried manually adding the file to run level 5 as a test, no luck (although I have no idea if that would normally work).

```
jeff@Nazara:/etc/rc5.d$ sudo ln -s ../init.d/rc.local S99rcLocalTest
jeff@Nazara:/etc/rc5.d$ ls -ltr | grep -i rcLocal
lrwxrwxrwx 1 root root  18 Sep  2 22:29 S99rcLocalTest -> ../init.d/rc.local
jeff@Nazara:/etc/rc5.d$ 

```

Other services are running, both created by the OS and my own.

I'm running Xubuntu (lsb_release says Ubuntu 14.04.1 LTS) in VirtualBox 4.3.6.

```
jeff@Nazara:/etc/rc5.d$ uname -a
Linux Nazara 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```


EDIT: rc.local has the correct permissions (I think)
```
jeff@Nazara:/etc$ ls -ltr rc.local
-rwxr-xr-x 1 root root 452 Sep  2 22:26 rc.local
jeff@Nazara:/etc$

```

---

