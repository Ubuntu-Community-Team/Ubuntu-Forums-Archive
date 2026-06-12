---
title: "Bug for some graphics cards from Silicon Integrated Systems / SIS solved in 14.04"
date: 2014-04-06
forum: General Help
---

### Post by mörgæs on 2014-04-06
Cards from Silicon Integrated Systems (SIS) are a frequent topic for discussion in Ubuntuforums. They were popular around 2001-5, and many of these computers are still suitable for light use. 

Up to and including 12.04 there was no problem here, but the Xorg environment used in Buntus after 12.04 did not support some of the SIS cards out of the box. Many a thread has been posted here asking what to do.

The problem was a broken xserver-xorg-video-sis package. A patch for most of the affected cards has been available for a long time, and normally the people maintaining Xorg would receive such a patch and fix xserver-xorg-video-sis so all distros built on Xorg would get fixed automatically. 

That didn't happen. 

Long story short, with the package from Xorg still being buggy the options were

[LIST=1]
[*]using 13.10 with hardware accereration disabled
[*]using 13.10 with the patch applied through a PPA from Temüjin
[*]using a 12.04-based distro like Bodhi Linux
[/LIST]
For most beginners the easiest solution was 3). The advice has been more or less a standard answer (at least my standard answer) when a SIS problem was posted.

From 14.04 the Buntu repositories have been upgraded with the fix. This makes Buntu 14.04 (and derived distros) the only new distro that I know of which supports SIS cards out of the box - or out of the bugs - with hardware acceleration. 

I'm posting here and not in the development forum in order to reach people answering posts, not people testing. Now it's time to un-learn the 12.04 routine answer and point to 14.04 in stead. Maybe this is not going to be an issue, for chances are that we will not see many post about SIS problems at all. Only some very old SIS cards still have the problem but they might be too slow to be useable anyway, fixed or not.

For people posting other places than Ubuntuforums this is a chance for marketing Buntu, especially Lubuntu. 


14.04 is now bringing three important fixes: This one for SIS, a boot option for non-PAE Pentium M's and a fix for Flash on Intel 8xx graphics cards. Good news for everyone dealing with old hardware.

---

### Post by mörgæs on 2014-04-10
If the command 
```
sudo lshw -C video
```
yields **661/741/760** or **662/761** then a 14.04.1 install works right away, but in 14.10 or 15.04 (development version) the package is only available in a personal package archive (PPA). The commands

```
sudo apt-add-repository ppa: xorg-edgers
sudo apt-get update
sudo apt-get install xserver-xorg-video-sis

```
install the necessary packages. Reboot. More info [here]("http://ubuntuforums.org/showthread.php?t=2252413").

Lubuntu 14.04 is supported through april 2017 so most users would probably prefer this one. 


Also if the card is **771/671** some modifications are necessary. The two options are 
[LIST=1]
[*]install Lubuntu 14.04 in low resolution, add updates and create an xorg.conf, as described later in this thread, or
[*]install a 12.04-based distro *with support* like Bodhi Linux or LXLE, both of which are supported through 2017.
[/LIST]

---

### Post by KBD47 on 2014-04-14
Great news about SIS. I've been using Linux Lite on that computer, I noticed Ubuntu quit working on it after 11.10.
What is the Flash fix? Something for SSE I hope?

---

### Post by mörgæs on 2014-04-15
As you can see the bug fix is for a particular series of Intel graphics cards. It's not related to the processor.

I don't think anyone is going to develop new stuff for processors with only SSE and not SSE2. We are talking about AMD XP's from 2001-3. 

Back on track, let's keep the tread focused on SIS.

---

### Post by javier-ejsf on 2014-04-18
Morgaes, I've been trying Trusty Live DVD, and it had an "acceptable 1024x768" (1200x800 was expected) resolution and wireless worked. But when I installed it wireless stopped working, couldn't install additional driver [solved somehow installing driver right from DVD] and resolution went down to 640x480, it won't allow any other option. Kinda disappointed, still searching though, In case any one finds a fix/trick keep me posted :-/

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


```

---

### Post by KBD47 on 2014-04-18
This is not working for me. 
"SIS...no compatible module..."
On booting the Live DVD. Could get no working desktop with either Ubuntu or Xubuntu 14.04.
BTW I'm using Linux Lite on the machine with no issues. Before that I used Debian Wheezy with no issues.

System:    Host: karlton-PW532AA-ABA-SR1403WM-NA520 Kernel: 3.8.0-34-generic i686 (32 bit) 
           Desktop: Xfce 4.8.3 Distro: Ubuntu 12.04 precise
Machine:   System: Compaq Presario 061 product: PW532AA-ABA SR1403WM NA520 version: 0n41411RE101SALMO00
           Mobo: ASUSTek model: Salmon version: 1.04 Bios: Phoenix version: 3.14 date: 08/11/2005
CPU:       Single core AMD Sempron 3000+ (-UP-) cache: 128 KB flags: (nx sse sse2) clocked at 1808.435 MHz 
Graphics:  Card: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter 
           X.Org: 1.11.3 drivers: vesa (unloaded: fbdev) Resolution: 1280x1024@0.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 0x300) GLX Version: 2.1 Mesa 8.0.4
Audio:     Card: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller driver: snd_intel8x0
           Sound: Advanced Linux Sound Architecture ver: k3.8.0-34-generic
Network:   Card: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet driver: sis900 
           IF: eth0 state: unknown speed: 100 Mbps duplex: full mac: 00:11:d8:ac:1e:92
Drives:    HDD Total Size: 80.0GB (33.6% used) 1: id: /dev/sda model: WDC_WD800BB size: 80.0GB 
Partition: ID: / size: 72G used: 26G (38%) fs: ext4 ID: swap-1 size: 0.49GB used: 0.00GB (0%) fs: swap 
           ID: swap-2 size: 2.10GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 147 Uptime: 10 min Memory: 274.7/939.1MB Client: Shell inxi: 1.8.4

---

### Post by mörgæs on 2014-04-20
Both of you, please post in CODE tags the output from 

```
apt-cache show xserver-xorg-video-sis
xrandr -q
sudo lshw -C video
```

---

### Post by javier-ejsf on 2014-04-20
My homework! I followed all your instructions, here's what I got:
```
**javier@exo:~$ apt-cache show xserver-xorg-video-sis**
Package: xserver-xorg-video-sis
Priority: optional
Section: x11
Installed-Size: 640
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 1:0.10.7-0ubuntu6
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-sis
Provides: xorg-driver-video, xserver-xorg-video-
Depends: libc6 (>= 2.7), xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Conflicts: xserver-xorg-driver-sis
Filename: pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.7-0ubuntu6_i386.deb
Size: 224774
MD5sum: 6690e9fcffa3312230f75f0527961097
SHA1: 663b9b043a9b74ee2ee83d6eed2f7f0c6fda3afb
SHA256: e6326f8006c5df30a19a97f52fb229a4b0b0d2a3a354b9e8164974e8d20406fe
Description-en: X.Org X server -- SiS display driver
 This package provides the driver for all SiS and XGI Volari cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-sis driver module.
Description-md5: 42dac6b9768ebbc736ea67fc56bc1813
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-active, kubuntu-active-desktop, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop, ubuntu-gnome-desktop

**javier@exo:~$ xrandr -q**
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0* 
**javier@exo:~$ sudo lshw -C video**
[sudo] password for javier: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128)
**javier@exo:~$ **


```

---

### Post by mörgæs on 2014-04-20
Hmmm... we don't have the exact same graphics card, but they are close relatives. You only get one resolution to choose from.

Did you add an xorg.conf?
Which screen are you using?

```
Package: xserver-xorg-video-sis
Priority: optional
Section: x11
Installed-Size: 640
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 1:0.10.7-0ubuntu6
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-sis
Provides: xorg-driver-video, xserver-xorg-video-
Depends: libc6 (>= 2.7), xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Conflicts: xserver-xorg-driver-sis
Filename: pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.7-0ubuntu6_i386.deb
Size: 224774
MD5sum: 6690e9fcffa3312230f75f0527961097
SHA1: 663b9b043a9b74ee2ee83d6eed2f7f0c6fda3afb
SHA256: e6326f8006c5df30a19a97f52fb229a4b0b0d2a3a354b9e8164974e8d20406fe
Description-en: X.Org X server -- SiS display driver
 This package provides the driver for all SiS and XGI Volari cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-sis driver module.
Description-md5: 42dac6b9768ebbc736ea67fc56bc1813
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-active, kubuntu-active-desktop, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop, ubuntu-gnome-desktop

```

```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      60.0* 
   1680x1050      60.0  
   1400x1050      75.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1280x854       59.0  
   1360x768       60.0  
   1280x800       60.0  
   1152x864       75.0     60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       70.0     60.0     75.0  
   1024x576       60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        60.0     56.0     75.0     72.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        67.0     60.0     75.0     73.0  
   720x400        70.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  

```

```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:f8100000-f811ffff ioport:2000(size=128)

```

---

### Post by javier-ejsf on 2014-04-20
When I do a fresh install no xorg.conf is created. The output I pasted in the previous message was without any xorg.conf.

But since resolution 640x480 is too low I kill X, paste this xorg.conf into /etc/X11 and start X again, which allows me to get 1280x768 resolution, lousy video playback and pressumably no acceleration, but at least it makes my notebook usable. I really don't understand what is written in this xorg.conf but it's supposed to force Vesa and it's been ok since Buntu 12.04 LTS, and it goes like this:
```
Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
    Busid "PCI:1:0:0"
    Driver "vesa"
    Screen 0
        Option "UseFBDev" "true"
        Option "DPMS"
        Option "ShadowFB"
        Option "MaxXFBMem"
        VideoRam 262016
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "true"
        Option "AddARGBGLXVisuals" "True"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    HorizSync 20-107
        VertRefresh 50-185
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
    EndSubSection
EndSection

Section "Module"
    Load "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "int10"
    Load "vbe"
    Load "speedo"
    Load "record"
EndSection

Section "DRI"
        Mode 0666
EndSection


```
I'm pasting it here since this might give a clue to the solution. I have to remind you that Live Session plays quite fine at a 1024x780 resolution, but I can't figure out how to keep that driver.

---

### Post by KAWill70 on 2014-04-20
This is welcome news and explains why Ubuntu 14.04 and Lubuntu 14.04 boot on my nine year old computer while many recent versions would not.

The computer incorporates a SIS 661FX Northbridge and SIS 964 Southbridge.  Unfortunately, Ubuntu 14.04 is not usable on this computer as it runs extremely slow.  The search tool only accepts one character every few seconds.  It is as though the CPU was taking over some or all graphics adapter functions.  I have the same problem in Mint 16 which only runs using compatibility mode.  The computer has 1 GB of memory which could be a factor along with a slow single core 2.66 Ghz Celeron D processor.

The SIS Patch may have missed one item.  I get a message during boot that no SIS 630 Compatible Bus was detected, and the SIS630_smbus module was not inserted.  It turns out that the smbus is a two wire serial control bus similar to I2C handling such things as power off, fans, cover sensor, battery, and other similar items.  Quite a few Linux distributions are unable to power off this computer as a result.  This problem is not new in version 14.04.

---

### Post by KAWill70 on 2014-04-21
I wonder if my problem running Ubuntu 14.04 was not related to SIS graphics but simply the result of running Live with only 1 GB memory.  Running Live uses RAM as disk and might leave very little extra.

Perhaps an installation on disk would work much better.

Here is the SIS Graphics information for my Lubuntu 14.04 installation.

If I understand this result I do have the correct SIS Graphics Driver installed and working.

```
kent@kent-desktop:~$ apt-cache show xserver-xorg-video-sis
Package: xserver-xorg-video-sis
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 640
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:0.10.7-0ubuntu6
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-sis
Provides: xorg-driver-video, xserver-xorg-video-
Depends: libc6 (>= 2.7), xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Conflicts: xserver-xorg-driver-sis
Description: X.Org X server -- SiS display driver
 This package provides the driver for all SiS and XGI Volari cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-sis driver module.
Description-md5: 42dac6b9768ebbc736ea67fc56bc1813
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

-  -  -

kent@kent-desktop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0*    75.0  
   1280x960       60.0  
   1280x854       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.0     60.0  
   1024x576       75.0     60.0  
   960x600        60.0  
   832x624        75.0  
   960x540        60.0  
   800x600        75.0     72.0     60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        75.0     60.0  
   720x480        61.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  

-  -  -

kent@kent-desktop:~$ sudo lshw -C video
[sudo] password for kent: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff memory:ed000000-ed01ffff ioport:c000(size=128)
kent@kent-desktop:~$ 

```

Thanks for any input.

---

### Post by adri_cala2 on 2014-04-27
Hi, I'm having the same Issue that [COLOR=#DD4814][COLOR=#000000][javier-ejsf]("http://ubuntuforums.org/member.php?u=1849431") [/COLOR][/COLOR]reported. (I'm running Lubuntu 14.04 in an old computer.)
Using the same commands proposed to him, I could see that I've the exact same video card. ([COLOR=#000000][FONT=Ubuntu Mono]771/671 PCIE VGA Display Adapter)[/FONT][/COLOR]
Using the xorg.conf that he posted, I managed to obtain a better resolution, but it seems that the acceleration is not working.

Is there any solution to this issue?
[COLOR=#DD4814][COLOR=#000000]
[/COLOR][/COLOR]
Thanks in advance.

---

### Post by KAWill70 on 2014-04-27
> **adri_cala2 said:**
> Hi, I'm having the same Issue that [COLOR=#DD4814][COLOR=#000000][javier-ejsf]("http://ubuntuforums.org/member.php?u=1849431") [/COLOR][/COLOR]reported. (I'm running Lubuntu 14.04 in an old computer.)
Using the same commands proposed to him, I could see that I've the exact same video card. ([COLOR=#000000][FONT=Ubuntu Mono]771/671 PCIE VGA Display Adapter)[/FONT][/COLOR]
Using the xorg.conf that he posted, I managed to obtain a better resolution, but it seems that the acceleration is not working.
If my understanding is correct, the fix for SIS Graphics includes 2D video drivers only.  See the thread below.

[http://ubuntuforums.org/showthread.php?t=2218977](http://ubuntuforums.org/showthread.php?t=2218977)

Any system requiring 3D video such as Ubuntu with the Unity Desktop would have a problem and software rendering could come into play.  If anyone can confirm please let us know.

Regardless, it is still great to see the fix for SIS graphics which should work with at least some of the Ubuntu derivatives.

---

### Post by javier-ejsf on 2014-04-28
> **KAWill70 said:**
> 
Regardless, it is still great to see the fix for SIS graphics which should work with at least some of the Ubuntu derivatives.

I'm testing Xubuntu 14.04 on a ***Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)***, no 3D acceleration (I don't mind it), the thing is I can't get the right resolution 1200x800 and videos play really bad and sometimes even freeze. 
Ubuntu/Kubuntu run unbearably slow, Xubuntu/Lubuntu quite ok, but not the expected screen resolution, in all cases I had to paste a tweaked xorg.conf to get an acceptable resolution.

---

### Post by javier-ejsf on 2014-04-28
Xorg.0.log comparison in 3 stages:
Live Session (no xorg.conf) ---> 1024x768
Fresh Install (no xorg.conf) ---> 640x480
w/Customised xorg.conf ------> 1200x768 (acceptable, no acceleration, lousy video playback)

My Xorg.0.log (live session 1024x768)
```
[   191.351] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   191.352] X Protocol Version 11, Revision 0
[   191.352] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   191.352] Current Operating System: Linux xubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686
[   191.352] Kernel command line: file=/cdrom/preseed/xubuntu.seed  boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   191.352] Build Date: 16 April 2014  01:40:08PM
[   191.352] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[   191.352] Current version of pixman: 0.30.2
[   191.352]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   191.352] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   191.352] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 28 02:17:58 2014
[   191.352] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   191.353] (==) No Layout section.  Using the first Screen section.
[   191.353] (==) No screen section available. Using defaults.
[   191.353] (**) |-->Screen "Default Screen Section" (0)
[   191.353] (**) |   |-->Monitor "<default monitor>"
[   191.353] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   191.353] (==) Automatically adding devices
[   191.353] (==) Automatically enabling devices
[   191.353] (==) Automatically adding GPU devices
[   191.353] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   191.353]     Entry deleted from font path.
[   191.353] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   191.353]     Entry deleted from font path.
[   191.354] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   191.354]     Entry deleted from font path.
[   191.354] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   191.354]     Entry deleted from font path.
[   191.354] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   191.354]     Entry deleted from font path.
[   191.354] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   191.354] (==) ModulePath set to  "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   191.354] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   191.354] (II) Loader magic: 0xb77a76c0
[   191.354] (II) Module ABI versions:
[   191.354]     X.Org ANSI C Emulation: 0.4
[   191.354]     X.Org Video Driver: 15.0
[   191.354]     X.Org XInput driver : 20.0
[   191.354]     X.Org Server Extension : 8.0
[   191.356] (--) PCI:*(0:1:0:0) 1039:6351:14c0:002b rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[   191.356] Initializing built-in extension Generic Event Extension
[   191.356] Initializing built-in extension SHAPE
[   191.356] Initializing built-in extension MIT-SHM
[   191.356] Initializing built-in extension XInputExtension
[   191.356] Initializing built-in extension XTEST
[   191.356] Initializing built-in extension BIG-REQUESTS
[   191.356] Initializing built-in extension SYNC
[   191.356] Initializing built-in extension XKEYBOARD
[   191.356] Initializing built-in extension XC-MISC
[   191.356] Initializing built-in extension SECURITY
[   191.356] Initializing built-in extension XINERAMA
[   191.356] Initializing built-in extension XFIXES
[   191.356] Initializing built-in extension RENDER
[   191.356] Initializing built-in extension RANDR
[   191.356] Initializing built-in extension COMPOSITE
[   191.356] Initializing built-in extension DAMAGE
[   191.356] Initializing built-in extension MIT-SCREEN-SAVER
[   191.356] Initializing built-in extension DOUBLE-BUFFER
[   191.356] Initializing built-in extension RECORD
[   191.356] Initializing built-in extension DPMS
[   191.356] Initializing built-in extension Present
[   191.356] Initializing built-in extension DRI3
[   191.356] Initializing built-in extension X-Resource
[   191.356] Initializing built-in extension XVideo
[   191.356] Initializing built-in extension XVideo-MotionCompensation
[   191.356] Initializing built-in extension SELinux
[   191.356] Initializing built-in extension XFree86-VidModeExtension
[   191.356] Initializing built-in extension XFree86-DGA
[   191.356] Initializing built-in extension XFree86-DRI
[   191.356] Initializing built-in extension DRI2
[   191.356] (II) LoadModule: "glx"
[   191.357] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   191.358] (II) Module glx: vendor="X.Org Foundation"
[   191.358]     compiled for 1.15.1, module version = 1.0.0
[   191.358]     ABI class: X.Org Server Extension, version 8.0
[   191.358] (==) AIGLX enabled
[   191.358] Loading extension GLX
[   191.358] (==) Matched sis as autoconfigured driver 0
[   191.358] (==) Matched modesetting as autoconfigured driver 1
[   191.358] (==) Matched fbdev as autoconfigured driver 2
[   191.358] (==) Matched vesa as autoconfigured driver 3
[   191.358] (==) Assigned the driver to the xf86ConfigLayout
[   191.358] (II) LoadModule: "sis"
[   191.358] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[   191.358] (II) Module sis: vendor="X.Org Foundation"
[   191.358]     compiled for 1.15.0, module version = 0.10.7
[   191.358]     Module class: X.Org Video Driver
[   191.358]     ABI class: X.Org Video Driver, version 15.0
[   191.358] (II) LoadModule: "modesetting"
[   191.359] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   191.359] (II) Module modesetting: vendor="X.Org Foundation"
[   191.359]     compiled for 1.15.0, module version = 0.8.1
[   191.359]     Module class: X.Org Video Driver
[   191.359]     ABI class: X.Org Video Driver, version 15.0
[   191.359] (II) LoadModule: "fbdev"
[   191.359] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   191.359] (II) Module fbdev: vendor="X.Org Foundation"
[   191.359]     compiled for 1.15.0, module version = 0.4.4
[   191.359]     Module class: X.Org Video Driver
[   191.359]     ABI class: X.Org Video Driver, version 15.0
[   191.359] (II) LoadModule: "vesa"
[   191.359] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   191.359] (II) Module vesa: vendor="X.Org Foundation"
[   191.359]     compiled for 1.15.0, module version = 2.3.3
[   191.359]     Module class: X.Org Video Driver
[   191.359]     ABI class: X.Org Video Driver, version 15.0
[   191.359] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[   191.359] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[   191.359] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   191.359] (II) FBDEV: driver for framebuffer: fbdev
[   191.359] (II) VESA: driver for VESA chipsets: vesa
[   191.359] (++) using VT number 7

