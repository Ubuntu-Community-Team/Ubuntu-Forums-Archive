---
title: "VMware Install issue"
date: 2007-05-18
forum: General Help
---

### Post by mcallahan01 on 2007-05-18
I'm new to the world of Linux and am really hoping you folks can help me out with a problem that I am having installing VMware on my new Ubuntu machine.  The install seems to go perfectly fine until it get's to the point where you have to run the vmware-config.pl and then things get a bit sticky. Below is the output of the error I am gettiing. Thanks in advance for helping out with this.

root@Ununtu:/bin# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps] Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca


/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!


Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:80:
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â€˜...â€™ before â€˜compat_exitâ€™
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â€˜...â€™ before â€˜exit_codeâ€™
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to â€˜intâ€™ in declaration of â€˜_syscall1â€™
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@Ununtu:/bin#

---

### Post by jinx099 on 2007-05-19
I'm having the same problem.  I'm running the amd64 version of feisty.

---

### Post by rysh on 2007-05-19
I am not really sure about the amd64 version, but i know the 2.6.20 was not yet supported by the last vmware-server version i tried to install. a little search on internet showed that i could try the un-official update from this site: 
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

When the installation script wants to run vmware-config.pl you abort and run the runme.pl from this update package .... 

goodluck

---

### Post by mcallahan01 on 2007-05-19
Yeah, I've also got the AMD64 version installed.  In any case I tried running the runme.pl from the update package and this is what I get:

root@ubuntu:/temp1/vmware-any-any-update109# sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... now patched
sh: ./update: not found
sh: ./update: not found
sh: ./update: not found
sh: ./update: not found
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it
for your running kernel by invoking the following command:
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for
you now? [yes]

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and V
Mware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PW
D/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@ubuntu:/temp1/vmware-any-any-update109#

---

### Post by Tahi_Kiwi on 2007-05-19
I'm getting a related problem.

I'm running VMware WS 6, Vista host, and installed Ubuntu Studio OK. Upon running the VMTools pearl script, everything was fine until I got:

The path "[/usr/src/linux/include] is not an existing directory. What is the location of the directory of the C header files that match the running kernel. [/usr/src/linux/include] 

Pressing Enter to accept the default, cycles back to the same question. 

I haven't found anything on the VMware forum.

---

### Post by HereInOz on 2007-05-19
From what I can work out, VMWare server does not support Feisty.  I ran into the same problem after I upgraded Edgy to Feisty, and VMWare server fell over.  No amount of re-configuring would make it happen.

So, back to Edgy, re-install VMWare Server and all is well.  Looks like I am stuck with Edgy for the time, until VMWare puts out a version which supports Feisty.

Sorry I can't be more help.

---

### Post by Bachstelze on 2007-05-19
As was stated earlier. VMware Server just does not support the 2.6.20 kernel, whatever your distro is, not only in Feisty. I've written a patch for it though :

```

cd
wget http://fkraiem.free.fr/vmmon.tar
sudo mv vmmon.tar /usr/lib/vmware/modules/source
sudo /usr/bin/vmware-config.pl
```

you're there :)


@Tahi_Kiwi, your problem is different, you need to install the headers for your running kernel, just do ;

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Tahi_Kiwi on 2007-05-20
Thank you, HymeToLife.

That worked! 

So, even though the situation is different, VMware Workstation and VMTools run Linux Guests with kernel 2.6.20. I had already successfully installed Ubuntu 704, Kubuntu 704, and Xubuntu 704...and now Ubuntu Studio. For some reason, Ubuntu Studio doesn't install the c headers by default. Who would have known?

VMTools requires the C headers to be installed first, afterwhich it runs fine.

---

### Post by Bachstelze on 2007-05-20
VMware Workstation does not run kernel 2.6.20. Ubuntu 7.04 does ;)

---

### Post by Tahi_Kiwi on 2007-05-20
Thanks. I had misunderstood. I had misunderstood that anything with kernel 2.6.20 would not cooperate with VMware some product.

Thanks.

---

### Post by HereInOz on 2007-05-20
Thanks for the patch, HymnToLife.  What we do without you - we would be lost!!

---

### Post by WattoDaToydarian on 2007-05-21
> **HymnToLife said:**
> As was stated earlier. VMware Server just does not support the 2.6.20 kernel, whatever your distro is, not only in Feisty. I've written a patch for it though :

```

cd
wget http://fkraiem.free.fr/vmmon.tar
sudo mv vmmon.tar /usr/lib/vmware/modules/source
sudo /usr/bin/vmware-config.pl
```

you're there :)


