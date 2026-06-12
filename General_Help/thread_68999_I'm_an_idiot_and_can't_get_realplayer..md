---
title: "I'm an idiot and can't get realplayer."
date: 2005-09-25
forum: General Help
---

### Post by grimmson on 2005-09-25
Hello all. I've spent the last 3 hours reading and trying to get realplayer and am missing something. I'm going to post what I've got.

gedit sources.list
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

grimmson@ubuntu:~$ sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
grimmson@ubuntu:~$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplay
grimmson@ubuntu:~$ wtf

the gui package manager search didn't find realplay or plalplayer.

gedit attempted install (didn't see anything about rp10gold after downloading rpm from real.com

grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ ls
default           locale    realplay.applications  realplay.mime  tigris.css
hxplay_help.html  mimelnk   realplay.desktop       realplay.png
icons             realplay  realplay.keys          realplay.xml
grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ chmod a+x realplay.bin chmod: cannot access `realplay.bin': No such file or directory
grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ chmod a+x ./realplay.bin
chmod: cannot access `./realplay.bin': No such file or directory
grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ ./realplay.bin bash: ./realplay.bin: No such file or directory
grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ realplay.bin
bash: realplay.bin: command not found
grimmson@ubuntu:~/Desktop/usr/local/RealPlayer/share$ wtf

I don't get it. sorry for posting a question thats been asked a thousand times but i've read and tried to follow what i've read and I'm totally unsucessful. If you can show me the easy way to install please do. After 3 hours for one common program I'm not in the mood to play anymore tonight.

---

### Post by Goober on 2005-09-25
I forgot how I did it, I read it somewhere, but I do remember it was something like sudo apt-get install realplayer.  Try the Realplayer website, real.com or something like that, there are Linux instructions there.

But I found Realplayer useless for Linux.  MPlayer works like a charm for me, and vlc.  RealPlayer just doesn't seem to work.

---

### Post by manicka on 2005-09-25
You could just download it straight from realnetworks

go to 

[http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)

Download the rpm version to a directory.

From that directory run 

sudo alien Real*.rpm

then

sudo dpkg -i real*.deb

---

### Post by grimmson on 2005-09-25
This might be something. dpkg-gencontrol: error: current build architecture powerpc does not appear in package's list. Anything we can dew about this?
g3 400 ppc here's the list.


grimmson@ubuntu:~/download$ ls
RealPlayer10GOLD.rpm
grimmson@ubuntu:~/download$ [COLOR=DarkRed]sudo alien RealPlayer10GOLD.rpm[/COLOR]
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/realplayer
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: ldd on `debian/realplayer/usr/local/RealPlayer/codecs/a mrn.so' gave error exit status 1
dh_shlibdeps: command returned error code 256
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
[COLOR=Red]dpkg-gencontrol: error: current build architecture powerpc does not appear in pa ckage's list (i386)[/COLOR]
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.5.756: No such file or directory
grimmson@ubuntu:~/download$

---

### Post by Xian on 2005-09-25
[QUOTE=Goober]I forgot how I did it, I read it somewhere, but I do remember it was something like sudo apt-get install realplayer. [/QUOTE]
Realplayer is in the multiverse repo.
You can download the Hoary version from [THIS](http://packages.ubuntu.com/hoary/net/realplayer) page.

---

### Post by artinla on 2005-09-25
If you don't mind adding some other (worthwhile) applications, this install script will put most everything you need, including realplayer, in for you.

[http://y.mrbass.org/ubuntuaddon.zip](http://y.mrbass.org/ubuntuaddon.zip)

Detailed instructions are located at:

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

Art

---