[   191.360] (WW) Falling back to old probe method for sis
[   191.360] (--) Assigning device section with no busID to primary device
[   191.360] (EE) open /dev/dri/card0: No such file or directory
[   191.360] (WW) Falling back to old probe method for modesetting
[   191.360] (EE) open /dev/dri/card0: No such file or directory
[   191.360] (II) Loading sub module "fbdevhw"
[   191.360] (II) LoadModule: "fbdevhw"
[   191.360] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   191.360] (II) Module fbdevhw: vendor="X.Org Foundation"
[   191.360]     compiled for 1.15.1, module version = 0.0.2
[   191.360]     ABI class: X.Org Video Driver, version 15.0
[   191.360] (EE) open /dev/fb0: No such file or directory
[   191.360] (WW) Falling back to old probe method for fbdev
[   191.360] (II) Loading sub module "fbdevhw"
[   191.360] (II) LoadModule: "fbdevhw"
[   191.361] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   191.361] (II) Module fbdevhw: vendor="X.Org Foundation"
[   191.361]     compiled for 1.15.1, module version = 0.0.2
[   191.361]     ABI class: X.Org Video Driver, version 15.0
[   191.361] (EE) open /dev/fb0: No such file or directory
[   191.361] (EE) Screen 0 deleted because of no matching config section.
[   191.361] (II) UnloadModule: "modesetting"
[   191.361] (EE) Screen 0 deleted because of no matching config section.
[   191.361] (II) UnloadModule: "fbdev"
[   191.361] (II) UnloadSubModule: "fbdevhw"
[   191.361] (II) Loading sub module "vbe"
[   191.361] (II) LoadModule: "vbe"
[   191.361] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   191.361] (II) Module vbe: vendor="X.Org Foundation"
[   191.361]     compiled for 1.15.1, module version = 1.1.0
[   191.361]     ABI class: X.Org Video Driver, version 15.0
[   191.361] (II) Loading sub module "int10"
[   191.361] (II) LoadModule: "int10"
[   191.362] (II) Loading /usr/lib/xorg/modules/libint10.so
[   191.362] (II) Module int10: vendor="X.Org Foundation"
[   191.362]     compiled for 1.15.1, module version = 1.0.0
[   191.362]     ABI class: X.Org Video Driver, version 15.0
[   191.362] (II) VESA(0): initializing int10
[   191.367] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   191.368] (II) VESA(0): VESA BIOS detected
[   191.368] (II) VESA(0): VESA VBE Version 3.0
[   191.368] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[   191.368] (II) VESA(0): VESA VBE OEM: SiS
[   191.368] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[   191.368] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[   191.368] (II) VESA(0): VESA VBE OEM Product: 6330
[   191.368] (II) VESA(0): VESA VBE OEM Product Rev: 3.72.15a
[   191.379] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   191.379] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   191.379] (==) VESA(0): RGB weight 888
[   191.379] (==) VESA(0): Default visual is TrueColor
[   191.379] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   191.379] (II) Loading sub module "ddc"
[   191.379] (II) LoadModule: "ddc"
[   191.379] (II) Module "ddc" already built-in
[   191.477] (II) VESA(0): VESA VBE DDC supported
[   191.477] (II) VESA(0): VESA VBE DDC Level none
[   191.477] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[   191.510] (II) VESA(0): VESA VBE DDC read failed
[   191.510] (II) VESA(0): Searching for matching VESA mode(s):
[   191.511] Mode: 11c (1280x768)
[   191.511]     ModeAttributes: 0x9f
[   191.511]     WinAAttributes: 0x7
[   191.511]     WinBAttributes: 0x0
[   191.511]     WinGranularity: 64
[   191.511]     WinSize: 64
[   191.511]     WinASegment: 0xa000
[   191.511]     WinBSegment: 0xa000
[   191.511]     WinFuncPtr: 0xc000862b
[   191.511]     BytesPerScanline: 1280
[   191.511]     XResolution: 1280
[   191.511]     YResolution: 768
[   191.511]     XCharSize: 8
[   191.511]     YCharSize: 16
[   191.511]     NumberOfPlanes: 1
[   191.511]     BitsPerPixel: 8
[   191.511]     NumberOfBanks: 1
[   191.511]     MemoryModel: 4
[   191.511]     BankSize: 0
[   191.511]     NumberOfImages: 7
[   191.511]     RedMaskSize: 0
[   191.511]     RedFieldPosition: 0
[   191.511]     GreenMaskSize: 0
[   191.511]     GreenFieldPosition: 0
[   191.511]     BlueMaskSize: 0
[   191.511]     BlueFieldPosition: 0
[   191.511]     RsvdMaskSize: 0
[   191.511]     RsvdFieldPosition: 0
[   191.511]     DirectColorModeInfo: 0
[   191.511]     PhysBasePtr: 0xc0000000
[   191.511]     LinBytesPerScanLine: 1280
[   191.511]     BnkNumberOfImagePages: 7
[   191.511]     LinNumberOfImagePages: 7
[   191.511]     LinRedMaskSize: 0
[   191.511]     LinRedFieldPosition: 0
[   191.511]     LinGreenMaskSize: 0
[   191.511]     LinGreenFieldPosition: 0
[   191.511]     LinBlueMaskSize: 0
[   191.511]     LinBlueFieldPosition: 0
[   191.511]     LinRsvdMaskSize: 0
[   191.511]     LinRsvdFieldPosition: 0
[   191.511]     MaxPixelClock: 0
[   191.511] Mode: 11d (1280x768)
[   191.511]     ModeAttributes: 0x9b
[   191.511]     WinAAttributes: 0x7
[   191.511]     WinBAttributes: 0x0
[   191.511]     WinGranularity: 64
[   191.511]     WinSize: 64
[   191.511]     WinASegment: 0xa000
[   191.511]     WinBSegment: 0xa000
[   191.511]     WinFuncPtr: 0xc000862b
[   191.511]     BytesPerScanline: 2560
[   191.511]     XResolution: 1280
[   191.511]     YResolution: 768
[   191.511]     XCharSize: 8
[   191.511]     YCharSize: 16
[   191.511]     NumberOfPlanes: 1
[   191.511]     BitsPerPixel: 16
[   191.511]     NumberOfBanks: 1
[   191.511]     MemoryModel: 6
[   191.511]     BankSize: 0
[   191.511]     NumberOfImages: 3
[   191.511]     RedMaskSize: 5
[   191.511]     RedFieldPosition: 11
[   191.511]     GreenMaskSize: 6
[   191.511]     GreenFieldPosition: 5
[   191.511]     BlueMaskSize: 5
[   191.511]     BlueFieldPosition: 0
[   191.511]     RsvdMaskSize: 0
[   191.511]     RsvdFieldPosition: 0
[   191.511]     DirectColorModeInfo: 0
[   191.512]     PhysBasePtr: 0xc0000000
[   191.512]     LinBytesPerScanLine: 2560
[   191.512]     BnkNumberOfImagePages: 3
[   191.512]     LinNumberOfImagePages: 3
[   191.512]     LinRedMaskSize: 5
[   191.512]     LinRedFieldPosition: 11
[   191.512]     LinGreenMaskSize: 6
[   191.512]     LinGreenFieldPosition: 5
[   191.512]     LinBlueMaskSize: 5
[   191.512]     LinBlueFieldPosition: 0
[   191.512]     LinRsvdMaskSize: 0
[   191.512]     LinRsvdFieldPosition: 0
[   191.512]     MaxPixelClock: 0
[   191.512] *Mode: 11e (1280x768)
[   191.512]     ModeAttributes: 0x9b
[   191.512]     WinAAttributes: 0x7
[   191.512]     WinBAttributes: 0x0
[   191.512]     WinGranularity: 64
[   191.512]     WinSize: 64
[   191.512]     WinASegment: 0xa000
[   191.512]     WinBSegment: 0xa000
[   191.512]     WinFuncPtr: 0xc000862b
[   191.512]     BytesPerScanline: 5120
[   191.512]     XResolution: 1280
[   191.512]     YResolution: 768
[   191.512]     XCharSize: 8
[   191.512]     YCharSize: 16
[   191.512]     NumberOfPlanes: 1
[   191.512]     BitsPerPixel: 32
[   191.512]     NumberOfBanks: 1
[   191.512]     MemoryModel: 6
[   191.512]     BankSize: 0
[   191.512]     NumberOfImages: 1
[   191.512]     RedMaskSize: 8
[   191.512]     RedFieldPosition: 16
[   191.512]     GreenMaskSize: 8
[   191.512]     GreenFieldPosition: 8
[   191.512]     BlueMaskSize: 8
[   191.512]     BlueFieldPosition: 0
[   191.512]     RsvdMaskSize: 8
[   191.512]     RsvdFieldPosition: 24
[   191.512]     DirectColorModeInfo: 0
[   191.512]     PhysBasePtr: 0xc0000000
[   191.512]     LinBytesPerScanLine: 5120
[   191.512]     BnkNumberOfImagePages: 1
[   191.512]     LinNumberOfImagePages: 1
[   191.512]     LinRedMaskSize: 8
[   191.512]     LinRedFieldPosition: 16
[   191.512]     LinGreenMaskSize: 8
[   191.512]     LinGreenFieldPosition: 8
[   191.512]     LinBlueMaskSize: 8
[   191.512]     LinBlueFieldPosition: 0
[   191.512]     LinRsvdMaskSize: 8
[   191.512]     LinRsvdFieldPosition: 24
[   191.512]     MaxPixelClock: 0
[   191.512] Mode: 101 (640x480)
[   191.512]     ModeAttributes: 0x9f
[   191.512]     WinAAttributes: 0x7
[   191.512]     WinBAttributes: 0x0
[   191.512]     WinGranularity: 64
[   191.512]     WinSize: 64
[   191.512]     WinASegment: 0xa000
[   191.512]     WinBSegment: 0xa000
[   191.512]     WinFuncPtr: 0xc000862b
[   191.512]     BytesPerScanline: 640
[   191.512]     XResolution: 640
[   191.512]     YResolution: 480
[   191.512]     XCharSize: 8
[   191.512]     YCharSize: 16
[   191.512]     NumberOfPlanes: 1
[   191.512]     BitsPerPixel: 8
[   191.512]     NumberOfBanks: 1
[   191.512]     MemoryModel: 4
[   191.512]     BankSize: 0
[   191.512]     NumberOfImages: 24
[   191.513]     RedMaskSize: 0
[   191.513]     RedFieldPosition: 0
[   191.513]     GreenMaskSize: 0
[   191.513]     GreenFieldPosition: 0
[   191.513]     BlueMaskSize: 0
[   191.513]     BlueFieldPosition: 0
[   191.513]     RsvdMaskSize: 0
[   191.513]     RsvdFieldPosition: 0
[   191.513]     DirectColorModeInfo: 0
[   191.513]     PhysBasePtr: 0xc0000000
[   191.513]     LinBytesPerScanLine: 640
[   191.513]     BnkNumberOfImagePages: 24
[   191.513]     LinNumberOfImagePages: 24
[   191.513]     LinRedMaskSize: 0
[   191.513]     LinRedFieldPosition: 0
[   191.513]     LinGreenMaskSize: 0
[   191.513]     LinGreenFieldPosition: 0
[   191.513]     LinBlueMaskSize: 0
[   191.513]     LinBlueFieldPosition: 0
[   191.513]     LinRsvdMaskSize: 0
[   191.513]     LinRsvdFieldPosition: 0
[   191.513]     MaxPixelClock: 0
[   191.513] Mode: 100 (640x400)
[   191.513]     ModeAttributes: 0x9f
[   191.513]     WinAAttributes: 0x7
[   191.513]     WinBAttributes: 0x0
[   191.513]     WinGranularity: 64
[   191.513]     WinSize: 64
[   191.513]     WinASegment: 0xa000
[   191.513]     WinBSegment: 0xa000
[   191.513]     WinFuncPtr: 0xc000862b
[   191.513]     BytesPerScanline: 640
[   191.513]     XResolution: 640
[   191.513]     YResolution: 400
[   191.513]     XCharSize: 8
[   191.513]     YCharSize: 16
[   191.513]     NumberOfPlanes: 1
[   191.513]     BitsPerPixel: 8
[   191.513]     NumberOfBanks: 1
[   191.513]     MemoryModel: 4
[   191.513]     BankSize: 0
[   191.513]     NumberOfImages: 31
[   191.513]     RedMaskSize: 0
[   191.513]     RedFieldPosition: 0
[   191.513]     GreenMaskSize: 0
[   191.513]     GreenFieldPosition: 0
[   191.513]     BlueMaskSize: 0
[   191.513]     BlueFieldPosition: 0
[   191.513]     RsvdMaskSize: 0
[   191.513]     RsvdFieldPosition: 0
[   191.513]     DirectColorModeInfo: 0
[   191.513]     PhysBasePtr: 0xc0000000
[   191.513]     LinBytesPerScanLine: 640
[   191.513]     BnkNumberOfImagePages: 31
[   191.513]     LinNumberOfImagePages: 31
[   191.513]     LinRedMaskSize: 0
[   191.513]     LinRedFieldPosition: 0
[   191.513]     LinGreenMaskSize: 0
[   191.513]     LinGreenFieldPosition: 0
[   191.513]     LinBlueMaskSize: 0
[   191.513]     LinBlueFieldPosition: 0
[   191.513]     LinRsvdMaskSize: 0
[   191.513]     LinRsvdFieldPosition: 0
[   191.513]     MaxPixelClock: 0
[   191.513] Mode: 103 (800x600)
[   191.513]     ModeAttributes: 0x9f
[   191.513]     WinAAttributes: 0x7
[   191.513]     WinBAttributes: 0x0
[   191.513]     WinGranularity: 64
[   191.513]     WinSize: 64
[   191.513]     WinASegment: 0xa000
[   191.513]     WinBSegment: 0xa000
[   191.513]     WinFuncPtr: 0xc000862b
[   191.513]     BytesPerScanline: 800
[   191.513]     XResolution: 800
[   191.513]     YResolution: 600
[   191.513]     XCharSize: 8
[   191.513]     YCharSize: 16
[   191.513]     NumberOfPlanes: 1
[   191.513]     BitsPerPixel: 8
[   191.513]     NumberOfBanks: 1
[   191.513]     MemoryModel: 4
[   191.513]     BankSize: 0
[   191.514]     NumberOfImages: 15
[   191.514]     RedMaskSize: 0
[   191.514]     RedFieldPosition: 0
[   191.514]     GreenMaskSize: 0
[   191.514]     GreenFieldPosition: 0
[   191.514]     BlueMaskSize: 0
[   191.514]     BlueFieldPosition: 0
[   191.514]     RsvdMaskSize: 0
[   191.514]     RsvdFieldPosition: 0
[   191.514]     DirectColorModeInfo: 0
[   191.514]     PhysBasePtr: 0xc0000000
[   191.514]     LinBytesPerScanLine: 800
[   191.514]     BnkNumberOfImagePages: 15
[   191.514]     LinNumberOfImagePages: 15
[   191.514]     LinRedMaskSize: 0
[   191.514]     LinRedFieldPosition: 0
[   191.514]     LinGreenMaskSize: 0
[   191.514]     LinGreenFieldPosition: 0
[   191.514]     LinBlueMaskSize: 0
[   191.514]     LinBlueFieldPosition: 0
[   191.514]     LinRsvdMaskSize: 0
[   191.514]     LinRsvdFieldPosition: 0
[   191.514]     MaxPixelClock: 0
[   191.514] Mode: 104 (1024x768)
[   191.514]     ModeAttributes: 0x1f
[   191.514]     WinAAttributes: 0x7
[   191.514]     WinBAttributes: 0x0
[   191.514]     WinGranularity: 64
[   191.514]     WinSize: 64
[   191.514]     WinASegment: 0xa000
[   191.514]     WinBSegment: 0xa000
[   191.514]     WinFuncPtr: 0xc000862b
[   191.514]     BytesPerScanline: 128
[   191.514]     XResolution: 1024
[   191.514]     YResolution: 768
[   191.514]     XCharSize: 8
[   191.514]     YCharSize: 16
[   191.514]     NumberOfPlanes: 4
[   191.514]     BitsPerPixel: 4
[   191.514]     NumberOfBanks: 1
[   191.514]     MemoryModel: 3
[   191.514]     BankSize: 0
[   191.514]     NumberOfImages: 15
[   191.514]     RedMaskSize: 0
[   191.514]     RedFieldPosition: 0
[   191.514]     GreenMaskSize: 0
[   191.514]     GreenFieldPosition: 0
[   191.514]     BlueMaskSize: 0
[   191.514]     BlueFieldPosition: 0
[   191.514]     RsvdMaskSize: 0
[   191.514]     RsvdFieldPosition: 0
[   191.514]     DirectColorModeInfo: 0
[   191.514]     PhysBasePtr: 0xc0000000
[   191.514]     LinBytesPerScanLine: 128
[   191.514]     BnkNumberOfImagePages: 15
[   191.514]     LinNumberOfImagePages: 15
[   191.514]     LinRedMaskSize: 0
[   191.514]     LinRedFieldPosition: 0
[   191.514]     LinGreenMaskSize: 0
[   191.514]     LinGreenFieldPosition: 0
[   191.514]     LinBlueMaskSize: 0
[   191.514]     LinBlueFieldPosition: 0
[   191.514]     LinRsvdMaskSize: 0
[   191.514]     LinRsvdFieldPosition: 0
[   191.514]     MaxPixelClock: 0
[   191.514] Mode: 105 (1024x768)
[   191.514]     ModeAttributes: 0x9f
[   191.514]     WinAAttributes: 0x7
[   191.514]     WinBAttributes: 0x0
[   191.514]     WinGranularity: 64
[   191.514]     WinSize: 64
[   191.514]     WinASegment: 0xa000
[   191.514]     WinBSegment: 0xa000
[   191.514]     WinFuncPtr: 0xc000862b
[   191.515]     BytesPerScanline: 1024
[   191.515]     XResolution: 1024
[   191.515]     YResolution: 768
[   191.515]     XCharSize: 8
[   191.515]     YCharSize: 16
[   191.515]     NumberOfPlanes: 1
[   191.515]     BitsPerPixel: 8
[   191.515]     NumberOfBanks: 1
[   191.515]     MemoryModel: 4
[   191.515]     BankSize: 0
[   191.515]     NumberOfImages: 9
[   191.515]     RedMaskSize: 0
[   191.515]     RedFieldPosition: 0
[   191.515]     GreenMaskSize: 0
[   191.515]     GreenFieldPosition: 0
[   191.515]     BlueMaskSize: 0
[   191.515]     BlueFieldPosition: 0
[   191.515]     RsvdMaskSize: 0
[   191.515]     RsvdFieldPosition: 0
[   191.515]     DirectColorModeInfo: 0
[   191.515]     PhysBasePtr: 0xc0000000
[   191.515]     LinBytesPerScanLine: 1024
[   191.515]     BnkNumberOfImagePages: 9
[   191.515]     LinNumberOfImagePages: 9
[   191.515]     LinRedMaskSize: 0
[   191.515]     LinRedFieldPosition: 0
[   191.515]     LinGreenMaskSize: 0
[   191.515]     LinGreenFieldPosition: 0
[   191.515]     LinBlueMaskSize: 0
[   191.515]     LinBlueFieldPosition: 0
[   191.515]     LinRsvdMaskSize: 0
[   191.515]     LinRsvdFieldPosition: 0
[   191.515]     MaxPixelClock: 0
[   191.515] Mode: 10d (320x200)
[   191.515]     ModeAttributes: 0x9b
[   191.515]     WinAAttributes: 0x7
[   191.515]     WinBAttributes: 0x0
[   191.515]     WinGranularity: 64
[   191.515]     WinSize: 64
[   191.515]     WinASegment: 0xa000
[   191.515]     WinBSegment: 0xa000
[   191.515]     WinFuncPtr: 0xc000862b
[   191.515]     BytesPerScanline: 640
[   191.515]     XResolution: 320
[   191.515]     YResolution: 200
[   191.515]     XCharSize: 8
[   191.515]     YCharSize: 8
[   191.515]     NumberOfPlanes: 1
[   191.515]     BitsPerPixel: 15
[   191.515]     NumberOfBanks: 1
[   191.515]     MemoryModel: 6
[   191.515]     BankSize: 0
[   191.515]     NumberOfImages: 63
[   191.515]     RedMaskSize: 5
[   191.515]     RedFieldPosition: 10
[   191.515]     GreenMaskSize: 5
[   191.515]     GreenFieldPosition: 5
[   191.515]     BlueMaskSize: 5
[   191.515]     BlueFieldPosition: 0
[   191.515]     RsvdMaskSize: 0
[   191.515]     RsvdFieldPosition: 0
[   191.515]     DirectColorModeInfo: 0
[   191.515]     PhysBasePtr: 0xc0000000
[   191.515]     LinBytesPerScanLine: 640
[   191.515]     BnkNumberOfImagePages: 63
[   191.515]     LinNumberOfImagePages: 63
[   191.515]     LinRedMaskSize: 5
[   191.515]     LinRedFieldPosition: 10
[   191.515]     LinGreenMaskSize: 5
[   191.515]     LinGreenFieldPosition: 5
[   191.515]     LinBlueMaskSize: 5
[   191.515]     LinBlueFieldPosition: 0
[   191.515]     LinRsvdMaskSize: 0
[   191.515]     LinRsvdFieldPosition: 0
[   191.515]     MaxPixelClock: 0
[   191.516] Mode: 10e (320x200)
[   191.516]     ModeAttributes: 0x9b
[   191.516]     WinAAttributes: 0x7
[   191.516]     WinBAttributes: 0x0
[   191.516]     WinGranularity: 64
[   191.516]     WinSize: 64
[   191.516]     WinASegment: 0xa000
[   191.516]     WinBSegment: 0xa000
[   191.516]     WinFuncPtr: 0xc000862b
[   191.516]     BytesPerScanline: 640
[   191.516]     XResolution: 320
[   191.516]     YResolution: 200
[   191.516]     XCharSize: 8
[   191.516]     YCharSize: 8
[   191.516]     NumberOfPlanes: 1
[   191.516]     BitsPerPixel: 16
[   191.516]     NumberOfBanks: 1
[   191.516]     MemoryModel: 6
[   191.516]     BankSize: 0
[   191.516]     NumberOfImages: 63
[   191.516]     RedMaskSize: 5
[   191.516]     RedFieldPosition: 11
[   191.516]     GreenMaskSize: 6
[   191.516]     GreenFieldPosition: 5
[   191.516]     BlueMaskSize: 5
[   191.516]     BlueFieldPosition: 0
[   191.516]     RsvdMaskSize: 0
[   191.516]     RsvdFieldPosition: 0
[   191.516]     DirectColorModeInfo: 0
[   191.516]     PhysBasePtr: 0xc0000000
[   191.516]     LinBytesPerScanLine: 640
[   191.516]     BnkNumberOfImagePages: 63
[   191.516]     LinNumberOfImagePages: 63
[   191.516]     LinRedMaskSize: 5
[   191.516]     LinRedFieldPosition: 11
[   191.516]     LinGreenMaskSize: 6
[   191.516]     LinGreenFieldPosition: 5
[   191.516]     LinBlueMaskSize: 5
[   191.516]     LinBlueFieldPosition: 0
[   191.516]     LinRsvdMaskSize: 0
[   191.516]     LinRsvdFieldPosition: 0
[   191.516]     MaxPixelClock: 0
[   191.516] Mode: 110 (640x480)
[   191.516]     ModeAttributes: 0x9b
[   191.516]     WinAAttributes: 0x7
[   191.516]     WinBAttributes: 0x0
[   191.516]     WinGranularity: 64
[   191.516]     WinSize: 64
[   191.516]     WinASegment: 0xa000
[   191.516]     WinBSegment: 0xa000
[   191.516]     WinFuncPtr: 0xc000862b
[   191.516]     BytesPerScanline: 1280
[   191.516]     XResolution: 640
[   191.516]     YResolution: 480
[   191.516]     XCharSize: 8
[   191.516]     YCharSize: 16
[   191.516]     NumberOfPlanes: 1
[   191.516]     BitsPerPixel: 15
[   191.516]     NumberOfBanks: 1
[   191.516]     MemoryModel: 6
[   191.516]     BankSize: 0
[   191.516]     NumberOfImages: 11
[   191.516]     RedMaskSize: 5
[   191.516]     RedFieldPosition: 10
[   191.516]     GreenMaskSize: 5
[   191.516]     GreenFieldPosition: 5
[   191.516]     BlueMaskSize: 5
[   191.516]     BlueFieldPosition: 0
[   191.516]     RsvdMaskSize: 0
[   191.516]     RsvdFieldPosition: 0
[   191.516]     DirectColorModeInfo: 0
[   191.516]     PhysBasePtr: 0xc0000000
[   191.516]     LinBytesPerScanLine: 1280
[   191.516]     BnkNumberOfImagePages: 11
[   191.516]     LinNumberOfImagePages: 11
[   191.516]     LinRedMaskSize: 5
[   191.516]     LinRedFieldPosition: 10
[   191.516]     LinGreenMaskSize: 5
[   191.516]     LinGreenFieldPosition: 5
[   191.516]     LinBlueMaskSize: 5
[   191.516]     LinBlueFieldPosition: 0
[   191.516]     LinRsvdMaskSize: 0
[   191.516]     LinRsvdFieldPosition: 0
[   191.516]     MaxPixelClock: 0
[   191.517] Mode: 111 (640x480)
[   191.517]     ModeAttributes: 0x9b
[   191.517]     WinAAttributes: 0x7
[   191.517]     WinBAttributes: 0x0
[   191.517]     WinGranularity: 64
[   191.517]     WinSize: 64
[   191.517]     WinASegment: 0xa000
[   191.517]     WinBSegment: 0xa000
[   191.517]     WinFuncPtr: 0xc000862b
[   191.517]     BytesPerScanline: 1280
[   191.517]     XResolution: 640
[   191.517]     YResolution: 480
[   191.517]     XCharSize: 8
[   191.517]     YCharSize: 16
[   191.517]     NumberOfPlanes: 1
[   191.517]     BitsPerPixel: 16
[   191.517]     NumberOfBanks: 1
[   191.517]     MemoryModel: 6
[   191.517]     BankSize: 0
[   191.517]     NumberOfImages: 11
[   191.517]     RedMaskSize: 5
[   191.517]     RedFieldPosition: 11
[   191.517]     GreenMaskSize: 6
[   191.517]     GreenFieldPosition: 5
[   191.517]     BlueMaskSize: 5
[   191.517]     BlueFieldPosition: 0
[   191.517]     RsvdMaskSize: 0
[   191.517]     RsvdFieldPosition: 0
[   191.517]     DirectColorModeInfo: 0
[   191.517]     PhysBasePtr: 0xc0000000
[   191.517]     LinBytesPerScanLine: 1280
[   191.517]     BnkNumberOfImagePages: 11
[   191.517]     LinNumberOfImagePages: 11
[   191.517]     LinRedMaskSize: 5
[   191.517]     LinRedFieldPosition: 11
[   191.517]     LinGreenMaskSize: 6
[   191.517]     LinGreenFieldPosition: 5
[   191.517]     LinBlueMaskSize: 5
[   191.517]     LinBlueFieldPosition: 0
[   191.517]     LinRsvdMaskSize: 0
[   191.517]     LinRsvdFieldPosition: 0
[   191.517]     MaxPixelClock: 0
[   191.517] Mode: 113 (800x600)
[   191.517]     ModeAttributes: 0x9b
[   191.517]     WinAAttributes: 0x7
[   191.517]     WinBAttributes: 0x0
[   191.517]     WinGranularity: 64
[   191.517]     WinSize: 64
[   191.517]     WinASegment: 0xa000
[   191.517]     WinBSegment: 0xa000
[   191.517]     WinFuncPtr: 0xc000862b
[   191.517]     BytesPerScanline: 1600
[   191.517]     XResolution: 800
[   191.517]     YResolution: 600
[   191.517]     XCharSize: 8
[   191.517]     YCharSize: 16
[   191.517]     NumberOfPlanes: 1
[   191.517]     BitsPerPixel: 15
[   191.517]     NumberOfBanks: 1
[   191.517]     MemoryModel: 6
[   191.517]     BankSize: 0
[   191.517]     NumberOfImages: 7
[   191.517]     RedMaskSize: 5
[   191.517]     RedFieldPosition: 10
[   191.517]     GreenMaskSize: 5
[   191.517]     GreenFieldPosition: 5
[   191.517]     BlueMaskSize: 5
[   191.517]     BlueFieldPosition: 0
[   191.517]     RsvdMaskSize: 0
[   191.517]     RsvdFieldPosition: 0
[   191.517]     DirectColorModeInfo: 0
[   191.517]     PhysBasePtr: 0xc0000000
[   191.517]     LinBytesPerScanLine: 1600
[   191.517]     BnkNumberOfImagePages: 7
[   191.517]     LinNumberOfImagePages: 7
[   191.517]     LinRedMaskSize: 5
[   191.517]     LinRedFieldPosition: 10
[   191.517]     LinGreenMaskSize: 5
[   191.517]     LinGreenFieldPosition: 5
[   191.517]     LinBlueMaskSize: 5
[   191.517]     LinBlueFieldPosition: 0
[   191.517]     LinRsvdMaskSize: 0
[   191.517]     LinRsvdFieldPosition: 0
[   191.517]     MaxPixelClock: 0
[   191.518] Mode: 114 (800x600)
[   191.518]     ModeAttributes: 0x9b
[   191.518]     WinAAttributes: 0x7
[   191.518]     WinBAttributes: 0x0
[   191.518]     WinGranularity: 64
[   191.518]     WinSize: 64
[   191.518]     WinASegment: 0xa000
[   191.518]     WinBSegment: 0xa000
[   191.518]     WinFuncPtr: 0xc000862b
[   191.518]     BytesPerScanline: 1600
[   191.518]     XResolution: 800
[   191.518]     YResolution: 600
[   191.518]     XCharSize: 8
[   191.518]     YCharSize: 16
[   191.518]     NumberOfPlanes: 1
[   191.518]     BitsPerPixel: 16
[   191.518]     NumberOfBanks: 1
[   191.518]     MemoryModel: 6
[   191.518]     BankSize: 0
[   191.518]     NumberOfImages: 7
[   191.518]     RedMaskSize: 5
[   191.518]     RedFieldPosition: 11
[   191.518]     GreenMaskSize: 6
[   191.518]     GreenFieldPosition: 5
[   191.518]     BlueMaskSize: 5
[   191.518]     BlueFieldPosition: 0
[   191.518]     RsvdMaskSize: 0
[   191.518]     RsvdFieldPosition: 0
[   191.518]     DirectColorModeInfo: 0
[   191.518]     PhysBasePtr: 0xc0000000
[   191.518]     LinBytesPerScanLine: 1600
[   191.518]     BnkNumberOfImagePages: 7
[   191.518]     LinNumberOfImagePages: 7
[   191.518]     LinRedMaskSize: 5
[   191.518]     LinRedFieldPosition: 11
[   191.518]     LinGreenMaskSize: 6
[   191.518]     LinGreenFieldPosition: 5
[   191.518]     LinBlueMaskSize: 5
[   191.518]     LinBlueFieldPosition: 0
[   191.518]     LinRsvdMaskSize: 0
[   191.518]     LinRsvdFieldPosition: 0
[   191.518]     MaxPixelClock: 0
[   191.518] Mode: 116 (1024x768)
[   191.518]     ModeAttributes: 0x9b
[   191.518]     WinAAttributes: 0x7
[   191.518]     WinBAttributes: 0x0
[   191.518]     WinGranularity: 64
[   191.518]     WinSize: 64
[   191.518]     WinASegment: 0xa000
[   191.518]     WinBSegment: 0xa000
[   191.518]     WinFuncPtr: 0xc000862b
[   191.518]     BytesPerScanline: 2048
[   191.518]     XResolution: 1024
[   191.518]     YResolution: 768
[   191.518]     XCharSize: 8
[   191.518]     YCharSize: 16
[   191.518]     NumberOfPlanes: 1
[   191.518]     BitsPerPixel: 15
[   191.518]     NumberOfBanks: 1
[   191.518]     MemoryModel: 6
[   191.518]     BankSize: 0
[   191.518]     NumberOfImages: 4
[   191.518]     RedMaskSize: 5
[   191.518]     RedFieldPosition: 10
[   191.519]     GreenMaskSize: 5
[   191.519]     GreenFieldPosition: 5
[   191.519]     BlueMaskSize: 5
[   191.519]     BlueFieldPosition: 0
[   191.519]     RsvdMaskSize: 0
[   191.519]     RsvdFieldPosition: 0
[   191.519]     DirectColorModeInfo: 0
[   191.519]     PhysBasePtr: 0xc0000000
[   191.519]     LinBytesPerScanLine: 2048
[   191.519]     BnkNumberOfImagePages: 4
[   191.519]     LinNumberOfImagePages: 4
[   191.519]     LinRedMaskSize: 5
[   191.519]     LinRedFieldPosition: 10
[   191.519]     LinGreenMaskSize: 5
[   191.519]     LinGreenFieldPosition: 5
[   191.519]     LinBlueMaskSize: 5
[   191.519]     LinBlueFieldPosition: 0
[   191.519]     LinRsvdMaskSize: 0
[   191.519]     LinRsvdFieldPosition: 0
[   191.519]     MaxPixelClock: 0
[   191.519] Mode: 117 (1024x768)
[   191.519]     ModeAttributes: 0x9b
[   191.519]     WinAAttributes: 0x7
[   191.519]     WinBAttributes: 0x0
[   191.519]     WinGranularity: 64
[   191.519]     WinSize: 64
[   191.519]     WinASegment: 0xa000
[   191.519]     WinBSegment: 0xa000
[   191.519]     WinFuncPtr: 0xc000862b
[   191.519]     BytesPerScanline: 2048
[   191.519]     XResolution: 1024
[   191.519]     YResolution: 768
[   191.519]     XCharSize: 8
[   191.519]     YCharSize: 16
[   191.519]     NumberOfPlanes: 1
[   191.519]     BitsPerPixel: 16
[   191.519]     NumberOfBanks: 1
[   191.519]     MemoryModel: 6
[   191.519]     BankSize: 0
[   191.519]     NumberOfImages: 4
[   191.519]     RedMaskSize: 5
[   191.519]     RedFieldPosition: 11
[   191.519]     GreenMaskSize: 6
[   191.519]     GreenFieldPosition: 5
[   191.519]     BlueMaskSize: 5
[   191.519]     BlueFieldPosition: 0
[   191.519]     RsvdMaskSize: 0
[   191.519]     RsvdFieldPosition: 0
[   191.519]     DirectColorModeInfo: 0
[   191.519]     PhysBasePtr: 0xc0000000
[   191.519]     LinBytesPerScanLine: 2048
[   191.519]     BnkNumberOfImagePages: 4
[   191.519]     LinNumberOfImagePages: 4
[   191.519]     LinRedMaskSize: 5
[   191.519]     LinRedFieldPosition: 11
[   191.519]     LinGreenMaskSize: 6
[   191.519]     LinGreenFieldPosition: 5
[   191.519]     LinBlueMaskSize: 5
[   191.519]     LinBlueFieldPosition: 0
[   191.519]     LinRsvdMaskSize: 0
[   191.519]     LinRsvdFieldPosition: 0
[   191.519]     MaxPixelClock: 0
[   191.520] Mode: 127 (320x240)
[   191.520]     ModeAttributes: 0x9f
[   191.520]     WinAAttributes: 0x7
[   191.520]     WinBAttributes: 0x0
[   191.520]     WinGranularity: 64
[   191.520]     WinSize: 64
[   191.520]     WinASegment: 0xa000
[   191.520]     WinBSegment: 0xa000
[   191.520]     WinFuncPtr: 0xc000862b
[   191.520]     BytesPerScanline: 320
[   191.520]     XResolution: 320
[   191.520]     YResolution: 240
[   191.520]     XCharSize: 8
[   191.520]     YCharSize: 8
[   191.520]     NumberOfPlanes: 1
[   191.520]     BitsPerPixel: 8
[   191.520]     NumberOfBanks: 1
[   191.520]     MemoryModel: 4
[   191.520]     BankSize: 0
[   191.520]     NumberOfImages: 63
[   191.520]     RedMaskSize: 0
[   191.520]     RedFieldPosition: 0
[   191.520]     GreenMaskSize: 0
[   191.520]     GreenFieldPosition: 0
[   191.520]     BlueMaskSize: 0
[   191.520]     BlueFieldPosition: 0
[   191.520]     RsvdMaskSize: 0
[   191.520]     RsvdFieldPosition: 0
[   191.520]     DirectColorModeInfo: 0
[   191.520]     PhysBasePtr: 0xc0000000
[   191.520]     LinBytesPerScanLine: 320
[   191.520]     BnkNumberOfImagePages: 63
[   191.520]     LinNumberOfImagePages: 63
[   191.520]     LinRedMaskSize: 0
[   191.520]     LinRedFieldPosition: 0
[   191.520]     LinGreenMaskSize: 0
[   191.520]     LinGreenFieldPosition: 0
[   191.520]     LinBlueMaskSize: 0
[   191.520]     LinBlueFieldPosition: 0
[   191.520]     LinRsvdMaskSize: 0
[   191.520]     LinRsvdFieldPosition: 0
[   191.520]     MaxPixelClock: 0
[   191.520] Mode: 128 (400x300)
[   191.520]     ModeAttributes: 0x9f
[   191.520]     WinAAttributes: 0x7
[   191.520]     WinBAttributes: 0x0
[   191.520]     WinGranularity: 64
[   191.520]     WinSize: 64
[   191.520]     WinASegment: 0xa000
[   191.520]     WinBSegment: 0xa000
[   191.520]     WinFuncPtr: 0xc000862b
[   191.520]     BytesPerScanline: 400
[   191.520]     XResolution: 400
[   191.520]     YResolution: 300
[   191.520]     XCharSize: 8
[   191.520]     YCharSize: 8
[   191.520]     NumberOfPlanes: 1
[   191.520]     BitsPerPixel: 8
[   191.520]     NumberOfBanks: 1
[   191.520]     MemoryModel: 4
[   191.520]     BankSize: 0
[   191.520]     NumberOfImages: 63
[   191.520]     RedMaskSize: 0
[   191.520]     RedFieldPosition: 0
[   191.520]     GreenMaskSize: 0
[   191.520]     GreenFieldPosition: 0
[   191.520]     BlueMaskSize: 0
[   191.520]     BlueFieldPosition: 0
[   191.520]     RsvdMaskSize: 0
[   191.520]     RsvdFieldPosition: 0
[   191.520]     DirectColorModeInfo: 0
[   191.520]     PhysBasePtr: 0xc0000000
[   191.520]     LinBytesPerScanLine: 400
[   191.520]     BnkNumberOfImagePages: 63
[   191.520]     LinNumberOfImagePages: 63
[   191.520]     LinRedMaskSize: 0
[   191.520]     LinRedFieldPosition: 0
[   191.520]     LinGreenMaskSize: 0
[   191.520]     LinGreenFieldPosition: 0
[   191.520]     LinBlueMaskSize: 0
[   191.520]     LinBlueFieldPosition: 0
[   191.520]     LinRsvdMaskSize: 0
[   191.520]     LinRsvdFieldPosition: 0
[   191.520]     MaxPixelClock: 0
[   191.521] Mode: 129 (512x384)
[   191.521]     ModeAttributes: 0x9f
[   191.521]     WinAAttributes: 0x7
[   191.521]     WinBAttributes: 0x0
[   191.521]     WinGranularity: 64
[   191.521]     WinSize: 64
[   191.521]     WinASegment: 0xa000
[   191.521]     WinBSegment: 0xa000
[   191.521]     WinFuncPtr: 0xc000862b
[   191.521]     BytesPerScanline: 512
[   191.521]     XResolution: 512
[   191.521]     YResolution: 384
[   191.521]     XCharSize: 8
[   191.521]     YCharSize: 8
[   191.521]     NumberOfPlanes: 1
[   191.521]     BitsPerPixel: 8
[   191.521]     NumberOfBanks: 1
[   191.521]     MemoryModel: 4
[   191.521]     BankSize: 0
[   191.521]     NumberOfImages: 41
[   191.521]     RedMaskSize: 0
[   191.521]     RedFieldPosition: 0
[   191.521]     GreenMaskSize: 0
[   191.521]     GreenFieldPosition: 0
[   191.521]     BlueMaskSize: 0
[   191.521]     BlueFieldPosition: 0
[   191.521]     RsvdMaskSize: 0
[   191.521]     RsvdFieldPosition: 0
[   191.521]     DirectColorModeInfo: 0
[   191.521]     PhysBasePtr: 0xc0000000
[   191.521]     LinBytesPerScanLine: 512
[   191.521]     BnkNumberOfImagePages: 41
[   191.521]     LinNumberOfImagePages: 41
[   191.521]     LinRedMaskSize: 0
[   191.521]     LinRedFieldPosition: 0
[   191.521]     LinGreenMaskSize: 0
[   191.521]     LinGreenFieldPosition: 0
[   191.521]     LinBlueMaskSize: 0
[   191.521]     LinBlueFieldPosition: 0
[   191.521]     LinRsvdMaskSize: 0
[   191.521]     LinRsvdFieldPosition: 0
[   191.521]     MaxPixelClock: 0
[   191.521] Mode: 12a (320x240)
[   191.521]     ModeAttributes: 0x9b
[   191.521]     WinAAttributes: 0x7
[   191.521]     WinBAttributes: 0x0
[   191.521]     WinGranularity: 64
[   191.521]     WinSize: 64
[   191.521]     WinASegment: 0xa000
[   191.521]     WinBSegment: 0xa000
[   191.521]     WinFuncPtr: 0xc000862b
[   191.521]     BytesPerScanline: 640
[   191.521]     XResolution: 320
[   191.521]     YResolution: 240
[   191.521]     XCharSize: 8
[   191.521]     YCharSize: 8
[   191.521]     NumberOfPlanes: 1
[   191.521]     BitsPerPixel: 16
[   191.521]     NumberOfBanks: 1
[   191.521]     MemoryModel: 6
[   191.521]     BankSize: 0
[   191.521]     NumberOfImages: 41
[   191.521]     RedMaskSize: 5
[   191.521]     RedFieldPosition: 11
[   191.521]     GreenMaskSize: 6
[   191.521]     GreenFieldPosition: 5
[   191.521]     BlueMaskSize: 5
[   191.521]     BlueFieldPosition: 0
[   191.521]     RsvdMaskSize: 0
[   191.521]     RsvdFieldPosition: 0
[   191.521]     DirectColorModeInfo: 0
[   191.521]     PhysBasePtr: 0xc0000000
[   191.521]     LinBytesPerScanLine: 640
[   191.521]     BnkNumberOfImagePages: 41
[   191.521]     LinNumberOfImagePages: 41
[   191.521]     LinRedMaskSize: 5
[   191.521]     LinRedFieldPosition: 11
[   191.521]     LinGreenMaskSize: 6
[   191.521]     LinGreenFieldPosition: 5
[   191.522]     LinBlueMaskSize: 5
[   191.522]     LinBlueFieldPosition: 0
[   191.522]     LinRsvdMaskSize: 0
[   191.522]     LinRsvdFieldPosition: 0
[   191.522]     MaxPixelClock: 0
[   191.522] Mode: 12b (400x300)
[   191.522]     ModeAttributes: 0x9b
[   191.522]     WinAAttributes: 0x7
[   191.522]     WinBAttributes: 0x0
[   191.522]     WinGranularity: 64
[   191.522]     WinSize: 64
[   191.522]     WinASegment: 0xa000
[   191.522]     WinBSegment: 0xa000
[   191.522]     WinFuncPtr: 0xc000862b
[   191.522]     BytesPerScanline: 800
[   191.522]     XResolution: 400
[   191.522]     YResolution: 300
[   191.522]     XCharSize: 8
[   191.522]     YCharSize: 8
[   191.522]     NumberOfPlanes: 1
[   191.522]     BitsPerPixel: 16
[   191.522]     NumberOfBanks: 1
[   191.522]     MemoryModel: 6
[   191.522]     BankSize: 0
[   191.522]     NumberOfImages: 31
[   191.522]     RedMaskSize: 5
[   191.522]     RedFieldPosition: 11
[   191.522]     GreenMaskSize: 6
[   191.522]     GreenFieldPosition: 5
[   191.522]     BlueMaskSize: 5
[   191.522]     BlueFieldPosition: 0
[   191.522]     RsvdMaskSize: 0
[   191.522]     RsvdFieldPosition: 0
[   191.522]     DirectColorModeInfo: 0
[   191.522]     PhysBasePtr: 0xc0000000
[   191.522]     LinBytesPerScanLine: 800
[   191.522]     BnkNumberOfImagePages: 31
[   191.522]     LinNumberOfImagePages: 31
[   191.522]     LinRedMaskSize: 5
[   191.522]     LinRedFieldPosition: 11
[   191.522]     LinGreenMaskSize: 6
[   191.522]     LinGreenFieldPosition: 5
[   191.522]     LinBlueMaskSize: 5
[   191.522]     LinBlueFieldPosition: 0
[   191.522]     LinRsvdMaskSize: 0
[   191.522]     LinRsvdFieldPosition: 0
[   191.522]     MaxPixelClock: 0
[   191.523] Mode: 12c (512x384)
[   191.523]     ModeAttributes: 0x9b
[   191.523]     WinAAttributes: 0x7
[   191.523]     WinBAttributes: 0x0
[   191.523]     WinGranularity: 64
[   191.523]     WinSize: 64
[   191.523]     WinASegment: 0xa000
[   191.523]     WinBSegment: 0xa000
[   191.523]     WinFuncPtr: 0xc000862b
[   191.523]     BytesPerScanline: 1024
[   191.523]     XResolution: 512
[   191.523]     YResolution: 384
[   191.523]     XCharSize: 8
[   191.523]     YCharSize: 8
[   191.523]     NumberOfPlanes: 1
[   191.523]     BitsPerPixel: 16
[   191.523]     NumberOfBanks: 1
[   191.523]     MemoryModel: 6
[   191.523]     BankSize: 0
[   191.523]     NumberOfImages: 20
[   191.523]     RedMaskSize: 5
[   191.523]     RedFieldPosition: 11
[   191.523]     GreenMaskSize: 6
[   191.523]     GreenFieldPosition: 5
[   191.523]     BlueMaskSize: 5
[   191.523]     BlueFieldPosition: 0
[   191.523]     RsvdMaskSize: 0
[   191.523]     RsvdFieldPosition: 0
[   191.523]     DirectColorModeInfo: 0
[   191.523]     PhysBasePtr: 0xc0000000
[   191.523]     LinBytesPerScanLine: 1024
[   191.523]     BnkNumberOfImagePages: 20
[   191.523]     LinNumberOfImagePages: 20
[   191.523]     LinRedMaskSize: 5
[   191.523]     LinRedFieldPosition: 11
[   191.523]     LinGreenMaskSize: 6
[   191.523]     LinGreenFieldPosition: 5
[   191.523]     LinBlueMaskSize: 5
[   191.523]     LinBlueFieldPosition: 0
[   191.523]     LinRsvdMaskSize: 0
[   191.523]     LinRsvdFieldPosition: 0
[   191.523]     MaxPixelClock: 0
[   191.523] Mode: 12d (320x200)
[   191.523]     ModeAttributes: 0x9f
[   191.523]     WinAAttributes: 0x7
[   191.523]     WinBAttributes: 0x0
[   191.523]     WinGranularity: 64
[   191.523]     WinSize: 64
[   191.523]     WinASegment: 0xa000
[   191.523]     WinBSegment: 0xa000
[   191.523]     WinFuncPtr: 0xc000862b
[   191.523]     BytesPerScanline: 320
[   191.523]     XResolution: 320
[   191.523]     YResolution: 200
[   191.523]     XCharSize: 8
[   191.523]     YCharSize: 8
[   191.523]     NumberOfPlanes: 1
[   191.523]     BitsPerPixel: 8
[   191.523]     NumberOfBanks: 1
[   191.523]     MemoryModel: 4
[   191.523]     BankSize: 0
[   191.523]     NumberOfImages: 127
[   191.523]     RedMaskSize: 0
[   191.523]     RedFieldPosition: 0
[   191.523]     GreenMaskSize: 0
[   191.523]     GreenFieldPosition: 0
[   191.523]     BlueMaskSize: 0
[   191.523]     BlueFieldPosition: 0
[   191.523]     RsvdMaskSize: 0
[   191.523]     RsvdFieldPosition: 0
[   191.523]     DirectColorModeInfo: 0
[   191.523]     PhysBasePtr: 0xc0000000
[   191.523]     LinBytesPerScanLine: 320
[   191.523]     BnkNumberOfImagePages: 127
[   191.523]     LinNumberOfImagePages: 127
[   191.523]     LinRedMaskSize: 0
[   191.523]     LinRedFieldPosition: 0
[   191.523]     LinGreenMaskSize: 0
[   191.523]     LinGreenFieldPosition: 0
[   191.523]     LinBlueMaskSize: 0
[   191.523]     LinBlueFieldPosition: 0
[   191.523]     LinRsvdMaskSize: 0
[   191.523]     LinRsvdFieldPosition: 0
[   191.523]     MaxPixelClock: 0
[   191.524] Mode: 131 (640x400)
[   191.524]     ModeAttributes: 0x9b
[   191.524]     WinAAttributes: 0x7
[   191.524]     WinBAttributes: 0x0
[   191.524]     WinGranularity: 64
[   191.524]     WinSize: 64
[   191.524]     WinASegment: 0xa000
[   191.524]     WinBSegment: 0xa000
[   191.524]     WinFuncPtr: 0xc000862b
[   191.524]     BytesPerScanline: 1280
[   191.524]     XResolution: 640
[   191.524]     YResolution: 400
[   191.524]     XCharSize: 8
[   191.524]     YCharSize: 16
[   191.524]     NumberOfPlanes: 1
[   191.524]     BitsPerPixel: 16
[   191.524]     NumberOfBanks: 1
[   191.524]     MemoryModel: 6
[   191.524]     BankSize: 0
[   191.524]     NumberOfImages: 15
[   191.524]     RedMaskSize: 5
[   191.524]     RedFieldPosition: 11
[   191.524]     GreenMaskSize: 6
[   191.524]     GreenFieldPosition: 5
[   191.524]     BlueMaskSize: 5
[   191.524]     BlueFieldPosition: 0
[   191.524]     RsvdMaskSize: 0
[   191.524]     RsvdFieldPosition: 0
[   191.524]     DirectColorModeInfo: 0
[   191.524]     PhysBasePtr: 0xc0000000
[   191.524]     LinBytesPerScanLine: 1280
[   191.524]     BnkNumberOfImagePages: 15
[   191.524]     LinNumberOfImagePages: 15
[   191.524]     LinRedMaskSize: 5
[   191.524]     LinRedFieldPosition: 11
[   191.524]     LinGreenMaskSize: 6
[   191.524]     LinGreenFieldPosition: 5
[   191.524]     LinBlueMaskSize: 5
[   191.524]     LinBlueFieldPosition: 0
[   191.524]     LinRsvdMaskSize: 0
[   191.524]     LinRsvdFieldPosition: 0
[   191.524]     MaxPixelClock: 0
[   191.525] *Mode: 112 (640x480)
[   191.525]     ModeAttributes: 0x9b
[   191.525]     WinAAttributes: 0x7
[   191.525]     WinBAttributes: 0x0
[   191.525]     WinGranularity: 64
[   191.525]     WinSize: 64
[   191.525]     WinASegment: 0xa000
[   191.525]     WinBSegment: 0xa000
[   191.525]     WinFuncPtr: 0xc000862b
[   191.525]     BytesPerScanline: 2560
[   191.525]     XResolution: 640
[   191.525]     YResolution: 480
[   191.525]     XCharSize: 8
[   191.525]     YCharSize: 16
[   191.525]     NumberOfPlanes: 1
[   191.525]     BitsPerPixel: 32
[   191.525]     NumberOfBanks: 1
[   191.525]     MemoryModel: 6
[   191.525]     BankSize: 0
[   191.525]     NumberOfImages: 5
[   191.525]     RedMaskSize: 8
[   191.525]     RedFieldPosition: 16
[   191.525]     GreenMaskSize: 8
[   191.525]     GreenFieldPosition: 8
[   191.525]     BlueMaskSize: 8
[   191.525]     BlueFieldPosition: 0
[   191.525]     RsvdMaskSize: 8
[   191.525]     RsvdFieldPosition: 24
[   191.525]     DirectColorModeInfo: 0
[   191.525]     PhysBasePtr: 0xc0000000
[   191.525]     LinBytesPerScanLine: 2560
[   191.525]     BnkNumberOfImagePages: 5
[   191.525]     LinNumberOfImagePages: 5
[   191.525]     LinRedMaskSize: 8
[   191.525]     LinRedFieldPosition: 16
[   191.525]     LinGreenMaskSize: 8
[   191.525]     LinGreenFieldPosition: 8
[   191.525]     LinBlueMaskSize: 8
[   191.525]     LinBlueFieldPosition: 0
[   191.525]     LinRsvdMaskSize: 8
[   191.525]     LinRsvdFieldPosition: 24
[   191.525]     MaxPixelClock: 0
[   191.526] *Mode: 115 (800x600)
[   191.526]     ModeAttributes: 0x9b
[   191.526]     WinAAttributes: 0x7
[   191.526]     WinBAttributes: 0x0
[   191.526]     WinGranularity: 64
[   191.526]     WinSize: 64
[   191.526]     WinASegment: 0xa000
[   191.526]     WinBSegment: 0xa000
[   191.526]     WinFuncPtr: 0xc000862b
[   191.526]     BytesPerScanline: 3200
[   191.526]     XResolution: 800
[   191.526]     YResolution: 600
[   191.526]     XCharSize: 8
[   191.526]     YCharSize: 16
[   191.526]     NumberOfPlanes: 1
[   191.526]     BitsPerPixel: 32
[   191.526]     NumberOfBanks: 1
[   191.526]     MemoryModel: 6
[   191.526]     BankSize: 0
[   191.526]     NumberOfImages: 3
[   191.526]     RedMaskSize: 8
[   191.526]     RedFieldPosition: 16
[   191.526]     GreenMaskSize: 8
[   191.526]     GreenFieldPosition: 8
[   191.526]     BlueMaskSize: 8
[   191.526]     BlueFieldPosition: 0
[   191.526]     RsvdMaskSize: 8
[   191.526]     RsvdFieldPosition: 24
[   191.526]     DirectColorModeInfo: 0
[   191.526]     PhysBasePtr: 0xc0000000
[   191.526]     LinBytesPerScanLine: 3200
[   191.526]     BnkNumberOfImagePages: 3
[   191.526]     LinNumberOfImagePages: 3
[   191.526]     LinRedMaskSize: 8
[   191.526]     LinRedFieldPosition: 16
[   191.526]     LinGreenMaskSize: 8
[   191.526]     LinGreenFieldPosition: 8
[   191.526]     LinBlueMaskSize: 8
[   191.526]     LinBlueFieldPosition: 0
[   191.526]     LinRsvdMaskSize: 8
[   191.526]     LinRsvdFieldPosition: 24
[   191.526]     MaxPixelClock: 0
[   191.527] *Mode: 118 (1024x768)
[   191.527]     ModeAttributes: 0x9b
[   191.527]     WinAAttributes: 0x7
[   191.527]     WinBAttributes: 0x0
[   191.527]     WinGranularity: 64
[   191.527]     WinSize: 64
[   191.527]     WinASegment: 0xa000
[   191.527]     WinBSegment: 0xa000
[   191.527]     WinFuncPtr: 0xc000862b
[   191.527]     BytesPerScanline: 4096
[   191.527]     XResolution: 1024
[   191.527]     YResolution: 768
[   191.527]     XCharSize: 8
[   191.527]     YCharSize: 16
[   191.527]     NumberOfPlanes: 1
[   191.527]     BitsPerPixel: 32
[   191.527]     NumberOfBanks: 1
[   191.527]     MemoryModel: 6
[   191.527]     BankSize: 0
[   191.527]     NumberOfImages: 1
[   191.527]     RedMaskSize: 8
[   191.527]     RedFieldPosition: 16
[   191.527]     GreenMaskSize: 8
[   191.527]     GreenFieldPosition: 8
[   191.527]     BlueMaskSize: 8
[   191.527]     BlueFieldPosition: 0
[   191.527]     RsvdMaskSize: 8
[   191.527]     RsvdFieldPosition: 24
[   191.527]     DirectColorModeInfo: 0
[   191.527]     PhysBasePtr: 0xc0000000
[   191.527]     LinBytesPerScanLine: 4096
[   191.527]     BnkNumberOfImagePages: 1
[   191.527]     LinNumberOfImagePages: 1
[   191.527]     LinRedMaskSize: 8
[   191.527]     LinRedFieldPosition: 16
[   191.527]     LinGreenMaskSize: 8
[   191.527]     LinGreenFieldPosition: 8
[   191.527]     LinBlueMaskSize: 8
[   191.527]     LinBlueFieldPosition: 0
[   191.527]     LinRsvdMaskSize: 8
[   191.527]     LinRsvdFieldPosition: 24
[   191.527]     MaxPixelClock: 0
[   191.528] Mode: 102 (800x600)
[   191.528]     ModeAttributes: 0x1f
[   191.528]     WinAAttributes: 0x7
[   191.528]     WinBAttributes: 0x0
[   191.528]     WinGranularity: 64
[   191.528]     WinSize: 64
[   191.528]     WinASegment: 0xa000
[   191.528]     WinBSegment: 0xa000
[   191.528]     WinFuncPtr: 0xc000862b
[   191.528]     BytesPerScanline: 100
[   191.528]     XResolution: 800
[   191.528]     YResolution: 600
[   191.528]     XCharSize: 8
[   191.528]     YCharSize: 16
[   191.528]     NumberOfPlanes: 4
[   191.528]     BitsPerPixel: 4
[   191.528]     NumberOfBanks: 1
[   191.528]     MemoryModel: 3
[   191.528]     BankSize: 0
[   191.528]     NumberOfImages: 31
[   191.528]     RedMaskSize: 0
[   191.528]     RedFieldPosition: 0
[   191.528]     GreenMaskSize: 0
[   191.528]     GreenFieldPosition: 0
[   191.528]     BlueMaskSize: 0
[   191.528]     BlueFieldPosition: 0
[   191.528]     RsvdMaskSize: 0
[   191.528]     RsvdFieldPosition: 0
[   191.528]     DirectColorModeInfo: 0
[   191.528]     PhysBasePtr: 0xc0000000
[   191.528]     LinBytesPerScanLine: 100
[   191.528]     BnkNumberOfImagePages: 31
[   191.528]     LinNumberOfImagePages: 31
[   191.528]     LinRedMaskSize: 0
[   191.528]     LinRedFieldPosition: 0
[   191.528]     LinGreenMaskSize: 0
[   191.528]     LinGreenFieldPosition: 0
[   191.528]     LinBlueMaskSize: 0
[   191.528]     LinBlueFieldPosition: 0
[   191.528]     LinRsvdMaskSize: 0
[   191.528]     LinRsvdFieldPosition: 0
[   191.528]     MaxPixelClock: 0
[   191.528] 
[   191.528] (II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[   191.528] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[   191.528] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[   191.528] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[   191.528] (WW) VESA(0): Unable to estimate virtual size
[   191.528] (II) VESA(0): Not using built-in mode "1280x768" (no mode of this name)
[   191.528] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[   191.528] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[   191.528] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[   191.528] (WW) VESA(0): No valid modes left. Trying less strict filter...
[   191.528] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[   191.528] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[   191.528] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[   191.528] (WW) VESA(0): Unable to estimate virtual size
[   191.528] (II) VESA(0): Not using built-in mode "1280x768" (hsync out of range)
[   191.528] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[   191.528] (**) VESA(0): *Built-in mode "1024x768"
[   191.528] (**) VESA(0): *Built-in mode "800x600"
[   191.528] (**) VESA(0): *Built-in mode "640x480"
[   191.529] (==) VESA(0): DPI set to (96, 96)
[   191.529] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[   191.529] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[   191.529] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[   191.529] (**) VESA(0): Using "Shadow Framebuffer"
[   191.529] (II) Loading sub module "shadow"
[   191.529] (II) LoadModule: "shadow"
[   191.530] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   191.530] (II) Module shadow: vendor="X.Org Foundation"
[   191.530]     compiled for 1.15.1, module version = 1.1.0
[   191.530]     ABI class: X.Org ANSI C Emulation, version 0.4
[   191.530] (II) Loading sub module "fb"
[   191.530] (II) LoadModule: "fb"
[   191.530] (II) Loading /usr/lib/xorg/modules/libfb.so
[   191.531] (II) Module fb: vendor="X.Org Foundation"
[   191.531]     compiled for 1.15.1, module version = 1.0.0
[   191.531]     ABI class: X.Org ANSI C Emulation, version 0.4
[   191.531] (II) UnloadModule: "sis"
[   191.531] (II) Unloading sis
[   191.531] (==) Depth 24 pixmap format is 32 bpp
[   191.531] (II) Loading sub module "int10"
[   191.531] (II) LoadModule: "int10"
[   191.531] (II) Loading /usr/lib/xorg/modules/libint10.so
[   191.531] (II) Module int10: vendor="X.Org Foundation"
[   191.531]     compiled for 1.15.1, module version = 1.0.0
[   191.531]     ABI class: X.Org Video Driver, version 15.0
[   191.531] (II) VESA(0): initializing int10
[   191.537] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   191.539] (II) VESA(0): VESA BIOS detected
[   191.539] (II) VESA(0): VESA VBE Version 3.0
[   191.539] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[   191.539] (II) VESA(0): VESA VBE OEM: SiS
[   191.539] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[   191.539] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[   191.539] (II) VESA(0): VESA VBE OEM Product: 6330
[   191.539] (II) VESA(0): VESA VBE OEM Product Rev: 3.72.15a
[   191.540] (II) VESA(0): virtual address = 0xa6a64000,
    physical address = 0xc0000000, size = 268435456
