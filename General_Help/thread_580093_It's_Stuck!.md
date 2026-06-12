---
title: "It's Stuck!"
date: 2007-10-18
forum: General Help
---

### Post by snick512 on 2007-10-18
Last night i tried installing VirtualBox, but it stayed at one screen for wayyy to long, so i canceled it. Which the first box went away, but the deb package didn't. Couldn't get rid of it (think i made a mistake by restarting the computer)

Anywho, I'm trying to install other things, but it's not letting me, so i tried to remove the virtual box

```

ty@ubuntu:~$ sudo apt-get remove virtualbox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
ty@ubuntu:~$ 

```

I'm stuck on this one, how do i fix this?

---

### Post by p_quarles on 2007-10-18
First thing I would try is:
```
sudo apt-get autoremove
```
Let us know how that works.

---

### Post by snick512 on 2007-10-18
Nope it doesnt work

```
ty@ubuntu:~$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
ty@ubuntu:~$ 
```

---

### Post by p_quarles on 2007-10-18
First, as a temporary fix, you might get it to ignore this problem by using:
```
sudo apt-get install -m *package-name*
```
As for a permanent fix . . . how did you try to install this? Did you use a .deb file, or (if you're on 7.10) did you install it from the repositories? Knowing this might help me or someone else give you a solution.

---

### Post by snick512 on 2007-10-18
```
ty@ubuntu:~$ sudo apt-get install -m virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
ty@ubuntu:~$ 

```


Ubuntu feisty 7.04, i think Feisty definitely

Yes, i tried installing from a deb file

[link]http://virtualbox.org/wiki/Downloads[/link]

---

### Post by p_quarles on 2007-10-18
Okay, so that means you downloaded the .deb from Innotek and installed that?

First, try this:
CD to the directory in which the .deb file is located, then type:
```
sudo dpkg -r *package-name*
```
*package-name* should be the name of the archive file -- the one I have is called "virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb"

That will attempt to remove the partial installation. If that doesn't work, try:
```
sudo dpkg -i *package-name*
```
That will try reinstall it from the file.

---

### Post by snick512 on 2007-10-18
```

ty@ubuntu:~/virtual$ sudo dpkg -r virtualbox_1.5.2-25433_Ubuntu_feisty_i386
dpkg - warning: ignoring request to remove virtualbox_1.5.2-25433_ubuntu_feisty_i386 which isn't installed.
ty@ubuntu:~/virtual$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_feisty_i386
dpkg: error processing virtualbox_1.5.2-25433_Ubuntu_feisty_i386 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox_1.5.2-25433_Ubuntu_feisty_i386
ty@ubuntu:~/virtual$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_feisty_i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
126549 files and directories currently installed.)
Preparing to replace virtualbox 1.5.0-24069-1_Ubuntu_feisty (using virtualbox_1.5.2-25433_Ubuntu_feisty_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Configuring virtualbox
----------------------

Old vboxdrv modules found. It is recommended to purge these modules as they might not work 
together with this version of VirtualBox. The module re-compilation can be forced later by 
executing

  /etc/init.d/vboxdrv setup

[More] ^[[B^[[B

as root

Delete old modules?  
```

I pressed CTRL+D


```

Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <FIN> line 7.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN1> line 6.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN1> line 6.
Unpacking replacement virtualbox ...
Setting up virtualbox (1.5.2-25433_Ubuntu_feisty) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Configuring virtualbox
----------------------

Creating group 'vboxusers'.

Users of VirtualBox must be member of that group in order to have write permissions to 
/dev/vboxdrv. Otherwise starting of VMs will not be possible.

Unable to find a precompiled module for the current kernel!
[More] 


Without a suitable kernel module you will never be able to start VMs. It is strongly recommended 
to compile a kernel module now. The kernel headers and the tools to build kernel modules (gcc, 
make, binutils, ...) are required. However, in case a suitable kernel module already exists at 
another place you might want to override the default position by setting 
KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox. The compilation can also be done 
later by executing

  /etc/init.d/vboxdrv setup
[More] 


as root.

Should the vboxdrv kernel module be compiled now? n


 * Starting VirtualBox kernel module vboxdrv                                                      FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/vbox/vboxdrv.ko': No such file or directory

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
Starting VirtualBox host networking...done.

ty@ubuntu:~/virtual$ sudo apt-get remove virtual
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtual
ty@ubuntu:~/virtual$ sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl-core libxalan110 libberylsettings0 nvidia-kernel-common beryl-plugins-data
  libberyldecoration0 libxerces27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
Need to get 0B of archives.
After unpacking 35.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127161 files and directories currently installed.)
Removing virtualbox ...
 * Stopping VirtualBox kernel module vboxdrv                                               [ OK ] 
Shutting down VirtualBox host networking...done.
ty@ubuntu:~/virtual$ 
```

:D thank you

---

### Post by p_quarles on 2007-10-18
Cool. Glad it worked.

---

