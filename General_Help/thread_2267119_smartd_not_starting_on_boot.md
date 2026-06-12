---
title: "smartd not starting on boot"
date: 2015-02-27
forum: General Help
---

### Post by jim97 on 2015-02-27
Hi

  New to Ubuntu and trying to get smartmontools running on a installation of 14.04.   installed smartd and checked /etc/init.dsmartmontools  ran update-rc.d smartmontools defaults and checked /etc/smartd.conf (copy below).  Google'n the problem gave the string below to test if it was a problem with the installation or with the init.d script.  
smartd -c /etc/smartd.conf -p /var/run/smartd.pid --logfacility=local3
And it looks like the script.  The command above will start smartd but it won't restart on boot.  I've added the "start_smartd=yes" line from another thread but that hasn't worked.


smartd.conf
> 
# Sample configuration file for smartd.  See man smartd.conf.

start_smartd=yes
# Home page is: [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

# smartd will re-read the configuration file if it receives a HUP
# signal

# The file gives a list of devices to monitor using smartd, with one
# device per line. Text after a hash (#) is ignored, and you may use
# spaces and tabs for white space. You may use '\' to continue lines.

# You can usually identify which hard disks are on your system by
# looking in /proc/ide and in /proc/scsi.

# The word DEVICESCAN will cause any remaining lines in this
# configuration file to be ignored: it tells smartd to scan for all
# ATA and SCSI devices.  DEVICESCAN may be followed by any of the
# Directives listed below, which will be applied to all devices that
# are found.  Most users should comment out DEVICESCAN and explicitly
# list the devices that they wish to monitor.
#DEVICESCAN -d removable -n standby -m root -M exec /usr/share/smartmontools/smartd-runner
#/dev/sda -a 

/dev/sda -a -d ata -o on -I 194 -I 231 -S on -s (O/../../5/11|L/../../5/13|C/../../5/15) -m root


Any help appreciated
Jim

---

### Post by oldos2er on 2015-02-27
Edit /etc/default/smartmontools, remove the # comment mark from the line *#start_smartd=yes*. Reboot. Is that the change you were referring to? I've never needed to change anything other than this to get smartd to start.

---

### Post by jim97 on 2015-02-27
Ann

   That did it.  I must have made the edit to the wrong file.

Thanks
Jim

---

### Post by tgalati4 on 2015-02-27
You can mark this thread as SOLVED in the thread tools menu in the upper right.

---

