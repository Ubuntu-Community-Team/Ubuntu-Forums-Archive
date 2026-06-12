---
title: "Firefox flash frequently crashing?"
date: 2014-02-03
forum: General Help
---

### Post by d4m1r on 2014-02-03
Has anyone else noticed that flash within Firefox has been crashing a lot more recently? Since the recent non-pepper update for Flash (to version 11.2.202.335) flash within Firefox has been crashing on 25% of videos :?

Before it was rock solid, now it will crash on 1/4 videos...And when I mean crash, is it says "the adobe flash plugin has crashed, reload the page to try again". Sometimes I can reload it and it will work right away, other times I have to reload the page 4-5 times the page to get it working....VERY annoying. Any idea's as to why? Was this latest update pushed without even spending a second to actually test it?

-Flash 11.2.202.335
-Firefox 26
-Ubuntu 12.04 LTS (x64)

---

### Post by ajgreeny on 2014-02-03
No problem here on Xubuntu 12.04 64bit using the same browser and flash version.

---

### Post by Erik1984 on 2014-02-03
No problems here either. Kubuntu + same FF and Flash version. Maybe the GPU makes the difference (I have intel graphics hd2500), did you recently receive any updates on your graphics drivers?

---

### Post by d4m1r on 2014-02-03
I have an Intel 4000 HD and no, I am using the stock drivers.

Can anyone running Ubuntu confirm or deny similar issues?

---

### Post by ajgreeny on 2014-02-04
My system is also using Intel HD4000, so that shouldn't be a problem.

---

### Post by Erik1984 on 2014-02-04
But you run Xubuntu, I have Kubuntu, both don't have Compiz running by default. @d4m1r Do you have the Gnome Flashback/Fallback session installed? You could try running the Flashback session with effects disabled. That could rule out Compiz.

---

### Post by ajgreeny on 2014-02-04
I had not considered compiz as I don't see a need for it in Xubuntu, but you could be right.

I also, incidentally, use the ppa at  [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)  for my xorg intel driver which I suppose could make my system more stable?

---

### Post by d4m1r on 2014-02-05
> **Euroman said:**
> @d4m1r Do you have the Gnome Flashback/Fallback session installed? You could try running the Flashback session with effects disabled. That could rule out Compiz.

No I don't, only have and use the default Unity (3D) session with compiz.

Is there a way to get more detailed logs as to why Flash crashing within Firefox? Error logs perhaps saved somewhere?

---

### Post by ajgreeny on 2014-02-05
You might find something in the hidden .xsession-errors file in your home.

---

### Post by d4m1r on 2014-02-05
You might be onto something.....Lots of weird looking errors, related to Firefox, Flash, etc. Take a look and tell me what you think if you don't mind.


