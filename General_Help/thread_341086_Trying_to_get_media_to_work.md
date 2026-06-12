---
title: "Trying to get media to work"
date: 2007-01-18
forum: General Help
---

### Post by mrwooster on 2007-01-18
Hi,

Am am using this link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) to try to get media and dvds to work, however I get the following error when trying to install the packages:

E: Couldn't find package gstreamer0.10-pitfdll

I have added all the repositories (i think) but can't seem to get round this error?

Any help would be great. Thanks

Guy

---

### Post by Jussi Kukkonen on 2007-01-18
That's in universe or multiverse repo (depends on your Ubuntu version)...

* Paste the contents of /etc/apt/sources.list
* paste the output of the install commands:```

sudo aptitude update
sudo aptitude install gstreamer0.10-pitfdll
```

---

### Post by mrwooster on 2007-01-18
Sources.list


#skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
# deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Output of command:

apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.10-pitfdll

---

### Post by Jussi Kukkonen on 2007-01-18
what about the output from the update command? -- it's the easiest way to see if the sources are correct.

EDIT you are missing multiverse repo, that's the problem.

Something like this:
```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper multiverse
```

Alternatively, you could combine the lines from the same address to make it more readable:
```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```
...only do that if you understand what you are doing.

---

