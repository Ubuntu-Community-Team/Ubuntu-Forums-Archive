---
title: "New ATI Driver - 8.42 Driver Brings Fixes &amp; AIGLX!"
date: 2007-10-23
forum: General Help
---

### Post by chatterbox101 on 2007-10-23
**It's here folks:**

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")

**Review here:**

[http://www.phoronix.com/scan.php?page=article&item=887&num=1]("http://www.phoronix.com/scan.php?page=article&item=887&num=1")

I'm downloading now :D :D

Finally proper wine, proper compiz-fusion....deletion of my windows partition...removal of xgl...defo

---

### Post by jelofson on 2007-10-23
> **chatterbox101 said:**
> **It's here folks:**

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")

**Review here:**

[http://www.phoronix.com/scan.php?page=article&item=887&num=1]("http://www.phoronix.com/scan.php?page=article&item=887&num=1")

I'm downloading now :D :D

Finally proper wine, proper compiz-fusion....deletion of my windows partition...removal of xgl...defo


Excellent!!! I just saw that on Phoronix as well. Looking forward to getting it installed. Hopefully it's straightforward enough.

---

### Post by Maestro23 on 2007-10-23
Thanks for the heads-up.  You can check their forums for early feedback/chatter on it.

[http://phoronix.com/forums/showthread.php?t=5947](http://phoronix.com/forums/showthread.php?t=5947)

---

### Post by Kymus on 2007-10-23
stupid question:

wtf do I do with this?

by that, I mean, gEdit is trying to open it when I run it.. nothing is recognizing the properties of the file and so it just stares at me and is like "ok, what do you want me to do with this?"

:confused:

---

### Post by Toadmund on 2007-10-23
I tried to install, but I get this message (see screenshot attachment ), How do I get into SU mode if it closes when I press OK.
Or, what do I do, I forget these things.

---

### Post by #Reistlehr- on 2007-10-23
in termanil type:


sudo ./FILENAME

replace FILENAME with the name of the driver when you are insid ethe directory with the driver

---

### Post by Maestro23 on 2007-10-23
I feel this link will be needed.

Ubuntu Gutsy Installation of ATI Driver: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Toadmund on 2007-10-23
Thanks!
For those who don't understand or don't know:

In terminal:
```
cd Desktop
``` (capital D!)
then
```
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```

---

### Post by Toadmund on 2007-10-23
> **Maestro23 said:**
> I feel this link will be needed.

Ubuntu Gutsy Installation of ATI Driver: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Are you sure these instructions are needed?

I just installed and I ran 'glxgears' and I am running about 1000 more FPS than I ever did.
Those instructions have you disable aiglx, but this driver has aiglx, you want that!

---

### Post by Maestro23 on 2007-10-23
> **Toadmund said:**
> Are you sure these instructions are needed?

I just installed and I ran 'glxgears' and I am running about 1000 more FPS than I ever did.
Those instructions have you disable aiglx, but this driver has aiglx, you want that!

Excellent man.  Getting ready to install it myself.  How is everything else running?

Yeah, that is more for the 8.40... driver.  That is just to give some people a CLUE. :)

From all the chatter I"ve been reading over at the other forum, some are having succes, some are not. Some issues on 64-bit, but none that can't be rectified with some terminal commands.   I don't recommend this driver just yet for some new to Linux and who has a good running system.

If you have to ask "What is this...", chances are stay with what you got right now on your system.:popcorn:

---

### Post by Kymus on 2007-10-23
> **Toadmund said:**
> Thanks!
For those who don't understand or don't know:

In terminal:
```
cd Desktop
``` (capital D!)
then
```
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```

when I do this:

> kymus@Shouxing:~/Desktop$ sudo ./ati-driver-installer-8.42.3-x86.x86_64.run

I get this:

> sudo: ./ati-driver-installer-8.42.3-x86.x86_64.run: command not found

:confused:

---

### Post by eternalperson on 2007-10-23
Hey, does anyone know if there is going to be better support for the ATI Radeon XPRESS 200 integrated graphics chipset in the future (cause the release notes said that version 8.42 of the driver wasn't intended and wont work properly on this model). Thanks!

---

### Post by infamousdd on 2007-10-23
> **Kymus said:**
> when I do this:



I get this:



:confused:

Same.

---

### Post by TheQuicksilver on 2007-10-23
> **infamousdd said:**
> Same.
Same.

---

### Post by TheQuicksilver on 2007-10-23
This shows you how to run it: [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

---

### Post by ba5e on 2007-10-23
Im So damn happy i am almost crying!!!!!!!!!

Now lets see if it installs okay ;) Well done all who have worked on this!!! hats off to ATI too!!!

---

### Post by Toadmund on 2007-10-23
> **eternalperson said:**
> Hey, does anyone know if there is going to be better support for the ATI Radeon XPRESS 200 integrated graphics chipset in the future (cause the release notes said that version 8.42 of the driver wasn't intended and wont work properly on this model). Thanks!

Mine is an Xpress 200g.

I tested it on glxgears, but that's it so far.



'Under the Permissions tab, make sure that Allow executing file as program is ticked and press Close'

Yeah should have mentioned I had to do that.(TheQuicksilvers link)

---

### Post by Kymus on 2007-10-23
It started to load, but then stopped short, telling me that I need to be a superuser :(

---

### Post by Maestro23 on 2007-10-23
> **Kymus said:**
> It started to load, but then stopped short, telling me that I need to be a superuser :(

**sudo**

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Maestro23 on 2007-10-23
> **ba5e said:**
> Im So damn happy i am almost crying!!!!!!!!!

Now lets see if it installs okay ;) Well done all who have worked on this!!! hats off to ATI too!!!

Man, just installed on 64-bit Gutsy. Installed without a hitch.  Direct Rendering = Yes!  Now to test Compiz and other stuff...:guitar:

---

### Post by Kymus on 2007-10-23
> **Maestro23 said:**
> **sudo**

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

thanks!

---

### Post by chatterbox101 on 2007-10-23
:( Ok I have to confess I'm not the greatest Linux hacker in the world...in fact, It's bordering on n00bish...however.  I have managed to get this working so glxinfo is reporting direct rendering, fglrxinfo is reporting the correct display info...ATI, not mesa etc etc.

All good then?

Nope - the following have issues (ATI X1300):

Compiz fusion - This works now without XGL....until FireFox is opened (see next)
FireFox - There seems to be some serious leakage with firefox - the [Phoronix forums]("http://www.phoronix.com/forums/showthread.php?t=5947") have been banging on about this for the last hour
Video - This flickers again the [Phoronix forums]("http://www.phoronix.com/forums/showthread.php?t=5947") are going wild over this.
Gaming - Not great results so far in either OpenGL Or faux d3d mode in cedega et al

In summary, for the short term I will be shifting back to my XGL combo...sad, but this is not yet ready to be used on my production machine.  May I also suggest that technical assistance is sort, at least in the immediacy over on the [Phoronix forums]("http://www.phoronix.com/forums/showthread.php?t=5947").  There's nearly 200 comments on the subject alone, so it involves quite a lot of wading to get an answer to technical problems, although I can't imagine many more popping up.

Keep smiling folks :) Maybe I should have kept my big mouth shut!

PS - One final thought - may it be worth waiting for these to appear in the Restricted Drivers repos? - I'm sure when they're in a suitable working condition Ubuntu will provide  :)

---

### Post by ravencoder on 2007-10-24
so... any of you actually got this working on ubuntu 7.04 with xserver 1.3?? i'm downloading this now .. i have a question. I have Xgl installed how do i get rid of Xgl and start a normal X server? .. i'm still new to linux maybe 3 weeks worth of linux exp. 

thnx in advance

---

### Post by misfitpierce on 2007-10-24
ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.O20472/debian/control.template ]; then \
                cat /tmp/fglrx.O20472/debian/control.template > /tmp/fglrx.O20472/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.O20472/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.O20472/debian/driver.$i > \
              /tmp/fglrx.O20472/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.O20472/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.O20472/debian/10fglrx.template > /tmp/fglrx.O20472/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.O20472/debian/fglrx.default ]; then \
          mv /tmp/fglrx.O20472/debian/fglrx.default /tmp/fglrx.O20472/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.O20472/debian/control.template ]; then \
                cat /tmp/fglrx.O20472/debian/control.template > /tmp/fglrx.O20472/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.O20472/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.O20472/debian/driver.$i > \
              /tmp/fglrx.O20472/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.O20472/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.O20472/debian/10fglrx.template > /tmp/fglrx.O20472/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.O20472/debian/fglrx.default ]; then \
          mv /tmp/fglrx.O20472/debian/fglrx.default /tmp/fglrx.O20472/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.O20472/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.O20472/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.e20391

