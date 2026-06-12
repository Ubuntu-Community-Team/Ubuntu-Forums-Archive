---
title: "Cairo crashes at Ubuntu 12.04 LTS"
date: 2013-11-12
forum: General Help
---

### Post by vagkavo on 2013-11-12
Hi guys,

I am running Ubuntu 12.04 LTS and I am trying to customize my Desktop. For that reason, I play around with Cairo Dock.
However after a while, Cairo package crashes and disappear and I receive the common message that Ubuntu 12.04 experience an internal error.

This is what I get, by running Cairo in Terminal (cairo-dock &)


> dejan@dejan-ThinkPad-Edge-E320:~$ warning :  (/build/buildd/cairo-dock-3.3.2/src/implementations/cairo-dock-glx.c:_initialize_opengl_backend:179)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...


 ============================================================================
    Cairo-Dock version : 3.3.2
    Compiled date      : Oct 29 2013 14:37:35
    Built with GTK     : 3.4
    Running with OpenGL: 0
 ============================================================================


Cairo-Dock - Launcher API Daemon is already running (3559)
GldiShortkey '<Super>L' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Super>L' (Log out: Lock the screen)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Control>F12' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Control>F12' (Log out: Show the logout menu)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Shift><Ctrl>F4' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Shift><Ctrl>F4' (Show Desktop: Expose all the desktops)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Control>F6' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Control>F6' (Quick Browser: Show/hide the folder menu)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Control>F1' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Control>F1' (Applications Menu: Show/hide the Applications menu)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Control>F2' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Control>F2' (Applications Menu: Show/hide the quick-launch dialogue)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Control>F10' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Control>F10' (Recent-Events: Show/hide the Recent Events)
 This shortkey is probably already used by another applet or another application
GldiShortkey '<Super>Return' failed!
warning :  (/build/buildd/cairo-dock-3.3.2/src/gldit/cairo-dock-keybinder.c:init_object:455)  
  Couldn't bind '<Super>Return' (Control from keyboard: Enable/disable the keyboard control of the dock)
 This shortkey is probably already used by another applet or another application






DO you have any idea how could I solve that...?

It's the 1st time I am posting and don't have any experience in Ubuntu, thus excuse me if my question seem to be foolish :p

---

### Post by ibjsb4 on 2013-11-13
I also run Cairo-dock/12o4 and get these warnings, but no crashes with the dock.

How did you install cario-dock?  I ask because I am running Cairo-Dock version : 3.0.0 from the software-center and your running 3.3.2

Here's mine:

```
============================================================================
    Cairo-Dock version : 3.0.0
    Compiled date      : Jun  6 2012 16:39:26
    Built with GTK     : 3.4
    Running with OpenGL: 0
 ============================================================================

_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
CairoKeyBinding '<Control>F1' failed!
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:283)  
  Couldn't bind '<Control>F1' (Applications Menu: Show/hide the Applications menu)
 This shortkey is probably already used by another applet or another application
CairoKeyBinding '<Control>F2' failed!
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:283)  
  Couldn't bind '<Control>F2' (Applications Menu: Show/hide the quick-launch dialog)
 This shortkey is probably already used by another applet or another application
```

---

### Post by vagkavo on 2013-11-13
Thanks for the reply.****
I installed it either from Ubuntu software center, or from Ubuntu Tweak.
When did you install it..? Right now the **_cairo-dock 3.3.2-0ubuntu0~precise_** version is available at the Ubuntu software center.
Do you experience any problems..?
Do think that this is a version's problem..?

---

### Post by ibjsb4 on 2013-11-13
Sounds like you have installed the PPA, which would then show up in the software-center.

