---
title: "init.d script doesn't start"
date: 2014-11-12
forum: General Help
---

### Post by arapaho on 2014-11-12
[Sandfox script]("http://igurublog.wordpress.com/downloads/script-sandfox") worked well on 13.10 but not on 14.04. I suspect something in system has changed.

When I do 
```
sudo /etc/init.d/sandfox start 
```
it starts and works but only until I restart system. It fails to start at system boot.
I don't understand why. [Here are details]("http://pastebin.com/1aP4A76z").
I followed strictly guidelines when creating it:
```
sudo apt-get install inotify-tools lsof
sudo install sandfox /usr/local/bin/sandfox
sudo nano /etc/init.d/sandfox
sudo chmod +x /etc/init.d/sandfox
sudo update-rc.d sandfox defaults
sudo sandfox firefox
```

---

### Post by btindie on 2014-11-12
What's the output of
```
find /etc/ -type l -name \*sandfox 2>/dev/null
```
That should list which runlevels that file is to be used in.

As if there isn't any then it may be because
```
sudo update-rc.d sandfox defaults
```
was unable to add it's links correctly as the example init file on the [sandfox]("http://igurublog.wordpress.com/downloads/script-sandfox/") website is missing the LSB comment header which I think is used by update-rc.d. This would be because there are no 'defaults' specified in the init file.

See 'man update-rc.d' and 'man insserv'.

e.g. from /etc/init.d/ssh
> #! /bin/sh

### BEGIN INIT INFO
# Provides:             sshd
# Required-Start:       $remote_fs $syslog
# Required-Stop:        $remote_fs $syslog
# Default-Start:        2 3 4 5
# Default-Stop:         
# Short-Description:    OpenBSD Secure Shell server
### END INIT INFO

---

### Post by arapaho on 2014-11-12
```
find /etc/ -type l -name \*sandfox 2>/dev/null
/etc/rc3.d/S20sandfox
/etc/rc0.d/K20sandfox
/etc/rc2.d/S20sandfox
/etc/rc1.d/K20sandfox
/etc/rc4.d/S20sandfox
/etc/rc6.d/K20sandfox
/etc/rc5.d/S20sandfox
```

"See 'man update-rc.d' and 'man insserv"
I wish but I don't understand much of it.

I found
[http://askubuntu.com/questions/335242/how-to-install-an-init-d-script-in-ubuntu](http://askubuntu.com/questions/335242/how-to-install-an-init-d-script-in-ubuntu)

And I did
```
sudo ln -s /usr/lib/insserv/insserv /sbin/insserv

sudo insserv sandfox
insserv: warning: script 'K20sandfox' missing LSB tags and overrides
insserv: warning: script 'sandfox' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: There is a loop between service rc.local and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service sandfox if started
insserv: There is a loop between service sandfox and umountfs if started
insserv:  loop involving service umountfs at depth 1
insserv: There is a loop at service rc.local if started
insserv: Starting sandfox depends on rc.local and therefore on system facility `$all' which can not be true!
```

And I changed
```
#!/bin/bash
# Sandfox boot startup script for Ubuntu and similar
```
to
```
#!/bin/sh
### BEGIN INIT INFO
# Provides: sandfox
# Required-Start: $local_fs $network
# Required-Stop: $local_fs
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: sandfox
# Description: Sandfox boot startup script for Ubuntu and similar
### END INIT INFO
as it is in last comment on sandfox blog

sudo insserv sandfox
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
```

---

