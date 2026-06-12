---
title: "Question about installed kernels"
date: 2019-06-28
forum: General Help
---

### Post by again? on 2019-06-28
Installed my OS from xubuntu-18.04-desktop-amd64.iso
Just noticed an installed kernel updating that wasn't what inxi shows I'm using.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] inxi -S**
System:    Host: Bionic Kernel: 4.18.0-16-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.2 LTS
```

From update log...
```
Start-Date: 2019-06-28  17:53:51
Commandline: apt upgrade
Requested-By: glen (1000)
Install: linux-modules-extra-4.15.0-54-generic:amd64 (4.15.0-54.58, automatic), linux-modules-4.15.0-54-generic:amd64 (4.15.0-54.58, automatic), linux-headers-4.15.0-54-generic:amd64 (4.15.0-54.58, automatic), linux-headers-4.15.0-54:amd64 (4.15.0-54.58, automatic), [COLOR="#FF0000"]linux-image-4.15.0-54-generic[/COLOR]:amd64 (4.15.0-54.58, automatic)
Upgrade: poppler-utils:amd64 (0.62.0-2ubuntu2.8, 0.62.0-2ubuntu2.9), linux-headers-generic:amd64 (4.15.0.52.54, 4.15.0.54.56), linux-libc-dev:amd64 (4.15.0-52.56, 4.15.0-54.58), google-chrome-beta:amd64 (76.0.3809.36-1, 76.0.3809.46-1), linux-image-generic:amd64 (4.15.0.52.54, 4.15.0.54.56), libpoppler-qt5-1:amd64 (0.62.0-2ubuntu2.8, 0.62.0-2ubuntu2.9), libpoppler-glib8:amd64 (0.62.0-2ubuntu2.8, 0.62.0-2ubuntu2.9), libpoppler73:amd64 (0.62.0-2ubuntu2.8, 0.62.0-2ubuntu2.9), linux-generic:amd64 (4.15.0.52.54, 4.15.0.54.56)
End-Date: 2019-06-28  17:55:23
```

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls /boot | grep vmlinuz**
[COLOR="#FF0000"]vmlinuz-4.15.0-54-generic[/COLOR]
vmlinuz-4.18.0-15-generic
vmlinuz-4.18.0-16-generic
```

4.15.0-54 shows up in my recovery options.
```
0	menuentry 'Ubuntu
     1	submenu 'Advanced options for Ubuntu
     2	menuentry 'Ubuntu, with Linux 4.18.0-16-generic
     3	menuentry 'Ubuntu, with Linux 4.18.0-16-generic (recovery mode)
     4	menuentry 'Ubuntu, with Linux 4.18.0-15-generic
     5	menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode)
     6	menuentry 'Ubuntu, with Linux 4.15.0-54-generic
     7	menuentry 'Ubuntu, with Linux 4.15.0-54-generic (recovery mode)
```

I ran "sudo update autoremove" but 4.15.0-54 remains.
Why do I have this kernel?

---

### Post by Bashing-om on 2019-06-28
guber2; Hey !

Looks as if you have 2 things at play here.
1) is that the original generic kernel meta-package from 18.04/.1 is still in effect
2) the updated HWE from 18.04.2 is also in effect. 
No harm in keeping both but what series do you want to use ?

Post back:
```

dpkg -l | grep linux-

```
to confirm this suspicion.

