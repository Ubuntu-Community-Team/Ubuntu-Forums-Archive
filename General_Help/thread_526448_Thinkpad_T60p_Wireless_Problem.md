---
title: "Thinkpad T60p Wireless Problem"
date: 2007-08-15
forum: General Help
---

### Post by cssutto on 2007-08-15
I have a Thinkpad T60p with the following wireless card:

product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.

The card is in the hardware list with the *network UNCLAIMED comment.

I have searchd the forum and have not found what is to me a useful solution to getting my wireless to work.

I can use the router and am now with the ethernet cable, but I need to go wireless.

I booted into XP and found that it had wireless turned off.  I turned it back on and exited XP.

I understand that it is common for laptops to be shipped with wireless disabled so as to conserve power.

Any help would be appreciated.

---

### Post by moore.bryan on 2007-08-15
*i finally got everything working on my thinkpad z61e working... after a, somewhat, long struggle.  do me a favor and give me the "type" # from a sticker on the bottom of your lappie, so we can check the lenovo site for exact/specific hardware details...*

---

### Post by cssutto on 2007-08-15
Type 2613-CTO

I sure would appreciate it.

I am getting nowhere on my own.

Ethernet cable just will not do.  I move 2 times every single day and sometimes more and dragging all of that cable around and lashing up every time is a pain.

CSSJR

---

### Post by moore.bryan on 2007-08-15
[I]okay, step 1: we're going to install the linux restricted modules
```
sudo aptitude install linux-restricted-modules-`uname -r`
```
and then reboot.

success?[/I]

---

### Post by cssutto on 2007-08-15
Done.

---

### Post by moore.bryan on 2007-08-15
*so, do you have wireless?*

---

### Post by cssutto on 2007-08-15
Wireless assistant says no useable system found.

System > administration > networking shows only modem and etho.

Network connection shows only etho and lo.

---

### Post by cssutto on 2007-08-15
Output of sudo aptitude install linux-restricted-modules-`uname -r`

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
claude69694@claude69694:~$

---

### Post by moore.bryan on 2007-08-15
[I]okay... were you hard-connected when you ran the aptitude command?

step 2: post the output of
```
lspci
iwconfig
```[/I]

---

### Post by cssutto on 2007-08-15
~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71d4
0000:02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
claude69694@claude69694:~$ sudo lspci Password:
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71d4
0000:02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
claude69694@claude69694:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

---

### Post by moore.bryan on 2007-08-15
[I]okay, so we'll go it the long way. :-)

make sure you're connected with your wired connection and install a couple of things:
```
sudo aptitude install build-essential linux-headers-`uname -r` module-assistant madwifi-source madwifi-tools
```

now, we can try to build and install the madwifi drivers for your atheros chipset:
```
sudo m-a prepare && sudo m-a a-i madwifi
```

if you run into any errors, just post them and we can try to tackle it...[/I]

---

### Post by cssutto on 2007-08-15
My ISP is really slow right now.  They are updating, so it will be a long time before the download is done.

And my bride is about to call me to supper, so you may not hear from me for an hour or so.

I sure do appreciate the help.

---

### Post by moore.bryan on 2007-08-15
*no problems... if i'm not here and everything works, a reboot should have you flying.*

---

### Post by cssutto on 2007-08-15
I got this.

What now?


~$ sudo m-a prepare && sudo m-a a-i madwifi
Password:
Getting source for kernel version: 2.6.15-28-686
Kernel headers available in /usr/src/linux-headers-2.6.15-28-686
Creating symlink...

Done!
madwifi, what is madwifi?

---

### Post by cssutto on 2007-08-16
I rebooted and have a "wired network connection" idon on my panel, but there is no way I can get it to say anything about wireless.  I does give me all of the connection info about the wired connection, meaning the etho to my router.

The "what is madwifi" line is a direct quote from the output of the m-a prepare command.

So it could not find something.

Anyway, it appears that we are making progress.

---

### Post by cssutto on 2007-08-16
Sorry, I forgot to include the error message from the first command, which is:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "madwifi-source"
Couldn't find any package whose name or description matched "madwifi-tools"

---

### Post by moore.bryan on 2007-08-16
[I]those errors are what's important!  :-)
have you [enabled extra repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")?  you need them...[/I]

---

### Post by cssutto on 2007-08-16
I looked at that page carefully and could not identify which repository you want me to use.

Most of that is for Fiesty and I am using Dapper 6.06.

---

### Post by moore.bryan on 2007-08-16
[I]that's okay... same premise, just upgrade the dapper repos:
> How to add extra repositories 
Read #General Notes 
You can also add extra repositories using the Synaptic Package Manager. New users may find it more user-friendly to add extra repositories through the Package Manager. If you follow the link above, you do not have follow the rest of this tip. 
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
Replace everything with the following lines 
To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
Save the edited file 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
You may also generate your own sources.list and find other repositories at: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) 
You may also replace your sources.list with this very complete list: sources.list (be sure to replace "it" from "it.archive.ubuntu.com" with your country code) Use at own risk. 
Modify the default Ubuntu sources.list only if you understand what you're doing. Mixing repos can cause breakage.
[/I]

