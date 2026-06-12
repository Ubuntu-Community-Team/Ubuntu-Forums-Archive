---
title: "Synaptic not installing latest Compiz update"
date: 2007-08-19
forum: General Help
---

### Post by waveslider on 2007-08-19
I have two Dell computers - a Dimension desktop pc that's been running Feisty Fawn since it was released, and a Inspiron 6400 laptop that I just installed Feisty Fawn on.

I'm having a weird problem with the laptop. I just installed Compiz on it last night, following the directions on this page of the Ubuntu community documentation:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

My desktop PC installed the latest Compiz updates (from 8/18/07) with no problem, but the laptop only installed one. 

When I click "Install Updates" on the laptop, it says the Compiz was installed successfully, but it continues to say the other update is ready to be installed and shows the orange update icon in the notification area.

Any ideas how to fix this?

p.s. Also, hat community documentation page did not include instructions for installing the gpg key for that repository. The update manager says the update cannot be authenticated. Could that be the problem? How do I install the gpg key?

Thanks!

---

### Post by Megaqwerty on 2007-08-19
You may want to try running ```
sudo aptitude dist-upgrade
``` to get anything pending installed. 

And by the way, just a matter of opinion, but I generally recommend Treviño's repository:
```
# Treviño's Ubuntu feisty EyeCandy Repository
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
GPG Key: ```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
``` 
To Install compiz:
```

sudo apt-get update
sudo apt-get install compiz # compiz-gnome AND/OR compiz-kde
```
To install CompizConfig configurator (and needed libs):
```
sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* 
```
To Install the Compiz Fusion Plugins
```
sudo apt-get install compiz-fusion-*
```

---

