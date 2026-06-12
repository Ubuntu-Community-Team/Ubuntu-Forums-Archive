---
title: "Ubuntu 16.04 LTS on Dell XPS, dual screens"
date: 2018-04-09
forum: General Help
---

### Post by bjfar on 2018-04-09
So I recently bought a Dell XPS 13 9370, which has a 4K "Ultra HD" screen (3840 x 2160), and I am trying to get something reasonable to work in my dual monitor setup. The second monitor has a much lower resolution, so out of the box there are issues where screen elements that are well proportioned for the laptop screen become enormous when moved to the second monitor.

My attempt to get around this is to run the following script:

```
#!/bin/bash
# Fix up the screen scaling and position for my LG external monitor

# Main trick; position of eDP1 (laptop screen) needs to be moved twice as far over
# due to the 2x scaling on the LG monitor
DP1w=1920
s=2 # Note, don't go to 3, will kill X or something. I guess that res is too high
xrandr --output DP1 --scale ${s}x${s} --pos 0x0 --output eDP1 --pos $(($s * $DP1w))x0
```

This seems to work fine for a while, however it is very unstable. For example if I disconnect the external monitor then Ubuntu apparently scales the size of my laptop display by 0.5, so it occupies only one quarter of the monitor. Reconnecting the external monitor then produces some bizarre overlapping desktop situation and my script is no longer the correct command to fix it. This disconnection/reconnection also sometimes just crashes Ubuntu. Also, when the computer hibernates and restores, the screen setup is often not restored correctly, and can also cause the system to lock up.

So I wonder if anyone has a better way to deal with this situation?

---

### Post by dragonfly41 on 2018-04-09
This is the second thread today where I suggest trying **x-tile** as a tiling GUI.

A [nearby thread]("https://ubuntuforums.org/showthread.php?t=2388862").

x-tile allows a grid of tiles to be configured and can extend tiles over dual monitors or workspaces.
Go to edit > preferences.

Here is the [developer's web site]("https://www.giuspen.com/x-tile/").

---

### Post by bjfar on 2018-04-17
Hmm, sounds like a nice tool, but the version in the standard repositories doesn't seem to work:

$ sudo apt install x-tile
[sudo] password for farmer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-94 linux-headers-4.4.0-94-generic linux-image-4.4.0-94-generic linux-image-extra-4.4.0-94-generic
  linux-signed-image-4.4.0-94-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  x-tile
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 78.4 kB of archives.
After this operation, 1,296 kB of additional disk space will be used.
Get:1 [http://mirror.as29550.net/archive.ubuntu.com](http://mirror.as29550.net/archive.ubuntu.com) xenial/universe amd64 x-tile all 2.5-3 [78.4 kB]
Fetched 78.4 kB in 0s (1,697 kB/s)
Selecting previously unselected package x-tile.
(Reading database ... 383847 files and directories currently installed.)
Preparing to unpack .../archives/x-tile_2.5-3_all.deb ...
Unpacking x-tile (2.5-3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up x-tile (2.5-3) ...


$ x-tile &
[1] 6995
$ GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
WM = Compiz
Traceback (most recent call last):
  File "/usr/bin/x-tile", line 66, in <module>
    x.launch_application()
  File "/usr/share/x-tile/modules/core.py", line 936, in launch_application
    self.init_from_gconf()
  File "/usr/share/x-tile/modules/core.py", line 503, in init_from_gconf
    self.status_icon_enable()
  File "/usr/share/x-tile/modules/core.py", line 363, in status_icon_enable
    self.ind = appindicator.Indicator("x-tile", "indicator-messages", appindicator.CATEGORY_APPLICATION_STATUS)
NameError: global name 'appindicator' is not defined

Any other ideas?

---

### Post by bjfar on 2018-04-17
Ah ok x-tile is still missing some python dependencies it seems. I had to install python-appindicator to get it to work, as in this old bug that they apparently still haven't fixed: [https://bugs.launchpad.net/ubuntu/+source/x-tile/+bug/1469200](https://bugs.launchpad.net/ubuntu/+source/x-tile/+bug/1469200)

Now I am having a fun time trying to squint to read the GUI which is absolutely teeny tiny on a HD screen...

---

### Post by bjfar on 2018-04-17
Ok I played with it a bit and I don't see how it can help with my problem. It looks like it tiles windows, not screens, and I don't see any way of adjusting the screen scaling parameters like in my xrandr example.

---

### Post by dragonfly41 on 2018-04-17
I'm sorry that this idea didn't work.

---

