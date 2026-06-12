---
title: "[SOLVED] OpenGL driver ?"
date: 2008-07-07
forum: General Help
---

### Post by WitchCraft on 2008-07-07
Question: I installed a Debian minimal system on one of my external USB hard drives.

[http://cdimage.debian.org/debian-cd/4.0_r3...386-netinst.iso]("http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-netinst.iso")

added sources

vi /etc/apt/sources.list

make it look like this
> # Find more repositories here:  [http://www.apt-get.org]("http://www.apt-get.org")
# Specific recommendations:     [http://www.visoracle.com/download/debian/sourceslist.html]("http://www.visoracle.com/download/debian/sourceslist.html")


# CD images - etch installer    [http://www.debian.org/devel/debian-installer/]("http://www.debian.org/devel/debian-installer/")
#deb cdrom:[Debian GNU/Linux 4.0 r3 _Etch_ - Official i386 NETINST Binary-1 20080218-14:15]/ etch contrib main


# repository for etch
deb [http://ftp.debian.org/debian/]("http://ftp.debian.org/debian/") etch main
deb-src [http://ftp.debian.org/debian/]("http://ftp.debian.org/debian/") etch main

# regular updates for etch
deb [http://ftp.debian.org/debian/]("http://ftp.debian.org/debian/") etch main contrib non-free
deb-src [http://ftp.debian.org/debian/]("http://ftp.debian.org/debian/") etch main contrib non-free

# security updates for etch
deb [http://security.debian.org/]("http://security.debian.org/") etch/updates main contrib non-free
deb-src [http://security.debian.org/]("http://security.debian.org/") etch/updates main contrib non-free

# multimedia	   Christian Marillat (was: ftp.nerim.net)
deb [http://www.debian-multimedia.org]("http://www.debian-multimedia.org") etch main
deb-src [http://www.debian-multimedia.org]("http://www.debian-multimedia.org") etch main

# unofficial      [http://www.debian-unofficial.org]("http://www.debian-unofficial.org")
deb [http://ftp.debian-unofficial.org/debian]("http://ftp.debian-unofficial.org/debian") etch main contrib non-free restricted
deb-src [http://ftp.debian-unofficial.org/debian]("http://ftp.debian-unofficial.org/debian") etch main contrib non-free restricted

Then i installed some software
```
apt-get update
apt-get upgrade
apt-get install apt-file
apt-file update
apt-get install gcc
apt-get install g++
apt-get install lzma
apt-get install manpages-dev
apt-get upgrade
```

Then I did compile the latest kernel.
[http://www.nixcoders.org/forum/index.php?showtopic=99]("http://www.nixcoders.org/forum/index.php?showtopic=99")
Worked like a charm, I did this before in Ubuntu, there it worked, too.

Then I installed a minimal version of a useful GUI:
```
apt-get install xfonts-base
apt-get install xserver-xorg
apt-get install gnome-desktop-environment
```

Then had to adjust the gnome keyboard layout. The keyboard worked correctly afterwards.

Then I installed a few multimedia things:
apt-get install w32codecs libdvdcss2
apt-get install synaptic
apt-get install wine
apt-get install firefox
apt-get install gnome-audio
apt-get totem
apt-get vlc
apt-get upgrade


I could watch videos, but had no sound.
So I just compiled the latest alsa drivers, installed them and restarted.
Bang, sound worked, video worked, nice.

Then I installed a game that I develop software for, it uses OpenGL, end there I got to a problem:

The game needs OpenGL, I know that, even on Windows I had to install the drivers.

I tried with software emulation of OpenGL, but it just is far too slow...

Now, I don't know whether it is correct, but I found that I had to compile the intel 915GM graphics driver in order to get OpenGL to work.

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
says:
2. Mesa 3D GL driver

so I downloaded 
git-clone git://anongit.freedesktop.org/git/mesa/mesa

The problem is I couldn't install it, it demanded a library version > 3.0.1 or something, but debian stable only has 2.5...

So I downloaded it from the experimental repositories, tried to get it to work, but got stuck when I should have had to install glibc > current version, meaning I would have to uninstall everything I installed, and install the entire experimental version...

Also, my attempts to install the newer library versions somehow screwed up apt... you couldn't remove the newly installed experimental libraries, and when you wanted to remove them with -f, apt-get also wanted to remove the rest of the system...

So I got fed up, and installed Ubuntu again.
Simply because OpenGL works on Ubuntu, don't know why...

I have also compiled the latest kernel on Ubuntu, had to reinstall the alsa driver of course, but OpenGL always worked...

Now the question:
Is there no other way to get Open GL to work with my graphics card than to compile the driver?
Why does it work on Ubuntu, how is that done?

Or would I simply have needed some additional library/module (that I know nothing about) installed for OpenGL?
It's also annoying because a lot of good graphical tools, eg. google-earth use OpenGL, and if it doesn't work, then it's just ************

---

### Post by WitchCraft on 2008-07-08
bump.

---

### Post by WitchCraft on 2008-07-09
bump.

---

### Post by WitchCraft on 2008-08-20
Solved, it doesn't work in Debian Etch, you need Debian Lenny, because you need newer versions of the dependencies, which do conflict with the base install of Etch (meaning you would have to uninstall almost the entire OS...).

---

