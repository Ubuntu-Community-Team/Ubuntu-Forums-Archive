---
title: "Can't Remove app from Ubuntu 20.04"
date: 2020-11-17
forum: General Help
---

### Post by jgwphd on 2020-11-17
I can seem to remove an app. I have a zoom (version 3.5.382 ...) app in the "show applications" list (9 dots at the bottom of the launcher).  When I left click on it it starts up and works. When I right click and select details I get "Sorry! There are no details for that application"  I am trying to delete this zoom app and I can't find it (see error msgs below). I must be doing something wrong. I tried the software center and it's not there (actually the Software Center Not Showing any installed Apps  ...i suspect that is another problem. I did the command sudo apt install --reinstall gnome-software and that didn't help). Leaving the software center out of this, how can I find this zoom app in the system and get rid of it?  Many thanks for any assistance.

jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **sudo apt policy zoom**
N: Unable to locate package zoom
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **sudo apt remove zoom**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package zoom

In the terminal I also did:

jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **grep -R Zoom /usr/share/applications ~/.local/share/applications**
/usr/share/applications/gnome-universal-access-panel.desktop:Keywords=Keyboard;Mouse;a11y;Accessibility;Contrast;Cursor;Sound;Zoom;Screen;Reader;big;high;large;text;font;size;AccessX;Sticky;Keys;Slow;Bounce;Mouse;Double;click;Delay;Speed;Assist;Repeat;Blink;visual;hearing;audio;typing;
/usr/share/applications/gnome-keyboard-panel.desktop:Keywords=Shortcut;Workspace;Window;Resize;Zoom;Contrast;Input;Source;Lock;Volume;
jgw@jgw-HP-EliteBook-8460p:~/Desktop$

---

### Post by deadflowr on 2020-11-17
check if it's a deb package or a snap package with
```
dpkg -l| grep zoom
snap list
```

---

### Post by T6&amp;sfpER35% on 2020-11-17
list of applications
```
ls -l /usr/share/applications
```
look for zoom ,it'll end in .desktop
copy that file name
to remove an application file
```
sudo rm /usr/share/applications/**paste-the-filename-here**
```
 to be safe run this after deletion
```
sudo apt autoremove
```
and 
```
sudo apt autoremove --purge
```

---

### Post by deadflowr on 2020-11-17
Don't remove files like that, it can break the packaging system.
Use the proper packaging tools like apt and dpkg to remove packages.

---

### Post by jgwphd on 2020-11-17
Command output:

```
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **dpkg -l| grep zoom**
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **snap list**
Name                             Version                     Rev    Tracking         Publisher   Notes
chromium                         86.0.4240.198               1399   latest/stable    canonical&#10003;  -
core                             16-2.47.1                   10185  latest/stable    canonical&#10003;  core
core18                           20200929                    1932   latest/stable    canonical&#10003;  base
gnome-3-26-1604                  3.26.0.20200529             100    latest/stable/&#8230;  canonical&#10003;  -
gnome-3-28-1804                  3.28.0-19-g98f9e67.98f9e67  145    latest/stable    canonical&#10003;  -
gnome-3-34-1804                  0+git.3556cb3               60     latest/stable    canonical&#10003;  -
gnome-system-monitor             3.36.0-12-g35f88a56d7       148    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes                0.1-36-gc75f853             1506   latest/stable/&#8230;  canonical&#10003;  -
indicator-sensors                1.2                         291    latest/stable    alexmurray  -
kbreakout                        20.04.0                     52     latest/stable    kde&#10003;        -
kde-frameworks-5-core18          5.61.0                      32     latest/stable    kde&#10003;        -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4      latest/stable    kde&#10003;        -
skype                            8.66.0.74                   159    latest/stable    skype&#10003;      classic
snap-store                       3.36.0-82-g80486d0          481    latest/stable/&#8230;  canonical&#10003;  -
```
```
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **ls -l /usr/share/applications**
total 860
-rw-r--r-- 1 root root   291 Nov 10 15:03 apport-gtk.desktop
-rw-r--r-- 1 root root   125 May 19  2016 apturl.desktop
-rw-r--r-- 1 root root   484 Oct  1 11:15 bluetooth-sendto.desktop
-rw-r--r-- 1 root root 12478 Sep 18 10:14 chromium-browser.desktop
-rw-r--r-- 1 root root 13685 Nov 11 15:39 defaults.list
-rw-r--r-- 1 root root   210 Jul 25  2017 etcher-electron.desktop
-rw-r--r-- 1 root root   257 Aug 17 13:26 evolution-calendar.desktop
-rw-r--r-- 1 root root  9261 Nov  9 09:31 firefox.desktop
-rw-r--r-- 1 root root   968 Oct 29 14:54 flash-player-properties.desktop
-rw-r--r-- 1 root root   211 Jan 13  2018 frozen-bubble.desktop
-rw-r--r-- 1 root root   303 Mar 19  2020 gcr-prompter.desktop
-rw-r--r-- 1 root root   611 Mar 19  2020 gcr-viewer.desktop
-rw-r--r-- 1 root root   367 Mar 11  2019 gdebi.desktop
-rw-r--r-- 1 root root   227 Feb 28  2020 geoclue-demo-agent.desktop
-rw-r--r-- 1 root root   509 Feb 21  2019 gkbd-keyboard-display.desktop
-rw-r--r-- 1 root root   721 Sep 24 11:03 gnome-applications-panel.desktop
-rw-r--r-- 1 root root   667 Sep 24 11:03 gnome-background-panel.desktop
-rw-r--r-- 1 root root   817 Sep 24 11:03 gnome-bluetooth-panel.desktop
-rw-r--r-- 1 root root   821 Sep 24 11:03 gnome-camera-panel.desktop
-rw-r--r-- 1 root root   907 Sep 24 11:03 gnome-color-panel.desktop
-rw-r--r-- 1 root root   766 Sep 24 11:03 gnome-connectivity-panel.desktop
-rw-r--r-- 1 root root   637 Sep 24 11:03 gnome-control-center.desktop
-rw-r--r-- 1 root root   715 Sep 24 11:03 gnome-datetime-panel.desktop
-rw-r--r-- 1 root root   780 Sep 24 11:03 gnome-default-apps-panel.desktop
-rw-r--r-- 1 root root   829 Sep 24 11:03 gnome-diagnostics-panel.desktop
-rw-r--r-- 1 root root   386 Mar 24  2020 gnome-disk-image-mounter.desktop
-rw-r--r-- 1 root root   447 Mar 24  2020 gnome-disk-image-writer.desktop
-rw-r--r-- 1 root root   890 Sep 24 11:03 gnome-display-panel.desktop
-rw-r--r-- 1 root root  1001 Sep 24 11:03 gnome-info-overview-panel.desktop
lrwxrwxrwx 1 root root    55 Oct 27 14:11 gnome-initial-setup.desktop -> ../gdm/greeter/applications/gnome-initial-setup.desktop
-rw-r--r-- 1 root root   862 Sep 24 11:03 gnome-keyboard-panel.desktop
-rw-r--r-- 1 root root   494 Sep 27 16:07 gnome-language-selector.desktop
-rw-r--r-- 1 root root   858 Sep 24 11:03 gnome-location-panel.desktop
-rw-r--r-- 1 root root   834 Sep 24 11:03 gnome-lock-panel.desktop
-rw-r--r-- 1 root root   844 Sep 24 11:03 gnome-microphone-panel.desktop
-rw-r--r-- 1 root root   854 Sep 24 11:03 gnome-mouse-panel.desktop
-rw-r--r-- 1 root root   816 Sep 24 11:03 gnome-network-panel.desktop
-rw-r--r-- 1 root root   896 Sep 24 11:03 gnome-notifications-panel.desktop
-rw-r--r-- 1 root root  1002 Sep 24 11:03 gnome-online-accounts-panel.desktop
-rw-r--r-- 1 root root   924 Sep 24 11:03 gnome-power-panel.desktop
-rw-r--r-- 1 root root   816 Sep 24 11:03 gnome-printers-panel.desktop
-rw-r--r-- 1 root root   845 Sep 24 11:03 gnome-region-panel.desktop
-rw-r--r-- 1 root root   845 Sep 24 11:03 gnome-removable-media-panel.desktop
-rw-r--r-- 1 root root   836 Sep 24 11:03 gnome-search-panel.desktop
-rw-r--r-- 1 root root   476 Mar 26  2020 gnome-session-properties.desktop
-rw-r--r-- 1 root root   749 Sep 24 11:03 gnome-sharing-panel.desktop
-rw-r--r-- 1 root root   612 Jun 16 20:34 gnome-software-local-file.desktop
-rw-r--r-- 1 root root   852 Sep 24 11:03 gnome-sound-panel.desktop
-rw-r--r-- 1 root root   791 Mar 10  2020 gnome-system-monitor.desktop
-rw-r--r-- 1 root root   764 Mar 10  2020 gnome-system-monitor-kde.desktop
-rw-r--r-- 1 root root   778 Sep 24 11:03 gnome-thunderbolt-panel.desktop
-rw-r--r-- 1 root root   594 Sep 24 11:03 gnome-ubuntu-panel.desktop
-rw-r--r-- 1 root root  1014 Sep 24 11:03 gnome-universal-access-panel.desktop
-rw-r--r-- 1 root root   838 Sep 24 11:03 gnome-usage-panel.desktop
-rw-r--r-- 1 root root   829 Sep 24 11:03 gnome-user-accounts-panel.desktop
-rw-r--r-- 1 root root   817 Sep 24 11:03 gnome-wacom-panel.desktop
-rw-r--r-- 1 root root   808 Sep 24 11:03 gnome-wifi-panel.desktop
-rw-r--r-- 1 root root  8536 Nov 10 21:36 google-chrome.desktop
-rw-r--r-- 1 root root   397 Jul  1 12:55 google-earth-pro.desktop
-rw-r--r-- 1 root root 12834 Mar 21  2020 gparted.desktop
-rw-r--r-- 1 root root   878 Mar 22  2020 gsmartcontrol.desktop
-rw-r--r-- 1 root root   307 Apr  1  2020 hp-fab.desktop
-rw-r--r-- 1 root root   330 Apr  1  2020 hplip.desktop
-rw-r--r-- 1 root root   283 Apr  1  2020 hplip-kubuntu.desktop
-rw-r--r-- 1 root root   423 Jan 30  2020 hplj1020.desktop
-rw-r--r-- 1 root root   297 Apr  1  2020 hp-sendfax.desktop
-rw-r--r-- 1 root root   177 Nov 12  2019 hp-uiscan.desktop
-rw-r--r-- 1 root root   205 Feb 16  2020 ibus-setup-table.desktop
-rw-r--r-- 1 root root  1034 Oct 28 12:33 im-config.desktop
-rw-r--r-- 1 root root   217 Oct 10  2019 info.desktop
-rw-r--r-- 1 root root  1521 Mar  7  2020 ktelnetservice5.desktop
-rw-r--r-- 1 root root 22656 Aug 24 18:58 libreoffice-calc.desktop
-rw-r--r-- 1 root root 19686 Aug 24 18:58 libreoffice-draw.desktop
-rw-r--r-- 1 root root 22768 Aug 24 18:58 libreoffice-impress.desktop
-rw-r--r-- 1 root root 18554 Aug 24 18:58 libreoffice-math.desktop
-rw-r--r-- 1 root root 21355 Aug 24 18:58 libreoffice-startcenter.desktop
-rw-r--r-- 1 root root 21353 Aug 24 18:58 libreoffice-writer.desktop
-rw-r--r-- 1 root root  4709 Aug 24 18:58 libreoffice-xsltfilter.desktop
-rw-r--r-- 1 root root 29127 Nov 17 13:37 mimeinfo.cache
-rw-r--r-- 1 root root   494 Sep 23 16:03 mutter.desktop
-rw-r--r-- 1 root root   353 Jun  2 11:03 nautilus-autorun-software.desktop
-rw-r--r-- 1 root root   350 Jul 29 17:09 nm-applet.desktop
-rw-r--r-- 1 root root   464 Jul 29 17:09 nm-connection-editor.desktop
-rw-r--r-- 1 root root   216 Dec 27  2018 notification-daemon.desktop
-rw-r--r-- 1 root root   159 Jul  1 08:47 org.freedesktop.IBus.Panel.Emojier.desktop
-rw-r--r-- 1 root root   181 Jul  1 08:47 org.freedesktop.IBus.Panel.Extension.Gtk3.desktop
-rw-r--r-- 1 root root   339 Jul  1 08:47 org.freedesktop.IBus.Setup.desktop
-rw-r--r-- 1 root root   635 Sep 12  2019 org.gnome.baobab.desktop
-rw-r--r-- 1 root root   669 Mar  9  2020 org.gnome.Calculator.desktop
-rw-r--r-- 1 root root   531 Jun 22 09:20 org.gnome.Calendar.desktop
-rw-r--r-- 1 root root   602 Mar  8  2020 org.gnome.Characters.desktop
-rw-r--r-- 1 root root   567 Sep 24 15:37 org.gnome.Cheese.desktop
-rw-r--r-- 1 root root   265 Mar 21  2018 org.gnome.ChromeGnomeShell.desktop
-rw-r--r-- 1 root root   634 Jun 15 09:31 org.gnome.DejaDup.desktop
-rw-r--r-- 1 root root   659 Mar 24  2020 org.gnome.DiskUtility.desktop
-rw-r--r-- 1 root root  1138 Jul  6 10:17 org.gnome.eog.desktop
-rw-r--r-- 1 root root  1307 Jul  7 09:20 org.gnome.Evince.desktop
-rw-r--r-- 1 root root   401 Jul  7 09:20 org.gnome.Evince-previewer.desktop
-rw-r--r-- 1 root root   480 Jul  7 06:38 org.gnome.Evolution-alarm-notify.desktop
-rw-r--r-- 1 root root   344 Aug 17 13:26 org.gnome.Extensions.desktop
-rw-r--r-- 1 root root  2153 Sep 24 14:53 org.gnome.FileRoller.desktop
-rw-r--r-- 1 root root   848 Feb 24  2020 org.gnome.font-viewer.desktop
-rw-r--r-- 1 root root   749 Apr 28  2020 org.gnome.gedit.desktop
-rw-r--r-- 1 root root   565 May 21 09:29 org.gnome.Logs.desktop
-rw-r--r-- 1 root root   529 Mar 10  2020 org.gnome.Mahjongg.desktop
-rw-r--rSometimes they stay around even after reporting and keep loading over and ver the same reports-- 1 root root   704 Mar 28  2020 org.gnome.Mines.desktop
-rw-r--r-- 1 root root  1211 Jun  2 11:03 org.gnome.Nautilus.desktop
-rw-r--r-- 1 root root   741 Sep 25  2019 org.gnome.PowerStats.desktop
-rw-r--r-- 1 root root  1109 Mar 12  2020 org.gnome.Screenshot.desktop
-rw-r--r-- 1 root root   597 Mar 13  2020 org.gnome.seahorse.Application.desktop
-rw-r--r-- 1 root root   388 Aug 17 13:26 org.gnome.Shell.desktop
-rw-r--r-- 1 root root   357 Aug 17 13:26 org.gnome.Shell.Extensions.desktop
-rw-r--r-- 1 root root   326 Aug 17 13:26 org.gnome.Shell.PortalHelper.desktop
-rw-r--r-- 1 root root   845 Jun 16 20:34 org.gnome.Software.desktop
-rw-r--r-- 1 root root   514 Mar 10  2020 org.gnome.Sudoku.desktop
-rw-r--r-- 1 root root   549 Jun 10 21:40 org.gnome.Terminal.desktop
-rw-r--r-- 1 root root   496 Sep 30  2019 org.gnome.Todo.desktop
-rw-r--r-- 1 root root  3623 Feb 25  2020 org.gnome.Totem.desktop
-rw-r--r-- 1 root root   599 Apr  6  2020 org.gnome.tweaks.desktop
-rw-r--r-- 1 root root  6460 Mar  5  2020 org.kde.k3b.desktop
-rw-r--r-- 1 root root  6699 Feb 29  2020 org.kde.keditbookmarks.desktop
-rw-r--r-- 1 root root  8699 Aug  4  2019 org.qbittorrent.qBittorrent.desktop
-rw-r--r-- 1 root root  5708 Apr 12  2020 org.remmina.Remmina.desktop
-rw-r--r-- 1 root root   264 Nov  4 12:27 piavpn.desktop
-rw-r--r-- 1 root root   302 Aug 12  2019 psensor.desktop
-rw-r--r-- 1 root root   220 Aug  4 07:16 python2.7.desktop
-rw-r--r-- 1 root root   220 Jul 28 08:59 python3.8.desktop
-rw-r--r-- 1 root root   588 Apr 12  2020 remmina-file.desktop
-rw-r--r-- 1 root root   254 Apr  8  2020 remmina-gnome.desktop
-rw-r--r-- 1 root root  1236 Jan 25  2020 rhythmbox.desktop
-rw-r--r-- 1 root root   632 Jan 25  2020 rhythmbox-device.desktop
-rw-r--r-- 1 root root   529 Mar 11  2020 rygel.desktop
-rw-r--r-- 1 root root   774 Jun 10 09:18 shotwell.desktop
-rw-r--r-- 1 root root  1128 Jun 10 09:18 shotwell-viewer.desktop
-rw-r--r-- 1 root root   528 Jun 16 23:46 simple-scan.desktop
-rw-r--r-- 1 root root   218 Oct  8 03:30 snap-handle-link.desktop
-rw-r--r-- 1 root root   362 Aug  7 09:15 software-properties-drivers.desktop
-rw-r--r-- 1 root root   580 Aug  7 09:15 software-properties-gtk.desktop
-rw-r--r-- 1 root root   337 Aug  7 09:15 software-properties-livepatch.desktop
-rw-r--r-- 1 root root   537 Jul 26  2019 solaar.desktop
-rw-r--r-- 1 root root   447 Sep 14  2019 sol.desktop
-rw-r--r-- 1 root root   318 Feb 28  2020 synaptic.desktop
-rw-r--r-- 1 root root   518 Nov  3 02:31 system-config-printer.desktop
-rw-r--r-- 1 root root 10062 Jul  1 10:11 thunderbird.desktop
-rw-r--r-- 1 root root  1089 Mar 15  2020 timeshift-gtk.desktop
-rw-r--r-- 1 root root  4493 Mar 25  2020 transmission-gtk.desktop
-rw-r--r-- 1 root root   302 Jun  3 13:18 update-manager.desktop
-rw-r--r-- 1 root root   288 Jul  2  2019 usb-creator-gtk.desktop
-rw-r--r-- 1 root root  4790 Apr 15  2020 vim.desktop
-rw-r--r-- 1 root root   354 Oct  6 10:33 vino-server.desktop
-rw-r--r-- 1 root root 11183 Apr  9  2020 vlc.desktop
-rw-r--r-- 1 root root  1226 Feb 24  2020 xdg-desktop-portal-gtk.desktop
-rw-r--r-- 1 root root  7553 Mar 15  2020 xfburn.desktop
-rw-r--r-- 1 root root  1406 Feb 10  2020 xsane.desktop
-rw-r--r-- 1 root root   614 Apr  7  2020 yelp.desktop
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ 
```

What next?   ...I want you to know I appreciate your assistance. 

BTW, when I click on the app icon in applications, how do I know it's called "zoom" internally in the system.

---

### Post by T6&amp;sfpER35% on 2020-11-17
> [COLOR=#000000]Don't remove files like that[/COLOR]
oops sorry , i had trouble before getting rid of menu items after deletion , and that was the advice i got , it worked everytime and nothing broke ,maybe i'm just lucky lol

---

### Post by jgwphd on 2020-11-17
This is not a menu item problem. The app exists. When I click on the icon it starts a zoom app someplace in the system and how do I know it's called "zoom" internally in the system. Is their an alias involved and if so how do I find out?

---

### Post by T6&amp;sfpER35% on 2020-11-17
my bad , misunderstood 
ignore my post then

---

### Post by T6&amp;sfpER35% on 2020-11-17
how did you install the app? through terminal or deb file or software centre ?

---

### Post by deadflowr on 2020-11-17
Well, it's not listed as a snap or an apt.
Did you setup flatpaks?

The version installed is really old too.
current version is 5.4xxxxx

Snap [s]and apt[/s] would have updated it to the current version.
But flatpak's would not unless manually done so by you.
Edit: the apt version wouldn't update either as it doesn't add any zoom repository to update from.
So scratch that.

Edit:
The only other thing I can think of for it would be a web browser app launcher or something.

oh, or an appimage like this
[https://appimage.github.io/Zoom/]("https://appimage.github.io/Zoom/")
appimages would also require you to manually update it yourself, too.

---

### Post by jgwphd on 2020-11-17
I had the zoom apt on my Ubuntu system from some time. two years or longer maybe. I have been upgrading multiple-times from 18.10 and somewhere along the way I got this zoom apt. I might have installed it from some zoom website commands but I don't remember. 

Someone asked about "flatpaks" - see command below.. 

jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **sudo apt install flatpak**
[sudo] password for jgw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flatpak is already the newest version (1.6.5-0ubuntu0.1).
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ 

I checked the apps in chrome and chromium (chrome://apps) and it is not listed as a browser app for these two browsers. I don't see it in firefox extensions, themes or plugins.

How hard can it be to rid of a working app in Ubuntu "show applications" menu????    :-)

---

### Post by deadflowr on 2020-11-17
> flatpak is already the newest version (1.6.5-0ubuntu0.1).
Check 
```
flatpak list --app
```

With so many different versions it can be we will figure out which it is.

---

### Post by jgwphd on 2020-11-17
command output

jgw@jgw-HP-EliteBook-8460p:~/Desktop$ **flatpak list --app**
Name                        Application ID                            Version                  Branch          Installation
Adobe Flash Player          com.adobe.Flash-Player-Projector          32.0.0.270               stable          system
Zoom                        us.zoom.Zoom                              3.5.383291.0407          stable          system
jgw@jgw-HP-EliteBook-8460p:~/Desktop$ 

Ok, it looks like we found it ...yeah!!!!   Now, how do I get rid of it?

---

### Post by deadflowr on 2020-11-17
Should be
```
flatpak uninstall us.zoom.Zoom
```
See this for full flatpak howto documentation:
[https://docs.flatpak.org/en/latest/using-flatpak.html]("https://docs.flatpak.org/en/latest/using-flatpak.html")

---

### Post by jgwphd on 2020-11-17
That did it. Thanks for the flatpak reference (I read the "Using Flatpak" section already). I appreciate all your assistance. Many many thanks!!!

---

