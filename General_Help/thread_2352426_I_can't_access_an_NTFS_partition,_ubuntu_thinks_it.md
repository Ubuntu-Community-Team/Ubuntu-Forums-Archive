---
title: "I can't access an NTFS partition, ubuntu thinks it's hibernating..."
date: 2017-02-12
forum: General Help
---

### Post by javierdl on 2017-02-12
... But it's really not.
I have been sure to have both Fast Startup and Hibernation off (unchecked) in Windows 10.
Yet when I come to Ubuntu there's this NTFS partition that won't give me access saying (in a pop up):
 ```
*Unable to access “315 GB Volume” - Error mounting /dev/sda2 at /media/javier/766862CE68628D25: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda2" "/media/javier/766862CE68628D25"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.**Failed to mount '/dev/sda2': Operation not permitted*
*The NTFS partition is in an unsafe state. Please resume and shutdown*
*Windows fully (no hibernation or fast restarting), or mount the volume*
*read-only with the 'ro' mount option.*



```

Then I tried this:

```

ntfsfix dev/sda2
Failed to determine whether dev/sda2 is mounted: No such file or directory
Mounting volume... Failed to access 'dev/sda2': No such file or directory
Error opening 'dev/sda2': No such file or directory
FAILED
Attempting to correct errors... Failed to access 'dev/sda2': No such file or directory
Error opening 'dev/sda2': No such file or directory
FAILED
Failed to startup volume: No such file or directory
Failed to access 'dev/sda2': No such file or directory
Error opening 'dev/sda2': No such file or directory
Volume is corrupt. You should run chkdsk.


```

In the mean time I will go back to Windows and try to use chkdsk to check that partition.

What do you guys think?

Thanks

---

### Post by SeijiSensei on 2017-02-12
First, you would need to use "ntfsfix **/**dev/sda2 with the leading slash.  However ntfsfix has very limited abilities to correct an NTFS filesystem.  You need to use chkdsk.  From "man ntfsfix":
> ntfsfix is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS  consistency check for the first boot into Windows.

---

### Post by TheFu on 2017-02-12
If the partition isn't a "simple partition" in Windows, that can cause issues for Linux too. [https://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx)

I always use the file system tools from the OS that created that file system. Trying to use Linux tools to fix Windows file systems is risking corruption. Microsoft has modified the partitioning and NTFS for years. Did all those changes get included in the tools made by Linux developers?

And a clear understanding of relative paths and absolute paths is needed too.  Disk devices are located in the /dev/ directory, so if you are in / already, using /dev/..... is required.

---

### Post by oldfred on 2017-02-12
NTFSfix turns on the chkdsk flag. And the Linux NTFS driver will not mount NTFS with the chkdsk flag on in read/write mode.

So running NTFSfix locks out Linux until you boot Windows and run chkdsk on the NTFS partition(s).

---

### Post by javierdl on 2017-02-12
Man! 
You all guys "always" exceed my expectations! :)

Thank you for you help :)

JDL

---

### Post by javierdl on 2017-02-13
Well, chkdsk did not find anything wrong :(
And there are no BIOS updates available for me :(

Should I try formating the partition?

JDL

---

### Post by javierdl on 2017-02-15
I guess I'll have to format the partition, because I ran ntfsfix and gave me this:

```

sudo ntfsfix /dev/sda2
[sudo] password for javier: 
Mounting volume... Windows is hibernated, refused to mount.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
[COLOR=#a52a2a]**Windows is hibernated, refused to mount.**[/COLOR]
Remount failed: Operation not permitted




```

---

### Post by oldfred on 2017-02-15
You said you have hibernation off.
But ntfsfix is saying it is on.
> Mounting volume... Windows is hibernated, refused to mount.

Windows on updates may turn fast start back on. So you have to regularly check.
If you have auto update on in Windows it may just update & turn it on again.
Fast Start up off (always on hibernation)[URL="http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472"]
http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472[/URL][URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html[/URL][URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html[/URL]

---

### Post by javierdl on 2017-02-15
I see. I'll check now again.
One odd thing I have noticed (in Win10) though, the Time is never correct. I fix it every time. But if I have to reboot, it shows the wrong time again when booted up.
If it normally relies on writing information to some kind of log file to keep this consistent, then wouldn't this suggest that it is having a hard time doing it? If so, could this be related to the problem I have with the hibernation?

---

### Post by oldfred on 2017-02-15
Do not know if specifically Windows or Ubuntu, some links.
hardware clock, Windows clock, Ubuntu clock times
[URL="https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts"]
https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts[/URL]
time, UEFI, windows 8  - several posts by sudodus  
[URL="http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648"]http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648
[/URL]
 [http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows](http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows)
Clock and some boot settings like fsck, login,   tmp retain time.
/etc/default/rcS
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no 
sudo hwclock --localtime --adjust 

[URL="http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648"]
[/URL]

---

### Post by javierdl on 2017-02-17
I ended up just formating that partition to ext4. And installing a driver that allows Windows 10 to read & write on that same partition.

---

### Post by Mark Phelps on 2017-02-17
I can confirm that Win10 Updates routinely re-enable FastStartup -- as I have to KEEP turning mine off after each of the Update cycles in order to prevent Hibernation.

---

