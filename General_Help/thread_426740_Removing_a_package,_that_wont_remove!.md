---
title: "Removing a package, that wont remove!"
date: 2007-04-28
forum: General Help
---

### Post by [Flux] on 2007-04-28
Hi all, i tried installing vmware through a how to here on the forums. I decided to remove it, and now it just wont leave my system!

```

###@###~$ sudo aptitude purge vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libssl0.9.7 
The following packages will be REMOVED:
  vmware-player{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 37.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 100156 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I have tried using Synaptic and apitude. If anyone could please help me, it would be great!

---

### Post by Belathor on 2007-04-28
Hmm... according to [this]("http://ubuntuforums.org/showthread.php?t=411473&highlight=uninstall+vmware") thread, vmware has an uninstall script in /usr/bin. Maybe you could try that?

---

### Post by [Flux] on 2007-04-28
yeah i tried looking there, nothing. sorry should have posted that i did a search of the forums, and tried what I found, to no avail :(

###@####:/usr/bin$ ./vmplayer uninstall.pl
./vmplayer: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found


YAY fixed

 using [http://ubuntuforums.org/showthread.php?t=426198](http://ubuntuforums.org/showthread.php?t=426198)


Thanks for all the help!

---

### Post by Belathor on 2007-04-28
Ok, I did a Google search and found what looked like the same error in an older [post]("http://ubuntuforums.org/showthread.php?t=289974") from October 2006. You probably already saw it, but just in case you overlooked, I thought I'd post it.

---

