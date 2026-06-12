---
title: "missing packages / flash"
date: 2015-06-23
forum: General Help
---

### Post by pavel protin on 2015-06-23
hello! 

i recently installed xubuntu 14.04 on a cubox-i4pro. i had a problem with the policy-kit, but that seemed to solve itself by itself (just in case it matters for the problem at hand: [http://ubuntuforums.org/showthread.php?t=2283283](http://ubuntuforums.org/showthread.php?t=2283283) ). now:

i can't get the system to install the flashplayer (or freshplayer, or pepper) - no matter what software sources i add, and no matter if i add them via settings>software&updates or via writing in the sources.list. there is no flashplayer in my ubuntu software center, there is none to be found in synaptic, and if i try to install flash via terminal, i get:

```
cubox@cubox:~$ sudo apt-get install flashplugin-installer
[sudo] password for cubox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'flashplugin-installer' has no installation candidate
cubox@cubox:~$ 
```

my sources.list currently looks like this:

```
deb http://ports.ubuntu.com/ubuntu-ports trusty main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports trusty main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports trusty-updates main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports trusty-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports trusty-proposed main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports trusty-proposed main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports trusty-security main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports trusty-security main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ trusty-backports main multiverse universe restricted
deb http://download.videolan.org/pub/debian/stable/ /
deb-src http://download.videolan.org/pub/debian/stable/ /
deb http://download.webmin.com/download/repository sarge contrib
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

in case it matters: when opening this just now, i got the message in the terminal: 
```
(gedit:2731): IBUS-WARNING **: The owner of /home/cubox/.config/ibus/bus is not root!
```

when updating the list in settings>software&updates (meaning i uncheck one of the sources [not the one in the error-message below], check it again, click "close" and let the machine "update" the list), i get this charming riddle (fyi: i'm online) :

> Failed to download repository information
Check your Internet connection. Details:
W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-armhf/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.92.152 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.


anyone out there who can make heads or tails of of all this? thanks in advance!
(because, gender nonwithstanding: [https://www.youtube.com/watch?v=8fpjuoKhfJo](https://www.youtube.com/watch?v=8fpjuoKhfJo) )

---

### Post by Ty_Scheun on 2015-06-23
Add a PPA Repo forFlash Player, run ```
sudo apt-get update
``` and then install it

---

### Post by Ty_Scheun on 2015-06-23
[COLOR=#111111][FONT=Ubuntu]I'd try running apt in a terminal, and search for flashplugin-installer (or maybe adobe-flashplugin, not sure if I'm supposed to have both or not in the default Ubuntu repos). This should find either/both if they're available:[/FONT][/COLOR]
apt-cache search adobe flash
[COLOR=#111111][FONT=Ubuntu](And don't forget the sudo apt-get update first)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then should be able to install one with one of these, depending on your results:[/FONT][/COLOR]

[LIST]
[*]sudo apt-get install flashplugin-installer
[*]sudo apt-get install adobe-flashplugin
[/LIST]
[COLOR=#111111][FONT=Ubuntu]And, if you're using the Chrome/Chromium browser, it uses it's own built-in Pepper flash player anyway.[/FONT][/COLOR]
[HR][/HR][COLOR=#111111][FONT=Ubuntu]FYI: I just saw an article on WebUpd8.org about a **Firefox** plugin available on the WebUpd8 PPA that should let you use the newer Pepper flash player. Here's a link & clip:[/FONT][/COLOR]
[INDENT][h=2][Fresh Player Plugin Sees New Release (Pepper Flash Wrapper For Firefox)]("http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html")[/h]Date: Wednesday, January 14, 2015
As you probably know, the latest Adobe Flash Player is available on Linux only via Google Chrome (it's bundled with it) while other browsers such as Firefox are stuck with an old 11.2 version.
The Adobe Flash Player plugin that's bundled with Google Chrome is in the form of a PPAPI (or Pepper Plugin API) plugin and Mozilla isn't interested in adding support for it. Because of this, Rinat Ibragimov has developed Fresh Player Plugin, a wrapper that allows Linux users to use Pepper Flash from Google Chrome in Firefox and other NPAPI-compatible browsers.
Note that according to its GitHub page, Fresh Player Plugin "mostly works, but some essential APIs are still to be implemented", so it may not work with some websites.
[/INDENT][COLOR=#111111][FONT=Ubuntu]Here are the pasted [instructions for adding the WebUpd8 PPA & the Fresh Player Plugin]("http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html"):[/FONT][/COLOR]
[INDENT]
[LIST=1]
[*]Install Fresh Player Plugin in Ubuntu (via PPA), by using the following commands:
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
You can also download the deb from [HERE]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/f/freshplayerplugin/") but installing it without adding the PPA means you won't get updates!

[*]Fresh Player Plugin is just a wrapper for libpepflashplayer.so so it needs this file which is bundled with Google Chrome. The easiest way to get this file is to simply install Google Chrome Stable - [download it from here]("https://www.google.com/intl/en/chrome/browser/"), then install it. That's it!
There are other ways of getting libpepflashplayer.so but I won't post installation instructions for all of them here. Instead, I'll just list them below:

[LIST]
[*]if you're using Google Chrome Unstable, create a symbolic link from /opt/google/chrome-unstable/PepperFlash to /opt/google/chrome/ or add a freshwrapper.conf file and add the /opt/google/chrome-unstable/PepperFlash/libpepflashplayer.so path there - see step 3;
[*]you can install Pepper Flash using 2 other ways: via the **[installer]("http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html") available in the official Ubuntu 14.04 repositories** and via the [Pepper Flash PPA]("http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html") which is also available for older Ubuntu versions - once installed, then you'll need to create a symbolic link for Pepper Flash to /opt/google/chrome/PepperFlash/libpepflashplayer.so or see step 3 for how to change the path to it.
[/LIST]
[/LIST]
[/INDENT]

---

### Post by Mike_Walsh on 2015-06-23
Have you enabled 'Canonical Partners', on the 'Other Software' tab in Software & Updates? Tick the check boxes beside both of those entries, and recharge the cache when requested.

Then run

```
sudo apt-get update
```

in the terminal. After this, search for 'flashplugin-installer' in the Software Centre, and install it. This will give you the Linux version of FlashPlayer (currently 11.2.202.466/8), which is used by FireFox.

As far as your system is concerned, **until** you enable the 'Canonical Partners' repository, it doesn't know that  'flashplugin-installer' ( or indeed, a lot of other software) even exists..! It cannot install what it doesn't know about...

If you run Chrome, FlashPlayer (pepperflash) in included in the browser, so does not require installation. If, however, you wish to run Chromium (the open-source version of Chrome, and which it is based on), then the Pepperflashplayer is NOT included by default, and needs to be installed.

In the terminal,

```
sudo apt-get install pepperflashplugin-nonfree
```

and enter your password when requested. What this does is download Chrome, extract the pepperflashplayer from it, and install it into Chromium for you.

You should also install 'ubuntu-restricted-extras'; this gives you many of the additional multimedia codecs and proprietary code which Canonical are not legally permitted to include with the release.

Hope that helps.


Regards,

Mike.


Regards,

Mike.

---

### Post by pavel protin on 2015-06-23
thanks ty and mike, but... 

(here come the results of your kind suggestions, in order of incoming)
(with two questions at the end)

(1) 

before, i only had "canonical partners". 
now i added: deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) vivid partner 
then: sudo at-get update
then: reboot
then: no flash in synaptic or the manager. i tried all the possible names in the terminal:

```
cubox@cubox:~$ sudo apt-get install flashplugin
[sudo] password for cubox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flashplugin
cubox@cubox:~$ sudo apt-get install flash-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flash-plugin
cubox@cubox:~$ sudo apt-get install flashplayer-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flashplayer-plugin
cubox@cubox:~$ sudo apt-get install flash-player-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flash-player-plugin
cubox@cubox:~$ sudo apt-get install flash-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flash-installer
cubox@cubox:~$ 

```

(2) 

apt-cache search yields:

```
cubox@cubox:~$ apt-cache search adobe flash
texlive-latex-extra - TeX Live: LaTeX additional packages
bleachbit - delete unnecessary files from the system
cclive - lightweight command line video extraction tool
konqueror-nsplugins - Netscape plugin support for Konqueror
libjs-swfobject - tool to embed Flash content into webpages
libquvi-dev - library for parsing video download links (development package)
libquvi-doc - library for parsing video download links (documentation package)
libquvi-scripts - library for parsing video download links (Lua scripts)
libquvi7 - library for parsing video download links (runtime libraries)
libvdpau-va-gl1 - VDPAU driver with OpenGL/VAAPI backend
nomnom - download videos from Youtube and other similar video websites
quvi - command line program to extract video download links
red5-doc - flash streaming server - documentation
red5-server - flash streaming server
cubox@cubox:~$ 

```

... none of which seems useful (in case i'm wrong here, please let me know!)

(3)

i already had tried the WebUpd8-PPA. it is in my list. it gets me:

```
cubox@cubox:~$  sudo apt-get install freshplayerplugin
[sudo] password for cubox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freshplayerplugin
cubox@cubox:~$ 
```

(4)

yes, i indeed have canonical partners (see above, also my sources.list) enabled. the reason i put out this cry for help in the first place was that the install you describe doesn't work for some reason: my machine has the correct PPA enabled, but it doesn't see the flashplayer (neither by software center, by synaptic or "sudo apt-get install"). and it seems to be ONLY the flash-player. (i have even installed the xubuntu-restricted-extras, and all the other stuff in there, except for flash, work fine).


NOW THEREFORE: two questions:

(a)  

the only thing that comes up as persistently as the inability of my system to see the flashplayer is that it dosn't finde the armhf-packages when "sudo apt-get update" (in terminal as well as via "software&updates"):

```
Err http://extras.ubuntu.com trusty/main armhf Packages                        
  404  Not Found [IP: 91.189.92.152 80]

```
...
```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-armhf/Packages  404  Not Found [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

question: could there be a connection? i don't see how, as the armfh-stuff has nothing to do with media - OR DOES IT? 

(b) 

in the software center, i found something called the gnash SWF viewer - could this be as close as i get?

---

### Post by deadflowr on 2015-06-23
I'd simply add a comment to the extras.ubuntu line in the sources.list.
In the software and updates it should be the Independent stuff in Other Software.

It'd also remove the vivid partner stuff, if you are not running vivid.

Then re-run the sudo apt-get update command.

Then try installing the flashplugin-installer package.

Of course, with all that, I do not know if the armfh architecture even has that package...

---

