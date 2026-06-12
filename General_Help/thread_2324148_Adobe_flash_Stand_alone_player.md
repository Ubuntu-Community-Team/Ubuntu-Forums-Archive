---
title: "Adobe flash Stand alone player"
date: 2016-05-11
forum: General Help
---

### Post by CCgirl6690 on 2016-05-11
Hello. I'm on ubuntu 14/04 
Can someone help me Install download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz or the exe version?
With commands and all? 
Thank you

---

### Post by Frogs Hair on 2016-05-11
Try the following.

```
sudo apt-get install flashplugin-installer
```

---

### Post by CCgirl6690 on 2016-05-11
> **Frogs Hair said:**
> Try the following.

```
sudo apt-get install flashplugin-installer
```

Thank you, but i need the Stand alone player and version 10. or 11 .  Not the plugin

---

### Post by CCgirl6690 on 2016-05-11
THis is the file i want to install...
download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz     or
download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.exe

---

### Post by Yellow Pasque on 2016-05-11
You do know that's an old and insecure version of Flash, correct?

I don't know why you would need this program, but if you decide you want to take the risk:
```
cd ~/Downloads/   #or wherever you downloaded the file
tar xzf flashplayer_10_sa.tar.gz
cd install_flash_player_10_linux_sa/
./flashplayer
```

There's also an installer script, but it doesn't work without a little hacking. You'll have to change line 67 from:
```
GLIBCMINOR=`echo $ICONVVER | cut -d'.' -f2`
```
to
```
GLIBCMINOR=`echo $ICONVVER | cut -d'.' -f2 | cut -d'-' -f1`
```

Then, you can run the installer:
```
sudo ./flashplayer-installer
```

Change the directory to /usr/local/bin
Again, I can't warn you enough that it's a big security risk to run this thing.

---

### Post by CCgirl6690 on 2016-05-11
> **Temüjin said:**
> You do know that's an old and insecure version of Flash, correct?

I don't know why you would need this program, but if you decide you want to take the risk:
```
cd ~/Downloads/   #or wherever you downloaded the file
tar xzf flashplayer_10_sa.tar.gz
cd install_flash_player_10_linux_sa/
./flashplayer
```

There's also an installer script, but it doesn't work without a little hacking. You'll have to change line 67 from:
```
GLIBCMINOR=`echo $ICONVVER | cut -d'.' -f2`
```
to
```
GLIBCMINOR=`echo $ICONVVER | cut -d'.' -f2 | cut -d'-' -f1`
```

Then, you can run the installer:
```
sudo ./flashplayer-installer
```

Change the directory to /usr/local/bin
Again, I can't warn you enough that it's a big security risk to run this thing.
Hello And thanks or helping me, I did not understand your second part about The script But i tried teh first part and got this...
$ cd install_flash_player_10_linux_sa
none@none-x:~/install_flash_player_10_linux_sa$ ./flashplayer
./flashplayer: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
none@none-x:~/install_flash_player_10_linux_sa$

---

### Post by CCgirl6690 on 2016-05-11
I searched and i figured i needed lib file since im 64 bits,  So i installed it and i got this error now.  Can you help me further please?...
```
none@none-Latitude:~/install_flash_player_10_linux_sa$ sudo apt-get install libgtk2.0-0:i386
[sudo] password for none: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  glib-networking:i386 gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad-multiverse gstreamer1.0-x:i386 libaa1:i386
  libao-common libao4 libappframework-java libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libdv4:i386 libfaac0
  libgstreamer-plugins-good1.0-0:i386 libhdb9-heimdal libiec61883-0:i386
  libkdc2-heimdal libmjpegutils-2.1-0 libmpeg2encpp-2.1-0 libmplex2-2.1-0
  libnatpmp1 libnspr4:i386 libnss-mdns-i386:i386 libnss3:i386 libntdb1
  libproxy1:i386 libraw1394-11:i386 libshout3:i386 libspeex1:i386
  libswingworker-java libtag1-vanilla:i386 libtag1c2a:i386 libwavpack1:i386
  linux-image-3.19.0-25-generic linux-image-3.19.0-39-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-39-generic
  python-ntdb
Use 'apt-get autoremove' to remove them.
Suggested packages:
  librsvg2-common:i386 gvfs:i386
The following NEW packages will be installed:
  libgtk2.0-0:i386
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B/1,697 kB of archives.
After this operation, 6,454 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libgtk2.0-0:i386
Install these packages without verification? [y/N] y
Selecting previously unselected package libgtk2.0-0:i386.
(Reading database ... 703353 files and directories currently installed.)
Preparing to unpack .../libgtk2.0-0_2.24.23-0ubuntu1.4_i386.deb ...
Unpacking libgtk2.0-0:i386 (2.24.23-0ubuntu1.4) ...
Setting up libgtk2.0-0:i386 (2.24.23-0ubuntu1.4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
none@none-Latitude:~/install_flash_player_10_linux_sa$ ./flashplayerGtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13046): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
Adobe Flash Player error: could not load cURL library

(flashplayer:13046): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(flashplayer:13046): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
none@none-Latitude:~/install_flash_player_10_linux_sa$ 
```

---

### Post by Yellow Pasque on 2016-05-11
> Adobe Flash Player error: could not load cURL library

Don't ask me; I don't know. My guess is that you need to install something related to libcurl. Good luck..

---