[   191.554] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[   192.111] (==) VESA(0): Default visual is TrueColor
[   192.112] (==) VESA(0): Backing store enabled
[   192.112] (==) VESA(0): DPMS enabled
[   192.112] (==) RandR enabled
[   192.128] (II) SELinux: Disabled on system
[   192.131] (II) AIGLX: Screen 0 is not DRI2 capable
[   192.131] (EE) AIGLX: reverting to software rendering
[   192.154] (II) AIGLX: Loaded and initialized swrast
[   192.154] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   192.180] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   192.187] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   192.187] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   192.187] (II) LoadModule: "evdev"
[   192.187] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   192.188] (II) Module evdev: vendor="X.Org Foundation"
[   192.188]     compiled for 1.15.0, module version = 2.8.2
[   192.188]     Module class: X.Org XInput Driver
[   192.188]     ABI class: X.Org XInput driver, version 20.0
[   192.188] (II) Using input driver 'evdev' for 'Power Button'
[   192.188] (**) Power Button: always reports core events
[   192.188] (**) evdev: Power Button: Device: "/dev/input/event2"
[   192.188] (--) evdev: Power Button: Vendor 0 Product 0x1
[   192.188] (--) evdev: Power Button: Found keys
[   192.188] (II) evdev: Power Button: Configuring as keyboard
[   192.188] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   192.188] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   192.188] (**) Option "xkb_rules" "evdev"
[   192.188] (**) Option "xkb_model" "pc105"
[   192.188] (**) Option "xkb_layout" "us"
[   192.189] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   192.189] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   192.189] (II) Using input driver 'evdev' for 'Power Button'
[   192.189] (**) Power Button: always reports core events
[   192.189] (**) evdev: Power Button: Device: "/dev/input/event1"
[   192.189] (--) evdev: Power Button: Vendor 0 Product 0x1
[   192.189] (--) evdev: Power Button: Found keys
[   192.190] (II) evdev: Power Button: Configuring as keyboard
[   192.190] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1/event1"
[   192.190] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   192.190] (**) Option "xkb_rules" "evdev"
[   192.190] (**) Option "xkb_model" "pc105"
[   192.190] (**) Option "xkb_layout" "us"
[   192.191] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   192.191] (II) No input driver specified, ignoring this device.
[   192.191] (II) This device may have been added with another device file.
[   192.191] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   192.191] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   192.191] (II) Using input driver 'evdev' for 'Video Bus'
[   192.191] (**) Video Bus: always reports core events
[   192.191] (**) evdev: Video Bus: Device: "/dev/input/event4"
[   192.191] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   192.191] (--) evdev: Video Bus: Found keys
[   192.191] (II) evdev: Video Bus: Configuring as keyboard
[   192.191] (**) Option "config_info"  "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input5/event4"
[   192.191] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   192.191] (**) Option "xkb_rules" "evdev"
[   192.191] (**) Option "xkb_model" "pc105"
[   192.191] (**) Option "xkb_layout" "us"
[   192.193] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event5)
[   192.193] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[   192.193] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[   192.193] (**) Genius Optical Mouse: always reports core events
[   192.193] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event5"
[   192.193] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[   192.193] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[   192.193] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[   192.193] (--) evdev: Genius Optical Mouse: Found relative axes
[   192.193] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[   192.193] (II) evdev: Genius Optical Mouse: Configuring as mouse
[   192.193] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[   192.193] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[   192.193] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   192.193] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input6/event5"
[   192.193] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 9)
[   192.193] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[   192.193] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[   192.193] (**) Genius Optical Mouse: (accel) acceleration profile 0
[   192.193] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[   192.193] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[   192.194] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[   192.194] (II) No input driver specified, ignoring this device.
[   192.194] (II) This device may have been added with another device file.
[   192.195] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event9)
[   192.195] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[   192.195] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[   192.195] (**) USB 2.0 Camera: always reports core events
[   192.195] (**) evdev: USB 2.0 Camera: Device: "/dev/input/event9"
[   192.195] (--) evdev: USB 2.0 Camera: Vendor 0x4f2 Product 0xb018
[   192.195] (--) evdev: USB 2.0 Camera: Found keys
[   192.195] (II) evdev: USB 2.0 Camera: Configuring as keyboard
[   192.195] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input10/event9"
[   192.195] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD, id 10)
[   192.195] (**) Option "xkb_rules" "evdev"
[   192.195] (**) Option "xkb_model" "pc105"
[   192.195] (**) Option "xkb_layout" "us"
[   192.196] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event8)
[   192.196] (II) No input driver specified, ignoring this device.
[   192.196] (II) This device may have been added with another device file.
[   192.196] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event7)
[   192.196] (II) No input driver specified, ignoring this device.
[   192.196] (II) This device may have been added with another device file.
[   192.197] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   192.197] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   192.197] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   192.197] (**) AT Translated Set 2 keyboard: always reports core events
[   192.197] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   192.197] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   192.197] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   192.197] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   192.197] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   192.197] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   192.197] (**) Option "xkb_rules" "evdev"
[   192.197] (**) Option "xkb_model" "pc105"
[   192.197] (**) Option "xkb_layout" "us"
[   192.198] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[   192.198] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[   192.198] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[   192.198] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[   192.198] (II) LoadModule: "synaptics"
[   192.199] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   192.199] (II) Module synaptics: vendor="X.Org Foundation"
[   192.199]     compiled for 1.15.0, module version = 1.7.4
[   192.199]     Module class: X.Org XInput Driver
[   192.199]     ABI class: X.Org XInput driver, version 20.0
[   192.199] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[   192.199] (**) ETPS/2 Elantech Touchpad: always reports core events
[   192.199] (**) Option "Device" "/dev/input/event6"
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 32 - 544 (res 0)
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 32 - 352 (res 0)
[   192.348] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[   192.348] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report finger width.
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: invalid pressure range.  defaulting to 0 - 255
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: invalid finger width range.  defaulting to 0 - 15
[   192.348] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   192.348] (**) ETPS/2 Elantech Touchpad: always reports core events
[   192.444] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event6"
[   192.444] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[   192.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[   192.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[   192.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.332
[   192.444] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[   192.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[   192.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   192.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   192.444] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   192.445] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[   192.445] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"


```

My Xorg.0.log (fresh install 640x480)
```
[    16.945] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    16.945] X Protocol Version 11, Revision 0
[    16.945] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    16.945] Current Operating System: Linux exo 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686
[    16.945] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic  root=UUID=d489848e-6593-440c-a543-6e0a37783137 ro quiet splash  vt.handoff=7
[    16.945] Build Date: 16 April 2014  01:40:08PM
[    16.945] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    16.945] Current version of pixman: 0.30.2
[    16.945]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.945] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.945] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 23:10:00 2014
[    16.959] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.959] (==) No Layout section.  Using the first Screen section.
[    16.959] (==) No screen section available. Using defaults.
[    16.959] (**) |-->Screen "Default Screen Section" (0)
[    16.959] (**) |   |-->Monitor "<default monitor>"
[    16.960] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.960] (==) Automatically adding devices
[    16.960] (==) Automatically enabling devices
[    16.960] (==) Automatically adding GPU devices
[    16.960] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.960]     Entry deleted from font path.
[    16.960] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.960]     Entry deleted from font path.
[    16.960] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.960]     Entry deleted from font path.
[    16.960] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.960]     Entry deleted from font path.
[    16.960] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.960]     Entry deleted from font path.
[    16.960] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.960] (==) ModulePath set to  "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.960] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.960] (II) Loader magic: 0xb77166c0
[    16.960] (II) Module ABI versions:
[    16.960]     X.Org ANSI C Emulation: 0.4
[    16.960]     X.Org Video Driver: 15.0
[    16.960]     X.Org XInput driver : 20.0
[    16.960]     X.Org Server Extension : 8.0
[    16.962] (--) PCI:*(0:1:0:0) 1039:6351:14c0:002b rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[    16.962] Initializing built-in extension Generic Event Extension
[    16.962] Initializing built-in extension SHAPE
[    16.962] Initializing built-in extension MIT-SHM
[    16.962] Initializing built-in extension XInputExtension
[    16.962] Initializing built-in extension XTEST
[    16.962] Initializing built-in extension BIG-REQUESTS
[    16.962] Initializing built-in extension SYNC
[    16.962] Initializing built-in extension XKEYBOARD
[    16.962] Initializing built-in extension XC-MISC
[    16.962] Initializing built-in extension SECURITY
[    16.962] Initializing built-in extension XINERAMA
[    16.962] Initializing built-in extension XFIXES
[    16.962] Initializing built-in extension RENDER
[    16.962] Initializing built-in extension RANDR
[    16.962] Initializing built-in extension COMPOSITE
[    16.962] Initializing built-in extension DAMAGE
[    16.962] Initializing built-in extension MIT-SCREEN-SAVER
[    16.962] Initializing built-in extension DOUBLE-BUFFER
[    16.962] Initializing built-in extension RECORD
[    16.962] Initializing built-in extension DPMS
[    16.962] Initializing built-in extension Present
[    16.962] Initializing built-in extension DRI3
[    16.962] Initializing built-in extension X-Resource
[    16.962] Initializing built-in extension XVideo
[    16.962] Initializing built-in extension XVideo-MotionCompensation
[    16.962] Initializing built-in extension SELinux
[    16.962] Initializing built-in extension XFree86-VidModeExtension
[    16.962] Initializing built-in extension XFree86-DGA
[    16.962] Initializing built-in extension XFree86-DRI
[    16.962] Initializing built-in extension DRI2
[    16.962] (II) LoadModule: "glx"
[    16.989] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.127] (II) Module glx: vendor="X.Org Foundation"
[    17.127]     compiled for 1.15.1, module version = 1.0.0
[    17.127]     ABI class: X.Org Server Extension, version 8.0
[    17.127] (==) AIGLX enabled
[    17.127] Loading extension GLX
[    17.127] (==) Matched sis as autoconfigured driver 0
[    17.127] (==) Matched modesetting as autoconfigured driver 1
[    17.127] (==) Matched fbdev as autoconfigured driver 2
[    17.127] (==) Matched vesa as autoconfigured driver 3
[    17.127] (==) Assigned the driver to the xf86ConfigLayout
[    17.127] (II) LoadModule: "sis"
[    17.127] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    17.162] (II) Module sis: vendor="X.Org Foundation"
[    17.162]     compiled for 1.15.0, module version = 0.10.7
[    17.162]     Module class: X.Org Video Driver
[    17.162]     ABI class: X.Org Video Driver, version 15.0
[    17.162] (II) LoadModule: "modesetting"
[    17.162] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.173] (II) Module modesetting: vendor="X.Org Foundation"
[    17.173]     compiled for 1.15.0, module version = 0.8.1
[    17.173]     Module class: X.Org Video Driver
[    17.173]     ABI class: X.Org Video Driver, version 15.0
[    17.173] (II) LoadModule: "fbdev"
[    17.173] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.178] (II) Module fbdev: vendor="X.Org Foundation"
[    17.178]     compiled for 1.15.0, module version = 0.4.4
[    17.178]     Module class: X.Org Video Driver
[    17.178]     ABI class: X.Org Video Driver, version 15.0
[    17.178] (II) LoadModule: "vesa"
[    17.178] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.179] (II) Module vesa: vendor="X.Org Foundation"
[    17.179]     compiled for 1.15.0, module version = 2.3.3
[    17.179]     Module class: X.Org Video Driver
[    17.179]     ABI class: X.Org Video Driver, version 15.0
[    17.179] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[    17.179] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[    17.179] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    17.179] (II) FBDEV: driver for framebuffer: fbdev
[    17.179] (II) VESA: driver for VESA chipsets: vesa
[    17.179] (++) using VT number 7

