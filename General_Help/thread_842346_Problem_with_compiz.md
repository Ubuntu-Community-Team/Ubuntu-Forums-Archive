---
title: "Problem with compiz"
date: 2008-06-27
forum: General Help
---

### Post by BlackSpot on 2008-06-27
Hi i install compiz and it work fine, but today toolbar on window gone.
I delete compiz (i think i delete it, but not shure), but now when i want "Extra visual effects" i receive this "failed to execute child process "compiz" (no such file or directory)"
I reinstall my ati driver - no result

---

### Post by Forlong on 2008-06-27
What do you mean, you deleted Compiz? How did you do it?

---

### Post by BlackSpot on 2008-06-27
with 
sudo apt-get purge compiz-core && sudo apt-get autoremove
sudo apt-get remove compiz
sudo apt-get remove fusion-icon
sudo apt-get remove compizconfig-settings-manager

i think this is all

---

### Post by Windsurfer619 on 2008-06-27
The problem is that you removed compiz. The toolbar on the window was only gone because the "decorations" plugin in compiz wasn't working (I have no idea how that would happen...). You probably just need to re-install compiz by typing "sudo apt-get install compiz" in a terminal.

---

### Post by BlackSpot on 2008-06-27
ok when i sudo apt-get install compiz
i go to System > Preferens > Apperance > Visual Effects and when i click on Extra i receive message Desktop effect could not be enabled
and when i go to System > Preferens > Compis...  
failed to execute child process "ccsm" (no such file or directory)

---

### Post by ajgreeny on 2008-06-27
for future reference, you have no need to uninstall compiz if it is causing problems at the moment, just don't use it either by going to System>>Preferences>>Appearance and then chosing "None" in the Visual effects tab, or simply using ```
metacity --replace
```

Then you can try to sort out the reasons for compiz causing problems. Many of them can be overcome just by careful chosing of the plugins you use.

---

### Post by BlackSpot on 2008-06-27
i search for solution but no found, but understand that metacity --replace 
restart graphic server right. When i write in terminal nothing hapend :/

---

### Post by BlackSpot on 2008-06-27
i go to System > Administrator > Hardware Driver and see thah ati driver is in use but not mark, i mark and reboot. After reboot i choose extra visual efects without error but toolbars disapper again. I write in terminal metacity --replace than visual effects are changing to NONE

---

### Post by Forlong on 2008-06-27
I'm pretty confused about your logic. You remove things and wonder afterwards, that they don't function? :)

If you want to be able to use ccsm again, you have to install it again:
```
sudo apt-get install compizconfig-settings-manager
```


As for the Desktop Effects problem: run [this]("http://ubuntuforums.org/showthread.php?t=799070") and post the output here.

---

### Post by BlackSpot on 2008-06-27
i install it and Compiz manager are running but now my minimize maximize and close bottons are gone and icons in compiz manager are blank

moni@moni-desktop:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV530 [Radeon X1600]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-06-27
Sorry, I didn't catch that Compiz is already working for you again.

What happens when running ```
gtk-window-decorator --replace
``` in a terminal?


As for ccsm not showing any icons: what did you do that it stopped working (and please say you didn't do anything)?

---

### Post by BlackSpot on 2008-06-27
Thank you with this gtk-window-decorator --replace bottons working again.
ccsm i didn't do anything :)
may i install ccsm from [here]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by Forlong on 2008-06-27
> **BlackSpot said:**
> Thank you with this gtk-window-decorator --replace bottons working again.
Great, then what is the output of this in a terminal:
```
gconftool-2 -g /apps/compiz/plugins/decoration/allscreens/options/command
```
> **BlackSpot said:**
> ccsm i didn't do anything :)
may i install ccsm from [here]("http://ubuntuforums.org/showthread.php?t=809695")
That is the very same version you have already installed.
Please run this command in a terminal:
```
sudo updatedb
``` (it will take a while)

Afterwards, post the output of this:
```
locate ccsm | grep ^/usr/share/ccsm
```
and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by BlackSpot on 2008-06-29
hello i back to home 10x for your advice.
```
moni@moni-desktop:~$ locate ccsm | grep ^/usr/share/ccsm
/usr/share/ccsm
/usr/share/ccsm/icons
/usr/share/ccsm/images
/usr/share/ccsm/icons/hicolor
/usr/share/ccsm/icons/hicolor/22x22
/usr/share/ccsm/icons/hicolor/scalable
/usr/share/ccsm/icons/hicolor/22x22/categories
/usr/share/ccsm/icons/hicolor/22x22/devices
/usr/share/ccsm/icons/hicolor/22x22/mimetypes
/usr/share/ccsm/icons/hicolor/22x22/categories/dummy
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-accessibility.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-desktop.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-effects.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-extras.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-general.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-image_loading.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-uncategorized.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-utility.png
/usr/share/ccsm/icons/hicolor/22x22/categories/plugins-window_management.png
/usr/share/ccsm/icons/hicolor/22x22/devices/input-keyboard.png
/usr/share/ccsm/icons/hicolor/22x22/devices/input-mouse.png
/usr/share/ccsm/icons/hicolor/22x22/devices/video-display.png
/usr/share/ccsm/icons/hicolor/22x22/mimetypes/audio-x-generic.png
/usr/share/ccsm/icons/hicolor/scalable/apps
/usr/share/ccsm/icons/hicolor/scalable/categories
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-3d.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-addhelper.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-animation.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-annotate.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-atlantis.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-bench.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-blur.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-bs.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-capture.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-clone.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-colorfilter.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-core.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-crashhandler.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cube.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cubecaps.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-cubereflex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-dbus.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-debug.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-decoration.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-expo.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-extrawm.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-ezoom.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fade.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fadedesktop.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fakeargb.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-firepaint.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-fs.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-gears.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-glib.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-group.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-imgjpeg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-inotify.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-loginout.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mag.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-maximumize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mblur.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-minimize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mousepoll.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-move.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-mswitch.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-neg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-notification.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-opacify.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-place.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-plane.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-png.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-put.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-reflex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-regex.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-resize.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-resizeinfo.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-ring.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-rotate.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scale.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scaleaddon.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-scalefilter.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-schemep.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screencasting.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screensaver.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-screenshot.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-session.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-shelf.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-shift.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-showdesktop.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-showmouse.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-snap.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-snow.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-splash.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-state.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-svg.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-switcher.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-text.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-thumbnail.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-tile.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-trailfocus.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-unknown.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-video.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-vpswitch.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wall.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wallpaper.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-water.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-widget.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-winrules.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-wobbly.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-workarounds.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-zoom.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-accessibility.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-all.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-desktop.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-effects.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-extras.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-general.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-image_loading.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-key_bindings.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-profiles.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-search.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-uncategorized.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-utility.svg
/usr/share/ccsm/icons/hicolor/scalable/categories/plugins-window_management.svg
/usr/share/ccsm/images/display.png
/usr/share/ccsm/images/modifier.png

```

---

### Post by Forlong on 2008-06-29
All the images are there.
Is there any output when running
```
ccsm
``` in a terminal?

---

### Post by BlackSpot on 2008-06-29
when i run ccsm in terminal only compiz manager start working

---

### Post by draconastar on 2008-12-31
I hate to resurrect an old thread, but I'm having an identical problem.  I am to the point where when I attempt to go to System -> Preferences -> Appearances and click "Extra", it seems busy doing something, then comes back and tells me that the effects couldn't be started.  When I go into the Advanced Desktop Effects manager, I can click on effects, but they don't do anything.  

These problems were also started by removing and reinstalling compiz after having problems with plugins.  Any help would be greatly appreciated!

---

### Post by maan on 2009-01-01
Hi,

When I tried to install Compiz, I got following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed:
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Can anyone help please.... Thanks!!!!!!!!

---

### Post by Forlong on 2009-01-01
> **draconastar said:**
> I hate to resurrect an old thread, but I'm having an identical problem.  I am to the point where when I attempt to go to System -> Preferences -> Appearances and click "Extra", it seems busy doing something, then comes back and tells me that the effects couldn't be started.  When I go into the Advanced Desktop Effects manager, I can click on effects, but they don't do anything.  

These problems were also started by removing and reinstalling compiz after having problems with plugins.  Any help would be greatly appreciated!
As long as Compiz (Desktop Effects) fails to run, the Advanced Desktop Effects Manager is useless.

Go here to find out what's wrong with your setup: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)


> **maan said:**
> 
When I tried to install Compiz, I got following message:

[...]

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
Did you have Synaptic running at the same time?
Close that and try again.

---

### Post by draconastar on 2009-01-01
Every time I try to click on Compiz-Check, it gives me a 500 Internal Server Error.  Sorry to be such a bother.

---

### Post by Forlong on 2009-01-01
> **draconastar said:**
> Every time I try to click on Compiz-Check, it gives me a 500 Internal Server Error.  Sorry to be such a bother.
What link exactly gives you this? Everything works here just fine.

---

### Post by draconastar on 2009-01-01
Both links you provide in your post about Compiz-Check, the one at the very top and the instructions at the bottom, give me this error.  

I've managed to get myself to the point where Compiz itself works.  The only problem is that I have the fusion-icon, which I find annoying, and compiz --replace does not work.  When I try to use compiz --replace in terminal I get:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found
```

And it reverts to regular window management.  Then it sits at that last line and does nothing until I use break to stop it.  The only way to actually get compiz working is to right-click on the fusion icon and click "Reload Window Manager".

I see now that I don't have Xgl.  I suppose I'll work on that.

---

### Post by Forlong on 2009-01-01
> **draconastar said:**
> Both links you provide in your post about Compiz-Check, the one at the very top and the instructions at the bottom, give me this error.  
Please try again, there shouldn't be a problem with those.
> **draconastar said:**
> I've managed to get myself to the point where Compiz itself works.  The only problem is that I have the fusion-icon, which I find annoying, and compiz --replace does not work.  When I try to use compiz --replace in terminal I get:
```
[...]
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found
```

And it reverts to regular window management.  Then it sits at that last line and does nothing until I use break to stop it.  The only way to actually get compiz working is to right-click on the fusion icon and click "Reload Window Manager".
How did you install Compiz?
It shouldn't point to /usr/local
> **draconastar said:**
> I see now that I don't have Xgl.  I suppose I'll work on that.
No, you most probably (99%) do _not_ need Xgl!

---

