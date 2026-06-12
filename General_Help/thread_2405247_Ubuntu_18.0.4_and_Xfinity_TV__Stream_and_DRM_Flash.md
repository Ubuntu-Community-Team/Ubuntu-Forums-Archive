---
title: "Ubuntu 18.0.4 and Xfinity TV / Stream and DRM Flash"
date: 2018-11-03
forum: General Help
---

### Post by l33ch on 2018-11-03
I wrote up a little guide which includes URLs I obtained information from to be able to get Ubuntu Studio 18.0.4 to successfully play Xfinity TV content.

As many of you know, flash installed under linux, for linux does not install DRM content, at least as far as distribution agreements go (Google, Adobe, Entertainment Industry, etc.). Rumor has/had it (early 2018?) , that xfinityoncampus was testing ground for HTML5 Xfinity content. If/when that happens, here is what I did to get it to work. Currently running Firefox Quantum 63.0.1, ESR, and Firefox 48 via 64-Bit on Ubuntu Studio 18.0.4 x64 and Debian 9.06 Stretch x64, and Pale Moon. All credit goes out to previous authors of this subject. This is step by step from fresh install.

One quick note, you might have to do a few commands again due to how sneaky Firefox will update itself. This is even if you do not run any updates after the install because if you forget to turn off auto updates under Firefox Settings, it will update shortly. **(EDIT:Or once you install firefox, before opening, disconnect/disable your Internet, then open firefox and set to disable/prompt for updates, close firefox, re-enable network, and reopen).

But, it works from Firefox 3x.x-to 48 and later (50x-63.x) including the newest/quantum builds. (I can't remember how early..I tried 27, but I couldn't get it to work, I think one of the high 30 versions and it worked..I think?) *The only reason I was also looking into earlier builds was to see if content played better on a semi-older computer (circa 2012-2013), and it did, but newest builds were still acceptable. I'm still comparing and fiddling to compare, etc.

For the older versions, it really was more an issue finding a user agent extension that would still work on an old browser version-- (waybackmachine.org could be your friend here, or check for past version links on addon pages). Works wonderful on Pale Moon with Eclipse Moon. 

How to Get Xfinity TV / Xfinity Stream to Work on a Fresh Install of Ubuntu Studio 18.04 (May/Should Work on other flavors of 18.04 like Ubuntu Desktop, possibly Mint)

