---
title: "system crashed, won't boot anymore (12.10 64bit)"
date: 2013-01-21
forum: General Help
---

### Post by E411 on 2013-01-21
Hi there,

I recently installed ubuntu (12.10 64bit) on my brand new laptop. A few days ago, while I was streaming a video, everything stopped quite suddenly. I don't know if it is actually related but there was no battery in the laptop at the time.

Since then the system hangs at boot. After the purple screen and the Ubuntu sound, I get a somehow flickering black screen. I can still go through grub holding F8, boot a kernel in recovery mode and then drop to root shell prompt. 

I can access the filesystem, I can run apt-get, I can go online using lynx, but when I try to run startx I get a fatal server error.

I can also boot from my USB stick so that I can use a human-friendly browser ;)

Do you guys have any idea of what happened and how to fix it? It seems that I could reinstall everything but I'd still prefer to understand and repair.

---

### Post by Bashing-om on 2013-01-21
E411l Hi !

Try this, as is worth a shot.
Boot into the recovery kernel, choose fsck to check/repair the file system.
Let fsck run and choose to "resume normal boot" to the desktop.
Reboot.

[INDENT][INDENT]look'n good now ?

[/INDENT][/INDENT]

---

### Post by E411 on 2013-01-22
Hello bashing-om,

I forgot to mention that I tried that numerous time, but the system hangs:

fsck from util-linux 2.20.1
dosfsck 3.0.13, 30 Jun 2012, FAT32, LFN
/dev/sda1: 5 files, 2207/95491 clusters
/devsda2: 223829/38805504 files (0.3% non-contiguous), 3559339/155221760 blocks

I have to say that while /dev/sda1 is indeed a fat partition (mounted on /boot/efi), /dev/sda2 is an ext4 partition, which must be the reason why it hangs.

I can still check any filesystem from the command prompt though but I am unsure which one (fsck, e2fsck,..) and which options I should use.

---

### Post by bogan on 2013-01-22
Hi!, **E411**,

There is a bug in fsck 12.10 from recovery that causes it to hang even when there are no faults, if you press 'Ctrl+c' and wait a bit, it will drop to a text terminal, and you can run it from there more sucessfully,.
Alternatively 'Ctrl+Alt+Del' will return you to the Recovery menu.

Chao!, **bogan.**

---