[INDENT][INDENT]clean and lean ?
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-28
Hi Bashing-om,
Your wishes obeyed....
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -l | grep linux-**
ii  binutils-x86-64-linux-gnu              2.30-21ubuntu1~18.04.2                     amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                             4.5ubuntu1                                 all          Linux image base package
ii  linux-firmware                         1.173.6                                    all          Firmware for Linux kernel drivers
ii  linux-generic                          4.15.0.54.56                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-54                4.15.0-54.58                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-15                4.18.0-15.16~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-15-generic        4.18.0-15.16~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-16                4.18.0-16.17~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-16-generic        4.18.0-16.17~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.15.0.54.56                               amd64        Generic Linux kernel headers
rc  linux-image-4.15.0-20-generic          4.15.0-20.21                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-22-generic          4.15.0-22.24                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-23-generic          4.15.0-23.25                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-24-generic          4.15.0-24.26                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-29-generic          4.15.0-29.31                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-30-generic          4.15.0-30.32                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-32-generic          4.15.0-32.35                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-33-generic          4.15.0-33.36                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-34-generic          4.15.0-34.37                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-36-generic          4.15.0-36.39                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-38-generic          4.15.0-38.41                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-39-generic          4.15.0-39.42                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-42-generic          4.15.0-42.45                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-43-generic          4.15.0-43.46                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-44-generic          4.15.0-44.47                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-45-generic          4.15.0-45.48                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-46-generic          4.15.0-46.49                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-47-generic          4.15.0-47.50                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-48-generic          4.15.0-48.51                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-50-generic          4.15.0-50.54                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-51-generic          4.15.0-51.55                               amd64        Signed kernel image generic
rc  linux-image-4.15.0-52-generic          4.15.0-52.56                               amd64        Signed kernel image generic
ii  linux-image-4.15.0-54-generic          4.15.0-54.58                               amd64        Signed kernel image generic
ii  linux-image-4.18.0-15-generic          4.18.0-15.16~18.04.1                       amd64        Signed kernel image generic
ii  linux-image-4.18.0-16-generic          4.18.0-16.17~18.04.1                       amd64        Signed kernel image generic
ii  linux-image-generic                    4.15.0.54.56                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.15.0-54.58                               amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-20-generic        4.15.0-20.21                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-22-generic        4.15.0-22.24                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-23-generic        4.15.0-23.25                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-24-generic        4.15.0-24.26                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-29-generic        4.15.0-29.31                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-30-generic        4.15.0-30.32                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-32-generic        4.15.0-32.35                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-33-generic        4.15.0-33.36                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-34-generic        4.15.0-34.37                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-36-generic        4.15.0-36.39                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-38-generic        4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-39-generic        4.15.0-39.42                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-42-generic        4.15.0-42.45                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-43-generic        4.15.0-43.46                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-44-generic        4.15.0-44.47                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-45-generic        4.15.0-45.48                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-46-generic        4.15.0-46.49                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-47-generic        4.15.0-47.50                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-48-generic        4.15.0-48.51                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-50-generic        4.15.0-50.54                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-51-generic        4.15.0-51.55                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-52-generic        4.15.0-52.56                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.18.0-15-generic        4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-4.18.0-16-generic        4.18.0-16.17~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-20-generic  4.15.0-20.21                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-22-generic  4.15.0-22.24                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-23-generic  4.15.0-23.25                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-24-generic  4.15.0-24.26                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-29-generic  4.15.0-29.31                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-30-generic  4.15.0-30.32                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-32-generic  4.15.0-32.35                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-33-generic  4.15.0-33.36                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-34-generic  4.15.0-34.37                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-36-generic  4.15.0-36.39                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-38-generic  4.15.0-38.41                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-39-generic  4.15.0-39.42                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-42-generic  4.15.0-42.45                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-43-generic  4.15.0-43.46                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-44-generic  4.15.0-44.47                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-45-generic  4.15.0-45.48                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-46-generic  4.15.0-46.49                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-47-generic  4.15.0-47.50                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-48-generic  4.15.0-48.51                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-50-generic  4.15.0-50.54                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-51-generic  4.15.0-51.55                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-52-generic  4.15.0-52.56                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-54-generic  4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.18.0-15-generic  4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.18.0-16-generic  4.18.0-16.17~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
```

---

### Post by Bashing-om on 2019-06-28
guber2; Well !

I had expected to see " linux-generic-hwe-18.04" that would have pulled in the 4.18 series kernels.
In addition to the standard "ii  linux-generic".
As I do not see HWE, tell me - how did you install that 4.18.0-15-generic kernel ?

In the meantime, how about we get rid of all that 'rc' ( removed but config files remain) cruft ?
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

We do this way because while there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed; workie great last for some time :)

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-28
I don't know how.
I only vaguely understand hwe,point releases and kernels and I don't think I installed the HWE stack.
Not something I normally worry about.
I only have a xubuntu-18.04-desktop-amd64.iso but I also have a mini.iso.
Thinking back this may have been a net install where I chose xubuntu-desktop during the install.
Maybe that explains it?
Now...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -l | grep linux-**
ii  binutils-x86-64-linux-gnu              2.30-21ubuntu1~18.04.2                     amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                             4.5ubuntu1                                 all          Linux image base package
ii  linux-firmware                         1.173.6                                    all          Firmware for Linux kernel drivers
ii  linux-generic                          4.15.0.54.56                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-54                4.15.0-54.58                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-15                4.18.0-15.16~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-15-generic        4.18.0-15.16~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-16                4.18.0-16.17~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-16-generic        4.18.0-16.17~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.15.0.54.56                               amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-54-generic          4.15.0-54.58                               amd64        Signed kernel image generic
ii  linux-image-4.18.0-15-generic          4.18.0-15.16~18.04.1                       amd64        Signed kernel image generic
ii  linux-image-4.18.0-16-generic          4.18.0-16.17~18.04.1                       amd64        Signed kernel image generic
ii  linux-image-generic                    4.15.0.54.56                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.15.0-54.58                               amd64        Linux Kernel Headers for development
pc  linux-modules-4.15.0-23-generic        4.15.0-23.25                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.18.0-15-generic        4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-4.18.0-16-generic        4.18.0-16.17~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-54-generic  4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.18.0-15-generic  4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.18.0-16-generic  4.18.0-16.17~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
```

