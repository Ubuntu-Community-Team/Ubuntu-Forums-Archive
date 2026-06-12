---
title: "Beagle Daemon Error Log Not Found"
date: 2005-06-15
forum: General Help
---

### Post by XDevHald on 2005-06-15
> Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.
 
I started the daemon with beagled as the user not as root just incase if anyone was wondering. But when I installed the packages they told me to install, they worked, but now I am not able to find the beagle log file on my system. Odd?

**Edit: **Found the log files. Also I did add to the fstab - 
> /dev/hda3     /home     ext3     defaults,user_xattr     1 2

Then did: **mount -o remount /home** - of course in this case I was unable to get the process - [b]mount: /home not mounted already, or bad option

[/b]Anyone have any suggestions? :)

---

