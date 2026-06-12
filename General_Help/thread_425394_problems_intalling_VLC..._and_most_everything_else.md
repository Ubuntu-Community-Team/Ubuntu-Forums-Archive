---
title: "problems intalling VLC... and most everything else"
date: 2007-04-27
forum: General Help
---

### Post by charles hp on 2007-04-27
So I decided to try out linux- burned Feisty to a CD, installed, and wanted to get all my **** working. First I had to spend a few hours modifying my xorg.conf file to enable xinerama to get my dual monitors working (it works now, but dragging windows seems a lot more sluggish/sketchy than it does in windows. Maybe I should try to get the ATI proprietary drivers working?)

Anyway, I then set out on enabling the playing of media formats. I go into Add/Remove Applications and try to select VLC Media Player. I get the error message:

"This app. conflicts with other installed software. To install 'vlc' the conflicting software must be removed first. Switch to the 'synaptic' package manager to resolve this conflict."

So I instead try to install "GStreamer" packages. I manage to get "GStreamer ffmpeg video plugin" to install, but none of the other ones. When I try to install other ones they give me the same error message as VLC did. Do I necessarily need them, it seems like the GStreamer package I DLed has pretty much every codec.

So then I go into synaptic and it gives me more error messages when I try to install those programs. For example, when I try to install VLC, it says:

"The following packages have unresolvable dependencies. Make sure that all the required repositories are added and enabled in the preferences.

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libdsl-image1.2(>=1.2.5) but it is not installable"

I also get this error when I try to install automatix2:

"Error: Dependency is not satisfiable: python2.4"


Ugh it seems like my Ubuntu is ****** up. And I just installed it and pretty much the only thing I've done is get my dual monitors working with Xinerama.

---

### Post by strabes on 2007-04-27
What kind of video card do you have? You should install the newest video card drivers. Go here: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
If your card doesn't meet those specifications, go here to install the open source driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

All proprietary codecs can be installed with one command/package: ```
sudo aptitude install ubuntu-restricted-extras
```

Your dependency problems might be caused by conflicting sources. Paste the output of this command: ```
cat /etc/apt/sources.list
```
You might also consider getting a fresh sources.list from here: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Just replace your entire /etc/apt/sources.list with the feisty one on there.

Hope this helps.

---

### Post by charles hp on 2007-04-27
> What kind of video card do you have?

ATI Radeon X800XL PCI-E

Your dependency problems might be caused by conflicting sources. Paste the output of this command:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main


I then went and followed those instructions you lined to to enable extra repositories

I'm nervous about messing with my video drivers right now since it took me a while to get dual monitors working as it is (with xinerama, which I'm under the impression WILL NOT work with binary drivers, although I guess it doesnt matter since the binary drivers are supposed to support dual monitors anyway. What should I do to back up the xorg.conf (and anything else that effects video)? I already have the default xorg.conf file backed up so if I type:

> sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

what do I do to backup my CURRENT xorg.conf file to a DIFFERENT spot, so I can restore it at the command line with a different command?

---

### Post by charles hp on 2007-04-27
Also the directions on how to install the binary ATI drivers ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) aren't updated for 7.04. Considering pretty much everything I've seen has different directions for Edgy and Feisty, I'm a little nervous to use the Edgy instructions.

---

### Post by charles hp on 2007-04-27
Hmm I might have spoken too soon about that sources update. After it was done, it output:

> gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                        
  Sub-process gzip returned an error code (1)
Fetched 6594kB in 31m9s (3527B/s)                                               
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
charles@gateway:~$ 


not good, I'm guessing? Did it work at all? This has been really frustrating.

---

### Post by zvacet on 2007-04-27
system>administration>software properties and chek all boxes.Reload.

[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

```
sudo aptitude update
```

---

### Post by charles hp on 2007-04-28
> **zvacet said:**
> system>administration>software properties and chek all boxes.Reload.

[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

```
sudo aptitude update
```

I dont understand what I do with those "gpg" lines- into the terminal?

---

