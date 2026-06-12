---
title: "Swiftfox - Potential huge error in script, Aysiu Please look"
date: 2006-07-06
forum: General Help
---

### Post by Dr. Nick on 2006-07-06
Ok, I found mention of swiftfox [here]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox"), I noticed that Aysiu helped make the script and wanted to report my findings to someone who was involved with it, and I have no clue what is the best way to contact other author(s) I will send a copy of the following to the email address listed in the script, hope it works.

Here I go

My system:

AMD Athlon64 3000+
Ubuntu Dapper **32bit** (remember 32bit for later)

I went through the script and answered the questions "correctly" (my correct cpu, I just dont run Ubuntu 64bit, I think this is the problem) 

I saw that it was going to remove alot of "unused" packages and never asked for confirmation, once a few started to remove I closed the terminal as fast as humanly possible. This of course messed up dkpg so I had to run [B]
sudo dpkg --configure -a[/B] to get it dpkg working again.

Not being one to admit defeat easily my intrest was peaked. I decided that I wanted to see what all would have been removed so I used the wonderful "tee" command to see what might have been :)

I will post a "tee" output of the script in hopes that it will help. I think the fact that I selected a 64bit processor while on a 32bit OS caused this to occur. Not sure of how to fix this, if it is indeed a bug like I think it is. I think my system is fine due to my fast reflexes, Im just looking out for any other users. I am not sure if selecting a 32bit processor while in a 64bit Ubuntu will have similar occurances.

```
The most recent release of swiftfox is detected to be 1.5.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? 

Please choose your processor architecture for swiftfox. 
Enter the number of your choice from the list below. 
If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm

0: athlon
1: athlon64
2: athlon-xp
3: k6-2
4: pentium2
5: pentium3
6: pentium4
7: pentium-m
Enter your choice of localization: You have chosen CPU architecture "athlon64". Is that correct [y/n]? 
Updating repositories list

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
Writing extended state information...
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Get:5 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Ign http://theli.free.fr ./ Release.gpg
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://theli.free.fr ./ Release
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Get:6 http://security.ubuntu.com dapper-security/main Packages [27.4kB]
Ign http://theli.free.fr ./ Packages
Get:7 http://security.ubuntu.com dapper-security/restricted Packages [4253B]
Hit http://theli.free.fr ./ Packages
Fetched 62.7kB in 1s (44.0kB/s)
Reading package lists...

Making sure libstdc++5 and the old Firefox are installed

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
The following packages are unused and will be REMOVED:
  arj at-spi bittorrent bluez-pin bug-buddy contact-lookup-applet 
  dbus-1-utils deborphan ekiga eog esound evolution evolution-data-server 
  evolution-exchange evolution-plugins evolution-webcal festival 
  festlex-cmu festlex-poslex festvox-kallpc16k file-roller fping gcalctool 
  gconf-editor gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print 
  gimp-python gimp-svg gnome-accessibility-themes gnome-app-install 
  gnome-bluetooth gnome-btdownload gnome-cups-manager gnome-games 
  gnome-games-data gnome-games-extra-data gnome-mag gnome-nettool 
  gnome-pilot gnome-pilot-conduits gnome-screensaver gnome-spell 
  gnome-system-tools gnome-themes gnome-utils gnome-volume-manager 
  gnopernicus gok gstreamer0.10-gnomevfs gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gthumb gtk2-engines-clearlooks gtk2-engines-crux 
  gtk2-engines-highcontrast gtk2-engines-industrial 
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf 
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice 
  gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs 
  gutenprint-locales hal-device-manager hwdb-client im-switch 
  language-selector libapt-pkg-perl libbeecrypt6 libbtctl2 libcompfaceg1 
  libdigest-hmac-perl libdigest-sha1-perl libedata-book1.2-2 
  libedata-cal1.2-1 libestools1.2 libexchange-storage1.2-1 
  libgail-gnome-module libgimp2.0 libglew1 libglib-perl libgnome-mag2 
  libgnome-pilot2 libgnome-speech3 libgnome2-canvas-perl libgnome2-perl 
  libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomevfs2-bin 
  libgpod-common libgpod0 libgtk2-perl libguile-ltdl-1 libgutenprintui2-1 
  libmail-spf-query-perl libnet-cidr-lite-perl libnet-dns-perl 
  libnet-ip-perl libopal-2.2.0 libosp5 libpisync0 libpt-1.10.0 
  libpt-plugins-alsa libpt-plugins-avc libpt-plugins-dc libpt-plugins-oss 
  libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 
  libsdl1.2debian libsdl1.2debian-alsa libsocket6-perl libwmf0.2-7 lzop 
  nautilus-sendto openoffice.org-evolution openoffice.org-gtk p7zip 
  python-launchpad-integration python-vte python2.4-libbtctl rdesktop 
  rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket 
  sharutils sound-juicer spamassassin spamc ssh-askpass-gnome synaptic 
  system-tools-backends tangerine-icon-theme totem totem-gstreamer 
  totem-gstreamer-firefox-plugin tsclient ttf-arphic-ukai ubuntu-artwork 
  ubuntu-docs ubuntu-sounds unattended-upgrades update-manager 
  update-notifier vino vnc-common w3c-dtd-xhtml whois xsane xsane-common 
  xvncviewer zenity 
The following packages have been kept back:
  login passwd ppp 
0 packages upgraded, 0 newly installed, 167 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 442MB will be freed.
Writing extended state information...
(Reading database ... 89268 files and directories currently installed.)
Removing arj ...
Removing gok ...
```

