---
title: "Tokyocabinet &amp; Lessfs (What to do with sh file???)"
date: 2014-06-12
forum: General Help
---

### Post by g35celicaz on 2014-06-12
Hello, 

I am trying to install lessfs on Ubuntu 14.04 using this forum, but it hasn't been working for me :(

[http://ubuntuforums.org/showthread.php?t=1390085](http://ubuntuforums.org/showthread.php?t=1390085)

I do not know what to do with the files that the author provided: lessfs.sh 

Which contains this:

[HTML]#!/bin/sh
#
# lessfs This script starts and stops the spamd daemon
#
# chkconfig: - 78 30
# processname: lessfs
# description: lessfs a deduplicating filesystem

# Source function library.
#. /etc/rc.d/init.d/functions

prog="lessfs"

# Source networking configuration.
#. /etc/sysconfig/network

# Check that networking is up.
#[ ${NETWORKING} = "no" ] && exit 0
[ -f /var/run/network/ifstate ] && [ $(cat /var/run/network/ifstate | wc -l ) -eq 0 ] && exit 0

PATH=$PATH:/usr/local/bin
MKLESSFS=/usr/local/bin/mklessfs
MOUNTPOINT=/data
#LESSFS_OPTS="/etc/lessfs.cfg $MOUNTPOINT  -o kernel_cache,negative_timeout=0,entry_timeout=0,attr_timeout=0,use_ino,readdir_ino,default_permissions,allow_other,big_writes,max_read=4096,max_write=4096"
LESSFS_OPTS="/etc/lessfs.cfg $MOUNTPOINT  -o kernel_cache,negative_timeout=0,entry_timeout=0,attr_timeout=0,use_ino,readdir_ino,default_permissions,allow_other,big_writes,max_read=131072,max_write=131072"
LESSFS=/usr/local/bin/lessfs
# By default it's all good
RETVAL=0
export DEBUG=0

# See how we were called.
case "$1" in
  start)
	# Start daemon.
	echo -n $"Starting $prog: "
        $LESSFS $LESSFS_OPTS
	RETVAL=$?
        echo
	if [ $RETVAL = 0 ]; then
		touch /var/lock/lessfs
	fi
        ;;
  stop)
        # Stop daemons.
        echo -n $"Stopping $prog: "
        umount $MOUNTPOINT
        RETVAL=$?
        echo
	if [ $RETVAL = 0 ]; then
		rm -f /var/lock/lessfs
		rm -f $SPAMD_PID
	fi
        ;;
  restart)
        $0 stop
	sleep 3
        $0 start
        ;;
  *)
	echo "Usage: $0 {start|stop|restart}"
	RETVAL=1
	;;
esac

exit $RETVAL
[/HTML]

Or does anyone know how to install this on a Mac OSX? I have tried installing on both but have gotten no where 

Thanks for your help in advance!

---

### Post by llamabr on 2014-06-12
well, how far did you make it on those instructions, from the link you listed?

---

### Post by g35celicaz on 2014-06-13
I made it all the way up to: make && sudo checkinstall

I am stuck right at this step: sudo update-rc.d lessfs.sh enable

Currently, the lessfs-1.7.0 file is located on my desktop; so, in terminal, what I do is cd to it by using the following command: cd ./Desktop/lessfs-1.7.0

However, I do not see a the file location of: "etc/init.d" like he mentions in his tutorial: "Download it and save it to /etc/init.d"

I am assuming that I have to create the "init.d" folder in the etc folder? 

If you would like to see the original lessfs-1.7.0 folder you can download it from this website:  

[http://www.lessfs.com/wordpress/](http://www.lessfs.com/wordpress/)

Direct Link: [http://sourceforge.net/project/showfiles.php?group_id=257120](http://sourceforge.net/project/showfiles.php?group_id=257120)

----------------------------------------------------------------------**EDIT**---------------------------------------------------------------------

In fact I get the following error: "update-rc.d: /etc/init.d/lessfs.sh: file does not exist"

After using the provided command: "sudo update-rc.d lessfs.sh enable"

I have even tried using this command as well: "sudo update-rc.d lessfs.sh defaults" 

Any idea what I may be doing wrong?

Thank you for your help

---

