---
title: "New kernel available. Read this before upgrading"
date: 2006-07-11
forum: General Help
---

### Post by givré on 2006-07-11
A new kernel update (2.6.15-26) is available. Before upgrading and to not have the same problem as for the last update, it is recommanded to read this first
> ATTENTION: Due to an unavoidable ABI change the Ubuntu 6.06 kernel
update has been given a new version number, which requires you to
recompile and reinstall all third party kernel modules you might have
installed. If you use linux-restricted-modules, you have to update
that package as well to get modules which work with the new kernel
version. Unless you manually uninstalled the standard kernel
metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.
You can find the entire security notice there : [http://www.ubuntu.com/usn/usn-311-1](http://www.ubuntu.com/usn/usn-311-1)

In other words,

- To upgrade automaticly the linux-restricted-module, it's important to check that the metapackage linux-arch (where arch is the architecture of your current kernel) is install before upgrading (ie linux-386 for 2.6.15-25-386, linux-k7 for 2.6.15-25-k7 etc...check your currant kernel with 'uname -r')

- You will have to recompile all module/driver that you compiled for the previous kernel (ex: vmware, nvidia from their site...)

- If you need to recompile module or driver, and if you need the kernel headers for that, check also that you have the linux-headers-arch (where arch is the architecture of your current kernel) install.


If it's too late and you have problems at start-up, boot in recovery mode and install the kernel metapackage via apt-get:

- Check first your architecture
```
uname -r
```
- Install the metapackage
```
sudo apt-get install linux-arch #replace arch with your architecture
```

Have also a look at this: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by frodon on 2006-07-11
Stikied.

givré, could you add this link in your post : 
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

It explains how install the linux-restricted-modules and thus prevent all graphic drivers problems after the kernel update.

---

### Post by Jucato on 2006-07-11
A new kernel update? Just when my [problem](http://www.ubuntuforums.org/showthread.php?t=212787) with the last kernel hasn't been solved yet...

I'm afraid I have to sit this one out for a few days before trying to upgrade. Probably wait till the dust settles... :(

(Still hoping this new kernel would work this time...)

---

### Post by frodon on 2006-07-11
The new kernel may solve your problem, anyway all the old installed kernels will remain available so it don't prevent you to update the kernel.

That true that you were really unlucky Fenyx with the last update one month ago but most of us just never had any problems with any kernel updates in the past.
I close my eyes and hope that this kernel will solve your issue Fenyx.

BTW, did you fill a bug report ?

---

### Post by _simon_ on 2006-07-11
I upgraded before i read this but everything seems fine. This is the first time I haven't had to reinstall the nvidia drivers.... not sure why?

---

### Post by Jucato on 2006-07-11
Yep I did. 
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/49996](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/49996)
Still unresolved, and was transferred from "Affects kernel" to "Affects xorg". I'm not really sure if it's just an Xorg problem though. I'll just take the Ubuntu dev's word for it.

But if you would read the two links that I gave (in the previous post and this bug report), you'll see that I performed some tests that makes me believe that it might really be a kernel problem, or probably a kernel module problem. 

I'm really just unlucky in this particular area... So it shouldn't discourage others from upgrading and having a more secure system.

---

### Post by Raos on 2006-07-11
The system tried going through the upgrade, and it wanted to restart after, which I wasn't surprised by since it was updating the kernel.  Everything went fine during reboot, but after I entered my username and password, gnome didn't start.  It just went from the login screen to a a solid brown background with the mouse pointer, and I can't do anything. I tried updating the kernel through recovery mode, using the instructions in the first post, but it said the kernel is up to date.  I still just get the blank brown screen after login, though.

I also tried using failsafe gnome, and my normal desktop came up, but after restarting default gnome still won't start up after login.  Can anybody help fix this, or do I have to just stick to failsafe gnome?  Or do I have to re-install ubuntu?

---

### Post by givré on 2006-07-11
Do you use AIGLX or anything that need special DRI or modules?
if it works in gnome failsafe and not in normal gnome, it's probably a XGL/AIGLX/compiz problem

---

### Post by Raos on 2006-07-11
I don't think so.  How would I check if I do?  How would I fix it if that was the problem?

---

### Post by givré on 2006-07-11
The difference between a gnome session and a gnome-failsafe session is just the startup script which are not start. Check what you have in Pref>session.
Also what you can do is to start in failsafe terminal and exec gnome-session in this terminal. This will load gnome and you will have some debugging information.

---

### Post by Raos on 2006-07-11
What am I looking for in pref>sessions?  
Under the 'session options' tabs, I have Show splash screen on login checked and Ask on logout checked, Automatically save changes to session is not checked.  The only session listed is Default
Under the 'Current Session' tab, the currently running programs are  gnome-session-properties, metacity, gnome-panel, gnome-volume-manager, nautilus, update-notifier, gnome-cups-icon and stickynote_applet
Under the 'Startup Programs' tab, the additional startup programs listed are update-notifier, gnome power manager and gnome-volume-manager --sm-disable

If I exec gnome-session from a failsafe terminal, gnome starts up, and the terminal displays:
- using default device
- using default device
default: No such file or directory
/dev/dsp: No such file or directory
{then the first three lines of that repeat a few dozen times}
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
{the first three lines repeat several dozen more times}

** (gnome-session:6674): WARNING **: Esound failed to start.

Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-pane:7100): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion 'd
est_width > 0' failed
libnotify-Message: Unable to get session bus: Unable to determine the addres of
 the message bus