---

### Post by aysiu on 2006-07-06
I did help test the script a bit (never ran into that problem), but *nanotube* is the one who actually put the script together and maintains it.

You may want to send a private message to *[nanotube](http://www.ubuntuforums.org/member.php?u=66474)*.

---

### Post by TheMono on 2006-07-06
Holy crap. I'm hella glad that didn't happen to me lol. Seems like a fairly major error!

---

### Post by Dr. Nick on 2006-07-06
Thanks aysiu, I was just getting ready to email nanotube, didnt think to check if he was a forum memeber.

Thanks for your insanely fast reply and all the work that you do!!

---

### Post by nanotube on 2006-07-06
ok, so... it appears at first glance that all those packages it was trying to remove are dependencies of ubuntu-desktop. since aptitude automatically manages orphan dependencies, for some reason it thought all those things were no longer needed. so, my question is, do you have ubuntu-desktop package installed?

the thing is, at that point, the script has not even started installing swiftfox - it was merely trying to make sure that you have the original firefox, and libstc5 installed. so the error is coming from your package manager (in this case, aptitude), rather than from you choosing a 64bit version of swiftfox. 

so, check for ubuntu-desktop, and... check if your firefox and libstc++5 are installed. if ubuntu-desktop is missing, run
```
sudo aptitude install ubuntu-desktop
```
and that should restore any of the packages that it succeeded in removing before you canceled out.

other than that, i will modify the script to make it ask before aptitude takes any action, just in case, for the future. :)

---

### Post by Dr. Nick on 2006-07-06
I had removed ubuntu-desktop in the past, I have reinstalled it via aptitude and it reinsatalled about 4 packages. When I turned my computer on this morning everything worked like normal so I think I cancled out fast enough.

I have the newest version of firefox installed, I have libstdc++5(not -dev package) and libstdc++6(including -dev) installed. Version 6 is dependant on several packages that are in use so removal is not a option, libstdc++5 is only dependant on ubuntu-desktop and rar.

---

### Post by nanotube on 2006-07-06
[QUOTE=Dr. Nick]I had removed ubuntu-desktop in the past, I have reinstalled it via aptitude and it reinsatalled about 4 packages. When I turned my computer on this morning everything worked like normal so I think I cancled out fast enough.

I have the newest version of firefox installed, I have libstdc++5(not -dev package) and libstdc++6(including -dev) installed. Version 6 is dependant on several packages that are in use so removal is not a option, libstdc++5 is only dependant on ubuntu-desktop and rar.[/QUOTE]

ok, so ubuntu-desktop is installed now, great. libstdc5 does not conflict with libstdc6, so it's no problem to have them both installed. now that ubuntu-desktop is there, download the swiftfoxisnstall script again (i have modified it so that aptitude asks you before applying any changes, so you won't be taken by surprise again, even if it tries to do anything funny), and run it. this time, it should work properly.

for the future, unfortunately, i cannot make the script check that ubuntu-desktop is installed, because not everyone is running gnome... i will investigate aptitude and see if there are any flags i can pass it so that it does not attempt to remove any packages.

so, please try running the new script and report here if it worked right.

---

### Post by Dr. Nick on 2006-07-06
That apperars to have fixed it all. I selcted athlon64 and it looks like it ran perfectly. Thanks for the help.
When I ran the script I had ubuntu-desktop and the libstdc ver 5 and 6 installed. firefox doesnt appear any differnet then before visually, the Help -> About has no mention of swiftfox, Is that normal? I think it worked anyway since it seems a bit faster, and the script said it was linking firefox to swiftfox which does appear in /opt/swiftfox