---

### Post by Bashing-om on 2019-06-28
guber2; Humm ..

Well, is there a reason you desire the newer kernel ?
As an aside - I have no need of anything offered by HWE and I choose to remain on the original 4.15.0-54-generic series.
> 
sysop@x1804mini:~$ uname -r
4.15.0-54-generic
sysop@x1804mini:~$

Now, maybe in all that cruft I could have missed something.

show us a new
```

dpkg -l | grep linux-

```
and then advise us as to which kernel path you want to follow 4.15 or 4.18 ?
The Ubuntu LTS enablement stacks provide newer kernel and X support for existing LTS releases, see 
               [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
If you do not have HWE enabled then there will be no support for the 4.18 series kernels.
If 4.18  is your choice, we can fix that :)

[INDENT]we do as you desire[/INDENT]

---

### Post by again? on 2019-06-28
I updated previous post.
Would rather use 4.15

---

### Post by Bashing-om on 2019-06-28
guber2; Ho kay.

What is the booting kernel at this time:
```

uname -r

```

and we have that dangling 'pc' module to cope with.

what results:
```

sudo rm linux-modules-4.15.0-23-generic
sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```
as we get ready to remove the .18 kernel :)

[INDENT]I bet we can do that
[/INDENT]

---

### Post by again? on 2019-06-29
Commandments...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] uname -r**
4.18.0-16-generic
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo rm linux-modules-4.15.0-23-generic**
[sudo] password for glen:         
rm: cannot remove 'linux-modules-4.15.0-23-generic': No such file or directory
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt update**
Hit:1 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic InRelease
Get:2 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates InRelease [88.7 kB]                          
Get:3 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-backports InRelease [74.6 kB]                                   
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]         
Get:5 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:6 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/main i386 Packages [554 kB]                    
Get:7 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/main amd64 Packages [676 kB]         
Get:8 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [283 kB]
Get:9 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/main DEP-11 48x48 Icons [66.7 kB]
Get:10 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/main DEP-11 64x64 Icons [138 kB]
Get:11 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/universe i386 Packages [948 kB]
Get:12 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/universe amd64 Packages [964 kB]
Get:13 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [249 kB]
Get:14 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [198 kB]
Get:15 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [413 kB]
Get:16 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [7,224 B]
Fetched 4,753 kB in 5s (921 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg -C**
The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libglib2.0-0:amd64   GLib library of C routines
```

---

### Post by Bashing-om on 2019-06-29
guber2; Humm ...

Plot thickens - glad I checked :)

what results in taking the package manager's advise:
```

sudo dpkg --configure --pending

```

Now once we have a stable system, we want to install the 4.15.0-52-generic to have a fall back kernel installed.
Then we re-boot into the .54 kernel and purge the .18 kernels.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
I've got a mountain of dreams to climb...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg --configure --pending**
[sudo] password for glen:         
Processing triggers for libglib2.0-0:amd64 (2.56.4-0ubuntu0.18.04.3) ...
```

---

### Post by Bashing-om on 2019-06-29
guber2; Ho Kay :)