---

### Post by cssutto on 2007-08-17
I loaded the above and got the same results.

Here is my sources file:

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted




## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse






## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


# deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
# deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx





## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## uncomment this one for multimedia packages AFTER having finished the upgrade to Dapper.

## Dapper PLF
## only uncomment it if you need it
## deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
## deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype 
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

#AUTOMATIX REPOS START (appomatix has been removed due to bad reports)


deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by moore.bryan on 2007-08-17
[I]okay... a little digging answered your issue; madwifi isn't in the dapper repos, it's in later releases.  that means we have to fool-around a little.  this might take a little bit, but it'll be worth it when you're wireless!  ;-)

first, download the [madwifi-source]("http://www.bmoore.net/madwifi-source_0.9.3-3_all.deb") and [madwifi-tools]("http://www.bmoore.net/madwifi-tools_0.9.3+dfsg-2_i386.deb") files from my website and install them, posting the errors you get... and you SHOULD get errors.

```
sudo dpkg -i madwifi-source_0.9.3-3_all.deb
sudo dpkg -i madwifi-tools_0.9.3+dfsg-2_i386.deb
```
[/I]

---

### Post by cssutto on 2007-08-17
This what the first command returned:

 sudo dpkg -i madwifi-tools_0.9.3-3_all.deb
Password:
dpkg: error processing madwifi-tools_0.9.3-3_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 madwifi-tools_0.9.3-3_all.deb

---

### Post by moore.bryan on 2007-08-17
*sorry, that should have read "madwifi-source_0.9.3-3_all.deb"*

---

### Post by cssutto on 2007-08-17
sudo dpkg -i madwifi-source_0.9.3-3_all.deb
Password:
dpkg: error processing madwifi-source_0.9.3-3_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 madwifi-source_0.9.3-3_all.deb

---

