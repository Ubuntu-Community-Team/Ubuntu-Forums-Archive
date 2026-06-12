---
title: "trying to install hardinfo"
date: 2023-10-27
forum: General Help
---

### Post by jgw on 2023-10-27
I am trying to install a program called hardinfo.  Its a program that reports info about the computer.  When I tried I got:

```
sudo apt install hardinfo -y
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 zlib1g-dev : Depends: zlib1g (= 1:1.2.11.dfsg-2ubuntu9) but 1:1.2.11.dfsg-2ubuntu9.2 is to be installed
              Depends: libc6-dev but it is not going to be installed or
                       libc-dev
E: Unable to correct problems, you have held broken packages.

```

I have tried everything I could think of and failed.

I did a search here and found somebody who had exactly the same problem.  They seemed to have got past this.  I tried the exact stuff that he did and it did not fix my problem.  This seems to be a real stinker.

Thoughts?

---

### Post by sudodus on 2023-10-27
- Which version of Ubuntu are you running? 22.04.x LTS or some other version? Please check with

```

lsb_release -a

```

- Have you installed some 'special program', for example via ppa?

- It is also possible that **[FONT=Courier New]hardinfo[/FONT]** is no longer maintained. I remember that it was used in Lubuntu 'some versions ago'.

In my 22.04.3 LTS:
```

$ apt-cache policy hardinfo
hardinfo:
  Installerad: (ingen)
  Kandidat:    0.5.1+git20180227-2.1build1
  Versionstabell:
     0.5.1+git20180227-2.1build1 500
        500 http://se.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
indicates that the version in the repository is more than 5 years old (dated Feb 27 2018).

You might find a newer version at **github**: [https://github.com/lpereira/hardinfo](https://github.com/lpereira/hardinfo).

[hr][/hr]
Edit: alternative tools:

Ubuntu comes with **[FONT=Courier New]lshw[/FONT]**.
```

sudo lshw | less

```
You can download/install [the **[FONT=Courier New]system-info[/FONT]** script by Ubuntu Forums](https://github.com/UbuntuForums/system-info/) and get a lot of information about your system (both hardware and software).

---

### Post by TheFu on 2023-10-27
**inxi** is an alternative as well.

---

### Post by MAFoElffen on 2023-10-27
+1 to sudodus'es answer, but I may be bias'ed. 

I'm the author and sudodus was a major contributor to the project. TheFu was involved, and I picked his brain a lot on some ideas. I still bounce ideas off both of them.

We started by using 'inxi' as a go between to gather some information, but found some things while doing that. I felt we could just go directly to get things, so that people didn't have to install extras to get that information, besides using the basic Linux tool set, and the sysfs that are already there on a basic system. I tuned it to keep the resources down during the script process. Why? because it is a tool that is geared towards gathering information on what might be suspected as compromised or crippled systems. I think it turned out well.

---

### Post by TheFu on 2023-10-27
> **MAFoElffen said:**
> +1 to sudodus'es answer, but I may be bias'ed. 

I'm the author and sudodus was a major contributor to the project. TheFu was involved, and I picked his brain a lot on some ideas. I still bounce ideas off both of them.

We started by using 'inxi' as a go between to gather some information, but found some things while doing that. I felt we could just go directly to get things, so that people didn't have to install extras to get that information, besides using the basic Linux tool set, and the sysfs that are already there on a basic system. I tuned it to keep the resources down during the script process. Why? because it is a tool that is geared towards gathering information on suspected already compromised systems. I think it turned out well.

I think of **system-info** is a great source for gathering troubleshooting data, but often I just need an overview of the system and drivers.  Neither are installed by default in Ubuntu and sometimes I don't want to send someone to install and run a script though this one is really easy.   

I like the consistency of the inxi output. In 1 page, it is amazing the provided information when I don't need 20 pgs of information like to troubleshoot boot issues would require.

---

### Post by deadflowr on 2023-10-28
What does 
```
apt policy zlib1g-dev
```
show?

Double check that the system is up-to-date and no issues are arising from running updates.

---

### Post by jgw on 2023-10-28
Thanks for the reply.......

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy

Hardinfo is still there.  I think you can even install it with snap (when you have all the stuff it needs)

---

### Post by jgw on 2023-10-28
TheFu - Thank you for the reply......

inxi not quite what I wanted.  I was trying to figure out who made my computer (not paying to boot stuff and it flies by)  I knew hardinfo gave that information.  I really don't use it much anymore but not being able to install it was a little offputting.  Oh, same with system-info (at least I couldn't find it).  Kinda makes sense - kinda embarrassing, not knowing who built your computer.  

I'm calling this one solved.  Its not but I really don't need it so I give up.

---

### Post by sudodus on 2023-10-28
The **[FONT=Courier New]system-info[/FONT]** script is not in the Ubuntu repositories. But you can install it via a ppa or by downloading and extracting from a zipfile that you can get from github. See the following link

[https://github.com/UbuntuForums/system-info/](https://github.com/UbuntuForums/system-info/)

Scroll down to read the instructions.

---

### Post by deadflowr on 2023-10-28
You should still try to solve whatever issues you are having with installing zlib1g-dev as that's a very common package and it coming up as uninstallable is problematic.
And it's not an Ubuntu problem, it's a your system problem.

---

### Post by TheFu on 2023-10-28
There's not way to ensure what the vendor is, but in the motherboard will usually provide some details.
**sudo inxi -Mxx **

Also **lshw |less ** will have it right at the top, if not in the exact format.

Some examples from 1 of my systems:
```
$ sudo inxi -Mxx
Machine:
  Type: Desktop Mobo: **ASUSTeK** model: [B]ROG STRIX B450-F GAMING v: Rev 1.xx 