### Post by draconastar on 2009-01-01
Ah, I won't worry about Xgl then.  

The links to Compiz-Check are still broken for me.  I'm sure that it's something on my end that isn't working, but I have no idea what.  It's the same Internal Sever error every time, even after searching for the page on Google and finding it that way.

I've used a series of instructions given to me in [this post]("http://ubuntuforums.org/showthread.php?t=820802&page=17") (it starts on page 17 where my specific instructions were given).  I was taken to the French forum posted, and the instructions he gave (after translating through Firefox addon) seemed to work pretty well, with one problem.  All of the effects, plugins and such are *there*, they just aren't WORKING.  I have no window borders, no effects are working although I can see the options and they are checked in the config window.  My fusion icon is working (on startup no less), but doesn't help me at all other than allowing me to switch to metacity as my window handler so that I can even do anything.

What would I be missing where all of these effects aren't working?  I'm not getting any errors that pop up, just nothing happening.

---

### Post by Forlong on 2009-01-02
> **draconastar said:**
> I've used a series of instructions given to me in [this post]("http://ubuntuforums.org/showthread.php?t=820802&page=17") (it starts on page 17 where my specific instructions were given).  I was taken to the French forum posted, and the instructions he gave (after translating through Firefox addon) seemed to work pretty well, with one problem.  All of the effects, plugins and such are *there*, they just aren't WORKING.  I have no window borders, no effects are working although I can see the options and they are checked in the config window.  My fusion icon is working (on startup no less), but doesn't help me at all other than allowing me to switch to metacity as my window handler so that I can even do anything.

What would I be missing where all of these effects aren't working?  I'm not getting any errors that pop up, just nothing happening.
Oh my, those install scripts are the root of many evils.
I don't know why people advise to use them...


Anyway... let's try to fix this.
First of all, let's see what you have installed:
```
dpkg -l | grep compiz
```

---

### Post by draconastar on 2009-01-02
I really appreciate your help with this, Forlong.  :KS

When I entered that code into terminal, it returned with nothing:

```
daren@daren-desktop:~$ dpkg -l | grep compiz
daren@daren-desktop:~$ 

```

I figured I might just post a dpkg -l, but the list was entirely too long, and half of it wouldn't even fit in the terminal window.

---

### Post by draconastar on 2009-01-04
Bump.

Hate to bug you, but this problem is pretty frustrating, and have no idea where to start with it.

---

### Post by Forlong on 2009-01-05
No, it's good to bump your thread after such a time, I simply tend to forget about some threads when there are so many of them I have posted in.

So, your problem is, it appears you don't have Compiz installed at all (at least not via the package manager).
I am assuming you compiled it yourself (or by script), is that correct?

---

### Post by draconastar on 2009-01-05
I believe so, yes.  I vaguely remember having installed at least a few of the core files through Synaptic, but this is apparently not the case.

**EDIT**

I have just discovered that according to Synaptic I don't have compiz-core installed, nor anything else compiz-related.  I guess the script must have installed stuff but the package manager doesn't know.

---

### Post by Forlong on 2009-01-05
Sorry, I can not say anything about an install by some random script.
You'll have to either ask the person who wrote that script what might have gone wrong or un-install it completely and switch to Ubuntu's Compiz packages.

---

### Post by draconastar on 2009-01-05
I'd kind of like to get rid of everything and start from scratch, because I have a feeling that you'll be able to get me set up and working correctly.  :D  Where do I start?

---

### Post by Forlong on 2009-01-05
Well, OK. That won't be easy, though, since I don't know how you installed it on the first place...

What's the output of
```
locate compiz | grep ^/usr
```

---

### Post by draconastar on 2009-01-05
You're the best, Forlong.  Thanks for sticking with this.