(gnome-panel:7100): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to alloc
ate widget with width -15 and height 24

---

### Post by givré on 2006-07-11
What you have in session is ok.
failsafe-terminal + gnome-session is equivalent to a gnome session from gdm (in fact gdm launch gnome-session), so if it run fine, i don't know what could be the problem.
Oh, do you run xgl? and if it is which method do you use. if you choose method A (choice at startup) that would be the difference.
If not, the only thing i can say is reboot.

---

### Post by Raos on 2006-07-11
I don't think I run xgl.  I searched the filesystem for xgl, it didn't find anything, and I searched synaptic for xgl, and xserver-xgl came up as not being installed, so I'm pretty sure I don't have it.

You think my only choice is to re-install dapper, because I've rebooted the computer several times now?  

Two other things, when I went to run in failsafe, the other kernel images were listed, and if I run 2.6.25-25-386 instead of 2.6.26-386 gnome starts up fine.  The other is when I run gnome-session from a failsafe terminal or failsafe gnome, it comes up with a warning that says:

Power Manager

This program cannot start until you start the dbus *session* service.

This is usually started automatically  in X or gnome startup when  you start a new session

---

### Post by Flareman on 2006-07-11
Just my 2c, I upgraded to the new kernel via Update Manager (no problems whatsoever till then) - after the reboot X crashed (due to the nvidia driver), after I restored a former xorg.conf GDM login started up, but without mouse support, the ueagle-atm module would not compile, there was no sound at all (ALSA and OSS were completely non-responsive), and the system would randomly crash either on startup or reboot. I booted the old kernel (2.6.15-25), went into Synaptic, removed the nvidia-glx packet, reinstalled all the 2.6.15-26-k7 packets (due to my ADM CPU) such as restricted-modules and headers, and did the same for the corresponding general -k7 packets. After the reinstallation (no need for any downloads, they were all in the cache) and the reboot everything is back to normal, the ueagle module went in like a charm, my DSL is back on, and everything else is back to normal... fortunately:) I will reinstall the nvidia module now, if there are any additional hickups I will keep you posted.

---

### Post by givré on 2006-07-11
@Raos: I really don't know what could be your problem, i think you should stay with the old kernel and fill a bug in launchpad  [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug). You could try to reinstall if this was a new install, but i'm not sure it will change things. Good luck, and keep us informed