```

Warning: Only changing the first 12 of 13 buttons. 
Backend     : gconf 
Integration : true 
Profile     : unity 
Adding plugins 
Initializing core options...done 
gnome-session[2101]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "indicator-cpufreq" (No such file or directory) 
Initializing composite options...done 
Initializing opengl options...done 
Initializing decor options...done 
Initializing vpswitch options...done 
Initializing snap options...done 
Initializing mousepoll options...done 
Initializing resize options...done 
INFO:root:Menu shown 
INFO:root:Fetcher started 
Initializing place options...done 
Initializing move options...done 
usage:  xprop [-options ...] [[format [dformat]] atom] ... 
 
where options include: 
    -grammar                       print out full grammar for command line 
    -display host:dpy              the X server to contact 
    -id id                         resource id of window to examine 
    -name name                     name of window to examine 
    -font name                     name of font to examine 
    -remove propname               remove a property 
    -set propname value            set a property to a given value 
    -root                          examine the root window 
    -len n                         display at most n bytes of any property 
    -notype                        do not display the type field 
    -fs filename                   where to look for formats for properties 
    -frame                         don't ignore window manager frames 
    -f propname format [dformat]   formats to use for property of given name 
    -spy                           examine window properties forever 
 
WARNING:21:18:47:DesktopService:uinput:No joystick calibration available. 
WARNING:21:18:47:DesktopService:uinput:No joystick calibration available. 
Initializing wall options...done 
Initializing grid options...done 
 
(gnome-settings-daemon:2153): color-plugin-WARNING **: failed to reset xrandr-Apple Computer Inc-16843009 gamma tables: gamma size is zero 
No LSB modules are available. 
I/O warning : failed to load external entity "/home/damir/.compiz/session/10934b78475c780675139163152312848000000021010048" 
Initializing session options...done 
Initializing gnomecompat options...done 
** Message: applet now removed from the notification area 
Initializing animation options...done 
Initializing fade options...done 
Initializing unitymtgrabhandles options...done 
** Message: using fallback from indicator to GtkStatusIcon 
Initializing workarounds options...done 
Initializing scale options...done 
compiz (expo) - Warn: failed to bind image to texture 
Initializing expo options...done 
Initializing ezoom options...done 
 
(compiz:2171): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed 
/usr/lib/jupiter/scripts/resolutions: line 42: /var/jupiter/available_resolutions_LVDS1: Permission denied 
Initializing unityshell options...done 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing. 
 
** Message: moving back from GtkStatusIcon to indicator 
Setting Update "main_menu_key" 
Setting Update "run_key" 
Setting Update "launcher_hide_mode" 
Setting Update "icon_size" 
Setting Update "reveal_pressure" 
Setting Update "devices_option" 
Setting Update "num_launchers" 
Setting Update "launcher_capture_mouse" 
gnome-session[2101]: WARNING: Could not launch application 'telepathy-indicator.desktop': Unable to start application: Failed to execute child process "telepathy-indicator" (No such file or directory) 
 
** (zeitgeist-datahub:3082): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus! 
WARNING:21:22:39:MainThread:dbus:Got page_changed event when no such page (sysmon) exists 
 
(gnome-settings-daemon:2153): color-plugin-WARNING **: failed to reset xrandr-Apple Computer Inc-16843009 gamma tables: gamma size is zero 
[0x1ddd108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface. 
[0x1df0928] main playlist: stopping playback 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
WARNING:21:32:56:default:icon:Icon text-plain (43) not found 
[0x7f6f8c001398] access_http access: Raw-audio server found, m4a demuxer selected 
[0x7f6f8c007348] packetizer_mpeg4audio demux packetizer: AAC channels: 2 samplerate: 22050 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:57:default:icon:Icon text-plain (43) not found 
WARNING:21:32:58:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:00:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:05:default:icon:Icon text-plain (43) not found 
WARNING:21:33:55:default:icon:Icon text-plain (43) not found 
WARNING:21:33:55:default:icon:Icon text-plain (43) not found 
WARNING:21:33:55:default:icon:Icon text-plain (43) not found 
WARNING:21:33:55:default:icon:Icon text-plain (43) not found 
WARNING:21:33:57:default:icon:Icon text-plain (43) not found 
WARNING:21:33:57:default:icon:Icon text-plain (43) not found 
WARNING:21:33:57:default:icon:Icon text-plain (43) not found 
WARNING:21:33:57:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:02:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:05:default:icon:Icon text-plain (43) not found 
WARNING:21:34:30:default:icon:Icon text-plain (43) not found 
WARNING:21:34:30:default:icon:Icon text-plain (43) not found 
WARNING:21:34:30:default:icon:Icon text-plain (43) not found 
WARNING:21:34:30:default:icon:Icon text-plain (43) not found 
WARNING:21:34:32:default:icon:Icon text-plain (43) not found 
WARNING:21:34:32:default:icon:Icon text-plain (43) not found 
WARNING:21:34:32:default:icon:Icon text-plain (43) not found 
WARNING:21:34:32:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:33:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:34:36:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:00:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:03:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:11:default:icon:Icon text-plain (43) not found 
WARNING:21:35:22:default:icon:Icon text-plain (43) not found 
WARNING:21:35:22:default:icon:Icon text-plain (43) not found 
WARNING:21:35:22:default:icon:Icon text-plain (43) not found 
WARNING:21:35:22:default:icon:Icon text-plain (43) not found 
WARNING:21:35:24:default:icon:Icon text-plain (43) not found 
WARNING:21:35:24:default:icon:Icon text-plain (43) not found 
WARNING:21:35:24:default:icon:Icon text-plain (43) not found 
WARNING:21:35:24:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
WARNING:21:38:23:default:icon:Icon text-plain (43) not found 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:27:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:41:51:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:11:default:icon:Icon text-plain (43) not found 
WARNING:21:42:12:default:icon:Icon text-plain (43) not found 
WARNING:21:42:12:default:icon:Icon text-plain (43) not found 
WARNING:21:42:12:default:icon:Icon text-plain (43) not found 
WARNING:21:42:12:default:icon:Icon text-plain (43) not found 
WARNING:21:42:20:default:icon:Icon text-plain (43) not found 
WARNING:21:42:20:default:icon:Icon text-plain (43) not found 
WARNING:21:42:20:default:icon:Icon text-plain (43) not found 
WARNING:21:42:20:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:22:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:57:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:42:59:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:00:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:43:02:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:46:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:MainThread:dbus:Got page_changed event when no such page (sysmon) exists 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:47:default:icon:Icon text-plain (43) not found 
WARNING:21:44:48:default:icon:Icon text-plain (43) not found 
WARNING:21:44:48:default:icon:Icon text-plain (43) not found 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
 
(plugin-container:20840): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.10/gdk/x11/gdkdrawable-x11.c:874 drawable is not a pixmap or window 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
[xcb] Too much data requested from _XRead 
[xcb] This is most likely caused by a broken X extension library 
[xcb] Aborting, sorry about that. 
plugin-container: ../../src/xcb_io.c:736: _XRead: Assertion `!xcb_xlib_too_much_data_requested' failed. 
 