```
daren@daren-desktop:~$ locate compiz | grep ^/usr
/usr/bin/compiz
/usr/lib/window-manager-settings/libcompiz.a
/usr/lib/window-manager-settings/libcompiz.la
/usr/lib/window-manager-settings/libcompiz.so
/usr/local/bin/compiz
/usr/local/bin/compizsrc-gen.sh
/usr/local/etc/compizconfig
/usr/local/etc/compizconfig/config
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-obs.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/include/compiz
/usr/local/include/compizconfig
/usr/local/include/compiz/compiz-animation.h
/usr/local/include/compiz/compiz-animationaddon.h
/usr/local/include/compiz/compiz-common.h
/usr/local/include/compiz/compiz-core.h
/usr/local/include/compiz/compiz-cube.h
/usr/local/include/compiz/compiz-mousepoll.h
/usr/local/include/compiz/compiz-plugin.h
/usr/local/include/compiz/compiz-scale.h
/usr/local/include/compiz/compiz-text.h
/usr/local/include/compiz/compiz.h
/usr/local/include/compiz/decoration.h
/usr/local/include/compizconfig/ccs-backend.h
/usr/local/include/compizconfig/ccs.h
/usr/local/lib/compiz
/usr/local/lib/compizconfig
/usr/local/lib/libcompizconfig.a
/usr/local/lib/libcompizconfig.la
/usr/local/lib/libcompizconfig.so
/usr/local/lib/libcompizconfig.so.0
/usr/local/lib/libcompizconfig.so.0.0.0
/usr/local/lib/compiz/lib3d.so
/usr/local/lib/compiz/libaddhelper.so
/usr/local/lib/compiz/libanaglyph.so
/usr/local/lib/compiz/libanimation.so
/usr/local/lib/compiz/libanimationaddon.so
/usr/local/lib/compiz/libanimationplus.so
/usr/local/lib/compiz/libannotate.a
/usr/local/lib/compiz/libannotate.la
/usr/local/lib/compiz/libannotate.so
/usr/local/lib/compiz/libatlantis.so
/usr/local/lib/compiz/libbasicblur.so
/usr/local/lib/compiz/libbench.so
/usr/local/lib/compiz/libblur.a
/usr/local/lib/compiz/libblur.la
/usr/local/lib/compiz/libblur.so
/usr/local/lib/compiz/libccp.a
/usr/local/lib/compiz/libccp.la
/usr/local/lib/compiz/libccp.so
/usr/local/lib/compiz/libclone.a
/usr/local/lib/compiz/libclone.la
/usr/local/lib/compiz/libclone.so
/usr/local/lib/compiz/libcolorfilter.so
/usr/local/lib/compiz/libcrashhandler.so
/usr/local/lib/compiz/libcube.a
/usr/local/lib/compiz/libcube.la
/usr/local/lib/compiz/libcube.so
/usr/local/lib/compiz/libcubeaddon.so
/usr/local/lib/compiz/libcubemodel.so
/usr/local/lib/compiz/libdbus.a
/usr/local/lib/compiz/libdbus.la
/usr/local/lib/compiz/libdbus.so
/usr/local/lib/compiz/libdecoration.a
/usr/local/lib/compiz/libdecoration.la
/usr/local/lib/compiz/libdecoration.so
/usr/local/lib/compiz/libdodge.so
/usr/local/lib/compiz/libelements.so
/usr/local/lib/compiz/libexpo.so
/usr/local/lib/compiz/libextrawm.so
/usr/local/lib/compiz/libezoom.so
/usr/local/lib/compiz/libfade.a
/usr/local/lib/compiz/libfade.la
/usr/local/lib/compiz/libfade.so
/usr/local/lib/compiz/libfadedesktop.so
/usr/local/lib/compiz/libfakeargb.so
/usr/local/lib/compiz/libfirepaint.so
/usr/local/lib/compiz/libfreewins.so
/usr/local/lib/compiz/libfs.a
/usr/local/lib/compiz/libfs.la
/usr/local/lib/compiz/libfs.so
/usr/local/lib/compiz/libgconf.a
/usr/local/lib/compiz/libgconf.la
/usr/local/lib/compiz/libgconf.so
/usr/local/lib/compiz/libgears.so
/usr/local/lib/compiz/libghost.so
/usr/local/lib/compiz/libglib.a
/usr/local/lib/compiz/libglib.la
/usr/local/lib/compiz/libglib.so
/usr/local/lib/compiz/libgreenscreen.so
/usr/local/lib/compiz/libgrid.so
/usr/local/lib/compiz/libgroup.so
/usr/local/lib/compiz/libimgjpeg.so
/usr/local/lib/compiz/libini.a
/usr/local/lib/compiz/libini.la
/usr/local/lib/compiz/libini.so
/usr/local/lib/compiz/libinotify.a
/usr/local/lib/compiz/libinotify.la
/usr/local/lib/compiz/libinotify.so
/usr/local/lib/compiz/liblazypointer.so
/usr/local/lib/compiz/libloginout.so
/usr/local/lib/compiz/libmag.so
/usr/local/lib/compiz/libmblur.so
/usr/local/lib/compiz/libminimize.a
/usr/local/lib/compiz/libminimize.la
/usr/local/lib/compiz/libminimize.so
/usr/local/lib/compiz/libmousegestures.so
/usr/local/lib/compiz/libmousepoll.so
/usr/local/lib/compiz/libmousetrails.so
/usr/local/lib/compiz/libmove.a
/usr/local/lib/compiz/libmove.la
/usr/local/lib/compiz/libmove.so
/usr/local/lib/compiz/libmswitch.so
/usr/local/lib/compiz/libneg.so
/usr/local/lib/compiz/libnewton.so
/usr/local/lib/compiz/libobs.a
/usr/local/lib/compiz/libobs.la
/usr/local/lib/compiz/libobs.so
/usr/local/lib/compiz/libopacify.so
/usr/local/lib/compiz/libpeek.so
/usr/local/lib/compiz/libphoto.so
/usr/local/lib/compiz/libplace.a
/usr/local/lib/compiz/libplace.la
/usr/local/lib/compiz/libplace.so
/usr/local/lib/compiz/libpng.a
/usr/local/lib/compiz/libpng.la
/usr/local/lib/compiz/libpng.so
/usr/local/lib/compiz/libput.so
/usr/local/lib/compiz/libputplus.so
/usr/local/lib/compiz/libreflex.so
/usr/local/lib/compiz/libregex.a
/usr/local/lib/compiz/libregex.la
/usr/local/lib/compiz/libregex.so
/usr/local/lib/compiz/libresize.a
/usr/local/lib/compiz/libresize.la
/usr/local/lib/compiz/libresize.so
/usr/local/lib/compiz/libresizeinfo.so
/usr/local/lib/compiz/libring.so
/usr/local/lib/compiz/librotate.a
/usr/local/lib/compiz/librotate.la
/usr/local/lib/compiz/librotate.so
/usr/local/lib/compiz/librubik.so
/usr/local/lib/compiz/libscale.a
/usr/local/lib/compiz/libscale.la
/usr/local/lib/compiz/libscale.so
/usr/local/lib/compiz/libscaleaddon.so
/usr/local/lib/compiz/libscalefilter.so
/usr/local/lib/compiz/libscreensaver.so
/usr/local/lib/compiz/libscreenshot.a
/usr/local/lib/compiz/libscreenshot.la
/usr/local/lib/compiz/libscreenshot.so
/usr/local/lib/compiz/libshelf.so
/usr/local/lib/compiz/libshift.so
/usr/local/lib/compiz/libshowdesktop.so
/usr/local/lib/compiz/libshowmouse.so
/usr/local/lib/compiz/libsmartput.so
/usr/local/lib/compiz/libsnap.so
/usr/local/lib/compiz/libsnowglobe.so
/usr/local/lib/compiz/libsplash.so
/usr/local/lib/compiz/libstackswitch.so
/usr/local/lib/compiz/libstatic.so
/usr/local/lib/compiz/libsvg.a
/usr/local/lib/compiz/libsvg.la
/usr/local/lib/compiz/libsvg.so
/usr/local/lib/compiz/libswap.so
/usr/local/lib/compiz/libswitcher.a
/usr/local/lib/compiz/libswitcher.la
/usr/local/lib/compiz/libswitcher.so
/usr/local/lib/compiz/libtext.so
/usr/local/lib/compiz/libthrow.so
/usr/local/lib/compiz/libthumbnail.so
/usr/local/lib/compiz/libtile.so
/usr/local/lib/compiz/libtoggledeco.so
/usr/local/lib/compiz/libtrailfocus.so
/usr/local/lib/compiz/libvideo.a
/usr/local/lib/compiz/libvideo.la
/usr/local/lib/compiz/libvideo.so
/usr/local/lib/compiz/libvpswitch.so
/usr/local/lib/compiz/libwall.so
/usr/local/lib/compiz/libwallpaper.so
/usr/local/lib/compiz/libwater.a
/usr/local/lib/compiz/libwater.la
/usr/local/lib/compiz/libwater.so
/usr/local/lib/compiz/libwidget.so
/usr/local/lib/compiz/libwinrules.so
/usr/local/lib/compiz/libwizard.so
/usr/local/lib/compiz/libwobbly.a
/usr/local/lib/compiz/libwobbly.la
/usr/local/lib/compiz/libwobbly.so
/usr/local/lib/compiz/libworkarounds.so
/usr/local/lib/compizconfig/backends
/usr/local/lib/compizconfig/backends/libini.a
/usr/local/lib/compizconfig/backends/libini.la
/usr/local/lib/compizconfig/backends/libini.so
/usr/local/lib/pkgconfig/compiz-animation.pc
/usr/local/lib/pkgconfig/compiz-animationaddon.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/pkgconfig/compiz-mousepoll.pc
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz-text.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compizconfig-python.pc
/usr/local/lib/pkgconfig/libcompizconfig.pc
/usr/local/lib/python2.5/site-packages/compizconfig.a
/usr/local/lib/python2.5/site-packages/compizconfig.la
/usr/local/lib/python2.5/site-packages/compizconfig.so
/usr/local/share/compiz
/usr/local/share/applications/compiz.desktop
/usr/local/share/compiz/3d.xml
/usr/local/share/compiz/Gnome
/usr/local/share/compiz/Oxygen
/usr/local/share/compiz/addhelper.xml
/usr/local/share/compiz/anaglyph.xml
/usr/local/share/compiz/animation.xml
/usr/local/share/compiz/animationaddon.xml
/usr/local/share/compiz/animationplus.xml
/usr/local/share/compiz/annotate.xml
/usr/local/share/compiz/atlantis.xml
/usr/local/share/compiz/autumn1.png
/usr/local/share/compiz/autumn2.png
/usr/local/share/compiz/basicblur.xml
/usr/local/share/compiz/bench.xml
/usr/local/share/compiz/blur.xml
/usr/local/share/compiz/bubbles1.png
/usr/local/share/compiz/bubbles2.png
/usr/local/share/compiz/ccp.xml
/usr/local/share/compiz/clone.xml
/usr/local/share/compiz/colorfilter.xml
/usr/local/share/compiz/compizcap.png
/usr/local/share/compiz/core.xml
/usr/local/share/compiz/crashhandler.xml
/usr/local/share/compiz/cube.xml
/usr/local/share/compiz/cubeaddon.xml
/usr/local/share/compiz/cubecap_release.png
/usr/local/share/compiz/cubemodel.xml
/usr/local/share/compiz/dbus.xml
/usr/local/share/compiz/decoration.xml
/usr/local/share/compiz/dodge.xml
/usr/local/share/compiz/elements.xml
/usr/local/share/compiz/expo.xml
/usr/local/share/compiz/extrawm.xml
/usr/local/share/compiz/ezoom.xml
/usr/local/share/compiz/fade.xml
/usr/local/share/compiz/fadedesktop.xml
/usr/local/share/compiz/fakeargb.xml
/usr/local/share/compiz/filters
/usr/local/share/compiz/fireflies1.svg
/usr/local/share/compiz/fireflies2.svg
/usr/local/share/compiz/firepaint.xml
/usr/local/share/compiz/freedesktop.png
/usr/local/share/compiz/freewins.xml
/usr/local/share/compiz/fs.xml
/usr/local/share/compiz/fusioncap.png
/usr/local/share/compiz/gconf.xml
/usr/local/share/compiz/gears.xml
/usr/local/share/compiz/ghost.xml
/usr/local/share/compiz/glib.xml
/usr/local/share/compiz/greenscreen.xml
/usr/local/share/compiz/grid.xml
/usr/local/share/compiz/group.xml
/usr/local/share/compiz/icon.png
/usr/local/share/compiz/imgjpeg.xml
/usr/local/share/compiz/ini.xml
/usr/local/share/compiz/inotify.xml
/usr/local/share/compiz/kconfig.xml
/usr/local/share/compiz/lazypointer.xml
/usr/local/share/compiz/loginout.xml
/usr/local/share/compiz/mag.xml
/usr/local/share/compiz/mblur.xml
/usr/local/share/compiz/minimize.xml
/usr/local/share/compiz/mousegestures.xml
/usr/local/share/compiz/mousepoll.xml
/usr/local/share/compiz/mousetrails.xml
/usr/local/share/compiz/move.xml
/usr/local/share/compiz/mswitch.xml
/usr/local/share/compiz/neg.xml
/usr/local/share/compiz/newton.xml
/usr/local/share/compiz/obs.xml
/usr/local/share/compiz/opacify.xml
/usr/local/share/compiz/peek.xml
/usr/local/share/compiz/photo.xml
/usr/local/share/compiz/place.xml
/usr/local/share/compiz/plugin-elements.png
/usr/local/share/compiz/png.xml
/usr/local/share/compiz/put.xml
/usr/local/share/compiz/putplus.xml
/usr/local/share/compiz/reflection.png
/usr/local/share/compiz/reflex.xml
/usr/local/share/compiz/regex.xml
/usr/local/share/compiz/resize.xml
/usr/local/share/compiz/resizeinfo.xml
/usr/local/share/compiz/ring.xml
/usr/local/share/compiz/rotate.xml
/usr/local/share/compiz/rubik.xml
/usr/local/share/compiz/scale.xml
/usr/local/share/compiz/scaleaddon.xml
/usr/local/share/compiz/scalefilter.xml
/usr/local/share/compiz/schemas.xslt
/usr/local/share/compiz/screensaver.xml
/usr/local/share/compiz/screenshot.xml
/usr/local/share/compiz/shelf.xml
/usr/local/share/compiz/shift.xml
/usr/local/share/compiz/showdesktop.xml
/usr/local/share/compiz/showmouse.xml
/usr/local/share/compiz/smartput.xml
/usr/local/share/compiz/snap.xml
/usr/local/share/compiz/snow1.png
/usr/local/share/compiz/snow2.png
/usr/local/share/compiz/snowglobe.xml
/usr/local/share/compiz/splash.xml
/usr/local/share/compiz/splash_background.png
/usr/local/share/compiz/splash_logo.png
/usr/local/share/compiz/stackswitch.xml
/usr/local/share/compiz/stars1.png
/usr/local/share/compiz/static.xml
/usr/local/share/compiz/svg.xml
/usr/local/share/compiz/swap.xml
/usr/local/share/compiz/switcher.xml
/usr/local/share/compiz/text.xml
/usr/local/share/compiz/throw.xml
/usr/local/share/compiz/thumbnail.xml
/usr/local/share/compiz/tile.xml
/usr/local/share/compiz/toggledeco.xml
/usr/local/share/compiz/trailfocus.xml
/usr/local/share/compiz/video.xml
/usr/local/share/compiz/vpswitch.xml
/usr/local/share/compiz/wall.xml
/usr/local/share/compiz/wallpaper.xml
/usr/local/share/compiz/water.xml
/usr/local/share/compiz/widget.xml
/usr/local/share/compiz/winrules.xml
/usr/local/share/compiz/wizard.xml
/usr/local/share/compiz/wobbly.xml
/usr/local/share/compiz/workarounds.xml
/usr/local/share/compiz/Gnome/image.svg
/usr/local/share/compiz/Gnome/mask.png
/usr/local/share/compiz/Gnome/overlay.png
/usr/local/share/compiz/Oxygen/image.svg
/usr/local/share/compiz/Oxygen/mask.png
/usr/local/share/compiz/Oxygen/overlay.png
/usr/local/share/compiz/filters/blackandwhite
/usr/local/share/compiz/filters/blueish-filter
/usr/local/share/compiz/filters/contrast
/usr/local/share/compiz/filters/deuteranopia
/usr/local/share/compiz/filters/grayscale
/usr/local/share/compiz/filters/negative
/usr/local/share/compiz/filters/negative-green
/usr/local/share/compiz/filters/protanopia
/usr/local/share/compiz/filters/sepia
/usr/local/share/compiz/filters/swap-green-blue
/usr/local/share/compiz/filters/swap-red-blue
/usr/local/share/compiz/filters/swap-red-green
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/or/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/pkgconfig/compiz.pc
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/gnome/wm-properties/compiz-wm.desktop
```

