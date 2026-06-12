---
title: "ATI 8.42.3 this was only guide that worked for me"
date: 2007-10-24
forum: General Help
---

### Post by sdowney717 on 2007-10-24
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

scott@scott-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6958 Release

scott@scott-desktop:~$ glxgears
10204 frames in 5.0 seconds = 2040.770 FPS
11142 frames in 5.0 seconds = 2228.317 FPS
9162 frames in 5.0 seconds = 1832.156 FPS
14568 frames in 5.1 seconds = 2845.380 FPS
14378 frames in 5.0 seconds = 2874.939 FPS
scott@scott-desktop:~$ fgl_gears
bash: fgl_gears: command not found
scott@scott-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2872 frames in 5.0 seconds = 574.400 FPS
2757 frames in 5.0 seconds = 551.400 FPS
scott@scott-desktop:~$

---

### Post by sdowney717 on 2007-10-24
compiz working now for my 9600

Dont even goto restricted drivers in system, the menu item for restricted driver management will remain unchecked

I did add the ATI catalyst to the install list in his instructions
scott@scott-desktop:~$ sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb fglrx-amdcccle_8.42.3-1_i386.deb



scott@scott-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by sdowney717 on 2007-10-24
posted instructions just in case the site goes away.

   1. Remove Xgl (whoohoo) (if present)

      sudo apt-get remove xserver-xgl


   2. Remove the old driver (if present)

      Go to System &#8594; Administration &#8594; Restricted Drivers Manager and choose disable.

      Alternatively remove it yourself:

      sudo apt-get remove xorg-driver-fglrx


   3. Delete old fglrx debs (might not be necessary)

      sudo rm -f /usr/src/fglrx-kernel*.deb


   4. Blacklist old fglrx module

      sudo gedit /etc/default/linux-restricted-modules-common

      And insert fglrx - it should look like this then:

      DISABLED_MODULES="fglrx"


      Alternatively remove the linux-restricted-modules-* package for your kernel (that's what I did, because I don't need them - don't do this, if you use an Atheros chip).


         1. You may want to reboot now. I did.


   5. Download the driver installer to your home folder

      wget [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)


   6. Install necessary packages

      sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic


   7. Create .deb packages

      bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy


   8. Install .deb packages

      sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb

(I added the control center to the list this way)
scott@scott-desktop:~$ sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb fglrx-amdcccle_8.42.3-1_i386.deb

   9. Compile kernel module

      sudo m-a prepare,update

      sudo m-a build,install fglrx-kernel

      sudo depmod


  10. Set up the driver

      sudo gedit /etc/X11/xorg.conf


      Make sure "fglrx" is set for the Driver in the Section "Device".

      And if present, remove (whoohoo again)

      Section "Extensions"

              Option        "Composite"        "0"     # or "Disable"

      EndSection

      As well as

      Section "ServerFlags"

              Option        "AIGLX"            "off"

      EndSection


  11. Reboot


  12. Enjoy

      SKIP_CHECKS=yes compiz

      (necessary because fglrx is not on Ubuntu's whitelist)

      If it works, do this:

      mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

      This will create a file in your home folder which makes sure that Compiz will run without the above prefix from then on.



Autor: Forlong
Kategorie: keine
23. 10. 07 - 22:41 Uhr
1 Empfehlung | 6 Kommentare

Schlagworte:

---

### Post by sdowney717 on 2007-10-24
also, if you get videos playing only when full screen selected. Then it has to do with catalyst control center settings. I have mine set to clone with the monitor as 1 and TV as 2

I can see video in windowed and normal screen on computer monitor. Before, it was full screen only and strange flashing.

Video will play on monitor and not on TV. 
 TV out  is black and white.
In XP, this same setup gives me color in TV out, so it is software problem.
Plus switching displays is buggy, IMO in linux.

---

### Post by fishwithapipe on 2007-10-24
why are you disabling aiglx??? in the new driver this is supported!

---

### Post by HornedBeast on 2007-10-24
> And if present, remove (whoohoo again)

Section "Extensions"

Option "Composite" "0" # or "Disable"

EndSection

As well as

Section "ServerFlags"

Option "AIGLX" "off"

EndSection


Says to REMOVE that - not add it. Maybe you didn't read the entire article.

---

### Post by sdowney717 on 2007-10-24
he said to REMOVE aiglx = off
so, it is not off then is it.

---

### Post by sdowney717 on 2007-10-24
Update, if you play around with svideo out in the catalyst control center, and when running  compiz 
get a horribly mangled scrambled screen, then go into synaptic and remove the fglrx catalyst control center amdcc.

I simply uninstalled it completely incuding configs. It must have written some nasty config that compiz could not deal with.

If anyone has any ideas?

---

### Post by sdowney717 on 2007-10-24
another update. If you cant see a movie video in windowed mode while running compiz, then change video to use x11 instead of Xv.
smplayer lets you change this in preferences.

Can you get Xv to work windowed?

---

### Post by Chonnawonga on 2007-10-24
Thanks so much! This is all working really well for me.

Video in X11 seems to be the way to go for now. Thanks for that tip, too.
:)

---

### Post by simeli on 2007-10-25
i did as described but i just don't get a fglrx module loaded. what else can i do? there's no error message though. i'm stuck.

---

### Post by sdowney717 on 2007-10-25
what driver is loading for you?
what is your card model?

I had started oiff with ENVY. 
ENVY seems to be doing what these instructions are doing yet by an automated script. 
You get driver 8.40.4 until he updates the script for the newest  driver.
Try ENVY, if it loads 8.40.4 then at least you know your card is supported.
Then perhaps try loading this new driver again.

---

### Post by Saruk on 2007-10-27
Hi all

First off, I'm totally new to Ubuntu :) I usually run openSuSE but like what I see. I'm trying to get these ATI drivers to work. I've tried for 3 days to get them to work..lol I'm running an AMD 64 X2 with an ATI x1300. I've tried everything I can think of but keep getting this build error:

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
if [ -f /tmp/fglrx.ZO7326/debian/control.template ]; then \
                cat /tmp/fglrx.ZO7326/debian/control.template > /tmp/fglrx.ZO7326/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.ZO7326/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.ZO7326/debian/driver.$i > \
              /tmp/fglrx.ZO7326/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.ZO7326/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.ZO7326/debian/10fglrx.template > /tmp/fglrx.ZO7326/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.ZO7326/debian/fglrx.default ]; then \
          mv /tmp/fglrx.ZO7326/debian/fglrx.default /tmp/fglrx.ZO7326/debian/fglrx; \
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
if [ -f /tmp/fglrx.ZO7326/debian/control.template ]; then \
                cat /tmp/fglrx.ZO7326/debian/control.template > /tmp/fglrx.ZO7326/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.ZO7326/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.ZO7326/debian/driver.$i > \
              /tmp/fglrx.ZO7326/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.ZO7326/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.ZO7326/debian/10fglrx.template > /tmp/fglrx.ZO7326/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.ZO7326/debian/fglrx.default ]; then \
          mv /tmp/fglrx.ZO7326/debian/fglrx.default /tmp/fglrx.ZO7326/debian/fglrx; \
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
rm -f /tmp/fglrx.ZO7326/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.ZO7326/debian/control
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
Removing temporary directory: fglrx-install.Yq7245


