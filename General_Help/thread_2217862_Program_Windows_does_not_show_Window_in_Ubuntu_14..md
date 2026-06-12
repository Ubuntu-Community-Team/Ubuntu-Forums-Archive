---
title: "Program Windows does not show Window in Ubuntu 14.04"
date: 2014-04-18
forum: General Help
---

### Post by khatkarrohit on 2014-04-18
I did a fresh install of Ubuntu 14.04. But when I run programs clicking their icons or from terminal than their window does not show up. Here are different error messages I get when I run programs through terminal:

1. When I run chromium browser:
```
chromium-browser 
ATTENTION: default value of option force_s3tc_enable overridden by environment.
```

2. When Itry to open System Monitor, it does not show up.
```
gnome-system-monitor
** (gnome-system-monitor:3279): WARNING **: SELinux was found but is not enabled.
```

3. When I reun VLC from terminal.
```
vlc
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x924118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
```


4. Rhythmbox also does not show up.
```
rhythmbox

(rhythmbox:4068): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

(rhythmbox:4068): GLib-GObject-CRITICAL **: object SoupServer 0x2d35930 finalized while still in-construction

(rhythmbox:4068): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
```

5. Virtualbox from Oracle website also does not work.
```
virtualbox 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "S&tart" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28
```

Their icons shows up in sidebar but no windows shows up. 

Some application like firefox, nautilus works fine. Does anyone else got similar problems.


System Info:
```
OS: Ubuntu 14.04
Processor: Intel® Core&#8482; i7-4771 CPU @ 3.50GHz × 8 
Memory: 32 GB
Motherboard: Intel® Desktop Board DH87MC
Graphics: Intel® Haswell Desktop 
OD Type: 64-bit
Disk: 248.8 GB (SSD)
```

I installed SE Linux with this command.
```
 sudo apt-get install selinux
```
After installing SELinux, gnome-system-monitor does not give any warning but still no window show up.

Before Installing UBuntu 14.04 I tested it in VirtualBox as Virtual machine and it was working fine and I remember that gnome-system-monitor was working fine and its windows was showing up. But on real machine many application windows do not show up.

---

### Post by sdowney717 on 2014-04-18
I would re-download and make a new liveusb, then reinstall.
there is a way to verify the integrity of the download, do that to know the files are ok.

If you have a working hard drive with working Ubuntu install on it, you can clone it and stick it in your PC and it will work. just keep 32 bit and 64 bit separated.
I have done things like that using clonezilla.

---

### Post by Bradley_Ware on 2014-04-18
Finally someone with the same problem. The issue is not with the iso as I have installed twice from separate isos and tried an upgrade from 12.04 and none worked.  Any ideas on how to fix this?

---

### Post by khatkarrohit on 2014-04-18
> **sdowney717 said:**
> I would re-download and make a new liveusb, then reinstall.
there is a way to verify the integrity of the download, do that to know the files are ok.

If you have a working hard drive with working Ubuntu install on it, you can clone it and stick it in your PC and it will work. just keep 32 bit and 64 bit separated.
I have done things like that using clonezilla.

Just freshly installed. This time from DVD, Different ISO downloaded in windows and Ubuntu 12.04. Same problem.

Even if I boot Ubuntu Live this same problem persistes. Rhythmbox, Gnome-system-monitor does not work in live mode also.

I also tried installing disabling secure boot completely. In legacy mode the installation window dows not show up. Just a colored background with a bar shows up after booting ubuntu in legacy mode and no way to install in legacy mode.

---

### Post by khatkarrohit on 2014-04-18
> **Bradley_Ware said:**
> Finally someone with the same problem. The issue is not with the iso as I have installed twice from separate isos and tried an upgrade from 12.04 and none worked.  Any ideas on how to fix this?

Lets try installing [Ubuntu Gnome]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME"). Maybe some problem in Unity Windowing Manager. This Unity thing is bad from starting. This Unity thing should be purged. 
I tried to download Ubuntu Gnome using torrent and foud out even Transmission Bittorrent Client window is not visible.

---

### Post by sdowney717 on 2014-04-18
I do see the window, and get the same terminal you get.
```
boat@boat-MS-7529:~$ rhythmbox

(rhythmbox:20955): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

(rhythmbox:20955): GLib-GObject-CRITICAL **: object SoupServer 0x7f53280036c0 finalized while still in-construction

(rhythmbox:20955): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
```

This is how I install gnome

sudo apt-get install gnome

select lightdm when prompted.

Could it be a video driver issue causing a window to not appear?

Someone earlier pointed another poster to an updated video for intel driver set.

---

### Post by khatkarrohit on 2014-04-18
> **sdowney717 said:**
> Could it be a video driver issue causing a window to not appear?

Someone earlier pointed another poster to an updated video for intel driver set.

I tried Ubuntu Gnome and Gnome is also not working at all for me. Where can I find the new Intel driver set.

---

### Post by khatkarrohit on 2014-04-18
> **sdowney717 said:**
> Could it be a video driver issue causing a window to not appear?

Someone earlier pointed another poster to an updated video for intel driver set.

I tried installing Inel driver from their website. The drivers are for Ubuntu 13.10. I tried those drivers and they did not change anything.

Looks like I found problem. 
 			The problem is there because of two monitors  connected to my PC. Windows which are not displaying were displayed in  other monitor that was turned off. Wasted whole day. Making a Fresh  install.[IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by khatkarrohit on 2014-04-18
My problem is solved. The problem is there because of two monitors connected to my PC. Windows which are not displaying were displayed in other monitor that was turned off. Wasted whole day. Making a Fresh install.:)

---

### Post by Bradley_Ware on 2014-04-19
Thanks khatkarrohit. This solved my problem too.

---

### Post by khatkarrohit on 2014-04-20
The problem is Ubuntu 14.04 has disabled Workspace switcher by default.  Its hard to find on which monitor Window appeared on first time if other  monitor is off. Its better to turn on enable workspaces in settings to  avoid confusion.
Settings-->Appearance-->Behaviour.

---

### Post by benawhile on 2014-04-23
Oh Dear. That made me laugh out loud, but I bet you didn't think it was funny!

---

### Post by uxuntuone on 2014-08-29
Thanks! This had been bugging me for weeks!

---