### Post by moore.bryan on 2007-08-17
*okay... i'm a little confused.  you downloaded [this]("http://www.bmoore.net/madwifi-source_0.9.3-3_all.deb") then typed ```
sudo dpkg -i madwifi-source_0.9.3-3_all.deb
``` and it gives you that error?*

---

### Post by cssutto on 2007-08-17
Idownloaded it just now and it told me that I need madwifi-tools

---

### Post by moore.bryan on 2007-08-17
*that's the other download... make sure that's downloaded and install it...*

---

### Post by cssutto on 2007-08-17
I am not having any luck downloading tools.

If you could please give me a link as you did with the source, I would appreciate it.

---

### Post by moore.bryan on 2007-08-17
[i]
sure.  [here]("http://www.bmoore.net/madwifi-tools_0.9.3+dfsg-2_i386.deb")

right-click the link and choose "save link" or something like that...
[/i]

---

### Post by cssutto on 2007-08-17
Source says that I need dbhelper and tools needs libc6.

Apt-get can not find them.

---

### Post by moore.bryan on 2007-08-17
[I]that's debhelper (in the dapper repos)... ```
sudo aptitude install debhelper libc6 libc6-dev
```

then try to install the packages again...[/I]

---

### Post by cssutto on 2007-08-17
apt-get says that it installed them.

The source/tools download will not install because it still says it needs them.

---

### Post by moore.bryan on 2007-08-17
*it probably needs a specific version... could you copy/paste everything that shows-up on the screen after you try to install?*

---

### Post by cssutto on 2007-08-17
Because of the way my downloader works, I can not copy except to send a print screen and that is not allowable here.

Actually, it gives no information other than what I have already told you.  It will not allow me to attempt an install.  It quits before that point.

---

### Post by moore.bryan on 2007-08-17
*okay... try downloading and installing [this]("http://www.bmoore.net/libc6_2.6-3_i386.deb") libc6 deb.*

---

### Post by cssutto on 2007-08-17
OK , that worked.

Now for dbhelper.

---

### Post by moore.bryan on 2007-08-17
> **cssutto said:**
> OK , that worked.

Now for dbhelper.
*that is "debhelper;" try installing it from the repos...  there's no such thing as "dbhelper" for this...*

---

### Post by cssutto on 2007-08-17
I still get the message that I need debhelper.

Synaptic says that it is installed.  Nevertheless, I did a reinstall using Synaptic.

That did not work.

So I used apt-get install and it said that I have the latest and goodbye.

So????

---

### Post by moore.bryan on 2007-08-17
*no worries... download [this]("http://mirrors.kernel.org/ubuntu/pool/main/d/debhelper/debhelper_5.0.42ubuntu1_all.deb") version and let's see what it gives us...*

---

### Post by cssutto on 2007-08-17
You will not believe this.

I can not install this because it says dpkg-dev is required.

Syhaptic says that I have it installed.

---

### Post by moore.bryan on 2007-08-17
[I]i told you this was going to be a quest!  ;-)
download and install [this]("http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb") deb...[/I]

---

### Post by cssutto on 2007-08-18
That says that I need dpkg.

Synaptic says I have it.

By the way, I do have one problem with one of the repositories, whether it is part of this problem I have no idea.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Is not accessable for some reason.

---

### Post by moore.bryan on 2007-08-18
[I]let's try this... i've attached a dapper sources.list; let's try and replace yours with this one.  download the attachment, rename it, back-up your sources.list, and then replace:
```
sudo mv sources.list.txt sources.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo mv sources.list /etc/apt/sources.list
sudo aptitude update && sudo aptitude upgrade
``` [/I]

---

### Post by cssutto on 2007-08-18
That command gets this error, but as you can see, locate shows the file exists and in etc.

claude69694@claude69694:~$ sudo mv sources.list /etc/apt/sources.list
mv: cannot stat `sources.list': No such file or directory
claude69694@claude69694:~$ whereis sources.list
sources:
claude69694@claude69694:~$ locate sources.list
/etc/apt/sources.list.d
/etc/apt/sources.list
/etc/apt/sources.list_backup_200701072137
/etc/apt/sources.list_backup_200701081048
/etc/apt/sources.list_backup_200701111005
/etc/apt/sources.list.save
/etc/apt/sources.list_backup_200701111040
/etc/apt/sources.list_backup_200701242351
/etc/apt/sources.list_backup_200701262158
/etc/apt/sources.list_backup_200703130910
/etc/apt/sources.list_backup_200703222245
/etc/apt/sources.list_backup_200704141634
/etc/apt/sources.list_backup_200704200829
/etc/apt/sources.list_backup_200706100941
/etc/apt/sources.list_backup_200706111359
/etc/apt/sources.list_backup_200706121909
/etc/apt/sources.list_backup_200706131037
/etc/apt/sources.list_backup_200706211723
/etc/apt/sources.list~
/etc/apt/sources.list_backup_200707060840
/usr/share/doc/apt/examples/sources.list
/usr/share/man/es/man5/sources.list.5.gz
/usr/share/man/fr/man5/sources.list.5.gz
/usr/share/man/man5/sources.list.5.gz
/usr/share/ubuntu-docs/ubuntu/serverguide/sample/sources.list

---

### Post by moore.bryan on 2007-08-18
> **cssutto said:**
> That command gets this error, but as you can see, locate shows the file exists and in etc.
```
claude69694@claude69694:~$ sudo mv sources.list /etc/apt/sources.list
mv: cannot stat `sources.list': No such file or directory