```
The most recent release of swiftfox is detected to be 1.5.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? Please choose your processor architecture for swiftfox. Enter the number of your choice from the list below. If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm
0: athlon
1: athlon64
2: athlon-xp
3: k6-2
4: pentium2
5: pentium3
6: pentium4
7: pentium-m
Enter your choice of localization: You have chosen CPU architecture "athlon64". Is that correct [y/n]? 
Updating repositories list

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Ign http://theli.free.fr ./ Release.gpg
Get:4 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper-updates Release
Get:5 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Ign http://theli.free.fr ./ Release
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://theli.free.fr ./ Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Get:6 http://security.ubuntu.com dapper-security/main Packages [27.4kB]
Hit http://theli.free.fr ./ Packages
Get:7 http://security.ubuntu.com dapper-security/restricted Packages [4253B]
Fetched 62.7kB in 1s (46.9kB/s)
Reading package lists...

Making sure libstdc++5 and the old Firefox are installed

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information...

Backing up old Firefox preferences


Changing to home directory


Downloading Swiftfox from the Swiftfox site


Downloading Swiftfox md5 sum from the Swiftfox site


Verifying md5sum...
If the script terminates at this point, the download was corrupt, and you should delete the swiftfox downloads and run this script again.


Unzipping the .tar.gz file


Removing the unzipped .tar.gz


Linking plugins


Linking firefox launcher to Swiftfox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

Swiftfox version "1.5.0.4" for architecture "athlon64" has been installed successfully.
```

---

### Post by nanotube on 2006-07-06
[QUOTE=Dr. Nick]That apperars to have fixed it all. I selcted athlon64 and it looks like it ran perfectly. Thanks for the help.
When I ran the script I had ubuntu-desktop and the libstdc ver 5 and 6 installed. firefox doesnt appear any differnet then before visually, the Help -> About has no mention of swiftfox, Is that normal? I think it worked anyway since it seems a bit faster, and the script said it was linking firefox to swiftfox which does appear in /opt/swiftfox

```
The most recent release of swiftfox is detected to be 1.5.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? Please choose your processor architecture for swiftfox. Enter the number of your choice from the list below. If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm
0: athlon
1: athlon64
2: athlon-xp
3: k6-2
4: pentium2
5: pentium3
6: pentium4
7: pentium-m
Enter your choice of localization: You have chosen CPU architecture "athlon64". Is that correct [y/n]? 
Updating repositories list

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Ign http://theli.free.fr ./ Release.gpg
Get:4 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper-updates Release
Get:5 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Ign http://theli.free.fr ./ Release
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://theli.free.fr ./ Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Get:6 http://security.ubuntu.com dapper-security/main Packages [27.4kB]
Hit http://theli.free.fr ./ Packages
Get:7 http://security.ubuntu.com dapper-security/restricted Packages [4253B]
Fetched 62.7kB in 1s (46.9kB/s)
Reading package lists...

Making sure libstdc++5 and the old Firefox are installed

Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information...

Backing up old Firefox preferences


Changing to home directory


Downloading Swiftfox from the Swiftfox site


Downloading Swiftfox md5 sum from the Swiftfox site


Verifying md5sum...
If the script terminates at this point, the download was corrupt, and you should delete the swiftfox downloads and run this script again.


Unzipping the .tar.gz file


Removing the unzipped .tar.gz


Linking plugins


Linking firefox launcher to Swiftfox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

Swiftfox version "1.5.0.4" for architecture "athlon64" has been installed successfully.
```[/QUOTE]

looks good. that's what it was supposed to look like in the first place... i wonder what was up with it.

anyway, to make sure you are running swiftfox, and not just old firefox, run command
```
ls -al /usr/bin/firefox
ls -al /usr/bin/mozilla-firefox
```

these should be shown as links linking to /opt/swiftfox/firefox
swiftfox is not going to show anything different in help>about, since its just a straight build of firefox sourcecode, with some extra compiler flags. so that's normal. :)

---

### Post by Dr. Nick on 2006-07-06
well I guess I was actually runnig normal firefox before, I restarted my computer and clicked on firefox and it asked to set swiftfox as the default browser which I did. And now swiftfox appears in the title bar instead of firefox.

I guess the problem before was just the lack of ubuntu-desktop package. It is weird that aptitude would want to remove all of that just because of the matapackage not being their.

Its cool that I can find a problem just before going to sleep and it be fixed shortly after I wake up.

---

