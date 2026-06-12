---
title: "Trying initctl, not all commands seem to be executed"
date: 2012-12-01
forum: General Help
---

### Post by jimkd1yv on 2012-12-01
I am trying to use initctl to run a script when I boot this machine, running Kubuntu 12.04 with all patches.  (I was very comfortable on previous releases using init.d, but this is my first foray into initctl.)  I created a script, then am running it with initctl.  

When I run it manually (sudo initctl start bkupHPmedia), it works correctly.  

However, when I let it auto-run at boot time, some of the commands are being successfully executed (I can see their results on the target system they connect to).  Others are apparently failing, but I cannot see why.  There is no log being created by initctl (although I think there is a way to do so, but haven't found it).

Here is my conf file from /etc/init/bkupHP.conf
# backup HP media service
description     "backup HP media"
author          "Jim R"

start on (local-filesystems and net-device-up IFACE!=lo and networking and network-manager )
stop on runlevel [016]

expect fork
normal exit 0 1 2 3 4

task
exec /backups/HPdesktop/multimedia/bkupHPmedia
===
That script does the following:
#!/bin/bash
sleep 120
# see if the target host is online
ping -c1 192.168.1.107
rcping=$?
if [rcping -gt 0]
  then exit rcping
fi
#
cd /backups/HPdesktop/multimedia
# use the port knocker to open the ssh port on the HP desktop 
wget 192.168.1.107:NNNN
sleep 5
#
wget 192.168.1.107:NNNN
sleep 5
#
wget 192.168.1.107:NNNN
sleep 5
#
rsync -av kd1yv3@192.168.1.107:/multimedia/images ./
sleep 5
#
===

I can see the successful results of the wget commands on the target system, so I know that they are working.  However, the rsync is not retrieving newly modified files.

As I stated, it works perfectly if I run it from the command line, but not if it auto-runs at boot time.

If nothing else, I need to know how to get all of the commands to log so I can see what is wrong.

Thanks

JimR

---

### Post by jimkd1yv on 2012-12-01
I figured out why rsync wasn't working when run at boot.  Since it was running as root instead of my normal account, the ssh keys were different.  I corrected those, and all worked correctly.

However, that does not explain the lack of logging.  Any suggestions?

Thanks,
JimR

---