---

### Post by Raos on 2006-07-11
Well, thanks for trying.  I suppose I atleast have the old kernel working to fall back on, it's definitely better than nothing.

Flareman: I don't think any of that would work for, I don't have nvidia, and my machine isn't an AMD, so I don't have any k7 packets.

---

### Post by Somenoob on 2006-07-11
[QUOTE=givré]
If it's too late and you have problems at start-up, boot in recovery mode and install the kernel metapackage via apt-get:
[/QUOTE]

how do I boot in recovrey mode?

---

### Post by givré on 2006-07-11
This should be one in your grub menu at startup, you have choice betweeen ubuntu, ubuntu recovery mode, memetest and probably more.
But if you don't have it, don't worry, just boot normaly and if it crash or whatever,just enter in a virtual terminal with Ctrl-Alt-F3. login and do the what is in the first post. Reboot and it should be ok.

---

### Post by crag277 on 2006-07-11
This may be a dumb question, but what's to gain from upgrading?  I've just recently gotten everything the way I want it (ATI driver, ndiswrapper, & XGl) and don't really want to have to go through all those steps again.

My point is will I be missing on something, such as fututre upgrades, if I just stick with the kernel I have now (2.6.15-25)?

---

### Post by Raos on 2006-07-11
speaking of the grub menu, since at least for now I'm going to be sticking with the older kernel version how do I edit the grub menu so it loads automatically, rather than the new broken kernel version?  I'd rather not have to catch the grub menu everytime I need to start up.

---

### Post by loserboy on 2006-07-11
Maybe I don't understand, but I downloaded the updates from synaptic and I didnt have to reconfigure my nvidia or anything...      so whats all this about?


Also why is mine "amd64-generic"? arent all athlon64s K8s? so couldnt i use "linux-image-2.6.10-6-amd64-k8"

---

### Post by givré on 2006-07-11
@crag277: Yeah it's a security update so it's quite important, but nobody force you to do it. Anyway, it's not that hard what you just have to do is to check that the metapackage is install, and then for every update it should upgrade properly.

@Raos: To change grub menu, you will have to edit /boot/grub/menu.lst
```
gksu gedit /boot/grub/menu.lst
```At the end you have your different entry. You can change the order like you want, and use the kernel you want by changing it in the kernel & initrd line. Keep an entry that you are sure of to be sure that you will be able to boot.

@loserboy: All that is because at the last update, many people who change their kernel to a better one (686, k7, k8...) didn't install the metapackage but only the linux-image and so we had a LOT of post of people complaigning that the new kernel was broken, but in 99 % of the case, the only problem was that the linux-restricted-module wasn't install.

---

### Post by Somenoob on 2006-07-11
Thanks,

this appears to have corrected my settings.

My video settings seem to functoning normally again, but should this metapackage have fixed all the other features that wen't wrong durring the kernel upgrade?

---

### Post by FrancoNero on 2006-07-11
are the downloads on ubuntu.com updated to reflect new versions and bug fixes? would be cool if somebody who downloads ubuntu now already has the latest kernel

---

### Post by givré on 2006-07-11
@Somenoob: linux-restricted-module contains module for nvidia/ATI card and for some wifi card. So that will solve only that kind of issue.
What are the other problem you encounter

@FrancoNero: The CD you download are still from the 1st June, there is no snapshot of the current version, but when you finish your installation, and if you have internet, you are prompt for the upgrade

---

### Post by Somenoob on 2006-07-11
> **givré said:**
> @Somenoob: linux-restricted-module contains module for nvidia/ATI card and for some wifi card. So that will solve only that kind of issue.
What are the other problem you encounter


My general speed was below the avrage, but that was most likely an effect from the entire video driver problem.

---

### Post by Bokonon on 2006-07-11
Perhaps this is not possible, but it would be better to post this type of message a few days before the kernel update was available.  I had no idea I needed to do something special before upgrading.

