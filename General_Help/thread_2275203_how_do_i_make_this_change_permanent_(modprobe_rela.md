---
title: "how do i make this change permanent? (modprobe related)"
date: 2015-04-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-04-24
I'm setting up a Lenovo G50-30 for a friend
i have one issues with the wifi (RTL8723BE), it requires running 3 commands to get it working on 14.04
i am running 15.10 live right now on it and the wifi is crapping out left/right with iperf(linux 3.19)
i got over 100Mbit using 14.04 w/ linux 3.16
*edit: unreliable on 14.04 w/ 3.16

```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```

credit for finding that - [http://ubuntuforums.org/showthread.php?t=2244018](http://ubuntuforums.org/showthread.php?t=2244018)

on a side note about this system is it seems removing the hdd is not enough to access the bios, it requires a working windows 8 install to allow you access to the settings

EDIT:
figured out how to make it perniment
also made a script for anyone dealing with this wifi chip and having a hard time
[http://pastebin.com/LiC7PA1M](http://pastebin.com/LiC7PA1M)

---

