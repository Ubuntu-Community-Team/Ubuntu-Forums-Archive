---
title: "Geforce 7600 GS driver"
date: 2013-02-10
forum: General Help
---

### Post by LilLZ on 2013-02-10
Hello. I recently noticed that my install of ubuntu 12.10 on my Dimension 9100 has no driver for my graphics card. I have a GeForce 7600 GS. I have followed pretty much every guide to get it installed but it always ends in the same way; my unity disappears and I have to purge nvidia.... Yes I've tried install linux-headers, but it doesn't make a difference. Any ideas? I'm doing this because whatever driver is on right now doesn't support suspend and when I come out of it, my screens looks like a bunch of fuzzy static and I've been told its a driver issue.

---

### Post by LilLZ on 2013-02-11
anyone?

---

### Post by oldfred on 2013-02-12
I run gnome-panel or fallback with my 9600GT.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

   Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

---

### Post by bogan on 2013-02-12
Hi!, **LilLz**,

What nvidia drivers have you tried?

I run a GeForce 7650 GT with no problems in any  currently available nvidia drivers, whether from Additional Drivers or the nvidia.com downloaded versions **up to**, [COLOR=Red]BUT NOT BEYOND[/COLOR], 304.xx.

The 310 versions give a message that 'no cards can be found that are compatible with the present driver'. The 313 versions I have not tried, but I expect they will be the same, judging by the warning on the nvidia.com>drivers site.

Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test  -p
```Chao!, **bogan.**

---

### Post by LilLZ on 2013-02-14
I have tried current and another one, but I don't remember the name. I'll post the terminal log in a minute.

log: 
```
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libasound2:i386 libasyncns0:i386 libatk1.0-0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcaca0:i386 libcups2:i386 libcurl3-gnutls:i386 libdatrie1:i386
  libflac8:i386 libgcrypt11:i386 libgdk-pixbuf2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgtk2.0-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libidn11:i386
  libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson0:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5support0:i386 libldap-2.4-2:i386 libllvm3.1:i386
  libnspr4:i386 libnss3:i386 libogg0:i386 libopenal-data libopenal1:i386
  libp11-kit0:i386 libpango1.0-0:i386 libpulse0:i386 libroken18-heimdal:i386
  librtmp0:i386 libsasl2-2:i386 libsasl2-modules:i386 libsdl1.2debian:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386
  libthai0:i386 libtheora0:i386 libtiff5:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvorbisfile3:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcomposite1:i386 libxcursor1:i386 libxft2:i386 libxi6:i386
  libxinerama1:i386 libxrandr2:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/69.5 MB of archives.
After this operation, 208 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package nvidia-current.
(Reading database ... 190351 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_304.51.really.304.43-0ubuntu1_amd64.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_304.51-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up nvidia-current (304.51.really.304.43-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Dimension 9100 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.43 DKMS files...
First Installation: checking all kernels...
Building only for 3.7.0-7-generic
Building for architecture x86_64
Building initial module for 3.7.0-7-generic
ERROR (dkms apport): kernel package linux-headers-3.7.0-7-generic is not supported
Error! Bad return status for module build on kernel: 3.7.0-7-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/304.43/build/make.log for more information.
Setting up nvidia-settings (304.51-0ubuntu2) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-settings/ld.so.conf because link group nvidia_settings_conf is broken
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-7-generic
Warning: No support for locale: en_US.utf8

```

And uname...

```

tomobrien@ubuntu:~$ uname -r
3.7.0-7-generic
tomobrien@ubuntu:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G73 [GeForce 7600 GS] [10de:0392] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:c549]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
05:05.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
tomobrien@ubuntu:~$ /usr/lib/nux/unity_support_test  -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 9.2-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Update: Just tried the 304 driver from xorg and it seems to be working. Graphics still shows up as unknown, but suspend works and sudo sbin/lsmod | grep nvidia shows that its loaded. The screen just looks all around better too.

---

### Post by oldfred on 2013-02-14
Are you running 12.10? 
You have the 3.7 kernel which is with 13.04. And 13.04 is not yet released. Many are testing it to see if it works. Is that your intent?

---