The directions seem like they could be a bit clearer as well.  Right now it would be nice if there was some information to check if we upgraded properly.  Not all of my systems run well with the new kernel.

FWIW, it went well on my P4 laptop and AMD-64X2 system, but it is very sluggish on my Centrino laptop.  That was true for 2.6.15-25 also.  Right now, 2.6.15-23 is the best kernel for my Centrino system.

When I get home, I will take a look at this thread and see if anything might help.  It shouldn't be too hard to reinstall.

---

### Post by kpkeerthi on 2006-07-12
Thanks for posting.. upgraded the kernel.. no apparent problems so far. Works as good as it used to be.

---

### Post by Flareman on 2006-07-12
@Crag: You don't have to upgrade to the new kernel, and it won't mess up the rest of your system (and if it does, you still have the older kernels to fix the problem) - but it's supposed to plug some guite important security holes... your cal:)

@Raos: doesn't matter whether you have an AMD or not, just reinstall the packages corresponding to your CPU architecture (k8, 386, 686, whatever - depending on your processor's make).

@Givre: actually, I already had the restricted-modules packaged installed and everything was working flawlessly - I guess something about the way that the autoupdater works was repsonsible for the mess. Anyway, after the packages' reinstallation everything is prim and proper (had a few problems with my nvidia driver but I fixed them by downloading the original .run file from their website and a sudo sh NVIDIAxxxx.run corrected everything).

---

### Post by houstonbofh on 2006-07-12
> **Raos said:**
> speaking of the grub menu, since at least for now I'm going to be sticking with the older kernel version how do I edit the grub menu so it loads automatically, rather than the new broken kernel version?  I'd rather not have to catch the grub menu everytime I need to start up.
/boot/grub/menu.lst
change *default 0* to whatever choice is correct.

And the most common cause is not installing the meta packages with a arch change.  I did a search in synaptic for "686" and "386" hit everything that was in "386" so my upgrade was unnoticed.

---

### Post by FrancoNero on 2006-07-12
> **givré said:**
> 
@FrancoNero: The CD you download are still from the 1st June, there is no snapshot of the current version, but when you finish your installation, and if you have internet, you are prompt for the upgrade

but the first post in this topic looks like it just isn't that easy to upgrade to the new kernel. or will there be no problem in a default install?

---

