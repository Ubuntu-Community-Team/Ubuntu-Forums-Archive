---
title: "Corrupt graphics in Firefox using AMD embedded graphics"
date: 2024-02-17
forum: General Help
---

### Post by peterx14 on 2024-02-17
Hi all,

This machine has been working perfectly well, but today I notice that Firefox shows corrupt graphics; although even during login, there's a momentary glitch when it paints the screen initially... however, it all otherwise looks fine.

Mobo: MSI A320M-A Pro M2
CPU: AMD 3000G
RAM: 16GB

I'm running Xubuntu with an XFCE desktop on X11.

Attached is a Firefox screenshot. It's got BBC News as it's home page, so you can kind of see the headlines.

I've booting using the previous kernel (5.15.0-91) and it's still the same... but I can't be sure when this issue first appeared, so perhaps it was the previous-previous kernel?!

Apt is fully up-to-date, as are Snaps. I believe Firefox is running as a Snap.

---

### Post by #&amp;thj^% on 2024-02-17
Is there any nVidia involved?
```
apt policy  mesa-va-drivers
```
If that is installed already, then try these steps below.
Firstly, open Firefox and go to about:config in url bar. Click on &#8220;Accept the Risk and Continue&#8221;. Then search for following keys, enable or disable them one by one:
[list]
    [*]media.ffmpeg.vaapi.enabled set to true
    [*]media.ffvpx.enabled set to false.
    [*]media.rdd-vpx.enabled set to false.
    [*]media.navigator.mediadatadecoder_vpx_enabled set to true.[/list]
    If you experience page crashes, try setting security.sandbox.content.level to 0.

---

### Post by peterx14 on 2024-02-17
No nVidia! I did wonder myself and checked, but the only "Hardware Driver" is for the Wifi. I think the AMD 3000G has graphics onboard.
```

$ apt policy mesa-va-drivers 
mesa-va-drivers:
  Installed: 23.2.1-1ubuntu3.1~22.04.2
  Candidate: 23.2.1-1ubuntu3.1~22.04.2
  Version table:
 *** 23.2.1-1ubuntu3.1~22.04.2 500 (phased 90%)
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     22.0.1-1ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
I'd try changing about:config in Firefox except I can't see anything (see screenshot). I know to use ctrl-L to set keyboard focus to the address bar, but even when typing "about:config" blindly into it and hitting return, I still can't see anything. :(

---

### Post by #&amp;thj^% on 2024-02-17
They have changed the look in "about:config" just add what I've shown in the list of items.
See Screenshots. Don't follow my settings seen in the scrteenshots, but try the suggestions first.

---

### Post by peterx14 on 2024-02-17
I started Firefox from the command line and it says:
```

$ firefox
[Parent 4415, Main Thread] WARNING: Failed to mkdir /home/pryan/snap/firefox/3779/.config/ibus/bus: Not a directory: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox:4415): IBUS-WARNING **: 17:17:29.789: Failed to mkdir /home/pryan/snap/firefox/3779/.config/ibus/bus: Not a directory
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment

```
of-course, this might be what it normally says during startup!!

---

### Post by #&amp;thj^% on 2024-02-17
Yep confirmed your running firefox as a snap

---

### Post by peterx14 on 2024-02-17
As mentioned already, I can't get into Firefox at all... the interface is entirely corrupt!! Thus, I can't change about:config settings there.

---

### Post by #&amp;thj^% on 2024-02-17
Well try a new profile then.
```
firefox -P
```
Seems like something is amiss.

---

### Post by peterx14 on 2024-02-17
In the meantime... I'd rebooted into Safe Mode (the OS not the browser) but that just boots up in text mode before offering me options to deal with various OS issues, or to just restart into the regular desktop... so I did that because there's no package or filesystem corruption (that I'm aware of anyway).

BUT that didn't reboot, it just seems to *continue* to start the desktop. So it was particularly quick... and, oddly, it defaulted by wallpaper. But more interestingly, Firefox was fine!

So I restarted and it booted as normal... but this time I got my normal wallpaper and Firefox was corrupt again!

At *this* point I tried creating a new profile as you suggested, using "firefox -P" but that popup up a dialogue window that would allow me to create a new profile or rename an existing one... but that window was itself corrupt! I believe I cancelled that.
But then I renamed out ~/snap/firefox to ~/snap/firefox-old and started Firefox again. This time I got what looked like a fresh Firefox startup page... but it was also corrupt.

I *think* that maybe it's something with the OS itself that's at fault, and Firefox and/or snaps particularly don't work with it. This is in part based on how when I first login, there's a "glitch" which does show some corruption on screen, but it disappears pretty much straight away.

---

### Post by peterx14 on 2024-02-17
^Recovery Mode (not Safe Mode!)

Okay, so I booted back into Recovery Mode - and then just booted into the desktop, and once again, it defaults my wallpaper... and Firefox works. Starting Firefox from the command line this time yeilds:
```

