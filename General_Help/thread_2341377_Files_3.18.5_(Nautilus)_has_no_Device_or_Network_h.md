---
title: "Files 3.18.5 (Nautilus) has no Device or Network header nor &quot;make link&quot;"
date: 2016-10-27
forum: General Help
---

### Post by Jeff_Rockel on 2016-10-27
Ubuntu 16.04: GUI Files manager (the app formally known as Nautilus) 3.18.5

When I upgraded from 14.04 I found I was not able to move a symbolic link icon on the desktop. After some research, I upgraded gnome and my link moving issue was fixed. However, I now have significant issues with the file manager. 1) When I right click on a file or folder, there is no "make link" command as there used to be. 2) In the left sidebar, there are the default shortcuts, my shortcuts and "+ Other Locations" but no Devices or Network. When i click on "+ Other Locations" the window freezes and I have to force the process to end.

I see three possible solutions: 1) reinstall Files (Nautilus?) to a previous version that works; 2) reinstall Ubuntu 16.04 completely; 3) reinstall Ubuntu 14.04. Any other ideas? (Hope I did screenshot correctly. I wasn't able to screenshot the right-click menu.)
[ATTACH=CONFIG]271810[/ATTACH]

---

### Post by mc4man on 2016-10-27
That would depend on what you're looking for. 
If you're happy with 3.18 except for it hanging on Other Locations then try to resolve that. The first thing to do is log into a guest session & try there. If it works then your issue is local to your user. If not then would have to look elsewhere.
(- If I temp install 3.18 here there is no issue opening Other Locations so it should work ok.

---

### Post by Jeff_Rockel on 2016-11-01
I have investigated my issues more thoroughly and I hope this explanation of my problem is clear. I am unhappy with my nautilus 3.18.5 installation as described above. I am attempting to install a previous version. I have done the following without error.
```
 
dpkg --list #This showed version 3.18.5 in the list
sudo apt-get --purge remove nautilus
dpkg --list #Nautilus is not in the list but "nautilus-data 3.18.5" is
sudo apt-get install nautilus 3.10.2
dpkg --list #Again version 3.18.5 is in the list
sudo apt-get --purge remove nautilus #Try again
sudo apt-get --purge remove nautilus-data #Attempt to remove has errors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-control-center : Depends: gnome-settings-daemon (>= 3.13.91) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Please note also that "nautilus-dropbox" is loaded and may be interfering with this attempt. I would prefer not to mess with dropbox if not necessary. I would appreciate help in understanding what I am doing wrong to uninstall and reinstall nautilus.

---

### Post by CantankRus on 2016-11-01
For your nautilus version to be 3.18.5, wouldn't you have needed to add a ppa with that later version.
eg my default version
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt-cache policy nautilus **
nautilus:
  Installed: 1:3.18.4.is.3.14.3-0ubuntu5
  Candidate: 1:3.18.4.is.3.14.3-0ubuntu5
  Version table:
 *** 1:3.18.4.is.3.14.3-0ubuntu5 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial/main amd64 Packages
```

If that's the case then I would re-enable the ppa where the 3.18.5 version came from and then use ppa-purge
to revert to the default version.

You also need to be wary when you uninstall packages.
eg this is what happens if I attempt to remove nautilus-data so I'm not sure how much damage you have done.

---

### Post by mc4man on 2016-11-01
> **CantankRus said:**
> For your nautilus version to be 3.18.5, wouldn't you have needed to add a ppa with that later version.

likely from here - 
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=xenial](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=xenial)

---

### Post by Jeff_Rockel on 2016-11-01
I may have installed a PPA when I upgraded gnome. (And I don't understand the ins and outs of PPA's.) Even so, I don't understand why I can't install a specific version.

---

### Post by CantankRus on 2016-11-01
> **Jeff_Rockel said:**
> I may have installed a PPA when I upgraded gnome. (And I don't understand the ins and outs of PPA's.) Even so, I don't understand why I can't install a specific version.
Each release of ubuntu has default versions of applications that work happily together.
Newer releases of applications may be dependent on the functionality in newer releases of other applications.
Application packages aren't isolated exe files like windows.

eg
If you run 
```
apt depends nautilus 
```
You will see the different versions of applications your current nautilus version relies upon.
Mostly saying greater than or equal (>=) to a certain version.
```
**glen@Xenial:~$ [COLOR="#006400"]apt depends nautilus[/COLOR]**
nautilus
  Depends: libatk1.0-0 (>= 1.32.0)
  Depends: libc6 (>= 2.14)
  Depends: libcairo-gobject2 (>= 1.10.0)
  Depends: libcairo2 (>= 1.10.0)
  Depends: libdbusmenu-glib4 (>= 0.4.2)
  Depends: libexempi3 (>= 2.2.0)
  Depends: libexif12 (>= 0.6.21-1~)
  Depends: libgail-3-0 (>= 3.0.0)
  Depends: libgdk-pixbuf2.0-0 (>= 2.25.2)
  Depends: libglib2.0-0 (>= 2.39.90)
  Depends: libgnome-desktop-3-12 (>= 3.18.1)
  Depends: libgtk-3-0 (>= 3.16.2)
  Depends: libnautilus-extension1a (>= 1:2.91)
  Depends: libnotify4 (>= 0.7.0)
  Depends: libpango-1.0-0 (>= 1.20.0)
  Depends: libpangocairo-1.0-0 (>= 1.14.0)
  Depends: libselinux1 (>= 1.32)
  Depends: libtracker-sparql-1.0-0 (>= 0.10.0)
  Depends: libunity9 (>= 3.8.4)
  Depends: libx11-6
  Depends: libxml2 (>= 2.7.4)
  Depends: libzeitgeist-2.0-0 (>= 0.9.9)
  Depends: session-migration
  Depends: nautilus-data (>= 1:3.18)
  Depends: nautilus-data (<< 1:3.19)
  Depends: shared-mime-info (>= 0.50)
    shared-mime-info:i386
  Depends: desktop-file-utils (>= 0.7)
    desktop-file-utils:i386
  Depends: gvfs (>= 1.3.2)
  Depends: libglib2.0-data
  Depends: gsettings-desktop-schemas (>= 3.8.0)
  Breaks: gnome-bluetooth (<< 3.0)
  Breaks: gnome-session (<< 2.28)
  Breaks: <gnome-volume-manager> (<< 2.24)
  Breaks: <nautilus-sendto-empathy> (<< 3.0)
  Breaks: rhythmbox (<< 0.12)
  Recommends: librsvg2-common
  Recommends: gvfs-backends
    gvfs-backends:i386
  Suggests: brasero (>= 2.26)
  Suggests: eog
 |Suggests: evince
  Suggests: <pdf-viewer>
    okular
    atril
    evince
    gv
    mupdf
    viewpdf.app
    xpdf
    zathura-pdf-poppler
 |Suggests: totem
  Suggests: <mp3-decoder>
    mpg321
    opencubicplayer
    vlc
    vlc-nox
  Suggests: xdg-user-dirs
    xdg-user-dirs:i386
  Suggests: tracker
  Suggests: gnome-sushi
  Replaces: nautilus-data (<< 1:3.18.1-1ubuntu1)
  Replaces: nautilus-sendto
```

In a lot of cases ppas contain more than just the application you're seeking to upgrade.
Eg gnome3 ppa
[ATTACH=CONFIG]271916[/ATTACH]

So I use the ppa and upgrade.
I don't like this version of nautilus I'm going to uninstall it,disable the ppa  and install the version I had before.
Which it will do, but it will leave behind upgraded versions of other packages from that ppa.
[ATTACH=CONFIG]271917[/ATTACH]

This may or may not cause problems.
What you should do is, with the ppa enabled, use ppa-purge to disable the ppa and revert to official packages.
[**[COLOR="#B22222"]HOW TO USE A LAUNCHPAD PPA (ADD, REMOVE, PURGE, DISABLE) IN UBUNTU[/COLOR]**]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

Linux assumes you know what you are doing and will let you happily do whatever you want with limited warnings.
If you add ppas you should be using synaptic for a better overall view of added ppas and package management.

In addition to this, when you do a system upgrade to a new release of Ubuntu you should purge all added ppas to revert to default packages.


Normally to fix your situation you would open software sources...
```
software-properties-gtk --open-tab 1
```
and re-enable the gnome3 ppa
Then update and purge.
```
sudo apt update
sudo ppa-purge ppa:gnome3-team/gnome3
```

eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sudo ppa-purge ppa:gnome3-team/gnome3**
Updating packages lists
PPA to be removed: gnome3-team gnome3
Package revert list generated:
 gnome-bluetooth/xenial grilo-plugins-0.2-base:amd64/xenial 
libgnome-bluetooth13:amd64/xenial libnautilus-extension1a/xenial 
nautilus/xenial nautilus-data/xenial

Disabling gnome3-team PPA from 
/etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-xenial.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grilo-plugins-0.2-base is already the newest version (0.2.17-0ubuntu2).
Selected version '3.18.2-1ubuntu2' (Ubuntu:16.04/xenial [amd64]) for 'gnome-bluetooth'
Selected version '0.2.17-0ubuntu2' (Ubuntu:16.04/xenial [amd64]) for 'grilo-plugins-0.2-base'
Selected version '3.18.2-1ubuntu2' (Ubuntu:16.04/xenial [amd64]) for 'libgnome-bluetooth13'
Selected version '1:3.18.4.is.3.14.3-0ubuntu5' (Ubuntu:16.04/xenial-updates [amd64]) for 'libnautilus-extension1a'
Selected version '1:3.18.4.is.3.14.3-0ubuntu5' (Ubuntu:16.04/xenial-updates [amd64]) for 'nautilus'
Selected version '1:3.18.4.is.3.14.3-0ubuntu5' (Ubuntu:16.04/xenial-updates [all]) for 'nautilus-data'
Suggested packages:
  brasero tracker gnome-sushi
The following packages will be DOWNGRADED:
  gnome-bluetooth libgnome-bluetooth13 libnautilus-extension1a nautilus nautilus-data
0 to upgrade, 0 to newly install, 5 to downgrade, 0 to remove and 0 not to upgrade.
Need to get 0 B/733 kB of archives.
After this operation, 12.2 MB disk space will be freed.
Do you want to continue? [Y/n] 
dpkg: warning: downgrading libnautilus-extension1a from 1:3.18.5-0ubuntu1~xenial1 to 1:3.18.4.is.3.14.3-0ubuntu5
(Reading database ... 280838 files and directories currently installed.)
Preparing to unpack .../libnautilus-extension1a_1%3a3.18.4.is.3.14.3-0ubuntu5_amd64.deb ...
Unpacking libnautilus-extension1a:amd64 (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.5-0ubuntu1~xenial1) ...
dpkg: warning: downgrading nautilus-data from 1:3.18.5-0ubuntu1~xenial1 to 1:3.18.4.is.3.14.3-0ubuntu5
Preparing to unpack .../nautilus-data_1%3a3.18.4.is.3.14.3-0ubuntu5_all.deb ...
Unpacking nautilus-data (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.5-0ubuntu1~xenial1) ...
dpkg: warning: downgrading nautilus from 1:3.18.5-0ubuntu1~xenial1 to 1:3.18.4.is.3.14.3-0ubuntu5
Preparing to unpack .../nautilus_1%3a3.18.4.is.3.14.3-0ubuntu5_amd64.deb ...
Unpacking nautilus (1:3.18.4.is.3.14.3-0ubuntu5) over (1:3.18.5-0ubuntu1~xenial1) ...
dpkg: warning: downgrading libgnome-bluetooth13:amd64 from 3.18.3-1ubuntu1~xenial1 to 3.18.2-1ubuntu2
Preparing to unpack .../libgnome-bluetooth13_3.18.2-1ubuntu2_amd64.deb ...
Unpacking libgnome-bluetooth13:amd64 (3.18.2-1ubuntu2) over (3.18.3-1ubuntu1~xenial1) ...
dpkg: warning: downgrading gnome-bluetooth from 3.18.3-1ubuntu1~xenial1 to 3.18.2-1ubuntu2
Preparing to unpack .../gnome-bluetooth_3.18.2-1ubuntu2_amd64.deb ...
Unpacking gnome-bluetooth (3.18.2-1ubuntu2) over (3.18.3-1ubuntu1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libnautilus-extension1a:amd64 (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up nautilus-data (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up nautilus (1:3.18.4.is.3.14.3-0ubuntu5) ...
Setting up libgnome-bluetooth13:amd64 (3.18.2-1ubuntu2) ...
Setting up gnome-bluetooth (3.18.2-1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
PPA purged successfully
```

This may not work for you because of other things you may have done in your attempts to revert nautilus.
If it doesn't work and since you said you upgraded Ubuntu from  14.04 which can be problematic anyway, I would backup and do a fresh install of 16.04
and write it off as a learning experience.

---

