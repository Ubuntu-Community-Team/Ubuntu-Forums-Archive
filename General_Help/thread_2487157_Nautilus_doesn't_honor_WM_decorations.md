---
title: "Nautilus doesn't honor WM decorations"
date: 2023-05-25
forum: General Help
---

### Post by TheFu on 2023-05-25
Running nautilus and there aren't any window decorations. No title. No borders.  How do I get window decorations back?

```
ii  nautilus       1:3.36.3-0ubuntu1.20.04.2 amd64
```

I'm on Ubuntu Server 20.04 with a WM-only setup, no DE.  Freshly installed this week. 
```
$ inxi -bz
System:    Kernel: 5.15.0-72-generic x86_64 bits: 64 [B]Desktop: FVWM2 2.6.8 
[/B]           Distro: Ubuntu **20.04.6** LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx 
           serial: <filter> UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD Ryzen 5 5600G with Radeon Graphics type: MT MCP speed: 4199 MHz 
           min/max: 1400/4200 MHz 
Graphics:  Device-1: AMD driver: amdgpu v: kernel 
           Display: server: X.Org 1.20.13 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-72-generic LLVM 12.0.0) 
           v: 4.6 Mesa 21.2.6 

```

The last few days, I've been trying to find a file manager that supports drag-n-drop of files into another program (AppImage) because the AppImage file-open dialog sucks .... and does with and without any DE.
Installed nautilus ... surprised me to have fewer dependencies than about 5 other options when I use
```
sudo apt install nautilus --no-install-recommends
```

I went through the preferences ... none of them have anything to allow the WM decorations.  Further, none of them can be toggled/changed.  What gives?  There aren't any Gnome apps or snaps installed.

Seems like a major bug to me.  All windows should be under the control of the chosen Window Manager.  That's a standard and fvwm supports the ICCCM standard.  Any ideas that don't involve bloat?

---

### Post by Holger_Gehrke on 2023-05-25
I don't know all the details, but AFAIK nautilus uses client side decorations by default - so it normally draws the title bar and the icons and other UI elements on it itself. So it probably tells the window manager not to decorate it - because it will do so itself -  and then doesn't get some kind of signal to do so and thinks that the window manager doesn't understand that hint and has already decorated it. Searching for "Gnome Nautilus Window decorations" on duckduckgo gives some old hits which tell you to set XDG_CURRENT_DESKTOP to the name of some desktop environment. The possible values should be the same as the [list of names for Desktop environments]("https://specifications.freedesktop.org/menu-spec/latest/apb.html") for the OnlyShowIn line in .desktop files.

Holger

---

### Post by TheFu on 2023-05-25
Thanks.  Seems that nautilus won't be standards compliant.
I tried setting the XDG_CURRENT_DESKTOP environment variable with 5 of the most likely to work options in that link. No difference.  Looking more and more like Gnome software is out for my tastes. 

Found this explanation:
> using the standard GTK header bar widget, so as far as I know it’s not possible to have the window manager responsible for decorations.
GTK toolkit gets in the way again?  Perhaps not.  
**Meld** is a GTK application and it happily shows the borders. Same for every other application I've run the last few days ... except nautilus.  Either nautilus is going out of their way to prevent the WM from doing what it is supposed to do OR every other gnome (and other) application is doing something special to allow the WM control over borders.  I'd bet it is the Nautilus team doing something, not the other way around.  Too bad.  Nautilus purged.  When gone, these packages aren't needed anymore either:
  ```
gnome-desktop3-data libcue2 libdee-1.0-4 libexempi8 libexiv2-27 libgexiv2-2
  libgnome-autoar-0-0 libgnome-desktop-3-19 libgsf-1-114 libgsf-1-common
  libnautilus-extension1a libtotem-plparser-common libtotem-plparser18
  libtracker-control-2.0-0 libtracker-miner-2.0-0 libtracker-sparql-2.0-0
  libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9
  tracker tracker-extract tracker-miner-fs
```

I'll find a solution, eventually.

---

### Post by #&amp;thj^% on 2023-05-25
> **TheFu said:**
> 

I'll find a solution, eventually.
If or when you do Please share, All I know is "libdecor" supports "xdg-decoration" and Wayland is built to not require something like xdg-decoration, but we’re at an impasse because I and maybe you too view that as a Bug and "They" view it as a feature.

