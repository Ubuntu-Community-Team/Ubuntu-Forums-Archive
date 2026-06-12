---
title: "Lost all network and USB functionality after system update"
date: 2015-10-02
forum: General Help
---

### Post by Michael_Serck on 2015-10-02
I have been using Linux on my laptop for about a year now, but am still a newbie. I installed Ubuntu 14.04 LTS on my HP laptop about a week ago, previously using Linux Mint. Everything was working great until yesterday I got a notification that a system update was available and to install it now. I went ahead and clicked Install Now, but after a while I got an error message that there was a problem with the update (package integrity or something similar, sorry I don't have exact message). I was leaving the office for the day so I just shut down my laptop. When I got home and booted my laptop back up later that evening I noticed my wifi was disabled (indicator light on laptop was orange instead of the usual blue). The laptop looked as though there was no wireless capability. Took the laptop over to my desk and plugged it into a wired connection and still no connection detected. I also noticed that the screen resolution looks distorted and now an external mouse doesn't work. It appears that many of the hardware drivers are no longer functioning correctly. I am unable to run any updates since I get absolutely no network connectivity. I realize that I could simply reinstall the OS, but I am in no hurry and enjoy troubleshooting. I figured this would be a great way to learn more about Linux. I've done some research and ran some terminal commands mentioned on similar posts, but still haven't found a resolution. Here is one command, hopefully this helps determine the problem.

Command: sudo lshw -C network

Returns:
*-network UNCLAIMED
product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
yada yada yada
*-network UNCLAIMED
product: NetLink BCM5787M Gigabit Ethernet PCI Express
yada yada yada

Any help appreciated, thanks!

---

### Post by dino99 on 2015-10-02
[http://ubuntuforums.org/showthread.php?t=2280174](http://ubuntuforums.org/showthread.php?t=2280174)
( use 'gedit' instead of 'pico')

---

### Post by Michael_Serck on 2015-10-02
Thanks for the link, but I already tried that and it's still not working.
Added "auto eth0" and "iface eth0 inet dhcp" to the file /etc/network/interfaces (it was not in the file when I first tried it)

---

### Post by cariboo on 2015-10-02
It looks like you shut your system down, while in the middle of doing updates, to solve the problem, open a terminal and type the following command:

```
sudo apt-get install -f
```

to finish the update. You may get a message asking you to run:

```
dpkg --configure -a
```

if you do, run that too.

---

### Post by Michael_Serck on 2015-10-04
sudo apt-get install -f
Returns: 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

sudo apt-get update (or "sudo apt-get update --fix-missing")
Returns:
W: Some index files failed to download. They have been ignored, or old ones used instead.

I assume because no network connections 

sudo dpkg --configure -a
Returns:
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure)
:
 dependencies problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic

---

