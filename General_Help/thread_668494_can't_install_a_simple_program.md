---
title: "can't install a simple program"
date: 2008-01-15
forum: General Help
---

### Post by Kalidor on 2008-01-15
This is a program that converts pfm font files to afm files. [http://www.ctan.org/tex-archive/fonts/utilities/pfm2afm/](http://www.ctan.org/tex-archive/fonts/utilities/pfm2afm/)

I just download it and unzip it. What do I run next? Please have a try yourself cause a normal ./configure, make didn't do it.

---

### Post by Kalidor on 2008-01-15
up

---

### Post by sumguy231 on 2008-01-15
Unless I'm looking at the wrong .zip, that's a zipfile containing Windows binaries. You'll need to install [Wine]("https://help.ubuntu.com/community/Wine") to run them.

---

### Post by Kalidor on 2008-01-15
I saw a makefile too in there.

---

### Post by sumguy231 on 2008-01-15
So there is, and source too. My bad. I guess that's what the Unix patch on that page is for.

---

### Post by Kalidor on 2008-01-15
How do I use that patch?

---

### Post by sumguy231 on 2008-01-15
You're supposed to use the patch command in some fashion like this:
```
patch -p0 <unix.patches
```
Where p<num> is the patchfile level, but I've never quite understood that option and I can't get it to not fail at any patch level.

Considering there are no build instructions for people who don't know much about patch or make, It looks like it might just be easier to install Wine and run the precompiled Windows binary.

---

### Post by Frogbarf on 2008-01-15
I've visually compared the unix.patches file with the pfm2afm.c & pfm2afm.h files and find that the patches have _**already**_ been applied.:KS

In other words, the presence of the file unix.patches appears to be a red herring; possibly included so you could back up one version. (That's just a guess.):lolflag:

Next step: to see if the unpatched C code will compile. Has anybody tried this yet?

Postscript: executing *gcc -c pfm2afm.c* produced a cloud of error messages and no output. At least not that I can find.

Postscript #2: does anybody know what the right compiler would be for the C code here?

---

### Post by aysiu on 2008-01-15
You may also want to try the RPM package: ```
wget  -c ftp://rpmfind.net/linux/dag/fedora/3/en/i386/dag/RPMS/pfm2afm-1.0-1.1.fc3.rf.i386.rpm
sudo apt-get update
sudo apt-get install alien
sudo alien -i pfm2afm-1.0-1.1.fc3.rf.i386.rpm
```

---

### Post by Frogbarf on 2008-01-16
after unzipping pfm2afm.c & pfm2afm.h into a directory

doing "make pfm2afm" generated a working program I can invoke via ./pfm2afm

But how do I now install this so it's visible system-wide? The web pages I've found say various things, all of which give errors when I try them.

These don't seem to work:

sudo make install
sudo make install pfm2afm
sudo checkinstall pfm2afm
sudo checkinstall

---

### Post by zionpsyfer on 2008-01-16
The easiest way would be to create a bin file in your home directory (/home/USERNAME/bin) and copy the pfm2afm file there.  IIRC, when opening a shell, bash will check for the existence of that directory.  If it exists, it is added to your path.   My .profile file in my home dir does contain the following:
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

It should be the same for you. If this doesn't work, you could always do it the dirtier way and try copying the pfm2afm file to somewhere in your path such as /usr/local/bin.

---

### Post by Frogbarf on 2008-01-17
By sheer chance I discovered a shell script in /usr/bin called pf2afm which does what pfm2afm does.

It's already installed by Ubuntu so you don't need to do anything except run it.

The notes say it uses the .pfb & .pfm files if present.

It's invoked in a terminal window with "pf2afm filename" where filename is the font file name excluding the dot and extension.

There is one hiccup: it assumes that the .pfb & .pfm extensions are in lower case and doesn't recognize .PFB & .PFM files. You have to rename them.

I presume this is a lot more up to date than the antique pfm2afm I and others have been trying to get up and running.

Is everybody laughing yet?:lolflag:

---