$ firefox
update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/local/share/doc /usr/local/share/doc none bind,ro 0 0): cannot open directory "/usr/local/share": permission denied
[Parent 2117, Main Thread] WARNING: Failed to mkdir /home/pryan/snap/firefox/3779/.config/ibus/bus: Not a directory: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox:2117): IBUS-WARNING **: 17:56:27.302: Failed to mkdir /home/pryan/snap/firefox/3779/.config/ibus/bus: Not a directory

```

---

### Post by #&amp;thj^% on 2024-02-17
What shows with:
```

ls /home/pryan/.config/ibus/bus
```
This smells like using sudo with a GUI

---

### Post by peterx14 on 2024-02-17
There's no "ibus" dir within ~/.config
```

~$ find -iname 'ibus*'
./snap/firefox/3728/.config/ibus
./snap/firefox/3779/.config/ibus

```
ahhh.... although the ibus within the snap dir contains a "bus" symlink to [FONT=Courier New]/home/pryan/.config/ibus/bus [/FONT]<-- which is obviously a broken link.

Although... (1). I don't think the ibus/bus has disappeared, but never existed in this desktop environment? and (2). Even when I boot into Recovery Mode and Firefox works, I guess the same warning about ibus/bus not being a dir.

Possibly this part of the message (when Firefox doesn't work) is related to it?
```

ATTENTION: default value of option mesa_glthread overridden by environment.

```

---

### Post by #&amp;thj^% on 2024-02-17
A proper return for a snap firefox will look like:
```
 [COLOR="#B22222"]env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/firefox_firefox.desktop /snap/bin/firefox %u[/COLOR]
[163447, Main Thread] WARNING: GTK+ module /snap/firefox/3779/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox:163447): Gtk-WARNING **: 11:51:57.249: GTK+ module /snap/firefox/3779/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 11:51:57.249: Failed to load module "canberra-gtk-module"
[Parent 163447, Main Thread] WARNING: open /home/me/snap/firefox/3779/.config/ibus/bus failed: Permission denied: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox:163447): IBUS-WARNING **: 11:51:57.400: open /home/me/snap/firefox/3779/.config/ibus/bus failed: Permission denied
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.

```
Please try:
```
sudo chown root:root /home/pryan/.config/ibus/bus

```
And start firefox again.
BTW
> **peterx14 said:**
> There's no "ibus" dir within ~/.config
It's there with the proper path
```
ls /home/me/.config/ibus/bus
55b959beaf3c4e8c885de71ed85401c1-unix-0

```

---

### Post by #&amp;thj^% on 2024-02-17
Firefox relies on ibus:
```
find -iname 'ibus*' 
./snap/surfshark/10/.config/ibus
./snap/firefox/3779/.config/ibus
./.config/ibus
./.cache/ibus
./.var/app/com.github.micahflee.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/.config/ibus
./.var/app/com.github.micahflee.torbrowser-launcher/config/ibus
./.var/app/org.mozilla.firefox/config/ibus
./.var/app/org.torproject.torbrowser-launcher/config/ibus
./.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/.config/ibus

```
```
snap info firefox
name:      firefox
summary:   Mozilla Firefox web browser
publisher: Mozilla&#10003;
store-url: https://snapcraft.io/firefox
contact:   https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla
license:   unset
description: |
  Firefox is a powerful, extensible web browser with support for modern web
  application technologies.
commands:
  - firefox
  - firefox.geckodriver
