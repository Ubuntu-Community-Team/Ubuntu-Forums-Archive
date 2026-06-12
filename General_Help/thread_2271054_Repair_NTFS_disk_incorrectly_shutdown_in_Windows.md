---
title: "Repair NTFS disk incorrectly shutdown in Windows"
date: 2015-03-27
forum: General Help
---

### Post by fkervin on 2015-03-27
Hi all,

I've a problem always when I plug any NTFS hard drive in my linux machine and this disk has been connected via dock station in the windows system. In Windows I have no problem at all if later I connect again.

I mean, I have the disk in Windows and unplug the disk of the dock station, if then I connect it in Linux I cant read it and have a message like "**The requested operation has failed: Error mounting /dev/sdb2 at /media/XXXXXXXXXXX**" and "**exited with non-zerp exist status 14: Windows is hibernated, refused to mount.**"

The only way I've found to solve this is connecting the disk again in Windows, and shutting down the computer having the disk connected. How could I make the disk working in linux avoiding this?

Many thanks in advance

---

### Post by dino99 on 2015-03-27
maybe run chkdsk on windows. before unplugging it , do you unmount it first ? (that might be what ubuntu does not like)

---

### Post by yancek on 2015-03-27
> **exist status 14: Windows is hibernated, refused to mount.**"

You need to shut down windows not hibernate which is the default windows 8 behavior, in order to access from Ubuntu.  Lots of posts here with this issue.

---

### Post by ajgreeny on 2015-03-27
> **yancek said:**
> You need to shut down windows not hibernate which is the default windows 8 behavior, in order to access from Ubuntu.  Lots of posts here with this issue.
Or you simply need to remove the disk properly from Windows, ie unmount it; if you don't the disk is left with an "In use" flag on it and will always be impossible to mount and therefore unusable in Linux.  Even though attached through a docking station the disk presumably shows as a separate item in your Win7 panel.

I don't have Windows so do not know how such things are shown as being mounted; in WinXP there was a small icon in the panel at bottom right which allowed safe removal of hardware items.

---

### Post by Mark Phelps on 2015-03-27
If you're running Win8, the problem is that FastStartup is enabled by default there, and when you shut down Win8, it goes into hibernation and keeps all open filesystems still mounted -- preventing them from being mounted again in Linux.  You need to go into Win8 and disable FastStartup (which is not the same as Fast Boot).  Also, when you leave Win8, be sure to use Shut Down, not Restart -- as the latter ignores the FastStartup setting and forces hibernation (again).

---

### Post by fkervin on 2015-03-27
Many thanks for all your answers,

I knew the problem came when the power off of the disk was not correctly made under windows. The question is that I was looking for a way to fix it un Linux, not to having to connect the disk again in the windows system.

I understand from all your answers that there is no program, utility or any other way to "fix" this problem in the disk when is connected in the Linux system. I think it can be a problem if you find this problem and you have any windows computer to connect the disk, something that happens to me sometimes :(

Regards

---

### Post by yancek on 2015-03-27
The problems is because microsoft chose to hibernate rather than shutdown as a default mode.  There really isn't anything Linux developers can do to change the proprietary microsoft windows code to change this.

---

