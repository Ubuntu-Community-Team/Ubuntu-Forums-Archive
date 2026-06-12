---
title: "Opengl man pages(edgy)"
date: 2006-10-30
forum: General Help
---

### Post by gorded on 2006-10-30
Does anyone know where i get opengl manpages from and how and where i can install them.


Thanks

---

### Post by gorded on 2006-10-31
bump

---

### Post by Blender on 2006-11-04
Hi!

There is an open bug in LaunchPad, you can report there too:
[https://launchpad.net/distros/ubuntu/+source/mesa/+bug/35632](https://launchpad.net/distros/ubuntu/+source/mesa/+bug/35632)

To manually install the manpages.
Create a directory, say ~/doc/glmanpages:
Go to [ftp://ftp.sgi.com/sgi/opengl/doc/]("ftp://ftp.sgi.com/sgi/opengl/doc/") and download mangl.tar.Z, manglu.tar.Z, manglx.tar.Z.
Note that in order to use file-roller to extract you will need the ncompress package (it's what I used).
```

$ sudo apt-get install ncompress

```
Using Nautilus go to that folder, double-click each file to open it with file-roller and drag the 'release' directory to your folder (where the .Z files are). Every one of them contains a single 'release' directory. When file-roller asks you whether to replace or skip, choose replace.
Then do the following in a terminal:
```

$ cd ~/doc/glmanpages
$ ls
mangl.tar.Z  manglu.tar.Z  manglx.tar.Z  release <-- this is what you should have in here
$ mkdir man3
$ mv release/xc/doc/man/GL/gl/*.3gl man3
$ mv release/xc/doc/man/GL/glu/*.3gl man3
$ mv release/xc/doc/man/GL/glx/*.3gl man3

```

Now you should have 208 files in the man3 directory.

All you need to do now is tell man where to find these files. Add the following line to your profile (e.g. ~/.bash_profile, if you are using bash. I added them to .zshrc for zsh)
```

export MANPATH=~/doc/glmanpages/man3:$MANPATH

```
That is, you add the directory containing the man3 directory to your MANPATH environment variable.

If you wanted to install the manpages for all users, i.e. globally, then instead of altering your profile you should do the following (in the ~/doc/glmanpages directory)
```

$ sudo mv man3 /usr/local/share/man

```

After you are done, do the following in the ~/doc/glmanpages directory:
```

$ rm -rf release

```

While searching for the manpages I found this page:
[http://emergent.unpythonic.net/01157053957]("http://emergent.unpythonic.net/01157053957")

Hope this helps.

---

### Post by geirha on 2007-02-22
Blender's guide here works fine, but it lacks one thing, the manpages should have lots of aliases, e.g. the manpage for the glVertex*-functions should not be called vertex, but glVertex2d, glVertex2f, etc (all aliases to the same man-page). This is done by the Makefiles which you can create from the Imakefiles. So I propose this guide (btw I'm using dapper, but it should be the same in edgy):

```

sudo apt-get install ncompress imake

# download
cd /tmp
wget ftp://ftp.sgi.com/sgi/opengl/doc/mangl{,u,x}.tar.Z

# unpack (you need the ncompress package for this to work)
tar xf mangl.tar.Z release/xc/doc/man
tar xf manglu.tar.Z release/xc/doc/man
tar xf manglx.tar.Z release/xc/doc/man

# configure and make (you need the imake package for this to work)
cd release/xc/doc/man/GL/
for dir in * ; do cd $dir && xmkmf && make && cd - ; done

# install (will install them into /usr/X11R6/man)
for dir in * ; do cd $dir && sudo make install && cd - ; done

# clean up
cd /tmp
rm -rf /tmp/release

```

---

### Post by predaeus on 2007-03-03
Thank you all for posting. I've only tried the last Howto. Works great on Edgy!

EDIT:
As an additional info, it installs to /usr/share/man/man3
```

...
+ install -c -m 0444 gluQuadricTexture.3gl /usr/share/man/man3
+ install -c -m 0444 gluScaleImage.3gl /usr/share/man/man3
+ install -c -m 0444 gluSphere.3gl /usr/share/man/man3
+ install -c -m 0444 gluTessBeginContour.3gl /usr/share/man/man3
...

```
and I am a bit confused because I think it just did so without root rights *g*

---

### Post by geirha on 2007-03-11
I see, on my Dapper system it installed them in /usr/X11R6/man/man3. Haven't looked too closely at the makefiles, but it probably has a clever way to figure out where best to put them.

As for the actual moving of the files, they were moved using root privileges. 

This is where the files get installed, and as you can see, it runs the make install command with sudo.
```
for dir in * ; do cd $dir && sudo make install && cd - ; done
```
It probably didn't ask you for a password though, since it remembers the password for a while, and it probably didn't take very long from when you installed ncompress and imake, till you installed the files.

---

### Post by notzed on 2007-04-19
If you want the man pages to work straight away might also want to add
```
sudo mandb

```
> I see, on my Dapper system it installed them in /usr/X11R6/man/man3. Haven't looked too closely at the makefiles, but it probably has a clever way to figure out where best to put them.


It's been a long time since I built X stuff, but if I remember correctly things like that are normally part of the Imake configuration files, FWIW.

---

