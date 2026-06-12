---
title: "Latest hal update breaks usb stick mounting on kubuntu dapper"
date: 2006-11-22
forum: General Help
---

### Post by hvbakel on 2006-11-22
After updating to the latest hal this morning I could no longer mount USB sticks with kde 3.5.5. Downgrading to the previous version fixed the problem. Was trying to submit a bug in launchpad but I'm having problems trying to find where...

---

### Post by dcstar on 2006-11-22
> **hvbakel said:**
> After updating to the latest hal this morning I could no longer mount USB sticks with kde 3.5.5. Downgrading to the previous version fixed the problem. Was trying to submit a bug in launchpad but I'm having problems trying to find where...

Interesting, I've been experimenting with the 2.6.18 kernel and that has been the result of every kernel I've complied.

---

### Post by bPawn on 2006-11-22
1@#41@3$!@#$12431 I have the same problem ](*,) (I Think) after today's update I cannot automount any usb stick. Of course as root I can mount the device /dev/sdb1 and If I use the vmware my wiblows 2000 VM can see the usbstick

Any Idea on how to fix it? Something about downgrading... how do I do that?

---

### Post by Castar on 2006-11-22
Me too... :neutral:

---

### Post by bPawn on 2006-11-22
just temporarily
make a dir in /media (as root)
and add (as root) in the /etc/fstab :
/dev/sdb1       /media/USBMEMORYSTICK_     vfat     rw,user,noauto,umask=0 0 0

where /dev/sdb1 is MY usb device.
If you plug the device the automount works. This is just a quick hack. The problem IS NOT SOLVED THIS WAY, just a work around

---