[    17.216] (WW) Falling back to old probe method for sis
[    17.217] (--) Assigning device section with no busID to primary device
[    17.217] (EE) open /dev/dri/card0: No such file or directory
[    17.217] (WW) Falling back to old probe method for modesetting
[    17.217] (EE) open /dev/dri/card0: No such file or directory
[    17.217] (II) Loading sub module "fbdevhw"
[    17.217] (II) LoadModule: "fbdevhw"
[    17.217] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.225] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.225]     compiled for 1.15.1, module version = 0.0.2
[    17.225]     ABI class: X.Org Video Driver, version 15.0
[    17.225] (**) FBDEV(1): claimed PCI slot 1@0:0:0
[    17.225] (II) FBDEV(1): using default device
[    17.225] (WW) Falling back to old probe method for vesa
[    17.225] (EE) Screen 0 deleted because of no matching config section.
[    17.225] (II) UnloadModule: "modesetting"
[    17.225] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.225] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    17.225] (==) FBDEV(0): RGB weight 888
[    17.225] (==) FBDEV(0): Default visual is TrueColor
[    17.225] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.225] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[    17.225] (II) FBDEV(0): checking modes against framebuffer device...
[    17.225] (II) FBDEV(0): checking modes against monitor...
[    17.225] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    17.225] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    17.225] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    17.226] (==) FBDEV(0): DPI set to (96, 96)
[    17.226] (II) Loading sub module "fb"
[    17.226] (II) LoadModule: "fb"
[    17.226] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.226] (II) Module fb: vendor="X.Org Foundation"
[    17.226]     compiled for 1.15.1, module version = 1.0.0
[    17.226]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.226] (**) FBDEV(0): using shadow framebuffer
[    17.226] (II) Loading sub module "shadow"
[    17.226] (II) LoadModule: "shadow"
[    17.226] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    17.226] (II) Module shadow: vendor="X.Org Foundation"
[    17.226]     compiled for 1.15.1, module version = 1.1.0
[    17.226]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.227] (II) UnloadModule: "sis"
[    17.227] (II) Unloading sis
[    17.227] (II) UnloadModule: "vesa"
[    17.227] (II) Unloading vesa
[    17.227] (==) Depth 24 pixmap format is 32 bpp
[    17.227] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    17.227] (==) FBDEV(0): Backing store enabled
[    17.227] (==) FBDEV(0): DPMS enabled
[    17.227] (==) RandR enabled
[    17.240] (II) SELinux: Disabled on system
[    17.243] (II) AIGLX: Screen 0 is not DRI2 capable
[    17.243] (EE) AIGLX: reverting to software rendering
[    17.343] (II) AIGLX: Loaded and initialized swrast
[    17.343] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    17.358] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.363] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    17.363] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.363] (II) LoadModule: "evdev"
[    17.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.374] (II) Module evdev: vendor="X.Org Foundation"
[    17.374]     compiled for 1.15.0, module version = 2.8.2
[    17.375]     Module class: X.Org XInput Driver
[    17.375]     ABI class: X.Org XInput driver, version 20.0
[    17.375] (II) Using input driver 'evdev' for 'Power Button'
[    17.375] (**) Power Button: always reports core events
[    17.375] (**) evdev: Power Button: Device: "/dev/input/event2"
[    17.375] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.375] (--) evdev: Power Button: Found keys
[    17.375] (II) evdev: Power Button: Configuring as keyboard
[    17.375] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    17.375] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    17.375] (**) Option "xkb_rules" "evdev"
[    17.375] (**) Option "xkb_model" "pc105"
[    17.375] (**) Option "xkb_layout" "es"
[    17.380] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    17.381] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.381] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.381] (II) Using input driver 'evdev' for 'Power Button'
[    17.381] (**) Power Button: always reports core events
[    17.381] (**) evdev: Power Button: Device: "/dev/input/event1"
[    17.381] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.381] (--) evdev: Power Button: Found keys
[    17.381] (II) evdev: Power Button: Configuring as keyboard
[    17.381] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1/event1"
[    17.381] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    17.381] (**) Option "xkb_rules" "evdev"
[    17.381] (**) Option "xkb_model" "pc105"
[    17.381] (**) Option "xkb_layout" "es"
[    17.382] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.382] (II) No input driver specified, ignoring this device.
[    17.382] (II) This device may have been added with another device file.
[    17.382] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    17.383] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.383] (II) Using input driver 'evdev' for 'Video Bus'
[    17.383] (**) Video Bus: always reports core events
[    17.383] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    17.383] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    17.383] (--) evdev: Video Bus: Found keys
[    17.383] (II) evdev: Video Bus: Configuring as keyboard
[    17.383] (**) Option "config_info"  "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input6/event5"
[    17.383] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    17.383] (**) Option "xkb_rules" "evdev"
[    17.383] (**) Option "xkb_model" "pc105"
[    17.383] (**) Option "xkb_layout" "es"
[    17.383] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[    17.383] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    17.383] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    17.383] (**) Genius Optical Mouse: always reports core events
[    17.384] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event4"
[    17.384] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[    17.384] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[    17.384] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[    17.384] (--) evdev: Genius Optical Mouse: Found relative axes
[    17.384] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[    17.384] (II) evdev: Genius Optical Mouse: Configuring as mouse
[    17.384] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[    17.384] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    17.384] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.384] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input5/event4"
[    17.384] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 9)
[    17.384] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[    17.384] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    17.384] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    17.384] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    17.384] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    17.384] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[    17.384] (II) No input driver specified, ignoring this device.
[    17.384] (II) This device may have been added with another device file.
[    17.385] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event6)
[    17.385] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    17.385] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    17.385] (**) USB 2.0 Camera: always reports core events
[    17.385] (**) evdev: USB 2.0 Camera: Device: "/dev/input/event6"
[    17.385] (--) evdev: USB 2.0 Camera: Vendor 0x4f2 Product 0xb018
[    17.385] (--) evdev: USB 2.0 Camera: Found keys
[    17.385] (II) evdev: USB 2.0 Camera: Configuring as keyboard
[    17.385] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input8/event6"
[    17.385] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD, id 10)
[    17.385] (**) Option "xkb_rules" "evdev"
[    17.385] (**) Option "xkb_model" "pc105"
[    17.385] (**) Option "xkb_layout" "es"
[    17.386] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event7)
[    17.386] (II) No input driver specified, ignoring this device.
[    17.386] (II) This device may have been added with another device file.
[    17.386] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event8)
[    17.386] (II) No input driver specified, ignoring this device.
[    17.386] (II) This device may have been added with another device file.
[    17.387] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    17.387] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.387] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.387] (**) AT Translated Set 2 keyboard: always reports core events
[    17.387] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    17.387] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    17.387] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    17.387] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    17.387] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    17.387] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    17.387] (**) Option "xkb_rules" "evdev"
[    17.387] (**) Option "xkb_model" "pc105"
[    17.387] (**) Option "xkb_layout" "es"
[    17.388] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event9)
[    17.388] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    17.388] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    17.388] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    17.388] (II) LoadModule: "synaptics"
[    17.388] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.388] (II) Module synaptics: vendor="X.Org Foundation"
[    17.388]     compiled for 1.15.0, module version = 1.7.4
[    17.388]     Module class: X.Org XInput Driver
[    17.388]     ABI class: X.Org XInput driver, version 20.0
[    17.388] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    17.388] (**) ETPS/2 Elantech Touchpad: always reports core events
[    17.388] (**) Option "Device" "/dev/input/event9"
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 32 - 544 (res 0)
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 32 - 352 (res 0)
[    17.508] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[    17.508] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report finger width.
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: invalid pressure range.  defaulting to 0 - 255
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: invalid finger width range.  defaulting to 0 - 15
[    17.508] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    17.508] (**) ETPS/2 Elantech Touchpad: always reports core events
[    17.572] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event9"
[    17.572] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    17.572] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    17.572] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    17.572] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.332
[    17.572] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    17.572] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    17.572] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    17.572] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    17.572] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    17.573] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    17.573] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    17.580] (EE) FBDEV(0): FBIOBLANK: Invalid argument


