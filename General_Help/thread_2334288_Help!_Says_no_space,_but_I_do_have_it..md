---
title: "Help! Says no space, but I do have it."
date: 2016-08-18
forum: General Help
---

### Post by zuto2 on 2016-08-18
I tried the Ubuntu Ubuntu Customization Kit and an error occurred. I deleted 4 gb in my home folder before logging out. I tried recovery and old kernels. No space even after removing more free space with recovery. Still says I have no space. I will be grabbing my files from Ubuntu in Windows and will check back. I will then reinstall with my 20 gb back up if there are no solutions when I check back here.

**Edit:**
[COLOR=#000000]I cannot login to Ubuntu due to this no space thing.
[/COLOR]
[B]Solved:
[/B][COLOR=#000000][COLOR=#000000]My whole Ubuntu Precise OS is restored because of my backup. I am never using [/COLOR][/COLOR][COLOR=#000000]Ubuntu Customization Kit again. The kit literally says an error has occurred. An error that kills your OS apparently. At least on Ubuntu Precise.[/COLOR]

---

### Post by mastablasta on 2016-08-18
post output of 

```
df -h
```

---

### Post by pqwoerituytrueiwoq on 2016-08-18
is your root partition separate?
in my exp i have had to reboot to get the system to see that there is now disk space available after running out

---

### Post by zuto2 on 2016-08-18
I forgot to add that I cannot login to ubuntu due to this no space thing.

---

### Post by mastablasta on 2016-08-18
> **zuto2 said:**
> I forgot to add that I cannot login to ubuntu due to this no space thing.

boot from live USB/DVD and post the output of the command. the command will say how much is occupied in readable form as well as reveal partitions. if you find it easier you can use boot-repair tool and create a report using the bootinfoscript found there. 

as it is now, we do not know the exact situation on your hard disk other than you get low or no disk space report and that you can't boot.

---

### Post by zuto2 on 2016-08-18
I am just going to reinstall. It will be faster. It is a good thing that I make back ups that can be restored in 20 min.  The Ubuntu Customization Kit in the ubuntu store on 12.04 precise is more of a virus. It should be removed.

---

### Post by ajgreeny on 2016-08-18
The most usual cause of the problem you have reported is a separate /boot partition which is created automatically if you choose to use LVM partitions or encryption when installing the OS.

Unfortunately that boot partition is too small and if you do not remove kernels as new ones are installed in updates the boot partition fills up very quickly.  It does not usually stop users logging in but means no further updates are installable, and usually no packages can be installed either as the whole package management system is brought to a grinding halt.

If you do not really need to use LVM or encryption I suggest you install without them as it will remove the possibility of this problem recurring.

---

### Post by grahammechanical on 2016-08-18
I have never used Ubuntu Customization Kit. I do not know how it works but I guess that it has to store on the drive all the packages selected by the user to be in the new ISO image and then store the ISO image itself. It needs space to work. In fact a recommended 3 - 5 GB of free space. I think that is an under estimate because an ISO image built on the 12.04 (and later) ISO image would be well over 1 GB in size.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

The ISO image is an archive. It has to be unpacked. Need more space.

---

### Post by zuto2 on 2016-08-20
You guys are not getting the issue that I had. I had over 200 GB of free space when using [COLOR=#000000]Ubuntu Customization Kit on my Ubuntu Precise. After using the kit it made my space go to zero. I literally tested it again on oracle virtualbox and the problem is the [/COLOR][COLOR=#000000]Ubuntu Customization Kit. As usual Ubuntu can not boot up unless you have free space.[/COLOR]

[COLOR=#000000]My whole Ubuntu Precise OS is restored because of my backup. I am never using [/COLOR][COLOR=#000000]Ubuntu Customization Kit again. The kit literally says an error has occurred. An error that kills your OS apparently.[/COLOR]

---