Just because I like backup plans, we install the -52 version of the kernel:
```

sudo apt install linux-{image,headers,modules}-4.15.0-32-generic {,extra}

```

When that completes, reboot to the 4.15.0-54-generic kernel and we purge :)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
Done and done...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] uname -r**
4.15.0-54-generic
```

---

### Post by Bashing-om on 2019-06-29
guber2 : As we move on along -

```

sudo dpkg -P linux-image-4.18.0-{15,16}-generic linux-modules{,-extra}-4.18.0-{15,16}-generic linux-headers-4.18.0-{15,16}{,-generic}

```

And to know that all is sane:
a new
```

dpkg -l | grep linux-

```

And to know that grub is happy happy happy
```

sudo update-grub

```

reboot once more - should boot the 54 version kernel automagically and now show
```

ls -al /vmlinuz* /initrd*

```

See here if we can pat ourselves on the back.

[INDENT][INDENT]maybe :P
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
Oops...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg -P linux-image{,-extra}-4.18.0-{15,16}-generic linux-headers-4.4.0-{15,16}{,-generic}**
[sudo] password for glen:         
dpkg: dependency problems prevent removal of linux-image-4.18.0-15-generic:
 linux-modules-extra-4.18.0-15-generic depends on linux-image-4.18.0-15-generic | linux-image-unsigned-4.18.0-15-generic; however:
  Package linux-image-4.18.0-15-generic is to be removed.
  Package linux-image-unsigned-4.18.0-15-generic is not installed.

dpkg: error processing package linux-image-4.18.0-15-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-4.18.0-16-generic:
 linux-modules-extra-4.18.0-16-generic depends on linux-image-4.18.0-16-generic | linux-image-unsigned-4.18.0-16-generic; however:
  Package linux-image-4.18.0-16-generic is to be removed.
  Package linux-image-unsigned-4.18.0-16-generic is not installed.

dpkg: error processing package linux-image-4.18.0-16-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-extra-4.18.0-15-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-extra-4.18.0-16-generic which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-15 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-15-generic which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-16 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-16-generic which isn't installed
Errors were encountered while processing:
 linux-image-4.18.0-15-generic
 linux-image-4.18.0-16-generic
```

---

### Post by Bashing-om on 2019-06-29
guber2; Naw -

Just thoughtless on my part - not keeping up with the time as they are achanging.

Try as:
```

sudo dpkg -P linux-image-4.18.0-{15,16}-generic linux-modules{,-extra}-4.18.0-{15,16}-generic linux-headers-4.18.0-{15,16}{,-generic}

```

the "extra modules" package is no longer named linux-image-extra-xxx but linux-modules-extra-xxx, !

