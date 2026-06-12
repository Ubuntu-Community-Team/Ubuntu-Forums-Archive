---
title: "Strange Boot/Lockup issues"
date: 2017-06-28
forum: General Help
---

### Post by aviator1 on 2017-06-28
Hello All:

This just started a few days ago.

Upon boot up, I can open programs such as Thunderbird, Firefox, LibreOffice 5, but cannot navigate anywhere. Thunderbird will auto download emails, but I cannot open anything.

I usually have to reboot 2 or 3 times before I can get anything to work. Seems to work OK after all the reboots.

System Monitor shows RAM usage at about 1.1 GB, never higher and an occasional blip on CPU and Internet usage.

I did have one of those strange scam popups a few days ago telling me my windows was infected and was sending all my financial data to someone. Had to hard reset to get rid of it.

Thanks for any ideas.

---

### Post by aviator1 on 2017-06-28
What does the green check mark and green symbol over the email icon mean?

Thanks

EDIT: Never mind I figured it out.

---

### Post by aviator1 on 2017-06-30
If anyone can help, I would really be thankful.

The problem seems to be getting worse. Had to boot 4 times in order to be able to navigate here. Was able to open System Monitor, but could not close it with the "X". Had to use the menu bar.

Was able to open a an Open Office spreadsheet, but could not navigate.

2 soft boots, 1 hard boot, and a soft boot got it working.

Any ideas?

---

### Post by aviator1 on 2017-07-01
Dear Friends:

I posted a few days ago about some strange boot up/lock up issues. Well, things have taken a turn for the worse.

It took 8 reboots this morning to be ale to have limited navigation. 5 soft reboots and 3 power  off/power on reboots.

Right now, I can navigate in Firefox, but all my other icons (Thunderbird, LibreOffice Calc, System, Home, etc, are all locked and unusable. I have no Menu bar at the top of the page.

I cannot open the icon, which would allow me to get to Terminal right now.

On some of the previous reboots, I would sometimes be able to open a spreadsheet (22kb). As soon as I closed it, everything was locked. System Monitor would show some CPU activity when opening the spreadsheet.

I would deeply appreciate any help. This is a dual boot machine, and the Windows side works fine.

Thanks.

---

### Post by vasa1 on 2017-07-01
BUMP!

OP, it's better to continue posting on the same issue here. That way, all the new, related information is in one thread for people to assess.

For starters, please tell us more about your system. Can you run *sudo apt-get update* and *sudo apt-get upgrade* without issues?

---

### Post by aviator1 on 2017-07-01
Sorry  for the other post. I saw no activity here, and did not know if anyone was seeing it.

I cannot do anything right now except linited navigation on Firefox. I can't open the icon, which allows me to get to terminal. Are there key strokes/combinations, which would get me there?

Thanks.

EDIT: I remembered how to do it. I was able to run *sudo apt-get update* and *sudo apt-get upgrade* without issues. Should I try a reboot?

---

### Post by aviator1 on 2017-07-01
After running sudo apt-get update and sudo apt-get upgrade, my icons were active, but I could not close anything from the "X". Can only close from the menu bar. The menu bar has now disappeared again, and the icons are frozen again

I have not rebooted.

Further info....Ran sudo apt-get update and sudo apt-get upgrade again. Menu bar came back, and icons will open a program. Still cannot close any program with "X". Only from the menu bar.

Thunderbird email will open and download, but I cannot navigate at all.

SPOKE TOO SOON. All are locked again.

Thanks for any help.

---

### Post by aviator1 on 2017-07-01
Follow up. I ran sudo apt-get update and sudo apt-get upgrade again, and the menu bar came back and I was able to navigate in Thunderbird, but Firefox and this page was locked.

I am back to having everything locked except limited navigation here. Running sudo apt-get update and sudo apt-get upgrade seems to open things up some.

---

### Post by vasa1 on 2017-07-01
> **aviator1 said:**
> Sorry  for the other post. I saw no activity here, and did not know if anyone was seeing it.

...
No problem. The view count may still be messed up and not reflect how many people have actually seen your thread.

You could bump this post once every 12 hours to catch folks in other time zones.

So you saw no errors when running the update and upgrade commands?

Are you using Unity or something else? 

Did you do anything out of the way?

[s]How old is your machine?[/s]

What is the output of ```
df -h
```?

Do you see anything with ```
dpkg -C
```?

Can you associate the start of your problems with an update to your graphics?

---

### Post by aviator1 on 2017-07-01
Thanks very much for your reply. I tried a reboot with no help. I rebooted again and went to advanced/recovery and selected "Fix"

That seems to have solved the problem. I have rebooted twice now, and everything seems to be working.

Here are the items you requested:

```
dave@dave-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.8M  1.6G   1% /run
/dev/sda6       102G   57G   40G  60% /
tmpfs           7.8G  320K  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   76K  1.6G   1% /run/user/1000
```

I get nothing when I request dpkg -C

Do not know what Unity is.

Have made no changes other that the upgrades when they appear. last one was well before all this started.

Thanks for your help.

---

### Post by vasa1 on 2017-07-01
> **aviator1 said:**
> ...
Do not know what Unity is.
...
Don't say that out aloud! It's the default shell or something in Ubuntu!

Anyway, nice to know you're sorted.

If nothing horrible happens for a few days, please come back and mark this thread [SOLVED] as described in [How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by aviator1 on 2017-07-01
Thanks for your reply. I will look up the unity thing, so that I do not commit another faux pas.......

Will mark the thread if all goes well.

I appreciate your responses. This is a great community.

---

### Post by CatKiller on 2017-07-01
> **vasa1 said:**
> Don't say that out aloud! It's the default shell or something in Ubuntu!

It's actually been discontinued. The next LTS will be just Gnome.

---

### Post by aviator1 on 2017-07-01
I spoke too soon, again.

I shut down and went off for a couple of hours. I am now back to the same scenario.

When I open Firefox, I can only navigate with the Firefox menu bar. I have no access to to the minimize, maximize, or close buttons.

Also, I did make a mistake. I did change an NVidia driver a few days ago, but I think this issue was already beginning.

I cannot access the system icon while Firefox is open. I can when the desktop shows up, but then I cannot access the software update icon.

I really appreciate any help.

Regards.

---

### Post by aviator1 on 2017-07-01
And the adventure continues......I seem to be all sorted out again.......for now......

After a few reboots, I was able to access System Setting/Additional Drivers, and changed back to the NVidia driver I had previously.

I have not shut down for any period of time, but have rebooted with not navigation issues.

Will post later if I am still in trouble, or hopefully to report thread as solved.

Regards.

---

### Post by aviator1 on 2017-07-02
Well, back in the battle.

After shutting down for a few hours, I booted up and had some basic navigation with the mouse and menus. After 2 resrts, all is normal

Shut down again for a few hours. Same scenario, Can open Thunderbird, and it downloads. No navigation. Firefox will ope with mouse, but can only navigate with the menu selections. After 2 restarts, all is normal.

At least I am not having to do hard shut downs.

Any help is greatly appreciated.

Regards.

---

### Post by aviator1 on 2017-07-03
Any help is greatly appreciated.

FWIW, I have tried to donate to one of my charities. When I click on the donate button, I get a scam message about microsoft has found a red square warning, and all my financial info is being sent somewhere. I have to reboot at least twice to get rid of the warning. The next time I click on the donate button, it works fine.

I reported this to the charity, and they tested on several different computers and had no problems.

Is a virus a possibility?

Thanks for any help.

---

### Post by CatKiller on 2017-07-03
> **aviator1 said:**
> Is a virus a possibility?

Not really, no. Clearing your Firefox cache may help if you're getting lots of things like that.

You've not really given us a lot to go on. You installed a graphics driver update at some point? And you're having some trouble interacting with UI elements sometimes now? That's as much as I've managed to glean from your posts.

Does the X.org log (/var/log/Xorg.o.log) say anything useful between when it works and when it doesn't? Have you tried using an earlier/later version of your graphics driver, or the nouveau driver if you're using the proprietary one?

---

### Post by aviator1 on 2017-07-03
> **CatKiller said:**
> Not really, no. Clearing your Firefox cache may help if you're getting lots of things like that.

You've not really given us a lot to go on. You installed a graphics driver update at some point? And you're having some trouble interacting with UI elements sometimes now? That's as much as I've managed to glean from your posts.

Does the X.org log (/var/log/Xorg.o.log) say anything useful between when it works and when it doesn't? Have you tried using an earlier/later version of your graphics driver, or the nouveau driver if you're using the proprietary one?

Thanks for your reply.

I had gone to NVidia and downloaded/installed their latest driver. When the troubles began, I reverted to the previous driver, and things seem to have cleared up a bit.

As of now, when I first bootup, I can open Thunderbird, and it will download emails. I can only navigate using the menu selections. Mouse clicks do nothing, except I can close the program using the "X" selection.

The same thing happens when I open Firefox. Also, if I open System Monitor, the computer freezes for a minute or so, and I can close SM using the menu bar commands using mouse clicks.

I am able to open a spreadsheet, navigate with the mouse, save and close.

If I restart, everything seems to work normally.

I have run sudo apt-get update and sudo apt-get upgrade

I do not know what X.org log (/var/log/Xorg.o.log) is. Please advise how to find it.

I appreciate any help.

Regards.

---

### Post by CatKiller on 2017-07-03
> **aviator1 said:**
> I had gone to NVidia and downloaded/installed their latest driver. 

It's not generally recommended to do that. It's easier and safer to install the proprietary drivers through the package manager.

> When the troubles began, I reverted to the previous driver, and things seem to have cleared up a bit.

And how did you do that?

> I do not know what X.org log (/var/log/Xorg.o.log) is. Please advise how to find it.

It's the log file for Xorg. It's at /var/log/Xorg.0.log. I don't know what else to tell you about it. It's long and boring, and it's where errors about your graphics system are put.

---

### Post by aviator1 on 2017-07-04
During the period, a few days ago, when I was having to reboot several times to get operational, I was finally able to navigate to System/Software Updates/Additional Drivers. I changed back to the driver, which was working before all this started.

There was an immediate improvement.

As of right now, I am on my first bootup. I can open Firefox with the mouse, but had to use the menu bar selections to open this bookmark.

As of right now, no other program will open. I cannot move anywhere, or do anything except right here.

Thanks for any help.

UPDATE: I am still on my first boot. If I close Firefox, and reopen, I cannot use any link on the menu bar. As soon as I click on bookmarks, all the menu bar links become available.

If I have Firefox open, then no icon on the sidebar is active.

When I close this page, I can open Thunderbird. After a minute or so, it appears I have limited navigation in Thunderbird. I have to close it from the menu selections.

UPDATE-2 Just rebooted and everything is working normally, Navigation with the mouse is normal and I can open multiple programs.

---

### Post by aviator1 on 2017-07-04
So, here is the latest that i have discovered.

Upon the first start, I can only open 1 program at a time. 

Upon the first start, when I open Firefox, the toolbar menu links are dead. If I click on any menu selection at the top, say Favorites, the screen bumps slightly downward and all the toolbar menu links are immediately available.

Upon the first start, I can open Thunderbird, and it will download emails. No navigation until I select something on the menu, say Open a new email. Still have to close using a menu selection instead of the"X"

Upon the restart, everything is back to normal.

Could something be going on in the boot process?

Thanks for any answers.

Regards.

---

### Post by CatKiller on 2017-07-04
You've still not said what's going on with your logs. We still don't know that you cleared out any cruft from when you (potentially) used the nvidia installer from their website, or if you just installed over the top, or what.

---

### Post by aviator1 on 2017-07-05
> **CatKiller said:**
> You've still not said what's going on with your logs. We still don't know that you cleared out any cruft from when you (potentially) used the nvidia installer from their website, or if you just installed over the top, or what.

Thanks very much for your reply. I am back to using the open source NVidia driver, which was working fine last week.

As of today's first boot up, everything worked normally. I shut down completely, and booted up again with no issues.

I didn't post anything, as I do not know what X.org log (/var/log/Xorg.o.log) are, where they are located, or what to look for.

Before getting into those, let me see how the boot ups go for the next day or so. If things go bad, I will repost here.

Thanks very much for your time and responses.

Regards

---

### Post by CatKiller on 2017-07-05
> **aviator1 said:**
> Thanks very much for your reply. I am back to using the open source NVidia driver, which was working fine last week.

As of today's first boot up, everything worked normally. I shut down completely, and booted up again with no issues.

I didn't post anything, as I do not know what X.org log (/var/log/Xorg.o.log) are, 


> **CatKiller said:**
> It's the log file for Xorg. It's long and boring, and it's where errors about your graphics system are put.

> where they are located,

> **CatKiller said:**
> It's at /var/log/Xorg.0.log.

> or what to look for.

> **CatKiller said:**
> Does the X.org log (/var/log/Xorg.0.log) say  anything useful between when it works and when it doesn't?

Hopefully not using any nvidia driver will continue to work for you.

---

### Post by aviator1 on 2017-07-05
Thanks for your response. Following are the logs.

```
[     5.276] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     5.276] X Protocol Version 11, Revision 0
[     5.276] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     5.276] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     5.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     5.276] Build Date: 02 November 2016  10:06:10PM
[     5.276] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.276] Current version of pixman: 0.33.6
[     5.276]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.276] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.276] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  5 13:13:35 2017
[     5.276] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.277] (==) No Layout section.  Using the first Screen section.
[     5.277] (==) No screen section available. Using defaults.
[     5.277] (**) |-->Screen "Default Screen Section" (0)
[     5.277] (**) |   |-->Monitor "<default monitor>"
[     5.277] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.277] (==) Automatically adding devices
[     5.277] (==) Automatically enabling devices
[     5.277] (==) Automatically adding GPU devices
[     5.277] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.277] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.278]     Entry deleted from font path.
[     5.278] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.278]     Entry deleted from font path.
[     5.278] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.278]     Entry deleted from font path.
[     5.278] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.278]     Entry deleted from font path.
[     5.278] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.278]     Entry deleted from font path.
[     5.278] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.278] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.278] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.278] (II) Loader magic: 0x555d68669dc0
[     5.278] (II) Module ABI versions:
[     5.278]     X.Org ANSI C Emulation: 0.4
[     5.278]     X.Org Video Driver: 20.0
[     5.278]     X.Org XInput driver : 22.1
[     5.278]     X.Org Server Extension : 9.0
[     5.278] (++) using VT number 7

[     5.278] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.278] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.279] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.279] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     5.280] (II) "glx" will be loaded by default.
[     5.280] (II) LoadModule: "glx"
[     5.280] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.324] (II) Module glx: vendor="NVIDIA Corporation"
[     5.324]     compiled for 4.0.2, module version = 1.0.0
[     5.324]     Module class: X.Org Server Extension
[     5.324] (II) NVIDIA GLX Module  381.22  Thu May  4 00:17:15 PDT 2017
[     5.324] (==) Matched nvidia as autoconfigured driver 0
[     5.324] (==) Matched nouveau as autoconfigured driver 1
[     5.324] (==) Matched nvidia as autoconfigured driver 2
[     5.324] (==) Matched nouveau as autoconfigured driver 3
[     5.324] (==) Matched modesetting as autoconfigured driver 4
[     5.324] (==) Matched fbdev as autoconfigured driver 5
[     5.324] (==) Matched vesa as autoconfigured driver 6
[     5.324] (==) Assigned the driver to the xf86ConfigLayout
[     5.324] (II) LoadModule: "nvidia"
[     5.324] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.327] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.328]     compiled for 4.0.2, module version = 1.0.0
[     5.328]     Module class: X.Org Video Driver
[     5.328] (II) LoadModule: "nouveau"
[     5.328] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.329] (II) Module nouveau: vendor="X.Org Foundation"
[     5.329]     compiled for 1.18.1, module version = 1.0.12
[     5.329]     Module class: X.Org Video Driver
[     5.329]     ABI class: X.Org Video Driver, version 20.0
[     5.329] (II) LoadModule: "modesetting"
[     5.330] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.330] (II) Module modesetting: vendor="X.Org Foundation"
[     5.330]     compiled for 1.18.4, module version = 1.18.4
[     5.330]     Module class: X.Org Video Driver
[     5.330]     ABI class: X.Org Video Driver, version 20.0
[     5.330] (II) LoadModule: "fbdev"
[     5.330] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.330] (II) Module fbdev: vendor="X.Org Foundation"
[     5.330]     compiled for 1.18.1, module version = 0.4.4
[     5.330]     Module class: X.Org Video Driver
[     5.330]     ABI class: X.Org Video Driver, version 20.0
[     5.330] (II) LoadModule: "vesa"
[     5.330] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.330] (II) Module vesa: vendor="X.Org Foundation"
[     5.330]     compiled for 1.18.1, module version = 2.3.4
[     5.330]     Module class: X.Org Video Driver
[     5.330]     ABI class: X.Org Video Driver, version 20.0
[     5.330] (II) NVIDIA dlloader X Driver  381.22  Wed May  3 23:53:41 PDT 2017
[     5.330] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.330] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.330] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.330]     RIVA TNT        (NV04)
[     5.330]     RIVA TNT2       (NV05)
[     5.330]     GeForce 256     (NV10)
[     5.331]     GeForce 2       (NV11, NV15)
[     5.331]     GeForce 4MX     (NV17, NV18)
[     5.331]     GeForce 3       (NV20)
[     5.331]     GeForce 4Ti     (NV25, NV28)
[     5.331]     GeForce FX      (NV3x)
[     5.331]     GeForce 6       (NV4x)
[     5.331]     GeForce 7       (G7x)
[     5.331]     GeForce 8       (G8x)
[     5.331]     GeForce GTX 200 (NVA0)
[     5.331]     GeForce GTX 400 (NVC0)
[     5.331] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.331] (II) FBDEV: driver for framebuffer: fbdev
[     5.331] (II) VESA: driver for VESA chipsets: vesa
[     5.332] (II) Loading sub module "fb"
[     5.332] (II) LoadModule: "fb"
[     5.332] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.332] (II) Module fb: vendor="X.Org Foundation"
[     5.332]     compiled for 1.18.4, module version = 1.0.0
[     5.332]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.332] (II) Loading sub module "wfb"
[     5.332] (II) LoadModule: "wfb"
[     5.332] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.333] (II) Module wfb: vendor="X.Org Foundation"
[     5.333]     compiled for 1.18.4, module version = 1.0.0
[     5.333]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.333] (II) Loading sub module "ramdac"
[     5.333] (II) LoadModule: "ramdac"
[     5.333] (II) Module "ramdac" already built-in
[     5.335] (WW) Falling back to old probe method for modesetting
[     5.335] (WW) Falling back to old probe method for fbdev
[     5.335] (II) Loading sub module "fbdevhw"
[     5.335] (II) LoadModule: "fbdevhw"
[     5.335] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.335] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.335]     compiled for 1.18.4, module version = 0.0.2
[     5.335]     ABI class: X.Org Video Driver, version 20.0
[     5.335] (WW) Falling back to old probe method for vesa
[     5.335] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.335] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.335] (==) NVIDIA(0): RGB weight 888
[     5.335] (==) NVIDIA(0): Default visual is TrueColor
[     5.335] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.336] (**) NVIDIA(0): Enabling 2D acceleration
[     5.687] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     5.687] (--) NVIDIA(0):     CRT-0
[     5.688] (--) NVIDIA(0):     DFP-0 (boot)
[     5.688] (--) NVIDIA(0):     DFP-1
[     5.689] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     5.689] (--) NVIDIA(0): Memory: 4194304 kBytes
[     5.689] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.56
[     5.689] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     5.690] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     5.690] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     5.690] (--) NVIDIA(GPU-0): 
[     5.701] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     5.701] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     5.701] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     5.701] (--) NVIDIA(GPU-0): 
[     5.701] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     5.701] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     5.701] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     5.701] (--) NVIDIA(GPU-0): 
[     5.704] (==) NVIDIA(0): 
[     5.704] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     5.704] (==) NVIDIA(0):     will be used as the requested mode.
[     5.704] (==) NVIDIA(0): 
[     5.704] (II) NVIDIA(0): Validated MetaModes:
[     5.704] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     5.704] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     5.714] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     5.714] (--) NVIDIA(0):     option
[     5.714] (II) UnloadModule: "nouveau"
[     5.714] (II) Unloading nouveau
[     5.714] (II) UnloadModule: "modesetting"
[     5.714] (II) Unloading modesetting
[     5.714] (II) UnloadModule: "fbdev"
[     5.714] (II) Unloading fbdev
[     5.714] (II) UnloadSubModule: "fbdevhw"
[     5.714] (II) Unloading fbdevhw
[     5.714] (II) UnloadModule: "vesa"
[     5.714] (II) Unloading vesa
[     5.714] (--) Depth 24 pixmap format is 32 bpp
[     5.715] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.715] (II) NVIDIA:     access.
[     5.738] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     5.791] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.791] (==) NVIDIA(0): Backing store enabled
[     5.791] (==) NVIDIA(0): Silken mouse enabled
[     5.792] (==) NVIDIA(0): DPMS enabled
[     5.793] (II) Loading sub module "dri2"
[     5.793] (II) LoadModule: "dri2"
[     5.793] (II) Module "dri2" already built-in
[     5.793] (II) NVIDIA(0): [DRI2] Setup complete
[     5.793] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.793] (--) RandR disabled
[     5.797] (II) SELinux: Disabled on system
[     5.798] (II) Initializing extension GLX
[     5.798] (II) Indirect GLX disabled.
[     5.849] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.849] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.849] (II) LoadModule: "evdev"
[     5.850] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.852] (II) Module evdev: vendor="X.Org Foundation"
[     5.852]     compiled for 1.18.1, module version = 2.10.1
[     5.852]     Module class: X.Org XInput Driver
[     5.852]     ABI class: X.Org XInput driver, version 22.1
[     5.852] (II) Using input driver 'evdev' for 'Power Button'
[     5.852] (**) Power Button: always reports core events
[     5.852] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.852] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.852] (--) evdev: Power Button: Found keys
[     5.852] (II) evdev: Power Button: Configuring as keyboard
[     5.852] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.852] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.852] (**) Option "xkb_rules" "evdev"
[     5.852] (**) Option "xkb_model" "pc105"
[     5.852] (**) Option "xkb_layout" "us"
[     5.852] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.852] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.852] (II) Using input driver 'evdev' for 'Power Button'
[     5.852] (**) Power Button: always reports core events
[     5.852] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.852] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.852] (--) evdev: Power Button: Found keys
[     5.852] (II) evdev: Power Button: Configuring as keyboard
[     5.852] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.852] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.852] (**) Option "xkb_rules" "evdev"
[     5.852] (**) Option "xkb_model" "pc105"
[     5.852] (**) Option "xkb_layout" "us"
[     5.853] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.853] (II) No input driver specified, ignoring this device.
[     5.853] (II) This device may have been added with another device file.
[     5.853] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.853] (II) No input driver specified, ignoring this device.
[     5.853] (II) This device may have been added with another device file.
[     5.853] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.853] (II) No input driver specified, ignoring this device.
[     5.853] (II) This device may have been added with another device file.
[     5.854] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.854] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.854] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.854] (**) Logitech M570: always reports core events
[     5.854] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.854] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.854] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.854] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.854] (--) evdev: Logitech M570: Found relative axes
[     5.854] (--) evdev: Logitech M570: Found x and y relative axes
[     5.854] (II) evdev: Logitech M570: Configuring as mouse
[     5.854] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.854] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.854] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.854] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.854] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.854] (II) evdev: Logitech M570: initialized for relative axes.
[     5.854] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.854] (**) Logitech M570: (accel) acceleration profile 0
[     5.854] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.854] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.854] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.854] (II) No input driver specified, ignoring this device.
[     5.854] (II) This device may have been added with another device file.
[     5.855] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.855] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.855] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.855] (**) Logitech K360: always reports core events
[     5.855] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.855] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.855] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.855] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.855] (--) evdev: Logitech K360: Found relative axes
[     5.855] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.855] (--) evdev: Logitech K360: Found absolute axes
[     5.855] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.855] (--) evdev: Logitech K360: Found keys
[     5.855] (II) evdev: Logitech K360: Configuring as mouse
[     5.855] (II) evdev: Logitech K360: Configuring as keyboard
[     5.855] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.855] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.855] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.855] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.855] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.855] (**) Option "xkb_rules" "evdev"
[     5.855] (**) Option "xkb_model" "pc105"
[     5.855] (**) Option "xkb_layout" "us"
[     5.855] (II) evdev: Logitech K360: initialized for relative axes.
[     5.855] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.855] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.855] (**) Logitech K360: (accel) acceleration profile 0
[     5.855] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.855] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.855] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.855] (II) No input driver specified, ignoring this device.
[     5.855] (II) This device may have been added with another device file.
[     5.856] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.856] (II) No input driver specified, ignoring this device.
[     5.856] (II) This device may have been added with another device file.
[     5.856] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.856] (II) No input driver specified, ignoring this device.
[     5.856] (II) This device may have been added with another device file.
[     5.856] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.856] (II) No input driver specified, ignoring this device.
[     5.856] (II) This device may have been added with another device file.
[     5.856] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.856] (II) No input driver specified, ignoring this device.
[     5.856] (II) This device may have been added with another device file.
[     5.856] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.857] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.857] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.857] (**) Eee PC WMI hotkeys: always reports core events
[     5.857] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.857] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.857] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.857] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.857] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.857] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.857] (**) Option "xkb_rules" "evdev"
[     5.857] (**) Option "xkb_model" "pc105"
[     5.857] (**) Option "xkb_layout" "us"
[     7.377] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.377] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.377] (--) NVIDIA(GPU-0): 
[     7.392] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.392] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.392] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.392] (--) NVIDIA(GPU-0): 
[     7.392] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.392] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.392] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.392] (--) NVIDIA(GPU-0): 
[     7.665] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.665] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.665] (--) NVIDIA(GPU-0): 
[     7.677] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.677] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.677] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.677] (--) NVIDIA(GPU-0): 
[     7.677] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.677] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.677] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.677] (--) NVIDIA(GPU-0): 
[     9.562] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     9.562] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     9.562] (--) NVIDIA(GPU-0): 
[     9.573] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     9.573] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     9.573] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     9.573] (--) NVIDIA(GPU-0): 
[     9.573] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.573] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.573] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.573] (--) NVIDIA(GPU-0): 
[  5400.353] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[  5400.354] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[  5400.354] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[  5400.354] (--) NVIDIA(GPU-0): 
[  5400.372] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[  5400.372] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[  5400.372] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[  5400.372] (--) NVIDIA(GPU-0): 
[  6811.205] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[  6811.205] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[  6811.205] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[  6811.205] (--) NVIDIA(GPU-0): 
[  6811.224] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[  6811.224] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[  6811.224] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[  6811.224] (--) NVIDIA(GPU-0): 
```

---

### Post by CatKiller on 2017-07-05
```
[     5.324] (==) Matched nvidia as autoconfigured driver 0
[     5.324] (==) Matched nouveau as autoconfigured driver 1
[     5.324] (==) Matched nvidia as autoconfigured driver 2
[     5.324] (==) Matched nouveau as autoconfigured driver 3
```

OK, that's not good. It seems both nouveau (the open source driver) and nvidia (the proprietary driver) are fighting over control of your graphics card. You didn't confirm whether you initially used the installer from NVidia's website, and what steps you'd taken to remove that driver afterwards. I suspect that it's cruft from that install that's causing you the conflicts now.

---

### Post by aviator1 on 2017-07-05
I first went to the NVidia site and found what was said to be the latest driver. Then I used Software & System Updates/Additional Drivers to select that driver. I did not notice it was a proprietary driver.

When I was able to get some navigation back, I used Software & System Updates/Additional Drivers and  selected the driver that had been previously working.

I did not know an uninstall was required, or how to do it.

The 3 cold starts I have done today have booted up with no problems.

Suggestions?

Thanks for your help.

Regards.

---

### Post by CatKiller on 2017-07-05
> **aviator1 said:**
> I first went to the NVidia site and found what was said to be the latest driver. Then I used Software & System Updates/Additional Drivers to select that driver. I did not notice it was a proprietary driver.

Ah, OK. Installing the driver from the website is quite a palaver. You'd definitely remember if you'd done that. It sounds like you didn't, and you actually installed it through the package manager. This is good.

> When I was able to get some navigation back, I used Software & System Updates/Additional Drivers and  selected the driver that had been previously working.

I did not know an uninstall was required, or how to do it.

If you didn't actually install the driver from their website, then you shouldn't need to do any tidying up. It's only if you had that you would potentially need to clean up after their installer. Installing through the package manager, as you appear to have done, is much easier to deal with.

>  The 3 cold starts I have done today have booted up with no problems.

Suggestions?

Thanks for your help.

Regards.

If it's still working, don't meddle with it ;)

If it starts playing up again we can see about removing any remaining nvidia stuff through the package manager. You can do it from the command-line if needs be, by using Ctrl-Alt-F1 to get to a terminal window and then using ```
sudo apt-get purge
```. After "purge" type nv and then use the Tab key, and it should intelligently auto-complete based on what you've actually got installed, so like "sudo apt-get purge nv<Tab>" If there's more than one way to autocomplete the command, pressing it twice will show you all the ways. Purge any nvidia options that you're given. That will leave you using the open-source nouveau driver, which is less performant but better-behaved. After that, ```
sudo apt-get install xserver-xorg-video-nouveau
``` or ```
sudo dpkg-reconfigure xserver-xorg-video-nouveau
``` should re-run nouveau's install scripts as a belt-and-braces approach. ```
sudo shutdown -r now
``` will restart the computer afterwards. You can use Tab-complete on all of these commands so you don't need to memorise every keypress.

The situation that you're in now, where both the nvidia and nouveau drivers are active, is supposed to be prevented by each of their install scripts: each of them is supposed to disable the other. I guess the process got interrupted by the navigation problems you were having.

But, for now, if it's working, you don't need to do anything.

---

### Post by aviator1 on 2017-07-05
Thanks very much for your efforts.

I will try it out for a few days and report back if it starts acting up.

If all is well, how should I report as "Solved"? Installed correct driver?

I really appreciate your time with this issue.

Regards.

---

### Post by CatKiller on 2017-07-05
Once you're happy that everything is as good as it's going to get, "Thread Tools" at the top of the page should have a "mark this thread as Solved" option.

If you get stuck, post back and hopefully someone can help you get unstuck again.

---

### Post by aviator1 on 2017-07-07
> **CatKiller said:**
> Once you're happy that everything is as good as it's going to get, "Thread Tools" at the top of the page should have a "mark this thread as Solved" option.

If you get stuck, post back and hopefully someone can help you get unstuck again.

I tried 

sudo apt-get purge nv (TAB)
sudo apt-get install xserver-xorg-video-nouveau
sudo shutdown -r now

and

sudo apt-get purge nv (TAB)
sudo dpkg-reconfigure xserver-xorg-video-nouveau  (This did nothing)
sudo shutdown -r now

Here is my latest xorg

```
[     5.384] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     5.384] X Protocol Version 11, Revision 0
[     5.384] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     5.384] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     5.384] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     5.384] Build Date: 02 November 2016  10:06:10PM
[     5.384] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.384] Current version of pixman: 0.33.6
[     5.384]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.384] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.384] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  7 18:14:28 2017
[     5.385] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.385] (==) No Layout section.  Using the first Screen section.
[     5.385] (==) No screen section available. Using defaults.
[     5.385] (**) |-->Screen "Default Screen Section" (0)
[     5.385] (**) |   |-->Monitor "<default monitor>"
[     5.386] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.386] (==) Automatically adding devices
[     5.386] (==) Automatically enabling devices
[     5.386] (==) Automatically adding GPU devices
[     5.386] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.386] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.386]     Entry deleted from font path.
[     5.386] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.386]     Entry deleted from font path.
[     5.386] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.386]     Entry deleted from font path.
[     5.386] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.386]     Entry deleted from font path.
[     5.386] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.386]     Entry deleted from font path.
[     5.386] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.386] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.386] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.386] (II) Loader magic: 0x55e8715dfdc0
[     5.386] (II) Module ABI versions:
[     5.386]     X.Org ANSI C Emulation: 0.4
[     5.386]     X.Org Video Driver: 20.0
[     5.386]     X.Org XInput driver : 22.1
[     5.386]     X.Org Server Extension : 9.0
[     5.387] (++) using VT number 7