snap-id:      3wdHCAVyZEmYsCMFDE9qt92UV8rC8Wdk
tracking:     latest/stable
refresh-date: today at 10:40 MST
channels:
  latest/stable:    122.0.1-1    2024-02-06 (3779) 275MB -
  latest/candidate: 123.0-3      2024-02-14 (3836) 279MB -
  latest/beta:      123.0b9-1    2024-02-09 (3806) 279MB -
  latest/edge:      124.0a1      2024-02-17 (3852) 298MB -
  esr/stable:       115.7.0esr-1 2024-01-23 (3671) 255MB -
  esr/candidate:    115.8.0esr-1 2024-02-13 (3827) 256MB -
  esr/beta:         &#8593;                                    
  esr/edge:         &#8593;                                    
installed:          122.0.1-1               (3779) 275MB -

```

---

### Post by peterx14 on 2024-02-17
```

$ sudo chown root:root /home/pryan/.config/ibus/bus
chown: cannot access '/home/pryan/.config/ibus/bus': No such file or directory

```
As mentioned... ibus/bus does not exist!

I've also checked backups and I can see no sign of ~/.config/ibus having previously existed and being removed... so I suspect this isn't the problem. I'm happy to be proved wrong on that, but it looks to me like the issue is something to do with the graphics/X11 or something having been updated and slightly broken in the process.

FYI: I *really* appreciate all your help with this. I'm giving up for tonight, so it'll likely be at least 24 hours before I post again. Thanks again!! :D

---

### Post by #&amp;thj^% on 2024-02-17
Xubuntu here as well and you can  see the differences between your and mine.

EDIT: even on Arch
```
find -iname 'ibus*' |grep firefox
./snap/firefox/3779/.config/ibus

```

---

### Post by #&amp;thj^% on 2024-02-18
What version of Xubuntu are you on?

here is something you may want to try:
```
cd && ls -al |grep -e snap -e.mozilla
## Mine
drwxrwxr-x   4 me   me            4 Nov 29 20:18 .mozilla
drwx------   4 me   me            4 Feb 15 13:30 snap
drwxrwxr-x   5 me   me           11 Nov 29 20:39 unsnap

```
backup and move ".config" out of the way.
```
mv .config  .config.bk
```
Login again, and now any better?
To revert:
```
mv .config.bk  .config
```

I have 3 Xubuntu installs>>>24.04 (Development) all show the "ibus/bus".
This problem has me very curious.

---

### Post by digitaltinker on 2024-02-18
I've had this before, and I've just reloaded my system and the error is back.  Problem disappears if you use Wayland but maybe you can't because of apps you use. I'll report back here if I find another fix.  And it affects other snaps, not just firefox but chromium for example.

---

### Post by #&amp;thj^% on 2024-02-18
> **digitaltinker said:**
> I've had this before, and I've just reloaded my system and the error is back.  Problem disappears if you use Wayland but maybe you can't because of apps you use. I'll report back here if I find another fix.  And it affects other snaps, not just firefox but chromium for example.
As of now there is no option for a wayland session on Xubuntu.

---

### Post by MAFoElffen on 2024-02-18
Please do this and post the results withi Code Tags:
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'

```
I looked up "AMD Athlon 3000G" at AMD, and I see: Radeon Vega 3

Which for that, also show the results of 
```

grep . /proc/cmdline

```

---

### Post by MAFoElffen on 2024-02-18
Please show the results of these, posted within CODE Tags:
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'
grep . /proc/cmdline
lsmod | grep 'amdgpu'
modinfo amdgpu | grep -E '^filename|^description|^firmware|^depends|^parm'

```
It should have Radeo Vega  and be using the amdgpu opensource driver with modules built from from linux-firmware

---

### Post by #&amp;thj^% on 2024-02-18
> **MAFoElffen said:**
> Please show the results of these, posted within CODE Tags:
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'
grep . /proc/cmdline
lsmod | grep 'amdgpu'
modinfo amdgpu | grep -E '^filename|^description|^firmware|^depends|^parm'

```
It should have Radeo Vega  and be using the amdgpu opensource driver with modules built from from linux-firmware

