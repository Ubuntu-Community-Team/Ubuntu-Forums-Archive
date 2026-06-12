---
title: "ATI and DRI, It does work."
date: 2008-06-26
forum: General Help
---

### Post by shadowbranch on 2008-06-26
Ok, I've finally decided to settle the arguments of how to get DRI to work with ATI. We all know that nVidia drivers work great when you hit the site, download them, and run the installer. I personally have nVidia on my desktop at work. But, my laptop, like so many others came with and ATI card. 

Now I thought for a long time that I was just SOL and couldn't do a thing about my graphics. Well, I really wanted Beryl to work, since it was the coolest thing at the time. I hit the forums and started reading. I tried all kinds of methods found in different combinations. I eventually found an xorg.conf setup that worked for me. But I figured, that ATI with it's proprietary drivers had to have a better way, other that just trying to piece crap together to produce a work around that may or may not work on someone else's system. Well, I got the ATI drivers and ran the installer. Even upon selecting to use the driver, I still got poor performance. Well, this rather ticked me off since ATI should have working drivers. So I again found was to use the ATI driver with an xorg configuration that produced good graphic speeds.

Not too long after completing that, I decided that I was tired of work arounds and patchwork code. So I set off reading. Ain't it great. It's amazing what you can find while reading docs! Now to the point of this story. ATI drivers work and they kick butt! I get 1500fps when running glxgears and I'm running the FGLRX drivers from ATI in DRI mode. How hard was it? Not hard at all, just read the docs that came with the driver and it explained it all. So, for all the people that fight and argue over the easy way to do it, here is the instructions, the exact way I do them to make my card work.

**Step 1:** Go to the ATI site, download the ATI driver.

**Step 2:** Open a terminal, switch to the super-user account(type: su -) or use sudo, if you've set it up. Enter your password if needed. Run the ATI driver installer using: sh ati-driver-installer*.run (assuming the file is named similar.

**Step 3:** Follow all instructions to get the driver installed. Basically, just click Next until you are finished.

**Step 4:** Once back at the terminal prompt, type: aticonfig --initial
This will run the ATI configuration script to setup and initial configuration. This will setup display for a single monitor. If you have dual montitors or tv out, trade --initial for --help. Then find your settings and run the command with those.

**Step 5:** Here's the tricky part. Not really, just wanted to scare ya. Change to the ATI driver directory by issuing the following command: cd /lib/modules/fglrx/build_mod
Once here, type: ./make.sh
Once it runs it will tell you what to do next, but I'll still let you know just incase. This step builds a kernel module that will allow your video card to be properly controlled by linux.

**Step 6:** Type: cd .. or cd /lib/modules/fglrx
Once in the main fglrx directory, type: ./make_install.sh
this will install the new kernel module. Now, just restart your system or if you have X setup to restart on logout, logout by normal methods or press CTRL+ALT+BACKSPACE.

Now once you've logged back in, you should be running in DRI mode and if you open a terminal and type glxgears, it should look great with now lagging. If not, well, double check your steps, make sure you are running the fglrx driver, and if it still doesn't work, leave a message and I'll help you out.

This should end all the crap about ATI. They put out a good driver, people just need to read the instructions. The difference between the ATI installer and the nVidia installer is, the nVidia installer builds the kernel module right there and ATI doesn't. Well, I hope this has helped.

---

### Post by prshah on 2008-06-26
> **shadowbranch said:**
> 
 I get 1500fps when running glxgears and I'm running the FGLRX drivers from ATI in DRI mode. 
**Step 1:** 
**Step 2:**
**Step 3:**
**Step 4:**
**Step 5:**
**Step 6:**


Wow, I don't have ATI, but such a nice guide makes me want to get one. Good hard work distilled into a few words and fewer steps. Kudos.

