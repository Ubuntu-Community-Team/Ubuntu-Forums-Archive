---
title: "purge, re-install LibreOffice"
date: 2016-08-28
forum: General Help
---

### Post by rolfUser on 2016-08-28
Was trying to uninstall and maybe purge altogether, LibreOffice. Then re-install.
When I upgraded from Ubuntu 14.04 to 16.04, I noticed that the previous dark theme (from Unity Tweak Tool) I had previously installed had stayed with LibreOffice even when I changed to default theme after upgrading.

I started here:
[http://anglehit.com/how-to-remove-libreoffice-from-ubuntu-linux-the-command-line-way/](http://anglehit.com/how-to-remove-libreoffice-from-ubuntu-linux-the-command-line-way/)

when I hit
```
[COLOR=#1D1D1D][FONT=&amp]sudo apt-get autoremove[/FONT][/COLOR]
```
Look at what outputted:
```
Reading package lists... 
DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-peas-1.0 : Depends: libpeas-1.0-0 (>= 1.18.0) but 1.16.0-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.
```

After entering **apt-get -f install**...
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

So there's a contingency I'm not meeting and still don't know how to meet it. Guessing to start with Nautilus, but then what?
Also tried uninstalling from Ubuntu Software and it doesn't want to remove.

---

### Post by howefield on 2016-08-28
So did you run..

```
sudo apt-get -f install
```

---

### Post by rolfUser on 2016-08-28
> **howefield said:**
> So did you run..

```
sudo apt-get -f install
```

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-rsvg-2.0 gstreamer0.10-ffmpeg gstreamer0.10-gconf libabw-0.1-1v5
  libavcodec54 libavdevice53 libavformat54 libavresample1 libavutil52
  libboost-python1.58.0 libcdaudio1 libcdr-0.1-1 libcmis-0.5-5v5
  libe-book-0.1-1 libeot0 libetonyek-0.1-1 libfdk-aac0 libfreehand-0.1-1
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libmspub-0.1-1
  libmwaw-0.3-3 libodfgen-0.1-1 libopenjpeg2 liborcus-0.10-0v5
  libpagemaker-0.0-0 libpeas-1.0-0-python3loader librevenge-0.0-0 libslv2-9
  libsqlite0 libswscale2 libtorrent-rasterbar8 libvisio-0.1-1 libvpx1:i386
  libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libx264-142 python-espeak
  python-eyed3 python-gtksourceview2 python-libtorrent python-mutagen
  python-pysqlite2 python-sqlite python-webkit python3-mutagen
  rhythmbox-plugin-android-remote rhythmbox-plugin-artdisplay
  rhythmbox-plugin-close-on-hide rhythmbox-plugin-desktopart
  rhythmbox-plugin-equalizer rhythmbox-plugin-fileorganizer
  rhythmbox-plugin-fullscreen rhythmbox-plugin-hide rhythmbox-plugin-llyrics
  rhythmbox-plugin-opencontainingfolder rhythmbox-plugin-parametriceq
  rhythmbox-plugin-podcast-pos rhythmbox-plugin-radio-browser
  rhythmbox-plugin-rating-filters rhythmbox-plugin-repeat-one-song
  rhythmbox-plugin-smallwindow rhythmbox-plugin-tray-icon
  rhythmbox-plugin-wikipedia streamripper
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libpeas-1.0-0
The following packages will be upgraded:
  libpeas-1.0-0
1 upgraded, 0 newly installed, 0 to remove and 71 not upgraded.
2 not fully installed or removed.
Need to get 197 kB of archives.
After this operation, 43.0 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial/main amd64 libpeas-1.0-0 amd64 1.18.0-2~ubuntu16.04.1~ppa1 [197 kB]
Fetched 197 kB in 1s (126 kB/s)         
(Reading database ... 500957 files and directories currently installed.)
Preparing to unpack .../libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb ...
Unpacking libpeas-1.0-0 (1.18.0-2~ubuntu16.04.1~ppa1) over (1.16.0-1ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libpeas-1.0/loaders/libpython3loader.so', which is also in package libpeas-1.0-0-python3loader 1.16.0-1ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2016-08-30
The error message is in fairly plain language:
> [COLOR=#000000][FONT=&amp]dpkg: error processing archive /var/cache/apt/archives/libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb (--unpack):[/FONT][/COLOR][COLOR=#000000][FONT=&amp] trying to overwrite '/usr/lib/libpeas-1.0/loaders/libpython3loader.so', which is also in package libpeas-1.0-0-python3loader 1.16.0-1ubuntu2[/FONT][/COLOR]

Two packages cannot provide the same file. Two packages that provide the same file *conflict* and cannot both be installed at the same time. 
This occasionally happens with PPA and other third-party software.
You, the admin, must decide which package you want installed.

---

### Post by rolfUser on 2016-08-31
[COLOR=#000000]That explains a lot.
When I access my Files, a new Files icon appears in the same bar and I can only select my Files from this new icon. RhythmBox no longer appears.... what else?

So how would I know which package to use? I should delete the old one and let the new one get installed, right? If so, what should I do??  How would I know which is the correct package?
[/COLOR]

---

### Post by ian-weisser on 2016-09-01
Look for the one that is in the Ubuntu Repositories. Generally rule out PPAs and other non-Ubuntu software first.

In this case, the existing package, libpeas-1.0-0-python3loader/xenial,now 1.16.0-1ubuntu2, is the package to keep.
Delete the PPA from your sources.
Delete the libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb package from your package cache.
Then run an apt update to refresh your package database based on the changed sources.

This should return you to your original problem,
```
The following packages have unmet dependencies:
 gir1.2-peas-1.0 : Depends: libpeas-1.0-0 (>= 1.18.0) but 1.16.0-1ubuntu2 is installed
```
Once you get back there, it should be fairly easy to solve.

---

### Post by rolfUser on 2016-09-05
So I get on the terminal and type...
[FONT=courier new]sudo apt-get rm [/FONT][COLOR=#000000][FONT=courier new]libpeas-1.0-0-python3loader/xenial,now 1.16.0-1ubuntu2[/FONT]     ?

I'm not that sure how a lot of things are done on Linux. I'm just glad that it works the way it does/[/COLOR]

---

### Post by ian-weisser on 2016-09-06
Almost.

1) Delete the PPA from your sources:
Do this in your apt sources: Either System Settings --> Software & Updates --> Other Software OR /etc/apt/sources.list/ (or sources.list.d/)

2) [COLOR=#000000]Delete the libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb package from your package cache.
sudo apt clean [/COLOR]libpeas-1.0-0

3) [COLOR=#000000]Then run an apt update to refresh your package database based on the changed sources.[/COLOR]
[COLOR=#000000]sudo apt update
[/COLOR]

---

### Post by rolfUser on 2016-09-14
> **ian-weisser said:**
> Almost.

1) Delete the PPA from your sources:
Do this in your apt sources: Either System Settings --> Software & Updates --> Other Software OR /etc/apt/sources.list/ (or sources.list.d/)

2) [COLOR=#000000]Delete the libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb package from your package cache.
sudo apt clean [/COLOR]libpeas-1.0-0

3) [COLOR=#000000]Then run an apt update to refresh your package database based on the changed sources.[/COLOR]
[COLOR=#000000]sudo apt update
[/COLOR]


So here's what I think I should do:

1) Get to the terminal and type in:
[FONT=courier new]sudo apt-get purge ppa:libreoffice/ppa

[FONT=arial]2) I'm not sure[/FONT][/FONT][FONT=arial]
[/FONT]
3) On the terminal type in:
[FONT=courier new]sudo apt-get update[/FONT]

---

### Post by howefield on 2016-09-14
> **rolfUser said:**
> sudo apt-get purge ppa:libreoffice/ppa

That won't get rid of the ppa, use this command to keep the file but not use it..

```
sudo mv /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.save
```

Alternatively as pointed out, use the Software & Updates application via the *Other Software* tab.

Then do your 
```
sudo apt-get update
```

---

### Post by rolfUser on 2016-09-14
After inputting...
[FONT=&amp]sudo mv /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.save[/FONT]

```
mv: cannot stat '/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list': No such file or directory
```

I tried deleting LibreOffice from the Software Center, but it doesn't let me.

---

### Post by howefield on 2016-09-14
> **rolfUser said:**
> ```
mv: cannot stat '/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list': No such file or directory
```

Ok, what is the output of this command ?

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by rolfUser on 2016-09-14
```
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/c_falco-mame-trusty.list.distUpgrade:deb http://ppa.launchpad.net/c.falco/mame/ubuntu trusty main
/etc/apt/sources.list.d/costales-anoise-trusty.list.distUpgrade:deb http://ppa.launchpad.net/costales/anoise/ubuntu trusty main
/etc/apt/sources.list.d/elementary-os-daily-trusty.list.distUpgrade:deb http://ppa.launchpad.net/elementary-os/daily/ubuntu trusty main
/etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-wily.list:deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu wily main
/etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-xenial.list:deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial main
/etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-xenial.list.save:deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial main
/etc/apt/sources.list.d/fossfreedom-rhythmbox-plugins-trusty.list.distUpgrade:deb http://ppa.launchpad.net/fossfreedom/rhythmbox-plugins/ubuntu trusty main
/etc/apt/sources.list.d/fossfreedom-rhythmbox-trusty.list:deb http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/fossfreedom-rhythmbox-trusty.list.distUpgrade:deb http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu trusty main
/etc/apt/sources.list.d/fossfreedom-rhythmbox-trusty.list.save:deb http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/jonoomph-openshot-edge-trusty.list.distUpgrade:deb http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu trusty main
/etc/apt/sources.list.d/libreoffice-ppa-trusty.list:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/libreoffice-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
/etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/libretro-stable-trusty.list.distUpgrade:deb http://ppa.launchpad.net/libretro/stable/ubuntu trusty main
/etc/apt/sources.list.d/lucioc-sayonara-trusty.list:deb http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/lucioc-sayonara-trusty.list.distUpgrade:deb http://ppa.launchpad.net/lucioc/sayonara/ubuntu trusty main
/etc/apt/sources.list.d/lucioc-sayonara-trusty.list.save:deb http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/maateen-ubuntu-battery-monitor-xenial.list:deb http://ppa.launchpad.net/maateen/battery-monitor/ubuntu xenial main
/etc/apt/sources.list.d/maateen-ubuntu-battery-monitor-xenial.list.save:deb http://ppa.launchpad.net/maateen/battery-monitor/ubuntu xenial main
/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.distUpgrade:deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
/etc/apt/sources.list.d/nicola-onorata-ubuntu-desktop-xenial.list:deb http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial main
/etc/apt/sources.list.d/nicola-onorata-ubuntu-desktop-xenial.list.save:deb http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial main
/etc/apt/sources.list.d/noobslab-themes-trusty.list.distUpgrade:deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
/etc/apt/sources.list.d/openshot_developers-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu trusty main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list.distUpgrade:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main
/etc/apt/sources.list.d/pmcenery-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu trusty main
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_interest-calculation_ubuntu.list.distUpgrade:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/interest-calculation/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf
/etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main
/etc/apt/sources.list.d/shutter-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/shutter/ppa/ubuntu trusty main
/etc/apt/sources.list.d/tualatrix-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
/etc/apt/sources.list.d/ubuntutrucchi.list.distUpgrade:deb http://www.muflone.com/repositories/ubuntutrucchi ubuntu main non-free #Repository Ubuntu Trucchi
/etc/apt/sources.list.d/videolan-stable-daily-trusty.list.distUpgrade:deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu trusty main
/etc/apt/sources.list.d/vlijm-takeabreak-trusty.list.distUpgrade:deb http://ppa.launchpad.net/vlijm/takeabreak/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-ubuntu-sublime-text-3-xenial.list:deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-sublime-text-3-xenial.list.save:deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial main
```

---

### Post by howefield on 2016-09-14
Ok, try this..

```
sudo mv /etc/apt/sources.list.d/libreoffice-ppa-trusty.list /etc/apt/sources.list.d/libreoffice-ppa-trusty.save
```

Btw, I'd wouldn't advise mixing the trusty and xenial ppas that you have in there.

---

### Post by speartip on 2016-09-14
That is one incredible sources list. No wonder you've had problems after upgrading. Personally I would delete all of the sources after line 19, update the sources list, and start again adding only xenial ppas.
This could easily be done using synaptic & keeping only the official repos. Then purge LibreOffice & reinstall just the official one.
 Using that many 3rd party ppas is asking for problems, particularly on upgrade. It might be beneficial for you to only add ppas for programs you absolutely need, & stick to the official packages in the repos for everything else.

---

### Post by rolfUser on 2016-09-14
> **speartip said:**
> That is one incredible sources list. No wonder you've had problems after upgrading. Personally I would delete all of the sources after line 19, update the sources list, and start again adding only xenial ppas.
This could easily be done using synaptic & keeping only the official repos. Then purge LibreOffice & reinstall just the official one.
 Using that many 3rd party ppas is asking for problems, particularly on upgrade. It might be beneficial for you to only add ppas for programs you absolutely need, & stick to the official packages in the repos for everything else.

Hi!

Thanks for the input. When my PC asked to upgrade, along the way, it asked if I wanted to replace my existing files. Something along those lines. I think I chose to replace, thinking my PC would be the most updated.
During the installation of the upgrade, I noticed that when I clicked on my Files, a new Files icon appeared.  After the upgrade, this still happens.

Anyway, you sound like you have a plan that could work. I appreciate the support.

---

### Post by rolfUser on 2016-09-14
> **howefield said:**
> Ok, try this..

```
sudo mv /etc/apt/sources.list.d/libreoffice-ppa-trusty.list /etc/apt/sources.list.d/libreoffice-ppa-trusty.save
```

Btw, I'd wouldn't advise mixing the trusty and xenial ppas that you have in there.


Okay. Inputted. terminal asked for my password. Nothing was outputted. What does this command do?

---

### Post by howefield on 2016-09-14
> **rolfUser said:**
> Okay. Inputted. terminal asked for my password. Nothing was outputted. What does this command do?

No output means the command was successful, you'd only expect output were there an error to report like you got initially because the file name was incorrect, I'd expected a xenial libreoffice ppa not a trusty one which is why I asked for a full output of your sources.

All the command did was disable the libreoffice ppa by renaming the file. The file is still there but won't be used, and can be reversed easily if required but as I said you really want to look at removing the trusty ppas in favour of ones built for xenial.

---

### Post by rolfUser on 2016-09-14
Okay so what should I input?

---

### Post by howefield on 2016-09-14
> **rolfUser said:**
> Okay so what should I input?

Well, having read the whole thread if it were mine I'd remove all the ppas (as speartip suggested) - you could use the command

```
sudo mv /etc/apt/sources.list.d/*.* ~/Documents
```

This will remove all the ppa file and store the files in your Documents folder that you can refer to later or delete once happy.
 
Alternatively if you prefer to use the GUI, load up the "*Software and Updates*" and deselect everything in the "*Other Software*" tab (personally I'd also deselect the sources option in the Ubuntu Software tab but that doesn't matter for now). You'll be prompted to enter your password, do so and press the reload button once you have done unchecking the PPAs.

That should take you to where you can solve the issue with libpeas.

---

### Post by rolfUser on 2016-09-14
Remove all the ppa files and store them in my Documents folder?
Do we really need to take all of them? Won't that cause all of my programs to stop working?

I'm only trying to remove LibreOffice so I can reinstall it. The dark theme I previously had while in Ubuntu 14.04 had stuck despite having reset it to default after upgrading to 16.04.

---

### Post by ian-weisser on 2016-09-14
> **rolfUser said:**
> Remove all the ppa files and store them in my Documents folder?
Do we really need to take all of them? Won't that cause all of my programs to stop working?

I'm only trying to remove LibreOffice so I can reinstall it. The dark theme I previously had while in Ubuntu 14.04 had stuck despite having reset it to default after upgrading to 16.04.

*"Sources"* like PPAa are merely the place on the internet  where you get software from. Removing a source won't break the software. Removing the source merely prevents the software from updating from that source. The software can still update from other sources.
 
After you uninstall the LibreOffice from some unsupported non-Ubuntu PPA, you will install the tested and supported version of Libreoffice from the Ubuntu sources. This will revert your LibreOffice a version or two...but your system will work again.

Again, the first milestone toward fixing your system is to revert your non-Ubuntu software to the Ubuntu versions (from the Ubuntu repositories), because those are tested and supported to prevent precisely such conflicts.

The most common reason for breakage like yours in systems like yours is too many non-Ubuntu sources.

---

### Post by howefield on 2016-09-15
> **rolfUser said:**
> Remove all the ppa files and store them in my Documents folder?
Do we really need to take all of them? Won't that cause all of my programs to stop working?

As above, removing the PPA files and reverting to stock Ubuntu repositories is only a temporary fix so you can remove the libpeas package that prevented you from uninstalling Libreoffice. The PPAs can be returned after you are done here, but with a suggested caveat of putting back only those that you really need and only those that have a xenial repository. As explained above removing the PPA files from /etc/apt/sources.list.d/ won't stop your software working, the packages installed by them will simply not update.

If this is a step too far for your sensibilities, you could try to establish which ppa the libpeas package comes from.

What is the output from...

```
apt-cache policy gir1.2-peas-1.0
```

> I'm only trying to remove LibreOffice so I can reinstall it. The dark theme I previously had while in Ubuntu 14.04 had stuck despite having reset it to default after upgrading to 16.04.

Have you tried deleting or renaming the libreoffice folder in your ~/.config/libreoffice folder ? to force libreoffice into creating a fresh "profile".

---

### Post by rolfUser on 2016-09-15
After inputting...
```
apt-cache policy gir1.2-peas-1.0
```

The output is as follows...
```
gir1.2-peas-1.0:
  Installed: 1.18.0-2~ubuntu16.04.1~ppa1
  Candidate: 1.18.0-2~ubuntu16.04.1~ppa1
  Version table:
 *** 1.18.0-2~ubuntu16.04.1~ppa1 500
        500 http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1.16.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```


> **howefield said:**
> Have you tried deleting or renaming the libreoffice folder in your ~/.config/libreoffice folder ? to force libreoffice into creating a fresh "profile".
I have not tried that. I haven't thought of it. 


> **ian-weisser said:**
> *"Sources"* like PPAa are merely the place on the internet where you get software from. Removing a source won't break the software. Removing the source merely prevents the software from updating from that source. The software can still update from other sources.

After you uninstall the LibreOffice from some unsupported non-Ubuntu PPA, you will install the tested and supported version of Libreoffice from the Ubuntu sources. This will revert your LibreOffice a version or two...but your system will work again.

Again, the first milestone toward fixing your system is to revert your non-Ubuntu software to the Ubuntu versions (from the Ubuntu repositories), because those are tested and supported to prevent precisely such conflicts.

The most common reason for breakage like yours in systems like yours is too many non-Ubuntu sources.
Okay. I think typing this into the terminal is the correct next step:
```
[COLOR=#000000]sudo mv /etc/apt/sources.list.d/*.* ~/Documents[/COLOR]
```

---

### Post by howefield on 2016-09-15
> **rolfUser said:**
> 
```
gir1.2-peas-1.0:
  Installed: 1.18.0-2~ubuntu16.04.1~ppa1
  Candidate: 1.18.0-2~ubuntu16.04.1~ppa1
  Version table:
 *** 1.18.0-2~ubuntu16.04.1~ppa1 500
        500 http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1.16.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

OK, so the libpeas package comes from the nicola-onorata PPA.

Either remove all PPAs as suggested or disable the nicola-onorata PPA which appears to be where the libpeas package installed from. What is your preference ?

---

### Post by howefield on 2016-09-15
Incidentally and slightly off topic, but can I ask what you use the nicola-onorata PPA for ?

I am mildly surprised you still have a (sort of) working operating system at all :)

---

### Post by rolfUser on 2016-09-15
nicola-onorata PPA.... don't know how I got it. What is it?
If I remove all PPAs, so will the [COLOR=#000000]nicola-onorata... so I guess I will choose to remove all PPAs/

Maybe I got this PPA from installing themes. Earlier this week I was trying to install QtsixA ([/COLOR]http://qtsixa.sourceforge.net/[COLOR=#000000]), which allows you to use a Playstation 3 controller on your Linux distribution. So there's this video game called AM2R: Return of Samus.....

---

### Post by howefield on 2016-09-15
> **rolfUser said:**
> nicola-onorata PPA.... don't know how I got it. What is it?
If I remove all PPAs, so will the [COLOR=#000000]nicola-onorata... so I guess I will choose to remove all PPAs/

OK, you already know how to move all the PPA files, if you just want to disable the nicola-onorata ppa, use

```
sudo mv /etc/apt/sources.list.d/nicola-onorata-ubuntu-desktop-xenial.* ~/Documents
```

According to your sources output that should move 2 files to your Documents folder.

Then remove the package gir1.2-peas-1.0..

```
sudo apt remove gir1.2-peas-1.0
```

Pay attention to what it wants to remove, if you are worried post back :)

then

```
sudo apt update
```

Hopefully, no errors ?

Then you can put back the Ubuntu repository gir1.2-peas-1.0 package with

```
sudo apt install gir1.2-peas-1.0
```

> Maybe I got this PPA from installing themes. Earlier this week I was trying to install QtsixA ([/COLOR]http://qtsixa.sourceforge.net/[COLOR=#000000]), which allows you to use a Playstation 3 controller on your Linux distribution.

Frankly, I would want to clean install this machine :)

---

### Post by speartip on 2016-09-15
> **howefield said:**
> Frankly, I would want to clean install this machine :)
Think I agree there. Or you could try using the "ppa-purge" package to revert back to the official packages.
 I've hosed my system to many times using 3rd party ppas, to get the latest version of something, when the version in the repos works just fine.
 Stick with what's tried & tested, unless absolutely necessary.

---

### Post by rolfUser on 2016-09-15
input:
```
[COLOR=#000000][FONT=&amp]sudo mv /etc/apt/sources.list.d/nicola-onorata-ubuntu-desktop-xenial.* ~/Documents[/FONT][/COLOR]
```
No output, and two files appeared instantly in my Documents folder just as you said. They are:
[LIST]
[*]nicola-onorata-ubuntu-desktop-xenial.list
[*]nicola-onorata-ubuntu-desktop-xenial.list.save
[/LIST]

input:
```
sudo apt remove gir1.2-peas-1.0
```
output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 eog : Depends: gir1.2-peas-1.0 but it is not going to be installed
 gedit : Depends: gir1.2-peas-1.0 but it is not going to be installed
 totem-plugins : Depends: gir1.2-peas-1.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I did not proceed to update after this. Maybe better to look over it, then decide. 

I think I agree that purging out all repositories might be a good solution.    I know that I can use the Computer Janitor under Ubuntu Tweak to clean out old, unnecessary packages.    Ever since I upgraded to 16.04, I refused to touch it.     I first started to used it with 14.04 on my new PC.       Then I tried installing it on another PC running Ubuntu 12.04   and used the Janitor to "clean out" old files. 
That was the last time I got to run Ubuntu on that PC.    It was dual-booted with Windows 7, and when you select Ubuntu, all you see is a black screen with a blinking cursor.     I think you'd have to reinstall from Windows but it is not a priority.

---

### Post by ian-weisser on 2016-09-15
> **rolfUser said:**
> ```
The following packages have unmet dependencies:
 eog : Depends: gir1.2-peas-1.0 but it is not going to be installed
 gedit : Depends: gir1.2-peas-1.0 but it is not going to be installed
 totem-plugins : Depends: gir1.2-peas-1.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Please try the following, and show us the complete output.
```
sudo apt remove gir1.2-peas-1.0 eog gedit totem-plugins
```




> **rolfUser said:**
> I think I agree that purging out all repositories might be a good solution.    I know that I can use the Computer Janitor under Ubuntu Tweak to clean out old, unnecessary packages.
Apt does not require any 'janitor' or 'tweak' helper application to keep your system clean...but such helpers are indeed available if you find them convenient. 
1) Occasionally use 'sudo apt autoremove' to clean out orphaned packages. Or use unattended-upgrades to run if for you.
2) Occasionally use 'sudo apt autoclean' to clean out old packages in your /var/cache/apt/archives cache. Or use unattended-upgrades to run if for you.
3) Occasionally audit your non-Ubuntu sources to see if still want them. If not, uninstall the software and remove the source.
4) Before a release upgrade, uninstall all non-Ubuntu software and return the system to as close to a stock state as possible.

