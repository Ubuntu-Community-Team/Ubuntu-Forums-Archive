---
title: "Can't install FGLRX driver in Ubuntu 14.04.2"
date: 2015-02-21
forum: General Help
---

### Post by kalsolette on 2015-02-21
When I try to install the AMD driver through 'Software Updates' it automatically reselects the 'Using X.Org X Server' option when I click apply. When I try to install the 'ATI Binary' option through the 'Ubuntu Software Centre' I get this error:  
[FONT=Verdana]
The following packages have unmet dependencies:[/FONT]

fglrx: Depends: libqtcore4 (>= 4:4.8.4) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
       Depends: xorg-video-abi-15 but it is a virtual package

This is the 2nd fresh install of 14.04.2. The driver installed fine in 14.04.1. Help please!!!

---

### Post by kalsolette on 2015-02-22
Bump.

I can't play several Steam games on the open source 'Radeon' driver because it doesn't support certain features.

---

### Post by Mark Phelps on 2015-02-22
Need to see what video chip you have.  Open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that information back here.

---

### Post by Ihokerros on 2015-02-22
Same thing happening to me. If I try to install the fglrx or fglrx-updates through Software & Updates it just bounces back to the open source drivers.

Don't really know what I'm doing but I fiddled around in the terminal and got this.

$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : Cypress XT [Radeon HD 5870]
vendor   : Advanced Micro Devices, Inc. [AMD/ATI]
modalias : pci:v00001002d00006898sv00001682sd00002961bc03sc00i00
driver   : fglrx-updates - distro non-free
driver   : fglrx - distro non-free
driver   : xserver-xorg-video-ati - distro free builtin recommended

$ sudo apt-get install fglrx-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx-updates : Depends: xorg-video-abi-11 but it is not installable or
                          xorg-video-abi-12 but it is not installable or
                          xorg-video-abi-13 but it is not installable or
                          xorg-video-abi-14 but it is not installable or
                          xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.

---

### Post by QIII on 2015-02-22
Hello!

I hadn't planned on doing much with this over the weekend, but since there are a couple of you with this issue, I'll work on it.

A couple off weeks ago I [blogged]("http://theleftcoastgeek.net/") about testing the R9 290X on Ubuntu, which worked just fine with fglrx-updates from 12.04 to 15.04 (development).  This is a recent issue.

I'll do a second boot install on my machine, take a look at it and see if there is anything on launchpad yet.  If not, I'll get it reported.

I'm not saying I'll have an answer right away.

Is this happening with both fglrx and fglrx-updates?

---

### Post by kalsolette on 2015-02-22
> **Mark Phelps said:**
> Need to see what video chip you have.  Open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that information back here.

Here you go!

VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850]

> **QIII said:**
> Hello!

I hadn't planned on doing much with this over the weekend, but since there are a couple of you with this issue, I'll work on it.

A couple off weeks ago I [blogged]("http://leftcoastgeek.blogspot.com/") (don't expect that to stay on blogspot too long.  I'm looking for hosting for my own domain) about testing the R9 290X on Ubuntu, which worked just fine with fglrx-updates from 12.04 to 15.04 (development).  This is a recent issue.

I'll do a second boot install on my machine, take a look at it and see if there is anything on launchpad yet.  If not, I'll get it reported.

I'm not saying I'll have an answer right away.

Is this happening with both fglrx and fglrx-updates?

Yes it happens with both 'fglrx' and 'fglrx-updates'. It also happens with 'ATI Binary' when trying to install it through the 'Ubuntu Software Centre'.

---

### Post by QIII on 2015-02-22
OK.  Thanks.  I'm going to install another boot and see what I can find out.

---

### Post by kalsolette on 2015-02-22
> **QIII said:**
> OK.  Thanks.  I'm going to install another boot and see what I can find out.

Good luck! :)

I'm also slightly jealous of your setup. A Phenom II X6 1100T, 16GB RAM, and a Radeon 290X? That's awesome! I'm only rocking an AMD A8 5500, 4GB RAM, and a Radeon 7850... :3

---

### Post by QIII on 2015-02-22
Can one of you confirm that this is the behavior you are seeing?

Attempt to install fglrx fails as follows:


```
zack3@ZACK3:~$ sudo apt-get install fglrx-updates xvba-va-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx-updates : Depends: xorg-video-abi-11 but it is not installable or
                          xorg-video-abi-12 but it is not installable or
                          xorg-video-abi-13 but it is not installable or
                          xorg-video-abi-14 but it is not installable or
                          xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.
```


Attempt to insatll xorg-video-abi-15 yields:

```
zack3@ZACK3:~$ sudo apt-get install xorg-video-abi-15
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xserver-xorg-core' instead of 'xorg-video-abi-15'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```


Attempting to install xserver-xorg-core instead yields:

```
zack3@ZACK3:~$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by QIII on 2015-02-22
If you would, please, see [this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") bug on Launchpad and click "Affects me".  Please do not add a post such as "This affects me, too!"  That makes the thread hard to read.  Just click the button.

---

### Post by Ihokerros on 2015-02-23
Attempt to install fglrx fails as follows:

$ sudo apt-get install fglrx-updates xvba-va-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx-updates : Depends: xorg-video-abi-11 but it is not installable or
                          xorg-video-abi-12 but it is not installable or
                          xorg-video-abi-13 but it is not installable or
                          xorg-video-abi-14 but it is not installable or
                          xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.

Attempt to insatll xorg-video-abi-15 yields:

$ sudo apt-get install xorg-video-abi-15
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xserver-xorg-core' instead of 'xorg-video-abi-15'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Attempting to install xserver-xorg-core instead yields:

$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by kalsolette on 2015-02-23
matt@matt-MS-7721:~$ sudo apt-get install fglrx-updates xvba-va-driver
[sudo] password for matt: 
Sorry, try again.
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 fglrx-updates : Depends: xorg-video-abi-11 but it is not installable or
                          xorg-video-abi-12 but it is not installable or
                          xorg-video-abi-13 but it is not installable or
                          xorg-video-abi-14 but it is not installable or
                          xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.
matt@matt-MS-7721:~$ 

matt@matt-MS-7721:~$ sudo apt-get install xorg-video-abi-15
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xserver-xorg-core' instead of 'xorg-video-abi-15'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
matt@matt-MS-7721:~$ 

matt@matt-MS-7721:~$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
matt@matt-MS-7721:~$ 
[SIZE=3][COLOR=#000000][B]
We all apparently get the same issues![/B][/COLOR][/SIZE]

> **QIII said:**
> If you would, please, see [this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") bug on Launchpad and click "Affects me".  Please do not add a post such as "This affects me, too!"  That makes the thread hard to read.  Just click the button.

Oops. Just saw this after posting the output of the commands! I'll go and post on that bug report.

---

### Post by mc4man on 2015-02-23
If you installed from the 14.04.2 image then you can't satisfy a dependency on xserver-xorg-core (what xorg-video-abi-XX means
The reason is you already have xserver-xorg-core-lts-utopic as 14.04.2 image is using the HWE utopic mesa stack

So your driver packages need to be updated to either accept the lts-utopic-mesa packages or maybe even updated to work with lts-utopic-mesa.
While not holding your breath on that it may be a better idea to use 14.04.1 & update everything which will give you 14.04.2 minus the  lts-utopic-mesa mess 
(the lts-utopic kernel can be install on 14.04.1 base install if desired noting there are a few issue there too.

I see no real reason to use the 14.04.2 image as it was done haphazardly & with little advantage over 14.04.1 upgraded. (and in some areas the lts-mesa is worse
A ppa (maybe xorgers) would be a better way to get a newer mesa on 14.04 as it can easily be reverted via ppa-purge

---

### Post by QIII on 2015-02-23
I updated to 14.04.2, less the HWE stack, last week.  When an HWE comes out, I hold off for a while.  But I do have the 3.16 kernel that way.

However, newer users may have difficulty with doing that.

This is a packaging issue that needs to be fixed.  However, without a bug report and enough "Affects me" submissions there will be little pressure to fix it.

For those who have already started the process of updating and those who are just coming to Ubuntu and have been told to use the most recent LTS, this is a major issue that needs to be raised to critical.

---

### Post by mc4man on 2015-02-23
> **QIII said:**
> I updated to 14.04.2, less the HWE stack, last week.  When an HWE comes out, I hold off for a while.  But I do have the 3.16 kernel that way.

However, newer users may have difficulty with doing that.

This is a packaging issue that needs to be fixed.  However, without a bug report and enough "Affects me" submissions there will be little pressure to fix it.

For those who have already started the process of updating and those who are just coming to Ubuntu and have been told to use the most recent LTS, this is a major issue that needs to be raised to critical.
a couple of things to keep in mind with the lts-utopic kernel
For Intel cpu's that support/use pstate it is default enabled in that kernel  but the ondemand script [has not been fixed to reflect that.]("http://ubuntuforums.org/showthread.php?t=2265277") If an issue then the script can be edited
Also in some cases log outs & restarts may [be slow or hang ]("http://ubuntuforums.org/showthread.php?t=2265453&p=13232972&viewfull=1#post13232972")when just upgrading to the lts kernel 

There is also a [URL="http://ubuntuforums.org/showthread.php?t=2265453&p=13233096&viewfull=1#post13233096"]missing mesa package & some devel packages that can't be installed
[/URL]
Likely more to arise..

---

### Post by QIII on 2015-02-23
It looks like the bug reports you referred to appeared about the time I got into this thread and I added my report.  Definitely a mess.

Point releases to LTS ought not to break things so disastrously.

---

### Post by nuco-ageka on 2015-02-23
How can i revert back to the trusry mesa stack?, i get an error when i try to remove the mesa-lts package.

---

### Post by mc4man on 2015-02-23
> **nuco-ageka said:**
> How can i revert back to the trusry mesa stack?, i get an error when i try to remove the mesa-lts package.

It's maybe  possible but a look suggests not practicable at all. Either live with & await bug fixes or start over with 14.04.1

---

### Post by palto42 on 2015-02-24
> **nuco-ageka said:**
> How can i revert back to the trusry mesa stack?, i get an error when i try to remove the mesa-lts package.

Did you originally install 14.04.1 and upgrade to the new utopic stack as described here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)  or directly installed 14.4.2?

If you upgraded from 14.04.1, then you can look at the apt logs in /var/log/apt and try to roll-back by applying the inverse changes (e.g. remove what was previously installed) in reverse order.
I successfully changed back two of my laptops with this method. Note that this doesn't change the reported version back to 14.04.1 but keeps 14.04.2 in the files /etc/issues, /etc/os-release and /etc/lsb-release (can be changed manually).

I highly recommend to do a partition backup before trying to roll-back (unfortunately I haven't done such backup before upgrading to 14.04.2).

---

### Post by kalsolette on 2015-02-26
This is now deeply annoying. Yet another lacklustre performance by Canonical.

---

### Post by pingoo on 2015-02-27
> **palto42 said:**
> If you upgraded from 14.04.1, then you can look at the apt logs in /var/log/apt and try to roll-back by applying the inverse changes (e.g. remove what was previously installed) in reverse order.
I successfully changed back two of my laptops with this method. Note that this doesn't change the reported version back to 14.04.1 but keeps 14.04.2 in the files /etc/issues, /etc/os-release and /etc/lsb-release (can be changed manually).

I highly recommend to do a partition backup before trying to roll-back (unfortunately I haven't done such backup before upgrading to 14.04.2).

There's a simpler way, less manual, to revert to 14.04.1/to a certain date system (es. to the 11/02)? The apt history is increased before I discovered that thread, hoping for a solution...

---

### Post by mc4man on 2015-02-27
> **pingoo said:**
> There's a simpler way, less manual, to revert to 14.04.1/to a certain date system (es. to the 11/02)? The apt history is increased before I discovered that thread, hoping for a solution...
If you don't mind a couple of hundred MB of downloads & 'living on the edge' for a few moments then one can use synaptic to effect a revert of the mesa-lts-utopic  to good old trusty versions. The key is to not freak out nor log out till it's squared up. 
In this scenario it's just simply marking one package in synaptic for removal to get the ball rolling.  I just did it here to see, all is now well but can't say it's 100 % guaranteed for others, but close..

---

### Post by pingoo on 2015-02-28
@mc4man: I installed synaptic but couldn't find mesa-lts-utopic, maybe libglapi-mesa-lts-utopic? The problem with this package is that I can see just the installed version,10.3.2-0ubuntu1~trusty2, in the version tab of the package properties. Clicking on remove, will remove a lot of packages in favour of mir, unity8 etc...

---

### Post by mc4man on 2015-02-28
> **pingoo said:**
> @mc4man: I installed synaptic but couldn't find mesa-lts-utopic, maybe libglapi-mesa-lts-utopic? The problem with this package is that I can see just the installed version,10.3.2-0ubuntu1~trusty2, in the version tab of the package properties. Clicking on remove, will remove a lot of packages in favour of mir, unity8 etc...
Just to see I did this a couple of more times & the last attempt failed so can't recommend (if it fails your install could be toast.
So if it was me I'd copy out any files of interest & fresh install 14.04.1 image or wait for fixes or the next lts HWE (vivid)

For info sake here is list of packages the mesa upgrade installed *here* - 
>   libegl1-mesa-drivers-lts-utopic
libegl1-mesa-lts-utopic
libepoxy0 
libevdev2
libgbm1-lts-utopic 
libgl1-mesa-dri-lts-utopic 
libgl1-mesa-glx-lts-utopic
libglapi-mesa-lts-utopic 
libgles1-mesa-lts-utopic 
libgles2-mesa-lts-utopic
libllvm3.5 
libopenvg1-mesa-lts-utopic 
libwayland-egl1-mesa-lts-utopic
libxatracker2-lts-utopic 
xserver-xorg-core-lts-utopic
xserver-xorg-input-all-lts-utopic
xserver-xorg-input-evdev-lts-utopic
xserver-xorg-input-mouse-lts-utopic 
xserver-xorg-input-synaptics-lts-utopic
xserver-xorg-input-vmmouse-lts-utopic 
xserver-xorg-input-wacom-lts-utopic
xserver-xorg-lts-utopic 
xserver-xorg-video-all-lts-utopic
 xserver-xorg-video-ati-lts-utopic 
xserver-xorg-video-cirrus-lts-utopic
 xserver-xorg-video-fbdev-lts-utopic 
xserver-xorg-video-intel-lts-utopic
 xserver-xorg-video-mach64-lts-utopic 
xserver-xorg-video-mga-lts-utopic
xserver-xorg-video-modesetting-lts-utopic
xserver-xorg-video-neomagic-lts-utopic 
xserver-xorg-video-nouveau-lts-utopic
xserver-xorg-video-openchrome-lts-utopic 
xserver-xorg-video-r128-lts-utopic
xserver-xorg-video-radeon-lts-utopic 
xserver-xorg-video-savage-lts-utopic
xserver-xorg-video-siliconmotion-lts-utopic
xserver-xorg-video-sisusb-lts-utopic 
xserver-xorg-video-tdfx-lts-utopic
xserver-xorg-video-trident-lts-utopic 
xserver-xorg-video-vesa-lts-utopic
xserver-xorg-video-vmware-lts-utopic

---

### Post by pingoo on 2015-02-28
> **mc4man said:**
> Just to see I did this a couple of more times & the last attempt failed so can't recommend (if it fails your install could be toast.
So if it was me I'd copy out any files of interest & fresh install 14.04.1 image or wait for fixes or the next lts HWE (vivid)

For info sake here is list of packages the mesa upgrade installed *here* -

Ok, thank you!
I reverted xserver-xorg-core to the previous version, 1.15.1-0ubuntu2, and the result appeared the same that removing the package libglapi-mesa-lts-utopic you said.
Two packages failed to install at the first attempt, but re-applying the changes, without closing anything, they installed.
I rebooted, installed the fglrx-updates and rebooted again, no toast ;)

---

### Post by mc4man on 2015-02-28
> **pingoo said:**
> Ok, thank you!
I reverted xserver-xorg-core to the previous version, 1.15.1-0ubuntu2, and the result appeared the same that removing the package libglapi-mesa-lts-utopic you said.
Two packages failed to install at the first attempt, but re-applying the changes, without closing anything, they installed.
I rebooted, installed the fglrx-updates and rebooted again, no toast ;)

Excellent, (don't try again..
Why my last attempt to test reverting  failed not sure, rather than waste time on I just dumped the install.

---

### Post by nuco-ageka on 2015-03-04
Someone at launchpad found a way to revert back to the trusty mesa drivers. 

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

By running [FONT=monospace][COLOR=#333333]"sudo apt-get install libcheese*" the old version gets installed, you have to manually add back the synaptic touchpad drivers if you are using a notebook.

I had a clean 14.04.2 install and this worked fine.[/COLOR][/FONT]

---

### Post by prangfamily on 2015-03-06
Fresh install of Ubuntu X64 14.04.02 LTS
Kernel Default: 3.16.0-31-genericVideo Card: Ati Mobility Radeon HD 5870

same problem as others currently using open drivers

---

### Post by mc4man on 2015-03-06
> **prangfamily said:**
> Fresh install of Ubuntu X64 14.04.02 LTS
Kernel Default: 3.16.0-31-genericVideo Card: Ati Mobility Radeon HD 5870

same problem as others currently using open drivers
If you're doing a fresh install then may be better to use 14.04.1 then downgrading nonsense (even though it can work

14.04.1 iso's are here, middle of the listings - 
 [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

---

### Post by QIII on 2015-03-06
@prangfamily:

If you haven't already, pleas go to the launchpad link given and click "Affects Me".  Don't leave a comment like "I have the same problem".  That just adds more for someone to have to read through.

"Affects me" is sufficient.

---

### Post by oc-nilsen on 2015-03-19
Well, this is annoying. Should've been fixed by now. I'm downloading 14.04.1 now, as I am not certain about how stable the workaround will be. Clicked 'Affects me' at Launchpad as well.

---

### Post by HeroCC on 2015-03-29
This bug is annoying indeed, I just reinstalled Ubuntu, and without the fglrx drivers my computer acts all wonky, I clicked 'This Affects Me' on the bug report linked, hope it gets fixed soon!

---

### Post by QIII on 2015-03-29
Thanks for clicking!

I'm somewhat disappointed that what amounts to a packaging error that affects an entire class of users is not getting fixed immediately.

---

### Post by J0nDaFr3aK on 2015-04-02
Hi there.
I don't know if the bug has been fixed yet, but I've just managed to install the fglrx-updates driver for my r9 270x.

The commands I ran are:

```
sudo apt-get install libcheese*
``` ^(I don't know if this one was actually needed - I tried it as suggested in the previous page)

```
sudo apt-get install xorg-video-abi-15
``` ^(this one worked for me and resolved all dependencies)

```
sudo apt-get install fglrx-updates
```

The additional driver utility is now displaying that AMD's proprietary driver is the one being used.

EDIT: I'm using a fresh install of 14.04.2.

---

### Post by QIII on 2015-04-02
Hi!

No, the actual bug has not been fixed yet.

The cheese thing is a viable work-around as discussed in the bug report I reference earlier, but it's not a fix.

If you haven't done so already, please go to the bug report and click "Affects me" to increase the heat index.

---

### Post by underskyzx on 2015-04-04
Same problem here... I'm not sure if I try the workaround, install 14.04.1 or wait for a fix.

Anyway can't hide how disappointed I am with Linux right now, bugs like this make the Windows > Linux transition a pain

---

### Post by underskyzx on 2015-04-04
Will this workaround conflict with future oficial patch?

---

### Post by svendheim2 on 2015-04-09
This happens in a LTS-release, and is still not fixed. Laughable.

---

### Post by DanielWEWO on 2015-04-21
Hey, I'm attempting that work-around and I'm just attempting to be cautious here. I have unmet dependencies when I attempt to install libcheese

```