[     5.387] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.387] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.388] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.388] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     5.388] (II) "glx" will be loaded by default.
[     5.388] (II) LoadModule: "glx"
[     5.388] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.432] (II) Module glx: vendor="NVIDIA Corporation"
[     5.432]     compiled for 4.0.2, module version = 1.0.0
[     5.432]     Module class: X.Org Server Extension
[     5.432] (II) NVIDIA GLX Module  381.22  Thu May  4 00:17:15 PDT 2017
[     5.432] (==) Matched nvidia as autoconfigured driver 0
[     5.432] (==) Matched nouveau as autoconfigured driver 1
[     5.432] (==) Matched nvidia as autoconfigured driver 2
[     5.432] (==) Matched nouveau as autoconfigured driver 3
[     5.432] (==) Matched modesetting as autoconfigured driver 4
[     5.432] (==) Matched fbdev as autoconfigured driver 5
[     5.432] (==) Matched vesa as autoconfigured driver 6
[     5.432] (==) Assigned the driver to the xf86ConfigLayout
[     5.432] (II) LoadModule: "nvidia"
[     5.432] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.436] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.436]     compiled for 4.0.2, module version = 1.0.0
[     5.436]     Module class: X.Org Video Driver
[     5.437] (II) LoadModule: "nouveau"
[     5.437] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.438] (II) Module nouveau: vendor="X.Org Foundation"
[     5.438]     compiled for 1.18.1, module version = 1.0.12
[     5.438]     Module class: X.Org Video Driver
[     5.438]     ABI class: X.Org Video Driver, version 20.0
[     5.438] (II) LoadModule: "modesetting"
[     5.438] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.438] (II) Module modesetting: vendor="X.Org Foundation"
[     5.438]     compiled for 1.18.4, module version = 1.18.4
[     5.438]     Module class: X.Org Video Driver
[     5.438]     ABI class: X.Org Video Driver, version 20.0
[     5.438] (II) LoadModule: "fbdev"
[     5.438] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.438] (II) Module fbdev: vendor="X.Org Foundation"
[     5.438]     compiled for 1.18.1, module version = 0.4.4
[     5.438]     Module class: X.Org Video Driver
[     5.438]     ABI class: X.Org Video Driver, version 20.0
[     5.438] (II) LoadModule: "vesa"
[     5.439] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.439] (II) Module vesa: vendor="X.Org Foundation"
[     5.439]     compiled for 1.18.1, module version = 2.3.4
[     5.439]     Module class: X.Org Video Driver
[     5.439]     ABI class: X.Org Video Driver, version 20.0
[     5.439] (II) NVIDIA dlloader X Driver  381.22  Wed May  3 23:53:41 PDT 2017
[     5.439] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.439] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.439] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.439]     RIVA TNT        (NV04)
[     5.439]     RIVA TNT2       (NV05)
[     5.439]     GeForce 256     (NV10)
[     5.439]     GeForce 2       (NV11, NV15)
[     5.439]     GeForce 4MX     (NV17, NV18)
[     5.439]     GeForce 3       (NV20)
[     5.439]     GeForce 4Ti     (NV25, NV28)
[     5.439]     GeForce FX      (NV3x)
[     5.439]     GeForce 6       (NV4x)
[     5.439]     GeForce 7       (G7x)
[     5.439]     GeForce 8       (G8x)
[     5.439]     GeForce GTX 200 (NVA0)
[     5.439]     GeForce GTX 400 (NVC0)
[     5.439] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.439] (II) FBDEV: driver for framebuffer: fbdev
[     5.439] (II) VESA: driver for VESA chipsets: vesa
[     5.440] (II) Loading sub module "fb"
[     5.440] (II) LoadModule: "fb"
[     5.441] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.441] (II) Module fb: vendor="X.Org Foundation"
[     5.441]     compiled for 1.18.4, module version = 1.0.0
[     5.441]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.441] (II) Loading sub module "wfb"
[     5.441] (II) LoadModule: "wfb"
[     5.441] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.442] (II) Module wfb: vendor="X.Org Foundation"
[     5.442]     compiled for 1.18.4, module version = 1.0.0
[     5.442]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.442] (II) Loading sub module "ramdac"
[     5.442] (II) LoadModule: "ramdac"
[     5.442] (II) Module "ramdac" already built-in
[     5.444] (WW) Falling back to old probe method for modesetting
[     5.444] (WW) Falling back to old probe method for fbdev
[     5.444] (II) Loading sub module "fbdevhw"
[     5.444] (II) LoadModule: "fbdevhw"
[     5.444] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.444] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.444]     compiled for 1.18.4, module version = 0.0.2
[     5.444]     ABI class: X.Org Video Driver, version 20.0
[     5.444] (WW) Falling back to old probe method for vesa
[     5.444] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.444] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.444] (==) NVIDIA(0): RGB weight 888
[     5.444] (==) NVIDIA(0): Default visual is TrueColor
[     5.444] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.445] (**) NVIDIA(0): Enabling 2D acceleration
[     5.800] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     5.800] (--) NVIDIA(0):     CRT-0
[     5.800] (--) NVIDIA(0):     DFP-0 (boot)
[     5.800] (--) NVIDIA(0):     DFP-1
[     5.801] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     5.801] (--) NVIDIA(0): Memory: 4194304 kBytes
[     5.801] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.56
[     5.801] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     5.802] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     5.802] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     5.802] (--) NVIDIA(GPU-0): 
[     5.814] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     5.814] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     5.814] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     5.814] (--) NVIDIA(GPU-0): 
[     5.814] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     5.814] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     5.814] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     5.814] (--) NVIDIA(GPU-0): 
[     5.816] (==) NVIDIA(0): 
[     5.816] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     5.816] (==) NVIDIA(0):     will be used as the requested mode.
[     5.816] (==) NVIDIA(0): 
[     5.817] (II) NVIDIA(0): Validated MetaModes:
[     5.817] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     5.817] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     5.826] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     5.826] (--) NVIDIA(0):     option
[     5.826] (II) UnloadModule: "nouveau"
[     5.826] (II) Unloading nouveau
[     5.826] (II) UnloadModule: "modesetting"
[     5.826] (II) Unloading modesetting
[     5.826] (II) UnloadModule: "fbdev"
[     5.826] (II) Unloading fbdev
[     5.826] (II) UnloadSubModule: "fbdevhw"
[     5.826] (II) Unloading fbdevhw
[     5.826] (II) UnloadModule: "vesa"
[     5.826] (II) Unloading vesa
[     5.826] (--) Depth 24 pixmap format is 32 bpp
[     5.827] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.827] (II) NVIDIA:     access.
[     5.851] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     5.903] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.903] (==) NVIDIA(0): Backing store enabled
[     5.903] (==) NVIDIA(0): Silken mouse enabled
[     5.905] (==) NVIDIA(0): DPMS enabled
[     5.905] (II) Loading sub module "dri2"
[     5.905] (II) LoadModule: "dri2"
[     5.905] (II) Module "dri2" already built-in
[     5.905] (II) NVIDIA(0): [DRI2] Setup complete
[     5.905] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.906] (--) RandR disabled
[     5.910] (II) SELinux: Disabled on system
[     5.910] (II) Initializing extension GLX
[     5.910] (II) Indirect GLX disabled.
[     5.959] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.959] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.959] (II) LoadModule: "evdev"
[     5.959] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.961] (II) Module evdev: vendor="X.Org Foundation"
[     5.961]     compiled for 1.18.1, module version = 2.10.1
[     5.961]     Module class: X.Org XInput Driver
[     5.961]     ABI class: X.Org XInput driver, version 22.1
[     5.961] (II) Using input driver 'evdev' for 'Power Button'
[     5.961] (**) Power Button: always reports core events
[     5.961] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.961] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.961] (--) evdev: Power Button: Found keys
[     5.961] (II) evdev: Power Button: Configuring as keyboard
[     5.961] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.961] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.961] (**) Option "xkb_rules" "evdev"
[     5.961] (**) Option "xkb_model" "pc105"
[     5.961] (**) Option "xkb_layout" "us"
[     5.962] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.962] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.962] (II) Using input driver 'evdev' for 'Power Button'
[     5.962] (**) Power Button: always reports core events
[     5.962] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.962] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.962] (--) evdev: Power Button: Found keys
[     5.962] (II) evdev: Power Button: Configuring as keyboard
[     5.962] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.962] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.962] (**) Option "xkb_rules" "evdev"
[     5.962] (**) Option "xkb_model" "pc105"
[     5.962] (**) Option "xkb_layout" "us"
[     5.962] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.962] (II) No input driver specified, ignoring this device.
[     5.962] (II) This device may have been added with another device file.
[     5.962] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.962] (II) No input driver specified, ignoring this device.
[     5.962] (II) This device may have been added with another device file.
[     5.963] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.963] (II) No input driver specified, ignoring this device.
[     5.963] (II) This device may have been added with another device file.
[     5.963] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.963] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.963] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.963] (**) Logitech M570: always reports core events
[     5.963] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.963] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.963] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.963] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.963] (--) evdev: Logitech M570: Found relative axes
[     5.963] (--) evdev: Logitech M570: Found x and y relative axes
[     5.963] (II) evdev: Logitech M570: Configuring as mouse
[     5.963] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.963] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.963] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.963] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.963] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.963] (II) evdev: Logitech M570: initialized for relative axes.
[     5.963] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.963] (**) Logitech M570: (accel) acceleration profile 0
[     5.963] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.963] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.964] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.964] (II) No input driver specified, ignoring this device.
[     5.964] (II) This device may have been added with another device file.
[     5.964] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.964] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.964] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.964] (**) Logitech K360: always reports core events
[     5.964] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.964] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.964] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.964] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.964] (--) evdev: Logitech K360: Found relative axes
[     5.964] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.964] (--) evdev: Logitech K360: Found absolute axes
[     5.964] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.964] (--) evdev: Logitech K360: Found keys
[     5.964] (II) evdev: Logitech K360: Configuring as mouse
[     5.964] (II) evdev: Logitech K360: Configuring as keyboard
[     5.964] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.964] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.964] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.964] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.964] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.964] (**) Option "xkb_rules" "evdev"
[     5.964] (**) Option "xkb_model" "pc105"
[     5.964] (**) Option "xkb_layout" "us"
[     5.964] (II) evdev: Logitech K360: initialized for relative axes.
[     5.964] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.965] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.965] (**) Logitech K360: (accel) acceleration profile 0
[     5.965] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.965] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.965] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.965] (II) No input driver specified, ignoring this device.
[     5.965] (II) This device may have been added with another device file.
[     5.965] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.965] (II) No input driver specified, ignoring this device.
[     5.965] (II) This device may have been added with another device file.
[     5.965] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.965] (II) No input driver specified, ignoring this device.
[     5.965] (II) This device may have been added with another device file.
[     5.965] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.965] (II) No input driver specified, ignoring this device.
[     5.965] (II) This device may have been added with another device file.
[     5.966] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.966] (II) No input driver specified, ignoring this device.
[     5.966] (II) This device may have been added with another device file.
[     5.966] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.966] (II) No input driver specified, ignoring this device.
[     5.966] (II) This device may have been added with another device file.
[     5.966] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.966] (II) No input driver specified, ignoring this device.
[     5.966] (II) This device may have been added with another device file.
[     5.966] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.966] (II) No input driver specified, ignoring this device.
[     5.966] (II) This device may have been added with another device file.
[     5.966] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.966] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.966] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.966] (**) Eee PC WMI hotkeys: always reports core events
[     5.966] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.967] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.967] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.967] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.967] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.967] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.967] (**) Option "xkb_rules" "evdev"
[     5.967] (**) Option "xkb_model" "pc105"
[     5.967] (**) Option "xkb_layout" "us"
[     7.502] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.502] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.502] (--) NVIDIA(GPU-0): 
[     7.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.516] (--) NVIDIA(GPU-0): 
[     7.516] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.516] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.516] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.516] (--) NVIDIA(GPU-0): 
[     7.754] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.754] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.754] (--) NVIDIA(GPU-0): 
[     7.766] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.766] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.766] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.766] (--) NVIDIA(GPU-0): 
[     7.766] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.766] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.766] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.766] (--) NVIDIA(GPU-0): 
[     9.630] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     9.630] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     9.630] (--) NVIDIA(GPU-0): 
[     9.642] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     9.642] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     9.642] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     9.642] (--) NVIDIA(GPU-0): 
[     9.642] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.642] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.642] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.642] (--) NVIDIA(GPU-0): 

```

Still have to boot twice to get everything working OK.

Thanks for any help.

---

### Post by CatKiller on 2017-07-07
OK, you've still got both nvidia and nouveau installed and fighting over your graphics card.

> **aviator1 said:**
> I tried 

sudo apt-get purge nv (TAB)

What did it autocomplete to?

---

### Post by aviator1 on 2017-07-07
When I hit TAB, it showed NVidia (Cannot recall if there was anything else)

I just tried it now, and nothing happened when I hit TAB

---

### Post by CatKiller on 2017-07-07
If there's more than one option, you need to press Tab twice so that it will display all the options. It used to beep at the same time, but I think users found the beep annoying so they turned it off for the default. Then, when you can see the options, you'll want to purge all the nvidia stuff. Then, when you've got rid of all the nvidia stuff you'll want to make sure that nouveau is installed, and then use dpkg-reconfigure to run nouveau's install scripts again.

Hopefully then you will only have nouveau, and nouveau will be properly installed.

---

### Post by aviator1 on 2017-07-07
When I typed in        sudo apt-get purge nv (TAB) just now,                nvidia-    showed up. I did not go further.

---

### Post by CatKiller on 2017-07-07
> **aviator1 said:**
> When I typed in        sudo apt-get purge nv (TAB) just now,                nvidia-    showed up. I did not go further.

Yes, that means that there's more than one way that it can complete the command, but they all start with "nvidia-". Pressing Tab again will show you all of the ways that the command can autocomplete: all the packages whose name starts with nvidia- that you can remove. You're probably going to want to remove all of them.

---

### Post by aviator1 on 2017-07-07
> **CatKiller said:**
> Yes, that means that there's more than one way that it can complete the command, but they all start with "nvidia-". Pressing Tab again will show you all of the ways that the command can autocomplete: all the packages whose name starts with nvidia- that you can remove. You're probably going to want to remove all of them.

I hit TAB twice and another NVidia showed up, and took me to the command prompt (if that's what it's called)

I then  ran 
sudo apt-get install xserver-xorg-video-nouveau
sudo shutdown -r now

I then did a complete shutdown and a restyart. all seemed OK.

Her is the latest xorg.
```
[     4.801] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     4.801] X Protocol Version 11, Revision 0
[     4.801] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     4.801] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     4.801] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     4.802] Build Date: 02 November 2016  10:06:10PM
[     4.802] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.802] Current version of pixman: 0.33.6
[     4.802]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.802] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.802] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  7 19:18:10 2017
[     4.805] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.809] (==) No Layout section.  Using the first Screen section.
[     4.809] (==) No screen section available. Using defaults.
[     4.809] (**) |-->Screen "Default Screen Section" (0)
[     4.809] (**) |   |-->Monitor "<default monitor>"
[     4.810] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.810] (==) Automatically adding devices
[     4.810] (==) Automatically enabling devices
[     4.810] (==) Automatically adding GPU devices
[     4.810] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.810] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.810]     Entry deleted from font path.
[     4.810] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.810]     Entry deleted from font path.
[     4.810] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.810]     Entry deleted from font path.
[     4.810] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.810]     Entry deleted from font path.
[     4.810] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.810]     Entry deleted from font path.
[     4.810] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.810] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.810] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.813] (II) Loader magic: 0x55b73f30ddc0
[     4.813] (II) Module ABI versions:
[     4.813]     X.Org ANSI C Emulation: 0.4
[     4.813]     X.Org Video Driver: 20.0
[     4.813]     X.Org XInput driver : 22.1
[     4.813]     X.Org Server Extension : 9.0
[     4.814] (++) using VT number 7