Im getting this error... Any idea on what I should do?

---

### Post by chatterbox101 on 2007-10-24
> **ravencoder said:**
> so... any of you actually got this working on ubuntu 7.04 with xserver 1.3?? i'm downloading this now .. i have a question. I have Xgl installed how do i get rid of Xgl and start a normal X server? .. i'm still new to linux maybe 3 weeks worth of linux exp. 

thnx in advance

Hi Raven,

I've not had a good experience - see my post above - I haven't searched the forums very much this afternoon, but last night and this morning people were seriously thinking about holding fire for a little while....that's what I'm going to do.

to remove XGL

```
sudo apt-get remove xserver-xgl
```

---

### Post by aealtrus on 2007-10-24
Does this work on ati radeon x200m?

---

### Post by Maestro23 on 2007-10-24
> **aealtrus said:**
> Does this work on ati radeon x200m?

According to some over at these forums, it's hit or miss for some with that card.

[http://phoronix.com/forums/showthread.php?t=5947](http://phoronix.com/forums/showthread.php?t=5947)

Factors include: LInux Distro, 32 or 64-bit, etc...

---

### Post by misfitpierce on 2007-10-24
I cant get it to even make gutsy package shows error that I posted above on this page - ATI X200

---

### Post by jbernardo on 2007-10-24
I'm having exactly the same error as misfitpierce, on kubuntu gutsy 7.10 x86-64, with a Radeon 9600 Pro.

---

### Post by misfitpierce on 2007-10-24
Wooo im not alone... No offense :) Anyone know of way to fix that?

