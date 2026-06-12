---
title: "Mounting and External Hard Drives"
date: 2007-04-24
forum: General Help
---

### Post by StargateGamingGeek on 2007-04-24
Hello All,

This is my first post on the Ubuntu forums, my third distro specific forum to post on. I have some questions regarding issues I have had with hard disk auto-mounting in Feisty.
Firstly: My external hard-drive has four partitions, all FAT, being mounted automatically. Occasionally, but not always, when GNOME loads after I log in one or more of them will be listed multiple times. This isn't really problematic just annoying and I was wondering how to correct this. It also does the same thing with CD's on occasion as well.
Secondly: When I try and eject the hard drive from above, using the right-click->Eject method, and it simply pops up numerous windows telling me it's can't eject it. The error message shows up for the partition I try to eject saying 'cannot eject volume' and a single window for each partition opens on the desktop. A tool-tip on the lower right claims there is data yet to be written to the device but I am trying this as I type and nothing has been accessed from or written to the disc since I restarted.

Any help on solving either, preferably both, of these problems is greatly appreciated.

---

### Post by will_in_wi on 2007-04-24
The problem with multiple disks I saw a long ago and have since fixed it but I don't remember how.

You can find out why it will not unmount the disks by using a program called fuser. If you type:
```

fuser -m /media/mountpoint

```
then it will tell you the process ids of the processes using the filesystem. Then you can open System Monitor and find the process id and close the app that is using it.

---