[INDENT][INDENT]see how this flies
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
lt'll shine when it shines...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg -P linux-image-4.18.0-{15,16}-generic linux-modules{,-extra}-4.18.0-{15,16}-generic linux-headers-4.4.0-{15,16}{,-generic}**
[sudo] password for glen:         
(Reading database ... 437929 files and directories currently installed.)
Removing linux-modules-extra-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
Purging configuration files for linux-modules-extra-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
Removing linux-modules-extra-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
Purging configuration files for linux-modules-extra-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
dpkg: warning: ignoring request to remove linux-headers-4.4.0-15 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-15-generic which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-16 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-4.4.0-16-generic which isn't installed
Removing linux-image-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
debconf: unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.18.0-15-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found background image: great-bear.png
Found linux image: /boot/vmlinuz-4.18.0-16-generic
Found initrd image: /boot/initrd.img-4.18.0-16-generic
Found linux image: /boot/vmlinuz-4.15.0-54-generic
Found initrd image: /boot/initrd.img-4.15.0-54-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found Ubuntu 19.04 (19.04) on /dev/sda3
Found Ubuntu 18.10 (18.10) on /dev/sdb5
Found Ubuntu 18.04.2 LTS (18.04) on /dev/sdc1
done
Purging configuration files for linux-image-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
rmdir: failed to remove '/lib/modules/4.18.0-15-generic': Directory not empty
Removing linux-image-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
debconf: unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
/etc/kernel/prerm.d/dkms:
dkms: removing: nvidia 390.116 (4.18.0-16-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia
Version: 390.116
Kernel:  4.18.0-16-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.18.0-16-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.18.0-16-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.18.0-16-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.18.0-16-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.18.0-16-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found background image: great-bear.png
Found linux image: /boot/vmlinuz-4.15.0-54-generic
Found initrd image: /boot/initrd.img-4.15.0-54-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found Ubuntu 19.04 (19.04) on /dev/sda3
Found Ubuntu 18.10 (18.10) on /dev/sdb5
Found Ubuntu 18.04.2 LTS (18.04) on /dev/sdc1
done
Purging configuration files for linux-image-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
rmdir: failed to remove '/lib/modules/4.18.0-16-generic': Directory not empty
Removing linux-modules-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
Purging configuration files for linux-modules-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
Removing linux-modules-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
Purging configuration files for linux-modules-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
```

---

### Post by Bashing-om on 2019-06-29
guber2; Ho kay .. look'n good :)

Now as you are multi-booting... which install is your "primary" ?
Do we now need to fudge with grub ?
Nvidia driver ?
I can accept that we will need to re-install it.

what does the system have set for booting ?
show a new:
```

dpkg -l | grep linux-
ls -al /vmlinuz* /initrd*

```

[INDENT][INDENT]no sweat ?
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
All appears good.
This is my main install on my boot disk (sda) and it controls grub.
I have rebooted to default kernel.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -l | grep linux-**
ii  binutils-x86-64-linux-gnu              2.30-21ubuntu1~18.04.2                     amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                             4.5ubuntu1                                 all          Linux image base package
ii  linux-firmware                         1.173.6                                    all          Firmware for Linux kernel drivers
ii  linux-generic                          4.15.0.54.56                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-32                4.15.0-32.35                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic        4.15.0-32.35                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-54                4.15.0-54.58                               all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-15                4.18.0-15.16~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-15-generic        4.18.0-15.16~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-4.18.0-16                4.18.0-16.17~18.04.1                       all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-16-generic        4.18.0-16.17~18.04.1                       amd64        Linux kernel headers for version 4.18.0 on 64 bit x86 SMP
ii  linux-headers-generic                  4.15.0.54.56                               amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-32-generic          4.15.0-32.35                               amd64        Signed kernel image generic
ii  linux-image-4.15.0-54-generic          4.15.0-54.58                               amd64        Signed kernel image generic
ii  linux-image-generic                    4.15.0.54.56                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   4.15.0-54.58                               amd64        Linux Kernel Headers for development
pc  linux-modules-4.15.0-23-generic        4.15.0-23.25                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-32-generic        4.15.0-32.35                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-54-generic        4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-54-generic  4.15.0-54.58                               amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -al /vmlinuz* /initrd***
lrwxrwxrwx 1 root root 33 Jun 29 12:43 /initrd.img -> boot/initrd.img-4.15.0-32-generic
lrwxrwxrwx 1 root root 33 Jun 29 12:43 /initrd.img.old -> boot/initrd.img-4.15.0-54-generic
lrwxrwxrwx 1 root root 30 Jun 29 12:43 /vmlinuz -> boot/vmlinuz-4.15.0-32-generic
lrwxrwxrwx 1 root root 30 Jun 29 12:43 /vmlinuz.old -> boot/vmlinuz-4.15.0-54-generic
```

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] uname -r**
4.15.0-54-generic
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl**
     [COLOR="#0000CD"]1	menuentry 'Ubuntu
     2	submenu 'Advanced options for Ubuntu
     3	menuentry 'Ubuntu, with Linux 4.15.0-54-generic
     4	menuentry 'Ubuntu, with Linux 4.15.0-54-generic (recovery mode)
     5	menuentry 'Ubuntu, with Linux 4.15.0-32-generic
     6	menuentry 'Ubuntu, with Linux 4.15.0-32-generic (recovery mode)[/COLOR]
     7	menuentry 'Ubuntu 19.04 (19.04) (on /dev/sda3)
     8	submenu 'Advanced options for Ubuntu 19.04 (19.04) (on /dev/sda3)
     9	menuentry 'Ubuntu (on /dev/sda3)
    10	menuentry 'Ubuntu, with Linux 5.0.0-17-generic (on /dev/sda3)
    11	menuentry 'Ubuntu, with Linux 5.0.0-17-generic (recovery mode) (on /dev/sda3)
    12	menuentry 'Ubuntu, with Linux 5.0.0-16-generic (on /dev/sda3)
    13	menuentry 'Ubuntu, with Linux 5.0.0-16-generic (recovery mode) (on /dev/sda3)
    14	menuentry 'Ubuntu, with Linux 5.0.0-15-generic (on /dev/sda3)
    15	menuentry 'Ubuntu, with Linux 5.0.0-15-generic (recovery mode) (on /dev/sda3)
    16	menuentry 'Ubuntu, with Linux 5.0.0-13-generic (on /dev/sda3)
    17	menuentry 'Ubuntu, with Linux 5.0.0-13-generic (recovery mode) (on /dev/sda3)
    18	menuentry 'Ubuntu, with Linux 5.0.0-11-generic (on /dev/sda3)
    19	menuentry 'Ubuntu, with Linux 5.0.0-11-generic (recovery mode) (on /dev/sda3)
    20	menuentry 'Ubuntu 18.10 (18.10) (on /dev/sdb5)
    21	submenu 'Advanced options for Ubuntu 18.10 (18.10) (on /dev/sdb5)
    22	menuentry 'Ubuntu (on /dev/sdb5)
    23	menuentry 'Ubuntu, with Linux 4.18.0-17-generic (on /dev/sdb5)
    24	menuentry 'Ubuntu, with Linux 4.18.0-17-generic (recovery mode) (on /dev/sdb5)
    25	menuentry 'Ubuntu, with Linux 4.18.0-15-generic (on /dev/sdb5)
    26	menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode) (on /dev/sdb5)
    27	menuentry 'Ubuntu, with Linux 4.18.0-13-generic (on /dev/sdb5)
    28	menuentry 'Ubuntu, with Linux 4.18.0-13-generic (recovery mode) (on /dev/sdb5)
    29	menuentry 'Ubuntu, with Linux 4.18.0-12-generic (on /dev/sdb5)
    30	menuentry 'Ubuntu, with Linux 4.18.0-12-generic (recovery mode) (on /dev/sdb5)
    31	menuentry 'Ubuntu 18.04.2 LTS (18.04) (on /dev/sdc1)
    32	submenu 'Advanced options for Ubuntu 18.04.2 LTS (18.04) (on /dev/sdc1)
    33	menuentry 'Ubuntu (on /dev/sdc1)
    34	menuentry 'Ubuntu, with Linux 4.15.0-54-generic (on /dev/sdc1)
    35	menuentry 'Ubuntu, with Linux 4.15.0-54-generic (recovery mode) (on /dev/sdc1)
    36	menuentry 'Ubuntu, with Linux 4.15.0-51-generic (on /dev/sdc1)
    37	menuentry 'Ubuntu, with Linux 4.15.0-51-generic (recovery mode) (on /dev/sdc1)
    38	menuentry 'Ubuntu, with Linux 4.15.0-20-generic (on /dev/sdc1)
    39	menuentry 'Ubuntu, with Linux 4.15.0-20-generic (recovery mode) (on /dev/sdc1)
    40	menuentry '     
    41	menuentry '*** ISO FILES ***
    42	menuentry 'Ubuntu 14.04.5 Trusty ISO
    43	menuentry 'Ubuntu Xenial 16.04 ISO
    44	menuentry 'Kubuntu 16.04.2 ISO
    45	menuentry 'Ubuntu 18.04 Bionic ISO
    46	menuentry 'Xubuntu 18.04 ISO
    47	menuentry 'Lubuntu 18.04 ISO
    48	menuentry 'Linuxmint-18-mate ISO
    49	#menuentry 'Ubuntu Disco 19.04 ISO
    50	menuentry 'Ubuntu Disco 19.04 ISO on USB
    51	#menuentry 'BunsenLabs Deuterium Live ISO
    52	#menuentry 'Lubuntu 16.04 ISO
    53	#menuentry 'Elementary-0.4.1 Loki ISO
    54	#menuentry 'Ubuntu mini.iso
    55	#menuentry 'Elementary 0.4 ISO


