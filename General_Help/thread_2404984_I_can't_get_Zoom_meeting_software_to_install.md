---
title: "I can't get Zoom meeting software to install"
date: 2018-10-31
forum: General Help
---

### Post by sharpdrop on 2018-10-31
I have gone to the site and downloaded the 64 bit deb installer. When I click on the run option in Chromium it opens the software store, I press the install button, enter my password, and nothing happens; it just goes back to the install window. I am running xubuntu 18.04 on an Asus Q505U with a Intel Core I5 8th gen processor.

---

### Post by ajgreeny on 2018-10-31
I'm confused; are you trying to run the .deb file in chromium or have you installed the zoom.deb in the usual way and it will not run in chromium?

I must add that I have no idea what this zoom is expected to do so please enlighten us more; there may be other ways to achieve what you want.

---

### Post by howefield on 2018-10-31
Assuming that the file you have downloaded is called zoom_amd64.deb and is downloaded to the default folder, ie the Downloads folder.

Open a terminal and use the following command, but substituting your username instead of mine in the path

```
sudo apt install /home/hugh/Downloads/zoom_amd64.deb
```

Should see something like the following...

```
sudo apt install /home/hugh/Downloads/zoom_amd64.deb
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'zoom' instead of '/home/hugh/Downloads/zoom_amd64.deb'
The following additional packages will be installed:
  libgl1-mesa-glx libxcb-xtest0
The following NEW packages will be installed
  libgl1-mesa-glx libxcb-xtest0 zoom
0 to upgrade, 3 to newly install, 0 to remove and 27 not to upgrade.
Need to get 8,572 B/65.5 MB of archives.
After this operation, 243 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu cosmic/main amd64 libgl1-mesa-glx amd64 18.2.2-0ubuntu1 [3,776 B]
Get:2 http://gb.archive.ubuntu.com/ubuntu cosmic/main amd64 libxcb-xtest0 amd64 1.13.1-1 [4,796 B]
Get:3 /Data/Downloads/zoom_amd64.deb zoom amd64 2.4.129780.0915 [65.5 MB]
Fetched 8,572 B in 2s (3,451 B/s)
Selecting previously unselected package libgl1-mesa-glx:amd64.
(Reading database ... 175302 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-glx_18.2.2-0ubuntu1_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (18.2.2-0ubuntu1) ...
Selecting previously unselected package libxcb-xtest0:amd64.
Preparing to unpack .../libxcb-xtest0_1.13.1-1_amd64.deb ...
Unpacking libxcb-xtest0:amd64 (1.13.1-1) ...
Selecting previously unselected package zoom.
Preparing to unpack /Data/Downloads/zoom_amd64.deb ...
Unpacking zoom (2.4.129780.0915) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up libxcb-xtest0:amd64 (1.13.1-1) ...
Processing triggers for desktop-file-utils (0.23-3ubuntu2) ...
Processing triggers for libc-bin (2.28-0ubuntu1) ...
Setting up libgl1-mesa-glx:amd64 (18.2.2-0ubuntu1) ...
Processing triggers for shared-mime-info (1.10-1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu2) ...
Setting up zoom (2.4.129780.0915) ...
run post install script, action is configure...
```

Then load the application from the start menu.

---

### Post by sharpdrop on 2018-11-27
Sorry for my tardiness, I apparently didn't subscribe to my own post.

@ajgreeny- Zoom is a videoconferencing service with a downloadable app that is the only way I can participate in the live production of my favorite Linux podcast "Destination Linux" of which I am a proud patron!

@howefield- I will give it a try just as soon as I can. Thank you so much in advance!

---

