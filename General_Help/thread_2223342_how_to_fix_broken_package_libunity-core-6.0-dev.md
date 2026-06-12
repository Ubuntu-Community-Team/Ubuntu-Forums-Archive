---
title: "how to fix broken package libunity-core-6.0-dev"
date: 2014-05-10
forum: General Help
---

### Post by s9032g@comcast.net on 2014-05-10
I cannot run Unity Tweak in Ubuntu 14.04 because the subject package is broken. Synaptic won't let me reload the package until it is fixed. Sort of a catch 22.

Is there a solution short of reloading all of Ubuntu 14.04?

---

### Post by Frogs Hair on 2014-05-10
I am running Unity Tweak in 14.04 and  libunity-core-6.0-dev is not even installed . How did you install Unity Tweak ?

```
sudo dpkg --configure -a 
```

```
sudo apt-get -f install 
```

---

### Post by Bashing-om on 2014-05-10
[email]s9032g@comcast.net[/email]; Hey,

As a relatively new user to ubuntu, I must ask, in relation to this;
> 
Package libunity-core-6.0-dev
trusty (14.04LTS) (libdevel): Core library for the Unity interface - [color=red]development files[/color]

Why would you need/want/install "development files" onto your system ? 
"libunity-core-6.0-dev" is not part of the standard install:
```

sysop@1310mini:~$ dpkg -l libunity-core-6.0-dev
dpkg-query: no packages found matching libunity-core-6.0-dev
sysop@1310mini:

```

[INDENT][INDENT]but
all things are possible
[/INDENT][/INDENT]

---

### Post by s9032g@comcast.net on 2014-05-10
Maybe it is not part; however the error message when it does not run refers to that package.

I installed Unity Tweak with sudo apt-get install unity-tweak-tool gnome-tweak-tool. It was recommended on one of those sites recommending things to do after getting 14.04.

---

### Post by Bashing-om on 2014-05-10
[email]s9032g@comcast.net[/email]; Well,

Do not know where "libunity-core-6.0-dev" came from, not from the 'tweak' tools install :
> 
sysop@1310mini:~$ apt-cache depends unity-tweak-tool
unity-tweak-tool
  Depends: python3
  Depends: <python3:any>
    python3:i386
    python3
  Depends: gir1.2-glib-2.0
  Depends: gir1.2-gtk-3.0
  Depends: unity
  Depends: python3-xdg
  Depends: python3-cairo
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
sysop@1310mini:~$ apt-cache depends gnome-tweak-tool
gnome-tweak-tool
  Depends: python
  Depends: python
  Depends: gsettings-desktop-schemas
  Depends: gnome-shell-common
  Depends: python-gi
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-gnomedesktop-3.0
sysop@1310mini:~$ 

I do agree, would be best to remove it from the system - observing some caution to know what results.
Let's look at 'simulating' what will happen:
```

sudo apt-get remove -s libunity-core-6.0-dev

```
With the -s option to (s)imulate;
And let's see what we can learn.

[INDENT][INDENT]look before we leap
[/INDENT][/INDENT]

---

### Post by s9032g@comcast.net on 2014-05-11
I decided to just do without Unity Tweak. I can do want I need with Ubuntu Tweak

---

### Post by Bashing-om on 2014-05-11
[email]s9032g@comcast.net[/email]; Hey,

For my edification, was that a conflict between the two packages unity/gnome Tweak ?

[INDENT][INDENT]nicer in the affirmative (well, mostly)
[/INDENT][/INDENT]

---

### Post by s9032g@comcast.net on 2014-05-12
I wish I knew. If you Google the problem you will see that I was not the only person noting this problem. There are a lot of complaints about a broken Gnome package as a known error on 14.04.

---

### Post by Bashing-om on 2014-05-12
[email]s9032g@comcast.net[/email]; Good 'nuff.

Will put that under my hat.

[INDENT][INDENT]all's well that is well
[/INDENT][/INDENT]

---

