---
title: "how to access NTFS partition used by Windows 8?"
date: 2015-04-20
forum: General Help
---

### Post by raymondvillain on 2015-04-20
Dual boot machine, Windows 8.1, Ubuntu 14.04.  Used to be able to access the windows NTFS partition from within Ubuntu, now cannot do so.  

error message:

Error mounting /dev/sdc2 at /media/daddy/E4ECAAB6ECAA8282: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdc2" "/media/daddy/E4ECAAB6ECAA8282"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sdc2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Did Windows change something in the shutdown protocol?  I can still boot to windows without any problems.

Doesn't make sense.  Why would it work one day and not the next?

---

### Post by Holger_Gehrke on 2015-04-20
You either didn't shut down Windows 8(.1) - that's what the error message says - but only sent it into hibernation or you set it to use fastboot - which is a lot like hibernation (it hybernates session 0 - the Windows kernel; in that state it stores information about the state of the disk in the hibernation file and doesn't re-read the disk on boot - so any changes you make while Windows is not running would either get lost as soon as Windows is restarted or worse you'd get some serious data corruption since block allocations wouldn't match anymore what windows thinks they are).
You have two options:
1) Change the settings of Windows not to use fastboot. Search the net on how to do this, I don't know.
2) Boot into Windows, tell Windows to do a full reboot and then boot into Linux. When told to reboot, Windows always does a full shutdown on the assumption that for the user to ask for a reboot something must be wrong with the current state of the system.

---

### Post by Mark Phelps on 2015-04-20
>  Change the settings of Windows not to use fastboot.Wrong!

It's not Fast Boot; it's Fast Startup.  The first is a BIOS/UEFI boot option;the second is the hibernation option.

Disable FastStartup in Win8.  But then, when you go to change OSs, be sure to select Shut Down, not Restart.  Why? Because Restart ingores the FastStartup option you disabled and automatically puts Win8 into hibernation -- including ALL the partitions that were open when Win8 was running.

Also, do NOT mount the Win8 OS partition as read/write in Ubuntu.  Doing so can easily cause filesystem corruption, rendering Win8 unbootable and, as a result, very hard to fix.

---

### Post by Holger_Gehrke on 2015-04-20
Thank you for correcting me, I was relying on memory ... which obviously failed me on the details.

---

