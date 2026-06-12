---
title: "gutsy broken since upgrade of packages last night"
date: 2008-01-08
forum: General Help
---

### Post by humbabba on 2008-01-08
Yesterday I downloaded updates through the regular update feature. The next time I turned on my computer gdm would load, but gnome wouldn't. I could see the taskbars but there were no icons and no background. Then the taskbars flickered and then the screen went black with only the mouse cursor. I heard my hard drive making a lot of noise so I checked top and it listed nautilus as taking a lot of the processor.

I was disgusted so I backed up my files and reinstalled. Everything was working again but after I ran the update sure enough the gui failed to function again in the same way. Surely someone else is having this problem?

---

### Post by flashbackk on 2008-01-08
Same here.  I lost my desktop after an upgrade tonight.

---

### Post by humbabba on 2008-01-09
any clues? What could be wrong? It's something about nautilus or gtk I think. I don't really know which logs to check.

---

### Post by sdb2028 on 2008-01-09
Not really the best thing to say, but... I'm glad someone else is having this problem. I ran an update yesterday and now have a blank screen with the cursor. Thought it was something I did, been backtracking and looking for problems with no luck. I think I will join this thread and  help try to find help.

---

### Post by humbabba on 2008-01-09
I've got to bump this, sorry. I'm in bad shape. My gui's broken and I am not sure why. It happened after an upgrade of packages (see above) a clean install worked but then when I upgraded the packages again the problem returned. Several people are having this problem, where can we look for clues as to what is going on? Or better yet what is going on?

---

### Post by Sidewinder1 on 2008-01-09
Thanks for this post. I was just about to click on the update icon when I saw it. Think I'll wait 'til this gets sorted out. I stink at command-line diagnostics and would rather not take the chance small though it may be.

---

### Post by Sidewinder1 on 2008-01-09
Did you folks rectify the prob yet? I 'ain't" clickin' on the icon 'til there's some answers; one way or the other....

---

### Post by Sidewinder1 on 2008-01-09
Guess I'm on my own; as usual...

---

### Post by ellaguno on 2008-01-09
I thought it was something I did but seems I am also with the same black screen after logging in. Only the cursor. I booted with the second grubs option and startx works including compiz, but can't solve the problem :confused:

---

### Post by Cryptic1911 on 2008-01-09
I'm running 64-bit, but I've done all the current updates and I'm not having any issues. are you guys all 32 bit?

---

### Post by Helios38 on 2008-01-09
ah... im glad i read this b4 i clicked on update, i'll hold off on this update til somebody finds a fix ;)

---

### Post by marx2k on 2008-01-09
2 32-bit and one 64-bit boxes in this house, all running Gutsy. 2 Kubuntu, 1 Ubuntu. Zero problems with all updates

---

### Post by amdalex on 2008-01-09
I gonna stick with Edgy till they work the bugs out.:)

---

### Post by satx on 2008-01-09
All,

To which upgrade are you referring, please?

---

### Post by sdb2028 on 2008-01-09
Not sure, can't get back into the system to find out what happened. What ever the last auto update was that went out Jan 7(thats when I got it)

---

