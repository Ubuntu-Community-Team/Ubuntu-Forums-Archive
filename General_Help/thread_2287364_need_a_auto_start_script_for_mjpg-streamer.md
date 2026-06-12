---
title: "need a auto start script for mjpg-streamer"
date: 2015-07-18
forum: General Help
---

### Post by jim97 on 2015-07-18
Hi
  I am in need of a daemon to control mjpg_streamer.  I've seen only a few thru google but don't know how to set them up.
Should it be a startup script or a sysV init.d script??

This one line command run in a terminal will start mjpg_streamer and allow me to view the output on any computer in the networks browser.
sudo /usr/bin/mjpg_streamer -i "/usr/lib/input_uvc.so -f 15 -r 352x288" -o "/usr/lib/output_http.so -p 8088"

Thanks
Jim

---

### Post by jim97 on 2015-07-19
Found a upstart example and created the following script, placed it in /etc/init .  It doesn't work as expected, gives no error messages and I am not sure were to look for any error messages.

/etc/init/mjpg.conf
> 
#description "mjpgstreamer - stream webcam to port 8088"
#author "JRH 19jul15 "

# Stanzas
#
# Stanzas control when and how a process is started and stopped
# See a list of stanzas here: [http://upstart.ubuntu.com/wiki/Stanzas#respawn](http://upstart.ubuntu.com/wiki/Stanzas#respawn)

# When to start the service
start on runlevel [2345]

# When to stop the service
stop on runlevel [016]

# Automatically restart process if crashed
respawn

# Essentially lets upstart know the process will detach itself to the background
expect fork

# Start the process
exec /usr/bin/mjpg_streamer -i "/usr/lib/input_uvc.so -f 15 -r 352x288" -o "/usr/lib/output_http.so -p 8088"


Anyone see anything wrong?  where would any errors be show?

Edit:  The last line of the script (without the exec command) run in a terminal as root starts up mjpg-steamer and logs to the /var/log/syslog file.  But the script produces no output in that file.

Thanks
Jim

---

### Post by jim97 on 2015-07-19
I think I hear an echo..  Created a systemd script after checking that it was using systemd init.

mjpg.service
> 
[Unit]
Description=Job that runs mjpg_streamer

[Service]
Type=forking
Enviroment=statedir=/usr/bin
ExecStart=/usr/bin/mjpg_streamer -i "/usr/lib/input_uvc.so -f 15 -r 352x288" -o "/usr/lib/output_http.so -p 8088"

[Install]
WantedBy=multi=user.target


It starts, stops and gives status with systemctl.   But it doesn't start up on reboot??

root@mill:/lib/systemd/system# systemctl  enable mjpg.service
Failed to execute operation: Invalid argument

Any help appreciated 
Jim

---

### Post by jim97 on 2015-07-21
Anyone have an idea why  # systemctl enable mjpg.service     would result in a Failed to execute operation: Invalid argument   error?

Thanks
Jim

---

### Post by jim97 on 2015-08-16
Well the final solution was to use /etc/rc.local

cat rc.local
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

echo before-mjpg
/usr/bin/mjpg_streamer -i "/usr/lib/input_uvc.so -f 15 -r 352x288" -o "/usr/lib/output_http.so -p 8088"

echo after-mjpg

exit 0




Just for general info.
Jim

---

