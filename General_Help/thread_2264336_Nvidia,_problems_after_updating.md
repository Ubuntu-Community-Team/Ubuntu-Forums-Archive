---
title: "Nvidia, problems after updating"
date: 2015-02-06
forum: General Help
---

### Post by adambond on 2015-02-06
Nvidia: Api mismatch

Ok, thanks to everyone helped me get up to speed, and get my updates going. Helped alot, and it updated and restarted just fine. 
Except, 
I have to click on a 'previous linux version' just for it to boot up properly. Otherwise im left with this screen. And dont know what the heck to do with it. :( 

[ATTACH=CONFIG]259773[/ATTACH]

Can I get to my desktop from this screen? 

I am currently in Windows now, because obviously, i cant get back into Ubuntu.

---

### Post by kerry_s on 2015-02-06
log in & type startx

---

### Post by adambond on 2015-02-06
Heres a vid of my restart. The first screen, I have to select 'Previous Linux Version' just to get it to boot up. But now, no previous version seems to work. At the end of the video, after the video cut off, it simply goes right to the screen you see above (see attached screen shot). 


[http://vid36.photobucket.com/albums/e44/327amc/MOV04835_zpsxpnaalxx.mp4](http://vid36.photobucket.com/albums/e44/327amc/MOV04835_zpsxpnaalxx.mp4)

---

### Post by adambond on 2015-02-06
logging in, and typing 'startx' gets me a little further. 



[ATTACH=CONFIG]259774[/ATTACH]

---

### Post by adambond on 2015-02-07
Looks like an Nvidia: Api mismatch.  Im searching and reading on it. Lots of info out there. :)  

Im not very good at terminal gymnastics. So, i'll probably be asking questions.

---

### Post by Mopar1973Man on 2015-02-07
It appears like your nVidia driver is crashing the X server. I would uninstall the nVidia drivers and re-install the open source drivers. 
[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by adambond on 2015-02-07
Thanks I will give that a try.

---

### Post by sorceror171 on 2015-02-07
I'm having the exact same problem with any kernel past 3.13.0-43:

[http://ubuntuforums.org/showthread.php?t=2252313](http://ubuntuforums.org/showthread.php?t=2252313)

No solution yet, but I've excerpted some logs if someone wants to try to figure out what broke.

---

### Post by oldfred on 2015-02-07
How did you install nVidia.
Best way is just from Ubuntu repository & then kernel will be updated with nVidia driver.
But if you directly install from nVidia, then you have to run commands to update kernel with nVidia driver or reinstall nVidia driver.

Or did you install nVidia from more than one source? If you use nVidia directly, then Ubuntu repository you get conflicts. You have to thoroughly purge all of first nVidia install before installing from another source.

Or did not not install the correct version for your nVidia card. There are several legacy versions now for older cards.

---

### Post by adambond on 2015-02-07
I managed to get logged on using a really old previous version someting like 3.7.0.52 

You are probably right oldfred. However, i have no idea how i installed nvidia. I built this computer a few years ago. And loaded ubuntu on it right after. 

I just need a safe path to proceed. Dont want to mess anything up with the wrong commands. Or by purging the old nvidia, and not being able to update.

---

### Post by oldfred on 2015-02-07
If you can boot:

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

      
 ubuntu-drivers devices | grep recommended

---

### Post by efflandt on 2015-02-07
One other thing you can try to see if you have Ubuntu nvidia packages installed is:```
dpkg-query -l nvidia* | grep ii
```But if that comes up empty, you likely downloaded something from nvidia.com and ran a script, which may need to be repeated after any kernel update. If you use Ubuntu packages, kernel updates should automatically compile new video modules (drivers). Years ago I mixed things up so badly trying to switch drivers when I had a failing video card (cheap Galaxy GT 430) that I had to reinstall Ubuntu.

---

### Post by adambond on 2015-02-07
> **oldfred said:**
> If you can boot:

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

      
 ubuntu-drivers devices | grep recommended

To vague. I dont know what you mean by #To see video: 

Also, i dont have a video card. The nvidia came with my motherboard.

---

### Post by oldfred on 2015-02-07
# is comment, lines without # are commands to copy into terminal so we can see details.
It still then is an nVidia chip, but then do you have dual video or just nVidia?

---

### Post by adambond on 2015-02-07
No dual video. Just a nvidia driver disc that came with my board.

---

### Post by oldfred on 2015-02-07
Any nVidia driver with system, it just for Windows.

---

### Post by adambond on 2015-02-07
> **oldfred said:**
> Any nVidia driver with system, it just for Windows.

What?  

Its a biostar motherboard. AMD processor. And version RN4.10B-NF61 driver cd for Nvidia chipset motherboard.

---

### Post by adambond on 2015-02-07
> **oldfred said:**
> 

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

      
 ubuntu-drivers devices | grep recommended


I finally made it home to input the commands. They are in order from right to left. 
[ATTACH=CONFIG]259813[/ATTACH][ATTACH=CONFIG]259814[/ATTACH][ATTACH=CONFIG]259815[/ATTACH][ATTACH=CONFIG]259816[/ATTACH][ATTACH=CONFIG]259817[/ATTACH]

---

### Post by adambond on 2015-02-07
Here is the Ubuntu Nvidia packages result
[ATTACH=CONFIG]259819[/ATTACH]

---

### Post by oldfred on 2015-02-07
Please post terminal output, not screen shots. Use screen shots for gui output.

You are using the open source driver. 
And you have an old nVidia 6150.

And it says you have both the 173 series & and 304 series drivers installed? Did you install both?

This says the 304 is the correct driver.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

You may have to totally uninstall both drivers and then reinstall jus tthe 304 one.
sudo apt-get purge nvidia-*
This may not exist so if an error that may be ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup    

Then go into system settings and other drivers icon or additional software and drivers tab depending on version of Ubuntu and install the correct 304.xx version which it should offer.

---

### Post by adambond on 2015-02-07
> **oldfred said:**
> Please post terminal output, not screen shots. Use screen shots for gui output.


You are going to have to explain that then. I assumed 'terminal output' is exactly what i was posting, via screen shots.

---

### Post by adambond on 2015-02-07
> **oldfred said:**
> 

You may have to totally uninstall both drivers and then reinstall jus tthe 304 one.
sudo apt-get purge nvidia-*
This may not exist so if an error that may be ok.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup    

Then go into system settings and other drivers icon or additional software and drivers tab depending on version of Ubuntu and install the correct 304.xx version which it should offer.

Ok, i was going to purge. But I noticed it was going to purge Nvidia common, which I read you dont want it to purge that particular one (not sure if that applied to my scenario, but figure more reasearch and reading until i know forsure). 

So monkyed around with trying to find your reference to 'additional software' and 'drivers tab' and clicked on additional drivers. 
In the 2 screen shots below, the first one (version 304) failed to install just now. 
But the (304 updates) appears to have installed successfully. 
[ATTACH=CONFIG]259820[/ATTACH][ATTACH=CONFIG]259821[/ATTACH]
I will restart in the morning, when Mr. Coffee gives me more patience. Thanks tremendously so far. Learning alot.

---

### Post by oldfred on 2015-02-08
You can just copy any terminal command we post here to the  terminal, and then copy & paste the output back here. If more than a few lines & preserve any formatting use Advanced Editor and the code tags # icon in edit panel.

Did you purge the 173.xx before reinstalling 304? Otherwise you still have the conflicts. 
Someone posted this, so newer versions do not have it:
 nvidia-common is obsolete in Ubuntu 14.04/Trusty


 Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
Uninstall fixes
[http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/)

---

### Post by adambond on 2015-02-08
Ok. Just did the purge. Heres the details. 

```
john@john-desktop:~$[COLOR=#ff0000] sudo apt-get remove --purge nvidia-*[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-173-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-current' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau-ia32' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-debugger' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau1' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-173' for regex 'nvidia-*'
Note, selecting 'nvidia-304' for regex 'nvidia-*'
Note, selecting 'nvidia-96-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-319' for regex 'nvidia-*'
Note, selecting 'nvidia-331' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-304-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-libopencl1-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-settings' for regex 'nvidia-*'
Note, selecting 'nvidia-libopencl1' for regex 'nvidia-*'
Note, selecting 'nvidia-vdpau-driver' for regex 'nvidia-*'
Note, selecting 'nvidia-96-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-opencl-profiler' for regex 'nvidia-*'
Note, selecting 'nvidia-cg-toolkit' for regex 'nvidia-*'
Note, selecting 'nvidia-96' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau1-ia32' for regex 'nvidia-*'
Note, selecting 'nvidia-173-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-331-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-96-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-331-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-experimental-304' for regex 'nvidia-*'
Note, selecting 'nvidia-experimental-310' for regex 'nvidia-*'
Note, selecting 'libkwinactivenvidiahack4' for regex 'nvidia-*'
Note, selecting 'nvidia-prime' for regex 'nvidia-*'
Note, selecting 'nvidia-180-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-profiler' for regex 'nvidia-*'
Note, selecting 'nvidia-current-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-opencl-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-current-updates-dev' for regex 'nvidia-*'
Note, selecting 'libkwinnvidiahack4' for regex 'nvidia-*'
Note, selecting 'nvidia-opencl-icd' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau' for regex 'nvidia-*'
Note, selecting 'nvidia-304-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-319-updates' for regex 'nvidia-*'
Note, selecting 'boinc-nvidia-cuda' for regex 'nvidia-*'
Note, selecting 'nvidia-current-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-compute-profiler' for regex 'nvidia-*'
Note, selecting 'nvidia-331-uvm' for regex 'nvidia-*'
Note, selecting 'nvidia-331-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-experimental-304-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-304' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-319' for regex 'nvidia-*'
Note, selecting 'nvidia-va-driver' for regex 'nvidia-*'
Note, selecting 'nvidia-current-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-173-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-185-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-319-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-texture-tools' for regex 'nvidia-*'
Note, selecting 'nvidia-304-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-common' for regex 'nvidia-*'
Note, selecting 'nvidia-tegra' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-319-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-331-updates-uvm' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-doc' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-gdb' for regex 'nvidia-*'
Note, selecting 'nvidia-304-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-experimental-310-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-toolkit' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau-dev' for regex 'nvidia-*'
Note, selecting 'libgl1-nvidia-alternatives' for regex 'nvidia-*'
Note, selecting 'nvidia-96-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-glx' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-experimental-304' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-experimental-310' for regex 'nvidia-*'
Note, selecting 'nvidia-173-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-319-updates-dev' for regex 'nvidia-*'
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Note, selecting 'vdpau-va-driver' instead of 'nvidia-va-driver'
Package nvidia-96-updates is not installed, so not removed
Package nvidia-96-updates-dev is not installed, so not removed
Package nvidia-cg-toolkit is not installed, so not removed
Package libkwinactivenvidiahack4 is not installed, so not removed
Package libkwinnvidiahack4 is not installed, so not removed
Package nvidia-prime is not installed, so not removed
Package nvidia-settings-304-updates is not installed, so not removed
Package nvidia-settings-319 is not installed, so not removed
Package nvidia-settings-319-updates is not installed, so not removed
Package nvidia-settings-experimental-304 is not installed, so not removed
Package nvidia-settings-experimental-310 is not installed, so not removed
Package nvidia-173-dev is not installed, so not removed
Package nvidia-173-updates is not installed, so not removed
Package nvidia-173-updates-dev is not installed, so not removed
Package nvidia-304-dev is not installed, so not removed
Package nvidia-304-updates-dev is not installed, so not removed
Package nvidia-319 is not installed, so not removed
Package nvidia-319-dev is not installed, so not removed
Package nvidia-319-updates is not installed, so not removed
Package nvidia-319-updates-dev is not installed, so not removed
Package nvidia-331 is not installed, so not removed
Package nvidia-331-dev is not installed, so not removed
Package nvidia-331-updates is not installed, so not removed
Package nvidia-331-updates-dev is not installed, so not removed
Package nvidia-331-updates-uvm is not installed, so not removed
Package nvidia-331-uvm is not installed, so not removed
Package nvidia-96 is not installed, so not removed
Package nvidia-96-dev is not installed, so not removed
Package nvidia-current-dev is not installed, so not removed
Package nvidia-current-updates is not installed, so not removed
Package nvidia-current-updates-dev is not installed, so not removed
Package nvidia-experimental-304 is not installed, so not removed
Package nvidia-experimental-304-dev is not installed, so not removed
Package nvidia-experimental-310 is not installed, so not removed
Package nvidia-experimental-310-dev is not installed, so not removed
Package nvidia-settings-updates is not installed, so not removed
Package boinc-nvidia-cuda is not installed, so not removed
Package nvidia-compute-profiler is not installed, so not removed
Package nvidia-cuda-dev is not installed, so not removed
Package nvidia-cuda-doc is not installed, so not removed
Package nvidia-cuda-gdb is not installed, so not removed
Package nvidia-cuda-toolkit is not installed, so not removed
Package nvidia-opencl-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu libunity6 gir1.2-ubuntuoneui-3.0
  linux-headers-3.2.0-40 linux-headers-2.6.35-22 wine-compholio-i386
  linux-headers-3.2.0-40-generic libubuntuoneui-3.0-1 libdee-1.0-1
  linux-headers-3.2.0-40-generic-pae wine-compholio
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-173* nvidia-304* nvidia-304-updates* nvidia-96-modaliases*
  nvidia-common* nvidia-current* nvidia-settings* nvidia-settings-304*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 266 MB disk space will be freed.

Do you want to continue [Y/n]? [COLOR=#ff0000]y[/COLOR]
(Reading database ... 871116 files and directories currently installed.)
Removing nvidia-173 ...
Removing all DKMS Modules
sudo aptDone.
update-alternatives: using /usr/share/nvidia-304-updates/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode.
Purging configuration files for nvidia-173 ...
dpkg: warning: while removing nvidia-173, directory '/usr/lib/nvidia-173/tls' not empty so not removed.
Removing nvidia-current ...
Purging configuration files for nvidia-current ...
Removing nvidia-304 ...
Removing all DKMS Modules
Done.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-304-updates/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-304-updates/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libcuda.so because associated file /usr/lib32/nvidia-304-updates/libcuda.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-304-updates/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-304-updates/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/nvidia.icd because associated file /usr/share/nvidia-304-updates/nvidia.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
INFO:Disable nvidia-304
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-304 ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-304-updates ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
INFO:Disable nvidia-304-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-304-updates ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-96-modaliases ...
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Removing nvidia-settings-304 ...
Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-76-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

john@john-desktop:~$ [COLOR=#ff0000]sudo apt-get install ubuntu-desktop[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu libunity6 gir1.2-ubuntuoneui-3.0
  linux-headers-3.2.0-40 linux-headers-2.6.35-22 wine-compholio-i386
  linux-headers-3.2.0-40-generic libubuntuoneui-3.0-1 libdee-1.0-1
  linux-headers-3.2.0-40-generic-pae wine-compholio
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-common pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11
Suggested packages:
  pavumeter paman paprefs pulseaudio-module-raop pulseaudio-esound-compat
The following NEW packages will be installed:
  nvidia-common pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 ubuntu-desktop
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,021 kB of archives.
After this operation, 4,074 kB of additional disk space will be used.
Do you want to continue [Y/n]? [COLOR=#ff0000]y[/COLOR]
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main nvidia-common i386 1:0.2.44.2 [18.9 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main pulseaudio i386 1:1.1-0ubuntu15.4 [885 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main pulseaudio-module-gconf i386 1:1.1-0ubuntu15.4 [13.8 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main pulseaudio-module-x11 i386 1:1.1-0ubuntu15.4 [18.4 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main ubuntu-desktop i386 1.267.1 [4,018 B]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main pulseaudio-module-bluetooth i386 1:1.1-0ubuntu15.4 [80.9 kB]
Fetched 1,021 kB in 5s (174 kB/s)                     
Preconfiguring packages ...
Selecting previously unselected package nvidia-common.
(Reading database ... 870618 files and directories currently installed.)
Unpacking nvidia-common (from .../nvidia-common_1%3a0.2.44.2_i386.deb) ...
Selecting previously unselected package pulseaudio.
Unpacking pulseaudio (from .../pulseaudio_1%3a1.1-0ubuntu15.4_i386.deb) ...
Selecting previously unselected package pulseaudio-module-gconf.
Unpacking pulseaudio-module-gconf (from .../pulseaudio-module-gconf_1%3a1.1-0ubuntu15.4_i386.deb) ...
Selecting previously unselected package pulseaudio-module-x11.
Unpacking pulseaudio-module-x11 (from .../pulseaudio-module-x11_1%3a1.1-0ubuntu15.4_i386.deb) ...
Selecting previously unselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.267.1_i386.deb) ...
Selecting previously unselected package pulseaudio-module-bluetooth.
Unpacking pulseaudio-module-bluetooth (from .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.4_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up nvidia-common (1:0.2.44.2) ...
Setting up pulseaudio (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-gconf (1:1.1-0ubuntu15.4) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.4) ...
Setting up ubuntu-desktop (1.267.1) ...
Setting up pulseaudio-module-bluetooth (1:1.1-0ubuntu15.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
john@john-desktop:~$ [COLOR=#ff0000]sudo rm /etc/x11/xorg.conf[/COLOR]
rm: cannot remove `/etc/x11/xorg.conf': No such file or directory
john@john-desktop:~$ [COLOR=#ff0000]echo 'noveau' | sudo tee -a /etc/modules
noveau[/COLOR]
john@john-desktop:~$
```

---

### Post by adambond on 2015-02-08
Now, 
Preferences- Additional Drivers- Version 304 (recommended)- installing

Preferences- Additional Drivers- Version 304 (updates)- installing

---

### Post by oldfred on 2015-02-08
Added code tags # in Advanced editor. Please use code tags on any long text/code output.

If you just reinstall 304, then you should not have conflicts. But real test is if you can reboot. Make sure you have good working Live installer just in case you have to make further repairs.

---

### Post by adambond on 2015-02-08
Well, you might as well point me in the direction of one of these 'live installers' you speak of. 

Unless a hammer will work. I have a couple of those.

---

### Post by oldfred on 2015-02-08
For every system you have installed you should have a current version repairCD or live installer. I have multiples for Linux including my Ubuntu LTS and most current versions, Knoppix, gparted liveCD, and several others.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by adambond on 2015-02-09
I have a bootable USB.  But really, im thinking if this thing doesnt reboot. Im dont with it. Flushing Ubuntu down the toilet and moving on. 

We'll see. I'll (try to) report back.

---

### Post by adambond on 2015-02-09
Havent rebooted yet, as I am downloading a fresh install cd, just to be  safe.  Should I make an Alternate Install CD or Desktop CD?

I checked what is installed, and looks like 304 with no others. 
Is there any code I can run to detect conflicts? 

```
john@john-desktop:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-common                                               1:0.2.44.2                                   Find obsolete NVIDIA drivers
john@john-desktop:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-304                                                  304.125-0ubuntu0.0.0.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-304-updates                                          304.125-0ubuntu0.0.0.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                               1:0.2.44.2                                   Find obsolete NVIDIA drivers
ii  nvidia-settings                                             331.20-0ubuntu0.0.1                          Tool for configuring the NVIDIA graphics driver
john@john-desktop:~$
```

---

### Post by oldfred on 2015-02-10
It looks like you have one newer one also?

331.20-0ubuntu0.0.1 

The dkms status command should show only one nVidia driver installed per kernel. I also suggest housecleaning older kernels. I try to keep at least two one older one that I know works and current. Once it builds up a couple I houseclean back to two. I prefer to use synaptic for housecleaning kernels.

---

### Post by adambond on 2015-02-10
> **oldfred said:**
> It looks like you have one newer one also?

331.20-0ubuntu0.0.1 

The dkms status command should show only one nVidia driver installed per kernel. I also suggest housecleaning older kernels. I try to keep at least two one older one that I know works and current. Once it builds up a couple I houseclean back to two. I prefer to use synaptic for housecleaning kernels.

Ok, i will take care of the older kernals. 

Well, atleast I understand im supposed to have only 1 driver per kernal. I thought the same thing. 

My question, how might I go through my older kernals, and get them set up with just 1 driver? 

Also, do I delete the 304 now? The 331 mentions its for configuring etc etc.  So might I be rebootable even with it installed?

---

### Post by oldfred on 2015-02-10
If you install nVidia from Ubuntu repository, it automatically updates all kernels. Or on install of nVidia driver it updates.

You can force the update.
This shows what driver is with what kernel.
 dkms status

      
 If already configured, you should not need this:

  man mkinitramfs
sudo update-initramfs -u 
or
sudo update-initramfs -k all -c

---

### Post by adambond on 2015-02-12
```
john@john-desktop:~$ dkms status
nvidia-304, 304.125, 3.2.0-54-generic, i686: installed
nvidia-304, 304.125, 3.2.0-76-generic, i686: installed
nvidia-304-updates, 304.125, 3.2.0-54-generic, i686: installed
nvidia-304-updates, 304.125, 3.2.0-76-generic, i686: installed
virtualbox, 4.1.12, 3.2.0-74-generic-pae, i686: installed
virtualbox, 4.1.12, 3.2.0-75-generic, i686: installed
virtualbox, 4.1.12, 3.2.0-76-generic, i686: installed
virtualbox, 4.1.12, 3.2.0-76-generic-pae, i686: installed
```


Seems like eveyrthing looks good. o.0 ?

---

### Post by oldfred on 2015-02-12
I think you still have two versions.
304 & 304-updates are not the same, so I think one or the other still needs to be housecleaned.

But I think you can just remove one or the other?
 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>

but not sure if package name is 

nvidia-304 or 304.125, but think the 304.125 is just the version.

---

### Post by adambond on 2015-02-12
Ok, checked here, and it mentioned the 'non update' 304 is not active. The '304 updated' is active.[ATTACH=CONFIG]259944[/ATTACH]

---

### Post by adambond on 2015-02-14
Success! Well, partially. 

I rebooted, and the latest kernal loaded up just fine. :KS

However, now my desktop is bigger than my screen (monitor).  In other words, I had many icons on my desktop lined up around the perimeter of my screen. Now that the desktop is bigger, those icons are now outside the perimter of my screen. 

Once I get back to normal here, (if that ever happens) i'll do a recap/last post of what all worked to solve my issue(s).

---

### Post by oldfred on 2015-02-14
I had that happen when I only was booting with the open source driver which defaulted to some low resolution. It was a bit tricky to get to system panel and the find the software/drivers icon which I was able to do. Would have been easier to have used command line, but it was in my system notes not printed & I could not easily get to them.

---

### Post by adambond on 2015-02-15
Yup, that sounds right. Definately in low res mode.

---

### Post by adambond on 2015-02-15
In the past, I just kept updating, and restarting. Eventually the graphics went back to normal. 

Get Ubuntu they said. 

Its will be no problem they said. 

](*,)

---

### Post by adambond on 2015-03-02
Well, we appear to have success.......... well partially. 

I restarted, and the graphics/resolution went all back to normal. My desktop now fits my screen. No lost icons. Im on kernal -77 now. 


BUUUUUT (ofcourse)  I am now not able to mount my usb stick that I use to transfer pictures from my phone to my computer.  

It pops up and lets me know its been connected, but WILL NOT MOUNT at all.

---

### Post by oldfred on 2015-03-02
Best to start a new thread on that topic.
Post what format and any other info you have on issue.

---

