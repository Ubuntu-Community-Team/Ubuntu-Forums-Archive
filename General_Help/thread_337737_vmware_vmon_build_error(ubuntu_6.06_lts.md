---
title: "vmware vmon build error(ubuntu 6.06 lts"
date: 2007-01-13
forum: General Help
---

### Post by iamcanadian on 2007-01-13
When i install vmware 5.5 or 6.0 i get the followng error:

marshall@marshall-desktop:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Workstation are stopped.

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

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-4.0". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

gcc-3.4: auto-build: No such file or directory
gcc-3.4: HEADER_DIR=/lib/modules/2.6.15-26-386/build/include: No such file or directory
gcc-3.4: CC=/usr/bin/gcc-4.0: No such file or directory
gcc-3.4: GREP=grep: No such file or directory
gcc-3.4: IS_GCC_3=no: No such file or directory
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

can any one help me!

thanks ;)

---

### Post by iamcanadian on 2007-01-13
anyone? i really need vmware

---

### Post by iamcanadian on 2007-01-13
bump?? please im useing wine right now but its not enugh please :)

---

### Post by Tanker Bob on 2007-01-13
I'm a noob to VMWare myself.  I installed Workstation 5.5.3 with no problems on Kubuntu 6.10, even though only 6.06 is officially supported by VMWare.  Did you try installing as root?  That's how I did my install, and I also run the VM as root so that it can access my scanner which is perpetually owned by root (known issue).  When I tried doing VM stuff not as root, there are always a number of error messages.

---

### Post by iamcanadian on 2007-01-13
i only have the one account i made at install, im not a n00b to linux or vmware (inless its on linux >.<)but i am to ubuntu, so is that account the root beacuse thats the account ive been useing to install vmware

---

### Post by Tanker Bob on 2007-01-13
I'm new to both Linux and VMWare, so I don't have any other ideas.  I only know what worked for me.

---

### Post by iamcanadian on 2007-01-13
no problem meby someone else can help me but thx for trying

---

