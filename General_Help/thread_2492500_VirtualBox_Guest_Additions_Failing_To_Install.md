---
title: "VirtualBox Guest Additions Failing To Install"
date: 2023-11-13
forum: General Help
---

### Post by fiscoking on 2023-11-13
Hi,

I've installed ubuntu-20.04.2.0-desktop-amd64 on Virtualbox. Minimal install selected to save disk space. the latest version of Ubuntu take up a lot more disk space.

Trying to install the VirtualBox Guest addition within Ubuntu.

Following the instructions below:

[https://www.pragmaticlinux.com/2020/07/install-virtualbox-guest-additions-in-debian-10/](https://www.pragmaticlinux.com/2020/07/install-virtualbox-guest-additions-in-debian-10/)
[https://www.pragmaticlinux.com/2021/02/how-to-mount-a-shared-folder-in-virtualbox/](https://www.pragmaticlinux.com/2021/02/how-to-mount-a-shared-folder-in-virtualbox/)

These are the only instructions I could find.

To summarise;

sudo apt update
sudo apt upgrade
sudo apt install build-essential dkms linux-headers-$(uname -r)
Inset CD ROM -> Cancel installation prompt
sudo sh /media/cdrom0/VBoxLinuxAdditions.run
sudo reboot

The installation is failing on VBoxLinuxAdditions.run. All the other commands the precede it work.

Script single error message is: Building the main guest additions module...fail!

The log file can be found below:

---------------------

Uninstalling modules from DKMS
Attempting to install using DKMS
 
Creating symlink /var/lib/dkms/vboxguest/5.0.24/source ->
                 /usr/src/vboxguest-5.0.24
 
DKMS: add completed.
 
Kernel preparation unnecessary for this kernel.  Skipping...
 
Building module:
cleaning build area...
make -j2 KERNELRELEASE=5.15.0-88-generic -C /lib/modules/5.15.0-88-generic/build M=/var/lib/dkms/vboxguest/5.0.24/build...(bad exit status: 2)
ERROR (dkms apport): binary package for vboxguest: 5.0.24 not found
Error! Bad return status for module build on kernel: 5.15.0-88-generic (x86_64)
Consult /var/lib/dkms/vboxguest/5.0.24/build/make.log for more information.
Failed to install using DKMS, attempting to install without
grep: /lib/modules/5.15.0-88-generic/build/include/linux/version.h: No such file or directory
make KBUILD_VERBOSE=1 CONFIG_MODULE_SIG= -C /lib/modules/5.15.0-88-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
: "  SYNC    include/config/auto.conf.cmd"
make -f ./Makefile syncconfig
make -f ./scripts/Makefile.build obj=scripts/basic
make -f ./scripts/Makefile.build obj=scripts/kconfig syncconfig
  flex -oscripts/kconfig/lexer.lex.c -L scripts/kconfig/lexer.l
/bin/sh: 1: flex: not found
make[3]: *** [scripts/Makefile.host:9: scripts/kconfig/lexer.lex.c] Error 127
make[2]: *** [Makefile:630: syncconfig] Error 2
make[1]: *** [Makefile:750: include/config/auto.conf.cmd] Error 2
make: *** [/tmp/vbox.0/Makefile.include.footer:79: vboxguest] Error 2
Creating user for the Guest Additions.
Creating udev rule for the Guest Additions kernel module.


----------------------

Has anyone got guest additions to install successfully on Ubuntu, and how did you do it?

Thanks.

---

### Post by SeijiSensei on 2023-11-13
It's not clear if you have a complete build environment. Run
```

sudo apt update
sudo apt install build-essential dkms

```
to make sure you all the needed packages. Then try again.

That said, why are you using 20.04 rather than 22.04?

Finally, back in the days when I used VirtualBox (now I use KVM), I would always add the official Oracle repository to my sources and download VBox and guest additions from there. I long ago stopped using the official Ubuntu releases.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by fiscoking on 2023-11-13
Hello [COLOR=#000000]SeijiSensei,

I'm using 20.04 because it has an installer option for a minimum install. 22.04 doesn't have this and the install is much larger. I don't need all the extra stuff. It just takes up more disk space on my small SSD.

[/COLOR]I've tried both commands and both executed. Output below.

VBox guest CD still errors in the same place.

[COLOR=#000000]Script single error message is: Building the main guest additions module...fail![/COLOR]

There is still no share as described in the tutorial at login. VBox has the share set to automount.

Is there some special place to look for the share?

Also, for some reason now my screen resolution has maxed out at 1024x768. It was larger than this before.

Thanks.

----

[LIST]
[*][COLOR=#000000]ubuntu@ubuntu-VirtualBox:~$ sudo apt install build-essential dkms[/COLOR]
[*][COLOR=#000000]Reading package lists... Done[/COLOR]
[*][COLOR=#000000]Building dependency tree       [/COLOR]
[*][COLOR=#000000]Reading state information... Done[/COLOR]
[*][COLOR=#000000]build-essential is already the newest version (12.8ubuntu1.1).[/COLOR]
[*][COLOR=#000000]dkms is already the newest version (2.8.1-5ubuntu2).[/COLOR]
[*][COLOR=#000000]The following packages were automatically installed and are no longer required:[/COLOR]
[*][COLOR=#000000]  gir1.2-goa-1.0 libfwupdplugin1 libllvm11 libxmlb1[/COLOR]
[*][COLOR=#000000]Use 'sudo apt autoremove' to remove them.[/COLOR]
[*][COLOR=#000000]0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.[/COLOR]
[/LIST]

---

### Post by Yellow Pasque on 2023-11-13
> /bin/sh: 1: flex: not found

Maybe you should install flex and try again:
```
sudo apt-get install flex
```

---

### Post by fiscoking on 2023-11-13
tried that. installed ok. still errors at the same place. log file below:


[LIST]
[*][COLOR=#000000]Uninstalling modules from DKMS[/COLOR]

[*][COLOR=#000000]Attempting to install using DKMS[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Creating symlink /var/lib/dkms/vboxguest/5.0.24/source ->[/COLOR]

[*][COLOR=#000000]                 /usr/src/vboxguest-5.0.24[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]DKMS: add completed.[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Kernel preparation unnecessary for this kernel.  Skipping...[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Building module:[/COLOR]

[*][COLOR=#000000]cleaning build area...[/COLOR]

[*][COLOR=#000000]make -j2 KERNELRELEASE=5.15.0-88-generic -C /lib/modules/5.15.0-88-generic/build M=/var/lib/dkms/vboxguest/5.0.24/build...(bad exit status: 2)[/COLOR]

[*][COLOR=#000000]ERROR (dkms apport): binary package for vboxguest: 5.0.24 not found[/COLOR]

[*][COLOR=#000000]Error! Bad return status for module build on kernel: 5.15.0-88-generic (x86_64)[/COLOR]

[*][COLOR=#000000]Consult /var/lib/dkms/vboxguest/5.0.24/build/make.log for more information.[/COLOR]

[*][COLOR=#000000]Failed to install using DKMS, attempting to install without[/COLOR]

[*][COLOR=#000000]grep: /lib/modules/5.15.0-88-generic/build/include/linux/version.h: No such file or directory[/COLOR]

[*][COLOR=#000000]make KBUILD_VERBOSE=1 CONFIG_MODULE_SIG= -C /lib/modules/5.15.0-88-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules[/COLOR]

[*][COLOR=#000000]: "  SYNC    include/config/auto.conf.cmd"[/COLOR]

[*][COLOR=#000000]make -f ./Makefile syncconfig[/COLOR]

[*][COLOR=#000000]make -f ./scripts/Makefile.build obj=scripts/basic[/COLOR]

[*][COLOR=#000000]make -f ./scripts/Makefile.build obj=scripts/kconfig syncconfig[/COLOR]

[*][COLOR=#000000]  flex -oscripts/kconfig/lexer.lex.c -L scripts/kconfig/lexer.l[/COLOR]

[*][COLOR=#000000]  bison -o scripts/kconfig/parser.tab.c --defines=scripts/kconfig/parser.tab.h -t -l scripts/kconfig/parser.y[/COLOR]

[*][COLOR=#000000]/bin/sh: 1: bison: not found[/COLOR]

[*][COLOR=#000000]make[3]: *** [scripts/Makefile.host:17: scripts/kconfig/parser.tab.h] Error 127[/COLOR]

[*][COLOR=#000000]make[3]: *** [scripts/kconfig/parser.tab.h] Deleting file 'scripts/kconfig/parser.tab.c'[/COLOR]

[*][COLOR=#000000]make[2]: *** [Makefile:630: syncconfig] Error 2[/COLOR]

[*][COLOR=#000000]make[1]: *** [Makefile:750: include/config/auto.conf.cmd] Error 2[/COLOR]

[*][COLOR=#000000]make: *** [/tmp/vbox.0/Makefile.include.footer:79: vboxguest] Error 2[/COLOR]

[*][COLOR=#000000]Creating user for the Guest Additions.[/COLOR]

[*][COLOR=#000000]Creating udev rule for the Guest Additions kernel module.[/COLOR]
[/LIST]

---

### Post by Yellow Pasque on 2023-11-13
No, this is a bit different:
> /bin/sh: 1: bison: not found

Install bison package. You may also need other packages, like autoconf automake libtool if you don't have them already.

---

### Post by fiscoking on 2023-11-13
Installed bison. It still errors in the same place. Log below.

>>[COLOR=#000000]You may also need other packages

[/COLOR]I'm new to linux. I can follow instructions but that's it. It still cannot find the correct dkms - whatever that is, even though I've done a full update.

[COLOR=#333333][FONT=Consolas][COLOR=#ACACAC]
[LIST]
[*][COLOR=#000000]Uninstalling modules from DKMS[/COLOR]

[*][COLOR=#000000]Attempting to install using DKMS[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Creating symlink /var/lib/dkms/vboxguest/5.0.24/source ->[/COLOR]

[*][COLOR=#000000]                 /usr/src/vboxguest-5.0.24[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]DKMS: add completed.[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Kernel preparation unnecessary for this kernel.  Skipping...[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]Building module:[/COLOR]

[*][COLOR=#000000]cleaning build area...[/COLOR]

[*][COLOR=#000000]make -j2 KERNELRELEASE=5.15.0-88-generic -C /lib/modules/5.15.0-88-generic/build M=/var/lib/dkms/vboxguest/5.0.24/build...(bad exit status: 2)[/COLOR]

[*][COLOR=#000000]ERROR (dkms apport): binary package for vboxguest: 5.0.24 not found[/COLOR]

[*][COLOR=#000000]Error! Bad return status for module build on kernel: 5.15.0-88-generic (x86_64)[/COLOR]

[*][COLOR=#000000]Consult /var/lib/dkms/vboxguest/5.0.24/build/make.log for more information.[/COLOR]

[*][COLOR=#000000]Failed to install using DKMS, attempting to install without[/COLOR]

[*][COLOR=#000000]grep: /lib/modules/5.15.0-88-generic/build/include/linux/version.h: No such file or directory[/COLOR]

[*][COLOR=#000000]make KBUILD_VERBOSE=1 CONFIG_MODULE_SIG= -C /lib/modules/5.15.0-88-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules[/COLOR]

[*][COLOR=#000000]: "  SYNC    include/config/auto.conf.cmd"[/COLOR]

[*][COLOR=#000000]make -f ./Makefile syncconfig[/COLOR]

[*][COLOR=#000000]make -f ./scripts/Makefile.build obj=scripts/basic[/COLOR]

[*][COLOR=#000000]make -f ./scripts/Makefile.build obj=scripts/kconfig syncconfig[/COLOR]

[*][COLOR=#000000]  bison -o scripts/kconfig/parser.tab.c --defines=scripts/kconfig/parser.tab.h -t -l scripts/kconfig/parser.y[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.lexer.lex.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89      -I ./scripts/kconfig -c -o scripts/kconfig/lexer.lex.o scripts/kconfig/lexer.lex.c[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.menu.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89       -c -o scripts/kconfig/menu.o scripts/kconfig/menu.c[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.parser.tab.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89      -I ./scripts/kconfig -c -o scripts/kconfig/parser.tab.o scripts/kconfig/parser.tab.c[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.preprocess.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89       -c -o scripts/kconfig/preprocess.o scripts/kconfig/preprocess.c[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.symbol.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89       -c -o scripts/kconfig/symbol.o scripts/kconfig/symbol.c[/COLOR]

[*][COLOR=#000000]  gcc -Wp,-MMD,scripts/kconfig/.util.o.d -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer -std=gnu89       -c -o scripts/kconfig/util.o scripts/kconfig/util.c[/COLOR]

[*][COLOR=#000000]  gcc   -o scripts/kconfig/conf scripts/kconfig/conf.o scripts/kconfig/confdata.o scripts/kconfig/expr.o scripts/kconfig/lexer.lex.o scripts/kconfig/menu.o scripts/kconfig/parser.tab.o scripts/kconfig/preprocess.o scripts/kconfig/symbol.o scripts/kconfig/util.o   [/COLOR]

[*][COLOR=#000000]scripts/kconfig/conf  --syncconfig Kconfig[/COLOR]

[*][COLOR=#000000]make -f ./scripts/Makefile.build obj=arch/x86/entry/syscalls all[/COLOR]

[*][COLOR=#000000]make[2]: *** No rule to make target 'arch/x86/entry/syscalls/syscall_32.tbl', needed by 'arch/x86/include/generated/uapi/asm/unistd_32.h'. Stop.[/COLOR]

[*][COLOR=#000000]make[1]: *** [arch/x86/Makefile:217: archheaders] Error 2[/COLOR]

[*][COLOR=#000000]make: *** [/tmp/vbox.0/Makefile.include.footer:79: vboxguest] Error 2[/COLOR]

[*][COLOR=#000000]Creating user for the Guest Additions.[/COLOR]

[*][COLOR=#000000]Creating udev rule for the Guest Additions kernel module.[/COLOR]

[*]

[/LIST]
[/COLOR]
[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2023-11-13
Again, it's not the same spot (the build gets further). This one has me stumped though. It seems that the file in question should be found if you have the appropriate kernel headers installed

Are you really using Virtualbox 5.0.24 or am I reading the output incorrectly? If so, what host system are you running on? Virtualbox 5.0.24 is outdated.

---

### Post by fiscoking on 2023-11-13
[COLOR=#000000]Are you really using Virtualbox 5.0.24

Yes. It's worked for everything else, so no need to change it.

[/COLOR][COLOR=#000000]If so, what host system are you running on? 

Win7x64

[/COLOR][COLOR=#000000]Virtualbox 5.0.24 is outdated.

It works with Windows guests. I've got XP, 7, 8.1 and 10 all running with guest additions. The virtual cd rom exe just works. It's only linux that has an issue.

If the virtual cd rom script doesn't work with this version of ubuntu, what about other sources? I tried installing [/COLOR]open-vm-tools-desktop and that went on without error but it just didn't work. No mapped folder.[COLOR=#000000]

[/COLOR]sudo apt-get install open-vm-tools open-vm-tools-desktop

---

### Post by ian-weisser on 2023-11-13
> **fiscoking said:**
> [COLOR=#000000]Yes. It's worked for everything else, so no need to change it.[/COLOR]

Perhaps you just found a reason to change it.

---

### Post by MAFoElffen on 2023-11-13
Please post the results of this:
```

apt list linux-headers-$(uname -r) --installed

```
If it is not there, then install it.

Why? Because to built dkms modules, it needs the header files to the current running kernel, and that is not always a default install on a minimized installation. And exit status 2 returned from make, when it is collecting resources is usually a missing resource, such as a header file.

---

### Post by fiscoking on 2023-11-14
results:

linux-headers-5.15.0-88-generic/focal-updates, focal-security,now 5.15.0-88.98~20.04.1  amd64 [installed]

---

### Post by fiscoking on 2023-11-14
> **ian-weisser said:**
> You just found a reason to change it.
A very good reason.

There is no evidence that VirtualBox is the problem here. The problem is the guest OS running the script, and the assumptions the script authors made about its runtime environment. It's a shame they didn't bother to tell us what those assumptions were. Here we are having to dig though log files to find out as a result.

As the OS is already running, VBox is doing its bit. The only way a change of Vbox would help is if the guest additions script has changed in a later version. A guess at this stage. This is why I asked if anyone had got it running on a modern version of Ubuntu.

---

### Post by Yellow Pasque on 2023-11-14
Full support for kernel 5.15.x (on hosts and guests) was not added until Virtualbox 6.1.28: [https://www.virtualbox.org/wiki/Changelog-6.1](https://www.virtualbox.org/wiki/Changelog-6.1)
If you use the "Insert Guest Addition CD" function, then the script is part of (your old) Virtualbox. So yes, your version of Virtualbox is the problem here.
Vbox 5.0.24 is ancient (2016) and the Vbox 5.x series has been unsupported for years (April 2017 was the last release).

EDIT: I remember I got the VBox guest additions to build just fine on Linux Mint 21.2 (which uses the same kernel and underpinnings as Ubuntu Jammy/22.04).

---

### Post by SeijiSensei on 2023-11-14
As I said before, using the Oracle repository for VirtualBox has always worked for me. Have you tried that yet instead of compiling?

---

### Post by ian-weisser on 2023-11-14
> **fiscoking said:**
> This is why I asked if anyone had got it running on a modern version of Ubuntu.

I am currently running VirtualBox 7.0.10 on Ubuntu 23.10, including Guest Additions. The particular Virtualbox packages are from the 23.10 Ubuntu repositories. There were zero problems with installation of Virtualbox, and zero problems with Guest Additions. Everything just worked properly.

---

### Post by fiscoking on 2023-11-14
Update.

Upgraded to VirtualBox 7.0.8 this evening. This is as high as I can go on Win7x64. Not too far of current. All my existing VMs work though.

I started over with a fresh Ubuntu 20.04.2 LTS build and selected minimal installation.

These are the commands I had to use on Ubuntu (minimal installation) to get Guest Additions to work.

sudo apt update
sudo apt install build-essential
sudo apt-get install manpages-dev
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo reboot
Inset Guest Additions CD ROM (Devices menu \ Insert GA CD Image) -> Cancel auto-run installation prompt.
sudo sh /media/ubuntu/VBox_GAs_7.0.8/VBoxLinuxAdditions.run
sudo reboot
sudo usermod -aG vboxsf $(whoami)
sudo reboot

Open file manager, the share to host is just above 'other locations' on the left.

Make sure 'shared folders' in the VirtualBox management console on the host has a path and is set to auto-mount before you start the above.

So [COLOR=#000000]Yellow Pasque and [/COLOR]ian-weisser were correct, it was the version of VirtualBox I was using. Would never have guessed.

Thanks for all your help.

---