So it doesn't really matter if either of us view it as a feature or bug. From the perspective of the window manager, decorations are still an optional thing just as they were in X11.

---

### Post by TheFu on 2023-05-25
Well, considering that I don't have many/any DE programs, the XDG stuff doesn't really work here.  I consider that a feature as well.  When I try to use Firefox-esr (inside a non-private firejail) with xdg-open, I get an error that Firefox is already open and not responding.

There are many things that I consider design flaws in all the current DEs.  Anything that looks like a DB rather than a config file is a bug to me.  dconf, gconf and whatever bus the DEs use are examples.  Don't get me wrong - I can see where most normal users just want stuff that works and I'm anti-bloat to a very high level.  I've thought about removing all the GUI and using the Suckless [https://suckless.org/](https://suckless.org/) programs instead.  For even me, the dwm is too little of a GUI.  That's saying something.  

No wayland here.  Maybe in 2024 I'll test my workflows again to see if they are still broken.  I expect they always will be, so I'll stay with X11 for another year, at least.
I have to day, the lack of bloat so far is nice:
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  **5.5G**   27G  17% /
/dev/nvme0n1p3                    ext4  672M  145M  479M  24% /boot
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01           ext4  9.8G  4.9G  4.4G  53% /home
/dev/mapper/vg01-tmp01            ext4  3.9G  988K  3.7G   1% /tmp
/dev/mapper/vg01-var01            ext4   20G  1.6G   17G   9% /var
/dev/mapper/vg01-libvirt--01      ext4  134G  **131G**     0 100% /var/lib/libvirt
```

Only the libvirt directory is bloated and that's because I have Win7 VM down there.  Check out / at only 5.5G.  I think there are less than 20 other programs still to be loaded.  I knew it could be done, being careful with dependencies. Who says that /boot needs to be 1G and EFI needs to be 500M?  Clearly not me.  Plenty of room in those partitions.

---

### Post by TheFu on 2023-05-25
**pcmanfm** is working.  It honors window borders, title, drag-n-drop and supports sftp. I did have to set an environment variable in the ~/.xinitrc for the DBUS, but with that, it is working crazy great and fast. 
The DBUS setting for me was:
```
export DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"
```
That's a named pipe, assuming for IPC. The pipe already existed.  Named pipes are handy.

BTW, thanks for the ideas folks.  I probably would have walked away and dealt with something else.   I need to get audio working in the browsers next, though it works perfect with mpv and mplayer on the system.

---

### Post by Holger_Gehrke on 2023-05-25
> **TheFu said:**
> 
The DBUS setting for me was:
```
export DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"
```
That's a named pipe, assuming for IPC. The pipe already existed.  Named pipes are handy.


D-Bus is IPC for desktop applications. There are usually at least two D-Bus instances, a system bus and a session bus per currently logged in user. There's a daemon at the other end of that pipe which will pass your program's messages to it's intended recipient. Pop-up notifications are done through D-Bus with another daemon waiting for messages to come in which it will then show. MPRIS (media player remote interface specification) is done through D-Bus, allowing other programs to control media players. Programs can be D-Bus activatable, meaning you send a message to a program that isn't running and the D-Bus daemon will start it and deliver the message to it ... And the bus allows introspection, there are calls you can make to find out what is connected to the bus under what names and what messages it will accept. There's a tool named D-Feet, which you can use to graphically explore the bus ...

Holger

---

### Post by TheFu on 2023-05-26
Thanks.  That's useful.  

I've used named pipes in my own code for IPC between a DB search application and a CAD system.  It was used to add drag-n-drop from the query results onto the CAD layout.  Clients loved it. The CAD software couldn't use network sockets, so we had to create little daemon that would receive the drop communication from the client system and put the message into the named-pipe on the CAD server.  Surprisingly simple.  Our application was a 4-teir CORBA app.  Nobody uses CORBA anymore (and haven't for 15 yrs, really. It was an attempt at a standard that few people wanted. It is hard to have a standard when the competing vendors all create extensions that aren't compatible.

Perhaps the MPRIS is why firefox and Brave won't play audio, but everything else I use does?  That's a different thread, assuming this hint doesn't let me solve it.

---

### Post by #&amp;thj^% on 2023-05-26
Thanks for the share @all

---

