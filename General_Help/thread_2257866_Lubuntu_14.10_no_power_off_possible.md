---
title: "Lubuntu 14.10 no power off possible"
date: 2014-12-23
forum: General Help
---

### Post by DrScum on 2014-12-23
using
hardware: Siemens/Nixdorf AmiloPro, Celeron Processor
software: Lubuntu 14.10, Kernel: 3.16.0-28-generic, Gnome 3.12.2

the system hangs on shutdown. I have already posted in Ask ubuntu, and filed a bug report.

I hope I don't violate any double posting or other Forum rules. However, this seems to be a problem around for quiet a while now and no fix or even a workaround has emerged. So I basically want to point to the problem and provide all the information I have gathered:
Here are two bug reports from quiete a while ago dealing with this problem
[https://bugs.launchpad.net/ubuntu/pr...ih/+bug/740390](https://bugs.launchpad.net/ubuntu/pr...ih/+bug/740390)
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1024868](https://bugs.launchpad.net/ubuntu/+s...r/+bug/1024868)
The bug reports are linked to modemmanager and network manager. Thus I purged the modem manager leaving the nm_dispatcher.action terminating with a signal 15. The last message the system gives me is "will now halt" and that's it, no power off

What I tried so far:
modifying grub with adding acpi=force to GRUB_CMDLINE_LINUX
shutting down the networkmanager manually with sudo stop network-manager before issuing the shutdown command
I also tried the various commands: shutdown -h now, halt-p being suggested in the posts relating to this problem

As I already said, I am stuck here and don't know what to do at the moment since I am trying to revive a pool of old Amilo Pro laptops at our school. Other than the no shutdown problem Lubuntu would be the perfect solution.

---

### Post by schragge on 2014-12-23
Have you tried to flash new BIOS firmware? The latest on Fujitsu support site seems to be version B0G from 27.04.2007. The README contains following two bits that may be of interest here:
> 
**BIOS B0E:** System hung up if reboot after resuming from S3.
**BIOS A0V:** To fix sometimes system will hang up during POST when rebooting.
 

Also, watch the output of
```

dmesg -r | grep '^<[0-4]>'

```
for any ACPI-related warnings/errors/exceptions. These are kernel messages during boot, and maybe googling them will bring you a bit further.

---

### Post by DrScum on 2014-12-23
Bios is B0G, will try the dmesg option, thanks for your help

---

### Post by DrScum on 2014-12-23
A minute ago I had the funny idea to test Lubuntu 14.04. Starting the system up with a 14.04 DVD, using it as a life CD, shutdown works normally. As a control I did the same with the 14.10 DVD and sure enough, the shutdown hangs after being asked to remove the media. Thus I conclude that the error was introduced with 14.10. That's as far as I am going to take it, as I am writing this (on another computer of course) Lubuntu 14.04 installs on the Amilo Pro system.

---

### Post by raptir on 2014-12-23
This sounds similar to the issue I have been having.

[http://ubuntuforums.org/showthread.php?t=2255354](http://ubuntuforums.org/showthread.php?t=2255354)

Oddly enough, when I tested Lubuntu from a live disc I did **not** have this problem, I only ran into it with Ubuntu and Xubuntu.

---