---

### Post by chatterbox101 on 2007-10-24
> **misfitpierce said:**
> Wooo im not alone... No offense :) Anyone know of way to fix that?

Could you post the command you're using to generate the above result?
Cheers

---

### Post by misfitpierce on 2007-10-24
> **chatterbox101 said:**
> Could you post the command you're using to generate the above result?
Cheers


sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

from the install guide.

---

### Post by jbernardo on 2007-10-24
> **chatterbox101 said:**
> Could you post the command you're using to generate the above result?
Cheers
I did this:
```
 bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

---

### Post by misfitpierce on 2007-10-24
negative same error... you did this on 64 bit system?

---

### Post by jbernardo on 2007-10-24
Yes, but just solved it by checking the bug in launchpad, and doing [this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325/comments/8"). Booting now into fglrx...

---

### Post by misfitpierce on 2007-10-24
Awesome looks like the fix... I will try in a bit and let you know.

---

### Post by crazytigger on 2007-10-24
Well i cant get it working, in fact ever since i reinstalled 7.04 i havent been able to get the fglrx driver to work at all. 

The ATI and radeon drivers work fine, however when i try fglrx in the driver section X throws up an error..  

II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14
(EE) No devices detected.

Fatal server error:
no screens found

This happens even after i do

sudo aticonfig --initial -f

Which re-writes xorg.conf removing any previous device./screen/monitor section.

I cant see anything wrong with the way aticonfig configures xorg. with the initial option.

With the new driver installed im im pretty sure fglrxinfo and glxinfo are giving different errors than before because at some point with the previous driver i had a longer list and directed rendering enabled: No .. however i cant get that now

Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

****@****:~$ glxinfo
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

(clearly this is because im using the ATI driver and not fglrx?)

Please would someone take a bit of time to help me out, ive been trying to get fglrx working for days i've googled, tried the guides and walkthroughs... i dont know where else to turn. It WAS working before this re-install.

Where can i start? What info do you need?

My attachments are my original xorg.conf and xorg.conf after aticonfig --initial -f

EDIT

after reinstalling the fglrx driver through synaptic, fglrxinfo does indeed give different information

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2

and 

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No

However when attempting to use the fglrx driver in xorg, the no device/screens errors are the same as described at the beginning of this post. :(

---

### Post by SupWiz17 on 2007-10-24
I just downloaded the new driver installed it and restarted now when I type amdcccle


I get

 There was a problem initializing Catalyst Controll Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not funtioning properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.

in a popup. I just installed the driver why wouldnt it read it.

---

### Post by Maestro23 on 2007-10-24
> **SupWiz17 said:**
> I just downloaded the new driver installed it and restarted now when I type amdcccle


I get

 There was a problem initializing Catalyst Controll Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not funtioning properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.

in a popup. I just installed the driver why wouldnt it read it.

Is there a menu item for the CCC under Apps.  Works for me both ways.  How did you install the driver?

---

### Post by SupWiz17 on 2007-10-24
yes there is a item for CCC under apps and I get the same error. I installed the driver by using the commands given in this thread

cd Desktop

sudo ./ati-driver-installer-8.42.3-x86.x86_64.run

---

### Post by SupWiz17 on 2007-10-24
If I followed the instructions in this thread would that help me at all?

[http://ubuntuforums.org/showthread.php?t=575843until](http://ubuntuforums.org/showthread.php?t=575843until)

---

### Post by Maestro23 on 2007-10-24
> **SupWiz17 said:**
> yes there is a item for CCC under apps and I get the same error. I installed the driver by using the commands given in this thread

cd Desktop

sudo ./ati-driver-installer-8.42.3-x86.x86_64.run

After you installed and rebooted, did your run:

> sudo aticonfig --initial

---

### Post by SupWiz17 on 2007-10-24
Not right after I rebooted, but I just tried it now and got 

Found fglrx primary device section
Nothing to do, terminating.

---

### Post by Maestro23 on 2007-10-24
> **SupWiz17 said:**
> Not right after I rebooted, but I just tried it now and got 

Found fglrx primary device section
Nothing to do, terminating.

What do the following show: (Type in terminal)

> fglrxinfo

glxinfo | grep direct

*If you see Mesa... then the installation did not go correctly.  Also, if Direct = No.

---

### Post by SupWiz17 on 2007-10-24
> **Maestro23 said:**
> What do the following show: (Type in terminal)



*If you see Mesa... then the installation did not go correctly.  Also, if Direct = No.
for fglrxinfo i get 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release


and for glxinfo | grep direct i get 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


So since I see Mesa in there and no for direct rendering do I have to reinstall the driver a different way?

---

### Post by Maestro23 on 2007-10-24
> **SupWiz17 said:**
> for fglrxinfo i get 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release


and for glxinfo | grep direct i get 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


So since I see Mesa in there and no for direct rendering do I have to reinstall the driver a different way?

Hmmm... What's under System>>Admin>>Restricted Driver

---

### Post by SupWiz17 on 2007-10-24
> **Maestro23 said:**
> Hmmm... What's under System>>Admin>>Restricted Driver
I have the ATi accelerated graphics driver box checked and it says that it is in use.

---

### Post by jpittack on 2007-10-24
Having the same issues.
This comes up when attempting to install. Is this the possible culprit?

> john@ubuntu:~/Desktop/ATI$ sudo  ./ati-driver-installer-8.42.3-x86.x86_64.run
Created directory fglrx-install.e13530
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
**[: 262: ==: unexpected operator**
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
loki_setup: directory: (null)
Removing temporary directory: fglrx-install.e13530
john@ubuntu:~/Desktop/ATI$ 



---

### Post by SupWiz17 on 2007-10-24
> **jpittack said:**
> Having the same issues.
This comes up when attempting to install. Is this the possible culprit?
that has to do with the super user account i think there was a link earlier in the thread

---

### Post by Unicycle on 2007-10-24
I installed the driver.  Under normal 2D GNOME operation, it is problem free.  But, I tried to do some 3D games (Neverball, TuxKart, etc.), and all of them just displayed a black window.  Fixes?

I did the install purely with the ATI GUI installer, and I did enable the restricted driver.  I'm using an AGP Radeon x1600 Pro 512MB.

---

### Post by Green_Star on 2007-10-24
> sudo: ./ati-driver-installer-8.42.3-x86.x86_64.run: command not found


if you get above error do the following
> 
chmod 777 ati-driver-installer-8.42.3-x86.x86_64.run

sudo: ./ati-driver-installer-8.42.3-x86.x86_64.run

---

### Post by TechSys on 2007-10-24
SInce I have a Radeon 9600 256meg vid card, figured I would go ahead and post here. I got the driver installed, pretty much went without any problems, however, I can't get compiz running at all.
Here are the outputs from fglrxinfo and glxinfo | grep direct

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6747 (8.40.4)

glxinfo | grep direct
direct rendering: Yes

glxgears does run, and has some pretty decent results. When typing in compiz, I get the following:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Not initializing the Gtk-Qt theme engine

Also the adept notifier pops up in the task bar, but has no updates. I can not close this.

Other than that, the driver seems to work very well. To get it to install, I just ran the file and waited for the screens to pop up.

Now I gotta work on the compiz stuff. ugh!

---

### Post by Green_Star on 2007-10-24
Mine is endup with some problem, i enabled the restricted drivers, rebooted the machine, when i tried fglrxinfo it showed ati drivers, then i installed this new ati drivers as discribed in above post. it installed successfully , then agian i rebooted my machine. now fglrxinfo showing mesa drivers. please see the screenshot, ati catalist window showing and the error when i tried to enable the eye candy. 

[IMG]http://img452.imageshack.us/img452/5748/screenshotle9.png[/IMG]

---

### Post by Maestro23 on 2007-10-24
Hey guys, try creating a Whitelist for the drivers in compiz-manager

/etc/xdg/compiz/compiz-manager

Add to the end of the file:

> WHITELIST="nvidia intel ati radeon i810 fglrx"

I'm running the new driver with 64-bit Gutsy with compiz, direct-rendering, etc... with no problems.

---

### Post by misfitpierce on 2007-10-25
I think I got it installed games work fine, I got direct rendering, CCC shows 8.42 on top and OpenGL says Ati Tech... 

Sometimes mouse does some weird flickering crap tho and I can get 3d effects going even adding fglrx to whitelist.

---

### Post by misfitpierce on 2007-10-25
[http://ubuntuforums.org/showthread.php?p=3619604](http://ubuntuforums.org/showthread.php?p=3619604)

Got it working with that... woooo :)

---

### Post by SupWiz17 on 2007-10-25
if i follow this will it turn on direct rendering

---

### Post by Mr. Picklesworth on 2007-10-25
It's a good idea to create a Debian package for Ubuntu.
sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/gutsy
or sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/feisty
etc.

That does not need to be (and should not be) run as root.

Now your drivers are much more tidy, and the Restricted Drivers Manager doesn't go crazy.

---

### Post by SupWiz17 on 2007-10-25
> **Mr. Picklesworth said:**
> It's a good idea to create a Debian package for Ubuntu.
sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/gutsy
or sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/feisty
etc.

That does not need to be (and should not be) run as root.

Now your drivers are much more tidy, and the Restricted Drivers Manager doesn't go crazy.
So i just type that command in and it will install my drivers alot better?

---

### Post by Mr. Picklesworth on 2007-10-25
That just creates debs, which you then have to install with dpkg or the graphical deb tool.


TechSys: I am on a Radeon 9600 Pro, and having problems with Compiz as well. When I try to enable it, I have the following behaviour:
-All windows disappear, showing only the desktop
-Display is just white, though the mouse pointer appears. It reacts to windows, so those are still present.
-Eventually, thankfully, it is disabled by the timer and I return to the boring world of regular, undecorated Ubuntu.

For me, however, DRI is not working:

grep -i AIGLX /var/log/Xorg.0.log
(**) Option "AIGLX" "true"
(**) AIGLX enabled
(EE) AIGLX: Screen 0 is not DRI capable

That, I suppose, also explains other strange behaviour with 3D things. For example, glxgears appears to have a terrible, slideshow-like performance (2 frames per second?), yet the console output says that it is around 400 FPS - which is still pretty horriffic vs. the free driver even with Compiz running, but definitely different from what was making it to the final output.

A shame that this is being such a pain. The 8.41.7 driver worked beautifully, but that one had to be installed manually.

---

### Post by elliio on 2007-10-25
Hi All,

I just managed to successfully install the new 8.42.3 driver for AMD64 on a FRESH install of the Ubuntu 7.10 Gutsy Gibbon AMD64 Distribution.

I wrote a step by step tutorial for my experience and attached it. Don't balk at the 36 steps! It's written for a Windows Convert/Ubuntu/GNU/Linux Initiate! :-)

Hope it helps some of you out there to have the instructions all in one place!

My Hardware:
Shuttle XPC P2700, AMD X2 6000+(3GHz(2)), Mushkin DDR2-800 (2GB(4))m, IBM DTLA-3070 ((30GB HDD) (for testing purposes)), Sapphire ATI Radeon HD 2600 Pro (256MB GDDR3), Logitech Classic Keyboard, Logitech MX-Revolution Mouse, Syntax Olevia LT 27 HV (27" LCD HDTV).

Note:
I added instructions for setting the Resolution of the Syntax Olevia, which was MADDENING to figure outwhen I first jumped ship from windows to Feisty!

Best of luck to you all!:popcorn:

---

### Post by laardwolf on 2007-10-27
> **misfitpierce said:**
> ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
--- SNIP ----
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.e20391

Im getting this error... Any idea on what I should do?

I got this error too.. I am using Debian, but my fix should work the same:

first, extract the installer:
[B]mkdir 8.42
sh ./ati-driver-installer-8.42.3-x86.x86_64.run --extract 8.42
cd 8.42[/B]

Then, create the missing directory, and create your package.
[B]mkdir -p common/usr/X11R6/lib/modules/dri
./ati-installer.sh 8.42.3 --buildpkg Ubuntu/gutsy[/B]

The packages should be built in the starting directory, and feel free to remove the 8.42 directory and contents when finished.

Hope this helped.

---

### Post by khristian on 2007-10-27
I couldn't get the new driver to work, and it screwed my old one. 
Every time I installed it, fglrxinfo only returned the Mesa driver. Now, when I reinstalled the Ubuntu fglrx driver from the repositories, fglrxinfo keeps showing Mesa.
This must be the shittiest release from ATI in a long time.

---

### Post by Digitallysick on 2007-10-28
when i try to manually install i get this error

cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.yV7434

---

### Post by Depressed Man on 2007-10-28
Hmm my ATI videocard is outdated (Currently using open source drivers but having modeline problems (right edge of the screen is slightly clipped off). Would the new driver have any effect on an X800 GTOII ? Kinda outdated by today's standard (It's sm 2.0, etc..)

---

### Post by Ubuntoob on 2007-10-28
Don't hold your breath at the moment.
Until they fix the driver with an update or something.

I have an X800pro and just live with the default Ubuntu driver since install (Ubuntu 7.10) for now which does everything apart from the high frame rate, visual effects, 3d activation stuff.

I have tried a few attempts at the drivers including the default automatic Ubuntu offering of the restricted drivers and like many or most of these ATi users - there are issues at the moment.

Hoping for an update soon but intend to build another system next year sometime so in no major rush..

---

### Post by sdowney717 on 2007-10-28
composite with the new driver is supposed to work, so these lines should be removed.
If you leave this, and dont run XGL server, and an XGL session,  then you wont have any desktop effects.


24. Add the following lines to the bottom of the xorg.conf file in gedit:

Section "Extensions"
        Option      "Composite" "disable"
EndSection

---

### Post by Enedok on 2007-10-28
Well, compiz still work. Thats a new one. Im unable to open catalyst control center. It says that no ati driver installed or not functioning properly. Install the correct one or use aticonfic to configure it.

```
glxinfo
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x56 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

