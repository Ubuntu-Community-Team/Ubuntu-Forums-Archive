---
title: "How to point grub to usable efi vmlinuz files?"
date: 2013-05-22
forum: General Help
---

### Post by Geezanansa on 2013-05-22
Hi all,

Have recently taken an interest in EFI boot feature on newer systems.  

Using an Ubuntu 12.10 amd64 Desktop dvd on an EFI capable machine have Grub boot options screen running in EFI mode.  Selecting "Try Ubuntu without installing" or "Install Ubuntu" gives "can not read cd/0" and "the kernel needs to be loaded first" errors.
 Trying latest release of other distros gives similar results. Trying booting newer and older flavours of Ubuntu gives similar results when booting EFI mode and trying any of the options available to boot to.
Dropping to grub command line and trying ```
search -f /vmlinuz
``` or ```
search -f /sbin/init 
``` only confirms missing EFI files.  
**Update:** Can not repeat the results using those commands but do get similar output from using ```
ls -l
``` from grub prompt which gives 
[IMG]http://i.imgur.com/FoHVFeo.jpg?1[/IMG]

How to point grub to usable EFI files in order to boot "Try Ubuntu without installing"?

---

### Post by Geezanansa on 2013-06-06
This question was reasked/moved to [http://ubuntuforums.org/showthread.php?t=2149013](http://ubuntuforums.org/showthread.php?t=2149013)

---

