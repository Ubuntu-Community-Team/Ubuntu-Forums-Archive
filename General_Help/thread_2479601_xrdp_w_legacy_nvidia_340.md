---
title: "xrdp w/ legacy nvidia 340"
date: 2022-09-29
forum: General Help
---

### Post by 00sivan on 2022-09-29
Ubuntu 22.04 w/ Nvidia GeForce 9800GTX

I'm trying to get xrdp to work.

xrdp and mstsc were working well with the nouveau driver. I since installed the kelebek333 repo version of the nvidia 340 driver, blacklisted nouveau, and rebooted.

Everything appears to be okay, except that connecting to xrdp using mstsc now gives a black screen with no error.

I have tried purge and reinstall xrdp, and also tried purge then install tightvncserver and then xrdp and using vnc to connect. In that case I get a green screen and eventually the "something happened" error message.


I'm not sure if this is relevant, but inxi says that X.org is "with Xwayland" which is disabled in gdm3.

inxi -G
```
Graphics:
  Device-1: NVIDIA G92 [GeForce 9800 GTX / GTX+] driver: nvidia v: 340.108
  Display: server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1 driver: X: loaded: nvidia
    gpu: nvidia tty: 120x30
  Message: GL data unavailable in console. Try -G --display
```

cat /etc/gdm3/custom.conf | grep Wayland
```
WaylandEnable=false
```


Here are the xrdp logs. I can see that sesman has trouble starting the window manager.

tail -100 /var/log/xrdp.log.
```
[20220929-18:03:26] [INFO ] address [0.0.0.0] port [3389] mode 1
[20220929-18:03:26] [INFO ] listening to port 3389 on 0.0.0.0
[20220929-18:03:26] [INFO ] xrdp_listen_pp done
[20220929-18:03:28] [INFO ] starting xrdp with pid 13334
[20220929-18:03:28] [INFO ] address [0.0.0.0] port [3389] mode 1
[20220929-18:03:28] [INFO ] listening to port 3389 on 0.0.0.0
[20220929-18:03:28] [INFO ] xrdp_listen_pp done
[20220929-18:04:06] [INFO ] Socket 12: AF_INET6 connection received from ::ffff:192.168.12.240 port 50942
[20220929-18:04:06] [INFO ] Using default X.509 certificate: /etc/xrdp/cert.pem
[20220929-18:04:06] [INFO ] Using default X.509 key file: /etc/xrdp/key.pem
[20220929-18:04:06] [ERROR] Cannot read private key file /etc/xrdp/key.pem: Permission denied
[20220929-18:04:06] [ERROR] libxrdp_force_read: header read error
[20220929-18:04:06] [INFO ] Socket 12: AF_INET6 connection received from ::ffff:192.168.12.240 port 50943
[20220929-18:04:06] [ERROR] Processing [ITU-T T.125] Connect-Initial failed
[20220929-18:04:06] [INFO ] Using default X.509 certificate: /etc/xrdp/cert.pem
[20220929-18:04:06] [ERROR] [MCS Connection Sequence] receive connection request failed
[20220929-18:04:06] [INFO ] Using default X.509 key file: /etc/xrdp/key.pem
[20220929-18:04:06] [ERROR] xrdp_sec_incoming: xrdp_mcs_incoming failed
[20220929-18:04:06] [ERROR] Cannot read private key file /etc/xrdp/key.pem: Permission denied
[20220929-18:04:06] [ERROR] xrdp_rdp_incoming: xrdp_sec_incoming failed
[20220929-18:04:06] [INFO ] Connected client computer name: VERMEER
[20220929-18:04:06] [ERROR] xrdp_process_main_loop: libxrdp_process_incoming failed
[20220929-18:04:06] [WARN ] Received [MS-RDPBCGR] TS_UD_HEADER type 0xc006 is unknown (ignored)
[20220929-18:04:06] [ERROR] xrdp_iso_send: trans_write_copy_s failed
[20220929-18:04:07] [WARN ] Received [MS-RDPBCGR] TS_UD_HEADER type 0xc00a is unknown (ignored)
[20220929-18:04:07] [ERROR] Sending [ITU T.125] DisconnectProviderUltimatum failed
[20220929-18:04:07] [INFO ] xrdp_load_keyboard_layout: Keyboard information sent by the RDP client, keyboard_type:[0x04], keyboard_subtype:[0x00], keylayout:[0x00000409]
[20220929-18:04:07] [INFO ] xrdp_load_keyboard_layout: model [] variant [] layout [us] options []
[20220929-18:04:07] [INFO ] Non-TLS connection established from ::ffff:192.168.12.240 port 50943: encrypted with standard RDP security
[20220929-18:04:07] [INFO ] xrdp_caps_process_pointer: client supports new(color) cursor
[20220929-18:04:07] [INFO ] xrdp_process_offscreen_bmpcache: support level 1 cache size 10485760 MB cache entries 100
[20220929-18:04:07] [INFO ] xrdp_caps_process_codecs: nscodec, codec id 1, properties len 3
[20220929-18:04:07] [WARN ] xrdp_caps_process_codecs: unknown codec id 5
[20220929-18:04:07] [INFO ] xrdp_caps_process_codecs: RemoteFX, codec id 3, properties len 49
[20220929-18:04:07] [INFO ] Loading keymap file /etc/xrdp/km-00000409.ini
[20220929-18:04:07] [WARN ] local keymap file for 0x00000409 found and doesn't match built in keymap, using local keymap file
[20220929-18:04:07] [INFO ] connecting to sesman ip 127.0.0.1 port 3350
[20220929-18:04:07] [INFO ] xrdp_wm_log_msg: sesman connect ok
[20220929-18:04:08] [INFO ] sesman connect ok
[20220929-18:04:08] [INFO ] sending login info to session manager, please wait...
[20220929-18:04:08] [INFO ] xrdp_wm_log_msg: login successful for display 10
[20220929-18:04:08] [INFO ] login successful for display 10
[20220929-18:04:08] [INFO ] loaded module 'libxup.so' ok, interface size 10296, version 4
[20220929-18:04:08] [INFO ] started connecting
[20220929-18:04:08] [INFO ] lib_mod_connect: connecting via UNIX socket

```