3D games also complains that it cant find glx visuals. 

```
armagetronad
Trying to start sound. Just restart Armagetron Advanced in case of crash.
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Error: Error in bool sr_InitDisplay() in ../../src/render/rScreen.cpp:737 : 
 
Sorry, played all my cards trying to initialize your video system.
Armagetron Advanced won't run on your computer. Reason:

Couldn't set video mode: Couldn't find matching GLX visual

I'll try again from the beginning, but the chances of success are minimal.
```

Does anyone have a good option to make GXL work? Maybe a commando with aticonfig? 

Dell Inspirion 9100
ATI Mobility Radeon 9800
512 ram
Pentium 4

---

### Post by dede54 on 2007-10-28
Hi, I need an advice. I have thinkpad z60m with ati radeon moilityx600. I tried xgl+compiz but it seems  that xgl eats too much cpu. Is it make sense to install new ati driver? Another question is if suspend/hibernate works with the new driver?
Thanks for any advice, help or suggestion.
-andrzej

---

### Post by chatterbox101 on 2007-10-29
dede54 - monitoring this thread and others around the net, I suggest you wait for a couple of weeks before using this driver - hopefully, and according to the forums over at Phoronix.com they (AMD/ATI) are aware of some of the issues being reported...I have reverted back to old driver + XGL combo...I'm sure fellow forum members will be of more help than me...:KS

