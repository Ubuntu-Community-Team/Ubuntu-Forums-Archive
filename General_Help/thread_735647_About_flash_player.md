---
title: "About flash player"
date: 2008-03-25
forum: General Help
---

### Post by satimis on 2008-03-25
Hi folks,


Ubuntu 7.04 server amd64
Mozilla Firefox 2.0.0.12


I need to install Adobe Flash Player which can be download on Adobe Website.  I don't think this proprietary package will be available on repo.


$ apt-cache search 'adobe flash player'
No printout


$ apt-cache search 'flash player'```

libflash-swfplayer - GPL Flash (SWF) Library - stand-alone player
liborange-dev - development libraries for liborange
liborange0 - library to extracts CAB files from self-extracting installers
orange - extracts CAB files from self-extracting installers

```


$ apt-cache search player | grep flash```

libflash-swfplayer - GPL Flash (SWF) Library - stand-alone player
mathwar - A flash card game designed to teach maths

```


$ sudo apt-get install flashplugin-nonfree```

Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

```


$ apt-cache search gnash```

gnash - free Flash movie player
gnash-tools - free Flash movie player - Command-line Tools
klash - free Flash movie player
konqueror-plugin-gnash - free Flash movie player - Plugin for Konqueror
libgnash0 - free Flash movie player - shared libraries
mozilla-plugin-gnash - free Flash movie player - Plugin for Mozilla and derivatives

```
I read positive and negative opinion on Gnash.  Not easy for me to decide.


However the tarball available on Adobe website is "install_flash_player_9_linus.tar.gz".  I'm running 64 bit Firefox.  Is there a solution avoiding installing an additional 32bit Firefox?  TIA



B.R.
satimis

---

### Post by Existentialist on 2008-03-26
I didn't even bother with installing the version from adobe's site.  First time I visited a site needing flash, I click install plugins in firefox, and it allows you to select gnash or adobe flash.  Picked adobe, let it install, and it has worked fine ever since in both ubuntu 7.10 (firefox 2) and 8.04 beta (firefox 3), both 64 bit.

---

### Post by forrestcupp on 2008-03-26
open up Synaptic.  Go to Settings->Repositories.  In the 'Ubuntu Software' tab, make sure all of the boxes are checked except the CD one.  The click on the 'Updates' tab and check the boxes next to 'Pre-released updates' and 'Unsupported updates'.  Close that window and click the Reload button in Synaptic.  Then do a search for **flashplugin-nonfree**.  It should show up, and it should be a version that works well with any Firefox or Opera.  Install it, and you're good to go.

---

### Post by satimis on 2008-03-27
> **forrestcupp said:**
> open up Synaptic.  Go to Settings->Repositories.  In the 'Ubuntu Software' tab, make sure all of the boxes are checked except the CD one.  The click on the 'Updates' tab and check the boxes next to 'Pre-released updates' and 'Unsupported updates'.  Close that window and click the Reload button in Synaptic.  Then do a search for **flashplugin-nonfree**.  It should show up, and it should be a version that works well with any Firefox or Opera.  Install it, and you're good to go.
Thanks for your advice.


I don't run Synaptic on this box.  It is a server.  I only start X when in need, mainly browsing Internet for tech doc/article.


I already uncomment most unsupported repo;```

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

```


except following 2 repo```

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

However I can't find flashplugin-nonfree.  I won't add pre-release repo on server.


satimis

---