### Post by Bashing-om on 2013-01-22
As I live and learn. Thanks bogan for the update.
@E411; What is your current status (after bogan's advise)....->
How may we be of further assistance ?


[INDENT]where there exist a will, a desktop will exist
[/INDENT]

---

### Post by E411 on 2013-01-22
I ran fsck (see output below) but it didn't change anything to the initial problem: the system still crashes just after the boot

> fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda2: clean, 223827/38805504 files, 3559406/155221760 blocks
dosfck 3.0.13, 30 Jun 2012, FAT32, LFN
/dev/sda1: 5files, 2207/95491 clusters

---

### Post by Bashing-om on 2013-01-22
E411;

It appears that starting the desktop is the sole problem. Try this:
```
sudo service lightdm stop
sudo unity --reset
sudo service lightdm start
```which should first reset compiz then unity to the default settings.

I have no access to 12.10, therefore the --reset command is not tested by me. I am not sure that it is a valid command for 12.10. I recall that unity has gone through a lot of changes for version 12.10.

Still worth a try.

---

### Post by E411 on 2013-01-22
sudo service lightdm stop

> stop: Unknown instance:

I tried sudo service lightdm restart

> stop: Unknown instance:
lightdm start/running, process 1002

and after that again sudo service lightdm stop

still

> stop: Unknown instance:

---

### Post by Bashing-om on 2013-01-22
E411;

Unity has indeed changed greatly in 12.10...the above commands are no longer supported !
This link is a tutorial for resetting unity in 12.10:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

I suggest the second method referenced in the article. imo simpler by far than the 1st, installing a ppa on the system.

The instructions are simple and straight forward, however, if there is a problem; Will assist !

Reset unity and advise status.

---

### Post by bogan on 2013-01-22
HI!**, Bashing-on & E41**1,

The 'unity --reset' command is deprecated with 12.10, but usually works, though it messes up the display and you have to reboot.

The approved command is :```
 setsid unity
```RE: lightdm 'unknown instance'; I had a lot of trouble with this the other day following the latest kernal update  from 12.10 3.5.0-22-generic #32 to #34.

Try```
 startx # after sudo service lightdm stop
```You will probably get a 'fatal Error' which will tell you what is wrong - probably if as in my case - a mismatched kernal module.

If that is what it is, you will need to 'apt-get remove --purge' the existing video driver and 'install --reinstall' it.

Chao!, **bogan**.

---

### Post by E411 on 2013-01-23
Hi guys,

All attempts to reset unity (I tried both methods) trigger a similar message:

> error: Error spawning command-line `dbus-launch --autolaunch=df06b5a2781cf40414047a1150f1b0fb --binary-syntax --close-stderr': Child process exited with code 1

---

### Post by bogan on 2013-01-23
Hi!, **E411**,

Is the result the same after re-booting?

No idea what that error means,'unity reset' often produces a crop of error messages, but still often works.

Does the .xsessions-errors file show any significant Errors or Warnings?? It is a hidden file in your Home folder. [Press 'Ctrl+h' to show hidden files.]

Chao!,** bogan**.

---

### Post by E411 on 2013-01-23
> **bogan said:**
> 

Is the result the same after re-booting?

Does the .xsessions-errors file show any significant Errors or Warnings?? It is a hidden file in your Home folder. [Press 'Ctrl+h' to show hidden files.]



Yes and oh yes. Wellm not sure what is significant in there but here is the log file

> (gnome-settings-daemon:1841): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp

(gnome-settings-daemon:1841): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS: unable to get EDID for output
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
** Message: applet now removed from the notification area
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
** Message: using fallback from indicator to GtkStatusIcon
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/myusername/.compiz/session/10966be71173652049135801679327052500000017590031"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (core) - Warn: Attempted to restack relative to 0x1000009 which is not a child of the root window or a window compiz owns
** Message: moving back from GtkStatusIcon to indicator
WARNING:root:timeout reached, exiting
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

** (firefox:3954): WARNING **: Failed to open webapp application path dir /usr/share/ubuntu/unity-webapps/userscripts: Error opening directory '/usr/share/ubuntu/unity-webapps/userscripts': No such file or directory

** (firefox:3954): WARNING **: Failed to open webapp application path dir /usr/share/gnome/unity-webapps/userscripts: Error opening directory '/usr/share/gnome/unity-webapps/userscripts': No such file or directory

** (firefox:3954): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory
polkit-agent-helper-1: pam_authenticate failed: Authentication failure

(gnome-control-center:4189): user-accounts-cc-panel-WARNING **: SetPassword call failed: GDBus.Error:org.freedesktop.Accounts.Error.Failed: running '/usr/bin/gpasswd' failed: /usr/bin/gpasswd returned an error (3): gpasswd: user 'mywifesusername' is not a member of 'nopasswdlogin'


(gnome-settings-daemon:1841): color-plugin-WARNING **: Done switch to new account, reload devices

(gnome-settings-daemon:1841): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS: unable to get EDID for output

(gnome-settings-daemon:1841): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:1841): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
gnome-session[1759]: WARNING: Unable to restart system: Authorization is required
gnome-session[1759]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
gnome-session[1759]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(nm-applet:1885): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:1883): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:1882): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(telepathy-indicator:2053): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:2372): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-manager:2393): Gdk-WARNING **: update-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(nautilus:1895): Gdk-WARNING **: nautilus: Fatal IO error 0 (Success) on X server :0.


** (zeitgeist-datahub:2070): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

---

### Post by bogan on 2013-01-23
Hi!, **E41**1,

The: > Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(nautilus:1895): Gdk-WARNING **: nautilus: Fatal IO error 0 (Success) on X server :0.and similar errors at the end of the log tie in with the 'startx' fatal error mentioned in the OP.

What error mesages do you get whem you run 'startx' ??

I had a similar set of .xsession-error reports the other day and cured it by 'remove --purge'ing , and 'install --re-install'ing the video driver and doing a 'Cold Finger Restart'.

That means shut down, power off and cable removed, unplug all external devices except monitors, [if a laptop, disconnect the battery] hold the power button in for at least 30 seconds [ longer if you do not get a flash from the disk activity light ].

Then reconnect and boot up normally. I know it does not make obvious sense, but believe me it sometimes works.

It may also cure the problems in getting the EDID data. What monitor/s are you using and how is it connected ??  VGA/DVI/HDMI ??? an Adapter ??

The other thing I do not like the look of, is all the "Pemission refused" messages, though I have no idea what might cause them.

Perhaps **Bashing-om** has some ideas, or someone else?

Chao!,** bogan**.

---

### Post by E411 on 2013-01-23
Something very weird, here bogan.

I decided to reinstall everything (as it was a fresh installation anyway, and it is actually my wife's laptop not mine, she was using mine which made me very unhappy, etc...).

So, hmmm, the new installation didn't change anything. I still get that flickering black screen right after the boot.

Which made me think that it is hardware related. But then why the hell can I use - without any problem - a live ubuntu through a usb stick?

:confused:

---

### Post by Bashing-om on 2013-01-23
E411, bogan -> The plot thickens !

OK, so we are dealing with a lap top so reseating the graphics card is not easy to do.

E411 when you (re)installed did you make sure you had checked the "install 3rd party software" box ? What hardware and modules are we working with:
To see your graphics card and info:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```This is the skinny on EDID:
> Since Hardy, the X server auto-detects what driver should be loaded for the video hardware it detects as present. It does this by polling the PCI bus for VGA devices, and then checks their PCI ID's against a registry of PCI ID's each video driver has reported as supported; if none are found, -vesa is the fallback. Next, it loads the driver and initializes it. Finally, it probes the monitor(s) for DDC or EDID information to determine its resolution, dpi, and other capabilities, and brings them up. In the event that the EDID info is not read, will have to provide that info manually.
[INDENT][INDENT]where a will exist a desktop will exist

[/INDENT][/INDENT]

---

### Post by E411 on 2013-01-24
> **Bashing-om said:**
> E411, bogan -> The plot thickens !

does it, really?


> **Bashing-om said:**
> 

E411 when you (re)installed did you make sure you had checked the "install 3rd party software" box ? 

I did

> **Bashing-om said:**
> 
To see your graphics card and info:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```

for some reason the output is in French, but it is still readable imo:

> description: VGA compatible controller
produit: Whistler LE [AMD Radeon HD 6625M Graphics]
fabriquant: Advanced Micro Devices [AMD] nee ATI
identifiant matériel: 0
information bus: pci@0000:01:00.0
version: 00
bits: 64 bits
horloge: 33MHZ
fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list
configuration: latency=0
ressources: mémoire:b0000000-bfffffff mémoire:c20000000-c201ffff portE/S:4000(taille=256) mémoire:c2040000-c205ffff

> 01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Whistler LE [AMD Radeon HD 6625M Graphics] [1002:6742]
Subsystem: Toshiba America Info Systems Device [1179:fb31]
Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series] [1002:aa90]

---

### Post by Bashing-om on 2013-01-24
E411;

The output shows a fairly recent ATI graphics card, NO driver is loaded.

What results from attempting to load a driver from the Additional Drivers utility (I am advised is under a tab in software sources application)?

[INDENT][INDENT]stroke'n and hope'n

[/INDENT][/INDENT]

---

### Post by E411 on 2013-01-24
> **Bashing-om said:**
> 

The output shows a fairly recent ATI graphics card.

Yes, it's a brand new laptop my wife bought a few days ago and she says that I crashed it by installing Linux on it. This is why I am under quite a huge pressure to fix it :(

> **Bashing-om said:**
> What results from attempting to load a driver from the Additional Drivers utility (I am advised is under a tab in software sources application)?


Well, in the live Ubuntu that I am booting from the usb stick, it says that the device is using the recommanded driver:
Using X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati (open-source, tested)

Obviously, on the system installed on the hard drive I have no graphical interface, which is why I can't open that window. I'd be happy to load a driver from the command line though but I have no idea how to do that.

I am still very surprised that the live ubuntu is working without any problem whereas the one freshly installed on my hard drive from the exact same usb stick is stuck.

---

### Post by Bashing-om on 2013-01-24
E411;

Making progress - looking better- And no, nothing you have done has "broke" that computer. 
The installCD utilizes different resources, It is often the case that graphics drivers specific to the onboard card need to be installed: To do so ....do this:
1. Boot up into your installation, soon as the bios splash screen clears, depress and hold the shift key -> grub menu.
2. In the grub menu insure the top item is highlighted (latest kernel version), press "e" to edit ->booting parameters, arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
arrow across to the term "quite splash" and insert "radeon.modeset=0" (with out the quotes) before "quiet splash" spaces between as delimiters. 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
3. ctl-x to continue to boot -> degraded graphics, OK .
4. Now find the Software sources application, open it, Additional Drivers tab utility, install the recommended driver.
5. reboot.
[INDENT][INDENT]hunky dory ?

[/INDENT][/INDENT]

---

### Post by black veils on 2013-01-24
**additional drivers** might be a separate application to **software sources**, if so, just search for it in the dash, or look in applications menu.

---

### Post by E411 on 2013-01-25
what happens when I add "radeon.modeset=0" is that I get a shell prompt on tty1 while tty7 is stuck on 
> * Stopping anac(h)ronistic crona few lines above I can see:

> *Starting LightDM Display Managerbut still  no graphical interface :(

So, has a look in /var/log/Xorg.0.log and there is something like 
> [    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"

Here is the full log file:

> [    16.820] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    16.820] X Protocol Version 11, Revision 0
[    16.820] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    16.820] Current Operating System: Linux blanco 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64
[    16.820] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic.efi.signed root=UUID=1d908588-c022-47c3-af8f-106b7e5b7aa1 ro radeon.modeset=0 quiet splash
[    16.820] Build Date: 27 November 2012  07:44:35AM
[    16.820] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.820] Current version of pixman: 0.26.0
[    16.820]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    16.820] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.820] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 25 14:34:04 2013
[    16.869] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.907] (==) No Layout section.  Using the first Screen section.
[    16.907] (==) No screen section available. Using defaults.
[    16.907] (**) |-->Screen "Default Screen Section" (0)
[    16.907] (**) |   |-->Monitor "<default monitor>"
[    16.930] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.930] (==) Automatically adding devices
[    16.930] (==) Automatically enabling devices
[    16.930] (==) Automatically adding GPU devices
[    16.969] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.969]     Entry deleted from font path.
[    16.970] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.970]     Entry deleted from font path.
[    16.970] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.970]     Entry deleted from font path.
[    16.970] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.970]     Entry deleted from font path.
[    16.970] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.970]     Entry deleted from font path.
[    16.970] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.970]     Entry deleted from font path.
[    16.970] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.970] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.970] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.970] (II) Loader magic: 0x7fc6fb120c40
[    16.970] (II) Module ABI versions:
[    16.970]     X.Org ANSI C Emulation: 0.4
[    16.970]     X.Org Video Driver: 13.0
[    16.970]     X.Org XInput driver : 18.0
[    16.970]     X.Org Server Extension : 7.0
[    16.970] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.971] (--) PCI:*(0:1:0:0) 1002:6742:1179:fb31 rev 0, Mem @ 0xb0000000/268435456, 0xc2000000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    16.971] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.994] Initializing built-in extension Generic Event Extension
[    16.994] Initializing built-in extension SHAPE
[    16.994] Initializing built-in extension MIT-SHM
[    16.994] Initializing built-in extension XInputExtension
[    16.994] Initializing built-in extension XTEST
[    16.994] Initializing built-in extension BIG-REQUESTS
[    16.994] Initializing built-in extension SYNC
[    16.994] Initializing built-in extension XKEYBOARD
[    16.994] Initializing built-in extension XC-MISC
[    16.994] Initializing built-in extension SECURITY
[    16.994] Initializing built-in extension XINERAMA
[    16.994] Initializing built-in extension XFIXES
[    16.994] Initializing built-in extension RENDER
[    16.994] Initializing built-in extension RANDR
[    16.994] Initializing built-in extension COMPOSITE
[    16.994] Initializing built-in extension DAMAGE
[    16.994] Initializing built-in extension MIT-SCREEN-SAVER
[    16.994] Initializing built-in extension DOUBLE-BUFFER
[    16.994] Initializing built-in extension RECORD
[    16.994] Initializing built-in extension DPMS
[    16.994] Initializing built-in extension X-Resource
[    16.994] Initializing built-in extension XVideo
[    16.994] Initializing built-in extension XVideo-MotionCompensation
[    16.994] Initializing built-in extension XFree86-VidModeExtension
[    16.994] Initializing built-in extension XFree86-DGA
[    16.994] Initializing built-in extension XFree86-DRI
[    16.994] Initializing built-in extension DRI2
[    16.994] (II) LoadModule: "glx"
[    17.032] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.063] (II) Module glx: vendor="X.Org Foundation"
[    17.063]     compiled for 1.13.0, module version = 1.0.0
[    17.063]     ABI class: X.Org Server Extension, version 7.0
[    17.063] (==) AIGLX enabled
[    17.064] Loading extension GLX
[    17.064] (==) Matched fglrx as autoconfigured driver 0
[    17.064] (==) Matched ati as autoconfigured driver 1
[    17.064] (==) Matched fglrx as autoconfigured driver 2
[    17.064] (==) Matched ati as autoconfigured driver 3
[    17.064] (==) Matched vesa as autoconfigured driver 4
[    17.064] (==) Matched modesetting as autoconfigured driver 5
[    17.064] (==) Matched fbdev as autoconfigured driver 6
[    17.064] (==) Assigned the driver to the xf86ConfigLayout
[    17.064] (II) LoadModule: "fglrx"
[    17.064] (WW) Warning, couldn't open module fglrx
[    17.064] (II) UnloadModule: "fglrx"
[    17.064] (II) Unloading fglrx
[    17.065] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.065] (II) LoadModule: "ati"
[    17.065] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.097] (II) Module ati: vendor="X.Org Foundation"
[    17.097]     compiled for 1.13.0, module version = 6.99.99
[    17.097]     Module class: X.Org Video Driver
[    17.097]     ABI class: X.Org Video Driver, version 13.0
[    17.097] (II) LoadModule: "radeon"
[    17.097] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.120] (II) Module radeon: vendor="X.Org Foundation"
[    17.120]     compiled for 1.13.0, module version = 6.99.99
[    17.120]     Module class: X.Org Video Driver
[    17.120]     ABI class: X.Org Video Driver, version 13.0
[    17.120] (II) LoadModule: "vesa"
[    17.121] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.164] (II) Module vesa: vendor="X.Org Foundation"
[    17.164]     compiled for 1.12.99.902, module version = 2.3.2
[    17.164]     Module class: X.Org Video Driver
[    17.164]     ABI class: X.Org Video Driver, version 13.0
[    17.164] (II) LoadModule: "modesetting"
[    17.164] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.172] (II) Module modesetting: vendor="X.Org Foundation"
[    17.172]     compiled for 1.13.0, module version = 0.5.0
[    17.172]     Module class: X.Org Video Driver
[    17.172]     ABI class: X.Org Video Driver, version 13.0
[    17.172] (II) LoadModule: "fbdev"
[    17.172] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.177] (II) Module fbdev: vendor="X.Org Foundation"
[    17.177]     compiled for 1.12.99.902, module version = 0.4.3
[    17.177]     Module class: X.Org Video Driver
[    17.177]     ABI class: X.Org Video Driver, version 13.0
[    17.177] (==) Matched fglrx as autoconfigured driver 0
[    17.177] (==) Matched ati as autoconfigured driver 1
[    17.177] (==) Matched fglrx as autoconfigured driver 2
[    17.177] (==) Matched ati as autoconfigured driver 3
[    17.177] (==) Matched vesa as autoconfigured driver 4
[    17.177] (==) Matched modesetting as autoconfigured driver 5
[    17.177] (==) Matched fbdev as autoconfigured driver 6
[    17.177] (==) Assigned the driver to the xf86ConfigLayout
[    17.177] (II) LoadModule: "fglrx"
[    17.177] (WW) Warning, couldn't open module fglrx
[    17.177] (II) UnloadModule: "fglrx"
[    17.177] (II) Unloading fglrx
[    17.177] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.177] (II) LoadModule: "ati"
[    17.177] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.177] (II) Module ati: vendor="X.Org Foundation"
[    17.177]     compiled for 1.13.0, module version = 6.99.99
[    17.177]     Module class: X.Org Video Driver
[    17.177]     ABI class: X.Org Video Driver, version 13.0
[    17.177] (II) LoadModule: "vesa"
[    17.177] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.177] (II) Module vesa: vendor="X.Org Foundation"
[    17.177]     compiled for 1.12.99.902, module version = 2.3.2
[    17.177]     Module class: X.Org Video Driver
[    17.177]     ABI class: X.Org Video Driver, version 13.0
[    17.177] (II) UnloadModule: "vesa"
[    17.177] (II) Unloading vesa
[    17.177] (II) Failed to load module "vesa" (already loaded, 0)
[    17.177] (II) LoadModule: "modesetting"
[    17.177] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.177] (II) Module modesetting: vendor="X.Org Foundation"
[    17.177]     compiled for 1.13.0, module version = 0.5.0
[    17.177]     Module class: X.Org Video Driver
[    17.177]     ABI class: X.Org Video Driver, version 13.0
[    17.177] (II) UnloadModule: "modesetting"
[    17.177] (II) Unloading modesetting
[    17.177] (II) Failed to load module "modesetting" (already loaded, 0)
[    17.177] (II) LoadModule: "fbdev"
[    17.178] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.178] (II) Module fbdev: vendor="X.Org Foundation"
[    17.178]     compiled for 1.12.99.902, module version = 0.4.3
[    17.178]     Module class: X.Org Video Driver
[    17.178]     ABI class: X.Org Video Driver, version 13.0
[    17.178] (II) UnloadModule: "fbdev"
[    17.178] (II) Unloading fbdev
[    17.178] (II) Failed to load module "fbdev" (already loaded, 0)
[    17.178] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE
[    17.180] (II) VESA: driver for VESA chipsets: vesa
[    17.180] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    17.180] (II) FBDEV: driver for framebuffer: fbdev
[    17.180] (++) using VT number 7

[    17.216] (II) [KMS] drm report modesetting isn't supported.
[    17.216] (II) [KMS] drm report modesetting isn't supported.
[    17.216] (II) [KMS] drm report modesetting isn't supported.
[    17.216] (II) [KMS] drm report modesetting isn't supported.
[    17.216] (II) [KMS] drm report modesetting isn't supported.
[    17.216] (WW) Falling back to old probe method for modesetting
[    17.216] (WW) Falling back to old probe method for fbdev
[    17.216] (II) Loading sub module "fbdevhw"
[    17.216] (II) LoadModule: "fbdevhw"
[    17.216] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.477] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.477]     compiled for 1.13.0, module version = 0.0.2
[    17.477]     ABI class: X.Org Video Driver, version 13.0
[    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"
[    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"
[    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"
[    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"
[    17.477] (II) Loading sub module "vbe"
[    17.477] (II) LoadModule: "vbe"
[    17.477] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    17.480] (II) Module vbe: vendor="X.Org Foundation"
[    17.480]     compiled for 1.13.0, module version = 1.1.0
[    17.480]     ABI class: X.Org Video Driver, version 13.0
[    17.480] (II) Loading sub module "int10"
[    17.480] (II) LoadModule: "int10"
[    17.481] (II) Loading /usr/lib/xorg/modules/libint10.so
[    17.586] (II) Module int10: vendor="X.Org Foundation"
[    17.586]     compiled for 1.13.0, module version = 1.0.0
[    17.586]     ABI class: X.Org Video Driver, version 13.0
[    17.586] (II) VESA(0): initializing int10
[    17.586] (EE) VESA(0): Cannot read V_BIOS (3) Input/output error
[    17.586] (II) UnloadModule: "vesa"
[    17.586] (II) UnloadSubModule: "int10"
[    17.586] (II) Unloading int10
[    17.586] (II) UnloadSubModule: "vbe"
[    17.586] (II) Unloading vbe
[    17.586] (II) UnloadModule: "radeon"
[    17.586] (EE) Screen(s) found, but none have a usable configuration.
[    17.586] 
Fatal server error:
[    17.586] no screens found
[    17.586] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    17.586] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    17.587] (EE) 
[    17.589] Server terminated with error (1). Closing log file.

---

### Post by Bashing-om on 2013-01-25
E411; Shucks, Amongst other things, the log tells us can not find a driver for the graphics card.

What I do not understand is why the kernel is attempting to set "modesetting" when the kernel command line option directed it not to. Maybe the kernel no longer supports that option (radeon.modeset=0) ?? Let's try a more generic form. Insert the term "nomodeset" instead, and see what results.

Look'n like we are going to have to go toAMD/ ATI (which is radeon) website and see if a driver exist to support 'buntu. Thus far I have found nothing about the HD6625M card. This is the easiest method I am aware of:
While you are booted up on a LiveCD... If you go to ATI:
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
And use "autodetect" when you are looking for a Linux Driver, what does say about your chipset and any suggested driver?

Might also be of interest at this time to look at the .xsessions-errors file in your home directory (the leading "." designates a hiiden file -> ctl+h to unhide the hidden files)

Any other thoughts are welcome.

---

### Post by black veils on 2013-01-25
**Bashing-om**:
remember it works in live mode, just not once installed. is there some way to replicate those configurations?

---

### Post by Bashing-om on 2013-01-25
black veils & E411 ;

I am far from an expert, or highly knowledgeable. The live environment uses a different structure and driver resources than that of the actual install (virtual). I can not cross relate what is going on in ram within the liveCD world and in the install with what really happens in the kernel to match a driver to the specific hardware.

Believe me, I look forward to any learning experience -> presently I am engrossed with the initramfs process. I know the big picture but little of the details. As I have the time and ability to focus I am gaining greater insight.

Problem at hand - as I perceive it - load a driver for this "perhaps" cutting edge graphics card, Can not boot to a GUI, so must use assets available from the command line. Nor am I in favor of blindly installing drivers.

Presently need info in respect to this card to identify the proper driver. Then comes the process to get it installed. AMD help ???

[INDENT]at this point, I know not - what else to do
[/INDENT]

---

### Post by E411 on 2013-01-26
> **Bashing-om said:**
> 

While you are booted up on a LiveCD... If you go to ATI:
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
And use "autodetect" when you are looking for a Linux Driver, what does say about your chipset and any suggested driver?.

from the live session, using autodetect leads me to download an exe file (amddriverdownloader.exe). If I select my material and my system manually (linux 64 bit then) it suggests me to download amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip

> **Bashing-om said:**
> 
Might also be of interest at this time to look at the .xsessions-errors file in your home directory (the leading "." designates a hiiden file -> ctl+h to unhide the hidden files)



I guess you mean the home folder when I boot on the hard drive and not on the usb stick. Then there is no .xsessions-errors file in my home folder. I looked on the entire disk and could only find an xsessions folder located in /media/ubuntu/1d908588-c022-47c3-af8f-106b7e5b7aa1/usr/share 

Here is all I can find in my home folder:  .bash_history .bash_logout .bashrc .profile .Xauthority

Will now boot with nomodeset and come back soon with the output...

Edit: the only difference between "radeon.modeset=0" and "nomodeset" is that I got stuck on tty7 without being redirected to tty1

---

### Post by bogan on 2013-01-26
Hi!, **E411,**

If you get to a TTY [ Ctrl+Alt+F1] and run: ```
sudo service lightdm stop
startx
```What error messages do you get?

Afterwards, re-check for an .xsession-errors file in your /home/username folder. There should be one and more than 15 other .files, including an ' .xsession-errors.old ' file.

When you Post commands and output - especially long ones, -  please highlight the text in the New Reply edit box, and press the '#' icon in the top toolbar, to make it easier to read in a Code box.

Edit: Have you tried other boot options, such as 'xforcevesa' , 'acpi=off' , 'acpi_osi=linux', or 'vmalloc=192MB' etc etc.

Chao!, **bogan**.

---

### Post by Bashing-om on 2013-01-26
E411 - bogan;

Pleased that bogan continues an interest.

It is good to have confirmation that a driver does exist (found two instances of this card working in ubuntu --but on desk tops). Doing the install from AMD is imho the last resort; I much prefer to stay in the ubuntu community (open source drivers are outstanding - I am running radeon on this box,open source driver, absolutely wonderful).

Bogan brings up a good point, lap tops can be finaky. Try the other options presented in the install's boot options (that is: shift key after bios screen clears->boot options screen-> f6 key for boot parameters to add to the command line-> f10 to continue to boot with the selected option/options). 

What I desire is to get some kind of GUI desktop up and activate "Additional Drivers" to have ubuntu find and install the appropriate driver. Failing that approach is command line to install a driver, lastly is going to AMD and doing the manual process. 

By the way, as a vote of confidence, bogan has become the resident "expert" on graphics drivers.

[INDENT]hang'n in there

[/INDENT]

---

### Post by bogan on 2013-01-26
Hi!,** Bashing_om**,> By the way, as a vote of confidence, bogan has become the resident "expert" on graphics drivers.Thanks for the vote of confidence, but I have to disclaim it.

The old saying is that an "expert" is one who learns more & more about less and less.

My "expertise" is due to having had many problems myself, and a lot of help  in these Forums.,   especially from MAFoElffen, who is much missed . 

Mostly it is limited to Nvidia.  About Bumblebee and ATI/AMD, in detail, and in practice, I know very little.

At least I have not yet reached the stage of knowing everything about nothing.

Chao!, **bogan**.

---

### Post by Bashing-om on 2013-01-26
@bogan

I have been aware of your presence on this forum for some time//you gained a lot in my eyes when you took over  from MAFoElffen; whence you particularly came to notice. I have followed your posts advisements and the confidence - in my humblest of opinions - is well founded.

I followed your tales of trials and tribulations as mostly related in the MAFoElffen sticky with interest and appreciation of your troubleshooting abilities and the knowledge you gained. That ability you now share with all of us.

[INDENT][INDENT]'nuff said

[/INDENT][/INDENT]

---

### Post by E411 on 2013-01-26
> **bogan said:**
> 



When you Post commands and output - especially long ones, -  please highlight the text in the New Reply edit box, and press the '#' icon in the top toolbar, to make it easier to read in a Code box.

Will do, sorry.

> **bogan said:**
> 
If you get to a TTY [ Ctrl+Alt+F1] and run: ```
sudo service lightdm stop
startx
```What error messages do you get?

Afterwards, re-check for an .xsession-errors file in your /home/username  folder. There should be one and more than 15 other .files, including an  ' .xsession-errors.old ' file.

with sudo service lightdm stop

```
stop: Unknown instance
```

We already had this earlier in the discussion, so I tried 
setsid unity

```
WARNING: no DISPLAY variable set, setting it to :0
```
tty1 hangs

startx

I get the log file I posted earlier, with
```
fatal server error:
no screens found
```

still no .xsession-errors file 



> **bogan said:**
> 
Edit: Have you tried other boot options, such as 'xforcevesa' , 'acpi=off' , 'acpi_osi=linux', or 'vmalloc=192MB' etc etc.



will try that now. Just as the "nomodeset" command, before "quiet splash"?

---

### Post by E411 on 2013-01-26
> **Bashing-om said:**
> 

Pleased that bogan continues an interest.



So am I. Thank you guys!

---

### Post by Bashing-om on 2013-01-26
E411;
Additional boot options:
liveCD Shift key depressed language screen, escape to accept the default, f6 key for a list of a few options/ Write them down, Boot the install to the grub menu and insert the boot option into the kernel boot line(as before with nomodset). The following link is overwhelming,but worth being aware of, there are hundreds of "boot options":
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
[http://https://help.ubuntu.com/community/BootOptions](http://https://help.ubuntu.com/community/BootOptions)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

It's a wonderful operating system.
[INDENT][INDENT]are we there yet ?

[/INDENT][/INDENT]

---

### Post by bogan on 2013-01-26
Hi!, **E411**,

You Posted:> with```
sudo service lightdm stop
stop: Unknown instance 
```We already had this earlier in the discussion, so I tried 
```
setsid unity
```startx
I get the log file I posted earlier, with```
  fatal server error: no screens found 
```still no .xsession-errors fileI expected the "stop: unknown instance" that was just to ensure the Xorg was closed.
Surely, when you run 'startx', after that you get a whole screen full of text, ending with Fatal Error; but before that, you should have had some more detailed error messages, which would indicate the source - that is what I was after.

From your reports, it looks to me as though the Xserver is not even trying to set itself up.
In that position I would try [ from a tty,  after running Update Manager if it is possible ] : ```
sudo apt-get update
sudo service lightdm stop
sudo apt-get install --reinstall xserver-xorg-core # reboot after each of:
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get install --reinstall xserver-xorg-video-radeon
```The problem is that there are dozens - literally, have a look in Synaptic - of 'xserver-xorg-xxxx' packages, and I do not know which others might be involved.

[ That assumes it is nouveau or the radeon driver you are using, not the fglrx one. ]
[B]
Chao!, [/B]bogan.

---

### Post by E411 on 2013-01-27
> **bogan said:**
> 
```
sudo apt-get update
sudo service lightdm stop
sudo apt-get install --reinstall xserver-xorg-core # reboot after each of:
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get install --reinstall xserver-xorg-video-radeon
```

no improvement whatsoever :cry:

---

### Post by bogan on 2013-01-27
Hi!, **E411** & **Bashing_om**,

I have just re-read all the Posts in this thread and there are several points that are a total mystery, contrary to anything I have encountered or read about.

The one that seems most likely to be important is that when you ran: 'sudo lshw  -C display' it showed: "Configuration: latency=0".[ in french ]

Whereas it should have shown the driver in use. eg "configuration: driver=nouveau latency=0" [ probably 'radeon' rather than 'nouveau' ].

Whilst 'lspci -nnk | grep -iA3 vga' showed the driver as' radeon'.

Since then, I think, you have re installed with the proprietary drivers option activated.

Please run those two commands again:
First, as is.
Second, booted from the LiveCd/Usb.
Third, if you can spare the time, after reinstalling without the proprietary drivers option activated.

The second point is the implication that when you run 'startx' you only get an Xorg Fatal Error=1, with no additional info on the screen, coupled with the absence of an .xsession-errors file. It usually gives half a screenful of messages, including a reference to the log file and suggesting contacting the Xorg organisation, as well as backlisting the assumed source of the fault. It would ease my bewilderment if you could Post the whole screen after 'sudo service lightdm stop' & startx'.

In the absence of those details, I can only suggest a systematic search for 'ERROR' and 'WARNING', 'Xorg' and 'xserver', or 'FATAL', in the various /var/ log/ files and dmesg.

A third point, reverting to the OP, apparently the fault was first apparent whilst actually running a video. When you boot from the LiveCD/Usb, can you still run videos ??

There are other points, but that will do for now, just one more question:

Have you had any 'System Fault' messages related to 'dbus' ?? I have had a lot, but they never seem to cause problems, whereas your first error message concerned a dbus fault.

Chao!, **bogan.**

---

### Post by E411 on 2013-01-27
> **bogan said:**
> 

I have just re-read all the Posts 

I definitely appreciate your commitment.

> **bogan said:**
> 
Please run those two commands again:
First, as is.
Second, booted from the LiveCd/Usb.


As is:

```
description: VGA compatible controller
produit: Whistler LE [AMD Radeon HD 6625M Graphics]
fabriquant: Advanced Micro Devices [AMD] nee ATI
identifiant matériel: 0
information bus: pci@0000:01:00.0
version: 00
bits: 64 bits
horloge: 33MHZ
fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list
configuration: latency=0
ressources: mémoire:b0000000-bfffffff mémoire:c20000000-c201ffff portE/S:4000(taille=256) mémoire:c2040000-c205ffff 			 		
```

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD]  nee ATI Whistler LE [AMD Radeon HD 6625M Graphics] [1002:6742]
Subsystem: Toshiba America Info Systems Device [1179:fb31]
Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series] [1002:aa90]
```

from the live usb:

```
description: VGA compatible controller
product: Whistler LE [AMD Radeon HD 6625M Graphics]
vendor: Advanced Micro Devices [AMD] nee ATI
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHZ
capabilities: pm pciexpress msi vga_controller bus_master cap_list
configuration: driver=radeon latency=0
resources: irq:44 memory:b0000000-bfffffff memory:c20000000-c201ffff ioport:4000(size=256) memory:c2040000-c205ffff 			 		
```

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD]  nee ATI Whistler LE [AMD Radeon HD 6625M Graphics] [1002:6742]
Subsystem: Toshiba America Info Systems Device [1179:fb31]
Kernel driver in use: radeon
Kernel modules: radeon

