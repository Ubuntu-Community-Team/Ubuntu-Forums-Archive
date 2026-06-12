---
title: "Wine"
date: 2004-11-30
forum: General Help
---

### Post by Infatuated_iPod on 2004-11-30
If i want to get wine, should i download the Debian version?

---

### Post by adbak on 2004-12-01
Did ya know there's a Wine in Universe?

---

### Post by Infatuated_iPod on 2004-12-01
I dont even know what universe is.. :-\

.. did some reaseacrh and tried to activate universe but when i tried to acess the programs i got this message.. 

>  Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory) 

---

### Post by adbak on 2004-12-01
In a terminal, type ```
cat /etc/apt/sources.list
``` copy and paste it here.  Somewhere you should have two lines that say ```
# deb http://archive.ubuntu.com/ubuntu/ warty universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe

```  There may or may not be the number signs in front of it.  Check to see that what you have matches what I have.

If yours has #'s in front of it too, then do ```
sudo emacs /etc/apt/sources.list
``` and cursor down until you get to those lines, take out the #'s ONLY in front of those lines, save and exit.

apt-get update
apt-get install wine

You may or may not get an error message saying something to the tune of duplicate sources -- that's okay, nothing to worry about.  When you're done, open up emacs again to edit the file and put those #'s back where they belong.

---

### Post by Infatuated_iPod on 2004-12-01
Okay, i got wine to work, and i also gained alot of ubuntu experience today. Now, is there a list of programs that work with wine? And how exactly do you use it? Would it be possible to emulate itunes and use an ipod with wine? itunes is the only reason i still have winxp on this computer.

---

### Post by jdodson on 2004-12-02
[QUOTE=Infatuated_iPod]Okay, i got wine to work, and i also gained alot of ubuntu experience today. Now, is there a list of programs that work with wine? And how exactly do you use it? Would it be possible to emulate itunes and use an ipod with wine? itunes is the only reason i still have winxp on this computer.[/QUOTE]

you cannot using vanilla wine to emulate itunes(or at least i don think you can).  crossover office is  going to support(albiet it seems really buggy) itunes in thier next release.  check the crossover office site:

[http://www.codeweavers.com/products/crossover/](http://www.codeweavers.com/products/crossover/)

if you want a native way to handle your ipod checkout gtkpod, the website is here:

[http://gtkpod.sourceforge.net/](http://gtkpod.sourceforge.net/)

you could check synaptic and see if there is a version available.  if not you can install it off the site.  btw gtkpod allows you to do thinkgs itunes does not, like take songs OFF the ipod.  i believe you can use it like a harddrive as well in ubuntu, anybody know for sure on this?

if you want a music player with similar look and feel and functionality to itunes but without the music store checkout rhytmbox, it is installed default in ubuntu.  i use it and really like it.  it has radio stations and a nice interface for managing your songs.  if you want mp3 playback you need to install the gstreamer-mad plugin that you can get off the mailrat repoistory.  you can do a forum search for multimedia howto and you should find info on howto do that.

hope that helps.

---

### Post by Infatuated_iPod on 2004-12-02
yea  i use mine as a hard drive in ubuntu now...and i didnt have to set anythinig up, it just worked.

---

### Post by jdong on 2004-12-02
```

jdong@jd64:~ $ apt-cache search gtkpod
gtkpod - A software using GTK2 for managing songs and playlists on an Apple iPodaptjdong@jd64:~ $ apt-cache show gtkpod
Package: gtkpod
Priority: extra
Section: universe/sound
Installed-Size: 812
Maintainer: QuÃ´c Peyrot <chojin@debian.org>
Architecture: i386
Version: 0.72-2-2
Depends: libatk1.0-0 (>= 1.6.0), libc6 (>= 2.3.2.ds1-4), libglib2.0-0 (>= 2.4.1), libgtk2.0-0 (>= 2.4.4), libid3tag0 (>= 0.15.0b), libpango1.0-0 (>= 1.5.2)
Filename: pool/universe/g/gtkpod/gtkpod_0.72-2-2_i386.deb
Size: 264978
MD5sum: 791296fa9adf5ffe78f948b443c48107
Description: A software using GTK2 for managing songs and playlists on an Apple iPod
 gtkpod is a platform independent GUI for Apple's iPod using GTK2. It
 allows you to upload songs and playlists to your iPod. It supports ID3
 tag editing, multiple charsets for ID3 tags, detects duplicate songs,
 allows offline modification of the database with later synchronisation,
 and more.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

Gtkpod is in Hoary's universe.... not sure about Warty, though.

---