```

My Xorg.0.log (customised xorg.conf 1200x768)
```
[    58.519] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    58.519] X Protocol Version 11, Revision 0
[    58.519] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    58.519] Current Operating System: Linux exo 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686
[    58.519] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic  root=UUID=d489848e-6593-440c-a543-6e0a37783137 ro quiet splash  vt.handoff=7
[    58.519] Build Date: 16 April 2014  01:40:08PM
[    58.519] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    58.519] Current version of pixman: 0.30.2
[    58.519]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    58.519] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    58.519] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 21:54:51 2014
[    58.519] (==) Using config file: "/etc/X11/xorg.conf"
[    58.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    58.520] (==) No Layout section.  Using the first Screen section.
[    58.520] (**) |-->Screen "Default Screen" (0)
[    58.520] (**) |   |-->Monitor "Configured Monitor"
[    58.520] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    58.520] (**) |   |-->Device "Generic Video Card"
[    58.520] (==) Automatically adding devices
[    58.520] (==) Automatically enabling devices
[    58.520] (==) Automatically adding GPU devices
[    58.520] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    58.520]     Entry deleted from font path.
[    58.520] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    58.520]     Entry deleted from font path.
[    58.520] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    58.520]     Entry deleted from font path.
[    58.520] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    58.520]     Entry deleted from font path.
[    58.520] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    58.520]     Entry deleted from font path.
[    58.520] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    58.520] (==) ModulePath set to  "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    58.520] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    58.520] (II) Loader magic: 0xb770c6c0
[    58.520] (II) Module ABI versions:
[    58.520]     X.Org ANSI C Emulation: 0.4
[    58.520]     X.Org Video Driver: 15.0
[    58.520]     X.Org XInput driver : 20.0
[    58.520]     X.Org Server Extension : 8.0
[    58.522] (--) PCI:*(0:1:0:0) 1039:6351:14c0:002b rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[    58.522] Initializing built-in extension Generic Event Extension
[    58.522] Initializing built-in extension SHAPE
[    58.522] Initializing built-in extension MIT-SHM
[    58.522] Initializing built-in extension XInputExtension
[    58.522] Initializing built-in extension XTEST
[    58.522] Initializing built-in extension BIG-REQUESTS
[    58.522] Initializing built-in extension SYNC
[    58.522] Initializing built-in extension XKEYBOARD
[    58.522] Initializing built-in extension XC-MISC
[    58.522] Initializing built-in extension SECURITY
[    58.522] Initializing built-in extension XINERAMA
[    58.522] Initializing built-in extension XFIXES
[    58.522] Initializing built-in extension RENDER
[    58.522] Initializing built-in extension RANDR
[    58.522] Initializing built-in extension COMPOSITE
[    58.522] Initializing built-in extension DAMAGE
[    58.522] Initializing built-in extension MIT-SCREEN-SAVER
[    58.522] Initializing built-in extension DOUBLE-BUFFER
[    58.522] Initializing built-in extension RECORD
[    58.522] Initializing built-in extension DPMS
[    58.522] Initializing built-in extension Present
[    58.522] Initializing built-in extension DRI3
[    58.522] Initializing built-in extension X-Resource
[    58.522] Initializing built-in extension XVideo
[    58.522] Initializing built-in extension XVideo-MotionCompensation
[    58.522] Initializing built-in extension SELinux
[    58.522] Initializing built-in extension XFree86-VidModeExtension
[    58.522] Initializing built-in extension XFree86-DGA
[    58.522] Initializing built-in extension XFree86-DRI
[    58.522] Initializing built-in extension DRI2
[    58.522] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    58.522] (WW) "xmir" is not to be loaded by default. Skipping.
[    58.522] (II) LoadModule: "dri"
[    58.522] (II) Module "dri" already built-in
[    58.522] (II) LoadModule: "dbe"
[    58.523] (II) Module "dbe" already built-in
[    58.523] (II) LoadModule: "v4l"
[    58.553] (WW) Warning, couldn't open module v4l
[    58.553] (II) UnloadModule: "v4l"
[    58.553] (II) Unloading v4l
[    58.553] (EE) Failed to load module "v4l" (module does not exist, 0)
[    58.553] (II) LoadModule: "extmod"
[    58.553] (II) Module "extmod" already built-in
[    58.553] (II) LoadModule: "glx"
[    58.553] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    58.645] (II) Module glx: vendor="X.Org Foundation"
[    58.645]     compiled for 1.15.1, module version = 1.0.0
[    58.645]     ABI class: X.Org Server Extension, version 8.0
[    58.645] (==) AIGLX enabled
[    58.645] Loading extension GLX
[    58.645] (II) LoadModule: "i2c"
[    58.645] (II) Module "i2c" already built-in
[    58.645] (II) LoadModule: "ddc"
[    58.645] (II) Module "ddc" already built-in
[    58.645] (II) LoadModule: "int10"
[    58.646] (II) Loading /usr/lib/xorg/modules/libint10.so
[    58.646] (II) Module int10: vendor="X.Org Foundation"
[    58.646]     compiled for 1.15.1, module version = 1.0.0
[    58.646]     ABI class: X.Org Video Driver, version 15.0
[    58.646] (II) LoadModule: "vbe"
[    58.646] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    58.646] (II) Module vbe: vendor="X.Org Foundation"
[    58.646]     compiled for 1.15.1, module version = 1.1.0
[    58.646]     ABI class: X.Org Video Driver, version 15.0
[    58.646] (II) LoadModule: "record"
[    58.646] (II) Module "record" already built-in
[    58.646] (II) LoadModule: "vesa"
[    58.646] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    58.647] (II) Module vesa: vendor="X.Org Foundation"
[    58.647]     compiled for 1.15.0, module version = 2.3.3
[    58.647]     Module class: X.Org Video Driver
[    58.647]     ABI class: X.Org Video Driver, version 15.0
[    58.647] (II) VESA: driver for VESA chipsets: vesa
[    58.647] (++) using VT number 7

