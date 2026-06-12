---
title: "wine problem"
date: 2008-05-29
forum: General Help
---

### Post by bosskaunhai on 2008-05-29
I am new to linux....I installed wine today on ubuntu 8.04 but could not run it... so i opened a terminal and tried to run it but this is what i got:

warren@warren-desktop:~$ sudo apt-get install wine
[sudo] password for warren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
warren@warren-desktop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/warren/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:seh:setup_exception_record stack overflow 840 bytes in thread 0009 eip 7bc65706 esp 7f120fe8 stack 0x7f120000-0x7f121000-0x7f220000
wine: wineprefixcreate failed while creating '/home/warren/.wine'.
warren@warren-desktop:~$ wineserver: could not save registry branch to /home/warren/.wine-4ricGd/system.reg : No such file or directory
wineserver: could not save registry branch to /home/warren/.wine-4ricGd/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/warren/.wine-4ricGd/user.reg : No such file or directory

please, can anybody tell me what i should do?????

---

### Post by Bakon Jarser on 2008-05-29
It looks like it is already installed.  To use it just double click a windows executable file.

---

### Post by mc4man on 2008-05-29
read here and run fix (note there are 2 parts, the fix and making it permanent. I don't think this is an issue with ver. 1.0rc.
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