---

### Post by khristian on 2007-10-29
> **khristian said:**
> I couldn't get the new driver to work, and it screwed my old one. 
Every time I installed it, fglrxinfo only returned the Mesa driver. Now, when I reinstalled the Ubuntu fglrx driver from the repositories, fglrxinfo keeps showing Mesa.
This must be the shittiest release from ATI in a long time.

I solved the mesa-problem with this (my post, in other thread):
> **khristian said:**
> Another user of the XPress 1100 card. I kept getting the Mesa driver even after re-enabling the fglrx driver from the Restricted Manager. Turned out that X server was always falling back to some other free driver (ati, apm, ark).
I then removed all of the xserver-xorg-video- packages, and suddenly the X server liked the fglrx driver again!
Weird thing is, when I installed the fglrx driver via the packages generated by the ATI installer, I couldn' t start a X session because some .sh script was missing in /etc/ati (don' t remember which one now, I couldn' t reproduce the error and the ~/.xsession-errors was overwritten).
If anyone that got the new driver could post the scripts in that folder, maybe I could get it to work.
EDIT: [COLOR="Red"][SIZE="7"]**_*IT WORKS!*_**[/SIZE][/COLOR]
:lolflag:
After removing those stupid drivers that came with the xserver-xorg-video-all package, installation through the ATI installer (not with the generated packages) worked, finally.
Compiz is running well, and the only problem is the already-mentioned slow scrolling in Firefox. The maker of the tutorial should add this possibility to his post, I think.

