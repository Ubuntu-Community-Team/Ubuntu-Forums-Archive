---
title: "ubuntu unresponsive and programs greyed out"
date: 2007-12-17
forum: General Help
---

### Post by kavoura on 2007-12-17
Suddenly my Ubuntu has gone unresponsive. (typing this on another PC). The menus at the top of the screen will not respond when I click. The programs I have open, Thunderbird and Firefox, have gone grey and will not respond to any clicks. I can drag the windows around, and minimise them, but that is all. It started after I logged into my Virgin Mobile account online in Firefox, then it went grey, then I tried to access Thunderbird and it went grey too. And the Ubuntu menus will not respond, nor any icons at the top right of the screen.
Now the Update Manager has started and seems to be stuck on "Building dependency tree". I guess I must have clicked on the icon for it at the top right of the screen, but it did not respond straight away. Now it is doing something I do not want it to do and everything is just going super slow...
A short while later, as I am typing the above, the programs are no longer grey and Update Manager is diong something.
But why did Ubuntu throw a fit after visiting a website? Or is there something else going on that could causing this? Up till now Ubuntu has worked fine, but this sudden problem is worrying.
I do know that some hard disks had bad sectors, which I fixed. Also at startup, before login screen, Ubuntu says it wants to scan some hard disk partitions for errors but cannot, and that I have to do it manually. Then I press Control D to continue booting.
I do not know yet how to check the disks manually from Ubuntu.
But so far I have not had any problems with them in Ubuntu.
When I get the time I shall install a new hard disk and copy stuff to that, which should help.

---

### Post by FuturePilot on 2007-12-17
I would think it's unrelated to the website you visited. If it happens again try running 
```
top
``` in a terminal and it might give you a clue as to what process may be causing it.
To fsck the drive manually I would boot from the live CD and run in a terminal
```
sudo fsck /dev/sdaX
```
Where X is the partition number. Usually hard drives are sda but yours could be different. To find out which one it is run
```
sudo fdisk -l
```
The drive should **not** be mounted while running fsck.

---