### Post by QDR06VV9 on 2016-05-11
As Temüjin tried to explain that version is probably not safe
Below is is a download link to the current Stand alone or as they are called (aka debug player or content debuggers) and standalone (aka projectors) players for Flex and Flash developers.
[http://www.adobe.com/support/flashplayer/debug_downloads.html](http://www.adobe.com/support/flashplayer/debug_downloads.html)

you can download & extract this, and run it by opening the flashplayerdebugger file.

---

### Post by CCgirl6690 on 2016-05-11
> **runrickus said:**
> As Temüjin tried to explain that version is probably not safe
Below is is a download link to the current Stand alone or as they are called (aka debug player or content debuggers) and standalone (aka projectors) players for Flex and Flash developers.
[http://www.adobe.com/support/flashplayer/debug_downloads.html](http://www.adobe.com/support/flashplayer/debug_downloads.html)

you can download & extract this, and run it by opening the flashplayerdebugger file.

Thank you.. i tried that version n i got this error....
```
none@none-Latitude:~$ cd flashplayer_11_sa.i386
none@none-Latitude:~/flashplayer_11_sa.i386$ ./flashplayerGtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:13602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
Vector smash protection is enabled.

(flashplayer:13602): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(flashplayer:13602): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
none@none-Latitude:~/flashplayer_11_sa.i386$ 

``` 
Can you help me please?

---

### Post by QDR06VV9 on 2016-05-11
I'm not sure you followed the instructions...but maybe?
Anyway go to where the download was saved and then right click on it and choose extract here.
Then inside that new folder you will see the flashplayerdebugger app And just to be safe right click on that(flashplayerdebugger) and go to permissions and make sure it shows "Allow this file to run as a Program"
There will be a checkbox that should show as checked.
Now just double click on that(flashplayerdebugger) and it should run as the window I showed in my Screenshot from my last post.

---

### Post by CCgirl6690 on 2016-05-11
Thanks. I did it but the window pops up and closes after a few seconds or sometimes stays up but closes as soon as i choose  a file to play. And the window doesnt look like yours. It looks weird i will show screenshot.
Thank again for helping

---

### Post by QDR06VV9 on 2016-05-11
Yeah what it plays is .swf files...
Try drag and dropping a Picture file in the URL Bar

---

### Post by CCgirl6690 on 2016-05-11
I know it plays that kidna file. But it doesnt work. It closes and disappears quickly.  Are you on 32 bits?

---

### Post by QDR06VV9 on 2016-05-11
No 64 Bit... but the player is 32 bit
Try this URL
```
[http://samples.mplayerhq.hu/SWF/zeldaADPCM2bit.swf](http://samples.mplayerhq.hu/SWF/zeldaADPCM2bit.swf)
```

---

### Post by howefield on 2016-05-12
Hi CCgirl6690, the windows version of the standalone player appears to work well in wine if that is acceptable to you as a workaround.

If you have wine already installed it would be easy enough to try, if not I'm not sure I'd install it just for flash. Shrug :)

---

### Post by CCgirl6690 on 2016-05-12
> **howefield said:**
> Hi CCgirl6690, the windows version of the standalone player appears to work well in wine if that is acceptable to you as a workaround.

If you have wine already installed it would be easy enough to try, if not I'm not sure I'd install it just for flash. Shrug :)

Hello my old Chess friend. 
I tired on wine. the gui loads up fine but when i try to open a file on the player it suddenly closes down and disappears,  I get the following errors when running wine through terminal
```
none@nonee:~$ wine '/home/none/Desktop/flashplayer_21_sa.exe' 
Vector smash protection is enabled.
fixme:win:EnumDisplayDevicesW ((null),0,0x32d4e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d4d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c5cc,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
none@none:~$ 
```

---

### Post by howefield on 2016-05-12
> **CCgirl6690 said:**
> I tired on wine. the gui loads up fine but when i try to open a file on the player it suddenly closes down and disappears,  I get the following errors when running wine through terminal

Hello again :)

I tried to replicate your issue on a fresh install of 14.04 and couldn't, it worked as expected. What version of wine are you using ?
> 
hugh@trusty:~$ wine --version
wine-1.6.2
hugh@trusty:~$ uname -a
Linux trusty 4.2.0-36-generic #41~14.04.1-Ubuntu SMP Tue Apr 19 17:04:05 UTC 2016 i686 i686 i686 GNU/Linux
hugh@trusty:~$

---

### Post by Yellow Pasque on 2016-05-12
You do have a CPU that supports SSE2, correct?

```
cat /proc/cpuinfo
```

---

### Post by Yellow Pasque on 2016-05-12
Sorry, I did not see you were using a 64-bit install. Disregard my previous post about SSE2. Maybe you need libcurl3:i386 package for this to work.

---

### Post by CCgirl6690 on 2016-05-12
Thanks everyone. I decided i don't want the flash anymore. To much headache. Also i noticed i can still watched vids on sites using html5?  I'm wondering shy should i install flash? 
Can someone answer me pelase?

---

### Post by Frogs Hair on 2016-05-12
Many videos are accessible with HTML 5, however, there are embedded video players and site content that still require Flash. The plug-in I described installing in post 2 will works for most embedded players and Flash content if using Firefox. If you have no problems veining the content you want there no need to install Flash. Google Chrome includes Flash with the browser.

---

### Post by QDR06VV9 on 2016-05-12
> **CCgirl6690 said:**
> Thanks everyone. I decided i don't want the flash anymore. To much headache. Also i noticed i can still watched vids on sites using html5?  I'm wondering shy should i install flash? 
Can someone answer me pelase?

I thought that this would end this way...It is good for special needs like Developing, Presentations, and Projectors etc etc.
But yes there are better ways to view media content on the web.
Kind Regards

---