[     4.814] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.814] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.815] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.815] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     4.815] (II) "glx" will be loaded by default.
[     4.815] (II) LoadModule: "glx"
[     4.815] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.010] (II) Module glx: vendor="NVIDIA Corporation"
[     5.010]     compiled for 4.0.2, module version = 1.0.0
[     5.010]     Module class: X.Org Server Extension
[     5.010] (II) NVIDIA GLX Module  381.22  Thu May  4 00:17:15 PDT 2017
[     5.010] (==) Matched nvidia as autoconfigured driver 0
[     5.010] (==) Matched nouveau as autoconfigured driver 1
[     5.010] (==) Matched nvidia as autoconfigured driver 2
[     5.010] (==) Matched nouveau as autoconfigured driver 3
[     5.010] (==) Matched modesetting as autoconfigured driver 4
[     5.010] (==) Matched fbdev as autoconfigured driver 5
[     5.010] (==) Matched vesa as autoconfigured driver 6
[     5.010] (==) Assigned the driver to the xf86ConfigLayout
[     5.010] (II) LoadModule: "nvidia"
[     5.010] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.014] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.014]     compiled for 4.0.2, module version = 1.0.0
[     5.014]     Module class: X.Org Video Driver
[     5.015] (II) LoadModule: "nouveau"
[     5.015] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.016] (II) Module nouveau: vendor="X.Org Foundation"
[     5.016]     compiled for 1.18.1, module version = 1.0.12
[     5.016]     Module class: X.Org Video Driver
[     5.016]     ABI class: X.Org Video Driver, version 20.0
[     5.016] (II) LoadModule: "modesetting"
[     5.016] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.016] (II) Module modesetting: vendor="X.Org Foundation"
[     5.016]     compiled for 1.18.4, module version = 1.18.4
[     5.016]     Module class: X.Org Video Driver
[     5.016]     ABI class: X.Org Video Driver, version 20.0
[     5.016] (II) LoadModule: "fbdev"
[     5.016] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.016] (II) Module fbdev: vendor="X.Org Foundation"
[     5.016]     compiled for 1.18.1, module version = 0.4.4
[     5.016]     Module class: X.Org Video Driver
[     5.016]     ABI class: X.Org Video Driver, version 20.0
[     5.016] (II) LoadModule: "vesa"
[     5.017] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.017] (II) Module vesa: vendor="X.Org Foundation"
[     5.017]     compiled for 1.18.1, module version = 2.3.4
[     5.017]     Module class: X.Org Video Driver
[     5.017]     ABI class: X.Org Video Driver, version 20.0
[     5.017] (II) NVIDIA dlloader X Driver  381.22  Wed May  3 23:53:41 PDT 2017
[     5.017] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.017] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.017] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.017]     RIVA TNT        (NV04)
[     5.017]     RIVA TNT2       (NV05)
[     5.017]     GeForce 256     (NV10)
[     5.017]     GeForce 2       (NV11, NV15)
[     5.017]     GeForce 4MX     (NV17, NV18)
[     5.017]     GeForce 3       (NV20)
[     5.017]     GeForce 4Ti     (NV25, NV28)
[     5.017]     GeForce FX      (NV3x)
[     5.017]     GeForce 6       (NV4x)
[     5.017]     GeForce 7       (G7x)
[     5.017]     GeForce 8       (G8x)
[     5.017]     GeForce GTX 200 (NVA0)
[     5.017]     GeForce GTX 400 (NVC0)
[     5.017] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.017] (II) FBDEV: driver for framebuffer: fbdev
[     5.017] (II) VESA: driver for VESA chipsets: vesa
[     5.018] (II) Loading sub module "fb"
[     5.018] (II) LoadModule: "fb"
[     5.019] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.019] (II) Module fb: vendor="X.Org Foundation"
[     5.019]     compiled for 1.18.4, module version = 1.0.0
[     5.019]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.019] (II) Loading sub module "wfb"
[     5.019] (II) LoadModule: "wfb"
[     5.019] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.019] (II) Module wfb: vendor="X.Org Foundation"
[     5.019]     compiled for 1.18.4, module version = 1.0.0
[     5.019]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.020] (II) Loading sub module "ramdac"
[     5.020] (II) LoadModule: "ramdac"
[     5.020] (II) Module "ramdac" already built-in
[     5.022] (WW) Falling back to old probe method for modesetting
[     5.022] (WW) Falling back to old probe method for fbdev
[     5.022] (II) Loading sub module "fbdevhw"
[     5.022] (II) LoadModule: "fbdevhw"
[     5.022] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.022] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.022]     compiled for 1.18.4, module version = 0.0.2
[     5.022]     ABI class: X.Org Video Driver, version 20.0
[     5.022] (WW) Falling back to old probe method for vesa
[     5.022] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.022] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.022] (==) NVIDIA(0): RGB weight 888
[     5.022] (==) NVIDIA(0): Default visual is TrueColor
[     5.022] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.023] (**) NVIDIA(0): Enabling 2D acceleration
[     5.370] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     5.370] (--) NVIDIA(0):     CRT-0
[     5.370] (--) NVIDIA(0):     DFP-0 (boot)
[     5.370] (--) NVIDIA(0):     DFP-1
[     5.372] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     5.372] (--) NVIDIA(0): Memory: 4194304 kBytes
[     5.372] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.56
[     5.372] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     5.373] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     5.373] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     5.373] (--) NVIDIA(GPU-0): 
[     5.384] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     5.384] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     5.384] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     5.384] (--) NVIDIA(GPU-0): 
[     5.384] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     5.384] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     5.384] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     5.384] (--) NVIDIA(GPU-0): 
[     5.387] (==) NVIDIA(0): 
[     5.387] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     5.387] (==) NVIDIA(0):     will be used as the requested mode.
[     5.387] (==) NVIDIA(0): 
[     5.387] (II) NVIDIA(0): Validated MetaModes:
[     5.387] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     5.387] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     5.397] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     5.397] (--) NVIDIA(0):     option
[     5.397] (II) UnloadModule: "nouveau"
[     5.397] (II) Unloading nouveau
[     5.397] (II) UnloadModule: "modesetting"
[     5.397] (II) Unloading modesetting
[     5.397] (II) UnloadModule: "fbdev"
[     5.397] (II) Unloading fbdev
[     5.397] (II) UnloadSubModule: "fbdevhw"
[     5.397] (II) Unloading fbdevhw
[     5.397] (II) UnloadModule: "vesa"
[     5.397] (II) Unloading vesa
[     5.397] (--) Depth 24 pixmap format is 32 bpp
[     5.398] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.398] (II) NVIDIA:     access.
[     5.422] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     5.474] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.474] (==) NVIDIA(0): Backing store enabled
[     5.474] (==) NVIDIA(0): Silken mouse enabled
[     5.475] (==) NVIDIA(0): DPMS enabled
[     5.475] (II) Loading sub module "dri2"
[     5.475] (II) LoadModule: "dri2"
[     5.475] (II) Module "dri2" already built-in
[     5.475] (II) NVIDIA(0): [DRI2] Setup complete
[     5.475] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.476] (--) RandR disabled
[     5.479] (II) SELinux: Disabled on system
[     5.480] (II) Initializing extension GLX
[     5.480] (II) Indirect GLX disabled.
[     5.530] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.530] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.530] (II) LoadModule: "evdev"
[     5.530] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.532] (II) Module evdev: vendor="X.Org Foundation"
[     5.532]     compiled for 1.18.1, module version = 2.10.1
[     5.532]     Module class: X.Org XInput Driver
[     5.532]     ABI class: X.Org XInput driver, version 22.1
[     5.532] (II) Using input driver 'evdev' for 'Power Button'
[     5.532] (**) Power Button: always reports core events
[     5.532] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.532] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.532] (--) evdev: Power Button: Found keys
[     5.532] (II) evdev: Power Button: Configuring as keyboard
[     5.532] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.532] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.532] (**) Option "xkb_rules" "evdev"
[     5.532] (**) Option "xkb_model" "pc105"
[     5.532] (**) Option "xkb_layout" "us"
[     5.533] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.533] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.533] (II) Using input driver 'evdev' for 'Power Button'
[     5.533] (**) Power Button: always reports core events
[     5.533] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.533] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.533] (--) evdev: Power Button: Found keys
[     5.533] (II) evdev: Power Button: Configuring as keyboard
[     5.533] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.533] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.533] (**) Option "xkb_rules" "evdev"
[     5.533] (**) Option "xkb_model" "pc105"
[     5.533] (**) Option "xkb_layout" "us"
[     5.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.533] (II) No input driver specified, ignoring this device.
[     5.533] (II) This device may have been added with another device file.
[     5.534] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.534] (II) No input driver specified, ignoring this device.
[     5.534] (II) This device may have been added with another device file.
[     5.534] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.534] (II) No input driver specified, ignoring this device.
[     5.534] (II) This device may have been added with another device file.
[     5.535] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.535] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.535] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.535] (**) Logitech M570: always reports core events
[     5.535] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.535] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.535] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.535] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.535] (--) evdev: Logitech M570: Found relative axes
[     5.535] (--) evdev: Logitech M570: Found x and y relative axes
[     5.535] (II) evdev: Logitech M570: Configuring as mouse
[     5.535] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.535] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.535] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.535] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.535] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.535] (II) evdev: Logitech M570: initialized for relative axes.
[     5.535] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.535] (**) Logitech M570: (accel) acceleration profile 0
[     5.535] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.535] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.536] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.536] (II) No input driver specified, ignoring this device.
[     5.536] (II) This device may have been added with another device file.
[     5.536] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.536] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.536] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.536] (**) Logitech K360: always reports core events
[     5.536] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.536] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.536] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.536] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.536] (--) evdev: Logitech K360: Found relative axes
[     5.536] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.536] (--) evdev: Logitech K360: Found absolute axes
[     5.536] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.536] (--) evdev: Logitech K360: Found keys
[     5.536] (II) evdev: Logitech K360: Configuring as mouse
[     5.536] (II) evdev: Logitech K360: Configuring as keyboard
[     5.536] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.536] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.536] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.536] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.536] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.536] (**) Option "xkb_rules" "evdev"
[     5.536] (**) Option "xkb_model" "pc105"
[     5.536] (**) Option "xkb_layout" "us"
[     5.537] (II) evdev: Logitech K360: initialized for relative axes.
[     5.537] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.537] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.537] (**) Logitech K360: (accel) acceleration profile 0
[     5.537] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.537] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.537] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.537] (II) No input driver specified, ignoring this device.
[     5.537] (II) This device may have been added with another device file.
[     5.537] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.537] (II) No input driver specified, ignoring this device.
[     5.537] (II) This device may have been added with another device file.
[     5.538] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.538] (II) No input driver specified, ignoring this device.
[     5.538] (II) This device may have been added with another device file.
[     5.538] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.538] (II) No input driver specified, ignoring this device.
[     5.538] (II) This device may have been added with another device file.
[     5.538] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.538] (II) No input driver specified, ignoring this device.
[     5.538] (II) This device may have been added with another device file.
[     5.538] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.538] (II) No input driver specified, ignoring this device.
[     5.538] (II) This device may have been added with another device file.
[     5.539] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.539] (II) No input driver specified, ignoring this device.
[     5.539] (II) This device may have been added with another device file.
[     5.539] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.539] (II) No input driver specified, ignoring this device.
[     5.539] (II) This device may have been added with another device file.
[     5.539] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.539] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.539] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.539] (**) Eee PC WMI hotkeys: always reports core events
[     5.539] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.539] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.539] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.539] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.539] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.539] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.539] (**) Option "xkb_rules" "evdev"
[     5.539] (**) Option "xkb_model" "pc105"
[     5.539] (**) Option "xkb_layout" "us"
[     7.084] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.084] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.084] (--) NVIDIA(GPU-0): 
[     7.096] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.096] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.096] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.096] (--) NVIDIA(GPU-0): 
[     7.096] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.096] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.096] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.096] (--) NVIDIA(GPU-0): 
[     7.315] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.315] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.315] (--) NVIDIA(GPU-0): 
[     7.327] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.327] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.327] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.327] (--) NVIDIA(GPU-0): 
[     7.327] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.327] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.327] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.327] (--) NVIDIA(GPU-0): 
[     9.434] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     9.434] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     9.434] (--) NVIDIA(GPU-0): 
[     9.446] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     9.446] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     9.446] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     9.446] (--) NVIDIA(GPU-0): 
[     9.446] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.446] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.446] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.446] (--) NVIDIA(GPU-0): 
```

---

### Post by CatKiller on 2017-07-07
> **aviator1 said:**
> I hit TAB twice and another NVidia showed up, and took me to the command prompt (if that's what it's called)


Yes, you need to give it enough from the options that you're given to complete the command. So you type sudo apt-get purge nv, hit tab twice and it says something like ```
nvidia-123
nvidia-456
``` (version numbers completely made up)
So then you'd fill in 123, and because you *also* want to remove nvidia-456, you would type nv<Tab> again to let it autocomplete again, and fill in the 456. So your command would look like ```
sudo apt-get purge nvidia-123 nvidia-456
``` including *all* of the nvidia stuff that you've currently got installed. You don't want to install nouveau till you've got rid of all the nvidia stuff, otherwise you aren't going to resolve the conflict.

---

### Post by aviator1 on 2017-07-07
I have done 3 complete shut downs and restarts with no issues.

Is there something I should be doing?

Thanks for your help.

---

### Post by CatKiller on 2017-07-07
Have you actually managed to remove all the nvidia packages yet?

---

### Post by aviator1 on 2017-07-07
> **CatKiller said:**
> Have you actually managed to remove all the nvidia packages yet?

I don't know. Here is the latest xorg
```
[     4.883] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     4.883] X Protocol Version 11, Revision 0
[     4.883] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     4.883] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     4.883] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     4.883] Build Date: 02 November 2016  10:06:10PM
[     4.883] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.883] Current version of pixman: 0.33.6
[     4.883]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.883] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.883] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  7 19:52:19 2017
[     4.918] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.919] (==) No Layout section.  Using the first Screen section.
[     4.919] (==) No screen section available. Using defaults.
[     4.919] (**) |-->Screen "Default Screen Section" (0)
[     4.919] (**) |   |-->Monitor "<default monitor>"
[     4.920] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.920] (==) Automatically adding devices
[     4.920] (==) Automatically enabling devices
[     4.920] (==) Automatically adding GPU devices
[     4.920] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.920] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.920]     Entry deleted from font path.
[     4.920] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.920]     Entry deleted from font path.
[     4.920] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.920]     Entry deleted from font path.
[     4.920] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.920]     Entry deleted from font path.
[     4.920] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.920]     Entry deleted from font path.
[     4.920] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.920] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.920] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.946] (II) Loader magic: 0x5562cf883dc0
[     4.946] (II) Module ABI versions:
[     4.946]     X.Org ANSI C Emulation: 0.4
[     4.946]     X.Org Video Driver: 20.0
[     4.946]     X.Org XInput driver : 22.1
[     4.946]     X.Org Server Extension : 9.0
[     4.947] (++) using VT number 7

[     4.947] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.947] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.948] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.948] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     4.948] (II) "glx" will be loaded by default.
[     4.948] (II) LoadModule: "glx"
[     4.949] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.074] (II) Module glx: vendor="NVIDIA Corporation"
[     5.074]     compiled for 4.0.2, module version = 1.0.0
[     5.074]     Module class: X.Org Server Extension
[     5.074] (II) NVIDIA GLX Module  381.22  Thu May  4 00:17:15 PDT 2017
[     5.074] (==) Matched nvidia as autoconfigured driver 0
[     5.074] (==) Matched nouveau as autoconfigured driver 1
[     5.074] (==) Matched nvidia as autoconfigured driver 2
[     5.074] (==) Matched nouveau as autoconfigured driver 3
[     5.074] (==) Matched modesetting as autoconfigured driver 4
[     5.074] (==) Matched fbdev as autoconfigured driver 5
[     5.074] (==) Matched vesa as autoconfigured driver 6
[     5.074] (==) Assigned the driver to the xf86ConfigLayout
[     5.074] (II) LoadModule: "nvidia"
[     5.074] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.078] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.078]     compiled for 4.0.2, module version = 1.0.0
[     5.078]     Module class: X.Org Video Driver
[     5.079] (II) LoadModule: "nouveau"
[     5.079] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.080] (II) Module nouveau: vendor="X.Org Foundation"
[     5.080]     compiled for 1.18.1, module version = 1.0.12
[     5.080]     Module class: X.Org Video Driver
[     5.080]     ABI class: X.Org Video Driver, version 20.0
[     5.080] (II) LoadModule: "modesetting"
[     5.080] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.080] (II) Module modesetting: vendor="X.Org Foundation"
[     5.080]     compiled for 1.18.4, module version = 1.18.4
[     5.080]     Module class: X.Org Video Driver
[     5.080]     ABI class: X.Org Video Driver, version 20.0
[     5.080] (II) LoadModule: "fbdev"
[     5.080] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.080] (II) Module fbdev: vendor="X.Org Foundation"
[     5.080]     compiled for 1.18.1, module version = 0.4.4
[     5.080]     Module class: X.Org Video Driver
[     5.080]     ABI class: X.Org Video Driver, version 20.0
[     5.080] (II) LoadModule: "vesa"
[     5.080] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.080] (II) Module vesa: vendor="X.Org Foundation"
[     5.080]     compiled for 1.18.1, module version = 2.3.4
[     5.080]     Module class: X.Org Video Driver
[     5.080]     ABI class: X.Org Video Driver, version 20.0
[     5.080] (II) NVIDIA dlloader X Driver  381.22  Wed May  3 23:53:41 PDT 2017
[     5.080] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.081] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.081] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.081]     RIVA TNT        (NV04)
[     5.081]     RIVA TNT2       (NV05)
[     5.081]     GeForce 256     (NV10)
[     5.081]     GeForce 2       (NV11, NV15)
[     5.081]     GeForce 4MX     (NV17, NV18)
[     5.081]     GeForce 3       (NV20)
[     5.081]     GeForce 4Ti     (NV25, NV28)
[     5.081]     GeForce FX      (NV3x)
[     5.081]     GeForce 6       (NV4x)
[     5.081]     GeForce 7       (G7x)
[     5.081]     GeForce 8       (G8x)
[     5.081]     GeForce GTX 200 (NVA0)
[     5.081]     GeForce GTX 400 (NVC0)
[     5.081] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.081] (II) FBDEV: driver for framebuffer: fbdev
[     5.081] (II) VESA: driver for VESA chipsets: vesa
[     5.082] (II) Loading sub module "fb"
[     5.082] (II) LoadModule: "fb"
[     5.082] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.083] (II) Module fb: vendor="X.Org Foundation"
[     5.083]     compiled for 1.18.4, module version = 1.0.0
[     5.083]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.083] (II) Loading sub module "wfb"
[     5.083] (II) LoadModule: "wfb"
[     5.083] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.083] (II) Module wfb: vendor="X.Org Foundation"
[     5.083]     compiled for 1.18.4, module version = 1.0.0
[     5.083]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.083] (II) Loading sub module "ramdac"
[     5.083] (II) LoadModule: "ramdac"
[     5.083] (II) Module "ramdac" already built-in
[     5.085] (WW) Falling back to old probe method for modesetting
[     5.085] (WW) Falling back to old probe method for fbdev
[     5.085] (II) Loading sub module "fbdevhw"
[     5.085] (II) LoadModule: "fbdevhw"
[     5.086] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.086] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.086]     compiled for 1.18.4, module version = 0.0.2
[     5.086]     ABI class: X.Org Video Driver, version 20.0
[     5.086] (WW) Falling back to old probe method for vesa
[     5.086] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.086] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.086] (==) NVIDIA(0): RGB weight 888
[     5.086] (==) NVIDIA(0): Default visual is TrueColor
[     5.086] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.087] (**) NVIDIA(0): Enabling 2D acceleration
[     5.440] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     5.440] (--) NVIDIA(0):     CRT-0
[     5.440] (--) NVIDIA(0):     DFP-0 (boot)
[     5.440] (--) NVIDIA(0):     DFP-1
[     5.441] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     5.441] (--) NVIDIA(0): Memory: 4194304 kBytes
[     5.441] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.56
[     5.441] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     5.442] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     5.442] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     5.442] (--) NVIDIA(GPU-0): 
[     5.454] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     5.454] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     5.454] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     5.454] (--) NVIDIA(GPU-0): 
[     5.454] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     5.454] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     5.454] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     5.454] (--) NVIDIA(GPU-0): 
[     5.456] (==) NVIDIA(0): 
[     5.456] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     5.456] (==) NVIDIA(0):     will be used as the requested mode.
[     5.456] (==) NVIDIA(0): 
[     5.457] (II) NVIDIA(0): Validated MetaModes:
[     5.457] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     5.457] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     5.466] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     5.466] (--) NVIDIA(0):     option
[     5.466] (II) UnloadModule: "nouveau"
[     5.466] (II) Unloading nouveau
[     5.466] (II) UnloadModule: "modesetting"
[     5.466] (II) Unloading modesetting
[     5.466] (II) UnloadModule: "fbdev"
[     5.466] (II) Unloading fbdev
[     5.466] (II) UnloadSubModule: "fbdevhw"
[     5.466] (II) Unloading fbdevhw
[     5.466] (II) UnloadModule: "vesa"
[     5.466] (II) Unloading vesa
[     5.466] (--) Depth 24 pixmap format is 32 bpp
[     5.467] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.467] (II) NVIDIA:     access.
[     5.491] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     5.543] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.544] (==) NVIDIA(0): Backing store enabled
[     5.544] (==) NVIDIA(0): Silken mouse enabled
[     5.545] (==) NVIDIA(0): DPMS enabled
[     5.545] (II) Loading sub module "dri2"
[     5.545] (II) LoadModule: "dri2"
[     5.545] (II) Module "dri2" already built-in
[     5.545] (II) NVIDIA(0): [DRI2] Setup complete
[     5.545] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.545] (--) RandR disabled
[     5.549] (II) SELinux: Disabled on system
[     5.550] (II) Initializing extension GLX
[     5.550] (II) Indirect GLX disabled.
[     5.602] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.602] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.602] (II) LoadModule: "evdev"
[     5.603] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.605] (II) Module evdev: vendor="X.Org Foundation"
[     5.605]     compiled for 1.18.1, module version = 2.10.1
[     5.605]     Module class: X.Org XInput Driver
[     5.605]     ABI class: X.Org XInput driver, version 22.1
[     5.605] (II) Using input driver 'evdev' for 'Power Button'
[     5.605] (**) Power Button: always reports core events
[     5.605] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.605] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.605] (--) evdev: Power Button: Found keys
[     5.605] (II) evdev: Power Button: Configuring as keyboard
[     5.605] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.605] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.605] (**) Option "xkb_rules" "evdev"
[     5.605] (**) Option "xkb_model" "pc105"
[     5.605] (**) Option "xkb_layout" "us"
[     5.605] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.605] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.605] (II) Using input driver 'evdev' for 'Power Button'
[     5.605] (**) Power Button: always reports core events
[     5.605] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.605] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.605] (--) evdev: Power Button: Found keys
[     5.605] (II) evdev: Power Button: Configuring as keyboard
[     5.605] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.605] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.605] (**) Option "xkb_rules" "evdev"
[     5.605] (**) Option "xkb_model" "pc105"
[     5.605] (**) Option "xkb_layout" "us"
[     5.606] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.606] (II) No input driver specified, ignoring this device.
[     5.606] (II) This device may have been added with another device file.
[     5.606] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.606] (II) No input driver specified, ignoring this device.
[     5.606] (II) This device may have been added with another device file.
[     5.606] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.606] (II) No input driver specified, ignoring this device.
[     5.606] (II) This device may have been added with another device file.
[     5.607] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.607] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.607] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.607] (**) Logitech M570: always reports core events
[     5.607] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.607] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.607] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.607] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.607] (--) evdev: Logitech M570: Found relative axes
[     5.607] (--) evdev: Logitech M570: Found x and y relative axes
[     5.607] (II) evdev: Logitech M570: Configuring as mouse
[     5.607] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.607] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.607] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.607] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.607] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.607] (II) evdev: Logitech M570: initialized for relative axes.
[     5.607] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.607] (**) Logitech M570: (accel) acceleration profile 0
[     5.607] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.607] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.607] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.607] (II) No input driver specified, ignoring this device.
[     5.607] (II) This device may have been added with another device file.
[     5.608] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.608] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.608] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.608] (**) Logitech K360: always reports core events
[     5.608] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.608] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.608] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.608] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.608] (--) evdev: Logitech K360: Found relative axes
[     5.608] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.608] (--) evdev: Logitech K360: Found absolute axes
[     5.608] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.608] (--) evdev: Logitech K360: Found keys
[     5.608] (II) evdev: Logitech K360: Configuring as mouse
[     5.608] (II) evdev: Logitech K360: Configuring as keyboard
[     5.608] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.608] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.608] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.608] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.608] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.608] (**) Option "xkb_rules" "evdev"
[     5.608] (**) Option "xkb_model" "pc105"
[     5.608] (**) Option "xkb_layout" "us"
[     5.608] (II) evdev: Logitech K360: initialized for relative axes.
[     5.608] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.608] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.608] (**) Logitech K360: (accel) acceleration profile 0
[     5.608] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.608] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.608] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.608] (II) No input driver specified, ignoring this device.
[     5.609] (II) This device may have been added with another device file.
[     5.609] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.609] (II) No input driver specified, ignoring this device.
[     5.609] (II) This device may have been added with another device file.
[     5.609] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.609] (II) No input driver specified, ignoring this device.
[     5.609] (II) This device may have been added with another device file.
[     5.609] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.609] (II) No input driver specified, ignoring this device.
[     5.609] (II) This device may have been added with another device file.
[     5.609] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.609] (II) No input driver specified, ignoring this device.
[     5.609] (II) This device may have been added with another device file.
[     5.610] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.610] (II) No input driver specified, ignoring this device.
[     5.610] (II) This device may have been added with another device file.
[     5.610] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.610] (II) No input driver specified, ignoring this device.
[     5.610] (II) This device may have been added with another device file.
[     5.610] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.610] (II) No input driver specified, ignoring this device.
[     5.610] (II) This device may have been added with another device file.
[     5.610] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.610] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.610] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.610] (**) Eee PC WMI hotkeys: always reports core events
[     5.610] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.610] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.610] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.610] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.610] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.610] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.610] (**) Option "xkb_rules" "evdev"
[     5.610] (**) Option "xkb_model" "pc105"
[     5.610] (**) Option "xkb_layout" "us"
[     7.133] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.133] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.133] (--) NVIDIA(GPU-0): 
[     7.144] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.144] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.144] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.144] (--) NVIDIA(GPU-0): 
[     7.144] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.144] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.144] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.144] (--) NVIDIA(GPU-0): 
[     7.341] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.341] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.341] (--) NVIDIA(GPU-0): 
[     7.353] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.353] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.353] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.353] (--) NVIDIA(GPU-0): 
[     7.353] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.353] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.353] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.353] (--) NVIDIA(GPU-0): 
[     9.504] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     9.504] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     9.504] (--) NVIDIA(GPU-0): 
[     9.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     9.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     9.516] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     9.516] (--) NVIDIA(GPU-0): 
[     9.516] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.516] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.516] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.516] (--) NVIDIA(GPU-0): 
```

---

### Post by CatKiller on 2017-07-07
> **aviator1 said:**
> I don't know. 

What did the purge command that you actually ran say?

You can look at the commands you've previously run by pressing up on the command line.

---

### Post by aviator1 on 2017-07-07
> **CatKiller said:**
> What did the purge command that you actually ran say?

You can look at the commands you've previously run by pressing up on the command line.

dave@dave-desktop:~$ sudo apt-get purge nvidia-
nvidia-381             nvidia-opencl-icd-381  nvidia-settings
nvidia-common          nvidia-prime

---

### Post by CatKiller on 2017-07-07
> **aviator1 said:**
> dave@dave-desktop:~$ sudo apt-get purge nvidia-
nvidia-381             nvidia-opencl-icd-381  nvidia-settings
nvidia-common          nvidia-prime

OK, so it looks like you haven't purged them yet. You'll want to run ```
sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime
``` You see how that's taking the autocompleted suggestions and adding them to the command?

The command may want to remove some other things too. Some small number of additional, related, packages is to be expected. If it wants to remove hundreds and hundreds of additional packages, check back before you say yes.

---

### Post by aviator1 on 2017-07-07
> **CatKiller said:**
> OK, so it looks like you haven't purged them yet. You'll want to run ```
sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime
``` You see how that's taking the autocompleted suggestions and adding them to the command?

The command may want to remove some other things too. Some small number of additional, related, packages is to be expected. If it wants to remove hundreds and hundreds of additional packages, check back before you say yes.

Ran what you suggested.

Here is what happened.

```
dave@dave-desktop:~$ sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms libjansson4 libxnvctrl0 screen-resolution-extra
  xserver-xorg-legacy
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libcuda1-381* nvidia-381* nvidia-common* nvidia-opencl-icd-381*
  nvidia-prime* nvidia-settings*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 340 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 302405 files and directories currently installed.)
Removing libcuda1-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing nvidia-opencl-icd-381 (381.22-0ubuntu0~gpu16.04.2) ...
Purging configuration files for nvidia-opencl-icd-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing nvidia-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-381-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
INFO:Disable nvidia-381
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-381 (381.22-0ubuntu0~gpu16.04.2) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-common (1:0.4.17.2) ...
Purging configuration files for nvidia-common (1:0.4.17.2) ...
Removing nvidia-prime (0.8.2) ...
Purging configuration files for nvidia-prime (0.8.2) ...
Removing nvidia-settings (381.22-0ubuntu0~gpu16.04.1) ...
Purging configuration files for nvidia-settings (381.22-0ubuntu0~gpu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
dave@dave-desktop:~$
```

---

### Post by aviator1 on 2017-07-07
> **aviator1 said:**
> Ran what you suggested.

Here is what happened.

```
dave@dave-desktop:~$ sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms libjansson4 libxnvctrl0 screen-resolution-extra
  xserver-xorg-legacy
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libcuda1-381* nvidia-381* nvidia-common* nvidia-opencl-icd-381*
  nvidia-prime* nvidia-settings*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 340 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 302405 files and directories currently installed.)