I compiled a 2.6.21 kernel on my server and your patch worked better for me but eventually failed further down the road.
This is the output:
```
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.21.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.21.1'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.21.1'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmmon.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```
Could you make a patch for 2.6.21?
Thanks!

---

### Post by peter3 on 2007-05-23
I've looked all over for a solution to this problem.  So far no luck.  The VMware install works with
a few hitches all the way to entering the registration key.  I have several keys, none of which seem
to work.  Here's the end of the install output for your review.  Any comments would be greatly
appreciated.

Peter

In which directory do you want to keep your virtual machine files? 
[/share/VM] 

sh: /usr/lib/vmware/bin/vmware-vmx: not found
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  90W81-YWM6G-2A7C1-4TL9E

sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number 90W81-YWM6G-2A7C1-4TL9E is invalid.

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  

You cannot power on any virtual machines until you enter a valid serial number.
To enter the serial number, run this configuration program again, or choose 
'Help > Enter Serial Number' in the virtual machine console.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.

####    yes, but it doesn't work!!!!
The line
sh: /usr/lib/vmware/bin/vmware-vmx: not found
does not indicate that the file is not found, but seems to indicate that this file can't find
something else.  
So I'm stumped....

Thanks.

---

### Post by mcallahan01 on 2007-05-24
Thanks HymnToLife. I finally had a chance to revisit my install and your patch did the trick. Much appreciated.:)

---

### Post by seamuso on 2007-05-24
seamuso@bluebuntu:~$ uname -a
Linux bluebuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
seamuso@bluebuntu:~$ vmware -v
VMware Server 1.0.3 build-44356

installed using these instructions ...

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

install was painless

---

### Post by Deano1123 on 2007-05-24
Hey all,

I am getting the exact same error as Peter3 above:

sh: /usr/lib/vmware/bin/vmware-vmx: not found

I've checked and the location and its there, but am stumped as to what to do now.

---------------:/usr/lib/vmware/bin$ ls -l
total 20352
-r-xr-xr-x 1 root root 3651784 2007-05-24 17:39 libvmcontrol-helper
-r-xr-xr-x 1 root root 1130988 2007-05-24 17:39 openssl
-r-xr-xr-x 1 root root 2410192 2007-05-24 17:39 vmrun
-r-xr-xr-x 1 root root 7615804 2007-05-24 17:39 vmware
-r-xr-xr-x 1 root root 1589452 2007-05-24 17:39 vmware-remotemks
-rwsrwsrwx 1 root root 4385956 2007-05-24 17:39 vmware-vmx
---------------:/usr/lib/vmware/bin$ 


Anybody have any ideas?

Cheers

---

### Post by Deano1123 on 2007-05-24
My problem is solved.

Turned out I didn't have the ia32-libs installed.

---

### Post by knichel on 2007-06-07
Thanks for the patch.  Was pulling my hair out...

---

### Post by jgeissin on 2007-06-12
Where do I find ia32-libs at?  I looked through the package manager and it is not listed.
Thanks!

---

### Post by wakingrufus on 2007-06-13
I ran the patch, and it worked until this:
```

Configuring the VMware VmPerl Scripting API.
Unable to find the VMware VmPerl Scripting API.  You may want to re-install 
VMware Server.

Execution aborted.

user@computer:~/Desktop/vmware-any-any-update109$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


```

---

### Post by dannymichel on 2007-06-19
I'm getting
```
danny@danny-desktop:~$ cd Desktop
danny@danny-desktop:~/Desktop$ dir
Mac_OS_X_10_4_8_[JaS_AMD_Intel_SSE2_SSE3_with_PPF1_PPF2]-[Demonoid.com]_4845464.5112.torrent
Tribal\ Seeds\ -\ BeautifulMysterious.mp3
vmware-any-any-update109
vmware-any-any-update109.tar.gz
danny@danny-desktop:~/Desktop$ cd vmware-any-any-update109
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ dir
runme.pl  services.sh  update  update.c  vmmon.tar  vmnet.tar
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ sudo update
Password:
sudo: update: command not found
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ sudo runme.pl
sudo: runme.pl: command not found
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... corrupted
The file /usr/lib/vmware-server/modules/source/vmmon.tar that this script was 
about to install already exists. Overwrite? [yes] y

The file /usr/lib/vmware-server/modules/source/vmnet.tar that this script was 
about to install already exists. Overwrite? [yes] y

Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware-server/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware-server/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware-server/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] y

sh: /usr/bin/vmware-config.pl: not found
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ sudo vmware-config.pl
sudo: vmware-config.pl: command not found
danny@danny-desktop:~/Desktop/vmware-any-any-update109$ 


```

---