(plugin-container:31085): Gdk-CRITICAL **: IA__gdk_pixmap_foreign_new_for_screen: assertion `GDK_IS_SCREEN (screen)' failed 
 
(plugin-container:31085): Gdk-CRITICAL **: IA__gdk_drawable_set_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed 
plugin-container: Fatal IO error 11 (Resource temporarily unavailable) on X server :0. 
WARNING: pipe error (99): Connection reset by peer: file /build/buildd/firefox-26.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 437 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
[xcb] Unknown request in queue while dequeuing 
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called 
[xcb] Aborting, sorry about that. 
plugin-container: Fatal IO error 11 (Resource temporarily unavailable) on X server :0. 
plugin-container: ../../src/xcb_io.c:179: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed. 
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED 
[32175:32208:0205/214701:ERROR:audio_manager_base.cc(422)] Not implemented reached in virtual std::string media::AudioManagerBase::GetDefaultOutputDeviceID() 
ATTENTION: default value of option force_s3tc_enable overridden by environment. 
[32175:32200:0205/214710:ERROR:audio_manager_base.cc(422)] Not implemented reached in virtual std::string media::AudioManagerBase::GetDefaultOutputDeviceID() 
** Message: Error: Stream contains no data. 
gsttypefindelement.c(954): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind: 
Can't typefind empty stream 
 
** Message: Error: This file is incomplete and cannot be played. 
qtdemux.c(2744): gst_qtdemux_loop_state_header (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstQTDemux:qtdemux0: 
We got less than expected (received 340050, wanted 1001507, offset 28) 
 
2014-02-05 21:59:05,495 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')' 
2014-02-05 21:59:05,495 - root - ERROR - Could not find any typelib for Gst 
2014-02-05 21:59:05,538 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None' 
2014-02-05 21:59:05,543 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 
2014-02-05 21:59:05,871 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file 
2014-02-05 21:59:05,999 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None. 
2014-02-05 21:59:06,004 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() 
2014-02-05 21:59:08,418 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/utils.py', 201, 'get_title_from_html')' 
2014-02-05 21:59:08,418 - root - WARNING - failed to parse: '<div style="background-color: #161513; width:1680px; height:200px;"> 
 <div style="background: url('/site_media/exhibits/2013/09/AAMFP_Leaderboard_700x200_1.jpg') top left no-repeat; width:700px; height:200px;"></div> 
</div>' ('ascii' codec can't encode character u'\xa0' in position 70: ordinal not in range(128)) 
2014-02-05 21:59:11,482 - softwarecenter.db.update - INFO - skipping region restricted app: 'Comentarios Web' (not whitelisted) 
2014-02-05 21:59:11,618 - softwarecenter.db.update - INFO - skipping region restricted app: 'reEarCandy' (not whitelisted) 
2014-02-05 21:59:12,196 - softwarecenter.db.update - INFO - skipping region restricted app: 'Flaggame' (not whitelisted) 
2014-02-05 21:59:12,459 - softwarecenter.db.update - INFO - skipping region restricted app: 'Bulleti d'esquerra de Calonge i Sant Antoni ' (not whitelisted) 
2014-02-05 21:59:12,554 - softwarecenter.db.update - INFO - skipping region restricted app: 'Source Code Analyzer' (not whitelisted) 
2014-02-05 21:59:13,219 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0 
2014-02-05 21:59:13,220 - softwarecenter.db.database - INFO - reopen() database 
2014-02-05 21:59:13,220 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 
2014-02-05 22:00:11,912 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
[xcb] Unknown request in queue while dequeuing 
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called 
[xcb] Aborting, sorry about that. 
plugin-container: ../../src/xcb_io.c:179: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed. 
WARNING: pipe error (97): Connection reset by peer: file /build/buildd/firefox-26.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 437 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
[xcb] Unknown request in queue while dequeuing 
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called 
[xcb] Aborting, sorry about that. 
plugin-container: ../../src/xcb_io.c:179: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed. 
WARNING: pipe error (97): Connection reset by peer: file /build/buildd/firefox-26.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 437 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory 
 
(nautilus:2205): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported 
 
 
(nautilus:2205): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported 
 
 
(nautilus:2205): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported 
 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing. 
 
 
(nautilus:2205): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported 


```

---

### Post by ajgreeny on 2014-02-05
I see them, but I'm afraid I don't really understand what they mean.
There is one instance of> [WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXEDbut that is just a warning, not a real error and suggests you also have google-chrome with pepperflash installed, or have you perhaps used the ppa to install pepperflash in chromium?,
You also have a repeated > WARNING: pipe error (97): Connection reset by peer: file /build/buildd/firefox-26.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 437 which seems to suggest that there is a file somewhere in your system (which I do not have) named /build/buildd/firefox-26.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc

Can you show the output of command ```
locate build/buildd
```to see if that file really does exist.

---

### Post by mc4man on 2014-02-05
I've seen  this numerous times on 14.04 with nvidia 660m where I'm only using the Intel 4000 side.
(though it's quite possible it's from enabling hw acceleration in FF for flash  but not starting FF with the env needed to actually do so.

In any event when I go to yt in FF with hwacel properly enabled then it never happens.

---

### Post by d4m1r on 2014-02-05
> **ajgreeny said:**
> 
Can you show the output of command ```
locate build/buildd
```to see if that file really does exist.

damir@damir-macbook:~$ locate build/buildd
damir@damir-macbook:~$

?

---

