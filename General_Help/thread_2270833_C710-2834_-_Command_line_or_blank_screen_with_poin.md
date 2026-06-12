---
title: "C710-2834 - Command line or blank screen with pointer?"
date: 2015-03-25
forum: General Help
---

### Post by draky87120 on 2015-03-25
I'm finally able to sucessfully install Ubuntu on my Acer C710-2834 chromebook via Chrubuntu (found here: [http://chromeos-cr48.blogspot.com/2012/04/chrubuntu-1204-now-with-double-bits.html](http://chromeos-cr48.blogspot.com/2012/04/chrubuntu-1204-now-with-double-bits.html) ). Now it installs and then when it reboots I get a blank screen with a pointer on it, login screen doesn't show up. If I hit the Ctrl+alt+Fx (1-6)  I can switch between the tty1-6 screens and log in and run command line things. But when I hit ctrl+alt+F7 button I only have the blank screen with the pointer.

When I attempt to "startx" I get:
> Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.
.....
XIO: fatal IO error11 (Resource temporarily unavailable) on X server ":0" after 7 requests (7 known processed) with 0 events remaining.

I get that every time, even after I reboot and every time I re-install Chrubuntu.
What I'm looking for is the Ubuntu UI. I was thinking maybe delete and re-install it (I just don't know enough about Ubuntu to do that on the command line)?

Thanks in advance for any assistance.

---

### Post by draky87120 on 2015-03-26
Does anyone have any idea how to get to the normal UI? I was wondering if from the command line I can delete and re-install the UI, perhaps that will work?

Trying a few thins here, I attempted to re-install and got the following error:
> ....
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ubuntu-desktop amd64 1.267 cound not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.267_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.267_amd64.deb) count not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
I then try it again with the --fix-missing and get
> ....
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Anyone have any ideas? I would love to pull the log but I'm not familiar with that process. I have a feeling that it's failing because it's not able to use or is failing with my graphics chipset. I have the 1.5gig 1007u chipset so I'm thinking that's the problem. I probably just need to install a driver but I don't know how to do it or where to find it.

I was just thinking, could be that it's not finding the url's because it isn't connected to wifi? It does have a RJ45 port, will it connect if I plug it in directly to my router?

Help please...

---