### Post by ellaguno on 2008-01-09
I am 32 bits. I finally solved the problem but was a great pain. 
[LIST=1]
[*]I uninstalled completly the gnome desktop, 
[*]I uninstalled compiz
[*]Installed xubuntu-desktop  (sudo apt-get install xubuntu-desktop)
[*]Logged in with xfce (it worked)
[*]Solved a network problem 
[*]Reinstalled ubuntustudio-desktop (is the one i'm using) (sudo apt-get install ubuntustudio-desktop)
[/LIST]

---

### Post by humbabba on 2008-01-10
I am amd64 to answer that question. Big problem, I jumped ship and am trying suse and it sux and I want my ubuntu back :-(

---

### Post by mistaceo on 2008-01-10
how do you uninstall the gnome-desktop?

---

### Post by manimal347 on 2008-01-10
> **mistaceo said:**
> how do you uninstall the gnome-desktop?

Um,  I'm not sure you should. Its components have lots of dependencies, and will probably demand you remove about half your GUI apps or more (stuff like Nautilus and Epiphany for sure). Just kill GDM (Google has help on this), and add another window manager to tide you over until the Ubuntu (security?)  team fixes whatever packages may have been broken while patching other bugs and security holes. You'll need to do some tweaking of config files and the like in Nano or Vim, just so you know. TWM comes stock with xwindows so you can use that, but It'll probably make you tear your hair out (it was last updated in 1991!) so I suggest you set up Fluxbox or something else simple and very light in the interim. That, or live in Windows or console mode. I have never run an Ubuntu Desktop install (only server-base w/ Fluxbox), so I can't help you here, but I bet there's an Ubuntu Wiki page on adding another window manager to GDM/KDM/XDM. If not, Google and ye shall probably receive. 

----------------- general topic continuation -------------------
This isn't Gentoo, so hearing this kind of surprises me, and dishearteningly reminds me of mothership-Debian's current troubles with the post-Etch branches (I'm a refugee). Now, pardon my French, but I'm darn well  glad I haven't run "sudo apt-get update" in a loooong time.

---

### Post by ellaguno on 2008-01-10
I was sort of desperated so I uninstall a bunch of things. But seems that my problem appeared after the upgrade and using the Suspend function. It seems to be enough to install xfce or as you say fluxbox..

when you boot you may change to a terminal pressing Ctrl+Alt+F1 there you log in and type:
sudo apt-get install xubuntu-desktop

I know it will install you a bunch of other things but at least you will be able to continue working in a different windows environment.

After xfce installs you change back to the graphical login with Ctrl+Alt+F7

There you press "Options">"Session" and select XFCE, then log in and after that you will be able to work. The suspend/hibernate functions work well for me from XFCE. 

The other choice you may have is to log in after selecting "Gnome safe" from the same "Options">"Session" choices in the login window. If you log in you may dissable using Compiz  opening the menu "System">"Appearence" changing to the "Effects" tab and selecting No Effects.

I don't know what created the problem but I'm working already again

---

### Post by mistaceo on 2008-01-10
I tried to install the xubuntu desktop but error upon error has been thrust upon me....

mistaceo@zookbox:/$ sudo apt-get -f install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fast-user-switch-applet: Depends: gdm but it is not going to be installed
  xubuntu-desktop: Depends: gdm but it is not going to be installed
                   Depends: gtk2-engines-murrine but it is not going to be installed
                   Depends: gtk2-engines-xfce but it is not going to be installed
                   Depends: thunar but it is not going to be installed
                   Depends: thunar-volman but it is not going to be installed
                   Depends: xfce4-mcs-plugins but it is not going to be installed
                   Depends: xfce4-mixer but it is not going to be installed
                   Depends: xfce4-panel but it is not going to be installed
                   Depends: xfce4-session but it is not going to be installed
                   Depends: xfce4-terminal but it is not going to be installed
                   Depends: xfce4-utils but it is not going to be installed
                   Depends: xfdesktop4 but it is not going to be installed
                   Depends: xfwm4 but it is not going to be installed
                   Depends: xfwm4-themes but it is not going to be installed
                   Depends: xubuntu-artwork-usplash but it is not going to be installed
                   Depends: xubuntu-default-settings but it is not going to be installed
                   Recommends: abiword but it is not going to be installed
                   Recommends: abiword-plugins but it is not going to be installed
                   Recommends: brasero but it is not going to be installed
                   Recommends: gnumeric-gtk but it is not going to be installed or
                               gnumeric but it is not going to be installed
                   Recommends: gqview but it is not going to be installed
                   Recommends: libgoffice-gtk-0-4 but it is not going to be installed
                   Recommends: mousepad but it is not going to be installed
                   Recommends: mozilla-thunderbird but it is not going to be installed
                   Recommends: orage but it is not going to be installed
                   Recommends: python-exo but it is not going to be installed
                   Recommends: thunar-archive-plugin but it is not going to be installed
                   Recommends: thunar-media-tags-plugin but it is not going to be installed
                   Recommends: totem-xine but it is not going to be installed
                   Recommends: xfce4-appfinder but it is not going to be installed
                   Recommends: xfce4-battery-plugin but it is not going to be installed
                   Recommends: xfce4-clipman-plugin but it is not going to be installed
                   Recommends: xfce4-cpugraph-plugin but it is not going to be installed
                   Recommends: xfce4-dict-plugin but it is not going to be installed
                   Recommends: xfce4-fsguard-plugin but it is not going to be installed
                   Recommends: xfce4-mailwatch-plugin but it is not going to be installed
                   Recommends: xfce4-mount-plugin but it is not going to be installed
                   Recommends: xfce4-netload-plugin but it is not going to be installed
                   Recommends: xfce4-notes-plugin but it is not going to be installed
                   Recommends: xfce4-places-plugin but it is not going to be installed
                   Recommends: xfce4-quicklauncher-plugin but it is not going to be installed
                   Recommends: xfce4-screenshooter-plugin but it is not going to be installed
                   Recommends: xfce4-smartbookmark-plugin but it is not going to be installed
                   Recommends: xfce4-systemload-plugin but it is not going to be installed
                   Recommends: xfce4-verve-plugin but it is not going to be installed
                   Recommends: xfce4-weather-plugin but it is not going to be installed
                   Recommends: xfce4-xkb-plugin but it is not going to be installed
                   Recommends: xfprint4 but it is not going to be installed
                   Recommends: xubuntu-docs but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then, I try to install gdm and get:
mistaceo@zookbox:/$ sudo apt-get -f install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  feisty-wallpapers libstlport5.1 libgpod1 linux-headers-2.6.20-16-generic libslab0 linux-headers-2.6.20-16 feisty-session-splashes libgs-esp8 libgdiplus
Use 'apt-get autoremove' to remove them.
Suggested packages:
  hibernate
Recommended packages:
  gdm-themes xserver-xephyr xnest
The following packages will be REMOVED:
  gnome-applets-data
The following NEW packages will be installed:
  gdm
0 upgraded, 1 newly installed, 1 to remove and 16 not upgraded.
85 not fully installed or removed.
Need to get 0B/1867kB of archives.
After unpacking 24.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 206692 files and directories currently installed.)
Removing gnome-applets-data ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxslt.so.1: undefined symbol: xmlIsExtenderGroup
dpkg: error processing gnome-applets-data (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-applets-data
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas/ thoughts on what I should try next?

Offtopic question: how can I put my otuput in a nice little box so people can read it easier?

---

### Post by Sidewinder1 on 2008-01-10
Threw caution to the wind and cliked install update. Everything OK. Ubuntu 7.10, 32 bit, Gnome. Don't know weather this had any bearing, but made sure no other programs were running (other than normal processes and services).

---

### Post by peabody on 2008-01-10
I'm not having any problems with my desktop, but I since I've run the update, my desktop settings were completely reset to the default.  My wallpaper, theme, toolbars, applets, all reset to defaults.

I assumed it might have been something I did until I checked this thread.  Sounds like the latest update did something screwy.  C'mon ubuntu devs!  First do no harm!  This ain't quite the infamous X breakage, but still...it's rather annoying.  My guess is the latest update did something with the gconf settings.  This something is what is causing the problem.

---

### Post by humbabba on 2008-01-10
I am glad you had luck, yeah I am x86_64 here so maybe it is just us? I don't know but the process is infuriating. I'm still using SuSe until I can figure out what happened and I don't like it much. Though the high resolution console is nice.

---

### Post by peabody on 2008-01-10
Okay, I'm really pissed...my tomboy notes were completely nuked as well...

I have a backup, but there's gonna be hell to pay for this!

[Edit]

I just checked my dpkg log and it was one of the following packages that did the dirty work:

openssh-server
openssh-client
deskbar-applet
libsnmp-base
ssh-askpass-gnome

I've got money on deskbar-applet.  My guess is its config script tried to zap something in the home folder and did a lot more damage than it was supposed to.

---

### Post by umuro on 2008-01-11
Yes, 32 bit update is broken. Now I am not able to install anything because of that.

---

### Post by umuro on 2008-01-11
Try this. If you do an 

```
sudo apt-get install
```

you get the list of problem packages. Apply the process below for each. I will call the package in question the_package!

```
cd /var/cache/apt/archieves
ls

```
If your *.deb file is not there redownload it
```

sudo aptitude download the_package

```
The FORCE an installation
```
sudo dpkg -i --force-all the_package*.deb

```
-------------------

For any package, you can use "dpkg -i --force-all" when ever you meet an "dpkg error processing .... (Broken pipe)". The package will install. And the complaints will be silenced. And you will be ok if the new package is working!

---

### Post by fadumpt on 2008-01-11
I'm on 32bit and when I turned the system on the next day after some updates I had the same thing with the black screen and Gnome not fully loading but after fighting with it a little (can't remember how) I managed to at least get it to (I think I just kept trying a few times, went into "failsafe gnome" once) load Gnome and I'm using it now but I have NO NAUTILUS whatsoever.  That last fix looked kinda promising so I'm gonna try that.

---

### Post by fadumpt on 2008-01-11
alright...not sure what happened but here is what I've got:

tried the apt-get install....it had some stuff it said it didn't need and it told me to run apt-get autoremove, so I did that, about that time someone on #ubuntuforums said to backup and delete the .nautilus folder contents....so I went to do that and ran another apt-get install and the screen blanked out to black with a blinking cursor.

I managed to get it back to the F7 GDM screen but then decided to go to an F2 terminal to load IRC in case it happened again, it went back to a black screen with cursor and I couldn't get out of it.

Restarted the computer and when it came back up, everything worked...

not sure what worked, but maybe it just needed a restart(???)

---

### Post by scottbporter on 2008-02-16
I have no idea how to fix. I have had problems as well, after headers upgrade. First, I put my computer in hibernation mode. When I re-booted, the partion could not be recognized by the computer. I ran gparted boot disk, it was not recognized as ANY type of partition. I ran grub restorer, no help. I re-installed. Next time I updated headers I lost the resolution settings. I run an ATI Radeon Xpress 200. No way have I found to resolve the issue, always boots in low resolution mode and I need 1440x900. I will need to re-install again! I guess I will just turn automatic upgrades off. Actually Feisty was better. I can't get 3d graphics to work with gutsy when it did with feisty. I may go back to it or swith distros until ubuntu gets worked out.

---