```

> **bogan said:**
>  It would ease my bewilderment if you could Post the whole screen after 'sudo service lightdm stop' & startx'.

I will but please give me some time, atm I have lots of difficulties to access grub (hence to boot) because holding the shift key (or F8) only works once in a while.

---

### Post by bogan on 2013-01-27
Hi!,** E411**,

Good, that c[ears one query. The Liveusb has and uses the radeon driver, whereas the installed OS has the radeon driver, but is not using it, and apparently is not using a driver at all- hence no xserver.

Chao!, **bogan**.

---

### Post by Bashing-om on 2013-01-27
E411 - bogan;

> atm I have lots of difficulties to access grub (hence to boot) because holding the shift key (or F8) only works once in a while.Adds to credence that the install is corrupted. Too many things are not adding up.
grub access, initramfs errors, xserver not reading EDID data, can not find or load a graphics driver, French language.

E411; Has the .iso been verified ? :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Has the installer's file system integrity been checked ? :
liveCD ->shift key->language screen ->escape key -> boot screen -> check disk integrity option.
[INDENT][INDENT]are we beating a dead horse ?

[/INDENT][/INDENT]

---

### Post by E411 on 2013-01-27
> **bogan said:**
> 

  It would ease my bewilderment if you could Post the whole screen after 'sudo service lightdm stop' & startx'.



sudo service lightdm stop

```
stop: Unknown instance:
```

startx

The whole screen I get as an output of the "startx" command is the  is the log file that I posted [here]("http://ubuntuforums.org/showpost.php?p=12473224&postcount=22") ( /var/log/Xorg.0.log). Do you want me to post it again? I double checked and it is exactly the same (except for the numbers between [ ])

---

### Post by E411 on 2013-01-28
> **Bashing-om said:**
> 

E411; Has the .iso been verified ? :


did so, it's ok

I forgot to mention that the two only ways to access a terminal while booting on the HD are with the boot options

nomodeset and radeon.modeset=0

in all other cases, black screen and no way to switch to a usable tty

edit: and "pci=off" gives me a clean boot with Busy box

---

### Post by E411 on 2013-01-28
> **bogan said:**
> d.


Have you had any 'System Fault' messages related to 'dbus' ?? I have had a lot, but they never seem to cause problems, whereas your first error message concerned a dbus fault.



where should I look for those messages?

---

### Post by E411 on 2013-01-28
I compared the Xorg.0.log file in the live version and the one on my system

The first difference is

```
[    17.216] (II) [KMS] drm report modesetting isn't supported.
```

while on the live version it says

```
[KMS] Kernel modesetting enabled
```

then a few lines below

```
[    17.477] (EE) Screen 0 deleted because of no matching config section.
[    17.477] (II) UnloadModule: "radeon"
```

while on the live version 

```
(II) RADEON(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
```

and the Radeon info goes on

How comes modesetting is not supported on the installed system while it is enabled on the live one?

---

### Post by E411 on 2013-01-28
I found this page: [http://www.x.org/wiki/radeonBuildHowTo#Missing_firmware](http://www.x.org/wiki/radeonBuildHowTo#Missing_firmware)

> **Missing firmware**

 This is not a KMS problem, but people often report X does *not* start (thus it's included in the troubleshooting list). The real cause for this is the drm cannot find a missing radeon firmware (or microcode). This depends on the Linux-kernel version you use. To fix this issue simply install the package containing the radeon firmware files or consult your distribution's support. 

could this apply to me?

---

### Post by furything on 2013-01-28
Hi All
Just a fresh pair of eyes and may be totally down the wrong avenue but
I note that the os was reinstalled.

I have found that unless you obliterate a previous install e.g. use a live cd/usb and delete the entire content from the hard disk and then install from scratch onto new blank partition, the install does not overwrite everything but uses the previous linux install  (has to be the exact same version - this happened to me was with I think version 11.04 - could be 10.10 or 11.10).

For example things like smb.conf, squid.conf remain the previously manually edited version rather then the package version.

What you are describing (and has now been alluded to) is a damaged albeit reinstalled version.

When you did the reinstall did you ensure the old install was blown away???
Also did you install as is - that is no download updates from the internet during install?
If the live usb works it should just install the same working image unless auto updates during install were applied or you overwrote the previous install without destroying it first.

Sorry if I am butting in and on wrong tangent but as I said this is similar to my issue which was caused by swapping an ati card for nvidia. I tried a reinstall only to find it still wanted to load ati and not nVidia.

---

### Post by E411 on 2013-01-28
Hi furything,

this is good to know because it was a big mystery to me why the first install was working in the beginning, then crashed, then the second install was behaving like the first one after it crashed.

I didn't remove anything, I used the same usb stick and went through the same steps as the first time thinking that everything would then be deleted.

And yes, I think that I allowed internet uploads during install.

---

### Post by furything on 2013-01-28
In that case I suggest you use live usb and clean up the hard drive (after backing user files from /home/your user/ - sub-directories)

Once clean - reinstall but don't allow updates (suggest turn off wifi).

Hopefully you get a good clean install and everything is normal. From there try and update packages and make sure all ok before you start doing more video streaming.

At worst case you end up the same as now and bogan hopefully will be able to sort it out.

I also suggest if you have an external hard drive, use something like clonezilla and take an image of your system in a  working state. If the usb pen drive is large enough you could put an image on that.

If you reinstall - let me know how you get on.

---

### Post by E411 on 2013-01-28
omg, did as you said and the computer is now booting as expected with the graphical interface

---

### Post by black veils on 2013-01-28
> **E411 said:**
> omg, did as you said and the computer is now booting as expected with the graphical interface

dont do any updates yet is all i can say, or avoid xorg updates and any obvious driver stuff.. which means avoid kernel, until you can figure out what is causing the problem.

---

### Post by E411 on 2013-01-28
> **black veils said:**
> dont do any updates yet is all i can say, or avoid xorg updates and any obvious driver stuff.. which means avoid kernel, until you can figure out what is causing the problem.

ok. software updater is suggesting 257 updates though :D

---

### Post by furything on 2013-01-28
:cool: E411 glad to see it worked.

As I said a clean wipe down is the only way to ensure no corruption is left behind.

I know this is the case with same version don't know what would happen if you had a corrupt 12.04 and then did an over install with 12.10. It might result in the same corrupted os but if anyone reads these posts would be interested if you have done just that and what the outcome was?

---

### Post by black veils on 2013-01-28
if you go into software sources, and on the updates tab, just make sure important is checked, not the other updates. this will lessen the mount.

now if you are going to do updates, look through them all and avoid kernel, xorg and anything that looks graphics related.

---

### Post by E411 on 2013-02-19
It seems that I reinstalled the problematic package as the initial problem is back.

Unfortunately  the computer wasn't recently rebooted so that I cant' be sure of when the  faulty package came into play. However, I tried to minimize the software  updates (although in the last days I updated quite a lot of them).

Here is the history log for apt:

```
Start-Date: 2013-02-13  13:25:00
Commandline: aptdaemon role='role-commit-packages' sender=':1.1093'
Install: linux-image-extra-3.5.0-23-generic:amd64 (3.5.0-23.35), linux-image-3.5.0-23-generic:amd64 (3.5.0-23.35), linux-signed-image-3.5.0-23-generic:amd64 (3.5.0-23.35), linux-headers-3.5.0-23-generic:amd64 (3.5.0-23.35), linux-headers-3.5.0-23:amd64 (3.5.0-23.35)
Upgrade: python3-gi:amd64 (3.4.0-1, 3.4.0-1ubuntu0.1), libreoffice-presentation-minimizer:amd64 (1.0.4+LibO3.6.2~rc2-0ubuntu3, 1.0.4+LibO3.6.2~rc2-0ubuntu4), apt-transport-https:amd64 (0.9.7.5ubuntu5, 0.9.7.5ubuntu5.2), libreoffice-gnome:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), udisks2:amd64 (2.0.0-1, 2.0.0-1ubuntu1), unity:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.2), libreoffice-draw:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libreoffice-help-en-us:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libjavascriptcoregtk-3.0-0:amd64 (1.10.0-0ubuntu1, 1.10.0-0ubuntu1.1), gedit-common:amd64 (3.6.0-0ubuntu1, 3.6.1-0ubuntu1), telepathy-logger:amd64 (0.4.0-1, 0.4.0-2~ubuntu12.10.0), gir1.2-rb-3.0:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), vim-common:amd64 (7.3.547-4ubuntu1, 7.3.547-4ubuntu1.1), base-files:amd64 (6.5ubuntu11, 6.5ubuntu12), gnome-mahjongg:amd64 (3.6.0.2-0ubuntu1, 3.6.0.2-0ubuntu1.2), libcupsppdc1:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), nautilus:amd64 (3.5.90.really.3.4.2-0ubuntu4, 3.5.90.really.3.4.2-0ubuntu4.1), libcompizconfig0:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), compiz-plugins-default:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), bind9-host:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), libatspi2.0-0:amd64 (2.6.0-0ubuntu1, 2.6.1-0ubuntu0.1), libebackend-1.2-5:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), libreoffice-style-tango:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libcupsimage2:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), gnome-session-bin:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu1.1), appmenu-gtk:amd64 (12.10.2-0ubuntu1, 12.10.2-0ubuntu1.3), rhythmbox-data:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), libcupscgi1:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), libreoffice-impress:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), poppler-utils:amd64 (0.20.4-0ubuntu1, 0.20.4-0ubuntu1.1), libglib2.0-data:amd64 (2.34.0-1ubuntu1, 2.34.1-1ubuntu1), at-spi2-core:amd64 (2.6.0-0ubuntu1, 2.6.1-0ubuntu0.1), python3.2-minimal:amd64 (3.2.3-6ubuntu3, 3.2.3-6ubuntu3.1), dconf-gsettings-backend:amd64 (0.14.0-0ubuntu2, 0.14.1-0ubuntu0.1), libcairo-gobject2:amd64 (1.12.2-1ubuntu2, 1.12.2-1ubuntu2.2), gnome-system-log:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu1.1), totem-plugins:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), memtest86+:amd64 (4.20-1.1ubuntu2, 4.20-1.1ubuntu2.1), activity-log-manager-control-center:amd64 (0.9.4-0ubuntu4, 0.9.4-0ubuntu4.2), dnsutils:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), libgpod-common:amd64 (0.8.2-6build1, 0.8.2-6ubuntu1), gstreamer0.10-alsa:amd64 (0.10.36-1ubuntu1, 0.10.36-1ubuntu1.1), fonts-opensymbol:amd64 (102.2+LibO3.6.2~rc2-0ubuntu3, 102.2+LibO3.6.2~rc2-0ubuntu4), bamfdaemon:amd64 (0.3.2-0ubuntu1, 0.3.4-0ubuntu1), libimobiledevice3:amd64 (1.1.4-1ubuntu2, 1.1.4-1ubuntu3), gnome-settings-daemon:amd64 (3.4.2-0ubuntu14, 3.4.2-0ubuntu15), perl:amd64 (5.14.2-13, 5.14.2-13ubuntu0.1), libcupsfilters1:amd64 (1.0.24-2, 1.0.24-2ubuntu0.1), thunderbird:amd64 (16.0.1+build1-0ubuntu1, 17.0.2+build1-0ubuntu0.12.10.1), rhythmbox:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), python3-distupgrade:amd64 (0.190.1, 0.190.5), gedit:amd64 (3.6.0-0ubuntu1, 3.6.1-0ubuntu1), libtelepathy-logger2:amd64 (0.4.0-1, 0.4.0-2~ubuntu12.10.0), unity-common:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.2), libpython3.2:amd64 (3.2.3-6ubuntu3, 3.2.3-6ubuntu3.1), gstreamer0.10-plugins-base-apps:amd64 (0.10.36-1ubuntu1, 0.10.36-1ubuntu1.1), libdee-1.0-4:amd64 (1.0.14-0ubuntu1, 1.0.14-0ubuntu1.1), gnome-session:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu1.1), python3-gi-cairo:amd64 (3.4.0-1, 3.4.0-1ubuntu0.1), linux-generic:amd64 (3.5.0.17.19, 3.5.0.23.29), gnome-session-common:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu1.1), firefox-globalmenu:amd64 (16.0.1+build1-0ubuntu1, 18.0.2+build1-0ubuntu0.12.10.1), rhythmbox-plugin-magnatune:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), libunity-webapps0:amd64 (2.4.1-0ubuntu2, 2.4.1-0ubuntu3.2), gnome-sudoku:amd64 (3.6.0.2-0ubuntu1, 3.6.0.2-0ubuntu1.2), libdns81:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), libufe-xidgetter0:amd64 (2.3.5-0ubuntu1, 2.4.1-0ubuntu1.2), seahorse:amd64 (3.6.0-0ubuntu1, 3.6.2-0ubuntu1), perl-base:amd64 (5.14.2-13, 5.14.2-13ubuntu0.1), libcairo2:amd64 (1.12.2-1ubuntu2, 1.12.2-1ubuntu2.2), perl-modules:amd64 (5.14.2-13, 5.14.2-13ubuntu0.1), gnome-keyring:amd64 (3.6.0-0ubuntu1, 3.6.1-0ubuntu1), xul-ext-unity:amd64 (2.3.5-0ubuntu1, 2.4.1-0ubuntu1.2), librhythmbox-core6:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), libtotem0:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), software-center:amd64 (5.4.1.2, 5.4.1.4), libapt-inst1.5:amd64 (0.9.7.5ubuntu5, 0.9.7.5ubuntu5.2), libgpod4:amd64 (0.8.2-6build1, 0.8.2-6ubuntu1), libboost-date-time1.49.0:amd64 (1.49.0-3.1ubuntu1, 1.49.0-3.1ubuntu1.1), libedata-book-1.2-15:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), python3.2:amd64 (3.2.3-6ubuntu3, 3.2.3-6ubuntu3.1), ubuntu-release-upgrader-gtk:amd64 (0.190.1, 0.190.5), libfontembed1:amd64 (1.0.24-2, 1.0.24-2ubuntu0.1), libwebkitgtk-3.0-0:amd64 (1.10.0-0ubuntu1, 1.10.0-0ubuntu1.1), libisccc80:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), cups-ppdc:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), libreoffice-math:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), apt-utils:amd64 (0.9.7.5ubuntu5, 0.9.7.5ubuntu5.2), libedata-cal-1.2-18:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), shotwell:amd64 (0.13.0-0ubuntu3, 0.13.1-0ubuntu1), duplicity:amd64 (0.6.19-0ubuntu2, 0.6.19-0ubuntu2.2), vim-tiny:amd64 (7.3.547-4ubuntu1, 7.3.547-4ubuntu1.1), update-manager:amd64 (0.174.3, 0.174.4), update-manager-core:amd64 (0.174.3, 0.174.4), gir1.2-totem-1.0:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), deja-dup:amd64 (24.0-0ubuntu1, 24.0-0ubuntu2), python3-update-manager:amd64 (0.174.3, 0.174.4), linux-signed-generic:amd64 (3.5.0.17.19, 3.5.0.23.29), libreoffice-gtk:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libreoffice-common:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), python3-problem-report:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10), coreutils:amd64 (8.13-3.2ubuntu2, 8.13-3.2ubuntu2.1), python-gi:amd64 (3.4.0-1, 3.4.0-1ubuntu0.1), app-install-data-partner:amd64 (12.12.10, 12.12.10.1), libgtk-3-bin:amd64 (3.6.0-0ubuntu3, 3.6.0-0ubuntu3.2), gnome-orca:amd64 (3.7.0.93-0ubuntu1, 3.7.0.94-0ubuntu0.1), apt:amd64 (0.9.7.5ubuntu5, 0.9.7.5ubuntu5.2), firefox:amd64 (16.0.1+build1-0ubuntu1, 18.0.2+build1-0ubuntu0.12.10.1), cups-common:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), uno-libs3:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), liblwres80:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), gir1.2-unity-5.0:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.1), libnux-3.0-0:amd64 (3.8.0-0ubuntu1, 3.10.0-0ubuntu1), python3-dbus:amd64 (1.1.1-1, 1.1.1-1ubuntu0.1), unity-lens-photos:amd64 (0.8-0ubuntu1, 0.9-0ubuntu1), python-uno:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libgtk-3-0:amd64 (3.6.0-0ubuntu3, 3.6.0-0ubuntu3.2), python-problem-report:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10), appmenu-gtk3:amd64 (12.10.2-0ubuntu1, 12.10.2-0ubuntu1.3), libunity-protocol-private0:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.1), python-dbus-dev:amd64 (1.1.1-1, 1.1.1-1ubuntu0.1), libedataserver-1.2-17:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), libsecret-common:amd64 (0.10-0ubuntu1, 0.11-0ubuntu0.12.10.1), gir1.2-gst-plugins-base-0.10:amd64 (0.10.36-1ubuntu1, 0.10.36-1ubuntu1.1), libebook-1.2-14:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), compiz-gnome:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), gir1.2-atspi-2.0:amd64 (2.6.0-0ubuntu1, 2.6.1-0ubuntu0.1), linux-headers-generic:amd64 (3.5.0.17.19, 3.5.0.23.29), vino:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu1.1), python-dbus:amd64 (1.1.1-1, 1.1.1-1ubuntu0.1), libgail-3-0:amd64 (3.6.0-0ubuntu3, 3.6.0-0ubuntu3.2), libreoffice-pdfimport:amd64 (1.0.6+LibO3.6.2~rc2-0ubuntu3, 1.0.6+LibO3.6.2~rc2-0ubuntu4), libbind9-80:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), linux-image-generic:amd64 (3.5.0.17.19, 3.5.0.23.29), libpoppler-glib8:amd64 (0.20.4-0ubuntu1, 0.20.4-0ubuntu1.1), libapt-pkg4.12:amd64 (0.9.7.5ubuntu5, 0.9.7.5ubuntu5.2), libcamel-1.2-40:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), python-gi-cairo:amd64 (3.4.0-1, 3.4.0-1ubuntu0.1), firefox-locale-en:amd64 (16.0.1+build1-0ubuntu1, 18.0.2+build1-0ubuntu0.12.10.1), flashplugin-installer:amd64 (11.2.202.261ubuntu0.12.10.1, 11.2.202.262ubuntu0.12.10.1), isc-dhcp-client:amd64 (4.2.4-1ubuntu10, 4.2.4-1ubuntu10.1), im-switch:amd64 (1.22ubuntu2, 1.22ubuntu2.1), rhythmbox-mozilla:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), libecal-1.2-15:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), libgeis1:amd64 (2.2.12-0ubuntu2, 2.2.12-0ubuntu3), indicator-appmenu:amd64 (12.10.3-0ubuntu1, 12.10.3-0ubuntu2.1), lsb-base:amd64 (4.0-0ubuntu26, 4.0-0ubuntu26.1), unity-services:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.2), nautilus-data:amd64 (3.5.90.really.3.4.2-0ubuntu4, 3.5.90.really.3.4.2-0ubuntu4.1), xul-ext-ubufox:amd64 (2.4.1-0ubuntu1, 2.6-0ubuntu0.12.10.1), libreoffice-style-human:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libwhoopsie0:amd64 (0.2.5, 0.2.7.1), gstreamer0.10-x:amd64 (0.10.36-1ubuntu1, 0.10.36-1ubuntu1.1), ufw:amd64 (0.33-0ubuntu2, 0.33-0ubuntu2.1), libdconf1:amd64 (0.14.0-0ubuntu2, 0.14.1-0ubuntu0.1), unity-greeter:amd64 (12.10.4-0ubuntu5, 12.10.4-0ubuntu5.1), ure:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), python-gobject:amd64 (3.4.0-1, 3.4.0-1ubuntu0.1), libdecoration0:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), libreoffice-base-core:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libperl5.14:amd64 (5.14.2-13, 5.14.2-13ubuntu0.1), libreoffice-ogltrans:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), unity-webapps-service:amd64 (2.4.1-0ubuntu2, 2.4.1-0ubuntu3.2), rhythmbox-plugin-zeitgeist:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), gnome-screensaver:amd64 (3.6.0-0ubuntu1, 3.6.0-0ubuntu2.1), libisccfg82:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), whoopsie:amd64 (0.2.5, 0.2.7.1), brasero-cdrkit:amd64 (3.4.1-0ubuntu2, 3.4.1-0ubuntu3), indicator-datetime:amd64 (12.10.2-0ubuntu3, 12.10.2-0ubuntu3.1), gpgv:amd64 (1.4.11-3ubuntu4, 1.4.11-3ubuntu4.1), brasero-common:amd64 (3.4.1-0ubuntu2, 3.4.1-0ubuntu3), busybox-static:amd64 (1.19.3-7ubuntu1, 1.19.3-7ubuntu1.1), libreoffice-calc:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), thunderbird-globalmenu:amd64 (16.0.1+build1-0ubuntu1, 17.0.2+build1-0ubuntu0.12.10.1), thunderbird-gnome-support:amd64 (16.0.1+build1-0ubuntu1, 17.0.2+build1-0ubuntu0.12.10.1), ubuntu-drivers-common:amd64 (0.2.71, 0.2.71.1), python3-apport:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10), evolution-data-server-common:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), gnome-games-data:amd64 (3.6.0.2-0ubuntu1, 3.6.0.2-0ubuntu1.2), libsecret-1-0:amd64 (0.10-0ubuntu1, 0.11-0ubuntu0.12.10.1), libudisks2-0:amd64 (2.0.0-1, 2.0.0-1ubuntu1), python-apport:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10), gir1.2-dee-1.0:amd64 (1.0.14-0ubuntu1, 1.0.14-0ubuntu1.1), evolution-data-server:amd64 (3.6.0-0ubuntu2, 3.6.2-0ubuntu0.1), busybox-initramfs:amd64 (1.19.3-7ubuntu1, 1.19.3-7ubuntu1.1), brasero:amd64 (3.4.1-0ubuntu2, 3.4.1-0ubuntu3), libreoffice-emailmerge:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), gir1.2-webkit-3.0:amd64 (1.10.0-0ubuntu1, 1.10.0-0ubuntu1.1), linux-libc-dev:amd64 (3.5.0-17.28, 3.5.0-23.35), libunity-core-6.0-5:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.2), isc-dhcp-common:amd64 (4.2.4-1ubuntu10, 4.2.4-1ubuntu10.1), libcupsmime1:amd64 (1.6.1-0ubuntu11, 1.6.1-0ubuntu11.3), libisc83:amd64 (9.8.1.dfsg.P1-4.2ubuntu3, 9.8.1.dfsg.P1-4.2ubuntu3.1), unity-lens-applications:amd64 (6.8.0-0ubuntu1, 6.10.0-0ubuntu1), compiz-core:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), totem:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), mountall:amd64 (2.42, 2.42ubuntu0.4), linux-signed-image-generic:amd64 (3.5.0.17.19, 3.5.0.23.29), remote-login-service:amd64 (1.0.0-0ubuntu1, 1.0.0-0ubuntu1.1), libssh-4:amd64 (0.5.2-1build1, 0.5.2-1ubuntu0.12.10.2), totem-mozilla:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), lintian:amd64 (2.5.10.2ubuntu2, 2.5.10.2ubuntu2.1), dconf-service:amd64 (0.14.0-0ubuntu2, 0.14.1-0ubuntu0.1), libreoffice-presenter-console:amd64 (1.1.1+LibO3.6.2~rc2-0ubuntu3, 1.1.1+LibO3.6.2~rc2-0ubuntu4), rhythmbox-plugin-cdrecorder:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), rhythmbox-plugins:amd64 (2.97-1ubuntu5, 2.97-1ubuntu6.1), libnautilus-extension1a:amd64 (3.5.90.really.3.4.2-0ubuntu4, 3.5.90.really.3.4.2-0ubuntu4.1), libpam-gnome-keyring:amd64 (3.6.0-0ubuntu1, 3.6.1-0ubuntu1), cups-filters:amd64 (1.0.24-2, 1.0.24-2ubuntu0.1), libbamf3-0:amd64 (0.3.2-0ubuntu1, 0.3.4-0ubuntu1), ubuntu-release-upgrader-core:amd64 (0.190.1, 0.190.5), libgtk-3-common:amd64 (3.6.0-0ubuntu3, 3.6.0-0ubuntu3.2), gstreamer0.10-plugins-base:amd64 (0.10.36-1ubuntu1, 0.10.36-1ubuntu1.1), totem-common:amd64 (3.4.3-0ubuntu4, 3.4.3-0ubuntu5), libpoppler28:amd64 (0.20.4-0ubuntu1, 0.20.4-0ubuntu1.1), lsb-release:amd64 (4.0-0ubuntu26, 4.0-0ubuntu26.1), dconf-tools:amd64 (0.14.0-0ubuntu2, 0.14.1-0ubuntu0.1), libwebkitgtk-3.0-common:amd64 (1.10.0-0ubuntu1, 1.10.0-0ubuntu1.1), adium-theme-ubuntu:amd64 (0.3.2-0ubuntu1, 0.3.3-0ubuntu0.1), activity-log-manager-common:amd64 (0.9.4-0ubuntu4, 0.9.4-0ubuntu4.2), libnux-3.0-common:amd64 (3.8.0-0ubuntu1, 3.10.0-0ubuntu1), firefox-gnome-support:amd64 (16.0.1+build1-0ubuntu1, 18.0.2+build1-0ubuntu0.12.10.1), libbrasero-media3-1:amd64 (3.4.1-0ubuntu2, 3.4.1-0ubuntu3), python-libxml2:amd64 (2.8.0+dfsg1-5ubuntu2, 2.8.0+dfsg1-5ubuntu2.1), gir1.2-javascriptcoregtk-3.0:amd64 (1.10.0-0ubuntu1, 1.10.0-0ubuntu1.1), file-roller:amd64 (3.6.0-0ubuntu3, 3.6.1.1-0ubuntu1.1), libreoffice-core:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), libreoffice-writer:amd64 (3.6.2~rc2-0ubuntu3, 3.6.2~rc2-0ubuntu4), gnupg:amd64 (1.4.11-3ubuntu4, 1.4.11-3ubuntu4.1), gnomine:amd64 (3.6.0.2-0ubuntu1, 3.6.0.2-0ubuntu1.2)
End-Date: 2013-02-13  13:37:50


