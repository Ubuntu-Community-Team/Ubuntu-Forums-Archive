---
title: "Adding MPG4 Support To BMP"
date: 2005-04-09
forum: General Help
---

### Post by MikeD03C on 2005-04-09
I just installed Ubunto 5.04.  The amount of out-of-box hardware support is awesome.  I used to use Slackware but got tired of having to rebuild the kernel to just get the 2.6.10 and having no package handler.  Ubuntu is my first Debian distro and this whole "apt-get-install" thing is new to me--but really cool!  

I got my ntfs windows xp partition mounted in ro just fine, but most of my music is in m4a format from iTunes.  Totem movie player will play them but this doesn't work too well for managing nearly 3000 songs!  I downloaded bmp and found what I think is a plugin for bmp to play mp4 called bmp-mp4_20041215.  I extracted it and I dont' see a configure script and I can't run a make on it.  The readme asks for three things I don't understand in the first 3 steps.  Here are the steps:

INSTALL
---------
Before you need to have automake/autoconf/libtool and gcc to build this
xmms plugin. Also you need to have bmp installed (and gtk+-2.x.x)

1) ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs
2) check you CFLAGS LDFLAGS for optimizations and libraries accesbility
3) check your PKG_CONFIG_PATH if bmp is installed other than in /usr dir and export it with the good directory of bmp.pc file.
3) run configure && make
4) install the plugin as root with : "make install" or "make install-strip"

How do I compile this to get it into bmp?  Thanks for your help!  I searched extensively on multiple sites but couldn't find what I was looking for.  My apologies if this is redundant.

---

### Post by gflores on 2005-04-09
There is an mp4 plugin for xmms in main that you can install. However, that is for xmms and not for bmp, although I've heard that some plugins work with bmp (since it is a fork of xmms).

---

### Post by pietro_spina on 2005-04-11
[QUOTE=MikeD03C]How do I compile this to get it into bmp?  Thanks for your help!  I searched extensively on multiple sites but couldn't find what I was looking for.  My apologies if this is redundant.[/QUOTE]

well I've just fought with this myself... 
This is the sequence of commands i think you should use.

lets say I downloaded and un-tar/un-zipped the "bmp-mp4_20041215.tar.bz2" file to a directory called ~/beepM4A

```

pietro@ubuntu:~$ sudo apt-get install beep-media-player beep-media-player-dev
pietro@ubuntu:~$ cd ~/beepM4A/bmp-mp4_20041215

pietro@ubuntu:~/beepM4A/bmp-mp4_20041215$ ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs

pietro@ubuntu:~/beepM4A/bmp-mp4_20041215$ ./configure && make
pietro@ubuntu:~/beepM4A/bmp-mp4_20041215$ sudo make install-strip
or
pietro@ubuntu:~/beepM4A/bmp-mp4_20041215$ sudo make install
```

I'm not sure if it maters, but I read somwhere that the "libfaad2-2.0_cvs20040912" that he uses is optimized for i686... might make a difference if that is not your setup... I don't know though. maybe somone else has had success with this...

cheers,
p

---

### Post by MikeD03C on 2005-04-17
Thanks for the advice.  It's really appreciated.  I get an error though on one of the steps: I get a an error for the "ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs" step where autoreconf command is not found.  What could this be caused by? 

Thanks in advance
MikeD03C

---

### Post by pietro_spina on 2005-04-17
[QUOTE=MikeD03C]I get a an error for the "ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs" step where autoreconf command is not found.  What could this be caused by? 
[/QUOTE]

I'm at work right now so this is just from memory... but,

In the read-me file the author included, I believe he mentions you need to have the automake tool and a couple of others...

Just go and open up synaptic and do a search for the various tools that he says you will need... be sure to get the correct versions. 1.8 I believe...

I'm not sure if it's ok to have multiple versions of these tools installed though, I assume it was because the ACLOCAL and AUTOMAKE commands specify the 1.8 version...

hope this is helpfull, I'm not exactly an expert on this stuff...

p

---

### Post by DanVarga on 2005-05-07
Anyone know how to get it to read the m4a tags in BMP?  I can play the files but it doesn't read the tags.

---

### Post by pietro_spina on 2005-05-25
It seems like lots of players don't really handel tags all that well and it wouldn't supprise me if Beep didn't either. (some just have tag viewing some don't have that...)

Easy Tag seems to be a popular tag manipulation tool.

cheers,
p

---

