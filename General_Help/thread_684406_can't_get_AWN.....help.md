---
title: "can't get AWN.....help"
date: 2008-02-01
forum: General Help
---

### Post by DeathGrind on 2008-02-01
i keep trying to get AWN.  But i can't.  I keep getting this error when trying to install form the command prompt:

> The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages


when trying to install through the synaptic package manager i get:

> avant-window-navigator-bzr:
 Depends: libawn-bzr but it is not going to be installed
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: libawn-bzr but it is not going to be installed


I followed the instuctions on the wiki.  Still no luck.  I have a fresh install of ubuntu 7.10.
I know i have compiz, cause i am running the 3d cube and wobbly windows.  

Can someone help me out please.  I've been at this for days.

---

### Post by jan quark on 2008-02-01
try this 
```
sudo apt-get -f install
```

this should fix the broken packages

---

### Post by DeathGrind on 2008-02-01
cool.  Will try that tomorrow.  My pc is booted into vista right now and i am going to bed.  Just wanted to say thanks for the suggestion.  Will post back tomorrow if it was succesfull.

---

### Post by SOULRiDER on 2008-02-01
If you still cant get it working, check out this thread.
[http://ubuntuforums.org/showthread.php?t=385929](http://ubuntuforums.org/showthread.php?t=385929)

---

### Post by DeathGrind on 2008-02-01
> try this
Code:

sudo apt-get -f install

this should fix the broken packages


nope....that didn't work....will try SOULRiDER suggestion.

---

### Post by DeathGrind on 2008-02-01
> f you still cant get it working, check out this thread.
[http://ubuntuforums.org/showthread.php?t=385929](http://ubuntuforums.org/showthread.php?t=385929)


nope, tried that.  Man.....what gives.  I would really like to have this.

---

### Post by DeathGrind on 2008-02-01
okay i have been at this all day.  I just gave up on a repoistory install.  So i got the files for AWN and was going to do a manual config/install.  

In the tutorial i am following:  [http://wiki.awn-project.org/index.php?title=InstallingFromSource](http://wiki.awn-project.org/index.php?title=InstallingFromSource)


at the very beginning of the process step one as follows:
> Note: A list of Debian-based distributions can be found at Wikipedia.

    * Install all of the dependencies: 

apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev \
libgnome-desktop-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev python-gtk2-dev python-gconf \
gnome-common python-dev python-cairo-dev python-gnome2-dev python-gnome2-desktop gnome-panel python-glade2 librsvg2-common \
libgnomevfs2-dev

Note: You most likely need root privileges to run apt-get, that is, via sudo or su.

ok that is a no go for me i get this in my command line, this includes the command line from above also:

> nate@nate-ubuntu:~$ apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev \
> libgnome-desktop-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev python-gtk2-dev python-gconf \
> gnome-common python-dev python-cairo-dev python-gnome2-dev python-gnome2-desktop gnome-panel python-glade2 librsvg2-common \
> libgnomevfs2-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
nate@nate-ubuntu:~$ 
nate@nate-ubuntu:~$ 



so WTF is going on.  Why is this so much trouble....am i missing something.  Please someone give some more pointers.

---

### Post by DeathGrind on 2008-02-01
YES!!!!!!!!!!!!!!!!
I got it, somehow.  i restarted and used the sudo command for installing dependices, and the sudo command for the make install.  
Followed the guide, AWN started!  Cool.  
I am not sure why i had so much trouble, 
I am new to linux (if you couldn't tell).  But thanks for the help from everyone.

Thanks for you time.

---

### Post by DeathGrind on 2008-02-01
Hey can someone tell me how to enable AWN at system startup/login.  I got to gnome-session-properties.  But i am clueless as what to do from there.

Thanks

---