---

### Post by Nem1976 on 2007-10-29
I have a weird issue,

I decided to just reload my gutsy Friday to get the Ati drivers working and I have done that.  And everything looks fine and I have compiz running on my X1300 w/o XGL.  But if I do a glxinfo | grep direct I get this.



direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

and Fglrxinfo gives me this.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 1.4 (2.0.6958 Release)

While my Compiz does work smoothly as well as firefox I'm wondering if something still isn't right with the system.   When I reloaded gutsy I installed the Ati drivers first before anything else and when I did the glxinfo I got direct rendering: Yes message as well as my Opengl versin string was just 2.0.6958  it didn't have the 1.4 on it.  I did all the updates to gutsy then and rebooted and it seemed to be working then the system hardlocked an when I rebooted I had the direct rendering no message then and the 1.4 Opengl showed up.

Any Ideas?

Thanks
Nem

---

### Post by rwap on 2007-10-29
I tried installing but i had the same luck as with old driver, I followed instructions to a T, I tried both ways, both times it locked up on boot, 

I look forward to a working driver.

I have a X1900 Cross Fire card 512MB

---

### Post by eddie_gordo on 2007-10-29
I was trying to install the drivers, going step by step through the tutorial in post #61, but I stopped in step 8, where I'm supposed to go to the terminal, enter the desktop and type sudo ./ati-installer.sh 8.42.3 --install.