tail -100 /var/log/xrdp-sesman.log
```
[20220929-18:03:26] [INFO ] starting xrdp-sesman with pid 13324
[20220929-18:04:07] [INFO ] Socket 8: AF_INET6 connection received from ::1 port 52172
[20220929-18:04:08] [INFO ] Terminal Server Users group is disabled, allowing authentication
[20220929-18:04:08] [INFO ] ++ created session (access granted): username sivan, ip ::ffff:192.168.12.240:50943 - socket: 12
[20220929-18:04:08] [INFO ] starting Xorg session...
[20220929-18:04:08] [INFO ] Starting session: session_pid 13396, display :10.0, width 3840, height 2160, bpp 24, client ip ::ffff:192.168.12.240:50943 - socket: 12, user name sivan
[20220929-18:04:08] [INFO ] [session start] (display 10): calling auth_start_session from pid 13396
[20220929-18:04:08] [ERROR] sesman_data_in: scp_process_msg failed
[20220929-18:04:08] [INFO ] Starting X server on display 10: /usr/lib/xorg/Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log
[20220929-18:04:08] [ERROR] sesman_main_loop: trans_check_wait_objs failed, removing trans
[20220929-18:04:08] [INFO ] Found X server running at /tmp/.X11-unix/X10
[20220929-18:04:08] [INFO ] Found X server running at /tmp/.X11-unix/X10
[20220929-18:04:08] [ERROR] There is no X server active on display 10
[20220929-18:04:08] [INFO ] Session started successfully for user sivan on display 10
[20220929-18:04:08] [INFO ] Starting the xrdp channel server for display 10
[20220929-18:04:09] [ERROR] A fatal error has occured attempting to start the window manager on display 10, aborting connection
[20220929-18:04:09] [INFO ] Session in progress on display 10, waiting until the window manager (pid 13397) exits to end the session
[20220929-18:04:09] [WARN ] Window manager (pid 13397, display 10) exited quickly (0 secs). This could indicate a window manager config problem
[20220929-18:04:09] [INFO ] Calling auth_stop_session and auth_end from pid 13396
[20220929-18:04:09] [INFO ] Terminating X server (pid 13398) on display 10
[20220929-18:04:09] [INFO ] Terminating the xrdp channel server (pid 13401) on display 10
[20220929-18:04:09] [INFO ] X server on display 10 (pid 13398) returned exit code 1 and signal number 0
[20220929-18:04:09] [INFO ] xrdp channel server for display 10 (pid 13401) exit code 0 and signal number 0
[20220929-18:04:09] [INFO ] cleanup_sockets:
[20220929-18:04:09] [INFO ] ++ terminated session:  username sivan, display :10.0, session_pid 13396, ip ::ffff:192.168.12.240:50943 - socket: 12

```

