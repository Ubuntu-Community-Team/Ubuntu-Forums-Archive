---
title: "Can't Mount NTFS Partitions after Installing Win 8.1 Preview"
date: 2013-08-18
forum: General Help
---

### Post by vibin-mdcp on 2013-08-18
Recently, I could install Windows 8.1 Preview version from microsoft on computer. And I used Boot-Repair to boot loader of Ubuntu. After that I could use Windows and Ubuntu 13.04 without any troubles. But, when I tried to access my NTFS partitions some error message is received. The error message is,

[ATTACH=CONFIG]245465[/ATTACH]
How can I solve this error...?

Please help me as my project files are on NTFS partitions. And for the last one week, I can't do anything for my project.

---

### Post by carl4926 on 2013-08-18
Windows is not shut down properly
Windows 8 does not shut down as you expect. You need to boot windows and change the settings to make it shutdown properly.
I suggest you google this, there have been thousands of people caught by this stupid windows setting, hidden in some deep dark corner...

---

### Post by Mark Phelps on 2013-08-19
You can't access Windows filesystems from Ubuntu because of two problems:
1) When you log out or shut down Win8, it actually goes into hibernation
2) The Win8 hibernation is different from previous Windows versions as it keeps the drives mounted,

So basically, even though you're not running Win8 at the time, its partitions are still mounted -- thus, you can't get access to them.

The Win8 feature is Fast Startup, which can be disabled -- but if you do that, Win8 will take a LOT longer to restart.

For Win8 features, suggest you check a Win8 forum -- eightforums.com.

---

### Post by vibin-mdcp on 2013-08-19
Can I unmount partitions from windows...

---

### Post by oldfred on 2013-08-19
As mentioned above it is the fast startup setting.

 
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