[https://launchpad.net/~cairo-dock-team/+archive/ppa?field.series_filter=precise](https://launchpad.net/~cairo-dock-team/+archive/ppa?field.series_filter=precise)

3.3.2 is listed as a package for the next Ubuntu release (14.04), but it does say thats its a stable release.  I can only speak for the package I have installed.  It has worked without issue since the install.  Thinking back on it, there were issues with getting it tweaked out, freezing being one of them.  But all has been well since.

If you wish to try the default version then just remove or disable this PPA from software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by vagkavo on 2013-11-13
Do you mean that as it is already installed, just to remove the PPA related to Cairo dock..?

---

### Post by ibjsb4 on 2013-11-13
Yes, **un**check the PPA and update.  When you remove or uncheck a PPA, if there is a default package, it will restore that package.  In this case that would be 3.0.0.

If problems persist, try purging cairo in terminal.

First remove the hidden file in your home folder.  Open Nautilus and press Ctrl + H then go to .config and remove cairo-dock.  Then ..

```
sudo apt-get remove --purge cairo-dock && sudo apt-get install cario-dock
```

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by vagkavo on 2013-11-15
Sorry if I didn't understand well, but by typing the above command into the terminal, again the 3.3.2 version was installed.
Probably, you meant something else, didn't you..?
Thanks

---

### Post by ibjsb4 on 2013-11-15
That should of worked.  Please post the output of:

```
ls /etc/apt/sources.list.d/
```

---

### Post by vagkavo on 2013-11-15
this is the output

> alanbell-unity-precise.listalanbell-unity-precise.list.save
cairo-dock-team-ppa-precise.list
cairo-dock-team-ppa-precise.list.save
diesch-testing-precise.list
diesch-testing-precise.list.save
ferramroberto-sopcast-precise.list
ferramroberto-sopcast-precise.list.save
ffdiaporamateam-stable-precise.list
ffdiaporamateam-stable-precise.list.save
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.save
google-chrome.list
google-chrome.list.save
ikarosdev-unity-revamped-precise.list
indicator-multiload-stable-daily-precise.list
indicator-multiload-stable-daily-precise.list.save
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save
screenlets-ppa-precise.list
screenlets-ppa-precise.list.save
tsbarnes-indicator-keylock-precise.list
tsbarnes-indicator-keylock-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
yorba-ppa-precise.list
yorba-ppa-precise.list.save




---

### Post by ibjsb4 on 2013-11-16
> cairo-dock-team-ppa-precise.list
cairo-dock-team-ppa-precise.list.save

The PPA is still there.  It appears you skipped the part about the removal of the PPA (post #4) or you did not update after this step.

Terminal update command:
```

sudo apt-get update
```


Edit:  An afterthought.  This link may help with a better understanding ppa removal and the different ways it can be done.

.[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

---

### Post by vagkavo on 2013-11-16
I don't know but it seems that I can't remove these PPAs.
I am running 

> [FONT=Ubuntu Mono]ls /etc/apt/sources.list.d[/FONT]

and I get

> alanbell-unity-precise.listalanbell-unity-precise.list.save
cairo-dock-team-ppa-precise.list
cairo-dock-team-ppa-precise.list.save
diesch-testing-precise.list
diesch-testing-precise.list.save
ferramroberto-sopcast-precise.list
ferramroberto-sopcast-precise.list.save
ffdiaporamateam-stable-precise.list
ffdiaporamateam-stable-precise.list.save
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.save
google-chrome.list
google-chrome.list.save
ikarosdev-unity-revamped-precise.list
ikarosdev-unity-revamped-precise.list.save
indicator-multiload-stable-daily-precise.list
indicator-multiload-stable-daily-precise.list.save
libreoffice-libreoffice-4-1-precise.list
libreoffice-libreoffice-4-1-precise.list.save
libreoffice-ppa-precise.list
libreoffice-ppa-precise.list.save
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_minitube-ubuntu_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save
screenlets-ppa-precise.list
screenlets-ppa-precise.list.save
tsbarnes-indicator-keylock-precise.list
tsbarnes-indicator-keylock-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
yorba-ppa-precise.list
yorba-ppa-precise.list.save




After that by 

> [FONT=Ubuntu Mono]sudo rm -i /etc/apt/sources.list.d/[/FONT]cairo-dock-team-ppa-precise.list

and

> [FONT=Ubuntu Mono]sudo rm -i /etc/apt/sources.list.d/[/FONT]cairo-dock-team-ppa-precise.list.save

I am trying to remove the Cairo ppa, but after the update they are still there

---

### Post by ibjsb4 on 2013-11-17
Your commands remove the package and not the source.  That is why 'software sources' was suggested to remove the package.

Edit: Even though I have removed PPAs with software-sources in the past.  I have ran across this:

[http://ubuntuforums.org/showthread.php?t=1950136&p=11807806#post11807806](http://ubuntuforums.org/showthread.php?t=1950136&p=11807806#post11807806)

Just do it in terminal.

[http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)

ppa-purge works well

---

