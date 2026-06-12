---
title: "How to display various system information?"
date: 2008-03-11
forum: General Help
---

### Post by rphil2008 on 2008-03-11
How do you display various system information about the computer where Ubuntu is running, in particular:

1. Cpu information
2. Physical memory 
3. Video memory

I have already figured out how to display cpu information from the command line using cat /proc/cpuinfo. Please assume pc has no internet connection to download graphical system information software. Thanks.

---

### Post by freddyp on 2008-03-11
Can't remember if Sysinfo is installed by default in 7.10....but that's what I use.  Check under System>Administration and see if there is a Sysinfo selection.  If not, you can install through Applications>Add/Remove.  I find it works pretty well for this type of info.  Hope this helps!

---

### Post by soldats on 2008-03-11
```
free
```
displays memory -- not sure if it shows video mem though
i know there is a command but i cant remember it

---

### Post by x1a4 on 2008-03-11
**top** will tell you current system load (mem, swap, buffers, cpu, who executed what)

Also: 
cat /proc/meminfo for memory usage
cat /proc/uptime how long the computer is running
cat /proc/modules loaded kernel modules
cat /proc/partitions partition info
cat /proc/swaps swap partition info
cat /proc/iomem memory I/O
cat /proc/ioports I/O ports addresses

etc. (just look in /proc/)

**uname** will give you some info like kernel info, hardware name and platform, processor type, host name
**/sbin/ifconfig** network interface info
**/sbin/discover** hardware detection utility
**/sbin/vol_id** probe a filesystem
**/sbin/vmstat** virtual memory statistics
**/sbin/acpi_available** is the acpi subsystem available

When you do have an internet connection Install the **hardinfo** package.

---

### Post by rphil2008 on 2008-03-11
Thanks for all the information. I am testing them all now. Quite a lot of it too.

- no sysinfo by default though
-hardinfo is very nice graphical information center. I will install it once that computer has internet connection.

Thanks fellows. I appreciate it!

---