Removing libcuda1-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing nvidia-opencl-icd-381 (381.22-0ubuntu0~gpu16.04.2) ...
Purging configuration files for nvidia-opencl-icd-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing nvidia-381 (381.22-0ubuntu0~gpu16.04.2) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-381-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-381-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
INFO:Disable nvidia-381
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-381 (381.22-0ubuntu0~gpu16.04.2) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-common (1:0.4.17.2) ...
Purging configuration files for nvidia-common (1:0.4.17.2) ...
Removing nvidia-prime (0.8.2) ...
Purging configuration files for nvidia-prime (0.8.2) ...
Removing nvidia-settings (381.22-0ubuntu0~gpu16.04.1) ...
Purging configuration files for nvidia-settings (381.22-0ubuntu0~gpu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
dave@dave-desktop:~$
```

I did a full shut down and restart and all is well. It did change the resolution as my page no longer fills my monitor screen. I'll get to that tomorrow.

I know it's late/early in Southend. I really appreciate your help with this. I will shut down for now, and report back tomorrow.

Regards

---

### Post by CatKiller on 2017-07-07
> **aviator1 said:**
> Ran what you suggested.

Here is what happened.

That all looks good. Fingers crossed for you!

---

### Post by aviator1 on 2017-07-08
I'm in trouble and need help again. I changed nothing since last night when i shut down. Cannot navigate in Thunderbird at all. it is locked.

Can only open 1 program at a time. Back to having to click on the menu toolbar in order to navigate. Multiple boots do not solve the issue.

Cannot navigate using the system icon and last night, have no way to change screen resolution.

I have no wat tp maximize/minimize on this page. I can only close it by using the X

Can get to Terminal by using control/alt/T but then it locks.

Thanks for any help.

```
[     4.799] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     4.799] X Protocol Version 11, Revision 0
[     4.799] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     4.799] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     4.799] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     4.799] Build Date: 02 November 2016  10:06:10PM
[     4.799] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.799] Current version of pixman: 0.33.6
[     4.799]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.799] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.799] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 07:44:49 2017
[     4.799] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.799] (==) No Layout section.  Using the first Screen section.
[     4.800] (==) No screen section available. Using defaults.
[     4.800] (**) |-->Screen "Default Screen Section" (0)
[     4.800] (**) |   |-->Monitor "<default monitor>"
[     4.800] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.800] (==) Automatically adding devices
[     4.800] (==) Automatically enabling devices
[     4.800] (==) Automatically adding GPU devices
[     4.800] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.800] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.800]     Entry deleted from font path.
[     4.800] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.800]     Entry deleted from font path.
[     4.800] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.800]     Entry deleted from font path.
[     4.800] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.800]     Entry deleted from font path.
[     4.800] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.800]     Entry deleted from font path.
[     4.800] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.800] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.800] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.800] (II) Loader magic: 0x55d35a95ddc0
[     4.800] (II) Module ABI versions:
[     4.800]     X.Org ANSI C Emulation: 0.4
[     4.800]     X.Org Video Driver: 20.0
[     4.800]     X.Org XInput driver : 22.1
[     4.800]     X.Org Server Extension : 9.0
[     4.801] (++) using VT number 7

[     4.801] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.802] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.802] (II) LoadModule: "glx"
[     4.802] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.810] (II) Module glx: vendor="X.Org Foundation"
[     4.810]     compiled for 1.18.4, module version = 1.0.0
[     4.810]     ABI class: X.Org Server Extension, version 9.0
[     4.810] (==) AIGLX enabled
[     4.811] (==) Matched nvidia as autoconfigured driver 0
[     4.811] (==) Matched nouveau as autoconfigured driver 1
[     4.811] (==) Matched modesetting as autoconfigured driver 2
[     4.811] (==) Matched fbdev as autoconfigured driver 3
[     4.811] (==) Matched vesa as autoconfigured driver 4
[     4.811] (==) Assigned the driver to the xf86ConfigLayout
[     4.811] (II) LoadModule: "nvidia"
[     4.811] (WW) Warning, couldn't open module nvidia
[     4.811] (II) UnloadModule: "nvidia"
[     4.811] (II) Unloading nvidia
[     4.811] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.811] (II) LoadModule: "nouveau"
[     4.811] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.812] (II) Module nouveau: vendor="X.Org Foundation"
[     4.812]     compiled for 1.18.1, module version = 1.0.12
[     4.812]     Module class: X.Org Video Driver
[     4.812]     ABI class: X.Org Video Driver, version 20.0
[     4.812] (II) LoadModule: "modesetting"
[     4.812] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.812] (II) Module modesetting: vendor="X.Org Foundation"
[     4.812]     compiled for 1.18.4, module version = 1.18.4
[     4.812]     Module class: X.Org Video Driver
[     4.812]     ABI class: X.Org Video Driver, version 20.0
[     4.812] (II) LoadModule: "fbdev"
[     4.812] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.812] (II) Module fbdev: vendor="X.Org Foundation"
[     4.812]     compiled for 1.18.1, module version = 0.4.4
[     4.812]     Module class: X.Org Video Driver
[     4.812]     ABI class: X.Org Video Driver, version 20.0
[     4.812] (II) LoadModule: "vesa"
[     4.812] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.812] (II) Module vesa: vendor="X.Org Foundation"
[     4.812]     compiled for 1.18.1, module version = 2.3.4
[     4.813]     Module class: X.Org Video Driver
[     4.813]     ABI class: X.Org Video Driver, version 20.0
[     4.813] (==) Matched nvidia as autoconfigured driver 0
[     4.813] (==) Matched nouveau as autoconfigured driver 1
[     4.813] (==) Matched modesetting as autoconfigured driver 2
[     4.813] (==) Matched fbdev as autoconfigured driver 3
[     4.813] (==) Matched vesa as autoconfigured driver 4
[     4.813] (==) Assigned the driver to the xf86ConfigLayout
[     4.813] (II) LoadModule: "nvidia"
[     4.813] (WW) Warning, couldn't open module nvidia
[     4.813] (II) UnloadModule: "nvidia"
[     4.813] (II) Unloading nvidia
[     4.813] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.813] (II) LoadModule: "nouveau"
[     4.813] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.813] (II) Module nouveau: vendor="X.Org Foundation"
[     4.813]     compiled for 1.18.1, module version = 1.0.12
[     4.813]     Module class: X.Org Video Driver
[     4.813]     ABI class: X.Org Video Driver, version 20.0
[     4.813] (II) UnloadModule: "nouveau"
[     4.813] (II) Unloading nouveau
[     4.813] (II) Failed to load module "nouveau" (already loaded, 0)
[     4.813] (II) LoadModule: "modesetting"
[     4.813] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.813] (II) Module modesetting: vendor="X.Org Foundation"
[     4.813]     compiled for 1.18.4, module version = 1.18.4
[     4.813]     Module class: X.Org Video Driver
[     4.813]     ABI class: X.Org Video Driver, version 20.0
[     4.813] (II) UnloadModule: "modesetting"
[     4.813] (II) Unloading modesetting
[     4.813] (II) Failed to load module "modesetting" (already loaded, 0)
[     4.813] (II) LoadModule: "fbdev"
[     4.813] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.813] (II) Module fbdev: vendor="X.Org Foundation"
[     4.813]     compiled for 1.18.1, module version = 0.4.4
[     4.813]     Module class: X.Org Video Driver
[     4.813]     ABI class: X.Org Video Driver, version 20.0
[     4.813] (II) UnloadModule: "fbdev"
[     4.813] (II) Unloading fbdev
[     4.813] (II) Failed to load module "fbdev" (already loaded, 0)
[     4.813] (II) LoadModule: "vesa"
[     4.813] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.813] (II) Module vesa: vendor="X.Org Foundation"
[     4.813]     compiled for 1.18.1, module version = 2.3.4
[     4.813]     Module class: X.Org Video Driver
[     4.813]     ABI class: X.Org Video Driver, version 20.0
[     4.813] (II) UnloadModule: "vesa"
[     4.813] (II) Unloading vesa
[     4.813] (II) Failed to load module "vesa" (already loaded, 0)
[     4.813] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     4.813] (II) NOUVEAU driver for NVIDIA chipset families :
[     4.813]     RIVA TNT        (NV04)
[     4.813]     RIVA TNT2       (NV05)
[     4.813]     GeForce 256     (NV10)
[     4.813]     GeForce 2       (NV11, NV15)
[     4.813]     GeForce 4MX     (NV17, NV18)
[     4.813]     GeForce 3       (NV20)
[     4.813]     GeForce 4Ti     (NV25, NV28)
[     4.814]     GeForce FX      (NV3x)
[     4.814]     GeForce 6       (NV4x)
[     4.814]     GeForce 7       (G7x)
[     4.814]     GeForce 8       (G8x)
[     4.814]     GeForce GTX 200 (NVA0)
[     4.814]     GeForce GTX 400 (NVC0)
[     4.814] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.814] (II) FBDEV: driver for framebuffer: fbdev
[     4.814] (II) VESA: driver for VESA chipsets: vesa
[     4.935] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.056] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.056] (EE) open /dev/dri/card0: No such file or directory
[     5.056] (EE) open /dev/dri/card0: No such file or directory
[     5.056] (WW) Falling back to old probe method for modesetting
[     5.056] (EE) open /dev/dri/card0: No such file or directory
[     5.056] (EE) open /dev/dri/card0: No such file or directory
[     5.056] (II) Loading sub module "fbdevhw"
[     5.056] (II) LoadModule: "fbdevhw"
[     5.056] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.056] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.056]     compiled for 1.18.4, module version = 0.0.2
[     5.056]     ABI class: X.Org Video Driver, version 20.0
[     5.056] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     5.056] (II) FBDEV(2): using default device
[     5.056] (WW) Falling back to old probe method for vesa
[     5.056] (EE) Screen 0 deleted because of no matching config section.
[     5.056] (II) UnloadModule: "modesetting"
[     5.056] (EE) Screen 0 deleted because of no matching config section.
[     5.056] (II) UnloadModule: "modesetting"
[     5.056] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.056] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.056] (==) FBDEV(0): RGB weight 888
[     5.056] (==) FBDEV(0): Default visual is TrueColor
[     5.056] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.056] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[     5.056] (II) FBDEV(0): checking modes against framebuffer device...
[     5.056] (II) FBDEV(0): checking modes against monitor...
[     5.056] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     5.056] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     5.056] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     5.056] (==) FBDEV(0): DPI set to (96, 96)
[     5.056] (II) Loading sub module "fb"
[     5.056] (II) LoadModule: "fb"
[     5.056] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.057] (II) Module fb: vendor="X.Org Foundation"
[     5.057]     compiled for 1.18.4, module version = 1.0.0
[     5.057]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.057] (**) FBDEV(0): using shadow framebuffer
[     5.057] (II) Loading sub module "shadow"
[     5.057] (II) LoadModule: "shadow"
[     5.057] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.058] (II) Module shadow: vendor="X.Org Foundation"
[     5.058]     compiled for 1.18.4, module version = 1.1.0
[     5.058]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.058] (II) UnloadModule: "vesa"
[     5.058] (II) Unloading vesa
[     5.058] (==) Depth 24 pixmap format is 32 bpp
[     5.058] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     5.060] (==) FBDEV(0): Backing store enabled
[     5.061] (==) FBDEV(0): DPMS enabled
[     5.061] (==) RandR enabled
[     5.065] (II) SELinux: Disabled on system
[     5.066] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.066] (EE) AIGLX: reverting to software rendering
[     5.182] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.182] (II) AIGLX: Loaded and initialized swrast
[     5.182] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.216] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.216] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.216] (II) LoadModule: "evdev"
[     5.216] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.218] (II) Module evdev: vendor="X.Org Foundation"
[     5.218]     compiled for 1.18.1, module version = 2.10.1
[     5.218]     Module class: X.Org XInput Driver
[     5.218]     ABI class: X.Org XInput driver, version 22.1
[     5.218] (II) Using input driver 'evdev' for 'Power Button'
[     5.218] (**) Power Button: always reports core events
[     5.218] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.218] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.218] (--) evdev: Power Button: Found keys
[     5.218] (II) evdev: Power Button: Configuring as keyboard
[     5.218] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.218] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.218] (**) Option "xkb_rules" "evdev"
[     5.218] (**) Option "xkb_model" "pc105"
[     5.218] (**) Option "xkb_layout" "us"
[     5.219] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.219] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.219] (II) Using input driver 'evdev' for 'Power Button'
[     5.219] (**) Power Button: always reports core events
[     5.219] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.219] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.219] (--) evdev: Power Button: Found keys
[     5.219] (II) evdev: Power Button: Configuring as keyboard
[     5.219] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.219] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.219] (**) Option "xkb_rules" "evdev"
[     5.219] (**) Option "xkb_model" "pc105"
[     5.219] (**) Option "xkb_layout" "us"
[     5.219] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.219] (II) No input driver specified, ignoring this device.
[     5.219] (II) This device may have been added with another device file.
[     5.219] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.219] (II) No input driver specified, ignoring this device.
[     5.219] (II) This device may have been added with another device file.
[     5.220] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.220] (II) No input driver specified, ignoring this device.
[     5.220] (II) This device may have been added with another device file.
[     5.220] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.220] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.220] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.220] (**) Logitech M570: always reports core events
[     5.220] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.220] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.220] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.220] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.220] (--) evdev: Logitech M570: Found relative axes
[     5.220] (--) evdev: Logitech M570: Found x and y relative axes
[     5.220] (II) evdev: Logitech M570: Configuring as mouse
[     5.220] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.220] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.220] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.220] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.220] (II) evdev: Logitech M570: initialized for relative axes.
[     5.220] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.220] (**) Logitech M570: (accel) acceleration profile 0
[     5.220] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.220] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.221] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.221] (II) No input driver specified, ignoring this device.
[     5.221] (II) This device may have been added with another device file.
[     5.221] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.221] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.221] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.221] (**) Logitech K360: always reports core events
[     5.221] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.221] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.221] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.221] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.221] (--) evdev: Logitech K360: Found relative axes
[     5.221] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.221] (--) evdev: Logitech K360: Found absolute axes
[     5.221] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.221] (--) evdev: Logitech K360: Found keys
[     5.221] (II) evdev: Logitech K360: Configuring as mouse
[     5.221] (II) evdev: Logitech K360: Configuring as keyboard
[     5.221] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.221] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.221] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.221] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.221] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.221] (**) Option "xkb_rules" "evdev"
[     5.221] (**) Option "xkb_model" "pc105"
[     5.221] (**) Option "xkb_layout" "us"
[     5.222] (II) evdev: Logitech K360: initialized for relative axes.
[     5.222] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.222] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.222] (**) Logitech K360: (accel) acceleration profile 0
[     5.222] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.222] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.222] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.222] (II) No input driver specified, ignoring this device.
[     5.222] (II) This device may have been added with another device file.
[     5.222] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.222] (II) No input driver specified, ignoring this device.
[     5.222] (II) This device may have been added with another device file.
[     5.222] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.222] (II) No input driver specified, ignoring this device.
[     5.222] (II) This device may have been added with another device file.
[     5.223] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.223] (II) No input driver specified, ignoring this device.
[     5.223] (II) This device may have been added with another device file.
[     5.223] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.223] (II) No input driver specified, ignoring this device.
[     5.223] (II) This device may have been added with another device file.
[     5.223] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.223] (II) No input driver specified, ignoring this device.
[     5.223] (II) This device may have been added with another device file.
[     5.223] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.223] (II) No input driver specified, ignoring this device.
[     5.223] (II) This device may have been added with another device file.
[     5.223] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.223] (II) No input driver specified, ignoring this device.
[     5.223] (II) This device may have been added with another device file.
[     5.224] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.224] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.224] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.224] (**) Eee PC WMI hotkeys: always reports core events
[     5.224] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.224] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.224] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.224] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.224] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.224] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.224] (**) Option "xkb_rules" "evdev"
[     5.224] (**) Option "xkb_model" "pc105"
[     5.224] (**) Option "xkb_layout" "us"
```

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> I'm in trouble and need help again. 

Did you reinstall nouveau and re-run its install scripts after you purged the nvidia drivers?

```
[     4.811] (==) Matched nvidia as autoconfigured driver 0
[     4.811] (==) Matched nouveau as autoconfigured driver 1
[     4.811] (==) Matched modesetting as autoconfigured driver 2
[     4.811] (==) Matched fbdev as autoconfigured driver 3
[     4.811] (==) Matched vesa as autoconfigured driver 4
[     4.811] (==) Assigned the driver to the xf86ConfigLayout
[     4.811] (II) LoadModule: "nvidia"
[     4.811] (WW) Warning, couldn't open module nvidia
[     4.811] (II) UnloadModule: "nvidia"
[     4.811] (II) Unloading nvidia
[     4.811] (EE) Failed to load module "nvidia" (module does not exist, 0)
```

When you were doing things before, did you change something in modules or xorg.conf?

---

### Post by aviator1 on 2017-07-08
No. All I did last night was shut down. I did have the screen resolution issue before shut down, but thought that might be simple to correct today.

As of right now, everything seems normal with navigation (5 reboots), however when I look at system settings/additional drivers, the one that was working last week is not selected. X.Org X Server is selected. I think the selection that was previously working id the NVIDIA Binary 381.22 (Open Source)

I still do not have any selection for changing screen resolution.

I do not know how to change any modules or xorg.

---

### Post by aviator1 on 2017-07-08
No. Do not know how to do that.

The last that I ran was ```

sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime
```

Things were OK after that except for the screen resolution.

UPDATE. I do have the capability now to navigate to additional drivers and make a selection, but did not want to change anything until I heard from you.

Thanks for your help.

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> No. All I did last night was shut down. I did have the screen resolution issue before shut down, but thought that might be simple to correct today.

OK, try to do so now. Hopefully the install script will go through and remove any remaining nvidia stuff.

>  As of right now, everything seems normal with navigation (5 reboots), however when I look at system settings/additional drivers, the one that was working last week is not selected. X.Org X Server is selected. I think the selection that was previously working id the NVIDIA Binary 381.22 (Open Source)

I still do not have any selection for changing screen resolution.

I do not know how to change any modules or xorg.

Well, something is still trying to load the nvidia stuff. It's failing to do so, obviously, because you've successfully uninstalled it, but it's still trying which means it's listed somewhere to try. I believe the usual place is /etc/modules for the kernel module and /etc/X11/xorg.conf for the driver itself. There could be other places too. It isn't clear which things you've tried in the past, which is why I asked.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> OK, try to do so now. Hopefully the install script will go through and remove any remaining nvidia stuff.



Well, something is still trying to load the nvidia stuff. It's failing to do so, obviously, because you've successfully uninstalled it, but it's still trying which means it's listed somewhere to try. I believe the usual place is /etc/modules for the kernel module and /etc/X11/xorg.conf for the driver itself. There could be other places too. It isn't clear which things you've tried in the past, which is why I asked.

So here is where we are.

I navigated to system settings/additional drivers and selected the NVIDIA Binary 381.22 (open source) driver. it appeared to load. There are other selctions, but did not want to change the selection for fear of further complicating the situation. The NVIDIA Binary 378.33 (open source) driver, may have been the one working previously. I just do not remember.

The screen resolution numbers did not change, but the browser now fits the screen again.

I shut down completely. Upon startup, I was back to the limited navigation situation. 2 reboots solved all the problems and it is operating normally. I suspect that if I shut down and restart, the same thing will happen.

I looked at, but did not run sudo apt-get purge nv TAB

Here is the result:

dave@dave-desktop:~$ sudo apt-get purge nvidia-
nvidia-381             nvidia-prime           
nvidia-opencl-icd-381  nvidia-settings        
dave@dave-desktop:~$ sudo apt-get purge nvidia-^C
dave@dave-desktop:~$ 


Thanks very much for your assistance.

Here is the latest xorg:
```
[     5.234] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     5.234] X Protocol Version 11, Revision 0
[     5.234] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     5.234] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     5.234] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     5.234] Build Date: 02 November 2016  10:06:10PM
[     5.234] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.234] Current version of pixman: 0.33.6
[     5.234]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.234] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.234] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 09:51:22 2017
[     5.235] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.235] (==) No Layout section.  Using the first Screen section.
[     5.235] (==) No screen section available. Using defaults.
[     5.235] (**) |-->Screen "Default Screen Section" (0)
[     5.235] (**) |   |-->Monitor "<default monitor>"
[     5.236] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.236] (==) Automatically adding devices
[     5.236] (==) Automatically enabling devices
[     5.236] (==) Automatically adding GPU devices
[     5.236] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.236] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.236]     Entry deleted from font path.
[     5.236] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.236]     Entry deleted from font path.
[     5.236] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.236]     Entry deleted from font path.
[     5.236] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.236]     Entry deleted from font path.
[     5.236] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.236]     Entry deleted from font path.
[     5.236] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.236] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.236] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.236] (II) Loader magic: 0x55fe89889dc0
[     5.236] (II) Module ABI versions:
[     5.236]     X.Org ANSI C Emulation: 0.4
[     5.236]     X.Org Video Driver: 20.0
[     5.236]     X.Org XInput driver : 22.1
[     5.236]     X.Org Server Extension : 9.0
[     5.236] (++) using VT number 7