[    58.647] (II) Loading sub module "vbe"
[    58.647] (II) LoadModule: "vbe"
[    58.647] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    58.647] (II) Module vbe: vendor="X.Org Foundation"
[    58.647]     compiled for 1.15.1, module version = 1.1.0
[    58.647]     ABI class: X.Org Video Driver, version 15.0
[    58.647] (II) Loading sub module "int10"
[    58.647] (II) LoadModule: "int10"
[    58.647] (II) Loading /usr/lib/xorg/modules/libint10.so
[    58.648] (II) Module int10: vendor="X.Org Foundation"
[    58.648]     compiled for 1.15.1, module version = 1.0.0
[    58.648]     ABI class: X.Org Video Driver, version 15.0
[    58.648] (II) VESA(0): initializing int10
[    58.653] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    58.654] (II) VESA(0): VESA BIOS detected
[    58.654] (II) VESA(0): VESA VBE Version 3.0
[    58.654] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    58.654] (II) VESA(0): VESA VBE OEM: SiS
[    58.654] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    58.654] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    58.654] (II) VESA(0): VESA VBE OEM Product: 6330
[    58.654] (II) VESA(0): VESA VBE OEM Product Rev: 3.72.15a
[    58.665] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    58.665] (==) VESA(0): RGB weight 888
[    58.666] (==) VESA(0): Default visual is TrueColor
[    58.666] (**) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    58.666] (II) Loading sub module "ddc"
[    58.666] (II) LoadModule: "ddc"
[    58.666] (II) Module "ddc" already built-in
[    58.765] (II) VESA(0): VESA VBE DDC supported
[    58.765] (II) VESA(0): VESA VBE DDC Level none
[    58.765] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    58.798] (II) VESA(0): VESA VBE DDC read failed
[    58.798] (II) VESA(0): Searching for matching VESA mode(s):
[    58.798] Mode: 11c (1280x768)
[    58.798]     ModeAttributes: 0x9f
[    58.798]     WinAAttributes: 0x7
[    58.798]     WinBAttributes: 0x0
[    58.798]     WinGranularity: 64
[    58.798]     WinSize: 64
[    58.798]     WinASegment: 0xa000
[    58.798]     WinBSegment: 0xa000
[    58.798]     WinFuncPtr: 0xc000862b
[    58.798]     BytesPerScanline: 1280
[    58.798]     XResolution: 1280
[    58.798]     YResolution: 768
[    58.798]     XCharSize: 8
[    58.798]     YCharSize: 16
[    58.799]     NumberOfPlanes: 1
[    58.799]     BitsPerPixel: 8
[    58.799]     NumberOfBanks: 1
[    58.799]     MemoryModel: 4
[    58.799]     BankSize: 0
[    58.799]     NumberOfImages: 7
[    58.799]     RedMaskSize: 0
[    58.799]     RedFieldPosition: 0
[    58.799]     GreenMaskSize: 0
[    58.799]     GreenFieldPosition: 0
[    58.799]     BlueMaskSize: 0
[    58.799]     BlueFieldPosition: 0
[    58.799]     RsvdMaskSize: 0
[    58.799]     RsvdFieldPosition: 0
[    58.799]     DirectColorModeInfo: 0
[    58.799]     PhysBasePtr: 0xc0000000
[    58.799]     LinBytesPerScanLine: 1280
[    58.799]     BnkNumberOfImagePages: 7
[    58.799]     LinNumberOfImagePages: 7
[    58.799]     LinRedMaskSize: 0
[    58.799]     LinRedFieldPosition: 0
[    58.799]     LinGreenMaskSize: 0
[    58.799]     LinGreenFieldPosition: 0
[    58.799]     LinBlueMaskSize: 0
[    58.799]     LinBlueFieldPosition: 0
[    58.799]     LinRsvdMaskSize: 0
[    58.799]     LinRsvdFieldPosition: 0
[    58.799]     MaxPixelClock: 0
[    58.799] Mode: 11d (1280x768)
[    58.799]     ModeAttributes: 0x9b
[    58.799]     WinAAttributes: 0x7
[    58.799]     WinBAttributes: 0x0
[    58.799]     WinGranularity: 64
[    58.799]     WinSize: 64
[    58.799]     WinASegment: 0xa000
[    58.799]     WinBSegment: 0xa000
[    58.799]     WinFuncPtr: 0xc000862b
[    58.799]     BytesPerScanline: 2560
[    58.799]     XResolution: 1280
[    58.799]     YResolution: 768
[    58.799]     XCharSize: 8
[    58.799]     YCharSize: 16
[    58.799]     NumberOfPlanes: 1
[    58.799]     BitsPerPixel: 16
[    58.799]     NumberOfBanks: 1
[    58.799]     MemoryModel: 6
[    58.799]     BankSize: 0
[    58.799]     NumberOfImages: 3
[    58.799]     RedMaskSize: 5
[    58.799]     RedFieldPosition: 11
[    58.799]     GreenMaskSize: 6
[    58.799]     GreenFieldPosition: 5
[    58.799]     BlueMaskSize: 5
[    58.799]     BlueFieldPosition: 0
[    58.799]     RsvdMaskSize: 0
[    58.799]     RsvdFieldPosition: 0
[    58.799]     DirectColorModeInfo: 0
[    58.799]     PhysBasePtr: 0xc0000000
[    58.799]     LinBytesPerScanLine: 2560
[    58.799]     BnkNumberOfImagePages: 3
[    58.799]     LinNumberOfImagePages: 3
[    58.800]     LinRedMaskSize: 5
[    58.800]     LinRedFieldPosition: 11
[    58.800]     LinGreenMaskSize: 6
[    58.800]     LinGreenFieldPosition: 5
[    58.800]     LinBlueMaskSize: 5
[    58.800]     LinBlueFieldPosition: 0
[    58.800]     LinRsvdMaskSize: 0
[    58.800]     LinRsvdFieldPosition: 0
[    58.800]     MaxPixelClock: 0
[    58.800] *Mode: 11e (1280x768)
[    58.800]     ModeAttributes: 0x9b
[    58.800]     WinAAttributes: 0x7
[    58.800]     WinBAttributes: 0x0
[    58.800]     WinGranularity: 64
[    58.800]     WinSize: 64
[    58.800]     WinASegment: 0xa000
[    58.800]     WinBSegment: 0xa000
[    58.800]     WinFuncPtr: 0xc000862b
[    58.800]     BytesPerScanline: 5120
[    58.800]     XResolution: 1280
[    58.800]     YResolution: 768
[    58.800]     XCharSize: 8
[    58.800]     YCharSize: 16
[    58.800]     NumberOfPlanes: 1
[    58.800]     BitsPerPixel: 32
[    58.800]     NumberOfBanks: 1
[    58.800]     MemoryModel: 6
[    58.800]     BankSize: 0
[    58.800]     NumberOfImages: 1
[    58.800]     RedMaskSize: 8
[    58.800]     RedFieldPosition: 16
[    58.800]     GreenMaskSize: 8
[    58.800]     GreenFieldPosition: 8
[    58.800]     BlueMaskSize: 8
[    58.800]     BlueFieldPosition: 0
[    58.800]     RsvdMaskSize: 8
[    58.800]     RsvdFieldPosition: 24
[    58.800]     DirectColorModeInfo: 0
[    58.800]     PhysBasePtr: 0xc0000000
[    58.800]     LinBytesPerScanLine: 5120
[    58.800]     BnkNumberOfImagePages: 1
[    58.800]     LinNumberOfImagePages: 1
[    58.800]     LinRedMaskSize: 8
[    58.800]     LinRedFieldPosition: 16
[    58.800]     LinGreenMaskSize: 8
[    58.800]     LinGreenFieldPosition: 8
[    58.800]     LinBlueMaskSize: 8
[    58.800]     LinBlueFieldPosition: 0
[    58.800]     LinRsvdMaskSize: 8
[    58.800]     LinRsvdFieldPosition: 24
[    58.800]     MaxPixelClock: 0
[    58.801] Mode: 101 (640x480)
[    58.801]     ModeAttributes: 0x9f
[    58.801]     WinAAttributes: 0x7
[    58.801]     WinBAttributes: 0x0
[    58.801]     WinGranularity: 64
[    58.801]     WinSize: 64
[    58.801]     WinASegment: 0xa000
[    58.801]     WinBSegment: 0xa000
[    58.801]     WinFuncPtr: 0xc000862b
[    58.801]     BytesPerScanline: 640
[    58.801]     XResolution: 640
[    58.801]     YResolution: 480
[    58.801]     XCharSize: 8
[    58.801]     YCharSize: 16
[    58.801]     NumberOfPlanes: 1
[    58.801]     BitsPerPixel: 8
[    58.801]     NumberOfBanks: 1
[    58.801]     MemoryModel: 4
[    58.801]     BankSize: 0
[    58.801]     NumberOfImages: 24
[    58.801]     RedMaskSize: 0
[    58.801]     RedFieldPosition: 0
[    58.801]     GreenMaskSize: 0
[    58.801]     GreenFieldPosition: 0
[    58.801]     BlueMaskSize: 0
[    58.801]     BlueFieldPosition: 0
[    58.801]     RsvdMaskSize: 0
[    58.801]     RsvdFieldPosition: 0
[    58.801]     DirectColorModeInfo: 0
[    58.801]     PhysBasePtr: 0xc0000000
[    58.801]     LinBytesPerScanLine: 640
[    58.801]     BnkNumberOfImagePages: 24
[    58.801]     LinNumberOfImagePages: 24
[    58.801]     LinRedMaskSize: 0
[    58.801]     LinRedFieldPosition: 0
[    58.801]     LinGreenMaskSize: 0
[    58.801]     LinGreenFieldPosition: 0
[    58.801]     LinBlueMaskSize: 0
[    58.801]     LinBlueFieldPosition: 0
[    58.801]     LinRsvdMaskSize: 0
[    58.801]     LinRsvdFieldPosition: 0
[    58.801]     MaxPixelClock: 0
[    58.801] Mode: 100 (640x400)
[    58.802]     ModeAttributes: 0x9f
[    58.802]     WinAAttributes: 0x7
[    58.802]     WinBAttributes: 0x0
[    58.802]     WinGranularity: 64
[    58.802]     WinSize: 64
[    58.802]     WinASegment: 0xa000
[    58.802]     WinBSegment: 0xa000
[    58.802]     WinFuncPtr: 0xc000862b
[    58.802]     BytesPerScanline: 640
[    58.802]     XResolution: 640
[    58.802]     YResolution: 400
[    58.802]     XCharSize: 8
[    58.802]     YCharSize: 16
[    58.802]     NumberOfPlanes: 1
[    58.802]     BitsPerPixel: 8
[    58.802]     NumberOfBanks: 1
[    58.802]     MemoryModel: 4
[    58.802]     BankSize: 0
[    58.802]     NumberOfImages: 31
[    58.802]     RedMaskSize: 0
[    58.802]     RedFieldPosition: 0
[    58.802]     GreenMaskSize: 0
[    58.802]     GreenFieldPosition: 0
[    58.802]     BlueMaskSize: 0
[    58.802]     BlueFieldPosition: 0
[    58.802]     RsvdMaskSize: 0
[    58.802]     RsvdFieldPosition: 0
[    58.802]     DirectColorModeInfo: 0
[    58.802]     PhysBasePtr: 0xc0000000
[    58.802]     LinBytesPerScanLine: 640
[    58.802]     BnkNumberOfImagePages: 31
[    58.802]     LinNumberOfImagePages: 31
[    58.802]     LinRedMaskSize: 0
[    58.802]     LinRedFieldPosition: 0
[    58.802]     LinGreenMaskSize: 0
[    58.802]     LinGreenFieldPosition: 0
[    58.802]     LinBlueMaskSize: 0
[    58.802]     LinBlueFieldPosition: 0
[    58.802]     LinRsvdMaskSize: 0
[    58.802]     LinRsvdFieldPosition: 0
[    58.802]     MaxPixelClock: 0
[    58.802] Mode: 103 (800x600)
[    58.802]     ModeAttributes: 0x9f
[    58.802]     WinAAttributes: 0x7
[    58.802]     WinBAttributes: 0x0
[    58.802]     WinGranularity: 64
[    58.802]     WinSize: 64
[    58.802]     WinASegment: 0xa000
[    58.802]     WinBSegment: 0xa000
[    58.802]     WinFuncPtr: 0xc000862b
[    58.802]     BytesPerScanline: 800
[    58.802]     XResolution: 800
[    58.802]     YResolution: 600
[    58.802]     XCharSize: 8
[    58.802]     YCharSize: 16
[    58.802]     NumberOfPlanes: 1
[    58.802]     BitsPerPixel: 8
[    58.802]     NumberOfBanks: 1
[    58.803]     MemoryModel: 4
[    58.803]     BankSize: 0
[    58.803]     NumberOfImages: 15
[    58.803]     RedMaskSize: 0
[    58.803]     RedFieldPosition: 0
[    58.803]     GreenMaskSize: 0
[    58.803]     GreenFieldPosition: 0
[    58.803]     BlueMaskSize: 0
[    58.803]     BlueFieldPosition: 0
[    58.803]     RsvdMaskSize: 0
[    58.803]     RsvdFieldPosition: 0
[    58.803]     DirectColorModeInfo: 0
[    58.803]     PhysBasePtr: 0xc0000000
[    58.803]     LinBytesPerScanLine: 800
[    58.803]     BnkNumberOfImagePages: 15
[    58.803]     LinNumberOfImagePages: 15
[    58.803]     LinRedMaskSize: 0
[    58.803]     LinRedFieldPosition: 0
[    58.803]     LinGreenMaskSize: 0
[    58.803]     LinGreenFieldPosition: 0
[    58.803]     LinBlueMaskSize: 0
[    58.803]     LinBlueFieldPosition: 0
[    58.803]     LinRsvdMaskSize: 0
[    58.803]     LinRsvdFieldPosition: 0
[    58.803]     MaxPixelClock: 0
[    58.803] Mode: 104 (1024x768)
[    58.803]     ModeAttributes: 0x1f
[    58.803]     WinAAttributes: 0x7
[    58.803]     WinBAttributes: 0x0
[    58.803]     WinGranularity: 64
[    58.803]     WinSize: 64
[    58.803]     WinASegment: 0xa000
[    58.803]     WinBSegment: 0xa000
[    58.803]     WinFuncPtr: 0xc000862b
[    58.803]     BytesPerScanline: 128
[    58.803]     XResolution: 1024
[    58.803]     YResolution: 768
[    58.803]     XCharSize: 8
[    58.803]     YCharSize: 16
[    58.803]     NumberOfPlanes: 4
[    58.803]     BitsPerPixel: 4
[    58.803]     NumberOfBanks: 1
[    58.803]     MemoryModel: 3
[    58.803]     BankSize: 0
[    58.803]     NumberOfImages: 15
[    58.803]     RedMaskSize: 0
[    58.803]     RedFieldPosition: 0
[    58.803]     GreenMaskSize: 0
[    58.803]     GreenFieldPosition: 0
[    58.803]     BlueMaskSize: 0
[    58.803]     BlueFieldPosition: 0
[    58.803]     RsvdMaskSize: 0
[    58.803]     RsvdFieldPosition: 0
[    58.803]     DirectColorModeInfo: 0
[    58.803]     PhysBasePtr: 0xc0000000
[    58.803]     LinBytesPerScanLine: 128
[    58.803]     BnkNumberOfImagePages: 15
[    58.804]     LinNumberOfImagePages: 15
[    58.804]     LinRedMaskSize: 0
[    58.804]     LinRedFieldPosition: 0
[    58.804]     LinGreenMaskSize: 0
[    58.804]     LinGreenFieldPosition: 0
[    58.804]     LinBlueMaskSize: 0
[    58.804]     LinBlueFieldPosition: 0
[    58.804]     LinRsvdMaskSize: 0
[    58.804]     LinRsvdFieldPosition: 0
[    58.804]     MaxPixelClock: 0
[    58.804] Mode: 105 (1024x768)
[    58.804]     ModeAttributes: 0x9f
[    58.804]     WinAAttributes: 0x7
[    58.804]     WinBAttributes: 0x0
[    58.804]     WinGranularity: 64
[    58.804]     WinSize: 64
[    58.804]     WinASegment: 0xa000
[    58.804]     WinBSegment: 0xa000
[    58.804]     WinFuncPtr: 0xc000862b
[    58.804]     BytesPerScanline: 1024
[    58.804]     XResolution: 1024
[    58.804]     YResolution: 768
[    58.804]     XCharSize: 8
[    58.804]     YCharSize: 16
[    58.804]     NumberOfPlanes: 1
[    58.804]     BitsPerPixel: 8
[    58.804]     NumberOfBanks: 1
[    58.804]     MemoryModel: 4
[    58.804]     BankSize: 0
[    58.804]     NumberOfImages: 9
[    58.804]     RedMaskSize: 0
[    58.804]     RedFieldPosition: 0
[    58.804]     GreenMaskSize: 0
[    58.804]     GreenFieldPosition: 0
[    58.804]     BlueMaskSize: 0
[    58.804]     BlueFieldPosition: 0
[    58.804]     RsvdMaskSize: 0
[    58.804]     RsvdFieldPosition: 0
[    58.804]     DirectColorModeInfo: 0
[    58.804]     PhysBasePtr: 0xc0000000
[    58.804]     LinBytesPerScanLine: 1024
[    58.804]     BnkNumberOfImagePages: 9
[    58.804]     LinNumberOfImagePages: 9
[    58.804]     LinRedMaskSize: 0
[    58.804]     LinRedFieldPosition: 0
[    58.804]     LinGreenMaskSize: 0
[    58.804]     LinGreenFieldPosition: 0
[    58.804]     LinBlueMaskSize: 0
[    58.804]     LinBlueFieldPosition: 0
[    58.804]     LinRsvdMaskSize: 0
[    58.804]     LinRsvdFieldPosition: 0
[    58.804]     MaxPixelClock: 0
[    58.805] Mode: 10d (320x200)
[    58.805]     ModeAttributes: 0x9b
[    58.805]     WinAAttributes: 0x7
[    58.805]     WinBAttributes: 0x0
[    58.805]     WinGranularity: 64
[    58.805]     WinSize: 64
[    58.805]     WinASegment: 0xa000
[    58.805]     WinBSegment: 0xa000
[    58.805]     WinFuncPtr: 0xc000862b
[    58.805]     BytesPerScanline: 640
[    58.805]     XResolution: 320
[    58.805]     YResolution: 200
[    58.805]     XCharSize: 8
[    58.805]     YCharSize: 8
[    58.805]     NumberOfPlanes: 1
[    58.805]     BitsPerPixel: 15
[    58.805]     NumberOfBanks: 1
[    58.805]     MemoryModel: 6
[    58.805]     BankSize: 0
[    58.805]     NumberOfImages: 63
[    58.805]     RedMaskSize: 5
[    58.805]     RedFieldPosition: 10
[    58.805]     GreenMaskSize: 5
[    58.805]     GreenFieldPosition: 5
[    58.805]     BlueMaskSize: 5
[    58.805]     BlueFieldPosition: 0
[    58.805]     RsvdMaskSize: 0
[    58.805]     RsvdFieldPosition: 0
[    58.805]     DirectColorModeInfo: 0
[    58.805]     PhysBasePtr: 0xc0000000
[    58.805]     LinBytesPerScanLine: 640
[    58.805]     BnkNumberOfImagePages: 63
[    58.805]     LinNumberOfImagePages: 63
[    58.805]     LinRedMaskSize: 5
[    58.805]     LinRedFieldPosition: 10
[    58.805]     LinGreenMaskSize: 5
[    58.805]     LinGreenFieldPosition: 5
[    58.805]     LinBlueMaskSize: 5
[    58.805]     LinBlueFieldPosition: 0
[    58.805]     LinRsvdMaskSize: 0
[    58.805]     LinRsvdFieldPosition: 0
[    58.805]     MaxPixelClock: 0
[    58.806] Mode: 10e (320x200)
[    58.806]     ModeAttributes: 0x9b
[    58.806]     WinAAttributes: 0x7
[    58.806]     WinBAttributes: 0x0
[    58.806]     WinGranularity: 64
[    58.806]     WinSize: 64
[    58.806]     WinASegment: 0xa000
[    58.806]     WinBSegment: 0xa000
[    58.806]     WinFuncPtr: 0xc000862b
[    58.806]     BytesPerScanline: 640
[    58.806]     XResolution: 320
[    58.806]     YResolution: 200
[    58.806]     XCharSize: 8
[    58.806]     YCharSize: 8
[    58.806]     NumberOfPlanes: 1
[    58.806]     BitsPerPixel: 16
[    58.806]     NumberOfBanks: 1
[    58.806]     MemoryModel: 6
[    58.806]     BankSize: 0
[    58.806]     NumberOfImages: 63
[    58.806]     RedMaskSize: 5
[    58.806]     RedFieldPosition: 11
[    58.806]     GreenMaskSize: 6
[    58.806]     GreenFieldPosition: 5
[    58.806]     BlueMaskSize: 5
[    58.806]     BlueFieldPosition: 0
[    58.806]     RsvdMaskSize: 0
[    58.806]     RsvdFieldPosition: 0
[    58.806]     DirectColorModeInfo: 0
[    58.806]     PhysBasePtr: 0xc0000000
[    58.806]     LinBytesPerScanLine: 640
[    58.806]     BnkNumberOfImagePages: 63
[    58.806]     LinNumberOfImagePages: 63
[    58.806]     LinRedMaskSize: 5
[    58.806]     LinRedFieldPosition: 11
[    58.806]     LinGreenMaskSize: 6
[    58.806]     LinGreenFieldPosition: 5
[    58.806]     LinBlueMaskSize: 5
[    58.806]     LinBlueFieldPosition: 0
[    58.806]     LinRsvdMaskSize: 0
[    58.806]     LinRsvdFieldPosition: 0
[    58.806]     MaxPixelClock: 0
[    58.807] Mode: 110 (640x480)
[    58.807]     ModeAttributes: 0x9b
[    58.807]     WinAAttributes: 0x7
[    58.807]     WinBAttributes: 0x0
[    58.807]     WinGranularity: 64
[    58.807]     WinSize: 64
[    58.807]     WinASegment: 0xa000
[    58.807]     WinBSegment: 0xa000
[    58.807]     WinFuncPtr: 0xc000862b
[    58.807]     BytesPerScanline: 1280
[    58.807]     XResolution: 640
[    58.807]     YResolution: 480
[    58.807]     XCharSize: 8
[    58.807]     YCharSize: 16
[    58.807]     NumberOfPlanes: 1
[    58.807]     BitsPerPixel: 15
[    58.807]     NumberOfBanks: 1
[    58.807]     MemoryModel: 6
[    58.807]     BankSize: 0
[    58.807]     NumberOfImages: 11
[    58.807]     RedMaskSize: 5
[    58.807]     RedFieldPosition: 10
[    58.807]     GreenMaskSize: 5
[    58.807]     GreenFieldPosition: 5
[    58.807]     BlueMaskSize: 5
[    58.807]     BlueFieldPosition: 0
[    58.807]     RsvdMaskSize: 0
[    58.807]     RsvdFieldPosition: 0
[    58.807]     DirectColorModeInfo: 0
[    58.807]     PhysBasePtr: 0xc0000000
[    58.807]     LinBytesPerScanLine: 1280
[    58.807]     BnkNumberOfImagePages: 11
[    58.807]     LinNumberOfImagePages: 11
[    58.807]     LinRedMaskSize: 5
[    58.807]     LinRedFieldPosition: 10
[    58.807]     LinGreenMaskSize: 5
[    58.807]     LinGreenFieldPosition: 5
[    58.807]     LinBlueMaskSize: 5
[    58.807]     LinBlueFieldPosition: 0
[    58.807]     LinRsvdMaskSize: 0
[    58.807]     LinRsvdFieldPosition: 0
[    58.807]     MaxPixelClock: 0
[    58.807] Mode: 111 (640x480)
[    58.807]     ModeAttributes: 0x9b
[    58.807]     WinAAttributes: 0x7
[    58.807]     WinBAttributes: 0x0
[    58.807]     WinGranularity: 64
[    58.807]     WinSize: 64
[    58.807]     WinASegment: 0xa000
[    58.807]     WinBSegment: 0xa000
[    58.807]     WinFuncPtr: 0xc000862b
[    58.807]     BytesPerScanline: 1280
[    58.807]     XResolution: 640
[    58.808]     YResolution: 480
[    58.808]     XCharSize: 8
[    58.808]     YCharSize: 16
[    58.808]     NumberOfPlanes: 1
[    58.808]     BitsPerPixel: 16
[    58.808]     NumberOfBanks: 1
[    58.808]     MemoryModel: 6
[    58.808]     BankSize: 0
[    58.808]     NumberOfImages: 11
[    58.808]     RedMaskSize: 5
[    58.808]     RedFieldPosition: 11
[    58.808]     GreenMaskSize: 6
[    58.808]     GreenFieldPosition: 5
[    58.808]     BlueMaskSize: 5
[    58.808]     BlueFieldPosition: 0
[    58.808]     RsvdMaskSize: 0
[    58.808]     RsvdFieldPosition: 0
[    58.808]     DirectColorModeInfo: 0
[    58.808]     PhysBasePtr: 0xc0000000
[    58.808]     LinBytesPerScanLine: 1280
[    58.808]     BnkNumberOfImagePages: 11
[    58.808]     LinNumberOfImagePages: 11
[    58.808]     LinRedMaskSize: 5
[    58.808]     LinRedFieldPosition: 11
[    58.808]     LinGreenMaskSize: 6
[    58.808]     LinGreenFieldPosition: 5
[    58.808]     LinBlueMaskSize: 5
[    58.808]     LinBlueFieldPosition: 0
[    58.808]     LinRsvdMaskSize: 0
[    58.808]     LinRsvdFieldPosition: 0
[    58.808]     MaxPixelClock: 0
[    58.808] Mode: 113 (800x600)
[    58.808]     ModeAttributes: 0x9b
[    58.808]     WinAAttributes: 0x7
[    58.808]     WinBAttributes: 0x0
[    58.808]     WinGranularity: 64
[    58.808]     WinSize: 64
[    58.808]     WinASegment: 0xa000
[    58.808]     WinBSegment: 0xa000
[    58.808]     WinFuncPtr: 0xc000862b
[    58.808]     BytesPerScanline: 1600
[    58.808]     XResolution: 800
[    58.808]     YResolution: 600
[    58.808]     XCharSize: 8
[    58.808]     YCharSize: 16
[    58.808]     NumberOfPlanes: 1
[    58.808]     BitsPerPixel: 15
[    58.808]     NumberOfBanks: 1
[    58.808]     MemoryModel: 6
[    58.808]     BankSize: 0
[    58.808]     NumberOfImages: 7
[    58.809]     RedMaskSize: 5
[    58.809]     RedFieldPosition: 10
[    58.809]     GreenMaskSize: 5
[    58.809]     GreenFieldPosition: 5
[    58.809]     BlueMaskSize: 5
[    58.809]     BlueFieldPosition: 0
[    58.809]     RsvdMaskSize: 0
[    58.809]     RsvdFieldPosition: 0
[    58.809]     DirectColorModeInfo: 0
[    58.809]     PhysBasePtr: 0xc0000000
[    58.809]     LinBytesPerScanLine: 1600
[    58.809]     BnkNumberOfImagePages: 7
[    58.809]     LinNumberOfImagePages: 7
[    58.809]     LinRedMaskSize: 5
[    58.809]     LinRedFieldPosition: 10
[    58.809]     LinGreenMaskSize: 5
[    58.809]     LinGreenFieldPosition: 5
[    58.809]     LinBlueMaskSize: 5
[    58.809]     LinBlueFieldPosition: 0
[    58.809]     LinRsvdMaskSize: 0
[    58.809]     LinRsvdFieldPosition: 0
[    58.809]     MaxPixelClock: 0
[    58.809] Mode: 114 (800x600)
[    58.809]     ModeAttributes: 0x9b
[    58.809]     WinAAttributes: 0x7
[    58.809]     WinBAttributes: 0x0
[    58.809]     WinGranularity: 64
[    58.809]     WinSize: 64
[    58.809]     WinASegment: 0xa000
[    58.809]     WinBSegment: 0xa000
[    58.809]     WinFuncPtr: 0xc000862b
[    58.809]     BytesPerScanline: 1600
[    58.809]     XResolution: 800
[    58.809]     YResolution: 600
[    58.809]     XCharSize: 8
[    58.809]     YCharSize: 16
[    58.809]     NumberOfPlanes: 1
[    58.809]     BitsPerPixel: 16
[    58.809]     NumberOfBanks: 1
[    58.809]     MemoryModel: 6
[    58.809]     BankSize: 0
[    58.809]     NumberOfImages: 7
[    58.809]     RedMaskSize: 5
[    58.809]     RedFieldPosition: 11
[    58.809]     GreenMaskSize: 6
[    58.809]     GreenFieldPosition: 5
[    58.809]     BlueMaskSize: 5
[    58.809]     BlueFieldPosition: 0
[    58.809]     RsvdMaskSize: 0
[    58.809]     RsvdFieldPosition: 0
[    58.809]     DirectColorModeInfo: 0
[    58.809]     PhysBasePtr: 0xc0000000
[    58.809]     LinBytesPerScanLine: 1600
[    58.810]     BnkNumberOfImagePages: 7
[    58.810]     LinNumberOfImagePages: 7
[    58.810]     LinRedMaskSize: 5
[    58.810]     LinRedFieldPosition: 11
[    58.810]     LinGreenMaskSize: 6
[    58.810]     LinGreenFieldPosition: 5
[    58.810]     LinBlueMaskSize: 5
[    58.810]     LinBlueFieldPosition: 0
[    58.810]     LinRsvdMaskSize: 0
[    58.810]     LinRsvdFieldPosition: 0
[    58.810]     MaxPixelClock: 0
[    58.810] Mode: 116 (1024x768)
[    58.810]     ModeAttributes: 0x9b
[    58.810]     WinAAttributes: 0x7
[    58.810]     WinBAttributes: 0x0
[    58.810]     WinGranularity: 64
[    58.810]     WinSize: 64
[    58.810]     WinASegment: 0xa000
[    58.810]     WinBSegment: 0xa000
[    58.810]     WinFuncPtr: 0xc000862b
[    58.810]     BytesPerScanline: 2048
[    58.810]     XResolution: 1024
[    58.810]     YResolution: 768
[    58.810]     XCharSize: 8
[    58.810]     YCharSize: 16
[    58.810]     NumberOfPlanes: 1
[    58.810]     BitsPerPixel: 15
[    58.810]     NumberOfBanks: 1
[    58.810]     MemoryModel: 6
[    58.810]     BankSize: 0
[    58.810]     NumberOfImages: 4
[    58.810]     RedMaskSize: 5
[    58.810]     RedFieldPosition: 10
[    58.810]     GreenMaskSize: 5
[    58.810]     GreenFieldPosition: 5
[    58.810]     BlueMaskSize: 5
[    58.810]     BlueFieldPosition: 0
[    58.810]     RsvdMaskSize: 0
[    58.810]     RsvdFieldPosition: 0
[    58.810]     DirectColorModeInfo: 0
[    58.810]     PhysBasePtr: 0xc0000000
[    58.810]     LinBytesPerScanLine: 2048
[    58.810]     BnkNumberOfImagePages: 4
[    58.810]     LinNumberOfImagePages: 4
[    58.810]     LinRedMaskSize: 5
[    58.810]     LinRedFieldPosition: 10
[    58.810]     LinGreenMaskSize: 5
[    58.810]     LinGreenFieldPosition: 5
[    58.810]     LinBlueMaskSize: 5
[    58.810]     LinBlueFieldPosition: 0
[    58.810]     LinRsvdMaskSize: 0
[    58.810]     LinRsvdFieldPosition: 0
[    58.810]     MaxPixelClock: 0
[    58.811] Mode: 117 (1024x768)
[    58.811]     ModeAttributes: 0x9b
[    58.811]     WinAAttributes: 0x7
[    58.811]     WinBAttributes: 0x0
[    58.811]     WinGranularity: 64
[    58.811]     WinSize: 64
[    58.811]     WinASegment: 0xa000
[    58.811]     WinBSegment: 0xa000
[    58.811]     WinFuncPtr: 0xc000862b
[    58.811]     BytesPerScanline: 2048
[    58.811]     XResolution: 1024
[    58.811]     YResolution: 768
[    58.811]     XCharSize: 8
[    58.811]     YCharSize: 16
[    58.811]     NumberOfPlanes: 1
[    58.811]     BitsPerPixel: 16
[    58.811]     NumberOfBanks: 1
[    58.811]     MemoryModel: 6
[    58.811]     BankSize: 0
[    58.811]     NumberOfImages: 4
[    58.811]     RedMaskSize: 5
[    58.811]     RedFieldPosition: 11
[    58.811]     GreenMaskSize: 6
[    58.811]     GreenFieldPosition: 5
[    58.811]     BlueMaskSize: 5
[    58.811]     BlueFieldPosition: 0
[    58.811]     RsvdMaskSize: 0
[    58.811]     RsvdFieldPosition: 0
[    58.811]     DirectColorModeInfo: 0
[    58.811]     PhysBasePtr: 0xc0000000
[    58.811]     LinBytesPerScanLine: 2048
[    58.811]     BnkNumberOfImagePages: 4
[    58.811]     LinNumberOfImagePages: 4
[    58.811]     LinRedMaskSize: 5
[    58.811]     LinRedFieldPosition: 11
[    58.811]     LinGreenMaskSize: 6
[    58.811]     LinGreenFieldPosition: 5
[    58.811]     LinBlueMaskSize: 5
[    58.811]     LinBlueFieldPosition: 0
[    58.811]     LinRsvdMaskSize: 0
[    58.811]     LinRsvdFieldPosition: 0
[    58.811]     MaxPixelClock: 0
[    58.812] Mode: 127 (320x240)
[    58.812]     ModeAttributes: 0x9f
[    58.812]     WinAAttributes: 0x7
[    58.812]     WinBAttributes: 0x0
[    58.812]     WinGranularity: 64
[    58.812]     WinSize: 64
[    58.812]     WinASegment: 0xa000
[    58.812]     WinBSegment: 0xa000
[    58.812]     WinFuncPtr: 0xc000862b
[    58.812]     BytesPerScanline: 320
[    58.812]     XResolution: 320
[    58.812]     YResolution: 240
[    58.812]     XCharSize: 8
[    58.812]     YCharSize: 8
[    58.812]     NumberOfPlanes: 1
[    58.812]     BitsPerPixel: 8
[    58.812]     NumberOfBanks: 1
[    58.812]     MemoryModel: 4
[    58.812]     BankSize: 0
[    58.812]     NumberOfImages: 63
[    58.812]     RedMaskSize: 0
[    58.812]     RedFieldPosition: 0
[    58.812]     GreenMaskSize: 0
[    58.812]     GreenFieldPosition: 0
[    58.812]     BlueMaskSize: 0
[    58.812]     BlueFieldPosition: 0
[    58.812]     RsvdMaskSize: 0
[    58.812]     RsvdFieldPosition: 0
[    58.812]     DirectColorModeInfo: 0
[    58.812]     PhysBasePtr: 0xc0000000
[    58.812]     LinBytesPerScanLine: 320
[    58.812]     BnkNumberOfImagePages: 63
[    58.812]     LinNumberOfImagePages: 63
[    58.812]     LinRedMaskSize: 0
[    58.812]     LinRedFieldPosition: 0
[    58.812]     LinGreenMaskSize: 0
[    58.812]     LinGreenFieldPosition: 0
[    58.812]     LinBlueMaskSize: 0
[    58.812]     LinBlueFieldPosition: 0
[    58.812]     LinRsvdMaskSize: 0
[    58.812]     LinRsvdFieldPosition: 0
[    58.813]     MaxPixelClock: 0
[    58.813] Mode: 128 (400x300)
[    58.813]     ModeAttributes: 0x9f
[    58.813]     WinAAttributes: 0x7
[    58.813]     WinBAttributes: 0x0
[    58.813]     WinGranularity: 64
[    58.813]     WinSize: 64
[    58.813]     WinASegment: 0xa000
[    58.813]     WinBSegment: 0xa000
[    58.813]     WinFuncPtr: 0xc000862b
[    58.813]     BytesPerScanline: 400
[    58.813]     XResolution: 400
[    58.813]     YResolution: 300
[    58.813]     XCharSize: 8
[    58.813]     YCharSize: 8
[    58.813]     NumberOfPlanes: 1
[    58.813]     BitsPerPixel: 8
[    58.813]     NumberOfBanks: 1
[    58.813]     MemoryModel: 4
[    58.813]     BankSize: 0
[    58.813]     NumberOfImages: 63
[    58.813]     RedMaskSize: 0
[    58.813]     RedFieldPosition: 0
[    58.813]     GreenMaskSize: 0
[    58.813]     GreenFieldPosition: 0
[    58.813]     BlueMaskSize: 0
[    58.813]     BlueFieldPosition: 0
[    58.813]     RsvdMaskSize: 0
[    58.813]     RsvdFieldPosition: 0
[    58.813]     DirectColorModeInfo: 0
[    58.813]     PhysBasePtr: 0xc0000000
[    58.813]     LinBytesPerScanLine: 400
[    58.813]     BnkNumberOfImagePages: 63
[    58.813]     LinNumberOfImagePages: 63
[    58.813]     LinRedMaskSize: 0
[    58.813]     LinRedFieldPosition: 0
[    58.813]     LinGreenMaskSize: 0
[    58.813]     LinGreenFieldPosition: 0
[    58.813]     LinBlueMaskSize: 0
[    58.813]     LinBlueFieldPosition: 0
[    58.813]     LinRsvdMaskSize: 0
[    58.813]     LinRsvdFieldPosition: 0
[    58.813]     MaxPixelClock: 0
[    58.814] Mode: 129 (512x384)
[    58.814]     ModeAttributes: 0x9f
[    58.814]     WinAAttributes: 0x7
[    58.814]     WinBAttributes: 0x0
[    58.814]     WinGranularity: 64
[    58.814]     WinSize: 64
[    58.814]     WinASegment: 0xa000
[    58.814]     WinBSegment: 0xa000
[    58.814]     WinFuncPtr: 0xc000862b
[    58.814]     BytesPerScanline: 512
[    58.814]     XResolution: 512
[    58.814]     YResolution: 384
[    58.814]     XCharSize: 8
[    58.814]     YCharSize: 8
[    58.814]     NumberOfPlanes: 1
[    58.814]     BitsPerPixel: 8
[    58.814]     NumberOfBanks: 1
[    58.814]     MemoryModel: 4
[    58.814]     BankSize: 0
[    58.814]     NumberOfImages: 41
[    58.814]     RedMaskSize: 0
[    58.814]     RedFieldPosition: 0
[    58.814]     GreenMaskSize: 0
[    58.814]     GreenFieldPosition: 0
[    58.814]     BlueMaskSize: 0
[    58.814]     BlueFieldPosition: 0
[    58.814]     RsvdMaskSize: 0
[    58.814]     RsvdFieldPosition: 0
[    58.814]     DirectColorModeInfo: 0
[    58.814]     PhysBasePtr: 0xc0000000
[    58.814]     LinBytesPerScanLine: 512
[    58.814]     BnkNumberOfImagePages: 41
[    58.814]     LinNumberOfImagePages: 41
[    58.814]     LinRedMaskSize: 0
[    58.814]     LinRedFieldPosition: 0
[    58.814]     LinGreenMaskSize: 0
[    58.814]     LinGreenFieldPosition: 0
[    58.814]     LinBlueMaskSize: 0
[    58.814]     LinBlueFieldPosition: 0
[    58.814]     LinRsvdMaskSize: 0
[    58.814]     LinRsvdFieldPosition: 0
[    58.814]     MaxPixelClock: 0
[    58.815] Mode: 12a (320x240)
[    58.815]     ModeAttributes: 0x9b
[    58.815]     WinAAttributes: 0x7
[    58.815]     WinBAttributes: 0x0
[    58.815]     WinGranularity: 64
[    58.815]     WinSize: 64
[    58.815]     WinASegment: 0xa000
[    58.815]     WinBSegment: 0xa000
[    58.815]     WinFuncPtr: 0xc000862b
[    58.815]     BytesPerScanline: 640
[    58.815]     XResolution: 320
[    58.815]     YResolution: 240
[    58.815]     XCharSize: 8
[    58.815]     YCharSize: 8
[    58.815]     NumberOfPlanes: 1
[    58.815]     BitsPerPixel: 16
[    58.815]     NumberOfBanks: 1
[    58.815]     MemoryModel: 6
[    58.815]     BankSize: 0
[    58.815]     NumberOfImages: 41
[    58.815]     RedMaskSize: 5
[    58.815]     RedFieldPosition: 11
[    58.815]     GreenMaskSize: 6
[    58.815]     GreenFieldPosition: 5
[    58.815]     BlueMaskSize: 5
[    58.815]     BlueFieldPosition: 0
[    58.815]     RsvdMaskSize: 0
[    58.815]     RsvdFieldPosition: 0
[    58.815]     DirectColorModeInfo: 0
[    58.815]     PhysBasePtr: 0xc0000000
[    58.815]     LinBytesPerScanLine: 640
[    58.815]     BnkNumberOfImagePages: 41
[    58.815]     LinNumberOfImagePages: 41
[    58.815]     LinRedMaskSize: 5
[    58.815]     LinRedFieldPosition: 11
[    58.815]     LinGreenMaskSize: 6
[    58.815]     LinGreenFieldPosition: 5
[    58.815]     LinBlueMaskSize: 5
[    58.815]     LinBlueFieldPosition: 0
[    58.815]     LinRsvdMaskSize: 0
[    58.815]     LinRsvdFieldPosition: 0
[    58.815]     MaxPixelClock: 0
[    58.816] Mode: 12b (400x300)
[    58.816]     ModeAttributes: 0x9b
[    58.816]     WinAAttributes: 0x7
[    58.816]     WinBAttributes: 0x0
[    58.816]     WinGranularity: 64
[    58.816]     WinSize: 64
[    58.816]     WinASegment: 0xa000
[    58.816]     WinBSegment: 0xa000
[    58.816]     WinFuncPtr: 0xc000862b
[    58.816]     BytesPerScanline: 800
[    58.816]     XResolution: 400
[    58.816]     YResolution: 300
[    58.816]     XCharSize: 8
[    58.816]     YCharSize: 8
[    58.816]     NumberOfPlanes: 1
[    58.816]     BitsPerPixel: 16
[    58.816]     NumberOfBanks: 1
[    58.816]     MemoryModel: 6
[    58.816]     BankSize: 0
[    58.816]     NumberOfImages: 31
[    58.816]     RedMaskSize: 5
[    58.816]     RedFieldPosition: 11
[    58.816]     GreenMaskSize: 6
[    58.816]     GreenFieldPosition: 5
[    58.816]     BlueMaskSize: 5
[    58.816]     BlueFieldPosition: 0
[    58.816]     RsvdMaskSize: 0
[    58.816]     RsvdFieldPosition: 0
[    58.816]     DirectColorModeInfo: 0
[    58.816]     PhysBasePtr: 0xc0000000
[    58.816]     LinBytesPerScanLine: 800
[    58.816]     BnkNumberOfImagePages: 31
[    58.816]     LinNumberOfImagePages: 31
[    58.816]     LinRedMaskSize: 5
[    58.816]     LinRedFieldPosition: 11
[    58.816]     LinGreenMaskSize: 6
[    58.816]     LinGreenFieldPosition: 5
[    58.816]     LinBlueMaskSize: 5
[    58.816]     LinBlueFieldPosition: 0
[    58.816]     LinRsvdMaskSize: 0
[    58.816]     LinRsvdFieldPosition: 0
[    58.816]     MaxPixelClock: 0
[    58.817] Mode: 12c (512x384)
[    58.817]     ModeAttributes: 0x9b
[    58.817]     WinAAttributes: 0x7
[    58.817]     WinBAttributes: 0x0
[    58.817]     WinGranularity: 64
[    58.817]     WinSize: 64
[    58.817]     WinASegment: 0xa000
[    58.817]     WinBSegment: 0xa000
[    58.817]     WinFuncPtr: 0xc000862b
[    58.817]     BytesPerScanline: 1024
[    58.817]     XResolution: 512
[    58.817]     YResolution: 384
[    58.817]     XCharSize: 8
[    58.817]     YCharSize: 8
[    58.817]     NumberOfPlanes: 1
[    58.817]     BitsPerPixel: 16
[    58.817]     NumberOfBanks: 1
[    58.817]     MemoryModel: 6
[    58.817]     BankSize: 0
[    58.817]     NumberOfImages: 20
[    58.817]     RedMaskSize: 5
[    58.817]     RedFieldPosition: 11
[    58.817]     GreenMaskSize: 6
[    58.817]     GreenFieldPosition: 5
[    58.817]     BlueMaskSize: 5
[    58.817]     BlueFieldPosition: 0
[    58.817]     RsvdMaskSize: 0
[    58.817]     RsvdFieldPosition: 0
[    58.817]     DirectColorModeInfo: 0
[    58.817]     PhysBasePtr: 0xc0000000
[    58.817]     LinBytesPerScanLine: 1024
[    58.817]     BnkNumberOfImagePages: 20
[    58.817]     LinNumberOfImagePages: 20
[    58.817]     LinRedMaskSize: 5
[    58.817]     LinRedFieldPosition: 11
[    58.817]     LinGreenMaskSize: 6
[    58.817]     LinGreenFieldPosition: 5
[    58.817]     LinBlueMaskSize: 5
[    58.817]     LinBlueFieldPosition: 0
[    58.817]     LinRsvdMaskSize: 0
[    58.817]     LinRsvdFieldPosition: 0
[    58.817]     MaxPixelClock: 0
[    58.818] Mode: 12d (320x200)
[    58.818]     ModeAttributes: 0x9f
[    58.818]     WinAAttributes: 0x7
[    58.818]     WinBAttributes: 0x0
[    58.818]     WinGranularity: 64
[    58.818]     WinSize: 64
[    58.818]     WinASegment: 0xa000
[    58.818]     WinBSegment: 0xa000
[    58.818]     WinFuncPtr: 0xc000862b
[    58.818]     BytesPerScanline: 320
[    58.818]     XResolution: 320
[    58.818]     YResolution: 200
[    58.818]     XCharSize: 8
[    58.818]     YCharSize: 8
[    58.818]     NumberOfPlanes: 1
[    58.818]     BitsPerPixel: 8
[    58.818]     NumberOfBanks: 1
[    58.818]     MemoryModel: 4
[    58.818]     BankSize: 0
[    58.818]     NumberOfImages: 127
[    58.818]     RedMaskSize: 0
[    58.818]     RedFieldPosition: 0
[    58.818]     GreenMaskSize: 0
[    58.818]     GreenFieldPosition: 0
[    58.818]     BlueMaskSize: 0
[    58.818]     BlueFieldPosition: 0
[    58.818]     RsvdMaskSize: 0
[    58.818]     RsvdFieldPosition: 0
[    58.818]     DirectColorModeInfo: 0
[    58.818]     PhysBasePtr: 0xc0000000
[    58.818]     LinBytesPerScanLine: 320
[    58.818]     BnkNumberOfImagePages: 127
[    58.818]     LinNumberOfImagePages: 127
[    58.818]     LinRedMaskSize: 0
[    58.818]     LinRedFieldPosition: 0
[    58.818]     LinGreenMaskSize: 0
[    58.818]     LinGreenFieldPosition: 0
[    58.818]     LinBlueMaskSize: 0
[    58.818]     LinBlueFieldPosition: 0
[    58.818]     LinRsvdMaskSize: 0
[    58.818]     LinRsvdFieldPosition: 0
[    58.818]     MaxPixelClock: 0
[    58.819] Mode: 131 (640x400)
[    58.819]     ModeAttributes: 0x9b
[    58.819]     WinAAttributes: 0x7
[    58.819]     WinBAttributes: 0x0
[    58.819]     WinGranularity: 64
[    58.819]     WinSize: 64
[    58.819]     WinASegment: 0xa000
[    58.819]     WinBSegment: 0xa000
[    58.819]     WinFuncPtr: 0xc000862b
[    58.819]     BytesPerScanline: 1280
[    58.819]     XResolution: 640
[    58.819]     YResolution: 400
[    58.819]     XCharSize: 8
[    58.819]     YCharSize: 16
[    58.819]     NumberOfPlanes: 1
[    58.819]     BitsPerPixel: 16
[    58.819]     NumberOfBanks: 1
[    58.819]     MemoryModel: 6
[    58.819]     BankSize: 0
[    58.819]     NumberOfImages: 15
[    58.819]     RedMaskSize: 5
[    58.819]     RedFieldPosition: 11
[    58.819]     GreenMaskSize: 6
[    58.819]     GreenFieldPosition: 5
[    58.819]     BlueMaskSize: 5
[    58.819]     BlueFieldPosition: 0
[    58.819]     RsvdMaskSize: 0
[    58.819]     RsvdFieldPosition: 0
[    58.819]     DirectColorModeInfo: 0
[    58.819]     PhysBasePtr: 0xc0000000
[    58.819]     LinBytesPerScanLine: 1280
[    58.819]     BnkNumberOfImagePages: 15
[    58.819]     LinNumberOfImagePages: 15
[    58.819]     LinRedMaskSize: 5
[    58.819]     LinRedFieldPosition: 11
[    58.819]     LinGreenMaskSize: 6
[    58.819]     LinGreenFieldPosition: 5
[    58.819]     LinBlueMaskSize: 5
[    58.819]     LinBlueFieldPosition: 0
[    58.819]     LinRsvdMaskSize: 0
[    58.819]     LinRsvdFieldPosition: 0
[    58.819]     MaxPixelClock: 0
[    58.819] *Mode: 112 (640x480)
[    58.819]     ModeAttributes: 0x9b
[    58.819]     WinAAttributes: 0x7
[    58.820]     WinBAttributes: 0x0
[    58.820]     WinGranularity: 64
[    58.820]     WinSize: 64
[    58.820]     WinASegment: 0xa000
[    58.820]     WinBSegment: 0xa000
[    58.820]     WinFuncPtr: 0xc000862b
[    58.820]     BytesPerScanline: 2560
[    58.820]     XResolution: 640
[    58.820]     YResolution: 480
[    58.820]     XCharSize: 8
[    58.820]     YCharSize: 16
[    58.820]     NumberOfPlanes: 1
[    58.820]     BitsPerPixel: 32
[    58.820]     NumberOfBanks: 1
[    58.820]     MemoryModel: 6
[    58.820]     BankSize: 0
[    58.820]     NumberOfImages: 5
[    58.820]     RedMaskSize: 8
[    58.820]     RedFieldPosition: 16
[    58.820]     GreenMaskSize: 8
[    58.820]     GreenFieldPosition: 8
[    58.820]     BlueMaskSize: 8
[    58.820]     BlueFieldPosition: 0
[    58.820]     RsvdMaskSize: 8
[    58.820]     RsvdFieldPosition: 24
[    58.820]     DirectColorModeInfo: 0
[    58.820]     PhysBasePtr: 0xc0000000
[    58.820]     LinBytesPerScanLine: 2560
[    58.820]     BnkNumberOfImagePages: 5
[    58.820]     LinNumberOfImagePages: 5
[    58.820]     LinRedMaskSize: 8
[    58.820]     LinRedFieldPosition: 16
[    58.820]     LinGreenMaskSize: 8
[    58.820]     LinGreenFieldPosition: 8
[    58.820]     LinBlueMaskSize: 8
[    58.820]     LinBlueFieldPosition: 0
[    58.820]     LinRsvdMaskSize: 8
[    58.820]     LinRsvdFieldPosition: 24
[    58.820]     MaxPixelClock: 0
[    58.820] *Mode: 115 (800x600)
[    58.820]     ModeAttributes: 0x9b
[    58.820]     WinAAttributes: 0x7
[    58.820]     WinBAttributes: 0x0
[    58.821]     WinGranularity: 64
[    58.821]     WinSize: 64
[    58.821]     WinASegment: 0xa000
[    58.821]     WinBSegment: 0xa000
[    58.821]     WinFuncPtr: 0xc000862b
[    58.821]     BytesPerScanline: 3200
[    58.821]     XResolution: 800
[    58.821]     YResolution: 600
[    58.821]     XCharSize: 8
[    58.821]     YCharSize: 16
[    58.821]     NumberOfPlanes: 1
[    58.821]     BitsPerPixel: 32
[    58.821]     NumberOfBanks: 1
[    58.821]     MemoryModel: 6
[    58.821]     BankSize: 0
[    58.821]     NumberOfImages: 3
[    58.821]     RedMaskSize: 8
[    58.821]     RedFieldPosition: 16
[    58.821]     GreenMaskSize: 8
[    58.821]     GreenFieldPosition: 8
[    58.821]     BlueMaskSize: 8
[    58.821]     BlueFieldPosition: 0
[    58.821]     RsvdMaskSize: 8
[    58.821]     RsvdFieldPosition: 24
[    58.821]     DirectColorModeInfo: 0
[    58.821]     PhysBasePtr: 0xc0000000
[    58.821]     LinBytesPerScanLine: 3200
[    58.821]     BnkNumberOfImagePages: 3
[    58.821]     LinNumberOfImagePages: 3
[    58.821]     LinRedMaskSize: 8
[    58.821]     LinRedFieldPosition: 16
[    58.821]     LinGreenMaskSize: 8
[    58.821]     LinGreenFieldPosition: 8
[    58.821]     LinBlueMaskSize: 8
[    58.821]     LinBlueFieldPosition: 0
[    58.821]     LinRsvdMaskSize: 8
[    58.821]     LinRsvdFieldPosition: 24
[    58.821]     MaxPixelClock: 0
[    58.821] *Mode: 118 (1024x768)
[    58.821]     ModeAttributes: 0x9b
[    58.821]     WinAAttributes: 0x7
[    58.821]     WinBAttributes: 0x0
[    58.821]     WinGranularity: 64
[    58.821]     WinSize: 64
[    58.821]     WinASegment: 0xa000
[    58.821]     WinBSegment: 0xa000
[    58.822]     WinFuncPtr: 0xc000862b
[    58.822]     BytesPerScanline: 4096
[    58.822]     XResolution: 1024
[    58.822]     YResolution: 768
[    58.822]     XCharSize: 8
[    58.822]     YCharSize: 16
[    58.822]     NumberOfPlanes: 1
[    58.822]     BitsPerPixel: 32
[    58.822]     NumberOfBanks: 1
[    58.822]     MemoryModel: 6
[    58.822]     BankSize: 0
[    58.822]     NumberOfImages: 1
[    58.822]     RedMaskSize: 8
[    58.822]     RedFieldPosition: 16
[    58.822]     GreenMaskSize: 8
[    58.822]     GreenFieldPosition: 8
[    58.822]     BlueMaskSize: 8
[    58.822]     BlueFieldPosition: 0
[    58.822]     RsvdMaskSize: 8
[    58.822]     RsvdFieldPosition: 24
[    58.822]     DirectColorModeInfo: 0
[    58.822]     PhysBasePtr: 0xc0000000
[    58.822]     LinBytesPerScanLine: 4096
[    58.822]     BnkNumberOfImagePages: 1
[    58.822]     LinNumberOfImagePages: 1
[    58.822]     LinRedMaskSize: 8
[    58.822]     LinRedFieldPosition: 16
[    58.822]     LinGreenMaskSize: 8
[    58.822]     LinGreenFieldPosition: 8
[    58.822]     LinBlueMaskSize: 8
[    58.822]     LinBlueFieldPosition: 0
[    58.822]     LinRsvdMaskSize: 8
[    58.822]     LinRsvdFieldPosition: 24
[    58.822]     MaxPixelClock: 0
[    58.822] Mode: 102 (800x600)
[    58.822]     ModeAttributes: 0x1f
[    58.822]     WinAAttributes: 0x7
[    58.822]     WinBAttributes: 0x0
[    58.822]     WinGranularity: 64
[    58.822]     WinSize: 64
[    58.822]     WinASegment: 0xa000
[    58.822]     WinBSegment: 0xa000
[    58.822]     WinFuncPtr: 0xc000862b
[    58.822]     BytesPerScanline: 100
[    58.822]     XResolution: 800
[    58.822]     YResolution: 600
[    58.823]     XCharSize: 8
[    58.823]     YCharSize: 16
[    58.823]     NumberOfPlanes: 4
[    58.823]     BitsPerPixel: 4
[    58.823]     NumberOfBanks: 1
[    58.823]     MemoryModel: 3
[    58.823]     BankSize: 0
[    58.823]     NumberOfImages: 31
[    58.823]     RedMaskSize: 0
[    58.823]     RedFieldPosition: 0
[    58.823]     GreenMaskSize: 0
[    58.823]     GreenFieldPosition: 0
[    58.823]     BlueMaskSize: 0
[    58.823]     BlueFieldPosition: 0
[    58.823]     RsvdMaskSize: 0
[    58.823]     RsvdFieldPosition: 0
[    58.823]     DirectColorModeInfo: 0
[    58.823]     PhysBasePtr: 0xc0000000
[    58.823]     LinBytesPerScanLine: 100
[    58.823]     BnkNumberOfImagePages: 31
[    58.823]     LinNumberOfImagePages: 31
[    58.823]     LinRedMaskSize: 0
[    58.823]     LinRedFieldPosition: 0
[    58.823]     LinGreenMaskSize: 0
[    58.823]     LinGreenFieldPosition: 0
[    58.823]     LinBlueMaskSize: 0
[    58.823]     LinBlueFieldPosition: 0
[    58.823]     LinRsvdMaskSize: 0
[    58.823]     LinRsvdFieldPosition: 0
[    58.823]     MaxPixelClock: 0
[    58.823] 
[    58.823] (II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[    58.823] (II) VESA(0): Configured Monitor: Using hsync range of 20.00-107.00 kHz
[    58.823] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-185.00 Hz
[    58.823] (II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "800x600@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "800x600@56" (no mode of this name)
[    58.823] (II) VESA(0): Not using built-in mode "1280x768" (no mode of this name)
[    58.823] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    58.823] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    58.823] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    58.823] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    58.823] (II) VESA(0): Configured Monitor: Using hsync range of 20.00-107.00 kHz
[    58.823] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-185.00 Hz
[    58.823] (II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "800x600@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    58.823] (II) VESA(0): Not using mode "800x600@56" (no mode of this name)
[    58.823] (**) VESA(0): Virtual size is 1280x768 (pitch 1280)
[    58.823] (**) VESA(0):  Built-in mode "1280x768"
[    58.823] (**) VESA(0):  Built-in mode "1024x768"
[    58.823] (**) VESA(0):  Built-in mode "800x600"
[    58.823] (**) VESA(0):  Built-in mode "640x480"
[    58.823] (==) VESA(0): DPI set to (96, 96)
[    58.823] (**) VESA(0): Option "ShadowFB"
[    58.823] (II) VESA(0): Attempting to use 60Hz refresh for mode "1280x768" (11e)
[    58.824] (II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (118)
[    58.824] (II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (115)
[    58.824] (II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (112)
[    58.824] (**) VESA(0): Using "Shadow Framebuffer"
[    58.824] (II) Loading sub module "shadow"
[    58.824] (II) LoadModule: "shadow"
[    58.824] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    58.824] (II) Module shadow: vendor="X.Org Foundation"
[    58.824]     compiled for 1.15.1, module version = 1.1.0
[    58.824]     ABI class: X.Org ANSI C Emulation, version 0.4
[    58.824] (II) Loading sub module "fb"
[    58.824] (II) LoadModule: "fb"
[    58.825] (II) Loading /usr/lib/xorg/modules/libfb.so
[    58.825] (II) Module fb: vendor="X.Org Foundation"
[    58.825]     compiled for 1.15.1, module version = 1.0.0
[    58.825]     ABI class: X.Org ANSI C Emulation, version 0.4
[    58.825] (==) Depth 24 pixmap format is 32 bpp
[    58.825] (II) Loading sub module "int10"
[    58.825] (II) LoadModule: "int10"
[    58.825] (II) Loading /usr/lib/xorg/modules/libint10.so
[    58.825] (II) Module int10: vendor="X.Org Foundation"
[    58.825]     compiled for 1.15.1, module version = 1.0.0
[    58.825]     ABI class: X.Org Video Driver, version 15.0
[    58.825] (II) VESA(0): initializing int10
[    58.830] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    58.831] (II) VESA(0): VESA BIOS detected
[    58.831] (II) VESA(0): VESA VBE Version 3.0
[    58.831] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    58.831] (II) VESA(0): VESA VBE OEM: SiS
[    58.831] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    58.831] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    58.831] (II) VESA(0): VESA VBE OEM Product: 6330
[    58.831] (II) VESA(0): VESA VBE OEM Product Rev: 3.72.15a
[    58.832] (II) VESA(0): virtual address = 0xa6a65000,
    physical address = 0xc0000000, size = 268435456
