---
title: "Ubuntu 20.04: Issues with dpkg and grub-efi-amd64-signed"
date: 2020-06-22
forum: General Help
---

### Post by tuddungoggo on 2020-06-22
Greetings, I am getting the following error below:

```
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 10
```

Here is more of a summarization:

```
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
Setting up grub-efi-amd64-signed (1.142.1+2.04-1ubuntu26) ...
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 grub-efi-amd64-signed

```
I am not sure on what to do to fix this problem.

---

### Post by tuddungoggo on 2020-06-25
Any updates? It doesn't seem that anyone here can assist me with my problem.

---

### Post by Bashing-om on 2020-06-25
tuddungoggo; Well - Hello :)

All we can do at this point is poke at the situation and see what we can find out for the reason the system is unable to configure "grub-efi-amd64-signed" .

To that end. Does the target partition exist ?
```

sudo parted -l

```

Is the system booting in EFI mode:
```

[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"

```

Make sure the system is updated:
```

sudo apt update

```

Now what results:
```

sudo apt upgrade

```

[INDENT][INDENT]starts the ball rolling
[/INDENT][/INDENT]

---

### Post by tuddungoggo on 2020-06-27
Hello Bashing-on, thanks for responding to my query. Here is what I get from based off of your instructions.

Partition:
```

lamidotijjo ~ $ sudo parted -l
[sudo] password for lamidotijjo: 
Model: PC SN730 NVMe WDC 1024GB (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  829MB   828MB   fat32        EFI system partition  boot, esp
 2      829MB   6198MB  5369MB  fat32        Basic data partition  msftres
 3      6198MB  1024GB  1018GB  ext4



```

It seems to exist.

The system is booting in EFI mode.

```

lamidotijjo ~ $ sudo apt update
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                                                    
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]                                    
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]                                   
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu focal InRelease                                  
Hit:6 http://archive.canonical.com/ubuntu focal InRelease                                                    
Get:7 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]             
Get:8 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [21.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [105 kB]
Get:10 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [31.6 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [152 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [532 B]
Fetched 622 kB in 1s (578 kB/s)     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

```

lamidotijjo ~ $ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up grub-efi-amd64-signed (1.142.1+2.04-1ubuntu26) ...
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