```

---

### Post by Bashing-om on 2019-06-29
guber2; Hummmm ...

A few things here that do not compute.
1) we removed linux-modules-4.15.0-23-generic - why is it back to haunt us ?
2) we purged the -16 headers - why are they still present ?
Ouch ! I see - A typo on my part, will edit the post,

3) linux-modules-extra-4.15.0-32-generic is missing ; maybe that is why grub has not updated to 4.15.0-54 as primary.

1) Let's try:
```

sudo dpkg -P linux-modules-4.15.0-23-generic

```

2) Let's run
```

sudo dpkg -P linux-headers-4.18.0-{15,16}{,-generic}

```

3) Let's run
```

sudo apt install linux-modules-extra-4.15.0-32-generic

```

[INDENT][INDENT]to err is human
[INDENT][INDENT]but I hate when it happens to me :P\
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
[COLOR="#006400"][/COLOR]I thought I was using 4.15.0-54 but mine is not to reason why....
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg -P linux-modules-4.15.0-23-generic**
[sudo] password for glen:         
(Reading database ... 425359 files and directories currently installed.)
Purging configuration files for linux-modules-4.15.0-23-generic (4.15.0-23.25) ...
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo dpkg -P linux-headers-4.18.0-{15,16}{,-generic}**
(Reading database ... 425358 files and directories currently installed.)
Removing linux-headers-4.18.0-15-generic (4.18.0-15.16~18.04.1) ...
Removing linux-headers-4.18.0-16-generic (4.18.0-16.17~18.04.1) ...
dpkg: warning: while removing linux-headers-4.18.0-16-generic, directory '/lib/modules/4.18.0-16-generic' not empty so not removed
Removing linux-headers-4.18.0-15 (4.18.0-15.16~18.04.1) ...
Removing linux-headers-4.18.0-16 (4.18.0-16.17~18.04.1) ...
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install linux-modules-extra-4.15.0-32-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  linux-modules-extra-4.15.0-32-generic
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 32.7 MB of archives.
After this operation, 171 MB of additional disk space will be used.
Get:1 http://security.ubuntu.com/ubuntu bionic-security/main amd64 linux-modules-extra-4.15.0-32-generic amd64 4.15.0-32.35 [32.7 MB]
Fetched 32.7 MB in 35s (928 kB/s)                                                                                                         
debconf: unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously unselected package linux-modules-extra-4.15.0-32-generic.
(Reading database ... 368518 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-4.15.0-32-generic_4.15.0-32.35_amd64.deb ...
Unpacking linux-modules-extra-4.15.0-32-generic (4.15.0-32.35) ...
Setting up linux-modules-extra-4.15.0-32-generic (4.15.0-32.35) ...
Processing triggers for linux-image-4.15.0-32-generic (4.15.0-32.35) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 4.15.0-32-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-32-generic
/etc/kernel/postinst.d/zz-update-grub:#############################################################################....................] 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found background image: great-bear.png
Found linux image: /boot/vmlinuz-4.15.0-54-generic
Found initrd image: /boot/initrd.img-4.15.0-54-generic
Found linux image: /boot/vmlinuz-4.15.0-32-generic
Found initrd image: /boot/initrd.img-4.15.0-32-generic
Found Ubuntu 19.04 (19.04) on /dev/sda3
Found Ubuntu 18.10 (18.10) on /dev/sdb5
Found Ubuntu 18.04.2 LTS (18.04) on /dev/sdc1
done
```

---

### Post by Bashing-om on 2019-06-29
guber2; Uh HUh :)

Reason why "linux-modules-4.15.0-23-generic" is to complete what I failed on earlier :(

And now I do "think" all is set to go :)

All now
[INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT]

---

### Post by again? on 2019-06-29
Thank you.
You certainly know your stuff.
Appreciate your help and [probably always will]("https://www.youtube.com/watch?v=e4rwXKDe2AQ").

---

### Post by Bashing-om on 2019-06-29
guber2; Oh Garsh -

This is a constant process in learning, I but share what others have taught me.

It's open source
[INDENT][INDENT]we are all in this together
[/INDENT][/INDENT]

---

