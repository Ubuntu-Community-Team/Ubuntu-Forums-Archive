---
title: "Custom kernel &amp; fglrx &amp; wireless"
date: 2006-07-05
forum: General Help
---

### Post by ehula on 2006-07-05
Could someone please give me a hand with getting the fglrx driver and wireless driver working with a custom kernel. I am able to successfully compile a kernel (2.6.16 & 2.6.17), but I am not able to get fglrx or wireless working.

I have a Thinkpad T43p which has a ATI Mobility FireGL V3200 and an IBM PRO/Wireless 2915ABG MiniPCI Adapter.

I have fglrx and wireless running fine in Dapper with 2.6.15, but there are a few reasons I would like to run a newer kernel:
1. USB support. USB seems to be broken in Dapper, and I need to sync my Palm to evolution.
2. Suspend/Hibernate. This seems to be hit and miss in Dapper, mostly related to how many apps I have running when trying to suspend/hibernate.

Like I said above, I have successfully compiled newer kernels, but I don't know how to get fglrx and wireless support working. Ideally, I would like a solution that would allow me to easily update fglrx and wireless drivers using Synaptic as they come out in the repos, if that is possible.

---

### Post by lamego on 2006-07-06
Regarding the fglrx if you are using a custom kernel you will need to install it manually using the ATI provided package.

Please read the [Using the drivers from ati.com]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") section.

Having a custom kernel means you can't get the updates for this drivers from synaptic, the packages on synaptic are built for the ubuntu specific kernel versions.

---

### Post by ehula on 2006-07-06
[QUOTE=lamego]Regarding the fglrx if you are using a custom kernel you will need to install it manually using the ATI provided package.

Please read the [Using the drivers from ati.com]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") section.

Having a custom kernel means you can't get the updates for this drivers from synaptic, the packages on synaptic are built for the ubuntu specific kernel versions.[/QUOTE]
Thanks, that's great feedback. I understand the issue about the Ubuntu binary drivers built for specific kernel versions.

Is it possible to use the fglrx-kernel-source package from Ubuntu instead of the binary from ATI? If so, how?

---

### Post by ehula on 2006-07-07
> **lamego said:**
> Regarding the fglrx if you are using a custom kernel you will need to install it manually using the ATI provided package.

Please read the [Using the drivers from ati.com]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") section.
OK, I have tried manually installing the ATI drivers, but am having a problem when I get to the following command:

> sudo module-assistant build fglrx

The build fails with the following error message:

> dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17-ck1.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/kernel-headers-2.6.17-ck1 SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/kernel-headers-2.6.17-ck1'
/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17-ck1'
make: *** [build] Error 2

Any ideas? I think I am getting close!

---

### Post by d3x7r0 on 2006-07-07
If anyone can help him with this you'll be helping me aswell. I've been trying to get the 2.6.17 kernel working for me since it's the only one where the agpgart supports my chipset and I get a similar error. The missing file is Makefile.lib.c

---

### Post by ehula on 2006-07-09
Bump...

Anyone successfully use the fglrx proprietary drivers from ATI with compiled kernel 2.6.17?

---

### Post by ehula on 2006-07-10
Fixed!

To get the ATI drivers working, I realized that I was missing the Makefile.cpu file from my kernel compile. I hope I am not missing more files. I extracted the missing file from the source tree at kernel.org and copied it into my /usr/src/linux/arch/i386 directory.

Then I got another error when trying to install the ATI driver...missing Makefile.lib.c. Running a make on the /usr/src/linux/scripts directory solved that problem and allowed me to install the ATI driver.

As far as the wireless driver goes, I just needed to download the ipw2200 firmware that corresponded with the ipw2200 driver in my kernel. I had to create a firmware directory corresponding to my version of the kernel in /lib/firmware, and then I copied the firmware files into that directory and then my wireless card worked fine.

Hope this helps someone out there.

---

### Post by d3x7r0 on 2006-07-10
> **ehula said:**
> Fixed!

To get the ATI drivers working, I realized that I was missing the Makefile.cpu file from my kernel compile. I hope I am not missing more files. I extracted the missing file from the source tree at kernel.org and copied it into my /usr/src/linux/arch/i386 directory.