---

### Post by rolfUser on 2016-09-15
input:
```
[COLOR=#000000][FONT=&quot]sudo apt remove gir1.2-peas-1.0 eog gedit totem-plugins[/FONT][/COLOR]
```

output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-rsvg-2.0 gstreamer0.10-ffmpeg gstreamer0.10-gconf libabw-0.1-1v5
  libavcodec54 libavdevice53 libavformat54 libavresample1 libavutil52
  libboost-python1.58.0 libcdaudio1 libcdr-0.1-1 libcmis-0.5-5v5
  libe-book-0.1-1 libeot0 libetonyek-0.1-1 libfdk-aac0 libfreehand-0.1-1
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libmspub-0.1-1
  libmwaw-0.3-3 libodfgen-0.1-1 libopenjpeg2 liborcus-0.10-0v5
  libpagemaker-0.0-0 libpeas-1.0-0-python3loader librevenge-0.0-0 libslv2-9
  libsqlite0 libswscale2 libtorrent-rasterbar8 libvisio-0.1-1 libvpx1:i386
  libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libx264-142 python-espeak
  python-eyed3 python-gtksourceview2 python-libtorrent python-mutagen
  python-pysqlite2 python-sqlite python-webkit python3-mutagen
  rhythmbox-plugin-android-remote rhythmbox-plugin-artdisplay
  rhythmbox-plugin-close-on-hide rhythmbox-plugin-desktopart
  rhythmbox-plugin-equalizer rhythmbox-plugin-fileorganizer
  rhythmbox-plugin-fullscreen rhythmbox-plugin-hide rhythmbox-plugin-llyrics
  rhythmbox-plugin-opencontainingfolder rhythmbox-plugin-parametriceq
  rhythmbox-plugin-podcast-pos rhythmbox-plugin-radio-browser
  rhythmbox-plugin-rating-filters rhythmbox-plugin-repeat-one-song
  rhythmbox-plugin-smallwindow rhythmbox-plugin-tray-icon
  rhythmbox-plugin-wikipedia streamripper
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  eog gedit gir1.2-peas-1.0 totem-plugins
0 upgraded, 0 newly installed, 4 to remove and 136 not upgraded.
2 not fully installed or removed.
After this operation, 5,589 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 500956 files and directories currently installed.)
Removing gedit (3.18.3-1~ubuntu16.04.1~ppa1) ...
Removing eog (3.18.2-1ubuntu1) ...
Removing totem-plugins (3.18.1-1ubuntu4) ...
Removing gir1.2-peas-1.0 (1.18.0-2~ubuntu16.04.1~ppa1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
```

---

### Post by rolfUser on 2016-09-15
[ATTACH=CONFIG]271209[/ATTACH][ATTACH=CONFIG]271210[/ATTACH][ATTACH=CONFIG]271211[/ATTACH]
Software Updater asked if I wanted to update. Maybe this information is important.

---

### Post by ian-weisser on 2016-09-15
It is important, and happily expected.

Try the following four commands, and please show us the complete output of the entire session.
If one command should happen to fail or error, then stop. Show us the session.
```
sudo apt autoremove
          # This command should remove about 65-70 orphaned and unused packages, including many Rhythmbox add-ons.
          # Don't panic. You can get them back easily later.


sudo apt clean
          # This command empties your onboard package cache at /var/cache/apt/archives
          # Packages from the removed PPA(s) are likely cached there. We need to empty the cache so those non-Ubuntu packages don't get reinstalled.
          # This command should have no output


sudo apt update
          # This command scans each Software Source and updates your onboard database of known and available packages.
          # We need to update the database because your sources changed.


sudo apt upgrade
          # This command will upgrade 136 packages waiting in various sources. The output will be lengthy.
          # We hope this command completes without any version errors.
```

---

### Post by rolfUser on 2016-09-15
input:
```
[COLOR=#000000][FONT=&amp]sudo apt autoremove[/FONT][/COLOR]
```
output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-rsvg-2.0 gstreamer0.10-ffmpeg gstreamer0.10-gconf libabw-0.1-1v5
  libavcodec54 libavdevice53 libavformat54 libavresample1 libavutil52
  libboost-python1.58.0 libcdaudio1 libcdr-0.1-1 libcmis-0.5-5v5
  libe-book-0.1-1 libeot0 libetonyek-0.1-1 libfdk-aac0 libfreehand-0.1-1
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libmspub-0.1-1
  libmwaw-0.3-3 libodfgen-0.1-1 libopenjpeg2 liborcus-0.10-0v5
  libpagemaker-0.0-0 libpeas-1.0-0-python3loader librevenge-0.0-0 libslv2-9
  libsqlite0 libswscale2 libtorrent-rasterbar8 libvisio-0.1-1 libvpx1:i386
  libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libx264-142 python-espeak
  python-eyed3 python-gtksourceview2 python-libtorrent python-mutagen
  python-pysqlite2 python-sqlite python-webkit python3-mutagen
  rhythmbox-plugin-android-remote rhythmbox-plugin-artdisplay
  rhythmbox-plugin-close-on-hide rhythmbox-plugin-desktopart
  rhythmbox-plugin-equalizer rhythmbox-plugin-fileorganizer
  rhythmbox-plugin-fullscreen rhythmbox-plugin-hide rhythmbox-plugin-llyrics
  rhythmbox-plugin-opencontainingfolder rhythmbox-plugin-parametriceq
  rhythmbox-plugin-podcast-pos rhythmbox-plugin-radio-browser
  rhythmbox-plugin-rating-filters rhythmbox-plugin-repeat-one-song
  rhythmbox-plugin-smallwindow rhythmbox-plugin-tray-icon
  rhythmbox-plugin-wikipedia streamripper
0 upgraded, 0 newly installed, 67 to remove and 136 not upgraded.
After this operation, 56.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 499272 files and directories currently installed.)
Removing rhythmbox-plugin-desktopart (0.3.0-1~rb3ubuntu1) ...
Removing gir1.2-rsvg-2.0:amd64 (2.40.13-3) ...
Removing gstreamer0.10-ffmpeg:amd64 (0.10.13-5ubuntu1~trusty2) ...
Removing gstreamer0.10-gconf:amd64 (0.10.31-3+nmu4ubuntu2~gcc5.1) ...
Removing libabw-0.1-1v5:amd64 (0.1.1-2ubuntu2) ...
Removing libavdevice53:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libavformat54:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libavcodec54:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libavresample1:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libswscale2:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libavutil52:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing python-libtorrent (1.0.7-1build1) ...
Removing libboost-python1.58.0 (1.58.0+dfsg-5ubuntu3.1) ...
Removing libcdaudio1:amd64 (0.99.12p2-14) ...
Removing libcdr-0.1-1:amd64 (0.1.2-2ubuntu2) ...
Removing libcmis-0.5-5v5:amd64 (0.5.1-2ubuntu2) ...
Removing libe-book-0.1-1:amd64 (0.1.2-2ubuntu1) ...
Removing libeot0:amd64 (0.01-3ubuntu1) ...
Removing libetonyek-0.1-1:amd64 (0.1.6-1ubuntu1) ...
Removing libfdk-aac0:amd64 (0.1.3.1) ...
Removing libfreehand-0.1-1:amd64 (0.1.1-1ubuntu1) ...
Removing python-gtksourceview2 (2.10.1-2build1) ...
Removing libgtksourceview2.0-0 (2.10.5-2ubuntu2) ...
Removing libgtksourceview2.0-common (2.10.5-2ubuntu2) ...
Removing libgtkspell0 (2.0.16-1.1ubuntu1) ...
Removing libmspub-0.1-1:amd64 (0.1.2-2ubuntu1) ...
Removing libmwaw-0.3-3:amd64 (0.3.7-1ubuntu2) ...
Removing libodfgen-0.1-1 (0.1.6-1ubuntu2) ...
Removing libopenjpeg2:amd64 (1.3+dfsg-4.7ubuntu1) ...
Removing liborcus-0.10-0v5:amd64 (0.9.2-4ubuntu2) ...
Removing libpagemaker-0.0-0:amd64 (0.0.3-1ubuntu1) ...
Removing libpeas-1.0-0-python3loader (1.16.0-1ubuntu2) ...
Removing libwps-0.4-4:amd64 (0.4.3-1ubuntu1) ...
Removing libwpg-0.3-3:amd64 (0.3.1-1ubuntu1) ...
Removing libslv2-9:amd64 (0.6.6+dfsg1-3build1) ...
Removing rhythmbox-plugin-android-remote (0.2-1) ...
Removing python-sqlite (1.0.1-12) ...
Removing libsqlite0 (2.8.17-12fakesync1) ...
Removing libtorrent-rasterbar8 (1.0.7-1build1) ...
Removing libvisio-0.1-1:amd64 (0.1.5-1ubuntu1) ...
Removing libvpx1:i386 (1.3.0-3~trusty) ...
Removing libwpd-0.10-10:amd64 (0.10.1-1ubuntu1) ...
Removing libx264-142:amd64 (3:0.142.2491+git24e4fed-1~trusty) ...
Removing python-espeak (0.5-1build3) ...
Removing rhythmbox-plugin-fileorganizer (3.0-1) ...
Removing python-eyed3 (0.6.18-1) ...
Removing python-mutagen (1.31.0-1) ...
Removing python-pysqlite2 (2.7.0-1) ...
Removing python-webkit (1.1.8-3.1) ...
Removing python3-mutagen (1.31.0-1) ...
Removing rhythmbox-plugin-artdisplay (0.3.1-1~rb3) ...
Removing rhythmbox-plugin-close-on-hide (0.1-1) ...
Removing rhythmbox-plugin-equalizer (0.4.0-1~rb3) ...
Removing rhythmbox-plugin-fullscreen (0.7.1-1) ...
Removing rhythmbox-plugin-hide (0.2-1) ...
Removing rhythmbox-plugin-llyrics (1.1-1~rb3) ...
Removing rhythmbox-plugin-opencontainingfolder (0.2-4~rb3) ...
Removing rhythmbox-plugin-parametriceq (0.2.2-1) ...
Removing rhythmbox-plugin-podcast-pos (0.2-1) ...
Removing rhythmbox-plugin-radio-browser (0.5.2-1~rb3) ...
Removing rhythmbox-plugin-rating-filters (0.2-2~rb3) ...
Removing rhythmbox-plugin-repeat-one-song (0.4.0-1ubuntu1) ...
Removing rhythmbox-plugin-smallwindow (0.2.2-1) ...
Removing rhythmbox-plugin-tray-icon (0.3-1ubuntu1) ...
Removing rhythmbox-plugin-wikipedia (0.1-3~rb3) ...
Removing streamripper (1.64.6-1) ...
Removing librevenge-0.0-0:amd64 (0.0.4-4ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
```
input:
```
[COLOR=#000000][FONT=&amp]sudo apt clean[/FONT][/COLOR]
```
no output
input:```
[COLOR=#000000][FONT=&amp]sudo apt update[/FONT][/COLOR]
```
output:```
Ign:1 http://dl.google.com/linux/chrome/deb stable InReleaseHit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Ign:5 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu wily InRelease           
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Ign:7 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial InRelease         
Hit:9 http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu xenial InRelease   
Hit:10 http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial InRelease        
Hit:11 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Hit:12 http://ppa.launchpad.net/maateen/battery-monitor/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial InRelease
Err:14 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu wily Release
  404  Not Found
Err:15 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial Release
  404  Not Found
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Sources [188 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [94.2 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [386 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [381 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [147 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [326 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [323 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [113 kB]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu wily Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

** I want to stop really quick and make a note of something: I see the word "wily" in the output. This may be in reference to something I did to try to get QtSixA to start working:[http://askubuntu.com/questions/409761/how-do-i-use-a-ps3-sixaxis-controller-with-ubuntu-to-control-games](http://askubuntu.com/questions/409761/how-do-i-use-a-ps3-sixaxis-controller-with-ubuntu-to-control-games)

So I'm not sure to proceed with the next command.
**

---

### Post by howefield on 2016-09-16
> **rolfUser said:**
> ** I want to stop really quick and make a note of something: I see the word "wily" in the output. This may be in reference to something I did to try to get QtSixA to start working:[http://askubuntu.com/questions/409761/how-do-i-use-a-ps3-sixaxis-controller-with-ubuntu-to-control-games](http://askubuntu.com/questions/409761/how-do-i-use-a-ps3-sixaxis-controller-with-ubuntu-to-control-games)

Use the following to move the wily repositories out of the way, again, it'll move the files to your Documents folder for later review/deletion.

```
sudo mv /etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-wily.* ~/Documents
```

Then again do

```
sudo apt update
```

and

```
sudo apt upgrade
```

---

### Post by howefield on 2016-09-16
OK, missed you also had a xenial repository for the /falk-t-j-ubuntu-qtsixa repository, use 

```
sudo mv /etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-xenial* ~/Documents
```

Then
```
sudo apt update
```
and
```
sudo apt upgrade
``` 
should complete without error ?

---

### Post by rolfUser on 2016-09-16
I also want to mention that I have _both_ Software Center (after upgrade to Ubuntu 16.04) and Ubuntu Software Center (kept since Ubuntu 14.04). Gedit mysteriously vanished while I followed a command to update or upgrade or something--I had not attempted to reinstall. Now I just use Notepad because I have Wine installed. Sublime Text appears to work just fine, though I'm new to it.



input:```
[COLOR=#000000][FONT=&amp]sudo mv /etc/apt/sources.list.d/falk-t-j-ubuntu-qtsixa-xenial* ~/Documents[/FONT][/COLOR]
```
This file(s) appears under Documents folder:
[LIST]
[*]falk-t-j-ubuntu-qtsixa-xenial.list.save
[*]falk-t-j-ubuntu-qtsixa-xenial.list
[/LIST]

input:```
[COLOR=#000000][FONT=&amp]sudo apt update[/FONT][/COLOR]
```
output:
```
Ign:1 http://dl.google.com/linux/chrome/deb stable InReleaseHit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:5 http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu xenial InRelease   
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Hit:7 http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial InRelease         
Hit:8 http://ppa.launchpad.net/maateen/battery-monitor/ubuntu xenial InRelease 
Hit:10 http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial InRelease
Hit:11 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [386 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [381 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [326 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [323 kB]
Fetched 1,606 kB in 7s (227 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

input:```
[COLOR=#000000][FONT=&amp]sudo apt upgrade[/FONT][/COLOR]
```
output:```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  librhythmbox-core9 linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic
  linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by ian-weisser on 2016-09-16
That's very good output.
Unless I misunderstand, seems from here like your problem is fixed.

You should probably run 'sudo apt autoremove' one more time to clean out those obsolete kernels.
After that, go ahead and try installing something (like re-installing your rhythmbox tools, if you still want them).

Best practice is to install from the Ubuntu Repositories.
Google and the glossy webzines and the random blogs won't tell you that. They want you to add PPAs and dodgy, edgy sources...but where were they when your system broke and you needed support?
It's your system, and you can install from any source you please...as long as you understand how to undo any damage.

---

### Post by howefield on 2016-09-16
> **rolfUser said:**
> ...Gedit mysteriously vanished while I followed a command to update or upgrade or something--I had not attempted to reinstall. Now I just use Notepad because I have Wine installed. Sublime Text appears to work just fine, though I'm new to it.

Not so mysterious, earlier back in the thread when you uninstalled gir1.2-peas-1.0, gedit was removed along with a couple of other packages, it was installed via the nicola-onorata repository and updated the default Ubuntu gedit package, may well be the same with eog (image viewer) and the totem-plugins, reinstalling (if you wish) them should now give you the default versions from the Ubuntu repositories.

---

### Post by rolfUser on 2016-09-16
After hitting [COLOR=#000000] 'sudo apt autoremove' ,
I can't remember, I completely forgot.[/COLOR][COLOR=#000000] I think it said it would free up 267 MB, had to restart afterwards.

Tried uninstalling LibreOffice from Ubuntu Software Center, but it seemed like another problem. I opened Ubuntu Software and it did work, eventually. I restarted again.  Then I proceeded to re-install Gedit, LibreOffice, and Rhythmbox from Ubuntu Software.  From the looks of things, not only did the theme remain the same, but the version as well.

Before:  
[/COLOR][ATTACH=CONFIG]271236[/ATTACH]


and after...

[ATTACH=CONFIG]271234[/ATTACH][ATTACH=CONFIG]271233[/ATTACH][ATTACH=CONFIG]271235[/ATTACH]


I do appreciate everything ~ I'm taking notes on this.

Is there anything else to go over, before marking this thread as SOLVED? 
I know that after this, I'm going to refrain from QtSixA and maybe opt for an xbox or Steam controller.

---

### Post by howefield on 2016-09-17
> **rolfUser said:**
> Tried uninstalling LibreOffice from Ubuntu Software Center, but it seemed like another problem. I opened Ubuntu Software and it did work, eventually. I restarted again.  Then I proceeded to re-install Gedit, LibreOffice, and Rhythmbox from Ubuntu Software.  From the looks of things, not only did the theme remain the same, but the version as well.

Uninstalling an application generally won't remove related files from your /home folder, so simply removing Libreoffice and then reinstalling it may not produce the result you expected. Presumably your "*after*" pictures mean that you have resolved the issue in this thread ?

[quote]Is there anything else to go over, before marking this thread as SOLVED?

Just a reminder that you have a mass of repositories relating to "Trusty". If you don't need then any more, remove them (it'll also speed up your "*sudo apt update*") if you do need them look for a Xenial option.

---

### Post by rolfUser on 2016-09-17
> **howefield said:**
> 
Uninstalling an application generally won't remove related files from your /home folder, so simply removing Libreoffice and then reinstalling it may not produce the result you expected. Presumably your "*after*" pictures mean that you have resolved the issue in this thread ?

It appears to be working fine-- unless you suggest that I actually do purge LibreOffice and then reinstall? If so, is it 'sudo apt purge libreoffice'?

> **howefield said:**
> 
Just a reminder that you have a mass of repositories relating to "Trusty". If you don't need then any more, remove them (it'll also speed up your "*sudo apt update*") if you do need them look for a Xenial option.

That's important. I still get two Documents icons when I select one. Steam doesn't open, XnRetro doesn't open. I don't think Ubuntu Software Center is supposed to be available. I thought to save it for another thread. 
Removing "Trusty" repositories sounds fairly straight-forward, but also a little tricky.  I don't want to go too far off-topic.  Where can I go to learn how to do this?

---

### Post by speartip on 2016-09-17
> **rolfUser said:**
> Removing "Trusty" repositories sounds fairly straight-forward, but also a little tricky.  I don't want to go too far off-topic.  Where can I go to learn how to do this?

This is simple. Install synaptic. Go to Settings-Repositories-Other Software, then untick all the repos relating to Trusty. Then click the Reload button. Job done.

---

### Post by howefield on 2016-09-17
> **rolfUser said:**
> It appears to be working fine-- unless you suggest that I actually do purge LibreOffice and then reinstall? If so, is it 'sudo apt purge libreoffice'?

No, if it is working I'd leave it alone :) 

I'm just pointing out that sometimes you'll have files left in the /home folder after uninstalling software, purging should remove them though, looks like it isn't needed in this case.

> That's important. I still get two Documents icons when I select one. Steam doesn't open, XnRetro doesn't open. I don't think Ubuntu Software Center is supposed to be available. I thought to save it for another thread.

Yes, sounds like a different issue(s), so a different thread is called for.
 
> Removing "Trusty" repositories sounds fairly straight-forward, but also a little tricky.  I don't want to go too far off-topic.  Where can I go to learn how to do this?

No need to install Synaptic, just load the Software & Updates application and uncheck whatever you want to remove from the "*Other Software*" tab, to be honest, the information is already posted to the thread that should allow you to sort out the repositories :)

---

### Post by rolfUser on 2016-09-17
[ATTACH=CONFIG]271241[/ATTACH]
I looked at Synaptic Package Manager, and I'm not ready to work with it. At least not yet.
In Software Updater, I went under 'Other Software'.
I noticed some items were already checked when I looked at it. Why is that?
Should I uncheck those, then check everything that says "Trusty" and then remove?
Even if it says (Source Code) at the end?

If use this, it will take all the PPAs. We only want to get rid of Trusty.
```
[COLOR=#000000][FONT=&quot]sudo mv /etc/apt/sources.list.d/*.* ~/Documents[/FONT][/COLOR]
```

---

### Post by ian-weisser on 2016-09-17
If you want to remove ancient Trusty repos, then do so.
You are the one who added them in the first place. You can easily add them again if you wish...and if you wrote them down.

---

### Post by howefield on 2016-09-18
> **rolfUser said:**
> Should I uncheck those, then check everything that says "Trusty" and then remove? Even if it says (Source Code) at the end?

Unchecking a repository in the Software & Updates tab disables the ppa, to reactivate it is as easy as checking it off again,  highlighting a line and pressing the remove button will remove the file from .../sources.list.d/. Unless you want to use the source code for an application it makes sense to disable the source code repositories, imho. 

> If use this, it will take all the PPAs. We only want to get rid of Trusty.
```
sudo mv /etc/apt/sources.list.d/*.* ~/Documents
```

That's right, so don't use it if all you want to do is remove the Trusty repositories, now that you have found the Software & Updates application, that should be the easy way to manipulate your sources.

---

### Post by rolfUser on 2016-09-20
I don't know if I want any Trusty repositories or not. All I know is that I want a fully functional and updated machine. 
Will this one command ultimately help my computer?  'sudo mv /etc/apt/sources.list.d/*.* ~/Documents' ?
Will it cause it to clean itself? If there is no chance it will hurt my computer, I think the command will only help it.

During the installation of 16.04, I think there were two instances in which prompts asked whether I wanted to use existing system files or to replace them with the new ones. I believe I opted to keep the existing ones. What ever strange anomalies that are going on with my PC, I'm guessing the command is a good step to stabilize it once again.

---

### Post by howefield on 2016-09-20
> **rolfUser said:**
> I don't know if I want any Trusty repositories or not. All I know is that I want a fully functional and updated machine.

Only you know what you want on your machine. You appear to have a fully functional machine now ? 

> Will this one command ultimately help my computer?  'sudo mv /etc/apt/sources.list.d/*.* ~/Documents' ? Will it cause it to clean itself? If there is no chance it will hurt my computer, I think the command will only help it.

All it will do is remove ALL ppa files from /ect/apt/sources.list.d and keep a copy in your Documents folder for reference/deletion.

There won't be any other "cleaning" than that, it would mean that updates to software that you have installed from those repositories will not be applied, so I'd suggest that now having a working system you leave well enough alone. :) It was only suggested when you had the Libreoffice issue which no longer applies and will do more harm than good now.

Any issues that you get in the future can be dealt with, every chance that you won't have any.

> During the installation of 16.04, I think there were two instances in which prompts asked whether I wanted to use existing system files or to replace them with the new ones. I believe I opted to keep the existing ones. What ever strange anomalies that are going on with my PC, I'm guessing the command is a good step to stabilize it once again.

This thread is going in circles now :)

I'd suggest starting new threads for the other issues that you referenced a few posts up and see where that takes you.

---