Start-Date: 2013-02-14  07:27:44
Commandline: aptdaemon role='role-commit-packages' sender=':1.742'
Upgrade: x11-apps:amd64 (7.7~2ubuntu1, 7.7~2ubuntu1.1), libunity9:amd64 (6.8.0-0ubuntu2, 6.12.0-0ubuntu0.1), unity-lens-video:amd64 (0.3.12-0ubuntu3, 0.3.14-0ubuntu1), xserver-xorg-core:amd64 (1.13.0-0ubuntu6, 1.13.0-0ubuntu6.1), unity-scope-video-remote:amd64 (0.3.9-0ubuntu1, 0.3.10-0ubuntu1), xserver-common:amd64 (1.13.0-0ubuntu6, 1.13.0-0ubuntu6.1), overlay-scrollbar:amd64 (0.2.16+r357-0ubuntu1, 0.2.16+r357-0ubuntu1.1), apport:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10), gir1.2-gtk-3.0:amd64 (3.6.0-0ubuntu3, 3.6.0-0ubuntu3.2), xdiagnose:amd64 (3.2, 3.2.2), nux-tools:amd64 (3.8.0-0ubuntu1, 3.10.0-0ubuntu1), compiz:amd64 (0.9.8.4-0ubuntu2, 0.9.8.6-0ubuntu1), overlay-scrollbar-gtk2:amd64 (0.2.16+r357-0ubuntu1, 0.2.16+r357-0ubuntu1.1), overlay-scrollbar-gtk3:amd64 (0.2.16+r357-0ubuntu1, 0.2.16+r357-0ubuntu1.1), unity-webapps-common:amd64 (2.4.7-0ubuntu4, 2.4.10-0ubuntu1), apport-gtk:amd64 (2.6.1-0ubuntu3, 2.6.1-0ubuntu10)
End-Date: 2013-02-14  07:28:33

