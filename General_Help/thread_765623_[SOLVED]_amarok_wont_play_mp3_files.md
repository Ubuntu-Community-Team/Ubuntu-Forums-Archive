---
title: "[SOLVED] amarok wont play mp3 files"
date: 2008-04-24
forum: General Help
---

### Post by elidoperezmd on 2008-04-24
after upgrade to heron, amarok wont play mp3 files, a window came up saying that i had to download something to play mp3 files, and i hit the dont remind me later button so i cant see it again. during the installion of whatecer i needed the computer restared itself for unknown reasons to me? any idea of what i need to install?

---

### Post by rouge568 on 2008-04-24
You will need to install some propietary codecs. Paste the following into a terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras

```
(Note, this will install dvd playback capabilities as well)

Have fun!

---

### Post by JimmyHopkins on 2008-04-24
If you want an easier way, go to applications->add/remove, set "show" to all available applications, and type in "mp3" or "ubuntu restricted extras" and install them for mp3 codecs.

---

### Post by elidoperezmd on 2008-04-24
thanks for the help, after trying both ways this is where i am at right now:

the first replies works fine untill i enter the third command, after that the terminal says 

elido@elidoperezmd:~$ sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
w32codecs is already the newest version.
E: Couldn't find package ubuntu-restricted-extras


what does this mean?




the second reply tells me to do it in a different way, but when installing updates it stops at 9%, here is the error report:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.



what should i do?  thanks for your time

---

### Post by JimmyHopkins on 2008-04-24
EDIT: Ignore this post, see my next post.


Try downloading and installing non-free codecs 1.1 i386.deb from this site ([http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/](http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/)) (assuming your processor's architecture is i386)

OR

Try adding medibuntu to your repositories. Visit here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
or go into terminal and type in:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list


then type in:

sudo apt-get update && sudo apt-get install medibuntu-keyring

then go in synaptic package manager (system->admin->synaptic)

Search for mp3 or codec or non-free codec until you find your codecs, and install it.



EDIT: Maybe [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) will help?

---

### Post by JimmyHopkins on 2008-04-24
Sorry for the double post, but ignore my last post. This should work.
If your processor's architecture is i386, and you are using ubuntu 8.04, download "ubuntu-restricted-extras_2.2_i386.deb" and run it from this site ([http://security.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/](http://security.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/))

If you have kubuntu (ubuntu with KDE), and you run on an old mac, you should download kubuntu restricted extras ppc.deb". But most likely "ubuntu-restricted-extras_2.2_i386.deb" is what you need. After it installs, go into the terminal, run:

sudo apt-get update

then run

sudo apt-get upgrade

and your codecs will be ready and updated.

---

### Post by rouge568 on 2008-04-24
In addition, you want to make sure you have all your repositories enabled. Go into synaptic package manager and go to Settings>Repositories. Make sure that the main, restricted, universe, and multiverse repositories are checked off.

---

### Post by NightwishFan on 2008-04-24
If nothing else works install the package: libxine1-ffmpeg

---

### Post by cprofitt on 2008-04-24
I think with the release of 8.04 there are some very busy servers -- people might want to let the rush die down and retry installing things.

---

### Post by elidoperezmd on 2008-04-24
nothing seems to work so far,

---

### Post by elidoperezmd on 2008-04-24
> **NightwishFan said:**
> If nothing else works install the package: libxine1-ffmpeg





This is what amarok says that i need to install, how do i install it?

---

### Post by NightwishFan on 2008-04-24
It should, are you using the xine engine? Gstreamer always is buggy.

---

### Post by NightwishFan on 2008-04-25
```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by elidoperezmd on 2008-04-26
i have taken every stpe mentioned in this post, every one in order, nothing works, unistalling and reeinstalling will get rid of the problem?

---

### Post by NightwishFan on 2008-04-26
I am not sure, but any one of them generally should have worked. If you want to reinstall amarok its:
```
sudo apt-get purge amarok && sudo apt-get install amarok
```

---

### Post by elidoperezmd on 2008-04-26
weird, reinstalling and updating fixed it, thanks all. untill next time

---

### Post by NightwishFan on 2008-04-26
Glad it worked for you. :popcorn:

---