Thanks for any ideas on this.

---

### Post by Bashing-om on 2022-09-29
00sivan; hummm ....


edit: Ouch!  musta had some wires crossed as Nvidia does recommend 340 !

[s]Nvidia recommends the 390 version driver:[/s]
 [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

[s]That 390 version driver is in our repo:
> 
sysop@x2204mini:~$ apt list nvidia-driver-390
Listing... Done
nvidia-driver-390/jammy-security,jammy-updates 390.154-0ubuntu0.22.04.1 amd64
nvidia-driver-390/jammy-security,jammy-updates 390.154-0ubuntu0.22.04.1 i386
sysop@x2204mini:~$ [/s]


> 
sysop@x2204mini:~$ apt list nvidia-340
Listing... Done
nvidia-340/jammy 340.108-0ubuntu8 amd64
sysop@x2204mini:~$ 


Purge what you have and try:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

Reboot to see the effect.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by 00sivan on 2022-09-29
Thanks for the reply.

```

sudo apt install nvidia-340
sudo reboot

```

...

```

~$ inxi -G
Graphics:
  Device-1: NVIDIA G92 [GeForce 9800 GTX / GTX+] driver: nouveau v: kernel
  Display: server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1 driver: X: loaded: nvidia
    gpu: nouveau tty: 120x30 resolution: 1920x1080
  Message: GL data unavailable in console. Try -G --display

```

okay... so let's blacklist nouveau

```

sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
sudo update-initramfs -u
sudo reboot

```

...

```

~$ inxi -G
Graphics:
  Device-1: NVIDIA G92 [GeForce 9800 GTX / GTX+] driver: N/A
  Display: server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1 driver: X: loaded: nvidia
    gpu: N/A tty: 120x30
  Message: GL data unavailable in console. Try -G --display

```

driver: N/A ? gpu: N/A? That doesn't look good. But at least it loaded: nvidia? okay. Let's try starting the graphical target.

```

~$ systemctl isolate graphical
~$ inxi -G
Graphics:
  Device-1: NVIDIA G92 [GeForce 9800 GTX / GTX+] driver: N/A
  Display: server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1 driver: X: loaded: nouveau
    unloaded: modesetting gpu: N/A tty: 120x30
  Message: GL data unavailable in console. Try -G --display

```

uh... so now we are back with nouveau?

hmmm... seems like the Ubuntu repo version doesn't exactly work. And that's how I ended up using the other repo.

Open to suggestions.

---

### Post by 00sivan on 2022-09-29
forgot to mention:
```

~$ sudo ubuntu-drivers autoinstall
All the available drivers are already installed.

```

---

### Post by Bashing-om on 2022-09-29
00sivan; Yeah

Real strange.

what shows:
```

sudo grep 'blacklist.*nouveau' /lib/modprobe.d/*
dpkg -l | grep -i nvidia
sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
#note the change to the blacklist directory location as of 18.04.

[INDENT][INDENT]gots to be a reason[/INDENT][/INDENT]

---

### Post by 00sivan on 2022-09-30
I think 340 doesn't work with kernel >5.4. [Nvidia Drops Linux Support For GeForce G8x, G9x, and GT2xx graphics cards - LinuxReviews]("https://linuxreviews.org/Nvidia_Drops_Linux_Support_For_GeForce_G8x,_G9x,_and_GT2xx_graphics_cards")

It's a legacy device, so I'm not surprised Ubuntu doesn't support it. Anyway, I assume that if it worked out of the box, there wouldn't be a 3rd party repository for it so I'm guessing further investigation into the Ubuntu driver is a waste of time.

My goal is to get xrdp to work with this driver. My best lead at the moment is that inxi -G is reporting that X.org is "with XWayland" and I can't seem to get that to turn off.

Is that part of the driver? Or is that an Xorg setting? If it's an Xorg setting, where can I configure that? Shouldn't setting Wayalend to false in the gdm3 config turn it off?

---

### Post by mikewhatever on 2022-09-30
Nvidia-340 is indeed unsupported and untested on 22.04. Nvidia dropped support at the end of 2019, so the last supported Ubuntu release is 20.04 with kernel 5.4. The PPA you've used just makes it installable on later releases, but there is no one to test and fix bugs.
If you want to use nvidia-340, use 20.04.

---

### Post by 00sivan on 2022-09-30
Good to know. But I'm encouraged by the fact that everything works aside from xrdp.

Anyone tested older versions of xrdp on 22.04?

Can I force xrdp / x.org to use Xorg not Wayland?

Any other ideas?

---

### Post by MAFoElffen on 2022-09-30
I cannot test this to confirm, as my main workstation is in the middle of maintenance and says it has 2 days left in expanding a partition, but...

Your logs say that it is crashing on the desktop, which you diagnosed as "Wayland", which is correct, XRDP works only on XServer... 

As I remember, (and correct me if I'm wrong,) I think the top of the first of three dialog boxes is "Session", where you can select the xrdp session's Desktop Environment (DE) from the XRDP Graphical Login Screen(?)... Where you would select the XServer Session available. Right?

---

### Post by 00sivan on 2022-09-30
Yes, you can. If I choose the Xorg session then I get a green screen that hangs and eventually produces the "some problem" error message.

So it might not be that xrdp isn't choosing xorg. It might be that something is wrong with the xorg server? Ubuntu seems to load up and run fine under Xorg generally though. Just not from xrdp.

Not sure what to check next.

---

### Post by 00sivan on 2022-09-30
Ran xrdp in debug to capture the following:

```

xorg-server 2:21.1.3-2ubuntu2.1 (For technical support please see http://www.ubuntu.com/support)Current version of pixman: 0.40.0
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: ".xorgxrdp.10.log", Time: Fri Sep 30 10:35:57 2022
(++) Using config file: "/etc/X11/xrdp/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
xorgxrdpSetup:
xrdpdevSetup:
================ WARNING WARNING WARNING WARNING ================
This server has a video driver ABI version of 25.2 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
=================================================================
(EE) NVIDIA: Use the -ignoreABI option to override this check.
================ WARNING WARNING WARNING WARNING ================
This server has a video driver ABI version of 25.2 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
=================================================================
(EE) NVIDIA: Use the -ignoreABI option to override this check.
rdpmousePlug:
rdpkeybPlug:
rdpIdentify:
rdpDriverFunc: op 10
(EE)
Fatal server error:
(EE) parse_vt_settings: Cannot open /dev/tty0 (Permission denied)
(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at ".xorgxrdp.10.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.

```

```
# cat .xorgxrdp.10.log[  3828.782]
X.Org X Server 1.21.1.3
X Protocol Version 11, Revision 0
[  3828.782] Current Operating System: Linux yorkfield 5.15.0-48-generic #54-Ubuntu SMP Fri Aug 26 13:26:29 UTC 2022 x86_64
[  3828.782] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-48-generic root=UUID=3c18500b-9ee2-4d00-848f-9f8b374112f6 ro quiet splash vt.handoff=7
[  3828.782] xorg-server 2:21.1.3-2ubuntu2.1 (For technical support please see http://www.ubuntu.com/support)
[  3828.782] Current version of pixman: 0.40.0
[  3828.782]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[  3828.782] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3828.782] (++) Log file: ".xorgxrdp.10.log", Time: Fri Sep 30 10:35:57 2022
[  3828.782] (++) Using config file: "/etc/X11/xrdp/xorg.conf"
[  3828.782] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3828.783] (**) Option "defaultserverlayout" "X11 Server"
[  3828.783] (**) ServerLayout "X11 Server"
[  3828.783] (**) |-->Screen "Screen (xrdpdev)" (0)
[  3828.783] (**) |   |-->Monitor "Monitor"
[  3828.783] (**) |   |-->Device "Video Card (xrdpdev)"
[  3828.783] (**) |   |-->GPUDevice "Nvidia Card"
[  3828.783] (**) |-->Input Device "xrdpMouse"
[  3828.783] (**) |-->Input Device "xrdpKeyboard"
[  3828.783] (**) Option "DontVTSwitch" "on"
[  3828.783] (**) Option "AutoAddDevices" "off"
[  3828.783] (**) Not automatically adding devices
[  3828.783] (==) Automatically enabling devices
[  3828.783] (==) Automatically adding GPU devices
[  3828.783] (==) Automatically binding GPU devices
[  3828.783] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  3828.783] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3828.783]    Entry deleted from font path.
[  3828.783] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3828.783]    Entry deleted from font path.
[  3828.783] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3828.783]    Entry deleted from font path.
[  3828.784] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3828.784]    Entry deleted from font path.
[  3828.784] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3828.784]    Entry deleted from font path.
[  3828.784] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[  3828.784] (**) ModulePath set to "/usr/lib/nvidia-340/xorg,/usr/lib/xorg/modules"
[  3828.784] (II) Loader magic: 0x555e67e5f020
[  3828.784] (II) Module ABI versions:
[  3828.784]    X.Org ANSI C Emulation: 0.4
[  3828.784]    X.Org Video Driver: 25.2
[  3828.784]    X.Org XInput driver : 24.4
[  3828.784]    X.Org Server Extension : 10.0
[  3828.787] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_319
[  3828.795] (--) PCI:*(1@0:0:0) 10de:0612:19f1:0a76 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[  3828.795] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  3828.795] (II) LoadModule: "dbe"
[  3828.795] (II) Module "dbe" already built-in
[  3828.795] (II) LoadModule: "ddc"
[  3828.795] (II) Module "ddc" already built-in
[  3828.795] (II) LoadModule: "extmod"
[  3828.795] (II) Module "extmod" already built-in
[  3828.795] (II) LoadModule: "glx"
[  3828.795] (II) Loading /usr/lib/nvidia-340/xorg/libglx.so
[  3828.819] (II) Module glx: vendor="NVIDIA Corporation"
[  3828.819]    compiled for 4.0.2, module version = 1.0.0
[  3828.819]    Module class: X.Org Server Extension
[  3828.819] (II) NVIDIA GLX Module  340.108  Wed Dec 11 14:26:50 PST 2019
[  3828.819] (II) LoadModule: "int10"
[  3828.819] (II) Loading /usr/lib/xorg/modules/libint10.so
[  3828.819] (II) Module int10: vendor="X.Org Foundation"
[  3828.819]    compiled for 1.21.1.3, module version = 1.0.0
[  3828.819]    ABI class: X.Org Video Driver, version 25.2
[  3828.819] (II) LoadModule: "record"
[  3828.819] (II) Module "record" already built-in
[  3828.819] (II) LoadModule: "vbe"
[  3828.819] (II) Loading /usr/lib/xorg/modules/libint10.so
[  3828.819] (II) Module int10: vendor="X.Org Foundation"
[  3828.819]    compiled for 1.21.1.3, module version = 1.0.0
[  3828.819]    ABI class: X.Org Video Driver, version 25.2
[  3828.819] (II) LoadModule: "glamoregl"
[  3828.820] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3828.829] (II) Module glamoregl: vendor="X.Org Foundation"
[  3828.829]    compiled for 1.21.1.3, module version = 1.0.1
[  3828.829]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3828.829] (II) LoadModule: "xorgxrdp"
[  3828.829] (II) Loading /usr/lib/xorg/modules/libxorgxrdp.so
[  3828.829] (II) Module XORGXRDP: vendor="X.Org Foundation"
[  3828.829]    compiled for 1.21.1.3, module version = 0.2.17
[  3828.829]    ABI class: X.Org Video Driver, version 25.2
[  3828.829] xorgxrdpSetup:
[  3828.829] (II) LoadModule: "fb"
[  3828.829] (II) Module "fb" already built-in
[  3828.829] (II) LoadModule: "xrdpdev"
[  3828.830] (II) Loading /usr/lib/xorg/modules/drivers/xrdpdev_drv.so
[  3828.830] (II) Module XRDPDEV: vendor="X.Org Foundation"
[  3828.830]    compiled for 1.21.1.3, module version = 0.2.17
[  3828.830]    ABI class: X.Org Video Driver, version 25.2
[  3828.830] xrdpdevSetup:
[  3828.830] (II) LoadModule: "nvidia"
[  3828.830] (II) Loading /usr/lib/nvidia-340/xorg/nvidia_drv.so
[  3828.831] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3828.831]    compiled for 4.0.2, module version = 1.0.0
[  3828.831]    Module class: X.Org Video Driver
[  3828.831] ================ WARNING WARNING WARNING WARNING ================
[  3828.831] This server has a video driver ABI version of 25.2 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
[  3828.831] =================================================================
[  3828.831] (EE) NVIDIA: Use the -ignoreABI option to override this check.
[  3828.831] (II) UnloadModule: "nvidia"
[  3828.831] (II) Unloading nvidia
[  3828.831] (EE) Failed to load module "nvidia" (unknown error, 0)
[  3828.961] (==) Matched nouveau as autoconfigured driver 0
[  3828.961] (==) Matched modesetting as autoconfigured driver 1
[  3828.961] (==) Matched fbdev as autoconfigured driver 2
[  3828.961] (==) Matched vesa as autoconfigured driver 3
[  3828.961] (==) Assigned the driver to the xf86ConfigLayout
[  3828.961] (II) LoadModule: "nouveau"
[  3828.961] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  3828.962] (II) Module nouveau: vendor="X.Org Foundation"
[  3828.962]    compiled for 1.21.1.3, module version = 1.0.17
[  3828.962]    Module class: X.Org Video Driver
[  3828.962]    ABI class: X.Org Video Driver, version 25.2
[  3828.962] (II) LoadModule: "nvidia"
[  3828.962] (II) Loading /usr/lib/nvidia-340/xorg/nvidia_drv.so
[  3828.963] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3828.963]    compiled for 4.0.2, module version = 1.0.0
[  3828.963]    Module class: X.Org Video Driver
[  3828.963] ================ WARNING WARNING WARNING WARNING ================
[  3828.963] This server has a video driver ABI version of 25.2 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
[  3828.963] =================================================================
[  3828.963] (EE) NVIDIA: Use the -ignoreABI option to override this check.
[  3828.963] (II) UnloadModule: "nvidia"
[  3828.963] (II) Unloading nvidia
[  3828.963] (EE) Failed to load module "nvidia" (unknown error, 0)
[  3828.963] (II) LoadModule: "modesetting"
[  3828.963] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3828.963] (II) Module modesetting: vendor="X.Org Foundation"
[  3828.963]    compiled for 1.21.1.3, module version = 1.21.1
[  3828.964]    Module class: X.Org Video Driver
[  3828.964]    ABI class: X.Org Video Driver, version 25.2
[  3828.964] (II) LoadModule: "fbdev"
[  3828.964] (WW) Warning, couldn't open module fbdev
[  3828.964] (EE) Failed to load module "fbdev" (module does not exist, 0)
[  3828.964] (II) LoadModule: "vesa"
[  3828.964] (WW) Warning, couldn't open module vesa
[  3828.964] (EE) Failed to load module "vesa" (module does not exist, 0)
[  3828.964] (II) LoadModule: "xrdpmouse"
[  3828.964] (II) Loading /usr/lib/xorg/modules/input/xrdpmouse_drv.so
[  3828.965] (II) Module XRDPMOUSE: vendor="X.Org Foundation"
[  3828.965]    compiled for 1.21.1.3, module version = 0.2.17
[  3828.965]    Module class: X.Org XInput Driver
[  3828.965]    ABI class: X.Org XInput driver, version 24.4
[  3828.965] rdpmousePlug:
[  3828.965] (II) LoadModule: "xrdpkeyb"
[  3828.965] (II) Loading /usr/lib/xorg/modules/input/xrdpkeyb_drv.so
[  3828.965] (II) Module XRDPKEYB: vendor="X.Org Foundation"
[  3828.965]    compiled for 1.21.1.3, module version = 0.2.17
[  3828.965]    Module class: X.Org XInput Driver
[  3828.965]    ABI class: X.Org XInput driver, version 24.4
[  3828.965] rdpkeybPlug:
[  3828.965] rdpIdentify:
[  3828.965] (II) XRDPDEV: driver for xrdp: XRDPDEV
[  3828.965] rdpDriverFunc: op 10
[  3828.965] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[  3828.965] (II) NOUVEAU driver for NVIDIA chipset families :
[  3828.965]    RIVA TNT            (NV04)
[  3828.965]    RIVA TNT2           (NV05)
[  3828.966]    GeForce 256         (NV10)
[  3828.966]    GeForce 2           (NV11, NV15)
[  3828.966]    GeForce 4MX         (NV17, NV18)
[  3828.966]    GeForce 3           (NV20)
[  3828.966]    GeForce 4Ti         (NV25, NV28)
[  3828.966]    GeForce FX          (NV3x)
[  3828.966]    GeForce 6           (NV4x)
[  3828.966]    GeForce 7           (G7x)
[  3828.966]    GeForce 8           (G8x)
[  3828.966]    GeForce 9           (G9x)
[  3828.966]    GeForce GTX 2xx/3xx (GT2xx)
[  3828.966]    GeForce GTX 4xx/5xx (GFxxx)
[  3828.967]    GeForce GTX 6xx/7xx (GKxxx)
[  3828.967]    GeForce GTX 9xx     (GMxxx)
[  3828.967]    GeForce GTX 10xx    (GPxxx)
[  3828.967] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3828.967] (EE)
Fatal server error:
[  3828.967] (EE) parse_vt_settings: Cannot open /dev/tty0 (Permission denied)
[  3828.967] (EE)
[  3828.967] (EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[  3828.967] (EE) Please also check the log file at ".xorgxrdp.10.log" for additional information.
[  3828.967] (EE)
[  3828.967] (WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
[  3828.967] (WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
[  3828.968] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by 00sivan on 2022-09-30
For the Nvidia warning, I added to the Section "ServerFlags" of /etc/X11/xrdp/xorg.conf

```
Option "IgnoreABI" "true"
```

Then to address this error:
```
(EE) parse_vt_settings: Cannot open /dev/tty0 (Permission denied)
```

I ran:
```
gpasswd -a myusername tty
```

Now the error I'm getting is:
```
(EE) xf86OpenConsole: Cannot open virtual console 2 (Permission denied)
```

Thanks for any help on this!

---