[     5.236] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.237] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.238] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.238] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     5.238] (II) "glx" will be loaded by default.
[     5.238] (II) LoadModule: "glx"
[     5.238] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.299] (II) Module glx: vendor="NVIDIA Corporation"
[     5.299]     compiled for 4.0.2, module version = 1.0.0
[     5.299]     Module class: X.Org Server Extension
[     5.299] (II) NVIDIA GLX Module  381.22  Thu May  4 00:17:15 PDT 2017
[     5.299] (==) Matched nvidia as autoconfigured driver 0
[     5.299] (==) Matched nouveau as autoconfigured driver 1
[     5.299] (==) Matched nvidia as autoconfigured driver 2
[     5.299] (==) Matched nouveau as autoconfigured driver 3
[     5.299] (==) Matched modesetting as autoconfigured driver 4
[     5.299] (==) Matched fbdev as autoconfigured driver 5
[     5.299] (==) Matched vesa as autoconfigured driver 6
[     5.299] (==) Assigned the driver to the xf86ConfigLayout
[     5.299] (II) LoadModule: "nvidia"
[     5.299] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.303] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.303]     compiled for 4.0.2, module version = 1.0.0
[     5.303]     Module class: X.Org Video Driver
[     5.303] (II) LoadModule: "nouveau"
[     5.304] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.308] (II) Module nouveau: vendor="X.Org Foundation"
[     5.308]     compiled for 1.18.1, module version = 1.0.12
[     5.308]     Module class: X.Org Video Driver
[     5.308]     ABI class: X.Org Video Driver, version 20.0
[     5.308] (II) LoadModule: "modesetting"
[     5.309] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.309] (II) Module modesetting: vendor="X.Org Foundation"
[     5.309]     compiled for 1.18.4, module version = 1.18.4
[     5.309]     Module class: X.Org Video Driver
[     5.309]     ABI class: X.Org Video Driver, version 20.0
[     5.309] (II) LoadModule: "fbdev"
[     5.309] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.309] (II) Module fbdev: vendor="X.Org Foundation"
[     5.309]     compiled for 1.18.1, module version = 0.4.4
[     5.309]     Module class: X.Org Video Driver
[     5.309]     ABI class: X.Org Video Driver, version 20.0
[     5.309] (II) LoadModule: "vesa"
[     5.309] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.309] (II) Module vesa: vendor="X.Org Foundation"
[     5.309]     compiled for 1.18.1, module version = 2.3.4
[     5.309]     Module class: X.Org Video Driver
[     5.309]     ABI class: X.Org Video Driver, version 20.0
[     5.309] (II) NVIDIA dlloader X Driver  381.22  Wed May  3 23:53:41 PDT 2017
[     5.309] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.310] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.310] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.310]     RIVA TNT        (NV04)
[     5.310]     RIVA TNT2       (NV05)
[     5.310]     GeForce 256     (NV10)
[     5.310]     GeForce 2       (NV11, NV15)
[     5.310]     GeForce 4MX     (NV17, NV18)
[     5.310]     GeForce 3       (NV20)
[     5.310]     GeForce 4Ti     (NV25, NV28)
[     5.310]     GeForce FX      (NV3x)
[     5.310]     GeForce 6       (NV4x)
[     5.310]     GeForce 7       (G7x)
[     5.310]     GeForce 8       (G8x)
[     5.310]     GeForce GTX 200 (NVA0)
[     5.310]     GeForce GTX 400 (NVC0)
[     5.310] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.310] (II) FBDEV: driver for framebuffer: fbdev
[     5.310] (II) VESA: driver for VESA chipsets: vesa
[     5.311] (II) Loading sub module "fb"
[     5.311] (II) LoadModule: "fb"
[     5.311] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.312] (II) Module fb: vendor="X.Org Foundation"
[     5.312]     compiled for 1.18.4, module version = 1.0.0
[     5.312]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.312] (II) Loading sub module "wfb"
[     5.312] (II) LoadModule: "wfb"
[     5.312] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.312] (II) Module wfb: vendor="X.Org Foundation"
[     5.312]     compiled for 1.18.4, module version = 1.0.0
[     5.312]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.312] (II) Loading sub module "ramdac"
[     5.313] (II) LoadModule: "ramdac"
[     5.313] (II) Module "ramdac" already built-in
[     5.315] (WW) Falling back to old probe method for modesetting
[     5.315] (WW) Falling back to old probe method for fbdev
[     5.315] (II) Loading sub module "fbdevhw"
[     5.315] (II) LoadModule: "fbdevhw"
[     5.315] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.315] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.315]     compiled for 1.18.4, module version = 0.0.2
[     5.315]     ABI class: X.Org Video Driver, version 20.0
[     5.315] (WW) Falling back to old probe method for vesa
[     5.315] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.315] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.315] (==) NVIDIA(0): RGB weight 888
[     5.315] (==) NVIDIA(0): Default visual is TrueColor
[     5.315] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.316] (**) NVIDIA(0): Enabling 2D acceleration
[     5.666] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     5.666] (--) NVIDIA(0):     CRT-0
[     5.666] (--) NVIDIA(0):     DFP-0 (boot)
[     5.666] (--) NVIDIA(0):     DFP-1
[     5.667] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     5.667] (--) NVIDIA(0): Memory: 4194304 kBytes
[     5.667] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.56
[     5.667] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     5.668] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     5.668] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     5.668] (--) NVIDIA(GPU-0): 
[     5.680] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     5.680] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     5.680] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     5.680] (--) NVIDIA(GPU-0): 
[     5.680] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     5.680] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     5.680] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     5.680] (--) NVIDIA(GPU-0): 
[     5.682] (==) NVIDIA(0): 
[     5.682] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     5.682] (==) NVIDIA(0):     will be used as the requested mode.
[     5.682] (==) NVIDIA(0): 
[     5.683] (II) NVIDIA(0): Validated MetaModes:
[     5.683] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     5.683] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     5.692] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     5.692] (--) NVIDIA(0):     option
[     5.692] (II) UnloadModule: "nouveau"
[     5.692] (II) Unloading nouveau
[     5.692] (II) UnloadModule: "modesetting"
[     5.692] (II) Unloading modesetting
[     5.692] (II) UnloadModule: "fbdev"
[     5.692] (II) Unloading fbdev
[     5.692] (II) UnloadSubModule: "fbdevhw"
[     5.692] (II) Unloading fbdevhw
[     5.692] (II) UnloadModule: "vesa"
[     5.692] (II) Unloading vesa
[     5.692] (--) Depth 24 pixmap format is 32 bpp
[     5.693] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.693] (II) NVIDIA:     access.
[     5.717] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     5.770] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.770] (==) NVIDIA(0): Backing store enabled
[     5.770] (==) NVIDIA(0): Silken mouse enabled
[     5.771] (==) NVIDIA(0): DPMS enabled
[     5.771] (II) Loading sub module "dri2"
[     5.771] (II) LoadModule: "dri2"
[     5.771] (II) Module "dri2" already built-in
[     5.771] (II) NVIDIA(0): [DRI2] Setup complete
[     5.771] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.772] (--) RandR disabled
[     5.775] (II) SELinux: Disabled on system
[     5.776] (II) Initializing extension GLX
[     5.776] (II) Indirect GLX disabled.
[     5.824] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.824] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.824] (II) LoadModule: "evdev"
[     5.824] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.825] (II) Module evdev: vendor="X.Org Foundation"
[     5.825]     compiled for 1.18.1, module version = 2.10.1
[     5.825]     Module class: X.Org XInput Driver
[     5.825]     ABI class: X.Org XInput driver, version 22.1
[     5.825] (II) Using input driver 'evdev' for 'Power Button'
[     5.825] (**) Power Button: always reports core events
[     5.825] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.825] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.825] (--) evdev: Power Button: Found keys
[     5.825] (II) evdev: Power Button: Configuring as keyboard
[     5.825] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.825] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.825] (**) Option "xkb_rules" "evdev"
[     5.825] (**) Option "xkb_model" "pc105"
[     5.825] (**) Option "xkb_layout" "us"
[     5.825] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.825] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.825] (II) Using input driver 'evdev' for 'Power Button'
[     5.825] (**) Power Button: always reports core events
[     5.825] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.825] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.825] (--) evdev: Power Button: Found keys
[     5.825] (II) evdev: Power Button: Configuring as keyboard
[     5.825] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.825] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.825] (**) Option "xkb_rules" "evdev"
[     5.825] (**) Option "xkb_model" "pc105"
[     5.825] (**) Option "xkb_layout" "us"
[     5.826] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.826] (II) No input driver specified, ignoring this device.
[     5.826] (II) This device may have been added with another device file.
[     5.826] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.826] (II) No input driver specified, ignoring this device.
[     5.826] (II) This device may have been added with another device file.
[     5.826] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.826] (II) No input driver specified, ignoring this device.
[     5.826] (II) This device may have been added with another device file.
[     5.826] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.826] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.826] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.826] (**) Logitech M570: always reports core events
[     5.827] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.827] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.827] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.827] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.827] (--) evdev: Logitech M570: Found relative axes
[     5.827] (--) evdev: Logitech M570: Found x and y relative axes
[     5.827] (II) evdev: Logitech M570: Configuring as mouse
[     5.827] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.827] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.827] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.827] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.827] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.827] (II) evdev: Logitech M570: initialized for relative axes.
[     5.827] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.827] (**) Logitech M570: (accel) acceleration profile 0
[     5.827] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.827] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.827] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.827] (II) No input driver specified, ignoring this device.
[     5.827] (II) This device may have been added with another device file.
[     5.828] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.828] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.828] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.828] (**) Logitech K360: always reports core events
[     5.828] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.828] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.828] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.828] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.828] (--) evdev: Logitech K360: Found relative axes
[     5.828] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.828] (--) evdev: Logitech K360: Found absolute axes
[     5.828] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.828] (--) evdev: Logitech K360: Found keys
[     5.828] (II) evdev: Logitech K360: Configuring as mouse
[     5.828] (II) evdev: Logitech K360: Configuring as keyboard
[     5.828] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.828] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.828] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.828] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.828] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.828] (**) Option "xkb_rules" "evdev"
[     5.828] (**) Option "xkb_model" "pc105"
[     5.828] (**) Option "xkb_layout" "us"
[     5.828] (II) evdev: Logitech K360: initialized for relative axes.
[     5.828] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.828] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.828] (**) Logitech K360: (accel) acceleration profile 0
[     5.828] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.828] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.828] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.828] (II) No input driver specified, ignoring this device.
[     5.828] (II) This device may have been added with another device file.
[     5.828] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.828] (II) No input driver specified, ignoring this device.
[     5.828] (II) This device may have been added with another device file.
[     5.829] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.829] (II) No input driver specified, ignoring this device.
[     5.829] (II) This device may have been added with another device file.
[     5.829] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.829] (II) No input driver specified, ignoring this device.
[     5.829] (II) This device may have been added with another device file.
[     5.829] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.829] (II) No input driver specified, ignoring this device.
[     5.829] (II) This device may have been added with another device file.
[     5.829] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.829] (II) No input driver specified, ignoring this device.
[     5.829] (II) This device may have been added with another device file.
[     5.830] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.830] (II) No input driver specified, ignoring this device.
[     5.830] (II) This device may have been added with another device file.
[     5.830] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.830] (II) No input driver specified, ignoring this device.
[     5.830] (II) This device may have been added with another device file.
[     5.830] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.830] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.830] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.830] (**) Eee PC WMI hotkeys: always reports core events
[     5.830] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.830] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.830] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.830] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.830] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.830] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.830] (**) Option "xkb_rules" "evdev"
[     5.830] (**) Option "xkb_model" "pc105"
[     5.830] (**) Option "xkb_layout" "us"
[     7.340] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.340] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.340] (--) NVIDIA(GPU-0): 
[     7.356] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.356] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.356] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.356] (--) NVIDIA(GPU-0): 
[     7.357] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.357] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.357] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.357] (--) NVIDIA(GPU-0): 
[     7.571] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     7.571] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.571] (--) NVIDIA(GPU-0): 
[     7.583] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     7.583] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     7.583] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     7.583] (--) NVIDIA(GPU-0): 
[     7.583] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     7.583] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     7.583] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     7.583] (--) NVIDIA(GPU-0): 
[     9.543] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     9.543] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     9.543] (--) NVIDIA(GPU-0): 
[     9.555] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[     9.555] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[     9.555] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[     9.555] (--) NVIDIA(GPU-0): 
[     9.555] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.555] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.555] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.555] (--) NVIDIA(GPU-0): 
[    21.477] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    21.477] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    21.477] (--) NVIDIA(GPU-0): 
[    21.488] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): connected
[    21.488] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): Internal TMDS
[    21.488] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VE278 (DFP-0): 340.0 MHz maximum pixel clock
[    21.488] (--) NVIDIA(GPU-0): 
[    21.488] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    21.488] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    21.488] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    21.488] (--) NVIDIA(GPU-0): 
```

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> So here is where we are.

I navigated to system settings/additional drivers and selected the NVIDIA Binary 381.22 (open source) driver.

Why did you do that? We were trying to get rid of the nvidia stuff and only use nouveau so that you wouldn't have conflicts.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> Why did you do that? We were trying to get rid of the nvidia stuff and only use nouveau so that you wouldn't have conflicts.

Here is what you advised. "OK, try to do so now. Hopefully the install script will go through and remove any remaining nvidia stuff." I thought you were referring to my ability to navigate through the system settings.

After running 
sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime, all the latest problems began.

Should I go to terminal and do the purge thing again?

Thanks.

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> Here is what you advised. "OK, try to do so now. Hopefully the install script will go through and remove any remaining nvidia stuff." I thought you were referring to my ability to navigate through the system settings.

No, I was referring to the dpkg-reconfigure... whatever the nouveau package was called.

> After running 
sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime, all the latest problems began.

Should I go to terminal and do the purge thing again?

Your latest problem seems to be exactly the same as the problem you've had all along, as far as I can tell.

I suspect that it's likely that it's caused by trying to run the nvidia stuff at the same time as the nouveau stuff, which is why I've spent the last how ever many posts trying to get you to uninstall the nvidia stuff and just have the nouveau stuff. I thought that was clear.

It might not be the cause, in which case, you would have the same symptoms regardless of whether you cleared the conflict. But we don't know, because you haven't yet cleared the conflict. Regardless of what's causing your UI problem, running both the nvidia driver and the nouveau driver at the same time is a Bad Plan.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> No, I was referring to the dpkg-reconfigure... whatever the nouveau package was called.



Your latest problem seems to be exactly the same as the problem you've had all along, as far as I can tell.

I suspect that it's likely that it's caused by trying to run the nvidia stuff at the same time as the nouveau stuff, which is why I've spent the last how ever many posts trying to get you to uninstall the nvidia stuff and just have the nouveau stuff. I thought that was clear.

It might not be the cause, in which case, you would have the same symptoms regardless of whether you cleared the conflict. But we don't know, because you haven't yet cleared the conflict. Regardless of what's causing your UI problem, running both the nvidia driver and the nouveau driver at the same time is a Bad Plan.

I agree with your suspicions. 

I apologize for not understanding your instructions. I have been an Ubuntu user for many year, but I am not well versed in things like this.

I will do the sudo apt-get purge nv TAB again. That actually seemed to fix things. So far, it doesn't seem the nouveau drivers work even when they are without the NVidia drivers.

I appreciate the time and effort you have put in to help me with this.

---

### Post by aviator1 on 2017-07-08
Follow up:

dave@dave-desktop:~$ sudo apt-get purge nvidia-
nvidia-381             nvidia-prime           
nvidia-opencl-icd-381  nvidia-settings        
dave@dave-desktop:~$ sudo apt-get purge nvidia-
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> 
dave@dave-desktop:~$ sudo apt-get purge nvidia-
[sudo] password for dave: 


You need to actually complete the command. Like you did before.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> You need to actually complete the command. Like you did before.

To complete the command, do you mean:
sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime

---

### Post by CatKiller on 2017-07-08
No, because not all of those are installed now. It's already told you the ways that the command can be completed. I've already explained how Tab-complete works.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> No, because not all of those are installed now. It's already told you the ways that the command can be completed. I've already explained how Tab-complete works.

Thanks for all that you have attempted to help me with.

I apologize for any inconvenience I may have caused by not following your instructions properly.

I will go back and review the procedures.

---

### Post by CatKiller on 2017-07-08
My mistake; I only saw the two packages on the line previously. I was distracted at the time. I apologise.

You are correct that you have all five installed. They should all be removed with the command that you suggested. Then check to see that the nouveau package is still installed. Then re-run the dpkg-reconfigure to run nouveau's install scripts on the chance that they will remove the traces of nvidia stuff.

Then when you reboot check the logs to see if nvidia is still being run somewhere. If it is, we'll have to find where it's being called from so that we can stop it. It might be modules, or it might be a .conf file. Hopefully you'll only be running nouveau, though, and we'll be able to see if the conflict is the cause of your problem.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> My mistake; I only saw the two packages on the line previously. I was distracted at the time. I apologise.

You are correct that you have all five installed. They should all be removed with the command that you suggested. Then check to see that the nouveau package is still installed. Then re-run the dpkg-reconfigure to run nouveau's install scripts on the chance that they will remove the traces of nvidia stuff.

Then when you reboot check the logs to see if nvidia is still being run somewhere. If it is, we'll have to find where it's being called from so that we can stop it. It might be modules, or it might be a .conf file. Hopefully you'll only be running nouveau, though, and we'll be able to see if the conflict is the cause of your problem.

I ran sudo apt-get purge nvidia-381 nvidia-opencl-icd-381 nvidia-settings nvidia-common nvidia-prime and rebooted.

Navigations is working. The Nouveau driver is now selected in the radio button in system settings/additional drivers.

However, I am back to not having my browser fill the entire screen, and have no selection capabilities under the display selection.

Can you give me the dpkg-reconfigure instructions again. I am looking for them. Is it sudo dpkg-reconfigure xserver-xorg-video-nouveau ? Thanks.

Here is the latest xorg info:

```
[     4.816] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     4.816] X Protocol Version 11, Revision 0
[     4.816] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     4.816] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     4.816] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     4.816] Build Date: 02 November 2016  10:06:10PM
[     4.816] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.816] Current version of pixman: 0.33.6
[     4.816]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.816] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.816] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 13:34:14 2017
[     4.816] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.816] (==) No Layout section.  Using the first Screen section.
[     4.816] (==) No screen section available. Using defaults.
[     4.816] (**) |-->Screen "Default Screen Section" (0)
[     4.816] (**) |   |-->Monitor "<default monitor>"
[     4.817] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.817] (==) Automatically adding devices
[     4.817] (==) Automatically enabling devices
[     4.817] (==) Automatically adding GPU devices
[     4.817] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.817] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.817]     Entry deleted from font path.
[     4.817] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.817]     Entry deleted from font path.
[     4.817] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.817]     Entry deleted from font path.
[     4.817] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.817]     Entry deleted from font path.
[     4.817] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.817]     Entry deleted from font path.
[     4.817] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.817] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.817] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.817] (II) Loader magic: 0x55b79059bdc0
[     4.817] (II) Module ABI versions:
[     4.817]     X.Org ANSI C Emulation: 0.4
[     4.817]     X.Org Video Driver: 20.0
[     4.817]     X.Org XInput driver : 22.1
[     4.817]     X.Org Server Extension : 9.0
[     4.818] (++) using VT number 7

[     4.818] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.819] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.819] (II) LoadModule: "glx"
[     4.819] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.827] (II) Module glx: vendor="X.Org Foundation"
[     4.827]     compiled for 1.18.4, module version = 1.0.0
[     4.827]     ABI class: X.Org Server Extension, version 9.0
[     4.827] (==) AIGLX enabled
[     4.827] (==) Matched nvidia as autoconfigured driver 0
[     4.827] (==) Matched nouveau as autoconfigured driver 1
[     4.827] (==) Matched modesetting as autoconfigured driver 2
[     4.827] (==) Matched fbdev as autoconfigured driver 3
[     4.827] (==) Matched vesa as autoconfigured driver 4
[     4.827] (==) Assigned the driver to the xf86ConfigLayout
[     4.827] (II) LoadModule: "nvidia"
[     4.827] (WW) Warning, couldn't open module nvidia
[     4.827] (II) UnloadModule: "nvidia"
[     4.827] (II) Unloading nvidia
[     4.827] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.827] (II) LoadModule: "nouveau"
[     4.827] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.829] (II) Module nouveau: vendor="X.Org Foundation"
[     4.829]     compiled for 1.18.1, module version = 1.0.12
[     4.829]     Module class: X.Org Video Driver
[     4.829]     ABI class: X.Org Video Driver, version 20.0
[     4.829] (II) LoadModule: "modesetting"
[     4.829] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.829] (II) Module modesetting: vendor="X.Org Foundation"
[     4.829]     compiled for 1.18.4, module version = 1.18.4
[     4.829]     Module class: X.Org Video Driver
[     4.829]     ABI class: X.Org Video Driver, version 20.0
[     4.829] (II) LoadModule: "fbdev"
[     4.829] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.829] (II) Module fbdev: vendor="X.Org Foundation"
[     4.829]     compiled for 1.18.1, module version = 0.4.4
[     4.829]     Module class: X.Org Video Driver
[     4.829]     ABI class: X.Org Video Driver, version 20.0
[     4.829] (II) LoadModule: "vesa"
[     4.829] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.829] (II) Module vesa: vendor="X.Org Foundation"
[     4.829]     compiled for 1.18.1, module version = 2.3.4
[     4.829]     Module class: X.Org Video Driver
[     4.829]     ABI class: X.Org Video Driver, version 20.0
[     4.829] (==) Matched nvidia as autoconfigured driver 0
[     4.829] (==) Matched nouveau as autoconfigured driver 1
[     4.829] (==) Matched modesetting as autoconfigured driver 2
[     4.829] (==) Matched fbdev as autoconfigured driver 3
[     4.829] (==) Matched vesa as autoconfigured driver 4
[     4.829] (==) Assigned the driver to the xf86ConfigLayout
[     4.829] (II) LoadModule: "nvidia"
[     4.829] (WW) Warning, couldn't open module nvidia
[     4.829] (II) UnloadModule: "nvidia"
[     4.829] (II) Unloading nvidia
[     4.829] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     4.829] (II) LoadModule: "nouveau"
[     4.829] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.829] (II) Module nouveau: vendor="X.Org Foundation"
[     4.829]     compiled for 1.18.1, module version = 1.0.12
[     4.829]     Module class: X.Org Video Driver
[     4.829]     ABI class: X.Org Video Driver, version 20.0
[     4.829] (II) UnloadModule: "nouveau"
[     4.830] (II) Unloading nouveau
[     4.830] (II) Failed to load module "nouveau" (already loaded, 0)
[     4.830] (II) LoadModule: "modesetting"
[     4.830] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.830] (II) Module modesetting: vendor="X.Org Foundation"
[     4.830]     compiled for 1.18.4, module version = 1.18.4
[     4.830]     Module class: X.Org Video Driver
[     4.830]     ABI class: X.Org Video Driver, version 20.0
[     4.830] (II) UnloadModule: "modesetting"
[     4.830] (II) Unloading modesetting
[     4.830] (II) Failed to load module "modesetting" (already loaded, 0)
[     4.830] (II) LoadModule: "fbdev"
[     4.830] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.830] (II) Module fbdev: vendor="X.Org Foundation"
[     4.830]     compiled for 1.18.1, module version = 0.4.4
[     4.830]     Module class: X.Org Video Driver
[     4.830]     ABI class: X.Org Video Driver, version 20.0
[     4.830] (II) UnloadModule: "fbdev"
[     4.830] (II) Unloading fbdev
[     4.830] (II) Failed to load module "fbdev" (already loaded, 0)
[     4.830] (II) LoadModule: "vesa"
[     4.830] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.830] (II) Module vesa: vendor="X.Org Foundation"
[     4.830]     compiled for 1.18.1, module version = 2.3.4
[     4.830]     Module class: X.Org Video Driver
[     4.830]     ABI class: X.Org Video Driver, version 20.0
[     4.830] (II) UnloadModule: "vesa"
[     4.830] (II) Unloading vesa
[     4.830] (II) Failed to load module "vesa" (already loaded, 0)
[     4.830] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     4.830] (II) NOUVEAU driver for NVIDIA chipset families :
[     4.830]     RIVA TNT        (NV04)
[     4.830]     RIVA TNT2       (NV05)
[     4.830]     GeForce 256     (NV10)
[     4.830]     GeForce 2       (NV11, NV15)
[     4.830]     GeForce 4MX     (NV17, NV18)
[     4.830]     GeForce 3       (NV20)
[     4.830]     GeForce 4Ti     (NV25, NV28)
[     4.830]     GeForce FX      (NV3x)
[     4.830]     GeForce 6       (NV4x)
[     4.830]     GeForce 7       (G7x)
[     4.830]     GeForce 8       (G8x)
[     4.830]     GeForce GTX 200 (NVA0)
[     4.830]     GeForce GTX 400 (NVC0)
[     4.830] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.830] (II) FBDEV: driver for framebuffer: fbdev
[     4.830] (II) VESA: driver for VESA chipsets: vesa
[     4.951] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.073] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.073] (EE) open /dev/dri/card0: No such file or directory
[     5.073] (EE) open /dev/dri/card0: No such file or directory
[     5.073] (WW) Falling back to old probe method for modesetting
[     5.073] (EE) open /dev/dri/card0: No such file or directory
[     5.073] (EE) open /dev/dri/card0: No such file or directory
[     5.073] (II) Loading sub module "fbdevhw"
[     5.073] (II) LoadModule: "fbdevhw"
[     5.073] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.073] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.073]     compiled for 1.18.4, module version = 0.0.2
[     5.073]     ABI class: X.Org Video Driver, version 20.0
[     5.073] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     5.073] (II) FBDEV(2): using default device
[     5.073] (WW) Falling back to old probe method for vesa
[     5.073] (EE) Screen 0 deleted because of no matching config section.
[     5.073] (II) UnloadModule: "modesetting"
[     5.073] (EE) Screen 0 deleted because of no matching config section.
[     5.073] (II) UnloadModule: "modesetting"
[     5.073] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.073] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.073] (==) FBDEV(0): RGB weight 888
[     5.073] (==) FBDEV(0): Default visual is TrueColor
[     5.073] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.073] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[     5.073] (II) FBDEV(0): checking modes against framebuffer device...
[     5.073] (II) FBDEV(0): checking modes against monitor...
[     5.073] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     5.073] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     5.073] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     5.073] (==) FBDEV(0): DPI set to (96, 96)
[     5.073] (II) Loading sub module "fb"
[     5.073] (II) LoadModule: "fb"
[     5.073] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.073] (II) Module fb: vendor="X.Org Foundation"
[     5.073]     compiled for 1.18.4, module version = 1.0.0
[     5.073]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.074] (**) FBDEV(0): using shadow framebuffer
[     5.074] (II) Loading sub module "shadow"
[     5.074] (II) LoadModule: "shadow"
[     5.074] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.074] (II) Module shadow: vendor="X.Org Foundation"
[     5.074]     compiled for 1.18.4, module version = 1.1.0
[     5.074]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.074] (II) UnloadModule: "vesa"
[     5.074] (II) Unloading vesa
[     5.074] (==) Depth 24 pixmap format is 32 bpp
[     5.074] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     5.077] (==) FBDEV(0): Backing store enabled
[     5.078] (==) FBDEV(0): DPMS enabled
[     5.078] (==) RandR enabled
[     5.081] (II) SELinux: Disabled on system
[     5.082] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.082] (EE) AIGLX: reverting to software rendering
[     5.199] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.200] (II) AIGLX: Loaded and initialized swrast
[     5.200] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.234] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.234] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.234] (II) LoadModule: "evdev"
[     5.234] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.234] (II) Module evdev: vendor="X.Org Foundation"
[     5.234]     compiled for 1.18.1, module version = 2.10.1
[     5.234]     Module class: X.Org XInput Driver
[     5.234]     ABI class: X.Org XInput driver, version 22.1
[     5.234] (II) Using input driver 'evdev' for 'Power Button'
[     5.234] (**) Power Button: always reports core events
[     5.234] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.234] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.234] (--) evdev: Power Button: Found keys
[     5.234] (II) evdev: Power Button: Configuring as keyboard
[     5.234] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.234] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.234] (**) Option "xkb_rules" "evdev"
[     5.234] (**) Option "xkb_model" "pc105"
[     5.234] (**) Option "xkb_layout" "us"
[     5.235] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.235] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.235] (II) Using input driver 'evdev' for 'Power Button'
[     5.235] (**) Power Button: always reports core events
[     5.235] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.235] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.235] (--) evdev: Power Button: Found keys
[     5.235] (II) evdev: Power Button: Configuring as keyboard
[     5.235] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.235] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.235] (**) Option "xkb_rules" "evdev"
[     5.235] (**) Option "xkb_model" "pc105"
[     5.235] (**) Option "xkb_layout" "us"
[     5.235] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.235] (II) No input driver specified, ignoring this device.
[     5.235] (II) This device may have been added with another device file.
[     5.235] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.235] (II) No input driver specified, ignoring this device.
[     5.235] (II) This device may have been added with another device file.
[     5.236] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.236] (II) No input driver specified, ignoring this device.
[     5.236] (II) This device may have been added with another device file.
[     5.236] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.236] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.236] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.236] (**) Logitech M570: always reports core events
[     5.236] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.236] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.236] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.236] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.236] (--) evdev: Logitech M570: Found relative axes
[     5.236] (--) evdev: Logitech M570: Found x and y relative axes
[     5.236] (II) evdev: Logitech M570: Configuring as mouse
[     5.236] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.236] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.236] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.236] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.236] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.236] (II) evdev: Logitech M570: initialized for relative axes.
[     5.236] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.236] (**) Logitech M570: (accel) acceleration profile 0
[     5.236] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.236] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.237] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.237] (II) No input driver specified, ignoring this device.
[     5.237] (II) This device may have been added with another device file.
[     5.237] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.237] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.237] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.237] (**) Logitech K360: always reports core events
[     5.237] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.237] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.237] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.237] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.237] (--) evdev: Logitech K360: Found relative axes
[     5.237] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.237] (--) evdev: Logitech K360: Found absolute axes
[     5.237] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.237] (--) evdev: Logitech K360: Found keys
[     5.237] (II) evdev: Logitech K360: Configuring as mouse
[     5.237] (II) evdev: Logitech K360: Configuring as keyboard
[     5.237] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.237] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.237] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.237] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.237] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.237] (**) Option "xkb_rules" "evdev"
[     5.237] (**) Option "xkb_model" "pc105"
[     5.237] (**) Option "xkb_layout" "us"
[     5.238] (II) evdev: Logitech K360: initialized for relative axes.
[     5.238] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.238] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.238] (**) Logitech K360: (accel) acceleration profile 0
[     5.238] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.238] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.238] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.238] (II) No input driver specified, ignoring this device.
[     5.238] (II) This device may have been added with another device file.
[     5.238] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.238] (II) No input driver specified, ignoring this device.
[     5.238] (II) This device may have been added with another device file.
[     5.238] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.238] (II) No input driver specified, ignoring this device.
[     5.238] (II) This device may have been added with another device file.
[     5.239] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.239] (II) No input driver specified, ignoring this device.
[     5.239] (II) This device may have been added with another device file.
[     5.239] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.239] (II) No input driver specified, ignoring this device.
[     5.239] (II) This device may have been added with another device file.
[     5.239] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.239] (II) No input driver specified, ignoring this device.
[     5.239] (II) This device may have been added with another device file.
[     5.239] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.239] (II) No input driver specified, ignoring this device.
[     5.239] (II) This device may have been added with another device file.
[     5.239] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.239] (II) No input driver specified, ignoring this device.
[     5.239] (II) This device may have been added with another device file.
[     5.240] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.240] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.240] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.240] (**) Eee PC WMI hotkeys: always reports core events
[     5.240] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.240] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.240] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.240] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.240] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.240] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.240] (**) Option "xkb_rules" "evdev"
[     5.240] (**) Option "xkb_model" "pc105"
[     5.240] (**) Option "xkb_layout" "us"
```

---

### Post by CatKiller on 2017-07-08
> **aviator1 said:**
> Can you give me the dpkg-reconfigure instructions again. I am looking for them. Is it sudo dpkg-reconfigure xserver-xorg-video-nouveau ? Thanks.

That sounds about right, yes.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> That sounds about right, yes.

I ran sudo dpkg-reconfigure xserver-xorg-video-nouveau  from terminal and nothing happened.

dave@dave-desktop:~$ sudo dpkg-reconfigure xserver-xorg-video-nouveau
[sudo] password for dave: 
dave@dave-desktop:~$

---

### Post by CatKiller on 2017-07-08
It wouldn't necessarily provide output. That doesn't mean nothing happened.

---

### Post by aviator1 on 2017-07-08
> **CatKiller said:**
> It wouldn't necessarily provide output. That doesn't mean nothing happened.

OK, but how can I get my display to use the entire screen?

Is there a reason to use the Nouveau driver instead of an NVidia driver if they are both open source? 

I understand the problem that BOTH cannot be used. I think we have that fixed. 

Thanks for your kind assistance.

---

### Post by aviator1 on 2017-07-08
Before we go any farther.

I did not touch or change anything since I ran sudo dpkg-reconfigure xserver-xorg-video-nouveau

I did a complete shut down and have reverted to the original problem.

Here is the xorg info:

```
[     5.304] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     5.304] X Protocol Version 11, Revision 0
[     5.304] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     5.304] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     5.304] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     5.304] Build Date: 02 November 2016  10:06:10PM
[     5.304] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.304] Current version of pixman: 0.33.6
[     5.304]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.304] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.304] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 15:49:59 2017
[     5.304] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.304] (==) No Layout section.  Using the first Screen section.
[     5.304] (==) No screen section available. Using defaults.
[     5.304] (**) |-->Screen "Default Screen Section" (0)
[     5.304] (**) |   |-->Monitor "<default monitor>"
[     5.305] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.305] (==) Automatically adding devices
[     5.305] (==) Automatically enabling devices
[     5.305] (==) Automatically adding GPU devices
[     5.305] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.305] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.305] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.305] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.305] (II) Loader magic: 0x55f0f5a7fdc0
[     5.305] (II) Module ABI versions:
[     5.305]     X.Org ANSI C Emulation: 0.4
[     5.305]     X.Org Video Driver: 20.0
[     5.305]     X.Org XInput driver : 22.1
[     5.305]     X.Org Server Extension : 9.0
[     5.306] (++) using VT number 7