I guess I'm lost and it's probably really simple..

Thanks for the help (in advance)..

Chuck

---

### Post by jimminy_kriket on 2007-10-27
you tried this right?

6. Install necessary packages

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

Other than that i dont know. something is messing with your package generation.

---

### Post by Saruk on 2007-10-27
> **jimminy_kriket said:**
> you tried this right?

6. Install necessary packages

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

Other than that i dont know. something is messing with your package generation.

Yep. I did. I've reinstalled atleast 8 times to make sure all was clean. I'm now using the restricted drivers but can only get 800x600. I've even tried installing all of the xservers for ati/fglrx etc and then following the instructions..

But thanks... I just know I'm missing something somewhere.lol

---

### Post by eigenlambda on 2007-10-28
Actually, I'm having the same problem compiling fglrx 8.42.3.  
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256

---

### Post by eigenlambda on 2007-10-28
Just to let everybody know, this one is SOLVED.  the answer is at the end of [http://ubuntuforums.org/showthread.php?p=3649250]("http://ubuntuforums.org/showthread.php?p=3649250")

---

### Post by therealknewman on 2007-11-08
Followed these instructions, but fglrxinfo reports that I'm still using the Mesa driver. ATICCC says the same thing, my OpenGL renderer, provider and version are Mesa. How can I make it use the ATI driver? ```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

---

