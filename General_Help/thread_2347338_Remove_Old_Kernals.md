---
title: "Remove Old Kernals"
date: 2016-12-23
forum: General Help
---

### Post by hyburn on 2016-12-23
I have followed the instructions listed here with regards on how to remove old kernals:
[http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu)

my question is "can I get rid of everything that does not have the (`16.04.1LTS) extension?"

the list ranges from:
3.4.0-4.27 to 4.9.0.32.5 with some of these having the above mentioned extention. I think this might be why I have a long boot time

---

### Post by Bashing-om on 2016-12-23
hyburn; Hey !

The short answer is that you run:
```

uname -r

```
you MUST keep this kernel.
Now also look at :
```

dpkg -l | grep linux-

```
IF and only IF the booting kernel ( uname -r) is shown as the highest kernel available, then yes remove all but the one version under this kernel.
We generally only want to keep 2 kernels, the one booting and 1 other as a backup .

// But no, the number of installed kernels will not effect how fast the system boots .

Now once you have the package manager in a happy state in respect to installed kernels, one can:
A) run ' sudo apt autoremove ' to remove the old kernels.
B) Use the unattended-upgrades package to regularly run autoremove for you.
C) I "think" 16.10+ is now set to only keep 2 kernels.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hyburn on 2016-12-23
*uname -r* gives me
**4.4.0-57-generic**

and the *dpkg -l|grep linux-* gives me:
[B]ii  linux-base                                 4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                             1.157.6                                       all          Firmware for Linux kernel drivers
ii  linux-generic                              4.4.0.57.60                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-31                     4.4.0-31.50                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic             4.4.0-31.50                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                     4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic             4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.4.0.57.60                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic               4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic         4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic         4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.57.60                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       4.4.0-57.78                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
[/B]
do I have the most recent kernal?

*sudo apt-get update* does not appear to install anything new

*sudo apt-get upgrade* has nothing further to install either

does this mean I have the most recent kernel?

---

### Post by ian-weisser on 2016-12-23
Do you HAVE the most recent kernel? Almost, but no.
You have one of the two 4.4.0-57-60 kernel packages.

Are you RUNNING the most recent kernel?
Use the command 'uname -r' to determine which kernel you are running.

Keep 4.4.0-57-60. It will become the most recent kernel.
Keep the one you are running.
Use the package manager to uninstall the rest.

---

### Post by hyburn on 2016-12-23
ok, on the synaptic package manager I searched for linux-image and organized by installed version

uname -r returns
4.4.0-57-generic

I have:
(linux-image-generic) 4.4.0-57.60
(linux-image-4.4.0-57 generic)4.4.0-57.78
(linux-image-extra-4.4.0-57-generic)4.4.0-57.78
(linux-image-extra-4.4.0-31-generic0 4.4.0-31.50

should I mark all but 1 and 2 for uninstall?

I only ask for a step by step because I am outide my realm of knowledge for this stuff and do not want to destroy my installation

---

### Post by hyburn on 2016-12-23
thank you Ian for the help

---

### Post by Bashing-om on 2016-12-23
hyburn; well;

tough to say, there is a reason we request outputs be between code tags

This is the latest kernel in the repo:
> 
linux-image-generic (source: linux-meta): Generic Linux kernel image. In component main, is optional. Version 4.4.0.57.60 (xenial), package 
                size 2 kB, installed size 12 kB


The command uname -a in a terminal will tell you which kernel you are running....then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for removal/complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
```

sudo update-grub

``` to propagate the changes to the operating system.

  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).
see also:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean) <-How to clean up Ubuntu


Now if all you have installed is
4.4.0-57.XX
-4.4.0-31
then you do not want to do else at this time . Might be best to hold on to what you have and await 4.4.0-57.78 to arrive in the repo .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