+1
I think I wore the OP out yesterday.....lol
```
modinfo amdgpu | grep -E '^filename|^description|^firmware' |grep vega
firmware:       amdgpu/vega12_gpu_info.bin
firmware:       amdgpu/vega10_gpu_info.bin
firmware:       amdgpu/vega12_asd.bin
firmware:       amdgpu/vega12_sos.bin
firmware:       amdgpu/vega10_cap.bin
firmware:       amdgpu/vega10_asd.bin
firmware:       amdgpu/vega10_sos.bin
firmware:       amdgpu/vega20_ta.bin
firmware:       amdgpu/vega20_asd.bin
firmware:       amdgpu/vega20_sos.bin
firmware:       amdgpu/vegam_rlc.bin
firmware:       amdgpu/vegam_mec2.bin
firmware:       amdgpu/vegam_mec.bin
firmware:       amdgpu/vegam_me.bin
firmware:       amdgpu/vegam_pfp.bin
firmware:       amdgpu/vegam_ce.bin
firmware:       amdgpu/vega20_rlc.bin
firmware:       amdgpu/vega20_mec2.bin
firmware:       amdgpu/vega20_mec.bin
firmware:       amdgpu/vega20_me.bin
firmware:       amdgpu/vega20_pfp.bin
firmware:       amdgpu/vega20_ce.bin
firmware:       amdgpu/vega12_rlc.bin
firmware:       amdgpu/vega12_mec2.bin
firmware:       amdgpu/vega12_mec.bin
firmware:       amdgpu/vega12_me.bin
firmware:       amdgpu/vega12_pfp.bin
firmware:       amdgpu/vega12_ce.bin
firmware:       amdgpu/vega10_rlc.bin
firmware:       amdgpu/vega10_mec2.bin
firmware:       amdgpu/vega10_mec.bin
firmware:       amdgpu/vega10_me.bin
firmware:       amdgpu/vega10_pfp.bin
firmware:       amdgpu/vega10_ce.bin
firmware:       amdgpu/vegam_sdma1.bin
firmware:       amdgpu/vegam_sdma.bin
firmware:       amdgpu/vega20_sdma1.bin
firmware:       amdgpu/vega20_sdma.bin
firmware:       amdgpu/vega12_sdma1.bin
firmware:       amdgpu/vega12_sdma.bin
firmware:       amdgpu/vega10_sdma1.bin
firmware:       amdgpu/vega10_sdma.bin
firmware:       amdgpu/vega20_uvd.bin
firmware:       amdgpu/vega12_uvd.bin
firmware:       amdgpu/vega10_uvd.bin
firmware:       amdgpu/vegam_uvd.bin
firmware:       amdgpu/vega20_vce.bin
firmware:       amdgpu/vega12_vce.bin
firmware:       amdgpu/vega10_vce.bin
firmware:       amdgpu/vegam_vce.bin
firmware:       amdgpu/vega20_smc.bin
firmware:       amdgpu/vega12_smc.bin
firmware:       amdgpu/vega10_acg_smc.bin
firmware:       amdgpu/vega10_smc.bin
firmware:       amdgpu/vegam_smc.bin

```
kernel mods;
```
 modinfo amdgpu | grep -E '^filename|^description'
filename:       /lib/modules/6.6.17-1-lts/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko.zst
description:    AMD GPU

```

---

### Post by peterx14 on 2024-06-10
[QUOTE=1fallen]
I think I wore the OP out yesterday.....lol
[/QUOTE]
I was just resting! :D

Sorry not to have replies to those commands (I'm not near the "problem" computer right now), but earlier I revisited the issue and discovered that it seems to only affect Snap packages... I noticed there is a Chromium (not Google Chrome) package that is also a snap, and that also renders with a corrupt window.

Googling that issue pulled up the following:
[https://bugzilla.mozilla.org/show_bug.cgi?id=1847175](https://bugzilla.mozilla.org/show_bug.cgi?id=1847175)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2004532](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2004532)
[https://superuser.com/a/1813091](https://superuser.com/a/1813091)

^ the last one provides a way to start Firefox in a non-GPU assisted mode which ***works around*** the problem! I'm guessing really I'm waiting for that launchpad.net bug to be fixed... but that might be a long wait.

---

### Post by #&amp;thj^% on 2024-06-10
Until that Bug gets a fix, will this work currently:
```
firefox --disable-gpu

```

I know how not fun a problem like this is to a user.

---