sudo apt-get install libcheese*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcheese-dev' for regex 'libcheese*'
Note, selecting 'libcheese7' for regex 'libcheese*'
Note, selecting 'libcheese-doc' for regex 'libcheese*'
Note, selecting 'libcheese-gtk-dev' for regex 'libcheese*'
Note, selecting 'libcheese-gtk23' for regex 'libcheese*'
libcheese-gtk23 is already the newest version.
libcheese-gtk23 set to manually installed.
libcheese7 is already the newest version.
libcheese7 set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not installable
 libcheese-dev : Depends: gir1.2-cheese-3.0 (= 3.10.2-0ubuntu2) but it is not going to be installed
                 Depends: libglib2.0-dev (>= 2.28.0) but it is not going to be installed
                 Depends: libclutter-1.0-dev (>= 1.10.0) but it is not going to be installed
                 Depends: libgstreamer1.0-dev (>= 0.11.0) but it is not going to be installed
                 Depends: libgstreamer-plugins-base1.0-dev (>= 0.11.0) but it is not going to be installed
                 Depends: libclutter-gst-2.0-dev (>= 1.9.0) but it is not going to be installed
                 Depends: libgdk-pixbuf2.0-dev but it is not going to be installed
 libcheese-gtk-dev : Depends: libglib2.0-dev (>= 2.28.0) but it is not going to be installed
                     Depends: libgtk-3-dev (>= 3.4.4) but it is not going to be installed
                     Depends: libgstreamer1.0-dev (>= 0.11.0) but it is not going to be installed
                     Depends: libgstreamer-plugins-base1.0-dev (>= 0.11.0) but it is not going to be installed
                     Depends: libclutter-gtk-1.0-dev (>= 0.91.8) but it is not going to be installed
                     Depends: libcanberra-gtk3-dev (>= 0.26) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

How should I proceed?

Edit: Oops. I still had pieces of fglrx-updates still installed from a previous attempt. Removed those, and attempted the workaround and was successful. fglrx-updates now running for me on 14.04.2

---

### Post by roky2 on 2015-04-22
All I did off the top of my head was these 2 commands and everything works perfectly. 

```
sudo apt-get install xorg-video-abi-15
```

```
sudo apt-get install fglrx-updates
```

Proprietary installed and running flawless.

---

### Post by QIII on 2015-04-22
There is no need for a work-around any longer.  The fix is in the trusty-proposed repo and should be in the trusty repo any time.

Please see my post #77 in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") cited above.

---