**Then I got another error when trying to install the ATI driver...missing Makefile.lib.c. Running a make on the /usr/src/linux/scripts directory solved that problem and allowed me to install the ATI driver.**

As far as the wireless driver goes, I just needed to download the ipw2200 firmware that corresponded with the ipw2200 driver in my kernel. I had to create a firmware directory corresponding to my version of the kernel in /lib/firmware, and then I copied the firmware files into that directory and then my wireless card worked fine.

Hope this helps someone out there.

THANK'S!!! That's was the only thing I couldn't get over so now I'm gonna try it again :D

---

### Post by xXx 0wn3d xXx on 2006-07-10
If that doesn't work install fglrx-kernel-source.
> sudo apt-get install fglrx-kernel-source

---

### Post by ehula on 2006-07-11
> **xXx 0wn3d xXx said:**
> If that doesn't work install fglrx-kernel-source.
I have seen you suggest this in many, many threads, but have you actually got this to work for yourself? I wonder if anyone has got this to work? I have tried, but installing this package only creates /usr/src/fglrx.tar.bz2. Nothing else happens. The .deb package appears to be broken.

BTW, I am running kernel 2.6.17 from kernel.org with the ck1 patch applied.

I was finally able to get this to work manually, but it isn't pretty. Firstly, after much experimentation, I realized that you also need the package xorg-fglrx-driver (maybe obvious for some, but I didn't see it documented anywhere.) I unpacked fglrx.tax.bz2. Then I ran a make in /usr/src/modules/fglrx. Next I ran an insmod of /usr/src/modules/fglrx/fglrx.ko (for some strange reason, I have to specify the whole path. I have tried copying the .ko to /lib/modules/$(uname -r)/kernel/drivers/video, but insmod can't seem to find it there). Finally I modified xorg.conf to call "fglrx" instead of "ati" and it worked. Note that I have to manually run insmod after every reboot!

Based on your many posts that say to just install fglrx-kernel-source, I am assuming either: I am doing something wrong, or fglrx-kernel-source is broken and you have never tried it.

---

### Post by inverarity on 2006-07-15
to ehula: Many, many thanks!  Based on your advice I now have fglrx installed and running splendidly.  Just in case it helps anybody else, I did find your instruction to do a make on /usr/src/linux/scripts slightly confusing.  I my case I had to run the following commands for the make scripts to execute without errors:

```

cd /usr/src/linux/
make scripts/

```

That should run all the make targets inside of the scripts directory.  The bizarre thing for me was that it still didn't create the Makefile.lib.c file, and in fact there was still a broken symlink to scripts/Makefile.lib.c inside of the /usr/src/linux directory, but since I was out of ideas I ran module-assistant build,install fglrx again just for kicks and sure enough it worked perfectly.

Thanks a lot!

P.S. if ```
make scripts/
``` doesn't work for someone, perhaps try ```
make scripts/Makefile.build
``` (also from the /usr/src/linux) directory.  If that doesn't work, try targeting some of the other Makefile.* that are in the scripts directory.  Since I was expecting to see Makefile.lib.c appear as the measure of success, I tried a number of different make targets and I'm not totally certain which one actually got module-assistant to work.

---

### Post by MrMojoRising on 2006-07-19
> **ehula said:**
> Fixed!

To get the ATI drivers working, I realized that I was missing the Makefile.cpu file from my kernel compile. I hope I am not missing more files. I extracted the missing file from the source tree at kernel.org and copied it into my /usr/src/linux/arch/i386 directory.


How would one go about doing that? I have the same problem.

I'm glad i'm not alone :)

---

### Post by damo21 on 2006-08-01
.

---

### Post by damo21 on 2006-08-01
Okay,
I worked out how to fix this problem.  I use pentium-m laptop with 2.6.17-ck1 and 8.27.10 fglrx!

The crux of the solution is ensuring that the command used to compile the kernel is correct, so that the fglrx module is recognised during the compile.  Also, to make sure a clean fglrx source module exists in the correct directory prior to compiling the kernel.  It now works with my Radeon Mobility 9000 (M9) seamlessly.

Suppose you wish to upgrade from 2.6.15 dapper standard kernel to 2.6.17-ck1 with fglrx.
Require the following files:
2.6.17 vanilla kernel from kernel.org: linux-2.6.17.tar.bz2
latest ck patch for 2.6.17: patch-2.6.17-ck1.bz2
8.27.10 version of ATI installer: ati-driver-installer-8.27.10-x86.run

Place the above 3 files into /usr/src

As a standard user execute the following commands:

```
sudo -s
cd /usr/src
tar jxfpv linux-2.6.17.tar.bz2
bunzip2 patch-2.6.17-ck1.bz2
mv linux-2.6.17 linux-2.6.17-ck1
cd linux-2.6.17-ck1
patch -p1 < ../patch-2.6.17-ck1
```

At this stage it would be a good idea to follow one of the existing guides for tweaking the kernel .config file, but it is important to leave the kernel revision EMPTY so that make menuconfig sees "v2.6.17-ck1" in the top left.  Secondly, ensure that you <*> your root filesystem type or you will get unbootable system!! 

Now we MUST do the following, (still as the root user with sudo -s)

```
cd /usr/src
rm -f fglrx*.deb
rm -fr ./modules/fglrx
chmod +x ati-driver-installer-8.27.10-x86.run
export PATH=$PATH:.
dpkg -r fglrx-kernel
dpkg -r fglrx-kernel-source
dpkg -r fglrx-control
dpkg -r xorg-driver-fglrx
./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper
dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
dpkg -i fglrx-kernel-source_8.27.10-1_i386.deb
dpkg -i fglrx-control_8.27.10-1_i386.deb
tar jxfpv fglrx.tar.bz2
cd linux-2.6.17-ck1
make-kpkg clean
make-kpkg --initrd kernel_image kernel_headers modules_image
```

Now you have 3 new debs to install...
including custom fglrx-kernel module !!

```
dpkg -i kernel-image-2.6.17-ck1_10.00.Custom_i386.deb
dpkg -i kernel-headers-2.6.17-ck1_10.00.Custom_i386.deb
dpkg -i fglrx-kernel-2.6.17-ck1_8.27.10-1+10.00.Custom_i386.deb
ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

Now generate a nice clean xorg.conf file with aticonfig:```
sudo aticonfig --initial
``` and perhaps edit /etc/X11/xorg.conf and put the following in the Device section:
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "XAANoOffscreenPixmaps"
	Option	    "OpenGLOverlay" "off"
EndSection
```

Good idea to REBOOT into your new kernel now but X will fail until you write:

```
sudo depmod -a
```

Now final reboot into new kernel with fglrx enabled

:D :D :D :D :D

---

### Post by damo21 on 2006-08-01
After a reboot i get:
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.27.6)
```

```
uname -a
Linux flop 2.6.17-ck1 #1 PREEMPT Tue Aug 1 19:58:43 EST 2006 i686 GNU/Linux
```
:D :D

---

### Post by EisenPM on 2006-08-04
thanks for the good how-to, unfortunately it didn't work for me. fglrxinfo says still mesa... and xorg.0.log states

[drm] failed to load kernel module "fglrx"

what went wrong? i did everything exactly as you posted by copy&paste and there were no error messages during the whole thing. the kernel boots, x is starting...

---

### Post by damo21 on 2006-08-04
I am trying to delete this post because I incorporated the changes into the post above :-k

---

### Post by machoo02 on 2006-08-06
> **EisenPM said:**
> thanks for the good how-to, unfortunately it didn't work for me. fglrxinfo says still mesa... and xorg.0.log states

[drm] failed to load kernel module "fglrx"

what went wrong? i did everything exactly as you posted by copy&paste and there were no error messages during the whole thing. the kernel boots, x is starting...

I am having the same problem here.  I followed damo's advice to the letter, and am using an xorg.conf file that worked with the fglrx driver from the repositories.  damo: how did you know how to put in that particular symlink?

---

### Post by EisenPM on 2006-08-06
> **machoo02 said:**
> I am having the same problem here.  I followed damo's advice to the letter, and am using an xorg.conf file that worked with the fglrx driver from the repositories.  damo: how did you know how to put in that particular symlink?

I did the changes that damo wrote and fglrxinfo still said mesa, but the 2D rendering in KDE was faster! but still, the module wasn't loaded.

then, i entered 

```
depmod
```

in order to reconfigure the module dependencies and now fglrx is working properly! good luck!

---

### Post by machoo02 on 2006-08-06
Thanks for the depmod tip.  Working great now.  :-D

---