[     5.306] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.307] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.307] (II) LoadModule: "glx"
[     5.307] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.315] (II) Module glx: vendor="X.Org Foundation"
[     5.315]     compiled for 1.18.4, module version = 1.0.0
[     5.315]     ABI class: X.Org Server Extension, version 9.0
[     5.315] (==) AIGLX enabled
[     5.315] (==) Matched nvidia as autoconfigured driver 0
[     5.315] (==) Matched nouveau as autoconfigured driver 1
[     5.315] (==) Matched modesetting as autoconfigured driver 2
[     5.315] (==) Matched fbdev as autoconfigured driver 3
[     5.315] (==) Matched vesa as autoconfigured driver 4
[     5.315] (==) Assigned the driver to the xf86ConfigLayout
[     5.315] (II) LoadModule: "nvidia"
[     5.316] (WW) Warning, couldn't open module nvidia
[     5.316] (II) UnloadModule: "nvidia"
[     5.316] (II) Unloading nvidia
[     5.316] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     5.316] (II) LoadModule: "nouveau"
[     5.316] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.317] (II) Module nouveau: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 1.0.12
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "modesetting"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.317] (II) Module modesetting: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.4, module version = 1.18.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "fbdev"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.317] (II) Module fbdev: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 0.4.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "vesa"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.317] (II) Module vesa: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 2.3.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (==) Matched nvidia as autoconfigured driver 0
[     5.317] (==) Matched nouveau as autoconfigured driver 1
[     5.317] (==) Matched modesetting as autoconfigured driver 2
[     5.317] (==) Matched fbdev as autoconfigured driver 3
[     5.317] (==) Matched vesa as autoconfigured driver 4
[     5.317] (==) Assigned the driver to the xf86ConfigLayout
[     5.317] (II) LoadModule: "nvidia"
[     5.318] (WW) Warning, couldn't open module nvidia
[     5.318] (II) UnloadModule: "nvidia"
[     5.318] (II) Unloading nvidia
[     5.318] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     5.318] (II) LoadModule: "nouveau"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.318] (II) Module nouveau: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 1.0.12
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "nouveau"
[     5.318] (II) Unloading nouveau
[     5.318] (II) Failed to load module "nouveau" (already loaded, 0)
[     5.318] (II) LoadModule: "modesetting"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.318] (II) Module modesetting: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.4, module version = 1.18.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "modesetting"
[     5.318] (II) Unloading modesetting
[     5.318] (II) Failed to load module "modesetting" (already loaded, 0)
[     5.318] (II) LoadModule: "fbdev"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.318] (II) Module fbdev: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 0.4.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "fbdev"
[     5.318] (II) Unloading fbdev
[     5.318] (II) Failed to load module "fbdev" (already loaded, 0)
[     5.318] (II) LoadModule: "vesa"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.318] (II) Module vesa: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 2.3.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "vesa"
[     5.318] (II) Unloading vesa
[     5.318] (II) Failed to load module "vesa" (already loaded, 0)
[     5.318] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.318] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.318]     RIVA TNT        (NV04)
[     5.318]     RIVA TNT2       (NV05)
[     5.318]     GeForce 256     (NV10)
[     5.318]     GeForce 2       (NV11, NV15)
[     5.318]     GeForce 4MX     (NV17, NV18)
[     5.318]     GeForce 3       (NV20)
[     5.318]     GeForce 4Ti     (NV25, NV28)
[     5.318]     GeForce FX      (NV3x)
[     5.318]     GeForce 6       (NV4x)
[     5.318]     GeForce 7       (G7x)
[     5.318]     GeForce 8       (G8x)
[     5.318]     GeForce GTX 200 (NVA0)
[     5.318]     GeForce GTX 400 (NVC0)
[     5.318] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.318] (II) FBDEV: driver for framebuffer: fbdev
[     5.318] (II) VESA: driver for VESA chipsets: vesa
[     5.440] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.561] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (WW) Falling back to old probe method for modesetting
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (II) Loading sub module "fbdevhw"
[     5.561] (II) LoadModule: "fbdevhw"
[     5.561] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.561] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.561]     compiled for 1.18.4, module version = 0.0.2
[     5.561]     ABI class: X.Org Video Driver, version 20.0
[     5.561] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     5.561] (II) FBDEV(2): using default device
[     5.561] (WW) Falling back to old probe method for vesa
[     5.561] (EE) Screen 0 deleted because of no matching config section.
[     5.561] (II) UnloadModule: "modesetting"
[     5.561] (EE) Screen 0 deleted because of no matching config section.
[     5.561] (II) UnloadModule: "modesetting"
[     5.561] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.561] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.561] (==) FBDEV(0): RGB weight 888
[     5.561] (==) FBDEV(0): Default visual is TrueColor
[     5.561] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.561] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[     5.561] (II) FBDEV(0): checking modes against framebuffer device...
[     5.561] (II) FBDEV(0): checking modes against monitor...
[     5.561] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     5.561] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     5.561] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     5.561] (==) FBDEV(0): DPI set to (96, 96)
[     5.561] (II) Loading sub module "fb"
[     5.561] (II) LoadModule: "fb"
[     5.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.562] (II) Module fb: vendor="X.Org Foundation"
[     5.562]     compiled for 1.18.4, module version = 1.0.0
[     5.562]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.562] (**) FBDEV(0): using shadow framebuffer
[     5.562] (II) Loading sub module "shadow"
[     5.562] (II) LoadModule: "shadow"
[     5.562] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.562] (II) Module shadow: vendor="X.Org Foundation"
[     5.562]     compiled for 1.18.4, module version = 1.1.0
[     5.562]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.562] (II) UnloadModule: "vesa"
[     5.562] (II) Unloading vesa
[     5.563] (==) Depth 24 pixmap format is 32 bpp
[     5.563] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     5.565] (==) FBDEV(0): Backing store enabled
[     5.566] (==) FBDEV(0): DPMS enabled
[     5.566] (==) RandR enabled
[     5.570] (II) SELinux: Disabled on system
[     5.571] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.571] (EE) AIGLX: reverting to software rendering
[     5.688] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.689] (II) AIGLX: Loaded and initialized swrast
[     5.689] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.722] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.722] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.722] (II) LoadModule: "evdev"
[     5.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.723] (II) Module evdev: vendor="X.Org Foundation"
[     5.723]     compiled for 1.18.1, module version = 2.10.1
[     5.723]     Module class: X.Org XInput Driver
[     5.723]     ABI class: X.Org XInput driver, version 22.1
[     5.723] (II) Using input driver 'evdev' for 'Power Button'
[     5.723] (**) Power Button: always reports core events
[     5.723] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.723] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.723] (--) evdev: Power Button: Found keys
[     5.723] (II) evdev: Power Button: Configuring as keyboard
[     5.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.723] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.723] (**) Option "xkb_rules" "evdev"
[     5.723] (**) Option "xkb_model" "pc105"
[     5.723] (**) Option "xkb_layout" "us"
[     5.723] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.723] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.723] (II) Using input driver 'evdev' for 'Power Button'
[     5.723] (**) Power Button: always reports core events
[     5.723] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.723] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.723] (--) evdev: Power Button: Found keys
[     5.723] (II) evdev: Power Button: Configuring as keyboard
[     5.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.723] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.723] (**) Option "xkb_rules" "evdev"
[     5.723] (**) Option "xkb_model" "pc105"
[     5.723] (**) Option "xkb_layout" "us"
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.725] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.725] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.725] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.725] (**) Logitech M570: always reports core events
[     5.725] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.725] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.725] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.725] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.725] (--) evdev: Logitech M570: Found relative axes
[     5.725] (--) evdev: Logitech M570: Found x and y relative axes
[     5.725] (II) evdev: Logitech M570: Configuring as mouse
[     5.725] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.725] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.725] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.725] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.725] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.725] (II) evdev: Logitech M570: initialized for relative axes.
[     5.725] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.725] (**) Logitech M570: (accel) acceleration profile 0
[     5.725] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.725] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.725] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.725] (II) No input driver specified, ignoring this device.
[     5.725] (II) This device may have been added with another device file.
[     5.726] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.726] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.726] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.726] (**) Logitech K360: always reports core events
[     5.726] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.726] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.726] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.726] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.726] (--) evdev: Logitech K360: Found relative axes
[     5.726] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.726] (--) evdev: Logitech K360: Found absolute axes
[     5.726] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.726] (--) evdev: Logitech K360: Found keys
[     5.726] (II) evdev: Logitech K360: Configuring as mouse
[     5.726] (II) evdev: Logitech K360: Configuring as keyboard
[     5.726] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.726] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.726] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.726] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.726] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.726] (**) Option "xkb_rules" "evdev"
[     5.726] (**) Option "xkb_model" "pc105"
[     5.726] (**) Option "xkb_layout" "us"
[     5.726] (II) evdev: Logitech K360: initialized for relative axes.
[     5.726] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.726] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.726] (**) Logitech K360: (accel) acceleration profile 0
[     5.726] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.726] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.728] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.728] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.728] (**) Eee PC WMI hotkeys: always reports core events
[     5.728] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.728] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.728] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.728] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.728] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.728] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.728] (**) Option "xkb_rules" "evdev"
[     5.728] (**) Option "xkb_model" "pc105"
[     5.728] (**) Option "xkb_layout" "us"
```

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> Before we go any farther.

I did not touch or change anything since I ran sudo dpkg-reconfigure xserver-xorg-video-nouveau

I did a complete shut down and have reverted to the original problem.

Here is the xorg info:

```
[     5.304] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     5.304] X Protocol Version 11, Revision 0
[     5.304] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     5.304] Current Operating System: Linux dave-desktop 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
[     5.304] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-83-generic root=UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 ro quiet splash vt.handoff=7
[     5.304] Build Date: 02 November 2016  10:06:10PM
[     5.304] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.304] Current version of pixman: 0.33.6
[     5.304]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.304] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.304] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 15:49:59 2017
[     5.304] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.304] (==) No Layout section.  Using the first Screen section.
[     5.304] (==) No screen section available. Using defaults.
[     5.304] (**) |-->Screen "Default Screen Section" (0)
[     5.304] (**) |   |-->Monitor "<default monitor>"
[     5.305] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.305] (==) Automatically adding devices
[     5.305] (==) Automatically enabling devices
[     5.305] (==) Automatically adding GPU devices
[     5.305] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.305] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.305]     Entry deleted from font path.
[     5.305] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.305] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.305] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.305] (II) Loader magic: 0x55f0f5a7fdc0
[     5.305] (II) Module ABI versions:
[     5.305]     X.Org ANSI C Emulation: 0.4
[     5.305]     X.Org Video Driver: 20.0
[     5.305]     X.Org XInput driver : 22.1
[     5.305]     X.Org Server Extension : 9.0
[     5.306] (++) using VT number 7

[     5.306] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.307] (--) PCI:*(0:1:0:0) 10de:0fc1:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.307] (II) LoadModule: "glx"
[     5.307] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.315] (II) Module glx: vendor="X.Org Foundation"
[     5.315]     compiled for 1.18.4, module version = 1.0.0
[     5.315]     ABI class: X.Org Server Extension, version 9.0
[     5.315] (==) AIGLX enabled
[     5.315] (==) Matched nvidia as autoconfigured driver 0
[     5.315] (==) Matched nouveau as autoconfigured driver 1
[     5.315] (==) Matched modesetting as autoconfigured driver 2
[     5.315] (==) Matched fbdev as autoconfigured driver 3
[     5.315] (==) Matched vesa as autoconfigured driver 4
[     5.315] (==) Assigned the driver to the xf86ConfigLayout
[     5.315] (II) LoadModule: "nvidia"
[     5.316] (WW) Warning, couldn't open module nvidia
[     5.316] (II) UnloadModule: "nvidia"
[     5.316] (II) Unloading nvidia
[     5.316] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     5.316] (II) LoadModule: "nouveau"
[     5.316] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.317] (II) Module nouveau: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 1.0.12
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "modesetting"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.317] (II) Module modesetting: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.4, module version = 1.18.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "fbdev"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.317] (II) Module fbdev: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 0.4.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (II) LoadModule: "vesa"
[     5.317] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.317] (II) Module vesa: vendor="X.Org Foundation"
[     5.317]     compiled for 1.18.1, module version = 2.3.4
[     5.317]     Module class: X.Org Video Driver
[     5.317]     ABI class: X.Org Video Driver, version 20.0
[     5.317] (==) Matched nvidia as autoconfigured driver 0
[     5.317] (==) Matched nouveau as autoconfigured driver 1
[     5.317] (==) Matched modesetting as autoconfigured driver 2
[     5.317] (==) Matched fbdev as autoconfigured driver 3
[     5.317] (==) Matched vesa as autoconfigured driver 4
[     5.317] (==) Assigned the driver to the xf86ConfigLayout
[     5.317] (II) LoadModule: "nvidia"
[     5.318] (WW) Warning, couldn't open module nvidia
[     5.318] (II) UnloadModule: "nvidia"
[     5.318] (II) Unloading nvidia
[     5.318] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     5.318] (II) LoadModule: "nouveau"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.318] (II) Module nouveau: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 1.0.12
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "nouveau"
[     5.318] (II) Unloading nouveau
[     5.318] (II) Failed to load module "nouveau" (already loaded, 0)
[     5.318] (II) LoadModule: "modesetting"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.318] (II) Module modesetting: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.4, module version = 1.18.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "modesetting"
[     5.318] (II) Unloading modesetting
[     5.318] (II) Failed to load module "modesetting" (already loaded, 0)
[     5.318] (II) LoadModule: "fbdev"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.318] (II) Module fbdev: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 0.4.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "fbdev"
[     5.318] (II) Unloading fbdev
[     5.318] (II) Failed to load module "fbdev" (already loaded, 0)
[     5.318] (II) LoadModule: "vesa"
[     5.318] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.318] (II) Module vesa: vendor="X.Org Foundation"
[     5.318]     compiled for 1.18.1, module version = 2.3.4
[     5.318]     Module class: X.Org Video Driver
[     5.318]     ABI class: X.Org Video Driver, version 20.0
[     5.318] (II) UnloadModule: "vesa"
[     5.318] (II) Unloading vesa
[     5.318] (II) Failed to load module "vesa" (already loaded, 0)
[     5.318] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[     5.318] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.318]     RIVA TNT        (NV04)
[     5.318]     RIVA TNT2       (NV05)
[     5.318]     GeForce 256     (NV10)
[     5.318]     GeForce 2       (NV11, NV15)
[     5.318]     GeForce 4MX     (NV17, NV18)
[     5.318]     GeForce 3       (NV20)
[     5.318]     GeForce 4Ti     (NV25, NV28)
[     5.318]     GeForce FX      (NV3x)
[     5.318]     GeForce 6       (NV4x)
[     5.318]     GeForce 7       (G7x)
[     5.318]     GeForce 8       (G8x)
[     5.318]     GeForce GTX 200 (NVA0)
[     5.318]     GeForce GTX 400 (NVC0)
[     5.318] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.318] (II) FBDEV: driver for framebuffer: fbdev
[     5.318] (II) VESA: driver for VESA chipsets: vesa
[     5.440] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.561] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (WW) Falling back to old probe method for modesetting
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (EE) open /dev/dri/card0: No such file or directory
[     5.561] (II) Loading sub module "fbdevhw"
[     5.561] (II) LoadModule: "fbdevhw"
[     5.561] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.561] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.561]     compiled for 1.18.4, module version = 0.0.2
[     5.561]     ABI class: X.Org Video Driver, version 20.0
[     5.561] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     5.561] (II) FBDEV(2): using default device
[     5.561] (WW) Falling back to old probe method for vesa
[     5.561] (EE) Screen 0 deleted because of no matching config section.
[     5.561] (II) UnloadModule: "modesetting"
[     5.561] (EE) Screen 0 deleted because of no matching config section.
[     5.561] (II) UnloadModule: "modesetting"
[     5.561] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.561] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.561] (==) FBDEV(0): RGB weight 888
[     5.561] (==) FBDEV(0): Default visual is TrueColor
[     5.561] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.561] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[     5.561] (II) FBDEV(0): checking modes against framebuffer device...
[     5.561] (II) FBDEV(0): checking modes against monitor...
[     5.561] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     5.561] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     5.561] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     5.561] (==) FBDEV(0): DPI set to (96, 96)
[     5.561] (II) Loading sub module "fb"
[     5.561] (II) LoadModule: "fb"
[     5.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.562] (II) Module fb: vendor="X.Org Foundation"
[     5.562]     compiled for 1.18.4, module version = 1.0.0
[     5.562]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.562] (**) FBDEV(0): using shadow framebuffer
[     5.562] (II) Loading sub module "shadow"
[     5.562] (II) LoadModule: "shadow"
[     5.562] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.562] (II) Module shadow: vendor="X.Org Foundation"
[     5.562]     compiled for 1.18.4, module version = 1.1.0
[     5.562]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.562] (II) UnloadModule: "vesa"
[     5.562] (II) Unloading vesa
[     5.563] (==) Depth 24 pixmap format is 32 bpp
[     5.563] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     5.565] (==) FBDEV(0): Backing store enabled
[     5.566] (==) FBDEV(0): DPMS enabled
[     5.566] (==) RandR enabled
[     5.570] (II) SELinux: Disabled on system
[     5.571] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.571] (EE) AIGLX: reverting to software rendering
[     5.688] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.689] (II) AIGLX: Loaded and initialized swrast
[     5.689] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.722] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.722] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.722] (II) LoadModule: "evdev"
[     5.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.723] (II) Module evdev: vendor="X.Org Foundation"
[     5.723]     compiled for 1.18.1, module version = 2.10.1
[     5.723]     Module class: X.Org XInput Driver
[     5.723]     ABI class: X.Org XInput driver, version 22.1
[     5.723] (II) Using input driver 'evdev' for 'Power Button'
[     5.723] (**) Power Button: always reports core events
[     5.723] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.723] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.723] (--) evdev: Power Button: Found keys
[     5.723] (II) evdev: Power Button: Configuring as keyboard
[     5.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.723] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.723] (**) Option "xkb_rules" "evdev"
[     5.723] (**) Option "xkb_model" "pc105"
[     5.723] (**) Option "xkb_layout" "us"
[     5.723] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.723] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.723] (II) Using input driver 'evdev' for 'Power Button'
[     5.723] (**) Power Button: always reports core events
[     5.723] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.723] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.723] (--) evdev: Power Button: Found keys
[     5.723] (II) evdev: Power Button: Configuring as keyboard
[     5.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.723] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.723] (**) Option "xkb_rules" "evdev"
[     5.723] (**) Option "xkb_model" "pc105"
[     5.723] (**) Option "xkb_layout" "us"
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.724] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.725] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[     5.725] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[     5.725] (II) Using input driver 'evdev' for 'Logitech M570'
[     5.725] (**) Logitech M570: always reports core events
[     5.725] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[     5.725] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[     5.725] (--) evdev: Logitech M570: Found 20 mouse buttons
[     5.725] (--) evdev: Logitech M570: Found scroll wheel(s)
[     5.725] (--) evdev: Logitech M570: Found relative axes
[     5.725] (--) evdev: Logitech M570: Found x and y relative axes
[     5.725] (II) evdev: Logitech M570: Configuring as mouse
[     5.725] (II) evdev: Logitech M570: Adding scrollwheel support
[     5.725] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[     5.725] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.725] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[     5.725] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[     5.725] (II) evdev: Logitech M570: initialized for relative axes.
[     5.725] (**) Logitech M570: (accel) keeping acceleration scheme 1
[     5.725] (**) Logitech M570: (accel) acceleration profile 0
[     5.725] (**) Logitech M570: (accel) acceleration factor: 2.000
[     5.725] (**) Logitech M570: (accel) acceleration threshold: 4
[     5.725] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[     5.725] (II) No input driver specified, ignoring this device.
[     5.725] (II) This device may have been added with another device file.
[     5.726] (II) config/udev: Adding input device Logitech K360 (/dev/input/event3)
[     5.726] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[     5.726] (II) Using input driver 'evdev' for 'Logitech K360'
[     5.726] (**) Logitech K360: always reports core events
[     5.726] (**) evdev: Logitech K360: Device: "/dev/input/event3"
[     5.726] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[     5.726] (--) evdev: Logitech K360: Found 1 mouse buttons
[     5.726] (--) evdev: Logitech K360: Found scroll wheel(s)
[     5.726] (--) evdev: Logitech K360: Found relative axes
[     5.726] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[     5.726] (--) evdev: Logitech K360: Found absolute axes
[     5.726] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[     5.726] (--) evdev: Logitech K360: Found keys
[     5.726] (II) evdev: Logitech K360: Configuring as mouse
[     5.726] (II) evdev: Logitech K360: Configuring as keyboard
[     5.726] (II) evdev: Logitech K360: Adding scrollwheel support
[     5.726] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[     5.726] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.726] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0007/0003:046D:4004.0008/input/input6/event3"
[     5.726] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 9)
[     5.726] (**) Option "xkb_rules" "evdev"
[     5.726] (**) Option "xkb_model" "pc105"
[     5.726] (**) Option "xkb_layout" "us"
[     5.726] (II) evdev: Logitech K360: initialized for relative axes.
[     5.726] (WW) evdev: Logitech K360: ignoring absolute axes.
[     5.726] (**) Logitech K360: (accel) keeping acceleration scheme 1
[     5.726] (**) Logitech K360: (accel) acceleration profile 0
[     5.726] (**) Logitech K360: (accel) acceleration factor: 2.000
[     5.726] (**) Logitech K360: (accel) acceleration threshold: 4
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.727] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     5.727] (II) No input driver specified, ignoring this device.
[     5.727] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     5.728] (II) No input driver specified, ignoring this device.
[     5.728] (II) This device may have been added with another device file.
[     5.728] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event12)
[     5.728] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.728] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.728] (**) Eee PC WMI hotkeys: always reports core events
[     5.728] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event12"
[     5.728] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.728] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.728] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.728] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input15/event12"
[     5.728] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     5.728] (**) Option "xkb_rules" "evdev"
[     5.728] (**) Option "xkb_model" "pc105"
[     5.728] (**) Option "xkb_layout" "us"
```

Hi aviator1 lets see if this will help point to a solution:
From the terminal run this:
```
inxi -G
```
paste back so we can have a look please.

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Hi aviator1 lets see if this will help point to a solution:
From the terminal run this:
```
inxi -G
```
paste back so we can have a look please.

```
dave@dave-desktop:~$ inxi -G
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi
dave@dave-desktop:~$ 
```

---

### Post by #&amp;thj^% on 2017-07-08
So ok run this:
```
sudo apt install inxi
```
It is very light weight system tool.
Mine shows this:
```
inxi -G
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 381.22

