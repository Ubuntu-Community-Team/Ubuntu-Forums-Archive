---
title: "Disk drive ran out of space after fresh install - log files taking up all space"
date: 2017-03-12
forum: General Help
---

### Post by faraz_k86 on 2017-03-12
Hi,

I did a fresh install twice on my new system. I am using the ASUS g20CB.

After a fresh install and after about 15 minutes my 20GB partition fills up and I get a warning telling me I have 0 bytes left on disk.

I checked whats taking up all the space and I apparently have 2 log files, over 7GB each - ker.log and syslog.

After a restart the system refuses to load up and I keep getting a stream of error messages as in the screenshot below: (I think the log files were also filled up with the same errors. 

[ATTACH=CONFIG]274102[/ATTACH]

Some help would be appreciated.

Thank you

---

### Post by oldfred on 2017-03-12
Issues are often common by brand.
You probably need the same boot parameter - pci=nomsi.

 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570) 


 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by ian-weisser on 2017-03-12
See [http://askubuntu.com/questions/771899/pcie-bus-error-severity-corrected](http://askubuntu.com/questions/771899/pcie-bus-error-severity-corrected) for another possible solution.

---

