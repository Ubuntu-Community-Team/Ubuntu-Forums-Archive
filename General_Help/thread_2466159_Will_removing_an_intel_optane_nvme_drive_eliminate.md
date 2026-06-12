---
title: "Will removing an intel optane nvme drive eliminate the RST restriction"
date: 2021-08-21
forum: General Help
---

### Post by gh0zt362 on 2021-08-21
After an update some part of it bork my system and now the xfce4-panel wont auto start media fkey controls dont work blah blah.

So I burn 2004 to a DVD and went to go install it and got a notice saying the rapid storage technology rst on the Intel chipset was preventing it from running and it had to be turned off. I went into the BIOS to attempt to see if I could turn it off and there's no setting on my BIOS I don't know whether it's an older bios that doesn't have that option to turn the rst off but it will not turn off so now I have a permanently board system and I can't install a new distro on it. So I was wondering if I remove the Intel optane drive would that eliminate the rst restriction on installing Ubuntu studio?

---

### Post by tea for one on 2021-08-21
I would be surprised if there were no settings in the UEFI set up to enable/disable Optane?

Is this link any help [https://support.hp.com/gb-en/document/c05591811](https://support.hp.com/gb-en/document/c05591811)

---

### Post by rbmorse on 2021-08-21
What hardware? 

The EFI setting you are looking for is the one that sets the disk controller operating mode. For ASUS machines this can be found under the under SATA options tab of Advanced settings. Dunno know about other brands.  

The choices vary depending upon the vintage of the machine but you have an Optane(tm) capable unit the current setting will probably be IRST or RAID or Intel RAID.  This needs to be changed to AHCI mode. 

Note that making this change will disable Optane(tm) capability and may keep you from booting into Windows on a machine configured for dual-booting until Windows is reconfigured to use the AHCI mode disk controller driver. 

But, if Ubuntu was previously installed and running at some point the disk controller mode should already in AHCI mode.

---

### Post by gh0zt362 on 2021-08-22
Thats what im saying. How did the install take no problem but now is critical RST failure?  Doesnt make sense.

Ill check bios settings again and see if i can find what youre referring to.

And windows last all of 10mins on that machine when I bought it.

---

### Post by oldfred on 2021-08-22
Windows updates will reset many UEFI settings to defaults.
You have to go back into UEFI and redo them.

Often you have to update UEFI and should update SSD firmware.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)


There is Intel software you can run in Windows to turn it off.
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735)
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

---

### Post by gh0zt362 on 2021-08-24
So I tried dist upgrade and it got me to 21.04 but still no right click menu extras nor xfce4-panel autostart . 


I tried dconf reset , I tried reinstall ubuntu desktop .... nothing works . Still in this barebones state 


I went into bios and there is NO SATA settings . It outlines non raid drives  but gives no option to change to ahci state . 


There are literally no settings to turn off RST . 

This machine came with win 10 and installed Ubuntu Studio 19.04 no issues. Now all of a sudden the RST  setting that cant be turned off is active and I cant install ubuntu studio 20.10lts . 


I dont know what to do Bios is F .42 revision 5 and has hardly any configuration options . Am I just doomed with a borked machine ?

---

### Post by gh0zt362 on 2021-08-24
tried installing mysql server to re install missing .services so I can logout  as I have no xfce-sessions-manager so I cant save sessions after I order sessions and startup to autostart xfce4-panel and cairo-dock . 


This is a real bummer . Shouldnt have gotten a machine with dumb optane and fisher price my first BIOS with no sata setting ...  ughhh   


I might have to eat this machine and buy another one . This borked state is just unusable . having to manually open everything and keep open terminals , no extra right click menu settings . no configurations saving .

---

### Post by oldfred on 2021-08-24
Did you see the link in post #5 on using an Intel app in Windows to change Optane settings?

---

### Post by gh0zt362 on 2021-08-25
> **oldfred said:**
> Did you see the link in post #5 on using an Intel app in Windows to change Optane settings?

