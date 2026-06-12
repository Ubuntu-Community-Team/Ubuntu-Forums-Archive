---
title: "bROTHER PRINTER DRIVER INSTALL FAILURE"
date: 2022-01-27
forum: General Help
---

### Post by eaglemnt on 2022-01-27
I have a glitch in my build of Ubuntu 18.04. I'd appreciate help from any who may have similar experience.

IThere is a problem loading the Brother hll2320d printer driver
Error msg;
"Sorry, something went wrong:
failed to resolve package_ids: E: The package hll2320dlpr:i386 needs to be reinstalled, but I can't find an archive for it"

 I located 4 instances of printer driver debs in Downloads and moved them to /var/cache/apt/archives successfully.
Then ran

```
sudo apt install --reinstall hll2320dlpr
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hll2320dlpr:i386 needs to be reinstalled, but I can't find an archive for it."
```

then ran
```
sudo bash linux-brprinter-installer-2.2.3-1 hll2320d
```

which produced the following log;

```
You are going to install following packages.
   hll2320dlpr-3.2.0-1.i386.deb
   hll2320dcupswrapper-3.2.0-1.i386.deb
OK? [y/N] ->y

(omit EULA)

wget -T 10 -nd --no-cache [https://download.brother.com/pub/com/linux/linux/packages/hll2320dcupswrapper-3.2.0-1.i386.deb](https://download.brother.com/pub/com/linux/linux/packages/hll2320dcupswrapper-3.2.0-1.i386.deb)
--2022-01-26 20:49:13--  [https://download.brother.com/pub/com/linux/linux/packages/hll2320dcupswrapper-3.2.0-1.i386.deb](https://download.brother.com/pub/com/linux/linux/packages/hll2320dcupswrapper-3.2.0-1.i386.deb)
Resolving download.brother.com (download.brother.com)... 104.117.232.235
Connecting to download.brother.com (download.brother.com)|104.117.232.235|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18982 (19K) [text/plain]
Saving to: &#8216;hll2320dcupswrapper-3.2.0-1.i386.deb&#8217;

hll2320dcupswrapper-3.2.0-1.i386.d 100%[================================================================>]  18.54K  --.-KB/s    in 0.008s  

2022-01-26 20:49:13 (2.33 MB/s) - &#8216;hll2320dcupswrapper-3.2.0-1.i386.deb&#8217; saved [18982/18982]

Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                                                                                    
Hit:4 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) bionic InRelease 
Hit:5 [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu) bionic InRelease                                                                  
Hit:2 [https://packagecloud.io/AtomEditor/atom/any](https://packagecloud.io/AtomEditor/atom/any) any InRelease                                     
Hit:6 [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu) xenial InRelease     
Hit:7 [http://ppa.launchpad.net/jonathonf/meson/ubuntu](http://ppa.launchpad.net/jonathonf/meson/ubuntu) bionic InRelease        
Hit:8 [http://ppa.launchpad.net/jonathonf/meson/ubuntu](http://ppa.launchpad.net/jonathonf/meson/ubuntu) xenial InRelease        
Hit:9 [http://ppa.launchpad.net/jonathonf/vlc-3/ubuntu](http://ppa.launchpad.net/jonathonf/vlc-3/ubuntu) bionic InRelease        
Hit:10 [http://ppa.launchpad.net/jonathonf/vlc-3/ubuntu](http://ppa.launchpad.net/jonathonf/vlc-3/ubuntu) xenial InRelease       
Reading package lists... Done                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hll2320dlpr:i386 needs to be reinstalled, but I can't find an archive for it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hll2320dlpr:i386 needs to be reinstalled, but I can't find an archive for it.
dpkg -x hll2320dlpr-3.2.0-1.i386.deb /
dpkg -x hll2320dcupswrapper-3.2.0-1.i386.deb /
(Reading database ... 224407 files and directories currently installed.)
Removing hll2320dcupswrapper:i386 (3.2.0-1) ...
Purging configuration files for hll2320dcupswrapper:i386 (3.2.0-1) ...
dpkg-deb: building package 'hll2320dlpr' in 'hll2320dlpr-3.2.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir hll2320dlpr-3.2.0-1a.i386.deb
dpkg-deb: building package 'hll2320dcupswrapper' in 'hll2320dcupswrapper-3.2.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir hll2320dcupswrapper-3.2.0-1a.i386.deb
dpkg -i --force-all hll2320dlpr-3.2.0-1a.i386.deb
(Reading database ... 224405 files and directories currently installed.)
Preparing to unpack hll2320dlpr-3.2.0-1a.i386.deb ...
Unpacking hll2320dlpr:i386 (3.2.0-1) over (3.2.0-1) ...
dpkg: warning: old hll2320dlpr:i386 package post-removal script subprocess returned error exit status 5
dpkg: trying script from the new package instead ...
dpkg: error processing archive hll2320dlpr-3.2.0-1a.i386.deb (--install):
 new hll2320dlpr:i386 package post-removal script subprocess returned error exit status 5
dpkg: error while cleaning up:
 new hll2320dlpr:i386 package post-removal script subprocess returned error exit status 5
Errors were encountered while processing:
 hll2320dlpr-3.2.0-1a.i386.deb
dpkg -i --force-all hll2320dcupswrapper-3.2.0-1a.i386.deb
Selecting previously unselected package hll2320dcupswrapper:i386.
(Reading database ... 224405 files and directories currently installed.)
Preparing to unpack hll2320dcupswrapper-3.2.0-1a.i386.deb ...
Unpacking hll2320dcupswrapper:i386 (3.2.0-1) ...
Setting up hll2320dcupswrapper:i386 (3.2.0-1) ...
lpadmin -p HLL2320D -E -v usb://Brother/HL-L2320D%20series?serial=U63877K6N185660 -P /usr/share/ppd/brother/brother-HLL2320D-cups-en.ppd
#
Will you specify the Device URI? [Y/n] ->n
```


