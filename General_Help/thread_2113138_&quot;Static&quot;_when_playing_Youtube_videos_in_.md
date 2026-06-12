---
title: "&quot;Static&quot; when playing Youtube videos in Chrome"
date: 2013-02-06
forum: General Help
---

### Post by GnuHouse on 2013-02-06
I'm running Ubuntu 12.07, Chrome 24.0.1312.57 (Official Build 178923), and Flash 11.5.31.137.

When I try watching Youtube videos in Chrome, the video looks like it has static on it, like when a TV channel has bad reception. Sound is okay, only the video has the issue.  I can use Flash on other site, and other streaming sites (like Twitch) with no issues.

Anyone else had this issue, or know how to solve it?

As an edit, the static does not stop when the video ends or when the video is paused.  The static continues to move, so to speak, so long as the video is open

---

### Post by WRStone on 2013-02-07
I'm seeing the same behavior.  One other tidbit:

Ads play without the video interference.

My system:

Dell Inspiron 1520
Ubuntu 12.10

 [wrstone@gallatin ~]$ uname -a
Linux gallatin 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Google Chrome:
Version 24.0.1312.69

---

### Post by dgmorris on 2013-02-08
You need to install a separate flash player and disable the player that is part of chrome. I copied the following solution from another forum:

Type about:plugins in the URL Bar. Then click on "Details". Disable the internal Flash plugin and use the plugin from the system (11.2)

The following is necessary to get Flash Player 11.2 working again in Chrome 20 (this worked for me on Ubuntu 12.04, anyway):

download Flash Player 11.2 (for "Select version to download...." choose "API for Ubuntu 10.04+)
manually install the plugin

sudo mkdir -p /opt/google/chrome/plugins
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /opt/google/chrome/plugins
Now if you visit chrome://plugins in your browser, you should see something like

Flash (4 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202

---