Just a suggestion: Maybe you should post expected outputs (trimmed, of course) so that others can know if they are getting some unexpected results. Take a look at my [http://ubuntuforums.org/showthread.php?t=756260&highlight=netgear](http://ubuntuforums.org/showthread.php?t=756260&highlight=netgear) thread for ndiswrapper for an example.

---

### Post by bluelamp999 on 2008-06-26
Hi ShadowBranch,

Followed your steps exactly (except for 'aticonfig --initial=dual-head' as I've a dual monitor setup) and all went fine until step 6 when I get the below error...


mike@LATITUDE-810:/lib/modules/fglrx$ sudo ./make_install.sh
- recreating module dependency list
- trying a sample load of the kernel modules
ERROR: Module fglrx does not exist in /proc/modules
done.
mike@LATITUDE-810:/lib/modules/fglrx$


Any ideas what might be amiss?

Thanks

8.04
2.6.24-19-generic
GNOME 2.22.2
ATI Mobility Radeon X300 on Dell Latitude D810


ATI module generator V 2.0
==========================
initializing...
build_date =Thu Jun 26 18:51:02 IST 2008
uname -a =Linux LATITUDE-810 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.24-19-generic
uname -v =#1 SMP Wed Jun 18 14:43:41 UTC 2008
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x 36 root root 4096 2008-06-26 18:46 /usr/include
.
total 28
drwxr-sr-x  2 root src  4096 2008-06-26 18:46 ati
drwxr-xr-x 20 root root 4096 2008-04-22 18:54 linux-headers-2.6.24-16
drwxr-xr-x  6 root root 4096 2008-04-29 19:17 linux-headers-2.6.24-16-generic
drwxr-xr-x 20 root root 4096 2008-06-10 18:27 linux-headers-2.6.24-18
drwxr-xr-x  6 root root 4096 2008-06-10 19:12 linux-headers-2.6.24-18-generic
drwxr-xr-x 20 root root 4096 2008-06-23 20:07 linux-headers-2.6.24-19
drwxr-xr-x  6 root root 4096 2008-06-23 20:08 linux-headers-2.6.24-19-generic
lrwxrwxrwx  1 root root   23 2008-06-10 19:11 vboxdrv-1.6.2 -> ../share/virtualbox/src
.
file /lib/modules/2.6.24-19-generic/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h says: MODVERSIONS=1
.
CC=gcc
cc_version=
found major but not minor version match for gcc and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx 1 root root 18 2008-06-26 18:51 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
build succeeded with return value 0
.
duplicating results into driver repository...
target location: /lib/modules/fglrx
stripping the debug info of kernel module
copying fglrx.ko
copying logfile of build
*** end of build log ***

---

### Post by ex.hav0k on 2008-06-26
> **bluelamp999 said:**
> Hi ShadowBranch,

Followed your steps exactly (except for 'aticonfig --initial=dual-head' as I've a dual monitor setup) and all went fine until step 6 when I get the below error...


mike@LATITUDE-810:/lib/modules/fglrx$ sudo ./make_install.sh
- recreating module dependency list
- trying a sample load of the kernel modules
ERROR: Module fglrx does not exist in /proc/modules
done.
mike@LATITUDE-810:/lib/modules/fglrx$


Any ideas what might be amiss?

Thanks

8.04
2.6.24-19-generic
GNOME 2.22.2
ATI Mobility Radeon X300 on Dell Latitude D810

this makes me wonder as i also have an x300mobile on a dell inspiron.  but i was just looking over at ati's website and saw:
[quote=ATI's Website]The following packages must be installed in order for the Catalyst™ Linux driver to install and work properly:

    * XFree86-Mesa-libGL
    * libstdc++
    * libgcc
    * XFree86-libs
    * fontconfig
    * freetype
    * zlib
    * gcc 
[/quote]

do you have all of that installed?  if so, i hope someone can figure out your problem, because i bet ill run into the same thing.

ex.hav0k

---

### Post by bluelamp999 on 2008-06-26
Damned if I know!

Bit of a noob...

The only real pain with Ubuntu/Linux is all this xorg.conf stuff, everything else 'just works'...

---

### Post by el-mar01 on 2008-06-26
Whats the significance of DRI ??

---

### Post by ex.hav0k on 2008-06-26
> **bluelamp999 said:**
> Damned if I know!

Bit of a noob...

The only real pain with Ubuntu/Linux is all this xorg.conf stuff, everything else 'just works'...

go to synaptic and search for each of those packages and make sure they're installed.  (System>Admin>Synaptic)

---

### Post by ex.hav0k on 2008-06-26
heh, well, i did it.  i ****** up my system.

i followed the directions here:  [http://wiki.cchtml.com/index.php/Category:Installation_Documentation](http://wiki.cchtml.com/index.php/Category:Installation_Documentation)

i got down to reboot, thinking i had done everything right, my system starts back up, i log in and all i get is a blank white screen.  also, i ran fglrxinfo and it's bringing up mesa and not ati.  my xorg.conf file doesn't look right either.

the only thing i'm wondering about is if i should try to undo what i've done or try to fix it from here.

---

### Post by Xavier Oddmon on 2008-06-27
Is any of this necessary in Hardy Heron? I simply enabled the driver from the restricted drivers menu, and I get 2852.968 fps on my HD 2600 (2186 with CF running, and noticible flicker)

---

### Post by bluelamp999 on 2008-06-27
I've gone back to the non-restricted driver.

Life's too short to be frustrated again by trying to get fglrx working reliably across dual monitors.

If anybody out there has managed to get fglrx running on a dual monitor setup (different screen resolutions) with a Mobility Radeon X300 on a Dell Latitude D810 I'd be delighted to hear.

I reckon it can't be impossible but I just don't want to waste more of my time dicking around with the dreaded xorg.conf.

I've tried Envy to no avail.

Surely it can't be beyond the abilities of the extremely talented Ubuntu developers to come up with something like the Windows Display Properties applet?

I just really, really wanna run Google Earth as easily as I can in Windows on the same setup...

---

### Post by Forlong on 2008-06-27
> **Xavier Oddmon said:**
> Is any of this necessary in Hardy Heron?
No.

---

### Post by shadowbranch on 2008-06-27
bluelamp999 - I'll look into it and see what I can turn up. I've only configured this for Single head. Although once configured for single head, I used the ATI Catalyst software to output to my second monitor off my laptop and it worked fine. Again, I'll look into it and see what I can turn up. I did see that once when I was doing it before, just don't remember how I fixed it.

prshah - Thanks for the advice. I'll post up my commands and some brief output that they should return.

So far, I have had this work on all Single head configurations on desktops and laptops. These all used the Newer cards. The older cards can usually use the Xorg radeon driver and function properly. Most of the 9200 cards can use the radeon driver and get good graphics. This is mostly a fix for all us people with cards made in the last year or so. Below is my Xorg config file. You'll notice nothing special about it.

```

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
	Option      "SHMConfig" "true"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

There is no special additions. The driver just works, once the kernel module is installed.

The purpose of DRI is for direct access to the video card to allow for fast speeds and good graphics. You basically can't run compiz or beryl properly without DRI. There are workarounds, but they fail to meet up to the standards.

---

