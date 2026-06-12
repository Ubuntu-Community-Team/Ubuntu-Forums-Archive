---
title: "sysv init script not running"
date: 2014-04-03
forum: General Help
---

### Post by brendand2 on 2014-04-03
13.10:  I have installed an old piece of software that requires a license service(flexnet) to be running. The original instructions are for a sysv init script.  I followed these instructions but the service is not starting at boot. The script works properly with a start/stop argument from the command line e.g. ```
/etc/init.d/flexnet start
```

How do I diagnose why this script is not running at startup? I can't see anything in the logs.
```
$ ls -l /etc/rc*.d/*flex*
lrwxrwxrwx 1 root root 17 Apr  2 12:42 /etc/rc2.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc3.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc4.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc5.d/S99flexnet -> ../init.d/flexnet
```

---

### Post by ian-weisser on 2014-04-03
Is the init file too long to post?

---

### Post by brendand2 on 2014-04-07
I assumed that since the script ran properly from the command line, the problem lie elsewhere. What bothers me is not being able to find anything in the log about it failing. Here is the init:
```
#!/bin/sh
#
# MATLAB FLEXnet Network License Manager Daemon
#
#       For boot-time initialization on Linux
#
# Steps: (as root)
#
#    If the following links do not exist create them:
#
#    ln -s $MATLAB/etc/lmboot /etc/lmboot_TMW
#    ln -s $MATLAB/etc/lmdown /etc/lmdown_TMW
#    
#    Then:
#
#    cp $MATLAB/etc/flexnet.boot.linux /etc/init.d/flexnet      (Debian, SuSE)
#    cp $MATLAB/etc/flexnet.boot.linux /etc/rc.d/init.d/flexnet (Red Hat, Fedora Core)
#
#    CRITICAL: replace username argument to the lmboot_TMW commands 
#              below by a real usename OTHER than root!
#
#    Look in /etc/inittab for the default runlevel. Create
#    a link in the rc directory associated with that run
#    level. For example if it is 5, then
#
#    cd /etc/rc5.d;        ln -s ../init.d/flexnet S90flexnet (Debian)
#    cd /etc/init.d/rc5.d; ln -s ../flexnet S90flexnet (SuSE)
#    cd /etc/rc.d/rc5.d;   ln -s ../init.d/flexnet S90flexnet (Red Hat, Fedora Core)
#
case "$1" in
  start)
        if [ -f /etc/lmboot_TMW ]; then
            /etc/lmboot_TMW -u dbrick && echo 'MATLAB_lmgrd'
        fi
        ;;
  stop)
        if [ -f /etc/lmdown_TMW ]; then
            /etc/lmdown_TMW  > /dev/null 2>&1
        fi
        ;;
  *)
        echo "Usage: $0 {start|stop}"
        exit 1
        ;;
esac


exit 0
```

update:
Changed the line to:
```
/etc/lmboot_TMW -u dbrick && echo 'MATLAB_lmgrd' >> /var/tmp/flexnet_test.log 2>&1
```
and no file  /var/tmp/flexnet_test.log exists after reboot, so the init script is not being run at all. Why would this be?

---

### Post by steeldriver on 2014-04-07
... don't like the look of this [COLOR=#ff0000]**#**[/COLOR]

```

#!/bin/sh[COLOR=#ff0000]**#**[/COLOR]
# MATLAB FLEXnet Network License Manager Daemon
#
#       For boot-time initialization on Linux

```

---

### Post by brendand2 on 2014-04-07
Sorry. That was a cut and paste typo. Edited original post. If that typo was in there the question remains why nothing appears in the log. As far as I can tell the script is not running at all. I have googled this sort of thing and most answers are that the script permissions are incorrect or that the user did not properly set up the rc?.d symlinks.

---

### Post by steeldriver on 2014-04-07
```
/etc/lmboot_TMW -u dbrick && echo 'MATLAB_lmgrd' >> /var/tmp/flexnet_test.log 2>&1
```

You need to be a bit careful about what you infer from the absence of the flexnet_test.log here - the way '&&' works is that it will execute the echo command *only if the lmboot_TMW command executes successfully*. It would be less ambiguous to do

```

echo 'MATLAB_lmgrd' >> /var/tmp/flexnet_test.log 2>&1
/etc/lmboot_TMW -u dbrick 

```

---

### Post by sandyd on 2014-04-07
> **brendand2 said:**
> 13.10:  I have installed an old piece of software that requires a license service(flexnet) to be running. The original instructions are for a sysv init script.  I followed these instructions but the service is not starting at boot. The script works properly with a start/stop argument from the command line e.g. ```
/etc/init.d/flexnet start
```

How do I diagnose why this script is not running at startup? I can't see anything in the logs.
```
$ ls -l /etc/rc*.d/*flex*
lrwxrwxrwx 1 root root 17 Apr  2 12:42 /etc/rc2.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc3.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc4.d/S99flexnet -> ../init.d/flexnet
lrwxrwxrwx 1 root root 17 Apr  3 10:18 /etc/rc5.d/S99flexnet -> ../init.d/flexnet
```

Have you tried adding it to startup - i.e.
```

sudo update-rc.d flexnet defaults
```

---

### Post by brendand2 on 2014-04-07
Yes, I did both:
```
$sudo update-rc.d flexnet defaults
update-rc.d: warning: /etc/init.d/flexnet missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/flexnet already exist.


$sudo update-rc.d flexnet enable
update-rc.d: warning: /etc/init.d/flexnet missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Enabling system startup links for /etc/init.d/flexnet ...
 Removing any system startup links for /etc/init.d/flexnet ...
   /etc/rc2.d/S99flexnet
   /etc/rc3.d/S99flexnet
   /etc/rc4.d/S99flexnet
   /etc/rc5.d/S99flexnet
 Adding system startup for /etc/init.d/flexnet ...
   /etc/rc2.d/S99flexnet -> ../init.d/flexnet
   /etc/rc3.d/S99flexnet -> ../init.d/flexnet
   /etc/rc4.d/S99flexnet -> ../init.d/flexnet
   /etc/rc5.d/S99flexnet -> ../init.d/flexnet
```

sysv-rc-conf shows flexnet as enabled for runlevels 2-5

addendum:

With advice about the redirection(>>) after the short circuit(&&) I have ascertained that the script is indeed running. The problem is the crappy command it calls produces not output so I can not easily debug the problem. But at least I know that it is running. Thanks.

---