[/B]  serial: 18073206xxxxxxx UEFI: **American Megatrends v: 5003 date: 02/03/2023** 

hadar                       
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=94E2DD6A-478A-37E2-E2FE-0C9D9287CE13
  *-core
       description: Motherboard
       product: **ROG STRIX B450-F GAMING**
       vendor: [B]ASUSTeK COMPUTER INC.
[/B]       physical id: 0
       version: [B]Rev 1.xx
[/B]       serial: 18073206xxxxxxx
       slot: Default string
     *-firmware
          description: BIOS
          vendor: **American Megatrends Inc**.
          physical id: 0
          version: **5003**
          date: **02/03/2023**
....
```

Basically, most O.E.M.s don't fill in all the data. It is optional.  Perhaps the huge boys like Lenovo, Dell, HP, Apple will complete that data. Who knows?

The only thing I changed in the output above was the serial number.  Everything else is copy/pasted.  With inxi, I could provide the -z switch to have it mask the serial number ... it looks like this:
```
$ sudo inxi -Mxxz
Machine:
  Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx 
  serial: <filter> UEFI: American Megatrends v: 5003 date: 02/03/2023 

```
using sudo really isn't needed 99.99% of the time.  I find that **inxi** provides the information in a compressed, but readable manner. Basically, what I want to know, without all the junk.

---

### Post by MAFoElffen on 2023-10-28
Or where 'inxi' get's that information:
```

mafoelffen@Mikes-B460M:~$ sudo dmidecode -t 0,1
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: F2
    Release Date: 08/28/2020
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.17

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: B460M DS3H AC-Y1
    Version: Default string
    Serial Number: Default string
    UUID: 03c00218-044d-053f-4d06-d50700080009
    Wake-up Type: Power Switch
    SKU Number: Default string
    Family: B460 MB

```

---

### Post by jgw on 2023-10-28
I don't want to get it as I have it.  You can also update it pretty easy, as well.  system-info -r should do the trick.

---

### Post by jgw on 2023-10-28
deadflowr:

greg@greg-System-Product-Name:~$ apt policy zlib1g-dev
zlib1g-dev:
  Installed: (none)
  Candidate: 1:1.2.11.dfsg-2ubuntu9
  Version table:
     1:1.2.11.dfsg-2ubuntu9 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
I have a good zlib1g file its this one that I cannot get and that has something to do with something else which also has something to do with something else.  This gets a bit tiresome.  However, that being said, I have installed hardinfo several times, over the years, I am just going to give it all a little time before I try and download it as I don't need it right now and I have found that, over time, a lot of stuff like this heals itself and I am in no hurry on this one.  There is, over time, also a chance that somebody will figure it out with a simple solution (which also actually happens over time).

Oh, one other thing, I am also pretty lazy...........

---

### Post by deadflowr on 2023-10-28
Ah, you have -updates and -security repos turned off.
They need to be on.

---

### Post by jgw on 2023-10-28
deadflowr;

I thought I had replied but, I guess not so:

How do I turn them on?

---

### Post by deadflowr on 2023-10-28
What do your sources.list look like right now?
post the output from
```
tac /etc/apt/sources.list
```

Also,
You should be able to enable the repos in Software and Updates > Updates tab and set "Subscribe to:" to All Updates.

---

### Post by jgw on 2023-10-28
Went to software and updates.  I am subscribed to all updates.  All security updates are automatically downloaded and installed.   Given I have changed nothing seems I had them both covered?

```
 tac /etc/apt/sources.list