Did you see where i said I installed ubuntu previously no problems and now i cant reinstall?

I dont have windows.  Windows lasted all of 10 minutes on this machine when id bought it.im running Ubuntu Studio 21.04 non lts which i upgraded from 20.10 lts hoping it would install missing packages , settings and configuration s to solve my problem. And it didnt

---

### Post by tea for one on 2021-08-25
> **gh0zt362 said:**
>  So I was wondering if I remove the Intel optane drive would that eliminate the rst restriction on installing Ubuntu studio?

> **gh0zt362 said:**
> I might have to eat this machine and buy another one . This borked state is just unusable 

I've been following this thread with interest because I **cannot** believe that the UEFI/BIOS lacks a setting to enable/disable Optane?
Is it hidden with a Supervisor or Admin password?
Can you supply any relevant UEFI/BIOS screenshots?

If the PC is unusable, then physically remove the Optane drive (because nothing ventured, nothing gained) and set the UEFI/BIOS back to default.
Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
See if anything miraculously appears in UEFI concerning AHCI, RST or RAID etc.

Then try and boot into a Live Ubuntu session.

---

### Post by oldfred on 2021-08-25
See this HP, shows screen shots for .
[https://ubuntuforums.org/showthread.php?t=2462045&p=14038639#post14038639](https://ubuntuforums.org/showthread.php?t=2462045&p=14038639#post14038639)
Was under UEFI HII configuration for controller type.

---

### Post by gh0zt362 on 2021-08-25
No such tab in the bios.  My machine has an old bare bones F.42 REVISION 5 bios with hardly any configuration settings.  Shows UEFI non raid drives but no option to change SATA mode or turn RST off 


So looks like i have 3 options. Buy and re install windows and hope the windows malware has the ability to turn RST off on the dino bios.

Try to figure out whats wrong with my current borked distro

Or abandon the machine and get an amd laptop.

Id like to figure out whats wrong with this machine but ive tried all the tricks i know to no avail.

Problem is i cant save any session modifications due to xfce-sessions-manager not being presented by any appropriate .service files.


No sessions listed in the startup and sessions box either .   Sucks.

---

### Post by oldfred on 2021-08-25
If system orginally came with Windows 10 in UEFI boot mode, your product key is inside the UEFI.
You can just reinstall Windows using standard Windows ISO. Issue then often is what vendor drivers may be required.

I have found that an external USB3 SSD is almost as fast as an internal SSD and faster than internal HDD.
Some use full install on external drive to not change internal drive's configuration.

---

### Post by gh0zt362 on 2021-09-01
Ok , so re install not an option ive been working on figuring out the problem . It seems xfce4-session not autostarting ?   first time I tried  to manually start it EVERYTHING came back . right click menu extras with desktop settings , cairo dock  , xfce4-panel options that had been missing . Sessions and startup current session wasn't empty and was showing the current session config and didnt return org.xfce.sessions.manager not being provided by any .service errror didnt show when I tried to save the session



 ```
xfce4-session/usr/bin/iceauth:  creating new authority file /run/user/1000/ICEauthority
gpg-agent: a gpg-agent is already running - not starting a new one
Another Window Manager (Openbox) is already running on screen :0.0
To replace the current window manager, try "--replace"


(xfwm4:19507): xfwm4-WARNING **: 10:54:57.558: Could not find a screen to manage, exiting


(xfce4-panel:19530): xfce4-panel-CRITICAL **: 10:55:05.654: Name org.xfce.Panel lost on the message dbus, exiting.
Xfce Power Manager: Another power manager is already running
Tracker-Message: 10:55:23.087: Set scheduler policy to SCHED_IDLE
Tracker-Message: 10:55:23.087: Setting priority nice level to 19
Another notification daemon is running, exiting


** (update-notifier:19633): WARNING **: 10:55:23.214: already running?


(tracker-miner-fs:19630): Tracker-CRITICAL **: 10:55:23.378: Could not request DBus name 'org.freedesktop.Tracker1.Miner.Files': D-Bus service name:'org.freedesktop.Tracker1.Miner.Files' is already taken, perhaps the application is already running?


(polkit-gnome-authentication-agent-1:19655): GLib-CRITICAL **: 10:55:24.738: g_variant_new_string: assertion 'string != NULL' failed


(polkit-gnome-authentication-agent-1:19655): polkit-gnome-1-WARNING **: 10:55:24.739: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (xfce4-volumed:19681): WARNING **: 10:55:25.063: Binding 'XF86AudioRaiseVolume' failed!


** (xfce4-volumed:19681): WARNING **: 10:55:25.070: Binding 'XF86AudioLowerVolume' failed!


** (xfce4-volumed:19681): WARNING **: 10:55:25.075: Binding 'XF86AudioMute' failed!


(xfce4-panel:19606): xfce4-panel-CRITICAL **: 10:55:25.126: Name org.xfce.Panel lost on the message dbus, exiting.
Tracker-Message: 10:55:25.132: Set scheduler policy to SCHED_IDLE
Tracker-Message: 10:55:25.132: Setting priority nice level to 19
blueman-applet version 2.1.4 starting
There is an instance already running


(tracker-extract:19686): Tracker-CRITICAL **: 10:55:26.637: Could not request DBus name 'org.freedesktop.Tracker1.Miner.Extract': D-Bus service name:'org.freedesktop.Tracker1.Miner.Extract' is already taken, perhaps the application is already running?


(process:19664): ayatana-indicator-application-service-WARNING **: 10:55:26.730: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
warning :  (/build/cairo-dock-zB8fkd/cairo-dock-3.4.1+git20201103.0836f5d1/src/implementations/cairo-dock-egl.c:gldi_register_egl_backend:232)  
  Cairo-Dock was not built with EGL support
warning :  (/build/cairo-dock-zB8fkd/cairo-dock-3.4.1+git20201103.0836f5d1/src/implementations/cairo-dock-glx.c:_initialize_opengl_backend:129)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...


 ============================================================================
	Cairo-Dock version : 3.4.1
	Compiled date      : Jan  2 2021 11:22:34
	Built with GTK     : 3.24
	Running with OpenGL: 1
 ============================================================================


g_file_test: assertion 'filename != NULL' failed
g_file_test: assertion 'filename != NULL' failed
sh: 1: /usr/lib/x86_64-linux-gnu/cairo-dock/cairo-dock-launcher-API-daemon: not found
^C
** (xiccd:19615): WARNING **: 10:58:42.975: Exiting


(xfce4-volumed:19681): xfce4-volumed-CRITICAL **: 10:58:42.982: xvd_context_state_callback: The connection failed or was disconnected, is PulseAudio Daemon running?

```

Then I ctrl c to exit xfce4-session to see if it stuck and everything was lost again 

And then I initialized xfce4-session in terminal again and not everything came back but cairo dock did and Sessions and startup current session was showing the current session again . this is the return on the second initialization of xfce4-session ```
xfce4-session
gpg-agent: a gpg-agent is already running - not starting a new one
Tracker-Message: 10:59:24.740: Set scheduler policy to SCHED_IDLE
Tracker-Message: 10:59:24.740: Setting priority nice level to 19
Xfce Power Manager: Another power manager is already running


** (xfce4-volumed:20386): WARNING **: 10:59:24.757: Binding 'XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.757: Binding '<Ctrl>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.758: Binding '<Alt>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.758: Binding '<Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.759: Binding '<Shift>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.759: Binding '<Ctrl><Shift>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.760: Binding '<Ctrl><Alt>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.761: Binding '<Ctrl><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.761: Binding '<Alt><Shift>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.762: Binding '<Alt><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.762: Binding '<Shift><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.762: Binding '<Ctrl><Shift><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.762: Binding '<Ctrl><Shift><Alt>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.763: Binding '<Ctrl><Alt><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.763: Binding '<Shift><Alt><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.764: Binding '<Ctrl><Shift><Alt><Super>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.764: Binding 'XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.764: Binding '<Ctrl>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.765: Binding '<Alt>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.765: Binding '<Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.765: Binding '<Shift>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.766: Binding '<Ctrl><Shift>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.766: Binding '<Ctrl><Alt>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.767: Binding '<Ctrl><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.767: Binding '<Alt><Shift>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.768: Binding '<Alt><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.768: Binding '<Shift><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.768: Binding '<Ctrl><Shift><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.769: Binding '<Ctrl><Shift><Alt>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.770: Binding '<Ctrl><Alt><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.770: Binding '<Shift><Alt><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.770: Binding '<Ctrl><Shift><Alt><Super>XF86AudioLowerVolume' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.771: Binding 'XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.771: Binding '<Ctrl>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.772: Binding '<Alt>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.772: Binding '<Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.772: Binding '<Shift>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.773: Binding '<Ctrl><Shift>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.773: Binding '<Ctrl><Alt>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.773: Binding '<Ctrl><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.774: Binding '<Alt><Shift>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.774: Binding '<Alt><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.775: Binding '<Shift><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.778: Binding '<Ctrl><Shift><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.778: Binding '<Ctrl><Shift><Alt>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.779: Binding '<Ctrl><Alt><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.779: Binding '<Shift><Alt><Super>XF86AudioMute' failed!


** (xfce4-volumed:20386): WARNING **: 10:59:24.780: Binding '<Ctrl><Shift><Alt><Super>XF86AudioMute' failed!


** (update-notifier:20367): WARNING **: 10:59:24.781: already running?
Another notification daemon is running, exiting
Tracker-Message: 10:59:24.854: Set scheduler policy to SCHED_IDLE
Tracker-Message: 10:59:24.855: Setting priority nice level to 19


(process:20419): ayatana-indicator-application-service-WARNING **: 10:59:24.860: Unable to get watcher name 'org.kde.StatusNotifierWatcher'


(polkit-gnome-authentication-agent-1:20402): GLib-CRITICAL **: 10:59:24.867: g_variant_new_string: assertion 'string != NULL' failed


(polkit-gnome-authentication-agent-1:20402): polkit-gnome-1-WARNING **: 10:59:24.870: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(xfce4-panel:20349): xfce4-panel-CRITICAL **: 10:59:24.902: Name org.xfce.Panel lost on the message dbus, exiting.


(xfce4-panel:20455): xfce4-panel-CRITICAL **: 10:59:24.940: Name org.xfce.Panel lost on the message dbus, exiting.


(tracker-miner-fs:20366): Tracker-CRITICAL **: 10:59:25.054: Could not request DBus name 'org.freedesktop.Tracker1.Miner.Files': D-Bus service name:'org.freedesktop.Tracker1.Miner.Files' is already taken, perhaps the application is already running?
blueman-applet version 2.1.4 starting
There is an instance already running


(tracker-extract:20436): Tracker-CRITICAL **: 10:59:25.437: Could not request DBus name 'org.freedesktop.Tracker1.Miner.Extract': D-Bus service name:'org.freedesktop.Tracker1.Miner.Extract' is already taken, perhaps the application is already running?
warning :  (/build/cairo-dock-zB8fkd/cairo-dock-3.4.1+git20201103.0836f5d1/src/implementations/cairo-dock-egl.c:gldi_register_egl_backend:232)  
  Cairo-Dock was not built with EGL support
warning :  (/build/cairo-dock-zB8fkd/cairo-dock-3.4.1+git20201103.0836f5d1/src/implementations/cairo-dock-glx.c:_initialize_opengl_backend:129)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...


 ============================================================================
	Cairo-Dock version : 3.4.1
	Compiled date      : Jan  2 2021 11:22:34
	Built with GTK     : 3.24
	Running with OpenGL: 1
 ============================================================================


g_file_test: assertion 'filename != NULL' failed
g_file_test: assertion 'filename != NULL' failed
sh: 1: /usr/lib/x86_64-linux-gnu/cairo-dock/cairo-dock-launcher-API-daemon: not found
_get_desktop_bg_surface: assertion 'iRootPixmapID != 0' failed
gh0tz@gh0tz-HP-Laptop-17-by0xxx:~$ _get_desktop_bg_surface: assertion 'iRootPixmapID != 0' failed
warning :  (/build/cairo-dock-plug-ins-8mDJtI/cairo-dock-plug-ins-3.4.1+git20201022.a0d3415c/switcher/src/applet-load-icons.c:cd_switcher_load_desktop_bg_map_surface:197)  
  couldn't get the wallpaper
```


 . Alot of failures but I feel like im getting closer . Anyone have any ideas ? it looks like perhaps xfce4-session isnt autostarting upon boot ??? 

Im not a seasoned terminal veteran  so im not sure how to proceed but as I said I think im getting closer .

---

### Post by gh0zt362 on 2021-09-01
Also Id downloaded part of the digibyte blockchain and didgibyte installed a user on my machine around the time I started having this problem .   im going to try to remove digibyte crypto user and see what happens .

---

### Post by gh0zt362 on 2021-09-01
ok , so progress . I installed xdm and set xfce4- to start with ```
[COLOR=#000000][FONT=&quot]sudo /etc/init.d/xdm start
```

and also installed xubuntu-desktop .

Not sure which one of those worked but now I have a new problem my right and left click only work on some items . 

So far they work on applications menu in task panel , text entry fields , tab selection , cairo dock app selections . 

The mouse clicks dont work  on window  minimize / maximize but work on exit button on browser ( maybe others? )   I have no right click menu now anywhere . not on desktop or anywhere else . 

right now I left click highlighted text and right clicked for a menu to copy and menu millisecond flashes and disappears like something is preventing the menu from staying displayed ( app conflict somewhere force closing the menu ? ) 

Im almost there. if I can fix this mousepad issue im good . Then ill take a picture with my phone of the bios and post it in this thread. 
[/FONT][/COLOR]

---

### Post by gh0zt362 on 2021-09-01
ok also cant type text in terminal now ? but I can type in browser ? I think because mouse buttons arent allowing me to switch fields ??  man . 1 step forward two steps back

---

### Post by gh0zt362 on 2021-09-01
Yeaaa.... suuuuper weird.   minimize and maximize buttons on browser highlight when I click them for a flash but do nothing . right click menu works in browser but just flashes for a second on desktop when browser is closed .  text entry works on terminal when browser is closed but not when browser is open . 

its almost click chromium has super priority when open and overrides everything like task/window switching with external applications .  and when its closed something is conflicting when the right click menu attepmts to initialize and immediately closes it . 


hmmm

---

### Post by gh0zt362 on 2021-09-01
ok we are there . I just need to know whats going on here ```
xfwm4 --replace
```  fixed the window and mouse clicks problem .   so I guess the window manager is causing an issue.  now I need the window manager to select xfwm4 permanently ....  how does one accomplish this ?

---

### Post by gh0zt362 on 2021-09-01
Ok , I rebooted . looks like xfwm4 --replace worked. Im now going to reboot to bios and take some pictures of options with my phone . Itll take a bit to post pictures so bear with me ...

---

### Post by gh0zt362 on 2021-09-01
[IMG]https://ibb.co/61fnKSS[/IMG][[IMG]https://i.ibb.co/wwx0nqq/IMG-20210901-131823504.jpg[/IMG]]("https://ibb.co/61fnKSS")
[[IMG]https://i.ibb.co/hYpJsdy/IMG-20210901-131848181.jpg[/IMG]]("https://ibb.co/VwXcVCt")
[[img]https://i.ibb.co/fQJSB5R/IMG-20210901-131911333.jpg[/img]](https://ibb.co/N7R3QPh)

---

### Post by oldfred on 2021-09-01
Please attach screenshots or photos.

If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Not sure if same:
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/hp-17-by0XXX/td-p/8050338](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/hp-17-by0XXX/td-p/8050338)
But it shows 
The BIOS is F.62 2/8/2021 SMBIOS version 3.0

If so you need to update UEFI.

---

### Post by tea for one on 2021-09-01
> **gh0zt362 said:**
> There are literally no settings to turn off RST 

You mentioned the above in post 6 yet your recent screenshot displays the RST setting?

Can you see the menu options behind [COLOR="#0000FF"]Intel (R) Rapid Storage Technology[/COLOR]?

---

### Post by gh0zt362 on 2021-09-01
> **tea for one said:**
> You mentioned the above in post 6 yet your recent screenshot displays the RST setting?

Can you see the menu options behind [COLOR=#0000FF]Intel (R) Rapid Storage Technology[/COLOR]?

Literally behind that arrowhead are the drive selections . 1) 2TB and if you click you get drive info 

2) 16gb optane drive with drive info as pictured ....  

the 13.8 or whatever the exact storage size in one of the screen shots I posted is the end of the fork of options. 

the only sub menu I didnt post is the fork for either 2tb or 16gb drive .  But the 16gb screenshot is the end of the tree with simple drive info .

---

### Post by gh0zt362 on 2021-09-01
I dont even see an option in the bios to update it .

---

### Post by tea for one on 2021-09-01
Your 16GB Optane is NVME and can possibly be enabled/disabled via the NVME Controller or the PCIE Interface.

However, if your 2TB drive is [COLOR="#0000FF"]also[/COLOR] NVME, then you may also inadvertently enable/disable this one simultaneously.

Just guessing at the moment because there is very little consistency between each vendor's UEFI screens.

---

### Post by oldfred on 2021-09-01
All the UEFI screens I have used & those others have posted have UEFI/BIOS update on last tab to right.
You need to review manual, if you do not have it, download it from HP.

UEFI typically has multiple ways to update.
Some update from Windows directly, a few now update from Ubuntu directly using fwupdmgr (only seen HP's workstations on list), most then can directly read an update file from a FAT32 formatted partition either internal or flash drive or from a DOS type bootable flash drive with update as an .exe program with the update file.
My NVMe SSD has a bootable ISO with just the update for my model NVMe drive. Looked like an old DOS screen, but worked.

---

### Post by Frogs Hair on 2021-09-01
In some brands of computer intel optane is enabled,disabled,or cleared from a utility in Windows installed by the oem. Not all brands have an option to enable or disable optane in the bios.

---

### Post by gh0zt362 on 2021-09-02
i wonder why the original ubuntu studio install wasnt prevented by RST . Bizzare , everything works again atleast except screen sleeps and locks despite all lock sleep controls disabled and some app icons dont show up on any app menu like opera browser

---

### Post by bobunderwood99 on 2021-09-07
I don't know if this will help but there is a Optane configuration utility that runs on Ubuntu:

[https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux)

---

### Post by cubdukat1968 on 2021-10-05
It would, but you would have to unpair the Optane stick from whatever drive it's paired with within Windows. Once it's unpaired in Windows, you can disable it in UEFI then physically uninstall.

I had something similar happen. I couldn't get the Optane stick to work in Win10 when I first built my system, so I disabled and removed it. then I set up a dual-boot with Ubuntu. But I later went back and reinstalled the Optane stick and was able to get it to work in Win10, but I lost the dual-boot. I found that by disabling the RST option in UEFI, I got the dual-boot back, but if I wanted to boot into Win10, I had to reenable it otherwise the system wouldn't boot. 

If you've got Optane in your system, you've definitely got a way to disable it, if HP hasn't locked off that area for you to disable it. 

But I would definitely not physically uninstall the Optane stick until it's been totally disabled; you'll end up borking Win10 as well. If you're not willing to take the risk of doing it, I'd definitely let a tech do it. With manufacturers locking off that kind of functionality in UEFI, that may be the only way to do it.

I think it's absolutely ridiculous that Intel has not made Optane and RST available to Linux users. That's why I will soon be ripping my Optane stick out and setting up a new dual-boot. Optane will go down with Rambus memory as yet another Intel gambit that was ultimately worthless.

---