[    58.841] (II) VESA(0): Setting up VESA Mode 0x11E (1280x768)
[    59.356] (==) VESA(0): Default visual is TrueColor
[    59.356] (**) VESA(0): Option "BackingStore" "true"
[    59.356] (**) VESA(0): Backing store enabled
[    59.357] (**) VESA(0): DPMS enabled
[    59.357] (WW) VESA(0): Option "UseFBDev" is not used
[    59.357] (WW) VESA(0): Option "MaxXFBMem" is not used
[    59.357] (WW) VESA(0): Option "RenderAccel" is not used
[    59.357] (WW) VESA(0): Option "AllowGLXWithComposite" is not used
[    59.357] (WW) VESA(0): Option "AddARGBGLXVisuals" is not used
[    59.357] (==) RandR enabled
[    59.366] (II) SELinux: Disabled on system
[    59.368] (II) AIGLX: Screen 0 is not DRI2 capable
[    59.368] (EE) AIGLX: reverting to software rendering
[    59.479] (II) AIGLX: Loaded and initialized swrast
[    59.479] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    59.499] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    59.503] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    59.504] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    59.504] (II) LoadModule: "evdev"
[    59.504] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    59.528] (II) Module evdev: vendor="X.Org Foundation"
[    59.528]     compiled for 1.15.0, module version = 2.8.2
[    59.528]     Module class: X.Org XInput Driver
[    59.528]     ABI class: X.Org XInput driver, version 20.0
[    59.528] (II) Using input driver 'evdev' for 'Power Button'
[    59.528] (**) Power Button: always reports core events
[    59.528] (**) evdev: Power Button: Device: "/dev/input/event2"
[    59.528] (--) evdev: Power Button: Vendor 0 Product 0x1
[    59.528] (--) evdev: Power Button: Found keys
[    59.528] (II) evdev: Power Button: Configuring as keyboard
[    59.528] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    59.528] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    59.528] (**) Option "xkb_rules" "evdev"
[    59.528] (**) Option "xkb_model" "pc105"
[    59.528] (**) Option "xkb_layout" "es"
[    59.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    59.536] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    59.536] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    59.537] (II) Using input driver 'evdev' for 'Power Button'
[    59.537] (**) Power Button: always reports core events
[    59.537] (**) evdev: Power Button: Device: "/dev/input/event1"
[    59.537] (--) evdev: Power Button: Vendor 0 Product 0x1
[    59.537] (--) evdev: Power Button: Found keys
[    59.537] (II) evdev: Power Button: Configuring as keyboard
[    59.537] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1/event1"
[    59.537] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    59.537] (**) Option "xkb_rules" "evdev"
[    59.537] (**) Option "xkb_model" "pc105"
[    59.537] (**) Option "xkb_layout" "es"
[    59.537] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    59.537] (II) No input driver specified, ignoring this device.
[    59.537] (II) This device may have been added with another device file.
[    59.538] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    59.538] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    59.538] (II) Using input driver 'evdev' for 'Video Bus'
[    59.538] (**) Video Bus: always reports core events
[    59.538] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    59.538] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    59.538] (--) evdev: Video Bus: Found keys
[    59.538] (II) evdev: Video Bus: Configuring as keyboard
[    59.538] (**) Option "config_info"  "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input6/event5"
[    59.538] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    59.538] (**) Option "xkb_rules" "evdev"
[    59.538] (**) Option "xkb_model" "pc105"
[    59.538] (**) Option "xkb_layout" "es"
[    59.539] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[    59.539] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    59.539] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    59.539] (**) Genius Optical Mouse: always reports core events
[    59.539] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event4"
[    59.540] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[    59.540] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[    59.540] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[    59.540] (--) evdev: Genius Optical Mouse: Found relative axes
[    59.540] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[    59.540] (II) evdev: Genius Optical Mouse: Configuring as mouse
[    59.540] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[    59.540] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    59.540] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    59.540] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input5/event4"
[    59.540] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 9)
[    59.540] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[    59.540] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    59.540] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    59.540] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    59.540] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    59.541] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[    59.541] (II) No input driver specified, ignoring this device.
[    59.541] (II) This device may have been added with another device file.
[    59.541] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event6)
[    59.541] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    59.541] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    59.541] (**) USB 2.0 Camera: always reports core events
[    59.541] (**) evdev: USB 2.0 Camera: Device: "/dev/input/event6"
[    59.541] (--) evdev: USB 2.0 Camera: Vendor 0x4f2 Product 0xb018
[    59.541] (--) evdev: USB 2.0 Camera: Found keys
[    59.541] (II) evdev: USB 2.0 Camera: Configuring as keyboard
[    59.541] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input8/event6"
[    59.542] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD, id 10)
[    59.542] (**) Option "xkb_rules" "evdev"
[    59.542] (**) Option "xkb_model" "pc105"
[    59.542] (**) Option "xkb_layout" "es"
[    59.542] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event7)
[    59.542] (II) No input driver specified, ignoring this device.
[    59.542] (II) This device may have been added with another device file.
[    59.543] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event8)
[    59.543] (II) No input driver specified, ignoring this device.
[    59.543] (II) This device may have been added with another device file.
[    59.543] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    59.543] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    59.543] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    59.543] (**) AT Translated Set 2 keyboard: always reports core events
[    59.543] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    59.543] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    59.543] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    59.543] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    59.543] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    59.543] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    59.543] (**) Option "xkb_rules" "evdev"
[    59.543] (**) Option "xkb_model" "pc105"
[    59.543] (**) Option "xkb_layout" "es"
[    59.544] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event9)
[    59.544] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    59.544] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    59.544] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    59.544] (II) LoadModule: "synaptics"
[    59.545] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    59.545] (II) Module synaptics: vendor="X.Org Foundation"
[    59.545]     compiled for 1.15.0, module version = 1.7.4
[    59.545]     Module class: X.Org XInput Driver
[    59.545]     ABI class: X.Org XInput driver, version 20.0
[    59.545] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    59.545] (**) ETPS/2 Elantech Touchpad: always reports core events
[    59.545] (**) Option "Device" "/dev/input/event9"
[    59.592] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 32 - 544 (res 0)
[    59.592] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 32 - 352 (res 0)
[    59.592] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[    59.593] (II) synaptics: ETPS/2 Elantech Touchpad: device does not report finger width.
[    59.593] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    59.593] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    59.593] (--) synaptics: ETPS/2 Elantech Touchpad: invalid pressure range.  defaulting to 0 - 255
[    59.593] (--) synaptics: ETPS/2 Elantech Touchpad: invalid finger width range.  defaulting to 0 - 15
[    59.593] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    59.593] (**) ETPS/2 Elantech Touchpad: always reports core events
[    59.628] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event9"
[    59.628] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    59.628] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    59.628] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    59.628] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.332
[    59.628] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    59.628] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    59.628] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    59.628] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    59.628] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    59.629] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    59.629] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[  3314.448] (II) VESA(0): Setting up VESA Mode 0x11E (1280x768)
[  3315.074] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found