### Post by givré on 2006-07-12
Yeah, my post was probably too much scary. In fact, the majority of people will not have problems, and after a fresh install you will not have problems (and they don't need to read this) simply because linux-386 is install by default. But some people who install a better kernel to their processor (686, k7, k8...) forget to install the associet metapackage and so when the upgrade linux-image, they don't upgrade linux-restricted-module, which lead to the situation we encounter last time.
If you think my first post is too scary, i will change it, but i think that it's always better to prevent than fixing problems.

---

### Post by junior aspirin on 2006-07-12
i have all the correct modules and things installed, but when i boot into the latest kernel the GDM will not display, its just a blank screen with a flashing cursor. i cannot type anything, or switch to a console. the keyboard is working though, since the caps-lock key works.

i use the k7 kernel (although the default is still installed) on an amd athlon 64. ati 9800 gfx card (fglx driver was updated too). i use xgl/compiz but that is not activated on the GDM, it is set as a session when i log-in. the old kernel still works fine. any ideas on this?

---

### Post by NT4usB on 2006-07-12
fwiw, updated without problems.
Only things that broke were expected to break (ivtv, lirc, etc...)
Thanks for the heads up on that.
nbd, I'm getting good at breaking Ubuntu and fixing it!

*Happy Linux user for going on ten weeks!*

---

### Post by autocrosser on 2006-07-12
Only thing that happened to me was a funky rewrite in my grub--I have been using grub-conf & have a fair amount of custom work--I checked my menu.lst before a reboot, so I caught the changes & reset it the way it was before..no big problem---System seems about the way it was before---Pent D 820 with 3g ram.

---

### Post by Schroeder on 2006-07-12
Hi,

Yesterday I upgraded to the new 2.6.15-26 (686) kernel on my Acer Centrino Laptop (1.5Ghz, 512MB). Everything seemed fine at the first look but then I discovered that my CPU idle time went down to about 75% steadily. Something was hogging CPU power all the time and it turned out to be Mozilla Thunderbird! :???: Now, I have been using the 686 kernels 23 and 25 for a while and never had the CPU idle problems reported frequently (which are apparently related to max_cstate being a too high value). Nevertheless setting the max_cstate to 1 didnt solve my problems with the 26 kernel. 

Does anybody else have problems with especially Thunderbird and the 26 kernel?

I switched back to 2.6.15-25 and everything is fine. :-| 

Chris

---

### Post by MarkSheely on 2006-07-12
No problems with Thunderbird, but Google Earth has slowed down to an unusable crawl.  Haven't figured out the problem yet.

--Mark
[email]marksheely@gmail.com[/email]

---

### Post by Flareman on 2006-07-13
FWIW, I still had some remainder problems with nvidia - for some reason the module for the older 1.0-7177 drivers was left over and it conflicted with the new driver, crashing X at startup. I ran the NVIDIA driver installer with the --unistall option, I did "sudo apt-get --purge remove" 'd the nvidia-glx, nvidia-kernel-common, linux-restricted-common, linux-restricted-`uname-r` and so on packages, and after the whole mess was in the garbage, I reinstalled the restricted modules and nvidia-glx packages necessary for the driver.

After a restart, everything worked smooth as vanilla - and I also setup my Graphire 3, without breaking a sweat! Now, if only I could configure my USB gamepad properly...

---

### Post by Schroeder on 2006-07-13
So, I think I have figured out what my problem was: powernowd ](*,) 

a) After I uninstalled it my system runs twice as fast! 
b) I dont have anymore problems with the new kernel 2.6.15-26.

I read somewhere else that someone wanted to diable powernowd because he ran his laptop on AC all the time (like me). So I thought Id give it a try and voila: better than ever. 

Chris

---

### Post by ba5e on 2006-07-13
How do i recompile my VMWare kernel module? is it a simple command or is it a reinstall? I have the latest headers etc

---

### Post by givré on 2006-07-13
If it's vmplayer from the repo, just wait the new module.
If it's a version download from their site, you can launch 
```
sudo vmware-config.pl
```from a terminal

---

### Post by geco on 2006-07-14
I upgraded my kernel from 2.6.15-23-686 to 2.6.15-26-686 but my fglrx (ATI) driver still doesn't work.

When I did 
```

sudo apt-get install linux-686

```
I found that there is no linux-restricted-modules-2.6.15-26-686 package in official repositories. I have just linux-restricted-modules-2.6.15-23-686 package installed... maybe that's why fglrx driver doesn't work with new kernel?

---

### Post by timetunnel on 2006-07-14
linux-restricted-modules-2.6.15-26-686 is definitely there. Do you have linux-restricted-modules-686 installed? That should update to the latest version automatically.

---

### Post by geco on 2006-07-14
> **timetunnel said:**
> linux-restricted-modules-2.6.15-26-686 is definitely there. Do you have linux-restricted-modules-686 installed? That should update to the latest version automatically.

Yes I have linux-restricted-modules-686 installed but apt-get did not upgrade linux-restricted-modules-2.6.15-23-686 to linux-restricted-modules-2.6.15-26-686