```
[i]
so, when you downloaded the sources.list.txt file, where did you put it?  that error's saying it's not in your home folder.  when you renamed the file (i.e. sudo mv sources.list.txt sources.list), were there any errors?
[/i]

---

### Post by cssutto on 2007-08-18
Exuse that last post.

I figured it out.

---

### Post by cssutto on 2007-08-18
udo aptitude update && sudo aptitude upgrade

That command lists lots of fiesty files.

I am running dapper.

I hop that is not going to cause a huge crash

---

### Post by moore.bryan on 2007-08-18
[I]none of the files should be feisty... i rewrote the sources.list for all dapper stuff.  go into it and double-check the right one was copied:
```
gedit /etc/apt/sources.list
```[/I]

---

### Post by cssutto on 2007-08-18
## BASE
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## UPDATES
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## BACKPORTS
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

---

### Post by moore.bryan on 2007-08-18
*i don't know how/why it's like that... either download the on on the post right above here or just change all the feisty to dapper.*

---

### Post by cssutto on 2007-08-18
OK, list installed, apt thing done.

Now do I not have to do apt-update before I go back to the attempt to install stuff?

I have some outside work to do in the next hours, so this will be the last post for a while.

---

### Post by moore.bryan on 2007-08-18
[I]still do the ```
sudo aptitude update && sudo aptitude upgrade
```
then we'll go from there....

enjoy the big bad world.[/I]

---

### Post by cssutto on 2007-08-18
I did that.

It appears that it worked.

---

### Post by moore.bryan on 2007-08-18
*okay, try installing the madwifi source...*

---

### Post by cssutto on 2007-08-18
I got this:

dpkg: error processing madwifi-source_0.9.3-3_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 madwifi-source_0.9.3-3_all.deb

---

### Post by moore.bryan on 2007-08-18
*you need to find the folder/directory in which you saved the madwifi .deb and _then_ run ```
sudo dpkg -i madwifi-source_0.9.3-3_all.deb
```*

---

### Post by cssutto on 2007-08-18
I don't think I was ever successful in downloading it because every attempt resulted in the error message that I needed another file.

---

### Post by moore.bryan on 2007-08-18
*okay... just download it from the debian mirror [here]("http://http.us.debian.org/debian/pool/non-free/m/madwifi/madwifi-source_0.9.3-3_all.deb") and install it.*

---

### Post by cssutto on 2007-08-18
It said the same thing:

"Dependancy not satisfied: dbhelper

---

### Post by cssutto on 2007-08-18
Sorry.  debhelper

---

### Post by moore.bryan on 2007-08-19
*```
sudo aptitude install debhelper
```... if that doesn't work, download the .deb from [here]("http://http.us.debian.org/debian/pool/main/d/debhelper/debhelper_5.0.53_all.deb") and install it.*

---

### Post by cssutto on 2007-08-19
Same old thing.

"dependancy not satisfiable: dpkg-dev"

---

### Post by moore.bryan on 2007-08-19
[I]get that .deb [here]("http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg-dev_1.14.5_all.deb")

are you having fun yet?
;-)[/I]

---

### Post by cssutto on 2007-08-19
That got me another dpkg needed.

My fun is not the question.

The question is: When do you get fed up with my problem.

The Ubuntu people should have their butts kicked.  Wireless is such a big thing and was a big thing with a lot of people when 6.06 was released that leaving it out or releasing it with such difficulties is inexcusable and is bound to hurt the acceptance of linux as a real OS rather than a game for technos.

---

### Post by moore.bryan on 2007-08-19
> **cssutto said:**
> That got me another dpkg needed.
*okay... that probably means your dpkg is outdated compared to the one debhelper is asking for.  try installing [this one]("http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.14.5_i386.deb")...*
> The question is: When do you get fed up with my problem.
*never... that's why i'm here.  :-)*
> The Ubuntu people should have their butts kicked.  Wireless is such a big thing and was a big thing with a lot of people when 6.06 was released that leaving it out or releasing it with such difficulties is inexcusable and is bound to hurt the acceptance of linux as a real OS rather than a game for technos.
[i]there are times i quite agree with you and i thought much the same not that long ago, but i'm realizing more and more those who make the hardware so it only works with microsoft are the one truly making it difficult for us ubuntu-ers.  although 6.06 is the stable, long-term support (lts) release, some of the more recent releases (i.e. fiesty) are infinitely superior because of the developmental support they receive.  now, that is only my opinion, but one i think is shared by many floating around these fora.  

whenever one upgrades to "extraordinary" packages, there's going to be a lot of downloading.  don't ask me how long it took me to get iceweasel running on edgy!
;-)[/i]

---

### Post by cssutto on 2007-08-19
This is my last post for the evening.

I will be gone until tomorrow afternoon.

But one short question:  Should I update to fiesty?

I dread it because I just now have 6.06 where I want it except for wireless.

How I dread having to go through all of that again to get my Epson Scanner and DVD's and other stuff working.

---

### Post by moore.bryan on 2007-08-20
> **cssutto said:**
> But one short question:  Should I update to fiesty?
[i]
there are inumerable posts here which ask that very question and, much like the journey on which we are currently, there is no easy answer; sorry.  here's one way to look at it: although 6.06 (dapper drake) is the lts release, there have been **two stable** releases since; namely, 6.10 (edgy eft) and 7.04 (feisty fawn).  and, to boot, 7.10 (gutsy gibbon) will be out on 18 october 2007 for stable release.  if you're not a corporate user, which i don't think you are, then upgrading would be my suggestion.
[/i]
> I dread it because I just now have 6.06 where I want it except for wireless.

How I dread having to go through all of that again to get my Epson Scanner and DVD's and other stuff working.
[i]
i hear you there... i'd suggest you download the [newest iso]("http://www.ubuntu.com/getubuntu/download") and run the live cd to make sure everything works how you want it.  many of the peripherals people use under older releases after tireless hours of work, "just plain work" under more recent ones.
[/i]

---

### Post by moore.bryan on 2007-08-24
*just checking in on you... did everything work itself out?*

---