Start-Date: 2013-02-15  18:11:18
Commandline: apt-get install libgconf2-4
Install: libgconf2-4:amd64 (3.2.5-0ubuntu4)
End-Date: 2013-02-15  18:11:29

Start-Date: 2013-02-16  21:26:37
Commandline: aptdaemon role='role-commit-packages' sender=':1.1544'
Install: sbsigntool:amd64 (0.6-0ubuntu1, automatic), secureboot-db:amd64 (1.1~ubuntu0.12.10.1, automatic)
Upgrade: libqt4-declarative:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-declarative:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), qdbus:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-test:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-script:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-script:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-designer:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-network:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-network:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-dbus:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-dbus:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-xmlpatterns:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-xmlpatterns:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-sql-sqlite:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-help:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libcurl3:amd64 (7.27.0-1ubuntu1, 7.27.0-1ubuntu1.1), libqtcore4:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqtcore4:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libcurl3-nss:amd64 (7.27.0-1ubuntu1, 7.27.0-1ubuntu1.1), libqt4-sql:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-sql:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), flashplugin-installer:amd64 (11.2.202.262ubuntu0.12.10.1, 11.2.202.270ubuntu0.12.10.1), libqt4-svg:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-xml:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-xml:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqtgui4:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqtgui4:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libcurl3-gnutls:amd64 (7.27.0-1ubuntu1, 7.27.0-1ubuntu1.1), libqt4-sql-mysql:i386 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), libqt4-scripttools:amd64 (4.8.3+dfsg-0ubuntu3, 4.8.3+dfsg-0ubuntu3.1), grub-efi-amd64-signed:amd64 (1.9+2.00-7ubuntu11, 1.9.1+2.00-7ubuntu11)
End-Date: 2013-02-16  21:29:49
```I had a look in the apt term.log and I found the next entry. Because it is a boot problem I thought that grub-efi-amd64-signed might be the culprit so I uninstalled it but it made no difference

```
Setting up grub-efi-amd64-signed (1.9.1+2.00-7ubuntu11) ... 
BootCurrent: 0002 
Timeout: 0 seconds 
BootOrder: 0003,2003,2001,2002 
Boot0000* EFI Network 0 for IPv6 (4C-72-B9-CD-51-99)  
Boot0001* EFI Network 0 for IPv4 (4C-72-B9-CD-51-99)  
Boot0003* Ubuntu 
Boot2001* EFI USB Device 
Boot2002* EFI DVD/CDROM 
Boot2003* EFI Network 
BootCurrent: 0002 
Timeout: 0 seconds 
BootOrder: 2003,2001,2002 
Boot0000* EFI Network 0 for IPv6 (4C-72-B9-CD-51-99)  
Boot0001* EFI Network 0 for IPv4 (4C-72-B9-CD-51-99)  
Boot2001* EFI USB Device 
Boot2002* EFI DVD/CDROM 
Boot2003* EFI Network 
BootCurrent: 0002 
Timeout: 0 seconds 
BootOrder: 0002,2003,2001,2002 
Boot0000* EFI Network 0 for IPv6 (4C-72-B9-CD-51-99)  
Boot0001* EFI Network 0 for IPv4 (4C-72-B9-CD-51-99)  
Boot2001* EFI USB Device 
Boot2002* EFI DVD/CDROM 
Boot2003* EFI Network 
Boot0002* ubuntu 
Installation finished. No error reported. 
Setting up sbsigntool (0.6-0ubuntu1) ... 
Setting up secureboot-db (1.1~ubuntu0.12.10.1) ... 
Can't access efivars filesystem at /sys/firmware/efi/efivars, aborting 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Log ended: 2013-02-16  21:29:49
```

---

### Post by E411 on 2013-02-24
Ok, may be I should ask my questions in a more specific way ;)

It seems to me that I have a boot problem rather than an X problem.

I noticed that I can boot on vmlinuz-3.5.0-17, the system only hangs at boot with vmlinuz-3.5.0-23

One of the first packets I updated before the problem occurred is indeed linux-image-extra-3.5.0-23-generic

What should I do? Just run update-grub and permanently boot on 3.5.0-17? Or is there something else I should do? 

Regarding the line "Setting up grub-efi-amd64-signed" I found in the apt term.log, is it just the fact that grub was adding 3.5.0-23 in the menu or is it something else? Was it a mistake to run apt-get remove grub-efi-amd64-signed?

Well, what do you recommend I should do here?

---

### Post by bogan on 2013-02-24
Hi!,** E411**,

Sorry, I do not have any answers to your technical Efi questions, but as 3.5.0-17 is working OK, I would suggest the choice is between sticking with that until a further kernal upgrade is released, or updating to, or doing a clean install with a 3.5.0 -24 or -25 LiveCD/USB.

Version -25 is currently available as an update from the 'Proposed' ppa, but of course using that will call for even more updates.

Another approach, one I use myself, is to create new partitions for /root and /home, install the latest released version, and try out things there, before installing them in my main priority installation, especially when video drivers are concerned.

Chao!, **bogan**.

---

### Post by E411 on 2013-02-24
Hello bogan and thanks again for your advice.

I tried 3.5.0-25 and nothing changed so that I guess I will have to stick to 3.5.0-17

I changed the GRUB_DEFAULT entry, is it ok to leave 0-23 and 0-25 in there or should I remove them totally?

May I also ask what difference it exactly makes to create new partitions for /home and /root?

---

### Post by bogan on 2013-02-24
Hi!, **E411**,

I do not understand: > I changed the GRUB_DEFAULT entry, is it ok to leave 0-23 and 0-25 in there or should I remove them totally?Those digits should not exist in /etc/default/grub. Or are you altering another default file.

Edit: If you mean the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in a grub menu script, any change you make is only there for that boot process, a reboot will revert to the original.

Having /home as a separate partition from /root means all your programs, data and settings are retained when a new kernal is installed, and you do not have to make a backup and copy them back afterwards.

Though of course, a backup is still advisable.

Edit: And also, in the case I was describing, your original installation is still accessible, unchanged.

Chao!,** bogan.**

---

### Post by E411 on 2013-02-24
> **bogan said:**
> 

I do not understand: Those digits should not exist in /etc/default/grub. Or are you altering another default file.



Sorry, that was not very clear. I mean I updated the GRUB_DEFAULT variable so that the default is now 3.5.0-17 but I still have 3.5.0-23 and 3.5.0-25 as menu entries. Does it make sense to remove them totally so that only the working kernel is installed or should I just leave things as they are (with Grub booting the oldest kernel in the list)?

---

### Post by bogan on 2013-02-24
Hi!, **E411**,

Unless you are very short of disk space in that partition I would be inclined to leave them as they are, you may want to update them later on.

Chao!,** boga**n.

---

### Post by E411 on 2013-02-24
Cheers, bogan

---

### Post by black veils on 2013-02-24
this tool may interest you: [grub customizer]("http://www.noobslab.com/2012/11/install-grub-customizer-302-in-ubuntu.html")[]("http://www.noobslab.com/2012/11/install-grub-customizer-302-in-ubuntu.html")

---

### Post by E411 on 2013-02-25
> **black veils said:**
> this tool may interest you: [grub customizer]("http://www.noobslab.com/2012/11/install-grub-customizer-302-in-ubuntu.html")

I tend to use the command line whenever it's possible but thanks anyway!

---

