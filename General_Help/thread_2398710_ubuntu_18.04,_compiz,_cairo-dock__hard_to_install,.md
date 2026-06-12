---
title: "ubuntu 18.04, compiz, cairo-dock : hard to install, harder to keep in working order"
date: 2018-08-16
forum: General Help
---

### Post by ReneVeerman on 2018-08-16
it's happened twice in the past week that i change a setting in ccsm (compiz config settings manager), i get auto-logged out, and lose the ability to start any desktop environment that supports compiz.

then i try to install the latest ubuntu-18.04.1 (downloaded today), and it just won't install. first, it fails to detect in rufus that my usb key needs replacing, second, when i use a new usb key, today's copy of the ubuntu-18.04.1.iso installs me a read-only filesystem.

so i revert to an older copy of the ubuntu installation iso, and that gets me a system with write-able filesystem.

then i install the following :

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo add-apt-repository ppa:cairo-dock-team/ppa 
sudo apt-get update
sudo apt-install nvidia-driver-396 exfat-fuse 
sudo apt-get dist-upgrade
sudo apt-get install cairo-dock cairo-dock-plug-ins compiz compizconfig-settings-manager compiz-plugins apache2 curl php libapache2-mod-php 
curl -L [https://couchdb.apache.org/repo/bintray-pubkey.asc](https://couchdb.apache.org/repo/bintray-pubkey.asc) | sudo apt-key add -
echo "deb [https://apache.bintray.com/couchdb-deb](https://apache.bintray.com/couchdb-deb) bionic main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update && sudo apt-get install couchdb
 
however, this order of installation gets me a cairo-dock + gnome login option under that gears icon at the login screen (not the screen lock screen), that doesnt work, like when compiz "just breaks down".

i like ubuntu, i like cairo-dock and compiz better than any other window manager and taskbar / startmenu combination, 
but stability could really be improved.

i'm currently trying a format of my 1TB SSD (takes another hour at least), then i'll try to install everything except cairo-dock first, do a reboot, then install cairo-dock, and then see if i can log in so i can use compiz and cairo-dock.

i'll update this thread when i know more.

i also know this issue requires filing bugreports to the compiz and cairo-dock guys, and i'll send them a link to this thread, but how do i get this message to the ubuntu developers? i think someone once told me they don't read this forum.

---

### Post by mc4man on 2018-08-16
That ppa for cairo-dock is useless for 18.04, last builds were 3 years ago for 15.10..
Seems ok in a test here though I'd likely switch to lightdm

---

### Post by ReneVeerman on 2018-08-16
done :
* complete harddrive format (took over 2 hours)
* re-install of ubuntu 18.04.1 downloaded 2 weeks ago via iso image and rufus.
* install nvidia drivers, reboot, install compiz, reboot, install unity, reboot, install cairo-dock, reboot : works, can log into the cairo-dock (gnome) desktop environment. no other install sequence seems to work.
* run ccsm to tweak compiz with the 2 things i need from it : zoom without focus tracking, and the opacity brightness plugin..
---> **compiz logs me out from the desktop after each change in ccsm**. i set the zoom without focus tracking first, can still log in to cairo-dock desktop environment. 
----> **i enable the opacity brightness plugin, and that breaks the entire cairo-dock (gnome) desktop environment, entirely.**
-- resetting compiz from the unity desktop environment doesnt help

i'm now going to try a lubuntu install with the same post-installation sequence to get to cairo-dock + compiz, but i hate the fact i've already had to waste 2 days on this this week alone.

---

### Post by ReneVeerman on 2018-08-16
can't even get compiz to run on lubuntu, despite claims of how putting compiz --replace in the autostart of lubuntu would do the trick.


i'll try one more time with ubuntu 18.04 and compiz told to use gnome compatibility, but if that doesnt work i'm calling it quits and filing this to ubuntu devs, compiz devs and cairo-dock devs.

---

### Post by NM5TF on 2018-08-16
I know of several people, myself included, that have cairo-dock & compiz running successfully in Arch Linux....have you considered that distro ???

Arch can be a little daunting for a newbie, but you don't seem to be in that category....

[https://wiki.archlinux.org/index.php/Installation_guide]("https://wiki.archlinux.org/index.php/Installation_guide")

tommy

---

### Post by ReneVeerman on 2018-08-16
i can't even install ubuntu.com 18.04.1 at all anymore..

i've tried 3 different USB keydrives, i've tried using rufus and pendrive linux to make the installer usb keydrive,

what i'm getting at the moment is a 'sorry, the installer has crashed' message, the internal bugreporting that is mentioned crashes too (although it appeared to send out something during some of the N times i re-installed today), and i'm left with the following message on a black text only screen :

[0.00000] [Firmware Bug] : TSC_DEADLINE disabled due to Errata : please update microcode to version : 0x02 (or later)

---

### Post by ReneVeerman on 2018-08-17
i had a look at Arch linux, but found it too much manual install labor.

but i have a working system again.. :)

here's what it took :
* creating a new ubuntu 18.04.1 installer usb key from ubuntu.com iso (probably doesnt matter if you use rufus or pendrivelinux, i used pendrive linux) with about 280MB of persistent data storage space (dont need more and wrting to USB is sloooow).
* booting up with the usb key (done in bios menu by the way, that very first menu you get as a PC starts up) into the live environment (top menu item in the menu just after the bios menu)
* starting 'disks', and formatting all partitions on the SSD or harddrive that i want to install ubuntu on, *completely* (option erase disk, and yes, it does take 3 hours for a 1TB SSD. So if you have a smaller extra SSD lying around, that might be a better option to install the OS on). without this step, the ubuntu installer crashes. each and every time.
* installing ubuntu onto the formatted disk (without rebooting, the icon for it should be at the top-left side of your usb live desktop), with all options in the installer menu most likely irrelevant except for using the 'erase disk' option, which, just to be sure, re-creates the partitions.
* installing the video driver, compiz, ubuntu-unity-desktop (and selecting lightdm as your window manager!)
* reboot
* install cairo-dock
* use ccsm (compiz config settings manager) to enable the 'enhanced zoom desktop' and the 'opacity, brightness and saturation' plugins, setting the settings for 'enhanced desktop zoom' with special note to that plugin's 'focus tracking' tab page, where it's best to uncheck the top option ('enable focus tracking')
* run cairo-dock as an app, because if you'd boot into the cairo-dock option at the ubuntu login screen (click on the ubuntu logo of the login input window in lightdm, which should be the default startup login window now), and change the ccsm settings for cairo-dock then, that entire desktop environment crashes to the ubuntu login screen and refuses to start up again, the moment you turn off 'focus tracking' in ccsm (with the 2 mentioned ccsm plugins enabled). solution : just don't change the ubuntu login screen's ubuntu-icon menu-option at all. you'll be booting into unity lightdm and running cairo-dock as an app. you can turn on autohide at least for the default ubuntu taskbar if you like, which gives you that windows-key start-menu along with cairo-dock.

the only thing still wrong with my setup is the fact that my wallpaper changer app, variety, doesn't work with lightdm apparently. 
but maybe i can find another wallpaper changer app that does work.

lastly, i'd like to mention that the SSD i was installing on, nor the USB keys, were ever faulty hardware.
i nearly bought new disks and USB keys, if it wasn't for the fact i didn't tust 3 different USB keys that hardly get used suddenly failing one after another, nor an SSD that i've been working on for under 2 years which has never had a write failure or bad health report in an ubuntu app like 'disks'.
i was also nearly desperate enough to buy windows again, but let's just say i like ubuntu better than windows, for a bunch of reasons.

i'll forward this thread to the relevant development teams, over the next few days, if i can find their contact details.

---

### Post by ReneVeerman on 2018-08-17
i've informed the cairo-dock development team about this at [https://bugs.launchpad.net/cairo-dock-core/+bug/1787555](https://bugs.launchpad.net/cairo-dock-core/+bug/1787555)

---

### Post by ReneVeerman on 2018-08-17
and the compiz development team at [https://bugs.launchpad.net/compiz/+bug/1787556](https://bugs.launchpad.net/compiz/+bug/1787556)

---

### Post by ReneVeerman on 2018-08-17
hitting alt-F2 and entered 'ubuntu-bug compiz' to report to ubuntu.com, at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1787557](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1787557) (this one contains all the relevant OS logs)

---

### Post by ReneVeerman on 2018-08-17
> **mc4man said:**
> That ppa for cairo-dock is useless for 18.04, last builds were 3 years ago for 15.10..
Seems ok in a test here though I'd likely switch to lightdm

they claim to be actively developing..

do you know a way to get a more recent version?

---

### Post by ReneVeerman on 2018-08-24
i have 2 screens, and wanted to turn off lightdm's feature to halt the mouse cursor at the screen edge.

at first glance, advice found on google said to tweak this in ccsm.

however, it seems touching just about anything in ccsm cripples the user interface completely (and logs you out automatically).

after another re-install like described before (but to a 120GB SSD instead of my 1TB SSD), including full drive format, took only about an hour and a half.

and i highly recommend tweaking the unity desktop ccsm settings before installing anything else or doing any work.

here's my updated post-ubuntu.com-installation script.. 
the 2nd version is the one without the tools specific to my work-environment..

please note that you should opt for 'lightdm' during the installation of ubuntu-unity-desktop.

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo add-apt-repository ppa:cairo-dock-team/ppa 
sudo apt-get update
sudo apt-get install nvidia-driver-396 exfat-fuse 
sudo apt-get dist-upgrade
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins ubuntu-unity-desktop apache2 curl php libapache2-mod-php 
sudo apt-get install cairo-dock cairo-dock-plug-ins 
sudo apt-get install kate git variety vlc imagemagick youtube-dl npm
curl -L [https://couchdb.apache.org/repo/bintray-pubkey.asc](https://couchdb.apache.org/repo/bintray-pubkey.asc) | sudo apt-key add -
echo "deb [https://apache.bintray.com/couchdb-deb](https://apache.bintray.com/couchdb-deb) bionic main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update 
sudo apt-get install couchdb
sudo npm install -g add-cors-to-couchdb
sudo add-cors-to-couchdb -u admin -p undisclosed


version without my development tools :


sudo add-apt-repository ppa:graphics-drivers/ppa
sudo add-apt-repository ppa:cairo-dock-team/ppa 
sudo apt-get update
sudo apt-get install nvidia-driver-396 exfat-fuse 
sudo apt-get dist-upgrade
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins ubuntu-unity-desktop 
sudo apt-get install cairo-dock cairo-dock-plug-ins 
sudo apt-get install variety vlc 


nvidia-driver-396 should be replaced with the driver specific to your video card, google 'ubuntu [ubuntu-major-version-number] [video card model number]' to see if you even need one.

exfat-fuse is to mount drives shared between windows and linux machines.

---

### Post by ReneVeerman on 2018-08-24
reported to variety's developers at [https://github.com/varietywalls/variety/issues/70](https://github.com/varietywalls/variety/issues/70)

---

### Post by ReneVeerman on 2018-08-24
[https://github.com/varietywalls/variety/issues/70#issuecomment-415841856](https://github.com/varietywalls/variety/issues/70#issuecomment-415841856)

[COLOR=#24292E][FONT=-apple-system]>You shouldn't need to be using the Cairo dock PPA on your system - it's out of date (in terms of Ubuntu release support), and a recent version of it is already in the main Ubuntu repo. Just to be safe, try installing [/FONT][/COLOR]ppa-purge[COLOR=#24292E][FONT=-apple-system] and running [/FONT][/COLOR]ppa-purge ppa:cairo-dock-team/ppa[COLOR=#24292E][FONT=-apple-system] to get rid of the cruft adding that PPA may have created.

[/FONT][/COLOR]https://github.com/varietywalls/variety/issues/70#issuecomment-415894304

[COLOR=#24292E][FONT=-apple-system]i did a dist-upgrade today,
and now variety works under lightdm :)[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]many thanks to whomever fixed it :)[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]i'll have a look at removing the cairo-dock PPA.. bit strange they have that as installation instructions on their website.. but ok.
first i gotta get some work done though, i feel uninstalling and re-installing things like cairo-dock and compiz result in broken systems. which is no big deal now that i have my smaller SSD as OS installation.[/FONT][/COLOR]

---

