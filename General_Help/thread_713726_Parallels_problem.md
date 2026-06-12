---
title: "Parallels problem"
date: 2008-03-03
forum: General Help
---

### Post by daniel.b on 2008-03-03
hi everyone, 
im running xubuntu at the moment and i tried installing parallels thru add/remove programs and it installed with no hitch, but when i try and run it i get this error

M```
odule vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config.
```

so i tried running
```
sudo parallels-config
```

and i get this 
```
 Unable to find linux kernel source.
     To configure Parallels Workstation 2.2 you should have
     kernel source package for your Linux system installed.

     Do you want to get more information about the kernel
     source package installation procedure? (Y/N) 
```

so i click on Yes and  i get this
 ```
To install kernel source:

If you use RPM-based system:
     1. Insert distribution CD into CD-ROM drive of your computer.
        Number of the CD for your system see in the table below.
     2. Mount CD-ROM.
     3. Change the current directory to the one which CD-ROM is
        mounted to (usually it is /mnt/cdrom or /media/cdrom).
     4. In the terminal issue the command:
        find . -name <package name> | xargs rpm -i
        Name of the package for your system see in the table below.

     System          CD#     Package Name
     ---------------------------------------------------------------
     Red Hat 9.0     2       kernel-source-2.4.20-8.i386.rpm
     RHEL 4          3       kernel-devel-2.6.9-5.EL.i686.rpm
     SUSE 9.0        3       kernel-source-2.4.21-69.i586.rpm
     SUSE 9.1        3       kernel-source-2.6.4-52.i586.rpm
     SUSE 9.2        5       kernel-source-2.6.8-24.i586.rpm
     SUSE 9.3        5       kernel-source-2.6.11.4-20a.i586.rpm
     Fedora Core 4   4       kernel-devel-2.6.11-1.1369_FC4.i686.rpm
```

so i type this
```
uname -r
```

and i get 
```
2.6.22-14-server
```

on this part im stuck...i dont know what to do and im not that familiar with xubuntu yet and would greatly appreciate a step by step instruction on what to do.

---