I get the following error:
> sudo: ./ati-installer.sh: command not found


I cannot understand what I'm not doing right, I'm kind a noob..! Any help?

Thanks!

---

### Post by rcmn on 2007-10-29
> **eddie_gordo said:**
> I was trying to install the drivers, going step by step through the tutorial in post #61, but I stopped in step 8, where I'm supposed to go to the terminal, enter the desktop and type sudo ./ati-installer.sh 8.42.3 --install.

I get the following error:


I cannot understand what I'm not doing right, I'm kind a noob..! Any help?

Thanks!

make sure you can execute ati-installer.sh 8.42.3.
if in a terminal you do :
$ ls -l ati-installer.sh 8.42.3 

you should see rwx-r-x-r-x.

if not do :
$ chmod 755 ati-installer.sh 8.42.3

also make sure you are in the correct directory.

finally the you can just check if you can execute it by right clicking on the file then look in properties and then security.execute should be checked.

---

### Post by eddie_gordo on 2007-10-29
Ok, I've managed to install it through the Envy.. :P Thanks anyway! :D

Now, when I go to System -> Preferences -> Appearance and then check Extra on Visual Effects, it says that "The Composite extension is not available"... Why?

Sorry about the noobish..! :P

Thanks

---

### Post by rcmn on 2007-10-29
have you compiz installed ? if not you should search in the forum the proper Post to do
 it ...

---

### Post by eddie_gordo on 2007-10-29
I just installed it through "sudo apt-get install compiz compizconfig-settings-manager"... 

It appears "Custom" in the System -> Preferences -> Appearance and Visual Effects Tab, but that error occurs when I choose any other than "None"!

I don't have the ystem -> Preferences -> **Desktop Effects** also... I ran compiz by Alt+F2 and compiz --replace

Am I missing something here?

Thanks

---

### Post by mike868y on 2007-10-29
i have an ati radeon x300 card.. is this the right driver for me?

---

### Post by Kymus on 2007-10-29
for a few days I've been experiencing issues with the new driver.

I figured that maybe I should see about making an inquiry about it here since there seems to be a good collective knowledge base within this thread. 

simply put, it seems that when I install the driver and then add **xserver-xgl** (for compiz) my system experiences a massive slowdown. I started a thread on it a few days ago [here]("http://ubuntuforums.org/showthread.php?t=590303").

has anyone else experienced slowdown issues with this? :confused:

---

### Post by baldychap on 2007-10-29
Sorry, ignore this post. Should have read more of the thread!

---

### Post by Nem1976 on 2007-10-29
> **Kymus said:**
> for a few days I've been experiencing issues with the new driver.

I figured that maybe I should see about making an inquiry about it here since there seems to be a good collective knowledge base within this thread. 

simply put, it seems that when I install the driver and then add **xserver-xgl** (for compiz) my system experiences a massive slowdown. I started a thread on it a few days ago [here]("http://ubuntuforums.org/showthread.php?t=590303").

has anyone else experienced slowdown issues with this? :confused:


You don't need to have xgl with this new driver.  I'm not running xgl for my compiz.

---

### Post by khristian on 2007-10-29
> **eddie_gordo said:**
> Ok, I've managed to install it through the Envy.. :P Thanks anyway! :D

