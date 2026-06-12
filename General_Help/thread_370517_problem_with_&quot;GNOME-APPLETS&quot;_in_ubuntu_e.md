---
title: "problem with &quot;GNOME-APPLETS&quot; in ubuntu edgy"
date: 2007-02-25
forum: General Help
---

### Post by K-a-M-u-Z-u on 2007-02-25
I have a laptop with ubuntu edgy for a while.everything worked great and usually i managed to solve any problem i'v encoutered with little google search.
i accidently delted "gnome-applets" manualy.
when i rebooted my laptop i got the next messege sfter the startup:
>  The panel encountered a problem while loading "OAFIID:GNOME_CPUFreqApplet". 
an then i got two options:
> do you want to delete the applet from your configuration?
all my laptop controls gone(CPU FREAQUENCY is the mos important so i can choose manualy the speed).
so i tried to install it again and get the messege:
> sudo apt-get install gnome-applets
and got:
>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-applets: Depends: libdbus-1-1 (>= 0.36.2) but it is not going to be installed
                 Depends: libdbus-glib-1-1 (>= 0.36.2) but it is not going to be installed
                 Depends: libnotify0 but it is not going to be installed
                 Depends: libxklavier10 (>= 2.0) but it is not going to be installed
E: Broken packages  

then i tried:
> sudo aptitude reinstall gnome-applets 
and got:
>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done     
gnome-applets is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used. 
then i tried:
> sudo aptitude install gnome-applets 
and got:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done     
The following packages are BROKEN:
  dbus libxklavier11
The following NEW packages will be automatically installed:
  gnome-applets-data gstreamer0.8-alsa imagemagick libdbus-1-1
  libdbus-glib-1-1 libgail17 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtop2-5 libgucharmap4 libmagick6 libnotify0 libxklavier10
The following NEW packages will be installed:
  gnome-applets gnome-applets-data gstreamer0.8-alsa imagemagick
  libdbus-1-1 libdbus-glib-1-1 libgail17 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libgtop2-5 libgucharmap4 libmagick6 libnotify0
  libxklavier10
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6MB of archives. After unpacking 52.0MB will be used.
The following packages have unmet dependencies:
  dbus: Conflicts: libdbus-1-1 but 0.36.2-0ubuntu7.1 is to be installed.
  libxklavier11: Conflicts: libxklavier10 but 2.0-0.2ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-applets [Not Installed]
gnome-applets-data [Not Installed]
libdbus-1-1 [Not Installed]
libdbus-glib-1-1 [Not Installed]
libnotify0 [Not Installed]
libxklavier10 [Not Installed]

Score is 44

Accept this solution? [Y/n/q/?] 

i also tried:
> apt-get update
and then:
> apt-get -f install 

Nothing helped.
so if i cant solve this i need to re-install ubuntu.
the problem is that i have changed so much and to do all the work again...is there any way to reinstall only what i need from the live cd?
or maybe to do install without loosing all the data in my "/" partition?
thanks.
:)

---