```

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> So ok run this:
```
sudo apt install inxi
```
It is very light weight system tool.
Mine shows this:
```
inxi -G
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 381.22

```

Done. Now what?

```
Graphics:  Card: NVIDIA GK107 [GeForce GT 640]
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) FAILED: nouveau
           Resolution: 1920x1080@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 12.0.6
dave@dave-desktop:~$ 
```

---

### Post by #&amp;thj^% on 2017-07-08
paste back the return of:
```
inxi -G
```
Please. :)

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> paste back the return of:
```
inxi -G
```
Please. :)

Here it is:

```
dave@dave-desktop:~$ inxi -G
Graphics:  Card: NVIDIA GK107 [GeForce GT 640]
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) FAILED: nouveau
           Resolution: 1920x1080@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 12.0.6
dave@dave-desktop:~$ inxi -G
Graphics:  Card: NVIDIA GK107 [GeForce GT 640]
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) FAILED: nouveau
           Resolution: 1920x1080@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 12.0.6
dave@dave-desktop:~$ 


```

---

### Post by #&amp;thj^% on 2017-07-08
There is the problem:
```
FAILED: nouveau
```
Now let's look at this also.
```
nano /etc/default/grub
```
paste back here again.
EDIT Also this one:
```
apt policy xserver-xorg-video-nouveau
```
Paste back both if you would be as kind.

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> There is the problem:
```
FAILED: nouveau
```
Now let's look at this also.
```
nano /etc/default/grub
```
paste back here again.

```
  GNU nano 2.5.3           File: /etc/default/grub                              

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
                [ Read 34 lines (Warning: No write permission) ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line


```

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> ```
  GNU nano 2.5.3           File: /etc/default/grub                              

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
                [ Read 34 lines (Warning: No write permission) ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line


```

OK Great... I also need to see this one also:
```
apt policy xserver-xorg-video-nouveau
```
Then we will make some adjustments.

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> OK Great... I also need to see this one also:
```
apt policy xserver-xorg-video-nouveau
```
Then we will make some adjustments.

```
dave@dave-desktop:~$ apt policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: 1:1.0.12-1build2
  Candidate: 1:1.0.12-1build2
  Version table:
 *** 1:1.0.12-1build2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
dave@dave-desktop:~$ 



```

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> ```
dave@dave-desktop:~$ apt policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: 1:1.0.12-1build2
  Candidate: 1:1.0.12-1build2
  Version table:
 *** 1:1.0.12-1build2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
dave@dave-desktop:~$ 



```
Nice Thanks! We will now edit this file via:
```
sudo nano /etc/default/grub
```
Look for your line that reads like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And change to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save with key combo (ctrl+o) and hit enter...then exit nano with key combo  (ctrl+x) 
Now Reboot your system for the change to take.
But maybe we should take a second look at the file first via:
```
gedit /etc/default/grub
```
paste back again just for Safety.

---

### Post by aviator1 on 2017-07-08
How do I go about editing the file? Terminal? Do not know. Thanks.

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> How do I go about editing the file? Terminal? Do not know. Thanks.
Well against my better judgment we will just use gedit then...much easier for newer users.
```
sudo -H gedit /etc/default/grub
```
Make the change i showed...now save the edited file and close.
I would still like to see the file after you closed it with.
```
gedit /etc/default/grub
```

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Well against my better judgment we will just use gedit then...much easier for newer users.
```
sudo -H gedit /etc/default/grub
```
Make the change i showed...now save the edited file and close.
I would still like to see the file after you closed it with.
```
gedit /etc/default/grub
```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by aviator1 on 2017-07-08
Standing by to reboot if the above is correct.

---

### Post by #&amp;thj^% on 2017-07-08
Thank You Sir.
Now reboot your system.
Hopefully it won't blow up...hehehe :D...just a joke.
Is the resolution any better now?

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Thank You Sir.
Now reboot your system.
Hopefully it won't blow up...hehehe :D...just a joke.
Is the resolution any better now?

Well. after the smoke cleared......nothing changed.

I had to boot twice in order to get full navigation, the display still does not fill the screen, and I still have no selection under the system settings/displays area.

Thanks very much for your help.

---

### Post by aviator1 on 2017-07-08
Background info. I don't think I have ever used the Nouveau drivers. I have always had an NVidia driver. I mistakenly selected a newer NVidia driver last week (When all this trouble started). When I switched back, using system settings/additiional drivers is when the Nouveau issues came up. Don't know if any of that matters now. If I were to change to the old NVidia drive using system settings/Additioanl drivers, the display would be OK, but then the Nouveau and NVidia togther issue might still be here.

---

### Post by #&amp;thj^% on 2017-07-08
Maybe some left overs that did not get removed.
Lets have a peek at this then... run one line at  a time:
```
cd /etc/X11
ls
```
post back here again please.

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Maybe some left overs that did not get removed.
Lets have a peek at this then... run one line at  a time:
```
cd /etc/X11
ls
```
post back here again please.

```
dave@dave-desktop:~$ cd /etc/X11
dave@dave-desktop:/etc/X11$ 


```

```
dave@dave-desktop:~$ ls
2012 RTBAV Seminar ODP.odp
2016-2020 Current-1.ods
2016 Onward EXP.ods
AMFED
Amortizations
Are You Ready
Attendance-1.ods
bacon tart.odt
Baldwin County ICPC Chaplains.ods
Baptist F&M June 24 2000.odt
BCBS ClaimStatement.ods
bee flowers.ods
bee flowers.odt
BHBA
Calibre Library
Chaplaincy
Chaplaincy Manual-1.docx
Chaplaincy Manual-1.odt
cloy ancestry chart.ods
Colonial Documents
Dave29SepFRBC.MP3
Dec Income Statement-WS.xlsx
Desktop
dispo 1.JPG
Documents
Downloads
download?use_mirror=ncu.1
dwhelper
Edington 10-3-18.ods
Edington 2015
Edington January 4 2016.odt
Edington January 4 2017.odt
editington 29 Aug 2014.odt
examples.desktop
familypreparednessplan.pdf
FEMA_emergency_gasifier.pdf
file:
Financial Passwords.ods
fontconfig
FRBC29Sep2013ppt-1.odp
FRBC29Sep2013ppt.pptx
FRBC 8 Oct 14.odt
Good Pictures
gunserialnumbers.ods
Handbook_of_Biomass_Downdraft_Gasifier_Engine_Systems.pdf
Health Insurance
Home Protection Booklet.doc
&#9654; How a Revolver Works - YouTube.mp4
Hummingbird Project.ods
IB School List.ods
IvanParker-1.pdf-pages.jpg
IvanParker_PromoPicture_8x10.pdf
jason bill of sale.odt
K400 Series Use and Care Guide.pdf
kdenlive
lawmowermanual.pdf
libflashplayer.so
LilandDaveMineola130ct13.mp3
LJR Music
LJR Music-1
LTS food.ods
Lynx-DVR
marriage statement.odt
MJ
Music
NVIDIA-Linux-x86_64-358.16.run
Old Firefox Data
Pictures
Prayer 24 Sep 2014.odt
Providence 16 July 2015.odt
Public
Puppy Rescue Sartup.ods
Ranger BOS.odt
Regions Mortgage.ods
RINO.jpg
RTBAV 7 Mar 2015.ods
RUREADY.wmv
Soccer.jpg
survivalfoodplan.ods
Templates
thetalleys.jpg
ttf-mscorefonts-installer_3.6_all.deb
Ubuntu One
udo apt update
uscarb 18 Aug 2014.odt
usr
Vegetables.ods
Videos
vuescan
vuescan.8ba
vuescan.ds
dave@dave-desktop:~$ 
```

Wow that's some weird stuff.

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> Background info. I don't think I have ever used the Nouveau drivers. I have always had an NVidia driver. I mistakenly selected a newer NVidia driver last week (When all this trouble started). When I switched back, using system settings/additiional drivers is when the Nouveau issues came up. Don't know if any of that matters now. If I were to change to the old NVidia drive using system settings/Additioanl drivers, the display would be OK, but then the Nouveau and NVidia togther issue might still be here.

> **aviator1 said:**
> ```
dave@dave-desktop:~$ cd /etc/X11
dave@dave-desktop:/etc/X11$ 


```

```
dave@dave-desktop:~$ ls

Wow that's some weird stuff.
Sorry my fault i should have been clearer:
First run this:
[CODE]cd /etc/X11
```
hit enter && Don't close yet
Now run this:
```
ls
```
now paste back the output.:)

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Sorry my fault i should have been clearer:
First run this:
```
cd /etc/X11
```
hit enter && Don't close yet
Now run this:
```
ls
```
now paste back the output.:)

```
dave@dave-desktop:~$ cd /etc/X11
dave@dave-desktop:/etc/X11$ ls
app-defaults             xinit               Xsession
core                     xkb                 Xsession.d
cursors                  xorg.conf.10032014  Xsession.options
default-display-manager  xorg.conf.failsafe  xsm
fonts                    Xreset              Xwrapper.config
rgb.txt                  Xreset.d
X                        Xresources
dave@dave-desktop:/etc/X11$ 



```
Thanks for your patience.

---

### Post by #&amp;thj^% on 2017-07-08
Your Welcome.;)
Thought so we have some old configs hanging around.
lets get rid of them with:
```
sudo rm -rf /etc/Xll/ xorg.conf.10032014 xorg.conf.failsafe
```
Now this time just use the power off option...you have a plenty fast machine and sometimes it dose dose not spin down long enough to achieve the expected results with a reboot.
So after running the above command...run this.
```
sudo shutdown -h now
```
You will have to manually power the machine back on after waiting for a **complete power off.** (Wait about 40 Seconds for the drive to stop spinning)

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Your Welcome.;)
Thought so we have some old configs hanging around.
lets get rid of them with:
```
sudo rm -rf /etc/Xll/ xorg.conf.10032014 xorg.conf.failsafe
```
Now this time just use the power off option...you have a plenty fast machine and sometimes it dose dose not spin down long enough to achieve the expected results with a reboot.
So after running the above command...run this.
```
sudo shutdown -h now
```
You will have to manually power the machine back on after waiting for a **complete power off.** (Wait about 40 Seconds for the drive to stop spinning)

Well............ I followed your instructions. Things got worse. Desktop locked. Finally was able to restart. after the restart, I ran the instructed items again, and waited longer after shut down (I wasn't sure I waited long enough the first time)

Anyway. Bootup was normal, navigation is normal, Still no change with the display or control there.

Maybe gasoline and fire? :-)

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> 
Maybe gasoline and fire? :-)
I know the feeling! ;)
Not sure whats going on with all this... but we may have to set it manually.
Give me the output of this:
```
xrandr -q
```

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> I know the feeling! ;)
Not sure whats going on with all this... but we may have to set it manually.
Give me the output of this:
```
xrandr -q
```

```
dave@dave-desktop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00* 
dave@dave-desktop:~$ 



```

However, I think when I was using the NVidia drivers, that this was the resolution that was set and filled the scree. Guessing.

---

### Post by #&amp;thj^% on 2017-07-08
Welp this is the bad part here:
```
xrandr: Failed to get size of gamma for output default
```
Give me some time to read through your whole thread to see how this would happen.???
In the meantime lets give this a shot to see if we can at least get some what a working system.
You did not by chance install the nvidia driver from Nvidia.com site did you? (I don't mean from the package manager) 
Anyway lets give this a whirl:
```
sudo -H gedit /etc/default/grub
```
Now we are going to change the line we edited a bit ago.
Change this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
To:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```
Save and close...power off again, wait a bit, and power up.
Fingers Crossed.

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> Welp this is the bad part here:
```
xrandr: Failed to get size of gamma for output default
```
Give me some time to read through your whole thread to see how this would happen.???
In the meantime lets give this a shot to see if we can at least get some what a working system.
You did not by chance install the nvidia driver from Nvidia.com site did you? (I don't mean from the package manager) 
Anyway lets give this a whirl:
```
sudo -H gedit /etc/default/grub
```
Now we are going to change the line we edited a bit ago.
Change this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
To:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```
Save and close...power off again, wait a bit, and power up.
Fingers Crossed.

I installed the NVidia driver simply by choosing another radio button inthe system settings/additional drivers area.

I mage the change as you instructed, and here is the result:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I will shut down for a minute or so and report back.

---

### Post by aviator1 on 2017-07-08
> **aviator1 said:**
> I installed the NVidia driver simply by choosing another radio button inthe system settings/additional drivers area.

I mage the change as you instructed, and here is the result:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I will shut down for a minute or so and report back.

No help so far. I shut down for 3 minutes. On startup. Thunderbird would open, download email, but allowed no navigation. Opened Firefox, and no navigation available until I clicked on a toolbar menu item. 

This happens if I do a full shutdown, not if I do a restart.

I rebooted and everything is working OK, except for the screen issues.

This scenario is exactly what was going on when this thread started. CatKiller discovered that the Nouveau and NVidia drivers were both loading and fighting each other.

I believe that if I went to system settings/additional drivers, and selected a radio button of one of the NVidia drivers, that the screen issue would resolve.

However, I think, also, that the loading of both drivers may come back as well.

I really appreciate the help you are giving. I will still be on for awhile tonight, but then not until the afternoon tomorrow, central time.

Is this a driver issue or a boot issue of some kind?

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> 

I really appreciate the help you are giving. I will still be on for awhile tonight, but then not until the afternoon tomorrow, central time.
Is this a driver issue or a boot issue of some kind?
No worries I enjoy helping friendly folks like yourself.:)
I think this is a big time Driver issue:
I think we can safely install the the driver again with the change we made: But i install them differently than others, I use the command line only, I'm just not a fan of package managers. :D
Lets see what you have to offer first before we jump into this>
Run this and give me the return back here.
```
ubuntu-drivers devices
```

---

### Post by aviator1 on 2017-07-08
> **1fallen said:**
> No worries I enjoy helping friendly folks like yourself.:)
I think this is a big time Driver issue:
I think we can safely install the the driver again with the change we made: But i install them differently than others, I use the command line only, I'm just not a fan of package managers. :D
Lets see what you have to offer first before we jump into this>
Run this and give me the return back here.
```
ubuntu-drivers devices
```

```
dave@dave-desktop:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FC1sv00000000sd00000000bc03sc00i00
model    : GK107 [GeForce GT 640]
vendor   : NVIDIA Corporation
driver   : nvidia-381 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-370 - third-party free
driver   : nvidia-340 - third-party free
driver   : nvidia-375 - distro non-free
driver   : nvidia-378 - third-party free
driver   : nvidia-304 - distro non-free

== cpu-microcode.py ==
driver   : amd64-microcode - distro non-free

dave@dave-desktop:~$
```

---

### Post by #&amp;thj^% on 2017-07-08
Ok I have seen many problems with this driver:
```
nvidia-381 - third-party free recommended
```
We now have a PPA that works great with your card.
And I use this one:
```
nvidia-381 - third-party non-free recommended

```

You will have to add this PPA though.


> PPA description

Fresh drivers from upstream, currently shipping Nvidia.

## Current Status

Current official release: `nvidia-381` (381.22)
Current long-lived branch release: `nvidia-375` (375.66)

For G8x, G9x and GT2xx GPUs use `nvidia-340` (340.102)
For NV4x and G7x GPUs use `nvidia-304` (304.135)

Support timeframes for Unix legacy GPU releases:
[https://nvidia.custhelp.com/app/answers/detail/a_id/3142](https://nvidia.custhelp.com/app/answers/detail/a_id/3142)

## What we're working on right now:

- Normal driver updates

So I have been using it for over a year now with no problems at all.
Add it with:
```
sudo add-apt-repository ppa:graphics-drivers/ppa

```
Now update && Install with:
```
sudo apt update && sudo apt install nvidia-381
```
Reboot...Now you should be golden...

---

### Post by aviator1 on 2017-07-08
The gold is shining brightly. The radio selection is showing the NVidia 381.22 in the additional drives area.

All navigation is normal and I have control of the display (Although no change was required)

How shall I mark this as being solved? Installed correct video driver?

Fantastic work. I am a long time user, but not a programmer of Ubuntu. I recommend it to everyone I know that uses computers.

I really appreciate your time, effort, and patience to help me with this.

Regards.

---

### Post by aviator1 on 2017-07-08
Oops.......back to being able to open only 1 program at a time.......

---

### Post by aviator1 on 2017-07-08
Just shut down and restarted. All is normal......

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> The gold is shining brightly. The radio selection is showing the NVidia 381.22 in the additional drives area.

All navigation is normal and I have control of the display (Although no change was required)

How shall I mark this as being solved? Installed correct video driver?

Fantastic work. I am a long time user, but not a programmer of Ubuntu. I recommend it to everyone I know that uses computers.

I really appreciate your time, effort, and patience to help me with this.

Regards.

Happy to help, Thanks for your Kind words. ;)
It was a pleasure.
You can use the the thread tools to mark as solved....run it for a few days first just to be sure we removed all of the gremlins. :D
Enjoy and Kind regards.

---

### Post by aviator1 on 2017-07-08
Well, back to the same problem.....From a fresh start, navigation is very limited. Thunderbird will open, but allows no navigation. Firefoc opens, but no navigation until I click on one of the toolbar menu items.

After a reboot, all seems normal.

Screen size and system settings controls are OK.

last night, CatKiller said that both the NVida and Nouveau drivers were opening. Is there any way to get rid of the Nouveau?

Thanks for your patience. I know this is not an easy one. :-)

UPDATE: Just did a simple reboot and navigation is off again.......

UPDATE-2 Just tried another reboot with the same results. Let's stop for this evening. I'll check in tomorrow afternoom. Thanks for all your help.

Regards.

---

### Post by #&amp;thj^% on 2017-07-08
> **aviator1 said:**
> Well, back to the same problem.....From a fresh start, navigation is very limited. Thunderbird will open, but allows no navigation. Firefoc opens, but no navigation until I click on one of the toolbar menu items.

After a reboot, all seems normal.

Screen size and system settings controls are OK.

last night, CatKiller said that both the NVida and Nouveau drivers were opening. Is there any way to get rid of the Nouveau?

Thanks for your patience. I know this is not an easy one. :-)

UPDATE: Just did a simple reboot and navigation is off again.......

This is sounding like a hardware issue now!
The two drivers should not be in conflict with this added to grub "nogpumanager" 
But now thinking back... did I tell you to run this:
```
sudo update-grub
```
Now check again with a few reboots.
I'm going to go offline for the evening, but will check back tomorrow to see how it is going.

---

### Post by #&amp;thj^% on 2017-07-09
Requesting update>here.
1.Did you run the above "update-grub"
2.Any changes in "/etc/X11" Any new xorg.conf's listed.
```
cd /etc/X11
```
```
ls
```
Paste back content the "ls"

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> This is sounding like a hardware issue now!
The two drivers should not be in conflict with this added to grub "nogpumanager" 
But now thinking back... did I tell you to run this:
```
sudo update-grub
```
Now check again with a few reboots.
I'm going to go offline for the evening, but will check back tomorrow to see how it is going.

I did run the sudo update-grub and nothing changed.

Here is the other info you requests
```
dave@dave-desktop:~$ cd /etc/X11
dave@dave-desktop:/etc/X11$ ls
app-defaults             xinit               Xsession
core                     xkb                 Xsession.d
cursors                  xorg.conf.10032014  Xsession.options
default-display-manager  xorg.conf.failsafe  xsm
fonts                    Xreset              Xwrapper.config
rgb.txt                  Xreset.d
X                        Xresources
dave@dave-desktop:/etc/X11$ 

```

The problems seem a bit inconsistent at times.

Let fill you in on what is happening.

On _any start_ from off to booted, the screen is fine now. I can open, use, and close a spreadsheet. Have not tried other files.

I can open Thunderbird and it will download emails. It is then locked and I cannot access any email.

I can open Firefox, but all of my "Link" icons are dead. If I click on any tool bar icon, such as bookmarks, the screen nudges down about 1/8" and the links are live.

After _1-4 reboots_, everything seems to work fine. I am getting an occasional/ransom screen dim while using Firefox.

I have had System monitor running and never use more than about 1.3 GB out of 16 GB RAM. No matter what I used, I never get over 1.8 GB RAM use.

I have the cover off and the video card was barely warm. It has 2 fans, and I have 4 case fans.

The unit is about 3 years old. Maybe a boat anchor? :-)

Thanks for your help.

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> Requesting update>here.
1.Did you run the above "update-grub"
2.Any changes in "/etc/X11" Any new xorg.conf's listed.
```
cd /etc/X11
```
```
ls
```
Paste back content the "ls"

Updated with other info. Post #110

---

### Post by #&amp;thj^% on 2017-07-09
> **aviator1 said:**
> I did run the sudo update-grub and nothing changed.

Here is the other info you requests
```
dave@dave-desktop:~$ cd /etc/X11
dave@dave-desktop:/etc/X11$ ls
app-defaults             xinit               Xsession
core                     xkb                 Xsession.d
cursors                  xorg.conf.10032014  Xsession.options
default-display-manager  xorg.conf.failsafe  xsm
fonts                    Xreset              Xwrapper.config
rgb.txt                  Xreset.d
X                        Xresources
dave@dave-desktop:/etc/X11$ 

```

The problems seem a bit inconsistent at times.

Let fill you in on what is happening.

On _any start_ from off to booted, the screen is fine now. I can open, use, and close a spreadsheet. Have not tried other files.

I can open Thunderbird and it will download emails. It is then locked and I cannot access any email.

I can open Firefox, but all of my "Link" icons are dead. If I click on any tool bar icon, such as bookmarks, the screen nudges down about 1/8" and the links are live.

After _1-4 reboots_, everything seems to work fine. I am getting an occasional/ransom screen dim while using Firefox.

I have had System monitor running and never use more than about 1.3 GB out of 16 GB RAM. No matter what I used, I never get over 1.8 GB RAM use.

I have the cover off and the video card was barely warm. It has 2 fans, and I have 4 case fans.

The unit is about 3 years old. Maybe a boat anchor? :-)

Thanks for your help.
Yep I have read the entire thread and up to speed now>
We did not update-grub fast enough, It generated two more "xorg.conf" files.:(
I would like to see the contents of this file:
```
gedit /etc/X11/xorg.conf.10032014
```
Paste Back please.
Whoa!!! Just seen this.
> I am getting an occasional/ransom screen dim while using Firefox. 
Can you take a screen shot when that happens...I would like to see that if possible.

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> Yep I have read the entire thread and up to speed now>
We did not update-grub fast enough, It generated two more "xorg.conf" files.:(
I would like to see the contents of this file:
```
gedit /etc/X11/xorg.conf.10032014
```
Paste Back please.

Not much there.....

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


```

---

### Post by #&amp;thj^% on 2017-07-09
> I am getting an **_occasional/ransom screen dim_** while using Firefox.
 
Do you have a screenshot when that happened...I would like to see that if possible.

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> Do you have a screenshot when that happened...I would like to see that if possible.

No, the computer is basically locked when that happens. I would have no access to my screen shot app.

This happened a lot on a large spreadsheet I had when I would save and close. I eventually changed the size of the spreadsheet and it's not a problem.

The random screen dim now, usually occurs during net surfing and on various pages. Does not happen on the same site or pages.

All that happens is that the screen goes dim, and 1 of my 8 processor cores hits 100%. Sometimes if the lock last 30 or more seconds, the 100% will swap with another core.

When the screen comes back, the cores are basically equalized.

All of this usually lasts about a minute. RAM always stays less than 2 GB....no matter what I am doing.

I will be offline for a few hours and back on. 

Have a great afternoon. Thanks for your help.

---

### Post by CatKiller on 2017-07-09
> **1fallen said:**
> Do you have a screenshot when that happened...I would like to see that if possible.

That sounds like just the unresponsive window indicator.

Is it just Thunderbird and Firefox that are unresponsive now, or are there other things that are currently nor working? OP reported not being able to use window controls previously, but if it's just the two Mozilla applications, a fresh profile might help with that.

---

### Post by #&amp;thj^% on 2017-07-09
> **CatKiller said:**
> **_That sounds like just the unresponsive window indicator._**

Is it just Thunderbird and Firefox that are unresponsive now, or are there other things that are currently nor working? OP reported not being able to use window controls previously, but if it's just the two Mozilla applications, a fresh profile might help with that.

Agreed ;)..With the news of ransomware floating about... newer or unexperienced users become a bit paranoid.
I would like to see some views from his firefox "about: performance" and "about:support" Snaps.
A friend had similar issues with his build turned out to be a failing north-bridge...these sort of hardware fails can be troublesome to diagnose.

---

### Post by bcschmerker on 2017-07-09
**After reading the traffic on the driver conflict,** I suspected that the nVIDIA® purge was incomplete.  Given the issues I encountered with ubuntuGNOME® 16.04-LTS on an eMachines®/Acer® EL1210-09 with specific major upgrades (viz., a 600W Shuttle® PSU and MicroStar® half-height VDA with nVIDIA® GK109 GPU), I would have probably gone about the task along the following lines:
```
sudo apt purge --remove nvidia-* cuda* libcuda*
sudo jupp /etc/default/grub
```
and, instead of setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager", I would have set GRUB_CMDLINE_LINUX_DEFAULT="debug nogpumanager" and GRUB_TERMINAL=console to capture the boot messages as the Kernel sends them.  After these would come:
```
sudo dpkg-reconfigure xserver-xorg-video-nouveau
sudo update-grub

```prior to a shutdown and cold restart.

---

### Post by aviator1 on 2017-07-09
> **CatKiller said:**
> That sounds like just the unresponsive window indicator.

Is it just Thunderbird and Firefox that are unresponsive now, or are there other things that are currently nor working? OP reported not being able to use window controls previously, but if it's just the two Mozilla applications, a fresh profile might help with that.

It's not just the Mozilla apps. Sometimes it's the spreadsheets, system monitor, calculator, etc.

However, I have discovered something interesting, and I will post below after I respond to you and the others who have posted here. See post #120

Thanks very much for your reply.

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> Agreed ;)..With the news of ransomware floating about... newer or unexperienced users become a bit paranoid.
I would like to see some views from his firefox "about: performance" and "about:support" Snaps.
A friend had similar issues with his build turned out to be a failing north-bridge...these sort of hardware fails can be troublesome to diagnose.

As I have mentioned, from a cold boot, Thunderbird will download, but there is no navigation. Firefox will open, but no lonks are live until I click on a tool bar selection.

However, I just discovered by accident, the following.

From a cold boot, when I get to the desktop, I use Control/Alt/Delete and get a prompt to Logout.

I select logout and get sent to another desktop with a place to enter my password.

I enter my password, and get returned to my desktop............from that point, everything is normal.........I have done this 5 times in the last 30 minutes. It works every time.

Sorry I have been away for a few hours. Thanks for your help.

---

### Post by aviator1 on 2017-07-09
> **bcschmerker said:**
> **After reading the traffic on the driver conflict,** I suspected that the nVIDIA® purge was incomplete.  Given the issues I encountered with ubuntuGNOME® 16.04-LTS on an eMachines®/Acer® EL1210-09 with specific major upgrades (viz., a 600W Shuttle® PSU and MicroStar® half-height VDA with nVIDIA® GK109 GPU), I would have probably gone about the task along the following lines:
```
sudo apt purge --remove nvidia-* cuda* libcuda*
sudo jupp /etc/default/grub
```
and, instead of setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager", I would have set GRUB_CMDLINE_LINUX_DEFAULT="debug nogpumanager" and GRUB_TERMINAL=console to capture the boot messages as the Kernel sends them.  After these would come:
```
sudo dpkg-reconfigure xserver-xorg-video-nouveau
sudo update-grub

```prior to a shutdown and cold restart.

Thanks very much for your post. Please see post #120.

---

### Post by aviator1 on 2017-07-09
> **1fallen said:**
> Agreed ;)..With the news of ransomware floating about... newer or unexperienced users become a bit paranoid.
I would like to see some views from his firefox "about: performance" and "about:support" Snaps.
A friend had similar issues with his build turned out to be a failing north-bridge...these sort of hardware fails can be troublesome to diagnose.