### Post by hvbakel on 2006-11-22
I submitted a bug to launchpad about this problem: [#72869]("https://bugz.launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869")

---

### Post by Castar on 2006-11-22
How can I downgrade HAL? :confused:

EDIT: USB sticks are found normally in Gnome....

---

### Post by djSeverin on 2006-11-22
> **Castar said:**
> Me too... :neutral:

*echo*

Same problem. Updated HAL and now device mounts to /dev/sda1, popup appears asking if I want to view in new window, but when Ok is selected, nothing futher happens.

Had to create a new dir and mount sda1 just to get access to the device.

Can someone provide instructions on downgrading HAL?

Cheers

---

### Post by hvbakel on 2006-11-23
There is more than one way to downgrade hal but the method that works for sure is to download the following packages from the ubuntu repository:

[hal_0.5.7-1ubuntu18.1_i386.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.1_i386.deb")
[hal-device-manager_0.5.7-1ubuntu18.1_all.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.1_all.deb")
[hal-doc_0.5.7-1ubuntu18.1_all.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-doc_0.5.7-1ubuntu18.1_all.deb")
[libhal1_0.5.7-1ubuntu18.1_i386.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.1_i386.deb")
[libhal-dev_0.5.7-1ubuntu18.1_i386.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-dev_0.5.7-1ubuntu18.1_i386.deb")
[libhal-storage1_0.5.7-1ubuntu18.1_i386.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.1_i386.deb")
[libhal-storage-dev_0.5.7-1ubuntu18.1_i386.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage-dev_0.5.7-1ubuntu18.1_i386.deb")

After downloading, execute the following command at the location of the downloaded packages:

```
sudo dpkg -i *1ubuntu18.1*.deb
```

And type the password when asked. This will downgrade the packages and USB mounting should work again. Off course, the update notifier will be showing updates again after this, but just ignore those (unless the package version of the updated packages is something like 0.5.7-1ubuntu18.3, which might indicate a fix). If you're still having problems after downgrading, it may be that there are some old hald processes running. Issuing the following commands should fix that:

```
sudo /etc/init.d/dbus stop
sudo killall hald
sudo /etc/init.d/dbus start
```


Hope this helps

---

### Post by Zeddicus on 2006-11-23
...strange.  Downgrading hal isn't fixing this for me. :/

---

### Post by bPawn on 2006-11-23
downgrade causes broken packages:
hal-device-manager
libhal-dev
libhal-storage-dev

and if I apt-get upgrade (after the downgrade):

```

mplampla@mplampla:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  hal-device-manager: Depends: python2.4-gnome2 but it is not installed
                      Depends: python-launchpad-integration but it is not instal                                                                                                   led
                      Depends: hwdb-client but it is not installed
  libhal-dev: Depends: libdbus-1-dev (>= 0.60) but it is not installed
  libhal-storage-dev: Depends: libdbus-1-dev (>= 0.60) but it is not installed
E: Unmet dependencies. Try using -f.

```

ofcourse with the adept updater I upgraded once again...

---

### Post by hvbakel on 2006-11-23
Are you by any chance using Edgy rather than Dapper? The packages listed above are for dapper.

---

### Post by bPawn on 2006-11-23
Using dapper, quite annoying bug... and what strikes me is that only few reported it

---

### Post by hvbakel on 2006-11-23
I guess this problem only exists in kubuntu and then probably only for those that upgraded to the latest kde 3.5.5 version (which has a different way of handling USB mounts). Regarding the packages, I think I just have more hal packages installed. If you restrict yourself to the following list it should install ok:


hal_0.5.7-1ubuntu18.1_i386.deb
hal-doc_0.5.7-1ubuntu18.1_all.deb
libhal1_0.5.7-1ubuntu18.1_i386.deb
libhal-storage1_0.5.7-1ubuntu18.1_i386.deb

---

### Post by shingalated on 2006-11-23
Updates are just evil...if its not broke, I'm not gonna try and fix it.

---

### Post by bPawn on 2006-11-23
> **hvbakel said:**
> I guess this problem only exists in kubuntu and then probably only for those that upgraded to the latest kde 3.5.5 version (which has a different way of handling USB mounts). Regarding the packages, I think I just have more hal packages installed. If you restrict yourself to the following list it should install ok:


hal_0.5.7-1ubuntu18.1_i386.deb
hal-doc_0.5.7-1ubuntu18.1_all.deb
libhal1_0.5.7-1ubuntu18.1_i386.deb
libhal-storage1_0.5.7-1ubuntu18.1_i386.deb

no complains during installation however if apt-get upgrade:


Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libhal-dev: Depends: libhal1 (= 0.5.7-1ubuntu18.2) but 0.5.7-1ubuntu18.1 is installed
  libhal-storage-dev: Depends: libhal-storage1 (= 0.5.7-1ubuntu18.2) but 0.5.7-1ubuntu18.1 is installed
E: Unmet dependencies. Try using -f.

broken packages and the problem remains after downgrade. I will stick to the fstab modification for now

---

### Post by hvbakel on 2006-11-23
I think the following commands should fix your problem:

```

sudo apt-get install libdbus-1-dev
sudo dpkg -i libhal-dev_0.5.7-1ubuntu18.1_i386.deb libhal-storage-dev_0.5.7-1ubuntu18.1_i386.deb
```

---

### Post by bPawn on 2006-11-23
bad luck:

Reading package lists... Done
Building dependency tree... Done
libdbus-1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
blabla@blabla:~/Desktop/HAL_USB$ sudo apt-get install libdbus-1-dev
Reading package lists... Done
Building dependency tree... Done
libdbus-1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kstamos@swengpc3:~/Desktop/HAL_USB$ sudo dpkg -i libhal-dev_0.5.7-1ubuntu18.1_i3
86.deb libhal-storage-dev_0.5.7-1ubuntu18.1_i386.deb
dpkg - warning: downgrading libhal-dev from 0.5.7-1ubuntu18.2 to 0.5.7-1ubuntu18
.1.
(Reading database ... 173359 files and directories currently installed.)
Preparing to replace libhal-dev 0.5.7-1ubuntu18.2 (using libhal-dev_0.5.7-1ubunt                                                                                                   u18.1_i386.deb) ...
Unpacking replacement libhal-dev ...
dpkg - warning: downgrading libhal-storage-dev from 0.5.7-1ubuntu18.2 to 0.5.7-1                                                                                                   ubuntu18.1.
Preparing to replace libhal-storage-dev 0.5.7-1ubuntu18.2 (using libhal-storage-                                                                                                   dev_0.5.7-1ubuntu18.1_i386.deb) ...
Unpacking replacement libhal-storage-dev ...
dpkg: dependency problems prevent configuration of libhal-dev:
 libhal-dev depends on libhal1 (= 0.5.7-1ubuntu18.1); however:
  Version of libhal1 on system is 0.5.7-1ubuntu18.2.
dpkg: error processing libhal-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhal-storage-dev:
 libhal-storage-dev depends on libhal-storage1 (= 0.5.7-1ubuntu18.1); however:
  Version of libhal-storage1 on system is 0.5.7-1ubuntu18.2.
 libhal-storage-dev depends on libhal-dev; however:
  Package libhal-dev is not configured yet.
dpkg: error processing libhal-storage-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libhal-dev
 libhal-storage-dev

---

### Post by dcstar on 2006-11-23
> **bPawn said:**
> Using dapper, quite annoying bug... and what strikes me is that only few reported it

Just out of interest, what type of CPU are all of you experiencing this problem using?

With the 2.6.18 kernel USB problem that I have seen, I believe that I have only seen posts from AMD CPU users.

---

### Post by Zeddicus on 2006-11-24
Intel Pentium M, here.

---

### Post by bPawn on 2006-11-24
uname -a:

Linux WHATEVER 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

and Pentium 4

and Asus P5LD2 mother

---

### Post by hvbakel on 2006-11-24
Pentium 4 (mobile) here as well.

bPawn, could you perhaps make a screenshot of your installed hal packages? If you start 'synaptic' and search for 'hardware abstraction layer' (CTRL+F) you should get a listing of your installed packages. That should make it a bit easier to see which package versions are installed.

---

### Post by bPawn on 2006-11-24
there

---

### Post by rookieone on 2006-11-24
Just chiming in to say i'm hit with the same problem and I'm pretty upset about it too. :evil: 
I can always manually mount but to get read/write permissions on the stick I have to jump through more burning hoops then I want to so it would be cool to see this problem adressed.
AthlonXP with kernel 2.6.15-27-686 if it makes any difference

---

### Post by paul cooke on 2006-11-24
> **hvbakel said:**
> I guess this problem only exists in kubuntu and then probably only for those that upgraded to the latest kde 3.5.5 version (which has a different way of handling USB mounts).

I'm running KDE 3.5.4 on this Dapper box and I get an error message in KDE of "An unknown error has occurred" when I plug in any USB drive. The device is detected and konq pops up the what do you want to do dialog, but then fails to mount the drive.

Kpilot works fine with my Palm Tungsten E as well which threw me (made me think my 160G USB hard disk had failed... major panic mode there for some hours).

I have no problems at all using USB drives in Gnome on this same computer.

I'm NOT going to risk doing an update on my other box or my daughter's laptop as it's working on those (standard as supplied and officially updated Kubuntu)

---

### Post by hvbakel on 2006-11-24
> **bPawn said:**
> there

Please try the following:

Edit the sources.list file in /etc/apt/ (using sudo) and disable the repositories for dapper-updates by adding a '#' at the beginning of the lines. In my case these now look like this:

```

#deb http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
#deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

```

Doing this will disable the repositories that contain the hal update to version 0.5.7-1ubuntu18.2 that cause the problems. After this you can downgrade to 18.1 without the risk that the 18.2 version is installed over it again.

Instead of editing the sources.list config file directly you can also open 'Synaptic' and deselect the repositories by going to settings->repositories.

Off course after disabling these repositories you won't receive future dapper updates (but you will still get all security updates, these come from a different repository), however, you can always enable them later once the hal problem gets fixed.

Now you can try to install all the following packages again with the command:

```

sudo dpkg -i hal_0.5.7-1ubuntu18.1_i386.deb hal-device-manager_0.5.7-1ubuntu18.1_all.deb hal-doc_0.5.7-1ubuntu18.1_all.deb libhal1_0.5.7-1ubuntu18.1_i386.deb libhal-dev_0.5.7-1ubuntu18.1_i386.deb libhal-storage1_0.5.7-1ubuntu18.1_i386.deb libhal-storage-dev_0.5.7-1ubuntu18.1_i386.deb

```

Reading back in the previous apt output messages, all dependencies should now be met for this downgrade, but just paste the output again if there should still be any error.

---

### Post by dcstar on 2006-11-26
> **hvbakel said:**
> Please try the following:

Edit the sources.list file in /etc/apt/ (using sudo) and disable the repositories for dapper-updates by adding a '#' at the beginning of the lines. In my case these now look like this:
......

If you want to use a previous version, just go into Synaptic, select the package and use the "Force Version" option, then use the "Lock Version" option and that package won't be looked at for upgrading.

No need to muck around with repositories.

---

### Post by Castar on 2006-11-26
> **dcstar said:**
> If you want to use a previous version, just go into Synaptic, select the package and use the "Force Version" option, then use the "Lock Version" option and that package won't be looked at for upgrading.

No need to muck around with repositories.

That was excellent advice, thank you!

Come to think of it, I will be using Synaptic from now on...

---

### Post by AlphaMack on 2006-11-26
^ And that is exactly why I don't like Adept.  You can't lock down certain versions of packages because it will insist on upgrading them every time.

---

### Post by moshuptrail on 2006-11-26
Odd.  I am using Dapper Ubuntu with KDE added (so now I get the Kubuntu splash) and I do not see this problem in either Gnome or KDE.  
Dell laptop with P3 Coppermine CPU.  1 USB port.  Must unplug my optical mouse to test a USB mem stick. But it works fine (KDE 3.5.2).

---

### Post by Castar on 2006-11-26
> **moshuptrail said:**
> Odd.  I am using Dapper Ubuntu with KDE added (so now I get the Kubuntu splash) and I do not see this problem in either Gnome or KDE.  
Dell laptop with P3 Coppermine CPU.  1 USB port.  Must unplug my optical mouse to test a USB mem stick. But it works fine (KDE 3.5.2).

It's because you use KDE 3.5.2. I think we all use 3.5.5.

---

### Post by byourg on 2006-11-27
USB memory stick is broken for me too.:(  Kubuntu Dapper, KDE 3.5.5, Intel Celeron D. USB joystick that I use works fine.:)

---

### Post by Pyro MX on 2006-11-27
USB memory stick broken here too - downgrading with Synaptic works, but even with locked version, Adept updater shows up. It bugs me a little hehe. Let's hope it'll be fixed soon.

---

### Post by person12345 on 2006-11-27
Create a file called /etc/apt/preferences by running
$ sudo kate /etc/apt/preferences

Put the following into it and then run
$ sudo apt-get update && sudo apt-get dist-upgrade

You will then be able to use your USB devices from within KDE again.

########################
# /etc/apt/preferences #
########################

Package: hal
Pin: version 0.5.7-1ubuntu18.1
Pin-Priority: 1000

Package: libhal1
Pin: version 0.5.7-1ubuntu18.1
Pin-Priority: 1000

Package: libhal-storage1
Pin: version 0.5.7-1ubuntu18.1
Pin-Priority: 1000

---

### Post by katiad on 2006-12-01
I, too, was affected by this. Downgrading worked for me. *sigh*

---

### Post by treris on 2006-12-04
weird enough i don't seem to have this problem (working on dapper with kde 3.5.5 and a amd64 on the i386 kernel)
maybe it's a bug that's affected by what kernel is used (k7, 586, 686 etc)?

---

### Post by Castar on 2006-12-04
I don't think so, for me usb sticks used to be found under Gnome, not KDE 3.5.5.

---

### Post by bPawn on 2006-12-15
> **hvbakel said:**
> I submitted a bug to launchpad about this problem: [#72869]("https://bugz.launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869")


they say it is fixed, but not tested my self yet:

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869)

---

### Post by paul cooke on 2006-12-15
> **bPawn said:**
> they say it is fixed, but not tested my self yet:

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/72869)

yay... we're back firing on all six... just upgraded from 3.5.4 to 3.5.5 using the kde-latest repositories and usb mounting is working... 

yippee!!!

---

### Post by paul cooke on 2006-12-16
> **paul cooke said:**
> yay... we're back firing on all six... just upgraded from 3.5.4 to 3.5.5 using the kde-latest repositories and usb mounting is working... 

yippee!!!

spoke too soon... now I can't see CDs to rip from them. KsCD plays them fine, but Konqueror just shows a blank entry for /dev/cdrom0 and when I try to mount it using KDiskFree I get the following error:

Called: mount /dev/hdc
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

argh!!!! I hate it when this happens...

dmesg | tail gives:

[18096973.936000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[18096973.936000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[18096973.936000] ide: failed opcode was: unknown
[18096973.936000] end_request: I/O error, dev hdc, sector 1024
[18096973.936000] UDF-fs: No partition found (1)
[18096973.944000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[18096973.944000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[18096973.944000] ide: failed opcode was: unknown
[18096973.944000] end_request: I/O error, dev hdc, sector 64
[18096973.944000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

---

