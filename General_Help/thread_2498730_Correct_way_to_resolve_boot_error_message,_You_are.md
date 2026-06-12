---
title: "Correct way to resolve boot error message, You are in emergency mode"
date: 2024-06-25
forum: General Help
---

### Post by cedric9 on 2024-06-25
I have very limited knowledge regarding the Linux operating system, yet I've been able to successfully use Kubuntu for over a decade, with little to no trouble to speak of.


However, the other day my PC gave me the boot error message after it had been switched off over the weekend.  See below.
=====================================================================================================================================
Failure to boot error below:
/dev/sda1: clean, 672792/30006464 files, 7326490/12014350 blocks
You are in emergency mode. After logging in, type "journalctl xb" to view
system logs, "systemctlreboot" to reboot, "systemctl default" or "exit"
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):
Reloading system manager configuration
Starting default target
Failed to start default target: Transaction for graphical.target/start is destructive (emergency.target has 'start' job queued, but stop is included in transaction).
===================================================================================================================================


Eventually I was able to overcome this error by restoring my root partition from an earlier backup image, but I'm wondering if there might have been an earlier way to deal with this problem?  As I said, I'm not that familiar with the inner workings of Linux, but from doing some online research, it appears that others may have been able to solve this problem by booting their computer from a live CD or USB, and then modifying the content of their fstab file.


So, it appears that the above error can be caused if a USB stick is not properly unmounted before the system is shutdown.  Is this correct?  However, this puzzles me, because I don't recall having used a USB stick in my PC lately, but it is possible that someone else around here may have stuck one in there when I wasn't looking. 


Any info greatly appreciated. 


System info below:
Operating System: Kubuntu 22.04
KDE Plasma Version: 5.24.7
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel Version: 5.15.0-112-generic (64-bit)
Graphics Platform: X11
Processors: 4 × Intel® Pentium® Gold G5400 CPU @ 3.70GHz
Memory: 7.7 GiB of RAM
Graphics Processor: NV138

---

### Post by TheFu on 2024-06-28
Look at the system logs.  Look for hardware errors.  HW does fail, after all.
Anytime the OS is NOT shut down cleanly, there is a small risk of a corrupted file causing issues later.  Journaled file systems usually prevent this, unless there's been a problem during a kernel upgrade (this would generally happen when you are patching the system.)

A USB stick isn't the specific issue. Any storage is, but it depends on the specific use of that storage. If it is temporary and doesn't have the OS being used on it, then that really won't harm the next boot.

While the system info is helpful, it doesn't show the important things - that would be all the storage.  What is the storage layout, which file systems are used, are any of the different areas full?  Are you using normal file systems or something exotic?

The error above - did you read it and do what it suggested?  That's an important step too.  I know that people's eyes will gloss over when they see errors like that, but YOU need to READ them, carefully, and do what it suggests.

---

### Post by currentshaft on 2024-06-28
> **cedric9 said:**
> You are in emergency mode. After logging in, type "journalctl xb" to view
system logs, "systemctlreboot" to reboot, "systemctl default" or "exit"
to boot into default mode.

Did you do these steps as the computer instructed?

---