---

### Post by Forlong on 2009-01-05
OK, for now, run those two command to get rid of most of the install:
```
sudo rm /usr/bin/compiz /usr/local/bin/compiz /usr/local/bin/compizsrc-gen.sh
```
```
sudo rm -r /usr/lib/window-manager-settings/ /usr/local/etc/compizconfig /usr/local/lib/compiz /usr/local/lib/compizconfig /usr/local/share/compiz
```
Afterwards, run
```
sudo updatedb
``` (that will take a while, it updates the search index)

And finally
```
locate compiz | grep ^/usr
``` again to post the output here.

---

### Post by draconastar on 2009-01-05
Just got home from work and executed the first three commands, here's the output of the last:

```
daren@daren-desktop:~$ locate compiz | grep ^/usr
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-obs.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/include/compiz
/usr/local/include/compizconfig
/usr/local/include/compiz/compiz-animation.h
/usr/local/include/compiz/compiz-animationaddon.h
/usr/local/include/compiz/compiz-common.h
/usr/local/include/compiz/compiz-core.h
/usr/local/include/compiz/compiz-cube.h
/usr/local/include/compiz/compiz-mousepoll.h
/usr/local/include/compiz/compiz-plugin.h
/usr/local/include/compiz/compiz-scale.h
/usr/local/include/compiz/compiz-text.h
/usr/local/include/compiz/compiz.h
/usr/local/include/compiz/decoration.h
/usr/local/include/compizconfig/ccs-backend.h
/usr/local/include/compizconfig/ccs.h
/usr/local/lib/libcompizconfig.a
/usr/local/lib/libcompizconfig.la
/usr/local/lib/libcompizconfig.so
/usr/local/lib/libcompizconfig.so.0
/usr/local/lib/libcompizconfig.so.0.0.0
/usr/local/lib/pkgconfig/compiz-animation.pc
/usr/local/lib/pkgconfig/compiz-animationaddon.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/pkgconfig/compiz-mousepoll.pc
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz-text.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compizconfig-python.pc
/usr/local/lib/pkgconfig/libcompizconfig.pc
/usr/local/lib/python2.5/site-packages/compizconfig.a
/usr/local/lib/python2.5/site-packages/compizconfig.la
/usr/local/lib/python2.5/site-packages/compizconfig.so
/usr/local/share/applications/compiz.desktop
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/or/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/pkgconfig/compiz.pc
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/gnome/wm-properties/compiz-wm.desktop
```

---

### Post by Forlong on 2009-01-06
OK, now run
```
sudo rm -r /usr/local/include/compiz /usr/local/include/compizconfig

```
Then ```
sudo updatedb
``` again and finally
```
sudo rm $(locate compiz | grep ^/usr)
```
In case there are any error messages, post them here.

If everything's OK, install Compiz like this:
```
sudo apt-get install compiz simple-ccsm
```

---

### Post by draconastar on 2009-01-06
All commands executed and completed without error, but compiz and all things related still seem to be unresponsive, so I'm guessing we're not done yet.  :popcorn:

**EDIT**

Actually, I now have a problem where on startup, Nautilus doesn't start correctly due to a problem with Bonobo while trying to find the factory, and in order to get it working I have to kill bonobo-activation-server and restart nautilus.  I'm guessing this is unrelated, but I figured I'd let you know just in case.

---

### Post by Forlong on 2009-01-06
Please try to download Compiz-Check to post the output here.

If it's still not working for you, what's the output of
```
compiz --replace
```

---

### Post by draconastar on 2009-01-06
I'm still unable to get Compiz-Check for some unknown reason.  Here's the output of compiz --replace:

```
daren@daren-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
libccs: dlopen: /usr/local/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
libccs: dlopen: /usr/local/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
Integration : true
Profile     : default
Adding plugins
```

When that happens, my window borders go away, so I have to go back to the default.

---

### Post by Forlong on 2009-01-06
Run this
```
sudo apt-get install --reinstall libcompizconfig0
```
and try again.

---

### Post by draconastar on 2009-01-06
Sorry for my late response, bad weather in my area had me knocked out for awhile.

After running the reinstall command and completing, I did a quick xserver kill and tried compiz --replace again.  Same result, windows with no border, and this output:

```
daren@daren-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
libccs: dlopen: /usr/local/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
libccs: dlopen: /usr/local/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
Integration : true
Profile     : default
Adding plugins
```

---

### Post by Forlong on 2009-01-07
I don't know why it's still looking for a library in /usr/local :-?

Try going to Synaptic and search for compiz. Then re-install every package that you find installed.

