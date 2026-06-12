---
title: "Some, not all programs take a LONG time to open"
date: 2023-04-10
forum: General Help
---

### Post by sofasurfer on 2023-04-10
Firefox initially takes a good 30 seconds to open when system is booted. Subsequent openings are normal fast. 
Nautilus, gedit, nemo do the same thing but seem to do it when opening them with sudo. 

Google-earth, brasero, zim and MANY others all open normally fast.
When I use linux MINT there are no delays in opening programs so I know this is a Ubuntu thing.

I use Ubuntu 20.04, 16g ram, 240g ssd, 100mbps internet connection. I don't thing isp has anything to do with it since text editor are strictly local.

Any idea how I can track down the process or step that is lagging behind?
I have tried using <$ strace nautilus>. I have it redirected to a file with ```
$ strace  nautilus 2>&1 | grep open > ~/Desktop/strace.txt
``` and with sudo as ```
$ sudo strace  nautilus 2>&1 | grep open > ~/Desktop/strace.txt
```
 but I have no idea how to read this file. If there was an option to maybe have each step (system call?) printed along with a execution time length maybe I could figure where the problem is.

Is there another method of diagnosing this issue? Looking for any help I can get.

I am posting this and then I will reboot and post the strace file from a fresh reopening of nautilus.

---

### Post by MAFoElffen on 2023-04-10
I think the difference is that in Ubuntu, as comparing with Mint, has Firefox installed as a Snap app, where Mint is apt. Snap apps are stored as SquashFS, so the first time you start them after a boot, it takes a short time to uncompress and mount the filesystem for it's use.

Installed as an apt binary install, it doesn't have to go through that initial 'unpacking' process for use. Linux Mint made a decision not to do Snap applications. So that is the difference their as I see it.

---

### Post by Holger_Gehrke on 2023-04-10
Firefox is so slow to start the first time because it's a snap. Snap packages are basically  compressed file systems that get mounted at boot and get decompressed when executing. Later executions go faster because of caching.

I don't know why nautilus takes a long time to start with sudo, but I do know you're not supposed to do this ... Instead try using the 'admin://' schema when giving nautilus a directory to work in for example 'admin:///usr/share/applications/'. Unless nautilus has changed even more than I know it has since I last used it you should be able to open a field for entering a location by hitting ctrl-L. Similar for nemo (and Thunar). Generally speaking, running graphical tools with sudo is a bad idea because it can end with these program changing the ownership of their configuration to 'root', making them unusable.

For editing files with root permissions it's better to use sudoedit. You can change the editor used for sudoedit by setting and exporting the variable SUDO_EDITOR to the path and name of your preferred editor like this:
```

export SUDO_EDITOR=/usr/bin/emacs

```
You can put your setting for SUDO_EDITOR in '~/.bashrc'.

Holger

---

### Post by sofasurfer on 2023-04-10
Here is my snap list...
```
 $ snap list
Name               Version           Rev    Tracking         Publisher      Notes
bare               1.0               5      latest/stable    canonical&#10003;     base
chromium           111.0.5563.146    2415   latest/stable    canonical&#10003;     -
core18             20230320          2721   latest/stable    canonical&#10003;     base
core20             20230308          1852   latest/stable    canonical&#10003;     base
core22             20230325          607    latest/stable    canonical&#10003;     base
cups               2.4.2-5           872    latest/stable    openprinting&#10003;  -
gnome-3-34-1804    0+git.3556cb3     90     latest/stable/&#8230;  canonical&#10003;     -
gnome-3-38-2004    0+git.6f39565     137    latest/stable    canonical&#10003;     -
gtk-common-themes  0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store         41.3-66-gfe1e325  638    latest/stable/&#8230;  canonical&#10003;     -$ apt list firefox
Listing... Done
firefox/focal-updates,focal-security,now 111.0.1+build2-0ubuntu0.20.04.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
snapd              2.58.3            18596  latest/stable    canonical&#10003;     snapd
yt-dlp             ab92d8651         233    latest/stable    degville       -

```
 
Here is apt list for Firefox ```
 $ apt list firefox
Listing... Done
firefox/focal-updates,focal-security,now 111.0.1+build2-0ubuntu0.20.04.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it 
```

---

### Post by MAFoElffen on 2023-04-11
==> 20.04.x...

RE: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1878666](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1878666)

---