[urls]
[https://ubuntuforums.org/showthread.php?t=2363550&page=2](https://ubuntuforums.org/showthread.php?t=2363550&page=2)
[https://askubuntu.com/questions/984246/failed-to-load-libpepflashplayer-so-on-firefox-ubuntu](https://askubuntu.com/questions/984246/failed-to-load-libpepflashplayer-so-on-firefox-ubuntu)
[https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf?source=linux_recovery.sh](https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf?source=linux_recovery.sh)
[https://dl.google.com/dl/edgedl/chromeos/recovery/chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin.zip](https://dl.google.com/dl/edgedl/chromeos/recovery/chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin.zip)
[https://unix.stackexchange.com/questions/136420/unable-to-play-protected-drm-content-on-chrome](https://unix.stackexchange.com/questions/136420/unable-to-play-protected-drm-content-on-chrome)  (Wyatt8740's answer)

[https://ufile.io/gcb6y](https://ufile.io/gcb6y) (for your convenience, the libpepflashplayer.so file, from ChromeOS x64 build. Flash version: 31.0.0.108)

Preq: From chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin ChromeOS recovery image file,or a newer or older one,  have its version of Flash (DRM) ' libpepflashplayer.so ' copied somewhere where it is available (like a USB drive, desktop, some folder, whatever, etc.). From that particular zako image, it's located at:

~\chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin.zip\chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin\ROOT-A.img\opt\google\chrome\pepper\

so other versions/builds (x64 at least) should all have them in the same relative location: \ROOT-A.img\opt\google\chrome\pepper\


Zako is a chromebook/box x64 architecture, which would be compatible with x64 build of the system. You may need to change the steps/files to accommodate your
particular architecture (i.e. downloading an x86 ChromeOS build). Visit [https://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices]("https://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices") for a list of architectures.

Mozilla Firefox 52 ESR .tar.bz2 file downloaded from Mozilla.org and accessible.
( [https://ftp.mozilla.org/pub/firefox/releases/52.0/linux-x86_64/en-US/firefox-52.0.tar.bz2](https://ftp.mozilla.org/pub/firefox/releases/52.0/linux-x86_64/en-US/firefox-52.0.tar.bz2) )

Install ubuntustudio-18.04-dvd-amd64 (download updates and 3rd party checked, not sure if it matters)
Close Software Updater if it comes up.
Open File Manager and goto View->Show Hidden Files . 
then View->View as Detailed List .


Open Terminal and Uninstall Pre-Installed Firefox

```
sudo apt-get remove firefox
```


Untar Firefox-52.0.tar.bz2 to where you want it. (I'm lazy and just put the
.tar.bz2 file in home folder's Download folder. You can also use archive manager
to drag and drop the folder to where you want it.

```
tar -xvf firefox-52.0.tar.bz2
```

Install pepperflashplugin-nonfree & browser-plugin-freshplayer-pepperflash

```
sudo apt-get install pepperflashplugin-nonfree 
sudo apt-get install browser-plugin-freshplayer-pepperflash 
```


At this point confirm that /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so
exists.
Also confirm that /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so (and .json) file exists as well.


Start up Firefox (command line or just double-click on the Firefox executable file)

Close Window about default browser. Goto Menu-> Add-Ons and Confirm Shockwave Flash 31.0.r0 present. More Info will say libfreshwrapper-flashplayer.so 31.0.0.122

Click Get Add-Ons From Firefox/Add-ons Manager and Find more Add-Ons.

Search for User-Agent Switcher by Linder
+ Add to Firefox

Click the new little globe that appears in upper right near menu
Click Firefox (Should say Firefox on Windows. If not, click Windows and Firefox, etc until it says that), then click somewhere
and it will close and show Firefox logo where globe was.

Close Firefox and all tabs.

*Edit this command so the path points to where you have the chromeOS libpepflashplayer.so file.* 
Copy the ChromeOS libpepflashplayer.so file from wherever you have it to /usr/lib/pepperflashplugin-nonfree/ making sure to overwrite
the non DRM libpepflashplayer.so file that's already there.

```
sudo cp ~/path to chromeOS libpepflashplayer.so file/libpepflashplayer.so /usr/lib/pepperflashplugin-nonfree/
```

Delete manifest.json from /usr/lib/pepperflashplugin-nonfree/

```
**sudo rm /usr/lib/pepperflashplugin-nonfree/manifest.json 
``` **edit: actually I think you can keep the .json file there.

load up Firefox again

Confirm Plugins still shows Shockwave Flash 31.0.0.122 and Agent Still on Mozilla/Windows

Goto tv.xfinity.com and sign in.

Click Allow and Remember When Flash attempts to run.


Chances are that firefox will update automatically to 63.0.1 and in the process will break libpepflashplayer. Uninstall pepperflashplugin-nonfree 
and browser-plugin-freshplayer-pepperflash (apt-get remove) and reinstall them again (apt-get install) and recopy the ChromeOS libpepflashplayer.so back over and everything should work again--that's what I had to do. Maybe go into Firefox settings and not have it set to automatically update Firefox since you will need to do this after every Firefox update. 


Hope that helps anyone else.


* Of special note is the warning that Flash is inherently insecure. This is why the majority of entertainment providers (Netflix, Hulu, Amazon, etc) have moved to HTML5 which offers DRM but better
security for the consumer. Why Comcast hasn't done so is for another thread/debate, I just wanted to help paying customers with getting what they are entitled to. Now, that being said, and after you do all this and are watching (in my case) CNN (I watch alot of news, lol), you should really look into securing this Firefox/Flash install. As suggested by a friend, research how to chroot / jail / sandbox Firefox as a security measure so it cannot get elevated privileges to the system. I'm just looking into that now, as I don't really know hardly anything about chroot; maybe someone can write up a guide for that. My friend sent me this link [https://igurublog.wordpress.com/downloads/script-sandfox/](https://igurublog.wordpress.com/downloads/script-sandfox/) and this might be a viable and easier way of jailing Firefox (automated scripts to create the environment for you) vs typing it all out manually. Do what works for you. I'll be looking into it because Flash cannot be 100% trusted.


* Bonus: If you have an integrated  INTEL video  (ex. i915), and notice screen tearing  doing this should help: 

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
**THIS IS ONLY FOR INTEL GRAPHICS DO NOT FOLLOW IF YOU HAVE ATI/AMD/NVIDIA VIDEO**
Visit [https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics) and [https://jlk.fjfi.cvut.cz/arch/manpages/man/intel.4](https://jlk.fjfi.cvut.cz/arch/manpages/man/intel.4) for more info.

edit or create /etc/X11/xorg.conf.d/20-intel-graphics.conf file           (if folder/file doesn't exist, create them manually)

```
Section "Device"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option      "TearFree" "true" 
EndSection
```

This one is my 20-intel-graphics.conf:

```
Section "Device"
Identifier "Intel Graphics"
Driver "intel"
Option "AccelMethod" "sna"
Option "TearFree" "true"
Option "TripleBuffer" "true"
Option "MigrationHeuristic" "greedy"
Option "Tiling" "true"
Option "Pageflip" "true"
Option "ExaNoComposite" "false"
Option "Tiling" "true"
Option "Pageflip" "true"
EndSection

```

---

### Post by pvanryn on 2018-11-15
Thanks so much for posting this. I tried two or three times using similar methods, but this is the first one that worked. 

And the performance is awesome - no lag at all - as good as native Windows streaming. Much better than Wine. Hopefully Comcast won't break it.  :D

---

### Post by praywwjd2004 on 2018-11-18
I am new to Ubuntu and I am having trouble with these instructions. Is there someone that can help walk me thru or troubleshoot what I am doing wrong? If so I can post the error messages I am getting.

---

### Post by pvanryn on 2018-11-19
What version Firefox and what error?

---

### Post by praywwjd2004 on 2018-11-20
> **pvanryn said:**
> What version Firefox and what error?


I uninstalled the original Firefox as per the instructions but I had trouble with the next step. Here is my output:

```
donavan@donavan-SX2840:~$ sudo apt-get remove firefox
[sudo] password for donavan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox
0 upgraded, 0 newly installed, 1 to remove and 35 not upgraded.
After this operation, 178 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 165600 files and directories currently installed.)
Removing firefox (63.0+build2-0ubuntu0.18.10.2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-3ubuntu2) ...
Processing triggers for man-db (2.8.4-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
donavan@donavan-SX2840:~$ Tar -xvf firefox-52.0.tar.bz2


Command 'Tar' not found, did you mean:


  command 'jar' from deb openjdk-11-jdk-headless
  command 'jar' from deb default-jdk
  command 'jar' from deb fastjar
  command 'jar' from deb openjdk-8-jdk-headless
  command 'car' from deb ucommon-utils
  command 'tar' from deb tar
  command 'dar' from deb dar
  command 'ar' from deb binutils
  command 'ear' from deb ecere-dev
  command 'par' from deb par
  command 'sar' from deb sysstat
  command 'bar' from deb bar
  command 'kar' from deb sra-toolkit
  command 'rar' from deb rar


Try: sudo apt install <deb name>


donavan@donavan-SX2840:~$ 
```


Please help me troubleshoot from here.

---

### Post by deadflowr on 2018-11-20
> I uninstalled the original Firefox as per the instructions but I had trouble with the next step.
See if tar is installed,
```
sudo apt install tar
```
if installed see if running it with all lowercase works.
(ie, instead of Tar with a capital T, try it like tar and a lower case t)

---

### Post by pvanryn on 2018-11-20
> **praywwjd2004 said:**
> I uninstalled the original Firefox as per the instructions but I had trouble with the next step. Here is my output:

```

donavan@donavan-SX2840:~$ Tar -xvf firefox-52.0.tar.bz2

Command 'Tar' not found

donavan@donavan-SX2840:~$ 
```


It is "tar" with a small t - not "Tar".

Unlike Windows, capitalization makes a big difference on Linux.

---

### Post by praywwjd2004 on 2018-11-20
tar is already installed.
```
donavan@donavan-SX2840:~$ sudo apt install tar
[sudo] password for donavan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tar is already the newest version (1.30+dfsg-2).
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.

```
Using the the lowercase tar gave me the following output:
```
donavan@donavan-SX2840:~$ tar -xvf firefox-52.0.tar.bz2
tar: firefox-52.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```

---

### Post by deadflowr on 2018-11-20
You need to be in the directory where the tarball is.
If downloaded normally, then cd into the Downloads folders.
(Typically that's where downloads are by default.)
Then run the tar command.

---

### Post by praywwjd2004 on 2018-11-20
> **deadflowr said:**
> You need to be in the directory where the tarball is.
If downloaded normally, then cd into the Downloads folders.
(Typically that's where downloads are by default.)
Then run the tar command.


Thank you I used "cd ~/Downloads" and was able to get past that step.
I have confirmed that /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so exists.
I also confirmed that /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so (and .json) file exists as well. 
However I don't have an icon for Firefox. How do I launch Firefox from the terminal?

---

### Post by monkeybrain20122 on 2018-11-20
Is there any reason you need FF ESR? It works for Firefox 60+ last I checked. [https://ubuntuforums.org/showthread.php?t=2363550&page=2](https://ubuntuforums.org/showthread.php?t=2363550&page=2)

---

### Post by praywwjd2004 on 2018-11-21
> **monkeybrain20122 said:**
> Is there any reason you need FF ESR? It works for Firefox 60+ last I checked. [https://ubuntuforums.org/showthread.php?t=2363550&page=2](https://ubuntuforums.org/showthread.php?t=2363550&page=2)


Honestly I don't know what I need. I am just following the steps in the guide that was posted. The post in the link that you provided is talking about getting flash to work. That is not really what I am trying to achieve. I just want to find an easy way to install and run Showbox as well as have access to the Google Playstore. If you know of an easier way for me to achieve this please let me know.

---

### Post by donkramer on 2018-11-25
Question ... I did the linux_recovery.sh script to retrieve the chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin.zip file, and unzip the chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin and placed on a USB thumbdrive, from that thumbdrive, I'm trying to mount ROOT-A but I can't ... closest I've gotten is below. Does anyone have specific instructions on mounting it so I can copy the DRM version of Flash? This is on Debian Stretch. I can clearly see on my desktop from the USB stick the directories "OEM", "10 MB Volume", and "ROOT-A". Thanks!

root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942# pwd
/media/myusername/35673072-f004-4afa-801f-e7a968eda942
root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942# ls
lost+found  unencrypted  vmlinuz_hd.vblock
root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942# kpartx -a vmlinuz_hd.vblock
root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942# kpartx -l vmlinuz_hd.vblock
loop0p1 : 0 125 /dev/loop0 3
root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942# mount -ro loop /dev/loop0 /mnt/img1
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
root@debian:/media/myusername/35673072-f004-4afa-801f-e7a968eda942#

---

### Post by pvanryn on 2018-11-26
> **donkramer said:**
> Question ... I did the linux_recovery.sh script to retrieve the chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin.zip file, and unzip the chromeos_10895.78.0_zako_recovery_stable-channel_mp-v3.bin and placed on a USB thumbdrive, from that thumbdrive, I'm trying to mount ROOT-A but I can't ... closest I've gotten is below. Does anyone have specific instructions on mounting it so I can copy the DRM version of Flash? 

It is confusing because the method is spread out over several threads now.

To extract libpepflashplayer.so, you need to follow[ this thread]("https://ubuntuforums.org/showthread.php?t=2363550").

Basically:

> **monkeybrain20122 said:**
> 
install kpartx, it will be needed to mount the chromeos image later

```
sudo apt install kpartx
```

To mount the recovery image


```
sudo kpartx -av /path/to/bin/file

```It will print out a lot of partitions like


```
add map loop7p1 (253:0): 0 28672 linear 7:7 2928640
add map loop7p2 (253:1): 0 32768 linear 7:7 20480
add map loop7p3 (253:2): 0 2641920 linear 7:7 286720
add map loop7p4 (253:3): 0 32768 linear 7:7 53248
add map loop7p5 (253:4): 0 4096 linear 7:7 282624
add map loop7p6 (253:5): 0 1 linear 7:7 16448
add map loop7p7 (253:6): 0 1 linear 7:7 16449
add map loop7p8 (253:7): 0 32768 linear 7:7 86016
add map loop7p9 (253:8): 0 1 linear 7:7 16450
add map loop7p10 (253:9): 0 1 linear 7:7 16451
add map loop7p11 (253:10): 0 16384 linear 7:7 64
add map loop7p12 (253:11): 0 32768 linear 7:7 249856

```
You need the third one (corresponds to "ROOT" shown in file manager
To mount it (it doesn't open in file manager)

create a directory in your home to mount the image

```
mkdir mnt

```
mount the image to mnt
```

sudo mount -t ext2 /dev/mapper/loop7p3 -o ro  ~/mnt

```


navigate to mnt, now you will see the content of the partition you just mounted

inside mnt, navigate to /opt/google/chrome/pepper/, libpepflashplayer.so is the flash that you need. Create a folder in your home called PepperFlash (say) then copy libpepflashplayer.so there


to unmount


```
sudo umount ~/mnt

```and


```
sudo kpartx -dv /path/to/bin/file

```


---

### Post by l33ch on 2018-12-06
> **pvanryn said:**
> Thanks so much for posting this. I tried two or three times using similar methods, but this is the first one that worked. 

And the performance is awesome - no lag at all - as good as native Windows streaming. Much better than Wine. Hopefully Comcast won't break it.  :D


Try it with Pale Moon and the Eclipsed Moon add-on user agent switcher/changer/randomizer. Old firefox code-base (which Pale Moon was built-up from) so it runs really zippy. Works fine with this (chromOS) version of libpepflashplayer.so. 

On slightly unrelated note, should also work on other flavors of linux like Mint and Debian 9 Stretch ([https://wiki.debian.org/PepperFlashPlayer/Installing);](https://wiki.debian.org/PepperFlashPlayer/Installing);) however, you will need to download the .deb separately, as it's not included in Stretch repos (1.8.3+nmu1 as of today).

---

### Post by l33ch on 2018-12-06
> **monkeybrain20122 said:**
> Is there any reason you need FF ESR? It works for Firefox 60+ last I checked. [https://ubuntuforums.org/showthread.php?t=2363550&page=2](https://ubuntuforums.org/showthread.php?t=2363550&page=2)



Not really. You can use ESR. Firefox48-50.x,etc (seems to run faster than quantum) , Firefox 60.x. Runs great on Pale Moon. When I did this, I wanted anything that could potentially conflict, out of the way (hence, removing pre-installed firefox browsers, etc) before doing the steps. But no, you should not have to remove the browser before-hand. I was working with multiple versions/profiles of firefox. I wanted one JUST for xfinity. And another for regular browsing (but also works for xfinity).  Firefox 48 runs faster than Firefox 50x-60/Quantum. Pale Moon seems to run as fast or faster than Firefox48. I average about 8-13% CPU utilization when watching the Xfinity DRM content. Definitely way way way less than Windows (40-60% or so). I'm a happy camper. Make sure to back up your system once you get this set up the way you want it, so you don't have to do it again, hahah.


* Note, if you are running multiple versions of Firefox, make sure to use to use the " -p " switch so that your profile(s) don't get overwritten. If only using one version of Firefox, you're fine.

If you would like to run multiple profiles of Firefox at once, also use the " -no-remote " flag. I set up all my Firefox to execute via: " Firefox-esr (or firefox) -p *ProfileName -no-remote ". 

For example, if the profile folder was named '897g87.Firefox' or '48098f0.default' or whatever, you would enter the command:

```
firefox -p 897g87.Firefox -no-remote
```

All versions of firefox put their profiles in ~/home/username/.mozilla/firefox/, so without those switch(s), and if you only have 1 profile in there, you will go back and forth between firefox versions but using the same profile (so your bookmarks, etc will go bye bye)., so to avoid that:

```
 firefox -p profilename -no-remote 
```  

The ' -p ' switch loads the profile. The ' -no-remote ' switch allows you to run multiple profiles at one. Running just 'firefox -p' will bring up the profile selection/rename/delete screen.

---

### Post by pvanryn on 2018-12-08
> **l33ch said:**
> Try it with Pale Moon and the Eclipsed Moon add-on user agent switcher/changer/randomizer. Old firefox code-base (which Pale Moon was built-up from) so it runs really zippy. Works fine with this (chromOS) version of libpepflashplayer.so. 

On slightly unrelated note, should also work on other flavors of linux like Mint and Debian 9 Stretch ([https://wiki.debian.org/PepperFlashPlayer/Installing);](https://wiki.debian.org/PepperFlashPlayer/Installing);) however, you will need to download the .deb separately, as it's not included in Stretch (1.8.3+nmu1 as of today).

Pale Moon works really well, but I don't have any on-screen controls when I use it. Does this happen to you? Any fix? I can live with it, but it is inconvenient for channel surfing. Controls appear for just a moment when the video starts, but after that they are inaccessible and I have to use the browser "back" button which takes me back to the login screen.

With the .deb package, do you still do ```
apt-get install pepperflashplugin-nonfree browser-plugin-freshplayer-pepperflash
``` or do you install the .deb only?

---

### Post by l33ch on 2018-12-08
> **pvanryn said:**
> Pale Moon works really well, but I don't have any on-screen controls when I use it. Does this happen to you? Any fix? I can live with it, but it is inconvenient for channel surfing. Controls appear for just a moment when the video starts, but after that they are inaccessible and I have to use the browser "back" button which takes me back to the login screen.

With the .deb package, do you still do ```
apt-get install pepperflashplugin-nonfree browser-plugin-freshplayer-pepperflash
``` or do you install the .deb only?

Under Ubuntu Studio those 2 commands installed the wrapper ' browser-plugin-freshplayer-pepperflash' and Adobe's regular DRM-Free Flash, 'pepperflashplugin-nonfree' from their site. However, under Debian, I could not install ' pepperflashplugin-nonfree ' as it was not included in Debian 9 Stretch repos but is avail from Buster..didn't seem to break any dependencies. After installing that .deb, I just did 'sudo apt-get install browser-plugin-freshplayer-pepperflash', which was available via the regular apt-get install method. So in Debian 9, they kept browser-plugin-freshplayer-pepperflash, but you need to get the .deb for pepperflashplugin-nonfree. Of course under Ubuntu, you can get/install both via apt-get.

Yes! I have the same exact issue! Unless I'm running the newest/recent version of firefox, I do not get the settings/pause, mini player , etc. options that normally should be there. Newest version of firefox, it's there. I have no idea why, it is kinda annoying, if I want to change quality settings from High to Low or vice-versa. As you found out, sometimes at the beginning of the stream, OR, at the start of advertisements, you can sometimes access those settings and it appears that they work vs trying to right click on the "stock" quality settings, which seem to have no effect. If you find out anything that could shed some light and possible solutions I would be most appreciated--but I can live with it. Could be some weird compatibility since technically that flash file is from a chromeOS build, I dunno.

Edit: So, I did some playing around. It seems that if you run a firefox base version of 52 or higher (firefox 52, waterfox 52, in my case) you will get the Xfinity Stream controls. If you run an older base version like Pale Moon, or Firefox 48, those options will not be available.  For some reason, I cannot run the newest firefox versions and watch xfinity, my tab crashes--but thats ok--the newer Firefox versions use noticeably more CPU and memory, even Waterfox.

Update: Seems my tabs were crashing with something to do with the libxul.so and associated libraries. I reproduced it in Ubuntu Studio 18 (Since I'm currently using Debian) from clean live ISO/usb boot, installed the flash and replaced the libpepflashplayer.so..and it would crash on me under Firefox6x instantly. Then did the Ubuntu Studio software updates (via system menu) and it worked (again, with high CPU usage, but the controls were there). Under Debian 9, maybe since versions tend to be held back more (aka stable), firefox updates but needs a particular/newer version pertaining to libxul.so, I dunno. Not going to worry about it. But will work in Ubuntu Studio and newest version(s) of Firefox provided you do the system updates--It didn't work via new firefox version and no updates on the LiveCD, until after doing the updates. Hope that helps anyone.

---

### Post by pvanryn on 2018-12-10
> **l33ch said:**
> 
Edit: So, I did some playing around. It seems that if you run a firefox base version of 52 or higher (firefox 52, waterfox 52, in my case) you will get the Xfinity Stream controls. If you run an older base version like Pale Moon, or Firefox 48, those options will not be available.  For some reason, I cannot run the newest firefox versions and watch xfinity, my tab crashes--but thats ok--the newer Firefox versions use noticeably more CPU and memory, even Waterfox.

I also installed Waterfox - must be a newer version because I have controls. Not as speedy as Pale Moon, but maybe a *little* better than Firefox. I have another problem however, Pale Moon is  causing my system to lock up. This is on Linux Mint 19 now. If I watch tv for any length of time, everything freezes except the cursor. Can't even switch to a virtual terminal, the only solution is a hard shutdown. I don't have this problem with Firefox / Waterfox.  I may switch back to Ubuntu eventually, but I'm going to give it a rest for awhile.

For anyone that is interested, I installed Linux Mint with the third party add-ons and then did the Xfinity Stream procedure. I couldn't get it to work, but finally figured out that Adobe Flash had been installed with the third party add-ons. Had to go into /usr/lib/ and delete the adobe flash directory before things would work.

---

### Post by l33ch on 2018-12-10
> **pvanryn said:**
> I also installed Waterfox - must be a newer version because I have controls. Not as speedy as Pale Moon, but maybe a *little* better than Firefox. I have another problem however, Pale Moon is  causing my system to lock up. This is on Linux Mint 19 now. If I watch tv for any length of time, everything freezes except the cursor. Can't even switch to a virtual terminal, the only solution is a hard shutdown. I don't have this problem with Firefox / Waterfox.  I may switch back to Ubuntu eventually, but I'm going to give it a rest for awhile.

For anyone that is interested, I installed Linux Mint with the third party add-ons and then did the Xfinity Stream procedure. I couldn't get it to work, but finally figured out that Adobe Flash had been installed with the third party add-ons. Had to go into /usr/lib/ and delete the adobe flash directory before things would work.

Oh good. I couldn't remember when I did U.S. if i had 3rd party checked or not--Theoretically, it should work without selecting that option during installation, then wont have to deal with deleting the adobe flash folder later when doing the steps, etc. I couldn't remember..lol.

Wow, lock ups in linux...that shouldn't happen..crashes, sure and usually it will tell you whats going on. That is really weird. I don't really have any suggestions except maybe a couple, but apologies ahead of time if it doesn't work. I'm running Pale Moon 28.2.1. I originally installed it via the .deb file from Pale Moon's site directly It has been working fine for me no problems (except the additional flash controls, of course). But, what I did was add the repo for Pale Moon as well if/when upgrade is available. On Pale Moon's site 28.2.2 is available but Debian won't download it despite me adding the Steve Pusser repos ([https://software.opensuse.org/download.html?project=home:stevenpusser&package=palemoon](https://software.opensuse.org/download.html?project=home:stevenpusser&package=palemoon)). I'm pretty sure I could remove the version I have now, and just directly install the .deb to bring it to version 28.2.2. Anyway, I guess what I was going to suggest would be to try removing/purging the pale moon version you have installed and reinstalling it , and/or install  a newer version (or go back to 28.2.1 if on 28.2.2)...and a fresh profile..maybe that might fix things? Other than that, I really have no idea. That sucks tho. it shouldn't crash like that. I hope you find out and resolve. Good luck!.

---

### Post by pvanryn on 2018-12-10
You can grab the Pale Moon 28.2.2 tar ball [here]("http://linux.palemoon.org/download/mainline/"). I just unzipped it in the /opt directory and made a symlink to the binary.

I think my crashes are partly due to the fact that I have a Ryzen APU and the drivers aren't mature yet. 

Keep up the good work. Hopefully this fix will work until Xfinity goes to HTML 5. Adobe Flash must die!

---

### Post by jrguinn on 2019-01-08
I've sucessfully gotten this to work. I am able to watch xfinity.com/stream with firefox, currently Firefox Quantum 64.0 (64 bit).
 I installed pepperflashplugin-nonfree, and browser-plugin-freshplayer-pepperflash. 
The only other thing needed is the libpepflashplayer.so file from the chromeOS recovery bin. 
That was an annoying task, and I had to do it with kpartz, since the file download link that was supplied is dead. 

Here is a link to the libpepflashplayer.so that I extracted from chromeOS recover file [https://goo.gl/45zn9a](https://goo.gl/45zn9a).

---

### Post by l33ch on 2019-01-16
Yeah I cheated, when extracting the file from the recovery file. Use whatever method (7zip, kpartz, do it in windows, whatever) to extract the .so file. I just used WINE and installed 7zip and just used that instead of kpartz to extract the libpepflashplayer.so file. Glad you and others were able to get it to work. They are now saying 2020 (sigh) when HTML5 will be in transition.

---

### Post by 3blake7 on 2019-07-18
> **jrguinn said:**
> I've sucessfully gotten this to work. I am able to watch xfinity.com/stream with firefox, currently Firefox Quantum 64.0 (64 bit).
 I installed pepperflashplugin-nonfree, and browser-plugin-freshplayer-pepperflash. 
The only other thing needed is the libpepflashplayer.so file from the chromeOS recovery bin. 
That was an annoying task, and I had to do it with kpartz, since the file download link that was supplied is dead. 

Here is a link to the libpepflashplayer.so that I extracted from chromeOS recover file [https://goo.gl/45zn9a](https://goo.gl/45zn9a).

Thank you!!! It's working.

---

### Post by l33ch on 2019-07-30
Works with Debian 10, and I would assume newer builds of Ubuntu as well.  I can now use newest builds of firefox. I have not been able to resolve the lack of closed captions, i.e. just getting black/blank caption boxes. I thought it could be a font issue, but I do not know. It is a good idea to update/remove reinstall pepperflashplugin-nonfree and browser-plugin-freshplayer-pepperflash from time to time, as it could resolve any potential tab crashing. But maybe like once every x months or something. Why can't Xfinity be on the same year technologically speaking as everyone else and use HTML5--it's ridiculous, and that we have to use these hacks to begin with.

---

### Post by l33ch on 2019-08-23
> **sakshi-8 said:**
> Thank you for posting this. I tried various other methods but this one worked pretty well. The steps were explained in a very easy manner. :)

Glad to hear it! I might re-write it, make it a little neater.  Anyone coming upon this thread, I would recommend downloading the .bin/.zip from 

[https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf?source=linux_recovery.sh](https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf?source=linux_recovery.sh) . 

The link I posted for one of the .bin/.zip's was just posted there for everyone's convenience, but is now an older version. Also use the developer device list link to lookup the code name for the device to allow one to match up in the recovery.conf/recovery.sh file to download the proper file for your particular computer (64-bit, 32-bit, etc). I just try to match up/download a 64-bit version with newest kernel version as listed in developer list, and look for it in the recovery.sh file and download it.

But that recovery.conf/recovery.sh file from google is updated daily by google, so you will always have a listing of the newest filenames and builds thereby making sure the flash version you get <extract> is always a newer/newest version. 

As stated before, I just used 7zip via WINE, to open the zip file. And further right-click/'look inside' the .bin to get to the .so file location in the firmware and extract it.

Credit goes out to all those who preceded me with their respective guides and URLs. I just tried to condense it a little bit for others to follow.  

Also, you don't have to use the linder user-agent switcher. But, I've found it to be one of the better ones. Another really good one is the user-agent platform spoofer by devkef and User-Agent Switcher and Manager by Ray.

As stated, this should work with most Debian-based distros like Ubuntu or Mint and of course Debian.

---

### Post by mark-bobak on 2020-04-29
Hi,

I'm trying this with 20.04, and I'm using Chrome rather than firefox.  I've got the .so installed, and I've set the User Agenst to Firefox/Windows, and I've allowed Flash.  I'm able to fool Xfinity, at least, I get past their "Your browser isn't supported" screen, but when I choose something to watch, I get "Attempting to resume" followed by "Well, that didn't go as planned....".

Any ideas/thoughts?

-Mark

---

### Post by l33ch on 2020-05-11
> **mark-bobak said:**
> Hi,

I'm trying this with 20.04, and I'm using Chrome rather than firefox.  I've got the .so installed, and I've set the User Agenst to Firefox/Windows, and I've allowed Flash.  I'm able to fool Xfinity, at least, I get past their "Your browser isn't supported" screen, but when I choose something to watch, I get "Attempting to resume" followed by "Well, that didn't go as planned....".

Any ideas/thoughts?

-Mark


I don't. :(

I'm having the same issue too. I've tried with other user agents and browsers. I think I even tried it with a fresh live-cd and I'm getting either 'playback paused' <without ability to resume> or 'Subscription Required'. So, Comcast must have done something on their end or something, I dunno. It worked for 2 years, but it isnt now. If it's still working for other folks, I'd like to know.

---