Afterwards, reboot (not just restarting X, we need to clear GNOME's cache)
Then run
```
compiz --replace
``` again and if it's still spitting out that error, post the output of ```
sudo updatedb && locate compiz | grep ^/usr
```

---

### Post by draconastar on 2009-01-07
I apologize again for my late response.  My satellite receiver is covered in ice at the moment.  :(

The reinstall completed without error, so I restarted my computer and booted into Ubuntu.  After opening a terminal and trying compiz --replace, I was left with the same result as before: no window borders, no effects, same missing file or directory output.

After executing the command that you told me to, I have the back of a list that I was able to catch, because it was too big for the terminal window:

```
/usr/lib/compiz/libthumbnail.so
/usr/lib/compiz/libtrailfocus.a
/usr/lib/compiz/libtrailfocus.la
/usr/lib/compiz/libtrailfocus.so
/usr/lib/compiz/libvideo.so
/usr/lib/compiz/libvpswitch.a
/usr/lib/compiz/libvpswitch.la
/usr/lib/compiz/libvpswitch.so
/usr/lib/compiz/libwall.a
/usr/lib/compiz/libwall.la
/usr/lib/compiz/libwall.so
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so
/usr/lib/compiz/libwater.so
/usr/lib/compiz/libwidget.a
/usr/lib/compiz/libwidget.la
/usr/lib/compiz/libwidget.so
/usr/lib/compiz/libwinrules.a
/usr/lib/compiz/libwinrules.la
/usr/lib/compiz/libwinrules.so
/usr/lib/compiz/libwobbly.so
/usr/lib/compiz/libworkarounds.a
/usr/lib/compiz/libworkarounds.la
/usr/lib/compiz/libworkarounds.so
/usr/lib/compiz/libzoom.so
/usr/lib/compizconfig/backends
/usr/lib/compizconfig/backends/libgconf.a
/usr/lib/compizconfig/backends/libgconf.la
/usr/lib/compizconfig/backends/libgconf.so
/usr/lib/compizconfig/backends/libini.so
/usr/lib/libgnome-window-settings1/libcompiz.so
/usr/lib/pkgconfig/compiz-mousepoll.pc
/usr/lib/pkgconfig/compiz-text.pc
/usr/lib/pkgconfig/compizconfig-python.pc
/usr/lib/python2.5/site-packages/compizconfig.so
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-obs.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/lib/libcompizconfig.a
/usr/local/lib/libcompizconfig.la
/usr/local/lib/libcompizconfig.so
/usr/local/lib/libcompizconfig.so.0
/usr/local/lib/libcompizconfig.so.0.0.0
/usr/local/lib/pkgconfig/compiz-animation.pc
/usr/local/lib/pkgconfig/compiz-animationaddon.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/pkgconfig/compiz-mousepoll.pc
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz-text.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compizconfig-python.pc
/usr/local/lib/pkgconfig/libcompizconfig.pc
/usr/local/lib/python2.5/site-packages/compizconfig.a
/usr/local/lib/python2.5/site-packages/compizconfig.la
/usr/local/lib/python2.5/site-packages/compizconfig.so
/usr/local/share/applications/compiz.desktop
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/or/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/pkgconfig/compiz.pc
/usr/share/compiz
/usr/share/compizconfig
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/compiz/3d.xml
/usr/share/compiz/Gnome
/usr/share/compiz/Oxygen
/usr/share/compiz/addhelper.xml
/usr/share/compiz/animation.xml
/usr/share/compiz/annotate.xml
/usr/share/compiz/bench.xml
/usr/share/compiz/bicubic.xml
/usr/share/compiz/blur.xml
/usr/share/compiz/bs.xml
/usr/share/compiz/ccp.xml
/usr/share/compiz/clone.xml
/usr/share/compiz/colorfilter.xml
/usr/share/compiz/compizcap.png
/usr/share/compiz/core.xml
/usr/share/compiz/crashhandler.xml
/usr/share/compiz/cube.xml
/usr/share/compiz/cubeaddon.xml
/usr/share/compiz/dbus.xml
/usr/share/compiz/decoration.xml
/usr/share/compiz/expo.xml
/usr/share/compiz/extrawm.xml
/usr/share/compiz/ezoom.xml
/usr/share/compiz/fade.xml
/usr/share/compiz/fadedesktop.xml
/usr/share/compiz/filters
/usr/share/compiz/firepaint.xml
/usr/share/compiz/freedesktop.png
/usr/share/compiz/fs.xml
/usr/share/compiz/fusioncap.png
/usr/share/compiz/gconf.xml
/usr/share/compiz/gears.xml
/usr/share/compiz/glib.xml
/usr/share/compiz/group.xml
/usr/share/compiz/icon.png
/usr/share/compiz/imgjpeg.xml
/usr/share/compiz/ini.xml
/usr/share/compiz/inotify.xml
/usr/share/compiz/loginout.xml
/usr/share/compiz/mag.xml
/usr/share/compiz/maximumize.xml
/usr/share/compiz/mblur.xml
/usr/share/compiz/minimize.xml
/usr/share/compiz/mousepoll.xml
/usr/share/compiz/move.xml
/usr/share/compiz/neg.xml
/usr/share/compiz/notification.xml
/usr/share/compiz/opacify.xml
/usr/share/compiz/place.xml
/usr/share/compiz/png.xml
/usr/share/compiz/put.xml
/usr/share/compiz/reflection.png
/usr/share/compiz/reflex.xml
/usr/share/compiz/regex.xml
/usr/share/compiz/resize.xml
/usr/share/compiz/resizeinfo.xml
/usr/share/compiz/ring.xml
/usr/share/compiz/rotate.xml
/usr/share/compiz/scale.xml
/usr/share/compiz/scaleaddon.xml
/usr/share/compiz/scalefilter.xml
/usr/share/compiz/screenshot.xml
/usr/share/compiz/session.xml
/usr/share/compiz/shelf.xml
/usr/share/compiz/shift.xml
/usr/share/compiz/showdesktop.xml
/usr/share/compiz/showmouse.xml
/usr/share/compiz/snap.xml
/usr/share/compiz/splash.xml
/usr/share/compiz/splash_background.png
/usr/share/compiz/splash_logo.png
/usr/share/compiz/staticswitcher.xml
/usr/share/compiz/svg.xml
/usr/share/compiz/switcher.xml
/usr/share/compiz/text.xml
/usr/share/compiz/thumbnail.xml
/usr/share/compiz/trailfocus.xml
/usr/share/compiz/video.xml
/usr/share/compiz/vpswitch.xml
/usr/share/compiz/wall.xml
/usr/share/compiz/wallpaper.xml
/usr/share/compiz/water.xml
/usr/share/compiz/widget.xml
/usr/share/compiz/winrules.xml
/usr/share/compiz/wobbly.xml
/usr/share/compiz/workarounds.xml
/usr/share/compiz/zoom.xml
/usr/share/compiz/Gnome/mask.png
/usr/share/compiz/Gnome/overlay.png
/usr/share/compiz/Oxygen/mask.png
/usr/share/compiz/Oxygen/overlay.png
/usr/share/compiz/filters/blackandwhite
/usr/share/compiz/filters/blueish-filter
/usr/share/compiz/filters/contrast
/usr/share/compiz/filters/deuteranopia
/usr/share/compiz/filters/grayscale
/usr/share/compiz/filters/negative
/usr/share/compiz/filters/negative-green
/usr/share/compiz/filters/protanopia
/usr/share/compiz/filters/sepia
/usr/share/compiz/filters/swap-green-blue
/usr/share/compiz/filters/swap-red-blue
/usr/share/compiz/filters/swap-red-green
/usr/share/compizconfig/extra.profile
/usr/share/compizconfig/global.xml
/usr/share/compizconfig/normal.profile
/usr/share/doc/compiz
/usr/share/doc/compiz-core
/usr/share/doc/compiz-fusion-plugins-extra
/usr/share/doc/compiz-fusion-plugins-main
/usr/share/doc/compiz-gnome
/usr/share/doc/compiz-plugins
/usr/share/doc/compizconfig-backend-gconf
/usr/share/doc/compizconfig-settings-manager
/usr/share/doc/libcompizconfig0
/usr/share/doc/python-compizconfig
/usr/share/doc/compiz/changelog.Debian.gz
/usr/share/doc/compiz/changelog.gz
/usr/share/doc/compiz/copyright
/usr/share/doc/compiz-core/AUTHORS
/usr/share/doc/compiz-core/NEWS.gz
/usr/share/doc/compiz-core/README
/usr/share/doc/compiz-core/README.Debian
/usr/share/doc/compiz-core/TODO
/usr/share/doc/compiz-core/changelog.Debian.gz
/usr/share/doc/compiz-core/changelog.gz
/usr/share/doc/compiz-core/copyright
/usr/share/doc/compiz-fusion-plugins-extra/AUTHORS
/usr/share/doc/compiz-fusion-plugins-extra/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-extra/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-extra/copyright
/usr/share/doc/compiz-fusion-plugins-main/AUTHORS
/usr/share/doc/compiz-fusion-plugins-main/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-main/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-main/copyright
/usr/share/doc/compiz-gnome/AUTHORS
/usr/share/doc/compiz-gnome/NEWS.gz
/usr/share/doc/compiz-gnome/README
/usr/share/doc/compiz-gnome/TODO
/usr/share/doc/compiz-gnome/changelog.Debian.gz
/usr/share/doc/compiz-gnome/changelog.gz
/usr/share/doc/compiz-gnome/copyright
/usr/share/doc/compiz-plugins/AUTHORS
/usr/share/doc/compiz-plugins/NEWS.gz
/usr/share/doc/compiz-plugins/README
/usr/share/doc/compiz-plugins/TODO
/usr/share/doc/compiz-plugins/changelog.Debian.gz
/usr/share/doc/compiz-plugins/changelog.gz
/usr/share/doc/compiz-plugins/copyright
/usr/share/doc/compizconfig-backend-gconf/AUTHORS
/usr/share/doc/compizconfig-backend-gconf/changelog.Debian.gz
/usr/share/doc/compizconfig-backend-gconf/copyright
/usr/share/doc/compizconfig-settings-manager/AUTHORS
/usr/share/doc/compizconfig-settings-manager/changelog.Debian.gz
/usr/share/doc/compizconfig-settings-manager/copyright
/usr/share/doc/libcompizconfig0/AUTHORS
/usr/share/doc/libcompizconfig0/NEWS.gz
/usr/share/doc/libcompizconfig0/TODO
/usr/share/doc/libcompizconfig0/changelog.Debian.gz
/usr/share/doc/libcompizconfig0/copyright
/usr/share/doc/python-compizconfig/changelog.Debian.gz
/usr/share/doc/python-compizconfig/copyright
/usr/share/gconf/defaults/10_compiz-gnome
/usr/share/gconf/schemas/compiz-3d.schemas
/usr/share/gconf/schemas/compiz-addhelper.schemas
/usr/share/gconf/schemas/compiz-animation.schemas
/usr/share/gconf/schemas/compiz-annotate.schemas
/usr/share/gconf/schemas/compiz-bench.schemas
/usr/share/gconf/schemas/compiz-bicubic.schemas
/usr/share/gconf/schemas/compiz-blur.schemas
/usr/share/gconf/schemas/compiz-bs.schemas
/usr/share/gconf/schemas/compiz-clone.schemas
/usr/share/gconf/schemas/compiz-colorfilter.schemas
/usr/share/gconf/schemas/compiz-core.schemas
/usr/share/gconf/schemas/compiz-crashhandler.schemas
/usr/share/gconf/schemas/compiz-cube.schemas
/usr/share/gconf/schemas/compiz-cubeaddon.schemas
/usr/share/gconf/schemas/compiz-dbus.schemas
/usr/share/gconf/schemas/compiz-decoration.schemas
/usr/share/gconf/schemas/compiz-expo.schemas
/usr/share/gconf/schemas/compiz-extrawm.schemas
/usr/share/gconf/schemas/compiz-ezoom.schemas
/usr/share/gconf/schemas/compiz-fade.schemas
/usr/share/gconf/schemas/compiz-fadedesktop.schemas
/usr/share/gconf/schemas/compiz-firepaint.schemas
/usr/share/gconf/schemas/compiz-fs.schemas
/usr/share/gconf/schemas/compiz-gconf.schemas
/usr/share/gconf/schemas/compiz-gears.schemas
/usr/share/gconf/schemas/compiz-glib.schemas
/usr/share/gconf/schemas/compiz-group.schemas
/usr/share/gconf/schemas/compiz-imgjpeg.schemas
/usr/share/gconf/schemas/compiz-ini.schemas
/usr/share/gconf/schemas/compiz-inotify.schemas
/usr/share/gconf/schemas/compiz-kconfig.schemas
/usr/share/gconf/schemas/compiz-loginout.schemas
/usr/share/gconf/schemas/compiz-mag.schemas
/usr/share/gconf/schemas/compiz-maximumize.schemas
/usr/share/gconf/schemas/compiz-mblur.schemas
/usr/share/gconf/schemas/compiz-minimize.schemas
/usr/share/gconf/schemas/compiz-mousepoll.schemas
/usr/share/gconf/schemas/compiz-move.schemas
/usr/share/gconf/schemas/compiz-neg.schemas
/usr/share/gconf/schemas/compiz-notification.schemas
/usr/share/gconf/schemas/compiz-opacify.schemas
/usr/share/gconf/schemas/compiz-place.schemas
/usr/share/gconf/schemas/compiz-png.schemas
/usr/share/gconf/schemas/compiz-put.schemas
/usr/share/gconf/schemas/compiz-reflex.schemas
/usr/share/gconf/schemas/compiz-regex.schemas
/usr/share/gconf/schemas/compiz-resize.schemas
/usr/share/gconf/schemas/compiz-resizeinfo.schemas
/usr/share/gconf/schemas/compiz-ring.schemas
/usr/share/gconf/schemas/compiz-rotate.schemas
/usr/share/gconf/schemas/compiz-scale.schemas
/usr/share/gconf/schemas/compiz-scaleaddon.schemas
/usr/share/gconf/schemas/compiz-scalefilter.schemas
/usr/share/gconf/schemas/compiz-screenshot.schemas
/usr/share/gconf/schemas/compiz-session.schemas
/usr/share/gconf/schemas/compiz-shelf.schemas
/usr/share/gconf/schemas/compiz-shift.schemas
/usr/share/gconf/schemas/compiz-showdesktop.schemas
/usr/share/gconf/schemas/compiz-showmouse.schemas
/usr/share/gconf/schemas/compiz-snap.schemas
/usr/share/gconf/schemas/compiz-splash.schemas
/usr/share/gconf/schemas/compiz-staticswitcher.schemas
/usr/share/gconf/schemas/compiz-svg.schemas
/usr/share/gconf/schemas/compiz-switcher.schemas
/usr/share/gconf/schemas/compiz-text.schemas
/usr/share/gconf/schemas/compiz-thumbnail.schemas
/usr/share/gconf/schemas/compiz-trailfocus.schemas
/usr/share/gconf/schemas/compiz-video.schemas
/usr/share/gconf/schemas/compiz-vpswitch.schemas
/usr/share/gconf/schemas/compiz-wall.schemas
/usr/share/gconf/schemas/compiz-wallpaper.schemas
/usr/share/gconf/schemas/compiz-water.schemas
/usr/share/gconf/schemas/compiz-widget.schemas
/usr/share/gconf/schemas/compiz-winrules.schemas
/usr/share/gconf/schemas/compiz-wobbly.schemas
/usr/share/gconf/schemas/compiz-workarounds.schemas
/usr/share/gconf/schemas/compiz-zoom.schemas
/usr/share/gnome/wm-properties/compiz-wm.desktop
/usr/share/gnome/wm-properties/compiz.desktop
/usr/share/gnome-control-center/keybindings/50-compiz-desktop-key.xml
/usr/share/gnome-control-center/keybindings/50-compiz-key.xml
/usr/share/locale/af/LC_MESSAGES/compiz.mo
/usr/share/locale/ar/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ar/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/share/locale/bn/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/bn/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/share/locale/ca/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ca/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/share/locale/da/LC_MESSAGES/compiz.mo
/usr/share/locale/de/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/de/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/de/LC_MESSAGES/compiz.mo
/usr/share/locale/el/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/el/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/el/LC_MESSAGES/compiz.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/share/locale/es/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/es/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/es/LC_MESSAGES/compiz.mo
/usr/share/locale/et/LC_MESSAGES/compiz.mo
/usr/share/locale/eu/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/eu/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/share/locale/fa/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fa/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fi/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fi/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/share/locale/fr/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fr/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/share/locale/gl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/gl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/share/locale/gu/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/gu/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/share/locale/he/LC_MESSAGES/compiz.mo
/usr/share/locale/hi/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/hi/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/share/locale/id/LC_MESSAGES/compiz.mo
/usr/share/locale/it/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/it/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/it/LC_MESSAGES/compiz.mo
/usr/share/locale/ja/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ja/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/share/locale/km/LC_MESSAGES/compiz.mo
/usr/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/share/locale/nb/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/nb/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/share/locale/nl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/nl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/share/locale/or/LC_MESSAGES/compiz.mo
/usr/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/share/locale/pl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/share/locale/pt/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pt/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/share/locale/ru/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ru/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/share/locale/sv/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/sv/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/share/locale/tr/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/tr/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/share/man/man1/compiz.1.gz
/usr/share/man/man1/compiz.real.1.gz
/usr/share/pyshared-data/compizconfig-settings-manager
```

Don't know what to make of that.  O_o

---

### Post by Forlong on 2009-01-07
Did you run any other commands in the meantime and/or scripts?

What's the output of ```
dpkg -l | grep compiz
```

Also, run this:
```
locate compiz | grep ^/usr > locate.out
```
And then post the output of
```
cat locate.out
```

---

### Post by draconastar on 2009-01-07
I'm pretty sure that I haven't done anything else other than what you've instructed me to do, at least involving Compiz.

Output of the dpkg command:

```
daren@daren-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.7.6-0ubuntu2~ppa1                                      OpenGL window and compositing manager
ii  compiz-core                                1:0.7.6-0ubuntu2~ppa1                                      OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.6-0ubuntu1~ppa1                                        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.6-0ubuntu1~ppa1                                        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.6-0ubuntu2~ppa1                                      OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.6-0ubuntu2~ppa1                                      OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                             Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              0.7.6-0ubuntu1~ppa1                                        Compiz configuration settings manager
ii  libcompizconfig0                           0.7.6-0ubuntu1~ppa1                                        Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.7.6-0ubuntu1~ppa1                                        Compiz configuration system bindings
```

After running the second bit of code (which I guess just put the output of the locate command into a .out) and running cat locate.out, I still have the same truncated list showing up in Terminal:

```
/usr/lib/compiz/libthumbnail.so
/usr/lib/compiz/libtrailfocus.a
/usr/lib/compiz/libtrailfocus.la
/usr/lib/compiz/libtrailfocus.so
/usr/lib/compiz/libvideo.so
/usr/lib/compiz/libvpswitch.a
/usr/lib/compiz/libvpswitch.la
/usr/lib/compiz/libvpswitch.so
/usr/lib/compiz/libwall.a
/usr/lib/compiz/libwall.la
/usr/lib/compiz/libwall.so
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so
/usr/lib/compiz/libwater.so
/usr/lib/compiz/libwidget.a
/usr/lib/compiz/libwidget.la
/usr/lib/compiz/libwidget.so
/usr/lib/compiz/libwinrules.a
/usr/lib/compiz/libwinrules.la
/usr/lib/compiz/libwinrules.so
/usr/lib/compiz/libwobbly.so
/usr/lib/compiz/libworkarounds.a
/usr/lib/compiz/libworkarounds.la
/usr/lib/compiz/libworkarounds.so
/usr/lib/compiz/libzoom.so
/usr/lib/compizconfig/backends
/usr/lib/compizconfig/backends/libgconf.a
/usr/lib/compizconfig/backends/libgconf.la
/usr/lib/compizconfig/backends/libgconf.so
/usr/lib/compizconfig/backends/libini.so
/usr/lib/libgnome-window-settings1/libcompiz.so
/usr/lib/pkgconfig/compiz-mousepoll.pc
/usr/lib/pkgconfig/compiz-text.pc
/usr/lib/pkgconfig/compizconfig-python.pc
/usr/lib/python2.5/site-packages/compizconfig.so
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-obs.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/lib/libcompizconfig.a
/usr/local/lib/libcompizconfig.la
/usr/local/lib/libcompizconfig.so
/usr/local/lib/libcompizconfig.so.0
/usr/local/lib/libcompizconfig.so.0.0.0
/usr/local/lib/pkgconfig/compiz-animation.pc
/usr/local/lib/pkgconfig/compiz-animationaddon.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/pkgconfig/compiz-mousepoll.pc
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz-text.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compizconfig-python.pc
/usr/local/lib/pkgconfig/libcompizconfig.pc
/usr/local/lib/python2.5/site-packages/compizconfig.a
/usr/local/lib/python2.5/site-packages/compizconfig.la
/usr/local/lib/python2.5/site-packages/compizconfig.so
/usr/local/share/applications/compiz.desktop
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/or/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/pkgconfig/compiz.pc
/usr/share/compiz
/usr/share/compizconfig
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/compiz/3d.xml
/usr/share/compiz/Gnome
/usr/share/compiz/Oxygen
/usr/share/compiz/addhelper.xml
/usr/share/compiz/animation.xml
/usr/share/compiz/annotate.xml
/usr/share/compiz/bench.xml
/usr/share/compiz/bicubic.xml
/usr/share/compiz/blur.xml
/usr/share/compiz/bs.xml
/usr/share/compiz/ccp.xml
/usr/share/compiz/clone.xml
/usr/share/compiz/colorfilter.xml
/usr/share/compiz/compizcap.png
/usr/share/compiz/core.xml
/usr/share/compiz/crashhandler.xml
/usr/share/compiz/cube.xml
/usr/share/compiz/cubeaddon.xml
/usr/share/compiz/dbus.xml
/usr/share/compiz/decoration.xml
/usr/share/compiz/expo.xml
/usr/share/compiz/extrawm.xml
/usr/share/compiz/ezoom.xml
/usr/share/compiz/fade.xml
/usr/share/compiz/fadedesktop.xml
/usr/share/compiz/filters
/usr/share/compiz/firepaint.xml
/usr/share/compiz/freedesktop.png
/usr/share/compiz/fs.xml
/usr/share/compiz/fusioncap.png
/usr/share/compiz/gconf.xml
/usr/share/compiz/gears.xml
/usr/share/compiz/glib.xml
/usr/share/compiz/group.xml
/usr/share/compiz/icon.png
/usr/share/compiz/imgjpeg.xml
/usr/share/compiz/ini.xml
/usr/share/compiz/inotify.xml
/usr/share/compiz/loginout.xml
/usr/share/compiz/mag.xml
/usr/share/compiz/maximumize.xml
/usr/share/compiz/mblur.xml
/usr/share/compiz/minimize.xml
/usr/share/compiz/mousepoll.xml
/usr/share/compiz/move.xml
/usr/share/compiz/neg.xml
/usr/share/compiz/notification.xml
/usr/share/compiz/opacify.xml
/usr/share/compiz/place.xml
/usr/share/compiz/png.xml
/usr/share/compiz/put.xml
/usr/share/compiz/reflection.png
/usr/share/compiz/reflex.xml
/usr/share/compiz/regex.xml
/usr/share/compiz/resize.xml
/usr/share/compiz/resizeinfo.xml
/usr/share/compiz/ring.xml
/usr/share/compiz/rotate.xml
/usr/share/compiz/scale.xml
/usr/share/compiz/scaleaddon.xml
/usr/share/compiz/scalefilter.xml
/usr/share/compiz/screenshot.xml
/usr/share/compiz/session.xml
/usr/share/compiz/shelf.xml
/usr/share/compiz/shift.xml
/usr/share/compiz/showdesktop.xml
/usr/share/compiz/showmouse.xml
/usr/share/compiz/snap.xml
/usr/share/compiz/splash.xml
/usr/share/compiz/splash_background.png
/usr/share/compiz/splash_logo.png
/usr/share/compiz/staticswitcher.xml
/usr/share/compiz/svg.xml
/usr/share/compiz/switcher.xml
/usr/share/compiz/text.xml
/usr/share/compiz/thumbnail.xml
/usr/share/compiz/trailfocus.xml
/usr/share/compiz/video.xml
/usr/share/compiz/vpswitch.xml
/usr/share/compiz/wall.xml
/usr/share/compiz/wallpaper.xml
/usr/share/compiz/water.xml
/usr/share/compiz/widget.xml
/usr/share/compiz/winrules.xml
/usr/share/compiz/wobbly.xml
/usr/share/compiz/workarounds.xml
/usr/share/compiz/zoom.xml
/usr/share/compiz/Gnome/mask.png
/usr/share/compiz/Gnome/overlay.png
/usr/share/compiz/Oxygen/mask.png
/usr/share/compiz/Oxygen/overlay.png
/usr/share/compiz/filters/blackandwhite
/usr/share/compiz/filters/blueish-filter
/usr/share/compiz/filters/contrast
/usr/share/compiz/filters/deuteranopia
/usr/share/compiz/filters/grayscale
/usr/share/compiz/filters/negative
/usr/share/compiz/filters/negative-green
/usr/share/compiz/filters/protanopia
/usr/share/compiz/filters/sepia
/usr/share/compiz/filters/swap-green-blue
/usr/share/compiz/filters/swap-red-blue
/usr/share/compiz/filters/swap-red-green
/usr/share/compizconfig/extra.profile
/usr/share/compizconfig/global.xml
/usr/share/compizconfig/normal.profile
/usr/share/doc/compiz
/usr/share/doc/compiz-core
/usr/share/doc/compiz-fusion-plugins-extra
/usr/share/doc/compiz-fusion-plugins-main
/usr/share/doc/compiz-gnome
/usr/share/doc/compiz-plugins
/usr/share/doc/compizconfig-backend-gconf
/usr/share/doc/compizconfig-settings-manager
/usr/share/doc/libcompizconfig0
/usr/share/doc/python-compizconfig
/usr/share/doc/compiz/changelog.Debian.gz
/usr/share/doc/compiz/changelog.gz
/usr/share/doc/compiz/copyright
/usr/share/doc/compiz-core/AUTHORS
/usr/share/doc/compiz-core/NEWS.gz
/usr/share/doc/compiz-core/README
/usr/share/doc/compiz-core/README.Debian
/usr/share/doc/compiz-core/TODO
/usr/share/doc/compiz-core/changelog.Debian.gz
/usr/share/doc/compiz-core/changelog.gz
/usr/share/doc/compiz-core/copyright
/usr/share/doc/compiz-fusion-plugins-extra/AUTHORS
/usr/share/doc/compiz-fusion-plugins-extra/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-extra/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-extra/copyright
/usr/share/doc/compiz-fusion-plugins-main/AUTHORS
/usr/share/doc/compiz-fusion-plugins-main/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-main/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-main/copyright
/usr/share/doc/compiz-gnome/AUTHORS
/usr/share/doc/compiz-gnome/NEWS.gz
/usr/share/doc/compiz-gnome/README
/usr/share/doc/compiz-gnome/TODO
/usr/share/doc/compiz-gnome/changelog.Debian.gz
/usr/share/doc/compiz-gnome/changelog.gz
/usr/share/doc/compiz-gnome/copyright
/usr/share/doc/compiz-plugins/AUTHORS
/usr/share/doc/compiz-plugins/NEWS.gz
/usr/share/doc/compiz-plugins/README
/usr/share/doc/compiz-plugins/TODO
/usr/share/doc/compiz-plugins/changelog.Debian.gz
/usr/share/doc/compiz-plugins/changelog.gz
/usr/share/doc/compiz-plugins/copyright
/usr/share/doc/compizconfig-backend-gconf/AUTHORS
/usr/share/doc/compizconfig-backend-gconf/changelog.Debian.gz
/usr/share/doc/compizconfig-backend-gconf/copyright
/usr/share/doc/compizconfig-settings-manager/AUTHORS
/usr/share/doc/compizconfig-settings-manager/changelog.Debian.gz
/usr/share/doc/compizconfig-settings-manager/copyright
/usr/share/doc/libcompizconfig0/AUTHORS
/usr/share/doc/libcompizconfig0/NEWS.gz
/usr/share/doc/libcompizconfig0/TODO
/usr/share/doc/libcompizconfig0/changelog.Debian.gz
/usr/share/doc/libcompizconfig0/copyright
/usr/share/doc/python-compizconfig/changelog.Debian.gz
/usr/share/doc/python-compizconfig/copyright
/usr/share/gconf/defaults/10_compiz-gnome
/usr/share/gconf/schemas/compiz-3d.schemas
/usr/share/gconf/schemas/compiz-addhelper.schemas
/usr/share/gconf/schemas/compiz-animation.schemas
/usr/share/gconf/schemas/compiz-annotate.schemas
/usr/share/gconf/schemas/compiz-bench.schemas
/usr/share/gconf/schemas/compiz-bicubic.schemas
/usr/share/gconf/schemas/compiz-blur.schemas
/usr/share/gconf/schemas/compiz-bs.schemas
/usr/share/gconf/schemas/compiz-clone.schemas
/usr/share/gconf/schemas/compiz-colorfilter.schemas
/usr/share/gconf/schemas/compiz-core.schemas
/usr/share/gconf/schemas/compiz-crashhandler.schemas
/usr/share/gconf/schemas/compiz-cube.schemas
/usr/share/gconf/schemas/compiz-cubeaddon.schemas
/usr/share/gconf/schemas/compiz-dbus.schemas
/usr/share/gconf/schemas/compiz-decoration.schemas
/usr/share/gconf/schemas/compiz-expo.schemas
/usr/share/gconf/schemas/compiz-extrawm.schemas
/usr/share/gconf/schemas/compiz-ezoom.schemas
/usr/share/gconf/schemas/compiz-fade.schemas
/usr/share/gconf/schemas/compiz-fadedesktop.schemas
/usr/share/gconf/schemas/compiz-firepaint.schemas
/usr/share/gconf/schemas/compiz-fs.schemas
/usr/share/gconf/schemas/compiz-gconf.schemas
/usr/share/gconf/schemas/compiz-gears.schemas
/usr/share/gconf/schemas/compiz-glib.schemas
/usr/share/gconf/schemas/compiz-group.schemas
/usr/share/gconf/schemas/compiz-imgjpeg.schemas
/usr/share/gconf/schemas/compiz-ini.schemas
/usr/share/gconf/schemas/compiz-inotify.schemas
/usr/share/gconf/schemas/compiz-kconfig.schemas
/usr/share/gconf/schemas/compiz-loginout.schemas
/usr/share/gconf/schemas/compiz-mag.schemas
/usr/share/gconf/schemas/compiz-maximumize.schemas
/usr/share/gconf/schemas/compiz-mblur.schemas
/usr/share/gconf/schemas/compiz-minimize.schemas
/usr/share/gconf/schemas/compiz-mousepoll.schemas
/usr/share/gconf/schemas/compiz-move.schemas
/usr/share/gconf/schemas/compiz-neg.schemas
/usr/share/gconf/schemas/compiz-notification.schemas
/usr/share/gconf/schemas/compiz-opacify.schemas
/usr/share/gconf/schemas/compiz-place.schemas
/usr/share/gconf/schemas/compiz-png.schemas
/usr/share/gconf/schemas/compiz-put.schemas
/usr/share/gconf/schemas/compiz-reflex.schemas
/usr/share/gconf/schemas/compiz-regex.schemas
/usr/share/gconf/schemas/compiz-resize.schemas
/usr/share/gconf/schemas/compiz-resizeinfo.schemas
/usr/share/gconf/schemas/compiz-ring.schemas
/usr/share/gconf/schemas/compiz-rotate.schemas
/usr/share/gconf/schemas/compiz-scale.schemas
/usr/share/gconf/schemas/compiz-scaleaddon.schemas
/usr/share/gconf/schemas/compiz-scalefilter.schemas
/usr/share/gconf/schemas/compiz-screenshot.schemas
/usr/share/gconf/schemas/compiz-session.schemas
/usr/share/gconf/schemas/compiz-shelf.schemas
/usr/share/gconf/schemas/compiz-shift.schemas
/usr/share/gconf/schemas/compiz-showdesktop.schemas
/usr/share/gconf/schemas/compiz-showmouse.schemas
/usr/share/gconf/schemas/compiz-snap.schemas
/usr/share/gconf/schemas/compiz-splash.schemas
/usr/share/gconf/schemas/compiz-staticswitcher.schemas
/usr/share/gconf/schemas/compiz-svg.schemas
/usr/share/gconf/schemas/compiz-switcher.schemas
/usr/share/gconf/schemas/compiz-text.schemas
/usr/share/gconf/schemas/compiz-thumbnail.schemas
/usr/share/gconf/schemas/compiz-trailfocus.schemas
/usr/share/gconf/schemas/compiz-video.schemas
/usr/share/gconf/schemas/compiz-vpswitch.schemas
/usr/share/gconf/schemas/compiz-wall.schemas
/usr/share/gconf/schemas/compiz-wallpaper.schemas
/usr/share/gconf/schemas/compiz-water.schemas
/usr/share/gconf/schemas/compiz-widget.schemas
/usr/share/gconf/schemas/compiz-winrules.schemas
/usr/share/gconf/schemas/compiz-wobbly.schemas
/usr/share/gconf/schemas/compiz-workarounds.schemas
/usr/share/gconf/schemas/compiz-zoom.schemas
/usr/share/gnome/wm-properties/compiz-wm.desktop
/usr/share/gnome/wm-properties/compiz.desktop
/usr/share/gnome-control-center/keybindings/50-compiz-desktop-key.xml
/usr/share/gnome-control-center/keybindings/50-compiz-key.xml
/usr/share/locale/af/LC_MESSAGES/compiz.mo
/usr/share/locale/ar/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ar/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/share/locale/bn/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/bn/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/share/locale/ca/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ca/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/share/locale/da/LC_MESSAGES/compiz.mo
/usr/share/locale/de/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/de/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/de/LC_MESSAGES/compiz.mo
/usr/share/locale/el/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/el/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/el/LC_MESSAGES/compiz.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/share/locale/es/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/es/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/es/LC_MESSAGES/compiz.mo
/usr/share/locale/et/LC_MESSAGES/compiz.mo
/usr/share/locale/eu/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/eu/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/share/locale/fa/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fa/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fi/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fi/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/share/locale/fr/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/fr/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/share/locale/gl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/gl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/share/locale/gu/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/gu/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/share/locale/he/LC_MESSAGES/compiz.mo
/usr/share/locale/hi/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/hi/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/share/locale/id/LC_MESSAGES/compiz.mo
/usr/share/locale/it/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/it/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/it/LC_MESSAGES/compiz.mo
/usr/share/locale/ja/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ja/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/share/locale/km/LC_MESSAGES/compiz.mo
/usr/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/share/locale/nb/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/nb/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/share/locale/nl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/nl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/share/locale/or/LC_MESSAGES/compiz.mo
/usr/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/share/locale/pl/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pl/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/share/locale/pt/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pt/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/share/locale/ru/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/ru/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/share/locale/sv/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/sv/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/share/locale/tr/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/tr/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz-fusion-plugins-extra.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz-fusion-plugins-main.mo
/usr/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/share/man/man1/compiz.1.gz
/usr/share/man/man1/compiz.real.1.gz
/usr/share/pyshared-data/compizconfig-settings-manager

```

Thank you again for working with me through this, I can't tell you how much I appreciate it.  :D

---

### Post by Forlong on 2009-01-07
I see... this is pretty messed up.
What's the content of your **/etc/apt/sources.list**

Edit: and the output of
```
ls /etc/apt/sources.list.d
```

---

### Post by draconastar on 2009-01-07
I don't know how it got that way.  O_o

My source list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ hardy main
deb http://fr.archive.ubuntu.com/ubuntu/ hardy restricted
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

And the ls command output:

```
daren@daren-desktop:~$ ls /etc/apt/sources.list.d
hardy-landure-games.list
```

---

### Post by anxiousdog on 2009-01-07
> **draconastar said:**
> I don't know how it got that way.  O_o

Sorry to jump in here but I'm having the same problems after I updated my Nvidia drivers today. Wondering if that caused issues for you as well...?

---

### Post by Forlong on 2009-01-07
First of all, get rid of this repository:
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

You can either remove it directly form the file or by going to *System &#8594; Administration &#8594; Software Sources* and delete it there (recommended, it should ask you to update your sources then).

Afterwards run this command to completely remove all current Compiz packages:
```
sudo apt-get remove --purge $(dpkg -l | grep compiz | awk '{print $2}')
```

Finally, **reboot** and post the output of
```
sudo updatedb && locate compiz | grep ^/usr
``` yet again

---

### Post by draconastar on 2009-01-07
I'm in a rush, as I'm pretty much out the door to work.  

To answer your question, anxiousdog, no, updating my NVIDIA driver is NOT what caused the problem, of that I'm certain.  I had Compiz working for awhile, and after following lots of advice about how to install plugins, I'm having these problems.  

Forlong, thanks again, and I'll follow your instructions as soon as I get home from work.

---

### Post by draconastar on 2009-01-07
Just walked in the door from work and followed your instructions, Forlong.  After removing the repository, getting rid of all of the Compiz stuff and rebooting, here's the output of the final command given:

```
daren@daren-desktop:~$ sudo updatedb && locate compiz | grep ^/usr
[sudo] password for daren: 
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-obs.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/lib/libcompizconfig.a
/usr/local/lib/libcompizconfig.la
/usr/local/lib/libcompizconfig.so
/usr/local/lib/libcompizconfig.so.0
/usr/local/lib/libcompizconfig.so.0.0.0
/usr/local/lib/pkgconfig/compiz-animation.pc
/usr/local/lib/pkgconfig/compiz-animationaddon.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/pkgconfig/compiz-mousepoll.pc
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz-text.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compizconfig-python.pc
/usr/local/lib/pkgconfig/libcompizconfig.pc
/usr/local/lib/python2.5/site-packages/compizconfig.a
/usr/local/lib/python2.5/site-packages/compizconfig.la
/usr/local/lib/python2.5/site-packages/compizconfig.so
/usr/local/share/applications/compiz.desktop
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn_IN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/eu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/or/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/pkgconfig/compiz.pc
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/gnome/wm-properties/compiz-wm.desktop

```

---

### Post by Forlong on 2009-01-08
Now try
```
sudo rm $(locate compiz | grep ^/usr)
``` again, then reboot and post the output of ```
sudo updatedb && locate compiz | grep ^/usr
```
If the first command went without errors, there should be nothing to post then.

---

### Post by draconastar on 2009-01-08
Yep, nothing to post.  :D  All completed without error, and the locate came back with nothing.

---

### Post by Forlong on 2009-01-09
Sorry for the delay, been kinda busy.

So, let's have a look at
```
dpkg -l | grep compiz
```
and
```
locate compiz
```

---

### Post by draconastar on 2009-01-09
No worries, Forlong.  :D

```
daren@daren-desktop:~$ dpkg -l | grep compiz
daren@daren-desktop:~$ 

```

And the locate is an *absurdly* long list which I had to pop into a locate.out, and is too large to be put into the clipboard for me to copy, I guess.  

It found lots of stuff.  O_o

---

### Post by Forlong on 2009-01-09
Hm... that doesn't really help me.
Let's delete some config files, is that OK for you?

First of all, reset all Compiz settings like this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
Afterwards, delete the config folder, plugins you tried to install and the gconf keys:
```
rm -r ~/.config/compiz
```
```
rm -r ~/.compiz
```
```
rm -r ~/.gconf/apps/compiz
```

Then have a look in your home directory. There is most probably a folder for the Compiz plugins you tried to install. Delete that one.

Then run
```
sudo updatedb && locate compiz | grep -v ^/var
``` and see if it's possible to post here.

---

### Post by draconastar on 2009-01-09
You know much more about this than I do, so anything you think is OK is definitely OK with me.  :D

The final two rm commands did not complete, saying "No such file or directory", which I guess is a good thing since it's getting rid of them anyway.

I found no files or folders in my Home directory having anything to do with Compiz.

As for the locate command... the list is incredibly, unnaturally long.  After moving the output into an Open Office file, it takes up **168 pages of text.**  I really don't know what to make of that.

---

### Post by Forlong on 2009-01-10
Can you attach the text file here?

---

### Post by draconastar on 2009-01-10
I cannot.  No matter what text format I save it as, it's always too big for the forum.  Even after I break it into five parts, each part is too big.  

Ah, just figured out a way.  I turned it into a .doc file (which increased the original file size to 1.3 MB), then zipped it, which reduced it to 80 KB (only 30 more than it's .odt format), and fits inside the 900 some limit for zip files.  

So it should be attached.  :D

---

### Post by Forlong on 2009-01-10
I see... get rid of these two:
```
sudo rm -r /opt/cfinstall ~/.gconf/schemas/apps/compiz
```
I hope this runs well, then, again:
```
sudo updatedb && locate compiz | grep -v ^/var
```

---

### Post by draconastar on 2009-01-10
That looks MUCH better.  Here's the output:

```
daren@daren-desktop:~$ sudo updatedb && locate compiz | grep -v ^/var
/etc/xdg/autostart/compiz-fusion-emerald.desktop
/etc/xdg/autostart/compiz-icon.desktop
/home/daren/Desktop/compizplugins4.sh~
```

The one that's apparently on my Desktop was a script that I had used (which probably got me into this mess), but I can't see it, so I just deleted it through Terminal.

---

### Post by Forlong on 2009-01-11
Alright, now get rid of the remaining ones as well (wonder why the script put them in there anyway):
```
sudo rm /etc/xdg/autostart/compiz-fusion-emerald.desktop /etc/xdg/autostart/compiz-icon.desktop
```
Now reboot and run ```
sudo updatedb && locate compiz
```


btw: the "invisible" file on your desktop was a backup file most probably created by gEdit (GNOME's text editor).
To make such files visible, hit [Strg]+[H] in the file browser. Same goes for files that begin with a dot.

---

### Post by draconastar on 2009-01-11
Thank you for the information.  :D

Here's the output of the locate command:

```
daren@daren-desktop:~$ sudo updatedb && locate compiz
[sudo] password for daren: 
/var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb
/var/cache/apt/archives/compiz-core_1%3a0.7.4-0ubuntu7_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.7.6-0ubuntu2~ppa1_i386.deb
/var/cache/apt/archives/compiz-dev_1%3a0.7.4-0ubuntu7_i386.deb
/var/cache/apt/archives/compiz-fusion-bcop_0.6.0-1_all.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.4-0ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-main_0.7.4-0ubuntu6.2_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-main_0.7.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.7.4-0ubuntu7_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.7.6-0ubuntu2~ppa1_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.7.4-0ubuntu7_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.7.6-0ubuntu2~ppa1_i386.deb
/var/cache/apt/archives/compiz_1%3a0.7.4-0ubuntu7_all.deb
/var/cache/apt/archives/compiz_1%3a0.7.6-0ubuntu2~ppa1_all.deb
/var/cache/apt/archives/compizconfig-backend-gconf_0.7.4-0ubuntu1_i386.deb
/var/cache/apt/archives/compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb
/var/cache/apt/archives/compizconfig-settings-manager_0.7.6-0ubuntu1~ppa1_all.deb
/var/cache/apt/archives/libcompizconfig0_0.7.4-0ubuntu1_i386.deb
/var/cache/apt/archives/libcompizconfig0_0.7.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/python-compizconfig_0.7.4-0ubuntu1_i386.deb
/var/cache/apt/archives/python-compizconfig_0.7.6-0ubuntu1~ppa1_i386.deb
daren@daren-desktop:~$ 


```

Don't know why all of those .deb's are there.

---

### Post by Forlong on 2009-01-11
That's absolutely fine, apt stores them there in case you'd like to (re-)install them at a later time. Then it doesn't have to download them again.

But in our case, we'd like to start from scratch, so clear that cache:
```
sudo apt-get clean
```

So... looks like we're ready to try to install Compiz again.
Let's start with
```
sudo apt-get install compiz
```
Afterwards, run
```
compiz --replace
```

---

### Post by draconastar on 2009-01-11
Compiz install with seemingly no errors; all that outputted was some unpacking, selecting previously unselected, etc.  

compiz --replace yielded this output:

```
daren@daren-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0290 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.



```

As well as working window borders and effects!  :D  That last bit worries me, and some of my open windows had borders but no close or maximize/minimize buttons, but some did.  When I closed the Terminal window, the manager fizzed out again, but I was left with the same borders and effects.  

Sweet!  What next?  :D

****EDIT****

Aha.  Checking "extra" in appearance settings still leaves me with no window borders or effects, and there are some windows that I open where the close button isn't shown, but I can still click on it.  So I'm guessing we're not done just yet.

---

### Post by Forlong on 2009-01-11
The last error message is a bug in Hardy, here's how to fix that:
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```
Now you can install any further Compiz packages via Synaptic.

---

### Post by Forlong on 2009-01-11
> **draconastar said:**
> Checking "extra" in appearance settings still leaves me with no window borders or effects
Hm, that's weird. Go to Synaptic and install any further compiz plugins you'll find.
Also install **simple-ccsm**, which will give you a Custom option in Appereances. Maybe that helps.
> **draconastar said:**
> and there are some windows that I open where the close button isn't shown, but I can still click on it.  So I'm guessing we're not done just yet.
As far as I know, that's a Nvidia related bug. Don't know if you can do anything about it on Hardy. Try switching to another theme.

You can also use Emerald (it's in the repos – so also installable via Synaptic), which is another window decorator.

---

### Post by draconastar on 2009-01-11
Thank you so, so much Forlong.  The fact that you've stuck with me for over a week on this is amazing, and I really appreciate it.

I have *one* more request, and then I'll leave you alone.  The Elements plugin (as well as every other extra plugin) are what got me in trouble in the past.  What's the best, safest way to install these?

****EDIT****

I'm sorry to bother you again, but for some reason when I click on each effect in the Compiz Settings Manager, it doesn't open the options for each, so I am unable to change them.  I got my different window theme working, and a lot of the effects are operational, so it's mostly fine-tuning from here on out, but you seem to be able to do it right.  :D

Also, it does this weird thing now where when I open new windows that aren't automatically maximized, it puts them up in the very top left corner, where the border of the window is behind my Ubuntu menu bar so I can't grab it.  Any idea what the cause is?

---