I found the package searching it manually on [http://packages.ubuntu.com](http://packages.ubuntu.com) and installed it via ```
 dpkg --install linux-restricted-modules-2.6.15-26-686_2.6.15.11-3_i386.deb
```
I dont'understand why apt-get didn't install it automatically even if i did an update.

I will check if everything works on next boot.

---

### Post by geco on 2006-07-14
> **geco said:**
> Yes I have linux-restricted-modules-686 installed but apt-get did not upgrade linux-restricted-modules-2.6.15-23-686 to linux-restricted-modules-2.6.15-26-686

I found the package searching it manually on [http://packages.ubuntu.com](http://packages.ubuntu.com) and installed it via ```
 dpkg --install linux-restricted-modules-2.6.15-26-686_2.6.15.11-3_i386.deb
```
I dont'understand why apt-get didn't install it automatically even if i did an update.

I will check if everything works on next boot.

I rebooted and fglrx seems to properly work. :cool: 
=D>

\\:D/

Still don't know why apt-get didn't install linux-restricted-modules-2.6.15-26-686 :-k

---

### Post by ChicoMakani on 2006-07-14
Hello. I'm new to Ubuntu/Linux so please forgive my stupid questions.

I experienced system problems with an upgrade from 2.6.15-25-k7 to 2.6.15.26-k7.  My /boot partition filled up so the install wasn't complete.  I managed to use the grub menu to boot back into 25.  Then I uninstalled older 386 images that were there.  THis worked fine.  After that I tried a reinstall of 2.6.15-26 but had problems starting XServer.  Since I have other hardware drivers (a PVR-150 capture card) that was built against the -25 kernel, I'm really not ready to switch.

I manually edited the /boot/grub/menu.lst file so that -25 boots on startup, but I'd really like to do this correctly.  (The system is a HTPC and I don't like disconnecting it and bringing it into the office for fixes.)

Now I'd like to uninstall the -26 upgrade but when I select linux-image-2.6.15-26-k7 the system says that the following will also be removed:
  linux-restricted-modules-2.6.15-26-k7
  linux-image-k7
  linux-k7
  linux-restricted-modules-k6

I am concerned that I need the last three in order to run 2.6.15-25-k7.  Any ideas on the best way to get back to my stable configuration?

Thanks.

---

### Post by givré on 2006-07-14
> linux-image-k7
linux-k7
linux-restricted-modules-k6

are just metapackage which permet you to upgrade to a newer version, you can uninstall them safely, but you will not be prompt for the following upgrade of the kernel.

---

### Post by ChicoMakani on 2006-07-15
Perfect!  I think that's exactly what I want to do.  THanks.

---

### Post by amunimanghi on 2006-07-15
How do you boot back into the older kernel (2.6.15-26)?

---

### Post by huwshimi on 2006-07-15
It seems that the update has caused some problems with 3D. Games seem to lag every 20 seconds or so. I have talked to other people and they are having the same issue. Any ideas?

---

### Post by givré on 2006-07-15
> **amunimanghi said:**
> How do you boot back into the older kernel (2.6.15-26)?
The older kernel is 2.6.15-25
If the other kernel is always install, it should be in your grub menu

[QUOTE=xi0nblue]It seems that the update has caused some problems with 3D. Games seem to lag every 20 seconds or so. I have talked to other people and they are having the same issue. Any ideas?[/QUOTE]
It's impossible that it is due to the new kernel. If you have an nvidia or an ATI, verify that the linux-restricted-module is install for your kernel (uname -r to). If you install your driver from there website or whatever, reinstall it.

---

### Post by huwshimi on 2006-07-15
> **givré said:**
> It's impossible that it is due to the new kernel. If you have an nvidia or an ATI, verify that the linux-restricted-module is install for your kernel (uname -r to). If you install your driver from there website or whatever, reinstall it.

I tried reinstalling the driver but that didn't fix it. Booting into the previous kernel does fix it. So maybe it is possible that it is due to the new kernel. I guess we'll find out when they bring out a new one.

Cheers.

---

### Post by givré on 2006-07-15
Change that could be relevant to you
>   * i8042-x86ia64io: Blacklist IBM 2656.
  * via-agp: Add support for PT880ULTRA.
  * sundance: Added IP100A chipset support.
  * pci/quirks: VIA IRQ fixup should only run for VIA southbridges.
  * cdrom: Fix cdrom open
  * com20020_cs: Add SoHard SH ARC-PCMCIA card.
  * drm: Allow drm detection of new VIA chipsets.
  * via-ircc: Fix memory leak.
  * acpi/boot: Fix noapic for acpi.
  * acpi: Do not abort method execution if asked to release not acquired mutex.
  * ati_remote: Fix FILTER_TIME causing multiple button presses.
    - Malone #50593
  * CIFS: Fix suspend/resume problem which causes EIO on subsequent access to
    - Malone #42583
If you see one thing that could cause your problem, ok, but you should fill a bug if it is [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug).
If not or if you don't know, we will try to find a solution if you want. What is you graphic card, how did you install the driver ?

---

### Post by MrHorus on 2006-07-15
Interesting about K7/K8.

Been running the stock and then the K7 kernel on my Mobile Sempron so i'm gonna get the K8 kernel installed tonight and see if I get a little bit extra performance.

---

### Post by huwshimi on 2006-07-15
> **givré said:**
> Change that could be relevant to you

If you see one thing that could cause your problem, ok, but you should fill a bug if it is [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug).
If not or if you don't know, we will try to find a solution if you want. What is you graphic card, how did you install the driver ?

None of those changes seem relevant. The driver was just install via Apt. I have an X700 (radeon).

I appreciate the help.

---

### Post by tommcd on 2006-07-16
A couple of questions:
1) what is the "associated metapackage"? When people refer to this, do they mean the linux-restricted-modules?
2) does this warning just apply to people who have compiled their own kernel, or have installed a nvidia/ati driver from the source, instead of the one's from the repos?
3) my update went fine (dumb luck??). I am on the k-7 kernel, and have the nvidia driver (nvidia-glx) from the repos. Did the linux-restricted-modules get installed automatically?
4) is there a k-8 kernel?? I can't find it in the repos?
From now on I will check that the linux-restricted-modules are updated whenever there is a kernel update.

---

### Post by riffic on 2006-07-19
nvidia-glx isn't working for me with the 2.6.15-26-k7 kernel.. I waited until just today to upgrade since I was waiting for the vmware-player modules. 

booting with 2.6.15-25-k7 works normally.

---

### Post by givré on 2006-07-19
> **riffic said:**
> nvidia-glx isn't working for me with the 2.6.15-26-k7 kernel.. I waited until just today to upgrade since I was waiting for the vmware-player modules. 

booting with 2.6.15-25-k7 works normally.
are you sure that linux-k7 is install?
so it like that:
```
sudo apt-get install linux-k7
```
If you compile yourself the driver from their site, recompile it.
That should works.

---

### Post by givré on 2006-07-19
> **tommcd said:**
> A couple of questions:
1) what is the "associated metapackage"? When people refer to this, do they mean the linux-restricted-modules?
2) does this warning just apply to people who have compiled their own kernel, or have installed a nvidia/ati driver from the source, instead of the one's from the repos?
3) my update went fine (dumb luck??). I am on the k-7 kernel, and have the nvidia driver (nvidia-glx) from the repos. Did the linux-restricted-modules get installed automatically?
4) is there a k-8 kernel?? I can't find it in the repos?
From now on I will check that the linux-restricted-modules are updated whenever there is a kernel update.
1) the metaphage is a package which contain nothing but have dependency, and it use because of that. So if you install linux-k7 for exemple, that will install linux-image-*-k7 AND linux-restricted-module-*-k7, and will upgrade them each time you have a new kernel.
2) This warning apply for people who install a better kernel for their processor (like -k7 -686...) but forget to install the metapackage. So linux-image will be upgrade but not linux-restricted-module, and because module need to be compile for one kernel, older linux-restricted-module will not work.
And this apply also for people who compile their own module & driver
3) Hey if you had linux-k7 install :cool: 
4) Yeah no, there is no k8 kernel, my mistake... :-#

---

### Post by riffic on 2006-07-19
I ended up reinstalling the linux-image, restricted modules, and the nvidia-glx packages, restarted and it now works.

---

### Post by givré on 2006-07-20
And finaly vmare-player has been update. great :D

---

### Post by Dural on 2006-07-21
I really wish I had read this thread before trying to update the kernel in Ubuntu Dapper Drake. The last time I tried it, I ended up being unable to enter Gnome after logging in and after asking around, I decided to just to reformat the hard drive and install Kubuntu Dapper Drake. 
Later, I checked the system updates in Adept, and I noticed that the new kernel update (2.6.15-26) was available. I didn't want to make the same mistake as last time, so I'm trying to figure out how to properly update the kernel so that I don't mess up again. 
System settings:
Processor: AMD Sempron 3100+
Video Card: Nvidia GeForce 4 Ti
Memory: 1 GB
Hard Drive: 40 GB
Current Kernel: 2.6.15-23-386
a. Would it be better to install the Nvidia drivers after updating the kernel?
b. What are the safest steps to updating the kernel?

---

### Post by wifiabc on 2006-07-22
If you use update manager to update the kernel, would it take care of upgrading the dependencies as well?

---

### Post by beneban on 2006-09-11
I went to recovery mode but still it goes with the same error, kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(0,0).kindly help me with this please icant log on.

---

### Post by beneban on 2006-09-11
You can find the entire security notice there : 
i've upgraded my computer but the same problem arise, when i went to recovery mode the error message appears, Kernel panic not syncing:Unable to mount fs on unknown-block(0,0) 











[http://www.ubuntu.com/usn/usn-311-1](http://www.ubuntu.com/usn/usn-311-1)

In other words,

- To upgrade automaticly the linux-restricted-module, it's important to check that the metapackage linux-arch (where arch is the architecture of your current kernel) is install before upgrading (ie linux-386 for 2.6.15-25-386, linux-k7 for 2.6.15-25-k7 etc...check your currant kernel with 'uname -r')

- You will have to recompile all module/driver that you compiled for the previous kernel (ex: vmware, nvidia from their site...)

- If you need to recompile module or driver, and if you need the kernel headers for that, check also that you have the linux-headers-arch (where arch is the architecture of your current kernel) install.


If it's too late and you have problems at start-up, boot in recovery mode and install the kernel metapackage via apt-get:

- Check first your architecture
```
uname -r
```
- Install the metapackage
```
sudo apt-get install linux-arch #replace arch with your architecture
```

Have also a look at this: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)[/QUOTE]

---

### Post by TrinitronX on 2006-09-14
hmm... i can't get the updates... it keeps telling me it's getting 403 forbidden errors.

Did they restrict access to the webserver?

---

### Post by web250 on 2006-09-14
> **TrinitronX said:**
> hmm... i can't get the updates... it keeps telling me it's getting 403 forbidden errors.

Did they restrict access to the webserver?

Same here.

---

### Post by Dinerty on 2006-09-14
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

anything to do with this?

---

### Post by ÄlveKatt on 2006-09-15
It seems I have the network card that doesn't work after the update. I just can't connect to the servers to do the suggested fix. 

Could someone please tell me how to go about this without an internet connection?

---

### Post by Kadin2048 on 2006-09-22
> **beneban said:**
> I went to recovery mode but still it goes with the same error, kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(0,0).kindly help me with this please icant log on.

I'm having this same problem.

I had to back up to the recovery mode of the old kernel (NOT "2.6.15-26-686") in order to boot without a kernel panic, even in Recovery Mode. That kernel is just totally hosed for me, apparently.

I did this, and now I'm trying to install the linux-`uname -r` metapackage, but it's not working.

When I try to install linux-2.6.15-26-686, I get a "couldn't find" error from apt-get. I've run apt-get update, too.

Anyone have any idea why I can't install it? I have a network connection. This problem is getting very frustrating; my system is basically unusable at the moment.

---

