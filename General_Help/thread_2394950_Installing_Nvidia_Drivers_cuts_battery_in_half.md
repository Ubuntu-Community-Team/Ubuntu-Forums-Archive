---
title: "Installing Nvidia Drivers cuts battery in half"
date: 2018-06-24
forum: General Help
---

### Post by creativiii on 2018-06-24
I'm fairly new to Linux and Ubuntu, but I'm not entirely tech illiterate, however this problem has really stumped me and I really do not know how to figure it out.

I spent the past few days setting up Ubuntu and every single time my battery would die right after installing ```
nvidia-390
``` drivers. I'm aware of the fact that after installing the drivers my laptop defaults to the Nvidia card, explaining the loss of battery life, however even after running ```
sudo prime-select intel
sudo prime-select query
```
And doing a reboot to make sure I was on my intergrated graphics, the battery life would still be hours shorter than it was before installing the drivers.

It doesn't just end here however. I cannot find a way to fix this problem, meaning that even if I uninstall the Nvidia drivers the battery will still have the same problems. So far the only solution I've found is to reinstall Ubuntu all over again. 

I exported my Powertop readings before and after installing the drivers and it's pretty clear something is wrong.
Here's before installing the drivers: [http://awesome-snyder-983ae4.bitballoon.com/](http://awesome-snyder-983ae4.bitballoon.com/)
And here's after installing them: [http://vibrant-bell-a0e02f.bitballoon.com/](http://vibrant-bell-a0e02f.bitballoon.com/)

Despite the backlight being at the same exact level in both cases, the second reading reports it to be several times more power consuming than before.

After the problem I tried installing TLP, which didn't help at all. I blacklisted both the NVidia and Nouveau driver AND the hardware associated with the GPU but the power consumption was unchanged.

Knowing this I tried to install Bumblebee from the wiki page ([https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)), but the program doesn't seem to work. 
I'm receiving the same error as many other people ([https://github.com/Bumblebee-Project/Bumblebee/issues/933](https://github.com/Bumblebee-Project/Bumblebee/issues/933)) are receiving, and even reported fixes to it like this one ([https://github.com/Bumblebee-Project/Bumblebee/issues/867#issuecomment-302827439](https://github.com/Bumblebee-Project/Bumblebee/issues/867#issuecomment-302827439)) don't seem to work.

I'm not sure if this is related to the problem, but I can't seem to install VirtualGL from the terminal since I receive this error:
```
Package virtualgl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'virtualgl' has no installation candidate

```


I would be extremely grateful if I could get any help in deciphering what is going on with my system. Please let me know if you need any more info.
I'm currently on the latest Ubuntu version (18.04) and have tried this with 3 different kernels:

-v4.13.10
-v4.16.17
-Whatever was installed when I made the fresh installation.

---

### Post by creativiii on 2018-06-25
After posting about this problem everywhere it turns out it's actually a bug with the drivers themselves.
Despite not being able to find the solution on my own I was linked this fix [https://github.com/stockmind/dell-xps-9560-ubuntu-respin/issues/8#issuecomment-389292575](https://github.com/stockmind/dell-xps-9560-ubuntu-respin/issues/8#issuecomment-389292575)

Power consumption is back down to what it was before!

---

### Post by ubname on 2018-06-25
There is an official Ubuntu fix in progress:

[URL="https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1778011"]https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1778011
[/URL]
i'm using the ppa suggested by the developer and it seems to work, not shure how to check for power consumption
you could try this solution ...

---

