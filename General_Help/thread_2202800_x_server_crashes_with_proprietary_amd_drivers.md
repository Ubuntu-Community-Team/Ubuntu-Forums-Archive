---
title: "x server crashes with proprietary amd drivers"
date: 2014-01-31
forum: General Help
---

### Post by Krackly on 2014-01-31
Hello everyone.
I have ubuntu 13.10 and amd radeon 4850 graphic card. I used open driver and it worked fine, but I wanted extra features and installed proprietary amd driver. I used that manual [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) , exactly part 3.1. Everything went fine as in the manual, I just changed the ubuntu version name and installed requested packages. But after reboot I can see with graphics only login screen, after login it swithes to the login screen back. I can login only with terminal, and when I do "startx" it crashes. Here is extras from my Xorg.1.log file, what is failed:
> 
[   674.097] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   674.160] (EE) Failed to load /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension
[   674.160] (II) UnloadModule: "fglrx"
[   674.160] (II) Unloading fglrx
[   674.160] (EE) Failed to load module "fglrx" (loader failed, 7)


> [   675.994] (EE) Backtrace:
[   675.995] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb777afc9]
[   675.995] (EE) 1: /usr/bin/X (0xb75da000+0x1a4d34) [0xb777ed34]
[   675.995] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb75b740c]
[   675.995] (EE) 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so (0xb6c37000+0x12556) [0xb6c49556]
[   675.995] (EE) 4: /usr/bin/X (0xb75da000+0x3c5fd) [0xb76165fd]
[   675.995] (EE) 
[   675.995] (EE) Segmentation fault at address 0x1000001

> [   675.995] (EE) Caught signal 11 (Segmentation fault). Server aborting

> [   677.418] (EE) Server terminated with error (1). Closing log file.

I can attach the whole log file if needed. 

I serched and found that proprietary drivers might be not supporting new versions of the xserver. Than I would not can to use proprietary driver? So what can I do, just delete fglrx ang use open driver? Or can I install classic gnome instead of unity to make it work? Or there are other ways?

---

### Post by Mark Phelps on 2014-01-31
The binary how-to does not apply in your case because AMD dropped support for the restricted AMD drivers for their HD 2x/3x/4x-series cards last summer.  Those drivers will not work with any Ubuntu version newer than 12.04.1.  You have to remove the fglrx drivers and replace them with the open source Radeon drivers.  Instructions for doing that are in the linked material: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by QIII on 2014-01-31
I'll try to make a note of that in the wiki this weekend ... and clean up some other crud that has built up and is no longer applicable.

---

### Post by Krackly on 2014-02-01
Hello and thanks for replying.
Then, what I did. Firstly I desided to give the last chance to the proprietary driver and tryed to use patched driver from ppa:makson96/fglrx. I added ppa and made apt-get update and apt-get upgrade and tryed to install fglrx-legacy but that was not found. After rebooting I couldn't even see the login screen, system just tryed to load in a safe graphics mode but couldn't and turned into terminal. Than I deleted the ppa, made update and upgrade and after it deleted fglrx with command "apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*" and "apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri" and "dpkg-reconfigure xserver-xorg" and after reboot I could see the login screen, but as earlier could not login, entered the terminal I did "startx" and surprisingly it started after some time, but only desktop without any unity features. I could make a folder, enter it to start nautilus, searched for the terminal emulator, run it, type "unity" and it started. Everything looked nice except the top panel, it had no elements. After it I rebooting and still now I cant enter graphics, only login screen, and when I enter console and type startx the screen just became black and nothing appears. 
Then I did everything like in this manual [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) Another time do commands deleting fglrx and reinstalling xserver, but nothing changes.
When I do command "dmesg | egrep 'drm|radeon' it shows a long report looking like driver and video adapter is working properly. 
But when i do "LIBGL_DEBUG=verbox glxinfo" it says "unable to open display"
So I think that the driver works fine but something wrong with the xserver. How can I fully reinstall it or somehow fix it?

---

### Post by Krackly on 2014-02-01
Now I have it working. I just deleted all authority files and now it running as usual. Except one thing - now it takes much more time for system to boot and to login, than before I tryed to install proprietary driver. When ubuntu boots I see the violet screen for about 10 second and after that ubuntu logo and orange points for about 2 seconds. I'm not sure if before it took less time but it was more time for logo and less for violet screen exactly. Also when I login, screen is black for about 2 seconds, than it's black with the cursor also about 2 seconds, and only then desktop appears. Before it was just one moment. Can I fix it somehow?

---

### Post by Mark Phelps on 2014-02-01
> Can I fix it somehow? 

Fix WHAT? Nothing is "broken" -- it's just a long wait to get to a desktop.  

There are utilities you can Google for, install, and use them to list out all the tasks that are loaded as part of startup and see how long each is taking -- but that is a LOT of work and generally results in very little improvement.

I too, got tired of the waiting and opted for a different solution -- an SSD.  SO now, my boot-to-desktop time went from around a minute to under 5 seconds.

---

### Post by Krackly on 2014-02-03
> Fix WHAT? Nothing is "broken" -- it's just a long wait to get to a desktop.
hah, I'm just not so good at english, sorry. I meant make it better.

What about the problem, I'm sure that login time was much faster before this story with driver, almost instantly (about boot time before login screen I'm not so sure). And I know that during xserver was fail to start I didn't install any apps excluding reinstalling the xserver. That's why I think it's not because of autostart apps or low hdd speed. I think that something might be wrong with xserver configuration... But I'd better won't touch it anymore. 
I learned how backup before doing something with system is important.

---

### Post by Mark Phelps on 2014-02-03
> I learned how backup before doing something with system is important. 

Would be nice if other folks showed the same high degree of common sense as you have.

A good backup tool is Clonezilla, but it can be difficult to use because of the great number of settings.

If you want an nice easy-to-use GUI, look into RedoBackup.

---