I meant random, not ransom

---

### Post by aviator1 on 2017-07-09
I appreciate everyone's help very much. I have to go offline until tomorrow afternoon.

Please check post #120 for the latest info.

Regards.

---

### Post by CatKiller on 2017-07-10
> **aviator1 said:**
> From a cold boot, when I get to the desktop, I use Control/Alt/Delete and get a prompt to Logout.

I select logout and get sent to another desktop with a place to enter my password.

I enter my password, and get returned to my desktop............from that point, everything is normal.........I have done this 5 times in the last 30 minutes. It works every time.

So, without doing this, you've set up your computer to automatically log in? What environment are you set to automatically log into? What environment do you log into if you log out and log in again as you've described above?

---

### Post by #&amp;thj^% on 2017-07-10
Thanks for Clarifying the ransom/random term.
Well now this might be due to the Tracker Constant Indexing. And we/I'm  only guessing at this point, with no concrete errors to work from.
Reference for what is Tracker: [https://wiki.ubuntu.com/IntegratedDesktopSearch](https://wiki.ubuntu.com/IntegratedDesktopSearch)
Which could be sorted with a hack like the below: **But I do not recommend this for now**.
To be clear Do Not run the below...See the preferred method I mention Below [COLOR="#FF0000"][COLOR="#FF0000"]Read the whole post, Run Only as a Last resort.[/COLOR][/COLOR]
```

echo -e "\nHidden=true\n"|sudo tee --append /etc/xdg/autostart/tracker-extract.desktop
echo -e "\nHidden=true\n"|sudo tee --append /etc/xdg/autostart/tracker-miner-apps.desktop
echo -e "\nHidden=true\n"|sudo tee --append /etc/xdg/autostart/tracker-miner-fs.desktop
echo -e "\nHidden=true\n"|sudo tee --append /etc/xdg/autostart/tracker-miner-user-guides.desktop
echo -e "\nHidden=true\n"|sudo tee --append /etc/xdg/autostart/tracker-store.desktop
```
We can set this to a lower value, and also stop monitoring the users files via... (This is a safer method)
```

gsettings set org.freedesktop.Tracker.Miner.Files crawling-interval -2
gsettings set org.freedesktop.Tracker.Miner.Files enable-monitors false
```
Then a reset:
```

tracker reset --hard
```
**_***This Would be the Preferred Method below.***_**
But there is also a more user friendly method using the Tracker GUI:
So Give this a try Before running the commands listed above here.
```
sudo apt install tracker-gui

```
Now Open the tracker-gui and Check the "_Only when the Computer is not being used_".
Next go to the tabs at the top and select **"Locations"** and un-tick all the user related files.
IE: , Desktop, Documents, Downloads, Music, Pictures, Videos.
Now again at the top tabs click "System"...And Push the "**Yes,remove all indexes**" button, now at the bottom of that window you will see "**Apply**" Click that.
So you see this should give some comfort to the user in that all changes can be visually done or reset with a GUI instead of running code in a console.
I have Screentshots to help with the instructions.

---

### Post by aviator1 on 2017-07-10
> **CatKiller said:**
> So, without doing this, you've set up your computer to automatically log in? What environment are you set to automatically log into? What environment do you log into if you log out and log in again as you've described above?

From a cold boot, I get a screen that describes the hardware. That moves on to a screen where I can make a selection of *Ubuntu, or Windows, etc. If I select nothing, it does automatically logon to my desktop.

I tried just letting it logon automatically, and the desktop was locked. I could do some navigation with the keyboard, but nothing with the mouse. The control/ALT/Delete to me to the logoff prompt, which I had to select with the keyboard.

After logging off and back on, everything was normal.

From a cold boot, if I hit enter on the selection screen, when I get to the desktop, I have some use of the mouse, but Thunderbird/Firefox are as previously described. Logging off and on, again fixes everything.

Sorry about the upside down images. Did not notice.
.

---

### Post by #&amp;thj^% on 2017-07-10
Your grub entry show 14.04.4 (Trusty)
Yet there is software showing 16.04 (Xenial)
Can you show us this from the terminal:
```
lsb_release -a
```
And try to disable auto login.

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> Your grub entry show 14.04.4 (Trusty)
Yet there is software showing 16.04 (Xenial)
Can you show us this from the terminal:
```
lsb_release -a
```
And try to disable auto login.

Do not know how to disable auto logon.

Followed your preferred method for previous post. No changes observed in the boot problems. However, I have this message at the top of my desktop:  
 	 	 	 	
   An error occurred, Please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ‘Unknown error’: Class’KeyError’>’(“The cache has no package named ‘wine 1.6-i386’)’ This usually means that your installed packages have unmet dependendancies.
  
Here is the info you requested. Thanks very much for your help.


```
dave@dave-desktop:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
dave@dave-desktop:~$ 
```

---

### Post by #&amp;thj^% on 2017-07-10
> **aviator1 said:**
> Do not know how to disable auto logon.

Followed your preferred method for previous post. No changes observed in the boot problems. However, I have this message at the top of my desktop:  
 	 	 	 	
   An error occurred, Please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ‘Unknown error’: Class’KeyError’>’(“The cache has no package named ‘wine 1.6-i386’)’ This usually means that your installed packages have unmet dependendancies.
  
Here is the info you requested. Thanks very much for your help.


```
dave@dave-desktop:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
dave@dave-desktop:~$ 
```
Lets work on one topic at a time, Lets see how this reads:
```
 gedit /etc/lightdm/lightdm.conf 
```

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> Lets work on one topic at a time, Lets see how this reads:
```
 gedit /etc/lightdm/lightdm.conf 
```
```

[SeatDefaults]
autologin-guest=false
autologin-user=dave
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```

---

### Post by #&amp;thj^% on 2017-07-10
> **aviator1 said:**
> ```

[SeatDefaults]
autologin-guest=false
autologin-user=dave
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```
Thanks...To disable Autologin we need to change this line:
```
autologin-user=dave
```
To read like this:
```
autologin-user=
```
Just remove your user name.
```
sudo -H gedit /etc/lightdm/lightdm.conf 
```
Will let you edit the file as I have shown. Save and close.
So it should now read:
```
[SeatDefaults]
autologin-guest=false
autologin-user=
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```
Now you should be greeted with a normal Login Window after rebooting.

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> Thanks...To disable Autologin we need to change this line:
```
autologin-user=dave
```
To read like this:
```
autologin-user=
```
Just remove your user name.
```
sudo -H gedit /etc/lightdm/lightdm.conf 
```
Will let you edit the file as I have shown. Save and close.
So it should now read:
```
[SeatDefaults]
autologin-guest=false
autologin-user=
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu
```
Now you should be greeted with a normal Login Window after rebooting.

Got that done. On the screen that offers the selections, I can just hit enter, or it still counts down and either way will send me to the page that I was getting where I need to add my password. I do so, and get my regular desktop.

However, I still have to logoff, add my password, and logon again. This is not a restart, just a logoff and logon.

---

### Post by #&amp;thj^% on 2017-07-10
Sorry don't quite understand? Have you rebooted yet?

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> Sorry don't quite understand? Have you rebooted yet?

Yes, twice. Once with hitting Enter and once letting it count down and auto boot.

Either way takes me to the screen which requires my password.

When I add my password, I am sent to my desktop. I still have the navigation issues until I logoff, add my password again, and return to my desktop. Then all is normal.

---

### Post by #&amp;thj^% on 2017-07-10
Is this by chance a upgrade from 14.04 to 16.04?
Or is it a Clean 16.04 Install?

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> Is this by chance a upgrade from 14.04 to 16.04?
Or is it a Clean 16.04 Install?

It was an upgrade from 14.04. Sometime last year. But did not have these problems until the past week.

Explain clean install, please.

EDIT: I got it.

---

### Post by aviator1 on 2017-07-10
Have to be offline for about 30 minutes

---

### Post by #&amp;thj^% on 2017-07-10
> **aviator1 said:**
> It was an upgrade from 14.04. Sometime last year. But did not have these problems until the past week.

Explain clean install, please.

EDIT: I got it.
I thought so! :(
I see you you now understand a Clean install right?
Upgrades are very much a crap shoot...unless you are a more of a advanced user. (This method is still a work in progress with Ubuntu) 
Even many Advanced users here use a clean install to avoid bad behaviors or faulty system errors from upgrading release to release.;)
This Thread has gone on for a week or longer now...I'm going to suggest a Clean install here. (Which i seldom do) 
You can wait for others here to help you...but with a clean install you will have a much better user experience and more problem free. 
Example: Had you just made a clean install a week ago when all this started you would be productively using your system now.

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> I thought so! :(
I see you you now understand a Clean install right?
Upgrades are very much a crap shoot...unless you are a more of a advanced user. (This method is still a work in progress with Ubuntu) 
Even many Advanced users here use a clean install to avoid bad behaviors or faulty system errors from upgrading release to release.;)
This Thread has gone on for a week or longer now...I'm going to suggest a Clean install here. (Which i seldom do) 
You can wait for others here to help you...but with a clean install you will have a much better user experience and more problem free. 
Example: Had you just made a clean install a week ago when all this started you would be productively using your system now.

Great idea. How do I do a clean install? Download and go through the install? Do I have to uninstall before the new install?

Thanks.

---

### Post by #&amp;thj^% on 2017-07-10
> **aviator1 said:**
> Great idea. How do I do a clean install? Download and go through the install? Do I have to uninstall before the new install?

Thanks.

To Start make sure you have a good back-up of what you want to keep...Documents, Pictures, Music, etc etc.(Or anything else you want/need) back it up to a different Disk or usb drive that has the room needed.
Some can even save their Home Directory/Part ion... again some prior experience needed for this method.
Now go to this site: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/) and choose the Arch needed, IE 64 or 32 bit.
Download it burn it to a USB or medium device you want.
When asked how it is to be installed, Choose the format the drive for a very clean install. (No left overs to deal with from a previous install) This would be the Preferred Method.
Now if you think you are capable you could use the something else option...and not format the existing partition, which trys to keep all your files in you old Home Directory intact.
But still a chance that old configs left over will come into play again, so if you think you can deal with this then go for it.
Here is a link for this: [https://askubuntu.com/questions/840434/how-to-reinstall-ubuntu-but-keep-personal-files](https://askubuntu.com/questions/840434/how-to-reinstall-ubuntu-but-keep-personal-files)
You will have to uninstall all Proprietary Drivers First, and Disable All added PPA's and run the update and upgrade command.
But if I were you I would just use the Format and Install everything Pure and clean.
Now I have no idea if you have a EFI/UEFI system...I did see a windows7 entry on your screenshot or camera shot. 
Good Luck :D
Kind Regards

---

### Post by aviator1 on 2017-07-10
> **1fallen said:**
> To Start make sure you have a good back-up of what you want to keep...Documents, Pictures, Music, etc etc.(Or anything else you want/need) back it up to a different Disk or usb drive that has the room needed.
Some can even save their Home Directory/Part ion... again some prior experience needed for this method.
Now go to this site: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/) and choose the Arch needed, IE 64 or 32 bit.
Download it burn it to a USB or medium device you want.
When asked how it is to be installed, Choose the format the drive for a very clean install. (No left overs to deal with from a previous install) This would be the Preferred Method.
Now if you think you are capable you could use the something else option...and not format the existing partition, which trys to keep all your files in you old Home Directory intact.
But still a chance that old configs left over will come into play again, so if you think you can deal with this then go for it.
Here is a link for this: [https://askubuntu.com/questions/840434/how-to-reinstall-ubuntu-but-keep-personal-files](https://askubuntu.com/questions/840434/how-to-reinstall-ubuntu-but-keep-personal-files)
You will have to uninstall all Proprietary Drivers First, and Disable All added PPA's and run the update and upgrade command.
But if I were you I would just use the Format and Install everything Pure and clean.
Now I have no idea if you have a EFI/UEFI system...I did see a windows7 entry on your screenshot or camera shot. 
Good Luck :D
Kind Regards
I am in the process of backing up everything now. Should be finished shortly. My basic drive is an SSD that is a dual boot with Windows 7. I have a second, storage 2 TB HDD. I am backing up to an external HDD

I have printed off your instructions, and will go to the links.

I really appreciate all the time and effort you, CatKiller, and the others have put in to help with this.

I will repost back as soon as I can.

Regards.

---

### Post by aviator1 on 2017-07-10
> **aviator1 said:**
> I am in the process of backing up everything now. Should be finished shortly. My basic drive is an SSD that is a dual boot with Windows 7. I have a second, storage 2 TB HDD. I am backing up to an external HDD

I have printed off your instructions, and will go to the links.

I really appreciate all the time and effort you, CatKiller, and the others have put in to help with this.

I will repost back as soon as I can.

Regards.

Good news, and average news.

I did a complete, clean install and everything is working very well.

The average news is that I used deja dup to backup to an external drive, and cannot seem to get restored.

Regards.

---

### Post by vasa1 on 2017-07-11
> **aviator1 said:**
> ...
The average news is that I used deja dup to backup to an external drive, and cannot seem to get restored.
...
Please start a new thread on the deja dup issue if your initial issue has been resolved. Thanks.

---

### Post by aviator1 on 2017-07-11
Yes sir. Thank you.

---

### Post by aviator1 on 2017-07-11
> **CatKiller said:**
> So, without doing this, you've set up your computer to automatically log in? What environment are you set to automatically log into? What environment do you log into if you log out and log in again as you've described above?

Thanks for all your time and effort. I ended up doing a clean re-install and all is well. Except, my back-up won't work. I will post that shortly. Have a great day.

Regards.

---

### Post by aviator1 on 2017-07-11
I don't know if you are still following this, but I am back to the same scenario after the complete clean install. The system did do an update after the install.

Thunderbird and Firefox are mostly locked as before.

A logoff/logon fixes everything

---

### Post by oldfred on 2017-07-11
How are you installing nVidia driver?
Only from Ubuntu repository and only once?
Issue often is from multiple copies of nVidia drivers installed and conflicting. 
Or settings created in /etc/X11/xorg.conf causing issues as not regularly used for video, but some other devices may still need it.

I have 620GT nVidia and find open source driver works well. One of my test installs, I did install nVidia and did not notice any real difference. But I primarily am on Internet or using files on system. No games or anything that would need more video power.

---

### Post by aviator1 on 2017-07-11
This just happened (as before)

From a cold start, Thunderbird would download, but had no navigation. Firefox would open, but links were dead until I clicked on a Toolbar button, such as Bookmarks. The screen shifted about 1/8" down, and navigation was working.

I opened a spreadsheet and could use it.

I opened System Settings to displays, and left it there. I opened System Monitor and just left it running.

That's when everything froze. No navigation at all.

Control/ALT/Delete brought up the logoff window. Mouse would not work. Had to use keyboard to select enter.

Got to screen with password box. Entered password and got back to my desktop.

Everything is normal.......maybe a hardware issue??????

---

### Post by aviator1 on 2017-07-11
> **oldfred said:**
> How are you installing nVidia driver?
Only from Ubuntu repository and only once?
Issue often is from multiple copies of nVidia drivers installed and conflicting. 
Or settings created in /etc/X11/xorg.conf causing issues as not regularly used for video, but some other devices may still need it.

I have 620GT nVidia and find open source driver works well. One of my test installs, I did install nVidia and did not notice any real difference. But I primarily am on Internet or using files on system. No games or anything that would need more video power.

I just did the 1 clean install last night. Everything was great. The system did do an auto update after I did the install.

This just started again 30 minutes ago.

It chose the Xorg X server - Nouveau Display Driver from xserver-xorg-video-nouveau (Open source)

I am primarily on the net, and use some spreadsheets. No video stuff.

I appreciate any help.

---

### Post by aviator1 on 2017-07-11
I have to be offline until tomorrow afternoon.

Thanks for any posts. I will follow up as soon as I get a chance.

Regards.

---

### Post by oldfred on 2017-07-11
With all the suggestions & fixes, I now wonder also if hardware issue.
I only know some Intel systems, does your AMD chip have video and can you unplug nVidia and use internal video. That would eliminate nVidia card as an issue or perhaps too much power draw on power supply.

But there have been some issues on AMD video drivers also which I know little about.

---

### Post by #&amp;thj^% on 2017-07-12
> **oldfred said:**
> **_With all the suggestions & fixes, I now wonder also if hardware issue._**
I only know some Intel systems, does your AMD chip have video and can you unplug nVidia and use internal video. That would eliminate nVidia card as an issue or perhaps too much power draw on power supply.

But there have been some issues on AMD video drivers also which I know little about.

+100 :D
I could never find any evidence his had a AMD GPU.
I keep wondering if the Nvidia card is seated properly or enough power to it, aside other hardware problems possible. 
Nvidia (Non-Free) drivers I play with all the time with absolutely NO problems or Issues...but 12 years of experience helps.
I need the extra options with a custom "xorg.conf" file for clocking and fan control, that I don't have with the free open source driver.

---

### Post by aviator1 on 2017-07-12
> **1fallen said:**
> +100 :D
I could never find any evidence his had a AMD GPU.
I keep wondering if the Nvidia card is seated properly or enough power to it, aside other hardware problems possible. 
Nvidia (Non-Free) drivers I play with all the time with absolutely NO problems or Issues...but 12 years of experience helps.
I need the extra options with a custom "xorg.conf" file for clocking and fan control, that I don't have with the free open source driver.

I was thinking of taking the card out and re-seating it. Works in airplanes sometimes.

Earlier in this thread I was having a problem with the browser not filling the screen. You supplied the method to use an nVidia  381 driver, which solved that problem.

Is there any way to turn off the nouveau driver and turn on an nVidia driver? Wouldn't that remove any conflicts? I don't do much video stuff. Mostly just browsing and spreadsheets.

I have a 600 watt power supply. 

I have an AMD 8350 8 core processor.

System settings/Graphics says I have a Gallium .04 on NVE7 

Thanks for your time and assistance.

---

### Post by #&amp;thj^% on 2017-07-12
I'm not sure if installing the Nvidia Driver will help aviator1??
How big is your PSU? (Power Supply Unit)....I'm thinking just a minium of 500watts is needed for your setup Preferred would be 800 to 1000 watts.
AMD CPU's and Nvidia GPU's are power hungry little devils.:D

---

### Post by aviator1 on 2017-07-12
> **1fallen said:**
> I'm not sure if installing the Nvidia Driver will help aviator1??
How big is your PSU? (Power Supply Unit)....I'm thinking just a minium of 500watts is needed for your setup Preferred would be 800 to 1000 watts.
AMD CPU's and Nvidia GPU's are power hungry little devils.:D

600 watts, but it's been doing OK for about 3 years.

Also, re-seated and cleaned the card. No change.

---

### Post by aviator1 on 2017-07-12
> **oldfred said:**
> With all the suggestions & fixes, I now wonder also if hardware issue.
I only know some Intel systems, does your AMD chip have video and can you unplug nVidia and use internal video. That would eliminate nVidia card as an issue or perhaps too much power draw on power supply.

But there have been some issues on AMD video drivers also which I know little about.

No. I have to have a video card, as far as I can tell. (ASUS M5A97 R2.0 motherboard)

---

### Post by #&amp;thj^% on 2017-07-12
I'm at a loss here :confused: I can find no apparent reason for your issue's.
Kernel maybe...but doubtful. I'm still leaning on possible hardware problems here.
Even though it has been just fine for 3 years dose not exclude possibility of pending failure of a chip set. (I have seen as I said, it take months before the chipset fails or dies )
Try booting to a older or lower version kernel for a couple of boots to confirm the same conditions still exist.
If you still have the 4.4 kernel that would be the one to try.

---

### Post by aviator1 on 2017-07-12
> **1fallen said:**
> I'm at a loss here :confused: I can find no apparent reason for your issue's.
Kernel maybe...but doubtful. I'm still leaning on possible hardware problems here.
Even though it has been just fine for 3 years dose not exclude possibility of pending failure of a chip set. (I have seen as I said, it take months before the chipset fails or dies )
Try booting to a older or lower version kernel for a couple of boots to confirm the same conditions still exist.
If you still have the 4.4 kernel that would be the one to try.

Since this was a new install, I don't think I would have anything earlier to log on to?

Here is what I see when I logon.

If I choose the 14.04 LTS, I get to a password screen, but then a system error message. I must still have 14.04 on my second drive.

If I choose the advanced logon selection, I get taken to a desktop at 1024X768 and no  control to change the display. However, everything else seems to work.

Can you recommend a graphics card that won't break the bank?

Sorry about them being upside down again. They are correct on my desktop.

Thanks very much for your help.
[ATTACH=CONFIG]275972[/ATTACH][ATTACH=CONFIG]275973[/ATTACH]

---

### Post by aviator1 on 2017-07-12
Will be offline for about 2 hours

---

### Post by aviator1 on 2017-07-12
I'm going to be offline until Friday afternoon.

I really appreciate all the help.

Pleas let me have your thoughts, suggestions, or ideas.

Kind Regards.

---

### Post by vasa1 on 2017-07-13
> **aviator1 said:**
> No. I have to have a video card, _as far as I can tell_. (ASUS M5A97 R2.0 motherboard)
You could install *inxi* with ```
sudo apt-get install inxi
```and then post the output of```
inxi -F
```here.

---

### Post by #&amp;thj^% on 2017-07-14
> **aviator1 said:**
> Since this was a new install, I don't think I would have anything earlier to log on to?

Here is what I see when I logon.

If I choose the 14.04 LTS, I get to a password screen, but then a system error message. I must still have 14.04 on my second drive.

[ATTACH=CONFIG]275972[/ATTACH][ATTACH=CONFIG]275973[/ATTACH]
If you downloaded your install from the link I provided earlier [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)
You should not show a entry for 14.04 at all...**you are doing something wrong when installing** your system.
Now I'm pretty sure your hardware is OK...**but user error is the problem here now**
A Clean install would have removed your entry for the OLD 14.04 Grub!

---

### Post by aviator1 on 2017-07-14
> **1fallen said:**
> If you downloaded your install from the link I provided earlier [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)
You should not show a entry for 14.04 at all...**you are doing something wrong when installing** your system.
Now I'm pretty sure your hardware is OK...**but user error is the problem here now**
A Clean install would have removed your entry for the OLD 14.04 Grub!

The 14.04 is on the second (storage) drive, not my primary. The only thing on my primary SSD is the new install of 16.04. It did have Windows 7 on it, but I just completely eliminated that with the new install.

---

### Post by aviator1 on 2017-07-14
I have discovered something.

When I did the clean install on my SSD, I still had the second storage HDD installed. 

I disconnected the SSD, and did a clean install on the HDD. I booted up and the first time, had the same old issues. However, I subsequently shut down completely and started up 10 times and everything worked OK.

I then disconnected the HDD and reconnected the SSD. I had the same old issues. I noticed at bootup that 14.04 was still in the selection list. When I did the clean install I selected erase everything on the list.

I ran a boot repair and now have something completely different on an SSD only bootup (see image)

I thought I would try another clean install, but when I have the install CD, I don't get a selection for another install.

---

### Post by aviator1 on 2017-07-14
Better image

---

### Post by aviator1 on 2017-07-14
I think the culprit is the SSD.

I was able to do another clean  install on the SSD, and had the same navigation problems from a cold boot. Still  had to do the logoff/logon to get things working.

I disconnected  the SSD and used only the HDD, and after 10 more cold boots, everything  is still working fine. There is a noticeable speed loss using the HDD (I  think it is a 5400 RPM HDD)

Possibly something in the SSD is failing, maybe *Intermittently*?

Have you ever seen this before?

Thanks for your response.

---

### Post by #&amp;thj^% on 2017-07-15
> **aviator1 said:**
> I think the culprit is the SSD.

Possibly something in the SSD is failing, maybe *Intermittently*?

Have you ever seen this before?

Thanks for your response.
I have no SSD's yet... but I have seen this on PATA && SATA drive's>> quirky oddities.
But yes you would notice a speed difference with a 5400 rpm drive.:)
Well at least we know it is a hardware related problem now. :(

---

### Post by aviator1 on 2017-07-15
> **1fallen said:**
> I have no SSD's yet... but I have seen this on PATA && SATA drive's>> quirky oddities.
But yes you would notice a speed difference with a 5400 rpm drive.:)
Well at least we know it is a hardware related problem now. :(

I am going to give it a few days before I report solved. 

I really appreciate your time and efforts. And, Thanks to CatKiller and Old Fred too.

Regards

---