# see the sources.list(5) manual.
# For information about how to configure apt package sources,
# entries were disabled at the end of the installation process.
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# This system was installed using small removable media

# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security main restricted

# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
## or updates from the Ubuntu security team.
## Also, please note that software in backports WILL NOT receive any review
## newer versions of some applications which may provide useful features.
## extensively as that contained in the main release, although it includes
## N.B. software from this repository may not have been tested as

# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
## security team.
## multiverse WILL NOT receive any review or updates from the Ubuntu
## your rights to use the software. Also, please note that software in 
## team, and may not be under a free licence. Please satisfy yourself as to 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
## review or updates from the Ubuntu security team.
## team. Also, please note that software in universe WILL NOT receive any
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
## distribution.
## Major bug fix updates produced after the final release of the

# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
# newer versions of the distribution.
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# deb cdrom:[Ubuntu 22.04.3 LTS _Jammy Jellyfish_ - Release amd64 (20230807.2)]/ jammy main restricted

```

---

### Post by deadflowr on 2023-10-28
run
```
sudo apt update
apt policy zlib1g-dev
```

This is what it should be showing:
```
zlib1g-dev:
  Installed: 1:1.2.11.dfsg-2ubuntu9.2
  Candidate: 1:1.2.11.dfsg-2ubuntu9.2
  Version table:
 *** 1:1.2.11.dfsg-2ubuntu9.2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:1.2.11.dfsg-2ubuntu9 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```
or in your case, Installed: will be none, since it not installed for you.

---

### Post by MAFoElffen on 2023-10-28
@deadflowr -- 
I totally agreed and think you are on the right track.

I am confused by what this error means:
```

 zlib1g-dev : Depends: zlib1g (= [COLOR=#ff0000]1:1.2.11.dfsg-2ubuntu9[/COLOR]) but 1:1.2.11.dfsg-2ubuntu9.2 is to be installed

```
I've looked at that 5 times. Are my eyes lying to me? That is not the depends for that package...

For jammy, i just did
```

sudo apt download hardinfo

```
It downloaded file: hardinfo_0.5.1+git20180227-2.1build1_amd64.deb

I extracted it to get to the control file in the .deb package
```

Package: hardinfo
Version: 0.5.1+git20180227-2.1build1
Architecture: amd64
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Simon Quigley <tsimonq2@debian.org>
Installed-Size: 879
[COLOR=#ff0000]Depends: pciutils (>= 1:2.1.11-10), zlib1g-dev, libc6 (>= 2.34), libgdk-pixbuf-2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.43.2), libgtk2.0-0 (>= 2.18.0), libpango-1.0-0 (>= 1.14.0)[/COLOR]
Recommends: lm-sensors
Suggests: mesa-utils
Section: x11
Priority: optional
Homepage: http://hardinfo.org
Description: Displays system information
 HardInfo is a small application that displays information about your
 hardware and operating system. Currently it knows about PCI, ISA PnP, USB,
 IDE, SCSI, Serial and parallel port devices.

```
Then I downloaded zlib1g-dev. The file was: zlib1g-dev_1%3a1.2.11.dfsg-2ubuntu9.2_amd64.deb
```

Package: zlib1g-dev
Source: zlib
Version: 1:1.2.11.dfsg-2ubuntu9.2
Architecture: amd64
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 592
[COLOR=#ff0000] Depends: zlib1g (= 1:1.2.11.dfsg-2ubuntu9.2), libc6-dev | libc-dev[/COLOR]
Conflicts: zlib1-dev
Provides: libz-dev
Section: libdevel
Priority: optional
Multi-Arch: same
Homepage: http://zlib.net/
Description: compression library - development
 zlib is a library implementing the deflate compression method found
 in gzip and PKZIP.  This package includes the development support
 files.
Original-Maintainer: Mark Brown <broonie@debian.org>

```
So it works, but is different from the error you are getting...

zlib1g 1:1.2.11.dfsg-2ubuntu9.2 is the current package and that is what zlib1g-dev is asking for...

Which brings up the path deadflowr is asking about: Where did his package come from, that is somehow "different" than what it should be?

---

### Post by sy41fox on 2023-10-28
To MAfoElffen! Can you walk me through how to do a Ubuntu 23.10 TPM backed FDE encryption on a Lenovo IdeaPad 3 i3 currently on Windows 11 Home. Pay attention to the Windows 11 Home detail. Is this possible to do, or would I fare better with choosing a FDE encryption with Veracrypt? And how do I then get the TPM keys manually signed? What I need is a step by step setup manual from you. You can also reach me at : [email]stoltzc1976@hotmail.com[/email]

---

### Post by jgw on 2023-10-28
From what I can tell it all has to do with some of the files involved are updated and some are not and its confusing the entire works.  This is one of the reasons I backed out for a bit.  Its VERY strange.  When that happens I just run away and wait.  Somebody who knows what to do will arrive and save the day!! (I have faith)

---

### Post by MAFoElffen on 2023-10-28
> **sy41fox said:**
> To MAfoElffen! Can you walk me through how to do a Ubuntu 23.10 TPM backed FDE encryption on a Lenovo IdeaPad 3 i3 currently on Windows 11 Home. Pay attention to the Windows 11 Home detail. Is this possible to do, or would I fare better with choosing a FDE encryption with Veracrypt? And how do I then get the TPM keys manually signed? What I need is a step by step setup manual from you. You can also reach me at : [EMAIL="stoltzc1976@hotmail.com"]stoltzc1976@hotmail.com[/EMAIL]
@deadflowr -- Can you please split out the post from sy41fox into a new thread of it's own in the "Installations & Upgrades" Section, I'll help him there so we do not muddy up this one. Or if easier for you, tell him to start one of his own there himself?

@sy41fox -- Welcome to Ubuntu Forums. Look for that new thread to get moved out to there. I'll help you there. In the future, please note that it is not good "netiquete" to hi-jack a thread with things not related to that thread, and what the original Poster is asking for support on... But to rather start a new thread of your own, where you can get personal attention that relates to your own needs.

---

### Post by jgw on 2023-10-28
I just tried to install hardinfo again for the heck of it.  Before I did that I did (again for the heck of it):
sudo apt update && sudo apt full-upgrade && sudo apt autoremove --purge -y && sudo apt clean

then the hardinfo install and IT WORKED!  I now have hardinfo installed and I have absolutely no idea what it might have done to cause it to happen!  One can only wonder but now, at least, my claim to installation is legal.  

Thanks to everybody involved.  One of you is responsible for my success, maybe even more.  Mysteries abound.

---

### Post by MAFoElffen on 2023-10-28
Yes... It seems that the original install somehow got the older version of zlib1g-dev. 

That could have been caused by doing the apt install, without first doing apt update to update the apt cache, thus ending up with the outdated packages instead of the current ones. But the related calls of that for the depends mixing the versions of those.

That would be my guess at what happened.

Glad everything is fixed for you now!

---

### Post by hwspeedy on 2024-04-02
Hi jgw,

**We have rebooted hardinfo, that has not have any release for >10 years as community edition hardinfo2.**

Please check the web page for github with build instructions and prebuild for most used distros.

[https://hardinfo2.org](https://hardinfo2.org)

Interested in foss, please join the project, thanx.

/hwspeedy

---

### Post by jgw on 2024-04-02
Interesting........  I have hardinfo up and running on my computers with no problem.  It will be interesting to update it.  In my list of applications its listed as "system profiler and benchmark".  I have been using system-info for a while now. 

Thanks for letting me know!

---

### Post by him610 on 2024-04-02
+inxi

I really like*** inxi***, it has an easy to remember start name.
Have not yet explored all of its options.

---

### Post by jgw on 2024-04-03
I just thought I would add that if you google "how to install hardinfo in 22.04 there are a LOT of offers.  I don't have it installed on this machine but I will check tonight and send the version.

---

### Post by jgw on 2024-04-03
here is the information on my hardinfo:
hardinfo --version
HardInfo version 0.6-alpha
Copyright (C) 2003-2017 Leandro A. F. Pereira. See COPYING for details.

Compile-time options:
  Release version:   Yes (ARCH_x86)
  BinReloc enabled:  Yes
  Data prefix:       /usr/share/hardinfo
  Library prefix:    /usr/lib/x86_64-linux-gnu/hardinfo
  Compiled for:      linux-ARCH_x86
Modules:
File Name            Name            Version     
computer.so          Computer        0.6-alpha   
devices.so           Devices         0.6-alpha   
network.so           Network         0.6-alpha   
benchmark.so         Benchmarks      0.6-alpha

---

