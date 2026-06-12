---
title: "How to Cleanup Kernels that are not listed by dpkg"
date: 2014-11-15
forum: General Help
---

### Post by 7-webmaster on 2014-11-15
I have been running Linux on this computer for many years and in particular I have a bunch of 3.2 kernels left over from 12.4.  These kernels are not listed by dpkg --list, so I cannot remove them using apt-get.  However because they are there they are added to the grub menu whenever that is built.  Is it safe to just remove all of these files from /boot?

---

### Post by grahammechanical on 2014-11-15
Ubuntu 12.04 should have Synaptic Package Manager installed whereas 14.04 does not have it installed by default. I would search for Linux kernels in Synaptic and use that to remove previous kernels leaving two working kernels. At the end of the operation Synaptic will run Grub os-prober and that should re-configure the Grub Boot menu.

Regards.

---

### Post by kc1di on 2014-11-15
Also you can install ubuntu-tweak it has a very good janitor which will remove old kernels

---

### Post by pfeiffep on 2014-11-15
I generally use nautilus launched with elevated privilege:
```
gksudo nautilus
``` My /boot directory looks like this after deleting all but the 2 most recent kernels and associated files.

---

### Post by ajgreeny on 2014-11-15
> **pfeiffep said:**
> I generally use nautilus launched with elevated privilege:
```
gksudo nautilus
``` My /boot directory looks like this after deleting all but the 2 most recent kernels and associated files.
It is not good practice to remove kernels simply by deleting them from the /boot folder as I assume you are doing.  It can leave you with a very unclean system, and might even give you big booting problems eventually as a result of grub not knowing what is installed any more.

You really should remove kernels either with a package manager or command```
sudo apt-get remove linux-image-3.13.0-27 linux-image-3.13.0-27
```and repeat the final part (linux-image-<version>) for each kernel to be removed with a space between.

---

### Post by deadflowr on 2014-11-15
Are those 12.04/3.2 kernel listings in grub actually showing by default or are they in the Advanced Options Listing? ( where the old kernels would be)
If they are showing below the Advanced Options line, then they most likely are not from the current OS, but another one entirely.
Where as grub in 12.04 would list all the kernels starting with the newest kernel, new grub(14.04) starts with newest kernel, then Advanced Options, then Memtest, then the kernels from any other system on the machine and then any other operating system--see Windows.

Of course this is all an assumption so perhaps running
```
sudo update-grub
```
Will help clarify things...
Post the output...

---

### Post by 7-webmaster on 2014-11-15
> **grahammechanical said:**
> Ubuntu 12.04 should have Synaptic Package Manager installed whereas 14.04 does not have it installed by default. I would search for Linux kernels in Synaptic and use that to remove previous kernels leaving two working kernels. At the end of the operation Synaptic will run Grub os-prober and that should re-configure the Grub Boot menu.

Regards.

Synaptic is just a different GUI front end to apt.  If the packages are not in apt then Synaptic should be no more able to find them than dpkg.

> **kc1di said:**
> Also you can install ubuntu-tweak it has a very good janitor which will remove old kernels

I did that first.  ubuntu-tweak found only 4 kernels that it could delete.  I then manually deleted all of the old kernels that were found by dpkg --list, which ubuntu-tweak had not found relevant for some reason.  All that ubuntu-tweak is doing is issuing the apt-get purge command for the kernel packages that it has identified.

> **ajgreeny said:**
> 
You really should remove kernels either with a package manager or command```
sudo apt-get remove linux-image-3.13.0-27 linux-image-3.13.0-27
```and repeat the final part (linux-image-<version>) for each kernel to be removed with a space between.

This does not work because these packages are not in the APT database.  For example if I try:

sudo apt-get remove linux-image-3.2.0-23 linux-image-3.2.0-23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0-23
E: Couldn't find any package by regex 'linux-image-3.2.0-23'
E: Unable to locate package linux-image-3.2.0-23
E: Couldn't find any package by regex 'linux-image-3.2.0-23'

So I am still at the original question:  How do I safely remove a linux image, so that all of the associated files are removed, so that when the grub menu is rebuilt it will not include all of these useless ancient images?

> **deadflowr said:**
> 

Of course this is all an assumption so perhaps running
```
sudo update-grub
```
Will help clarify things...
Post the output...

These 13 pointless images all appear in the "Advanced" sublisting.  Running sudo update-grub looks for every image file it can see, so as long as those useless images are physically present, the GRUB menu will include 2 lines for every one of them, no matter how many times I run update-grub.

---

### Post by pfeiffep on 2014-11-15
> **ajgreeny said:**
> It is not good practice to remove kernels simply by deleting them from the /boot folder as I assume you are doing.  It can leave you with a very unclean system, and might even give you big booting problems eventually as a result of grub not knowing what is installed any more.

You really should remove kernels either with a package manager or command```
sudo apt-get remove linux-image-3.13.0-27 linux-image-3.13.0-27
```and repeat the final part (linux-image-<version>) for each kernel to be removed with a space between.OP had many kernels that might have proven difficult to match with command line options.

In 2 years I've NEVER had a problem with unclean system or boot problems (Knock Wood). 
I really don't understand the difference using a gui or command line to delete unwanted files since Linux doesn't use a registry as Windows does I really don't think my method is faulty.

---

### Post by deadflowr on 2014-11-16
Mulling it over some, I wonder if it's the result of a corrupted/busted status file.
Perhaps try 
```
locate linux-image-3.2
```
Post any output.

---

### Post by ajgreeny on 2014-11-16
Can you also show us the output of ls /boot/ | grep vmlinuz, which I believe should show **all  **kernels on the system.

  I think you should then be able to use ```
sudo dpkg -P linux-image-#.#.#-#*
```changing the #.#.#-#* to the kernel version but leaving the wildcard * at the end.  My previous suggestion of using ```
sudo apt-get remove linux-image-3.2.0-23 linux-image-3.2.0-23
```but changing the version numbers, of course to your situation may also be because you have the generic versions installed, which I missed from the command.  The ls command above will tell you the specific version kernels you have, but it will probably be generic.

However, I seem to remember old, non-available kernels that I had installed in a version of Ubuntu could still be removed with synaptic even though it was impossible to install them if I wanted as they show in synaptic even if not in the repos any more, in exactly the same way as any third party .deb packages I had installed also show in synaptic when installed and can be removed using it.

I believe that synaptic will show all packages installed if they were installed by a package manager, dpkg, gdebi, etc etc, but not any installed from source unless you've used checkinstall.

---

### Post by oldfred on 2014-11-17
If you do an upgrade or a "dirty" install where you do not reformat partition, all the old files including kernels & related files will still be in /boot and probably in /usr/src but not in dpkg as current system did not install them.

This will only show those still in dpkg.
 dpkg -S /usr/src/*

 
ls -l /usr/src
cd /boot
ls -l /boot

Always best to use dpkg, apt-get or synaptic if registered as part of install.

If you just use nautilus to delete using gksudo, then you may have just moved them into root's trash. And sometimes housecleaning root's trash can be an issue.

  How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

And then you may have lots of very old log files and other left over bits.
 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by ajgreeny on 2014-11-18
OK, thanks oldfred; I have never upgraded so was not aware that old kernels did not show in any package manager, nor can they be removed with dpkg.

It seems yet another good reason to clean install.

---

### Post by oldfred on 2014-11-18
@ajgreeny
> It seems yet another good reason to clean install.
+1

I had used upgrades from 6.06 thru 9.04, but then wanted to change to 64 bit so had to do a clean install of 9.10. As a new user I had not been good about housecleaning and did not realize how much cruft I had accumulated.

---

