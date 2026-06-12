---
title: "Can't update or install manager does not work"
date: 2007-01-22
forum: General Help
---

### Post by p110011 on 2007-01-22
Really Green Coffee Bean I guess.
Don't really know what or how I did this but I can't get updates or install any programs from any Add/Remove or synaptic manager.

Expanding the terminal panel shows this:

dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
field name '_' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

Oh duh....I'm running Edgy Eft GNOME desktop.

Any help would mmmmm help!:biggrin:

---

### Post by taurus on 2007-01-22
What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by p110011 on 2007-01-22
Well it seems like it gets 4 things and hits a bunch of sites, and at the end says:Fetched 4B in 1s (3B/s)  
Reading package lists... Done
gilles@gilles-desktop:~$ 

Sorry, I'm about a week old and don't really know what it just did.
I tried the update manager after that and still it does not work.

---

### Post by p110011 on 2007-01-23
Is there anything else I can do? I seem to be stuck with no more installing, updating or plug-ins. I tried to get codecs for movie player because some e-mail attachments are in .wmv format and I can't even switch players yet. Maybe if I just hit this butto..........................................

---

### Post by kosmic on 2007-01-23
Hum it looks like your system is using /usr/bin/python2.5 instead of /usr/bin/python2.4.

Easy way :

Fire up synaptic and remove python and the reinstall python again and it should work :)

---

### Post by p110011 on 2007-01-23
It won't work to remove anything either. It shows 2.4 installed as default and It can't remove it because the same errors.

I do remember trying to get my webcam going and getting the latest kernel (sudo something or other) it got everything ok, but there was something that said I already had the latest python. Actually there was two python files and firefox too. It said to do some remove command, and I copy/pasted it back to the promt it said I was not the owner or something.

I found what it says: 

build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  python-foomatic python-ipy mozilla-firefox
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by p110011 on 2007-01-24
Bump
Anyone?

---

### Post by p110011 on 2007-01-25
Does anyone know why this is happening?

when i do sudo apt-get updates and then sudo aptitude -f install
I get this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  libc6-dev
The following packages will be automatically REMOVED:
  easycam2
The following packages have been kept back:
  automatix2 cli-common flashplugin-nonfree libc6 libc6-i686 libsoup2.2-8
  libtotem-plparser1 totem totem-gstreamer totem-mozilla
The following NEW packages will be installed:
  aspell-el aspell-es libwv-1.2-1 wdanish
The following packages will be REMOVED:
  build-essential{p} cpp-3.4 easycam2 gcc-3.4 gcc-3.4-base gftp-common
  gftp-gtk gxine kdelibs-data kdelibs4c2a konsole libarts1c2a
  libavahi-qt3-1 liblua50 liblualib50 libopenexr2c2a libpcre3 libxine1 ntp
  ntp-server ntp-simple
0 packages upgraded, 4 newly installed, 21 to remove and 11 not upgraded.
Need to get 0B/1723kB of archives. After unpacking 80.2MB will be freed.
Do you want to continue? [Y/n/?] y
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `-' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `-' must be followed by colon 

I don't have much on my partition so maybe I should just reinstall.

---

### Post by timbosa on 2007-01-25
The /var/lib/dpkg/available file that you're having trouble with is a list of packages that are available to be installed.

Try doing

```
sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by p110011 on 2007-01-25
That did it!
Thanks!

---