Now, when I go to System -> Preferences -> Appearance and then check Extra on Visual Effects, it says that "The Composite extension is not available"... Why?

Sorry about the noobish..! :P

Thanks
You have to make sure that:
1. You installed the latest version of the ATI driver, and not the one from the Ubuntu repositories, provided by the restricted-manager;
2. In xorg.conf, you need these lines:
```
Section "Extensions"
	Option		"Composite"	"1"
EndSection
Section "ServerFlags"
	Option	    "AIGLX" "On"
EndSection
```
Search for them and change them to this, if they already exist.
3. Make sure xserver-xorg is not installed (run sudo apt-get remove xserver-xorg).
4. If any change is made, reboot the X server (ctrl+alt+backspace, or log out and back in), run compiz and, if it worked, be happy :)

---

### Post by dark_harmonics on 2007-11-15
> **Nem1976 said:**
> I have a weird issue,

I decided to just reload my gutsy Friday to get the Ati drivers working and I have done that.  And everything looks fine and I have compiz running on my X1300 w/o XGL.  But if I do a glxinfo | grep direct I get this.



direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

and Fglrxinfo gives me this.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 1.4 (2.0.6958 Release)

While my Compiz does work smoothly as well as firefox I'm wondering if something still isn't right with the system.   When I reloaded gutsy I installed the Ati drivers first before anything else and when I did the glxinfo I got direct rendering: Yes message as well as my Opengl versin string was just 2.0.6958  it didn't have the 1.4 on it.  I did all the updates to gutsy then and rebooted and it seemed to be working then the system hardlocked an when I rebooted I had the direct rendering no message then and the 1.4 Opengl showed up.

Any Ideas?

Thanks
Nem

I have this same problem :( Any solutions?

---

### Post by dark_harmonics on 2007-11-25
Bump

---

### Post by Peter09 on 2007-11-26
Thought I would give you my experience here- it may help.

I have been struggling to get this driver to work, I sometimes had success but never with performance and I could never get the ATI Control Center to work, or glxgears to work.

I then went to this thread -- [http://ubuntuforums.org/showthread.php?t=588423&page=9](http://ubuntuforums.org/showthread.php?t=588423&page=9) and implemented the recommendations by khristian. (its earlier in the topic)

However, removing the xserver-org package stopped me running an xterm (through startx).

So - next thing I did was to reinstall the xserver-org package. I tried to run aticonfig but that requested another package (cannot remember name) so installed that.

Then ran the ATI installer again (this is all from the recovery mode command prompt). Note that you will need to make the installer executable.

And, Blat -it all works, ATI Control panel - the lot. :)

Now the next problem I have is that I cannot login normally because my greeter application fails, but where i do not know. (been having problems with this for some time). :(

So, it looks like (for me) adding the Sections, as recommended by Khristian and reinstalling the xserver did it. Whether just adding the sections would have worked I do not know.

Hope this helps.

---

### Post by Peter09 on 2007-11-26
I actually had this working, Glxgears at 3000+fps and the ATI Catalyst control center working.... and then for no reason at all it stopped. Glxgears now crashes the Xserver and The ATI control center does not work.


Bugger......

---

### Post by JohnLM_the_Ghost on 2007-11-27
Anyone there can tell me how to install the driver on Dapper?

I did run the install, and everything seemed to go smoothly.
Though it obviosly didn't cause all GL stuff runs around 1 FPS. :D
fglrx returns Mesa stuff and glrxinfo says Direct Rendering: no

It would be nice to have plain and simple explanation on installing this driver.
I'm using Ubuntu Dapper with my Radeon X1600 Pro, and have used fglrx driver which now seems a bit broken after tinkering with new driver.

Please post HowTo (and preferably send a copy on PM cause its a bit of mess in this thread) or a link to one. Thank You!

---

### Post by Linux Gabe on 2008-02-08
is that something that would work for an x1600? currently im using ati-driver-installer-8-01-x86.x86_64. 

I recently gotten excited about Linux again thanks to this video 
[http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

---

### Post by Sethalos on 2008-02-26
I have a Radeon 9100 Mobility video card in my HP Pavilion zv5000 laptop. I followed the instructions for installing the drivers and it didn't work for me.  Here is the information I received after running the fglrxinfo command:

sethalos@sethalos-laptop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

When I initially rebooted, it started up in safe graphics mode.

Here is my xorg.conf file:


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1440x900" "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


I've been trying to get my drivers for my card installed now for about 3 weeks and I'm just not having any luck.

Thanks 
Seth.

---