```

By customised xorg.conf, I mean this (I don't understand what it means, but somehow it kinda works)
```

Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
    Busid "PCI:1:0:0"
    Driver "vesa"
    Screen 0
        Option "UseFBDev" "true"
        Option "DPMS"
        Option "ShadowFB"
        Option "MaxXFBMem"
        VideoRam 262016
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "true"
        Option "AddARGBGLXVisuals" "True"

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    HorizSync 20-107
        VertRefresh 50-185
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
    EndSubSection
EndSection

Section "Module"
    Load "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "int10"
    Load "vbe"
    Load "speedo"
    Load "record"
EndSection

Section "DRI"
        Mode 0666
EndSection


```

---

### Post by PabT on 2014-05-18
Thanks a lot. This is exactly what saved my Lubuntu on an Esprimo v5535. :)

---

### Post by Ruy Benton on 2014-06-13
> **PabT said:**
> Thanks a lot. This is exactly what saved my Lubuntu on an Esprimo v5535. :)

And your Resol. is 1280X800 (16:10) ????   :P

Please post your xorg file and other settings.

Best regards,
Ruy

---

### Post by mick.cannon on 2014-06-17
I've just replaced xubuntu 12.04 with xubuntu 14.04 on a laptop with a sis761 display card; now I have no choice of screen resolution; 600x480 only.
I find it very strange that it works perfectly from the live disk and shows the correct resolution.
I remember when I installed 12.04 I had to install the driver and edit xorg.conf. I've done that, though the config file didn't exist, I just copied the old file that I'd saved. Still doesn't work though.

---

### Post by mörgæs on 2014-06-17
Hi, I merged your post into a thread dealing with the same problem. People here seem to be in a similar situation (correct resolution from live boot, not after install).

Please post your xorg.conf.

---

### Post by Antonio_Carlos_.. on 2014-06-17
[COLOR=#000000] I have an old notebook wich I just installed Lubuntu on it. The main purpose is to give It to my father so he can watch vídeos on youtube.
After Lubuntu's installation, I got a low resolution (640x480) wich I just don't know how to change/improve it. Anyone can help me? Thanks.[/COLOR]

---

### Post by mörgæs on 2014-06-17
Another merge.

Please post the output requested in post #7.

---

### Post by mick.cannon on 2014-06-17
Success !!  Got it working at last by replacing my xorg.conf file with the one in this thread. Thanks for the help.

---

### Post by Nikhil_mishra on 2014-07-17
this is my xorg.conf file works fine now giving me a resolution of 1280x1024 1024x768 800x600 and 640x480 works fine after a several reboot tried all the method but in the last tried this method [https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis) so m not assure which method worked  but i can say after using system in live usb mode once created a xconfig.org file and then reboot m not assured but if u want try above link method with this xorg file, sorry if u didn't get anything i just want to help u all so enjoy):P
```
Section "Device"    Identifier     "Configured Video Device"
    Driver         "sisimedia"
    Option         "UseTiming1366" "yes"
EndSection


Section "Monitor"
    Identifier     "Configured Monitor"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Configured Monitor"
    Device         "Configured Video Device"
EndSection
```

---

### Post by woody1 on 2014-10-14
Where did you put the xorg.conf, I copied into /etc/X11 and restarted X, but this doesn't seem to work

---

### Post by javier-ejsf on 2014-10-14
I pasted it exactly into /etc/X11
 Did you copy it with Root power? Like uhm, sudo cp....

---

### Post by Ruy Benton on 2014-10-28
> **PabT said:**
> Thanks a lot. This is exactly what saved my Lubuntu on an Esprimo v5535. :)

To get full video use SMPLAYER ...         ;)


And Ubuntu 14.04.1 LTS ... OK???   


And MIR full support?

Best regards,     
Ruy

---

### Post by terry24 on 2014-11-01
For anybody that hasn't been able to get 1366x768 with SiS - you may want to read this..

I have been trying to find a solution for my laptop (Acer K50C) sis 672.  I wanted to get  1366x768 resolution working with Ubuntu 14.04.   In previous releases of ubuntu I downloaded the sis761 driver and compiled it....but I haven't been able to find a code that compiles ok for this ubuntu release.

I ended up downloading the sisimedia driver 

followed the instructions at the URL Below:

[http://zatherz.cba.pl/sis/](http://zatherz.cba.pl/sis/)

---

### Post by Alex Eagle on 2014-11-12
I haven't read this whole thread so no need to accuse me of being  ignorant or owt, but I'm trying to post this on all SIS threads.

I have a (horrible) Fujitsu Siemens Esprimo Mobile V5535, and [this]("http://ubuntuforums.org/showthread.php?t=2252488") fixed it for me...

Hope it helps.

P.S: morgaes is really good. Also grahammechanical is brillo with 'buntu. Also Bashing-om. If you're ever in doubt about owt 'buntu-ish, ask them. I don't know anyone better, and I'm sure some one better don't exist, which explain why I don't know of them.

---

### Post by jan-prikryl on 2014-12-28
Just a quick note to other "happy" owners of notebooks with SiS 771/671 family (Mirage 3) graphics: The Xorg "sis" driver in 14.04 does not work with SiS 771/671 family (Mirage 3). Actually, as far as I was able to find out, no version of Xorg drivers seems to officially support 771/671. There are some hacked drivers for XF86 and older Xorg versions, but people do not report much success with them. Related askubuntu topic is [here]("http://askubuntu.com/questions/507118/which-ubuntu-version-works-fine-with-sis-driver-671-771"). I came across a Xorg-devel mailing list thread ([here]("http://lists.x.org/archives/xorg-devel/2013-May/036138.html"), [here]("http://lists.x.org/archives/xorg-devel/2013-May/036151.html"), and [here]("http://lists.x.org/archives/xorg-devel/2013-May/036156.html")) where a guy has tried to update such a driver for a recent Xorg codebase in May 2013, but the thread ends at the moment when the driver probably works, but still has some problems.

Besides downgrading to older distributions, the only possibility for SiS 771/671 owners seem to be using the "vesa" driver with custom config as mentioned earlier in this thread. But, at least on the Asus X58C that I am trying to setup, you will not get the native resolution 1280x800 and you will get no acceleration, hence DVD and video playback is unusable.

Of course, as mentioned in the Xorg-devel post and also in the askubuntu question, the best solution would be to go and try git-bisect on the Xorg with working driver and find the change that introduced the bug ...

-- jan

---

### Post by Nikhil_mishra on 2015-01-17
Sorry for bumping again but i got something i don't know it is important or not or someone else already find this but m writing here 
 i got VGA driver for sis graphic card with my motherboard cd 
cd contained vga driver mandriva2007.1  
redhat4.4
and SuSE10.1
build date is 7/13/2007
i'm not a developer and not using this chip any more so if any one want this driver for making latest driver (if possible ) then i can provide  a download link for these driver
Hopefully this is useful and P.s for poor english

---

### Post by QNEPFmr on 2015-01-24
I have a Sis 671 card and what I have done is installing Mint 13, with the fix earlier mentioned, the one from the google site.
My res is as it is supposed to be.
The only downside is that is lasts until 2017, since this is the eol of Mint 13 and Ubuntu 12.04.

There is one other option though, if you would like to use an up to date distro that runs ootb with your sis671, then try PClinuxos!
It is a rolling release so it will probably last longer than your machine. ;)

---

