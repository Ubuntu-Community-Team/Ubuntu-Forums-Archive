---
title: "Partition out of space while being 50% empty"
date: 2018-12-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-12-01
My 2 largest log files (293MB each) seem to be full of this message:
```
usb 3-10: usbfs: process 10976 (events) did not claim interface 0 before use
```
those files are kern.log.1 and syslog.1

The only other times i have had this issue is after dealing files cause i was out of disk space, but that was resolved with a reboot, but not only did not delete anything this time as i can not find the missing used gig a reboot did not get the system to realize it has free space

I am unable to check for updates due to disk space errors
```
Get:1 http://archive.canonical.com/ubuntu bionic InRelease [10.2 kB]
Err:1 http://archive.canonical.com/ubuntu bionic InRelease                     
  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.15 80]
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:3 http://ppa.launchpad.net/giuspen/ppa/ubuntu bionic InRelease             
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Err:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.23 80]
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Err:5 http://security.ubuntu.com/ubuntu bionic-security InRelease              
  Error writing to output file - write (28: No space left on device) [IP: 91.189.88.152 80]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Err:6 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.23 80]
Get:7 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease [21.3 kB]
Err:7 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
  Error writing to output file - write (28: No space left on device) [IP: 91.189.95.83 80]
Reading package lists... Done  
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.23 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.23 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/bionic/InRelease  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.15 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Error writing to output file - write (28: No space left on device) [IP: 91.189.88.152 80]
W: Failed to fetch http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/bionic/InRelease  Error writing to output file - write (28: No space left on device) [IP: 91.189.95.83 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
the only partition low on space looks to be /var in gparted, everything else has plenty

---

### Post by pqwoerituytrueiwoq on 2018-12-01
Found the extra gig booting live and checking, i have a sperate partition for apt's cache, a while back i was having issue with partitions not mounting, it seems that partition failed to mount and a gig of apt's cache was stored under my mount point (in other words my mount point was not empty)

---