This install glitch has effectively halted not only the printer install but all installs of other programs and upgrade to 20.04.

I would greatly appreciate help with this issue.

---

### Post by ActionParsnip on 2022-01-27
What is the output of:
```

lsb_release -a; uname -a

```

Thanks

---

### Post by SeijiSensei on 2022-01-27
Go to the Brother support page for your printer and download the "Driver Install Tool." That's a bash script that should detect the printer and download and install the appropriate drivers. As I recall you'll need to mark it executable before you can run it.

---

### Post by eaglemnt on 2022-01-27
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic
Linux BOX-1 4.15.0-135-generic #139-Ubuntu SMP Mon Jan 18 17:38:24 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by eaglemnt on 2022-01-27
I have done this.  The output (above ) is the result of running the bash script.
Thanks for your attention to this

---

### Post by deadflowr on 2022-01-27
Run
```
dpkg -l | grep hll2320
```
it should gives us the status of the package(s) as it/they stand.
> I located 4 instances of printer driver debs in Downloads and moved them to /var/cache/apt/archives successfully.
That in and out itself does nothing.
As the packages would also need to be in the proper list files as well; among other things.

My general quick assessment would be you'll need to do a force purge of the related packages, and then try reinstalling them from there.

---

### Post by oldfred on 2022-01-27
See also:
[https://ubuntuforums.org/showthread.php?t=2468600&page=2](https://ubuntuforums.org/showthread.php?t=2468600&page=2)

Are you using 32 bit system?
I would think an i386 driver is for 32 bit systems. Most are 64 bit now.

---

### Post by eaglemnt on 2022-01-27
Done! 

$ dpkg -l | grep hll2320
ii  hll2320dcupswrapper:i386                   3.2.0-1                                          i386         Brother HL-L2320D CUPS wrapper driver
iHR hll2320dlpr:i386                           3.2.0-1                                          i386         Brother HL-L2320D LPR driver

 Thanks

---

### Post by eaglemnt on 2022-01-27
64 bit system!

$ uname -a
Linux BOX-1 4.15.0-135-generic #139-Ubuntu SMP Mon Jan 18 17:38:24 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Thanks

---

### Post by eaglemnt on 2022-01-27
Force purge?
Can you direct me to a process for this?
Thanks, Deadflower.

---

### Post by deadflowr on 2022-01-27
The package status shows its in a very bad state and can only be removed with a force command like so
```
sudo dpkg --remove --force-remove-reinsterq hll2320dlpr:i386
``` 
You can general references for this all over the place, but here's one anyway: [https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error]("https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error")

Being that the package is both 
1) From an outside source
and 
2) 32-bit
it is unclear what is right or wrong.

So proceed with caution.

---

### Post by eaglemnt on 2022-01-28
Thanks for this and the cautionary note.  :)

---

