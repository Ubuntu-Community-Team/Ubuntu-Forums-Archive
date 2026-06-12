---
title: "[SOLVED] How do I get kubuntu to stop telling me about unmet dependencies?"
date: 2007-07-14
forum: General Help
---

### Post by acrefoot on 2007-07-14
I tried using the e17 and relate packages from the elivecd repositories (installed in Kubuntu) Installed without many problems.

Then, I tried installing "elpanel", a sort of control panel for elivecd. It wanted to install a whole bunch of dependencies, most of them relating to gnome stuff that I didn't want. So, I went to the repo itself, and got the .deb file, and forced it to install without deps using dpkg.


Now, whenever I try to install a new package with aptitude (et. al.) I get something like the following:
```
sudo aptitude install gtk-chtheme
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  elpanel
The following NEW packages will be automatically installed:
  python-cairo python-gobject python-gtk2 python-numeric
The following NEW packages will be installed:
  gtk-chtheme python-cairo python-gobject python-gtk2 python-numeric
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1865kB of archives. After unpacking 6722kB will be used.
The following packages have unmet dependencies:
  elpanel: Depends: efl-all (= cvs20070216) but cvs20060518 is installed.
           Depends: keybconf but it is not installable
           Depends: langconf but it is not installable
           Depends: synaptic but it is not installable
           Depends: engage-manager (>= 0.2-1) but it is not installable
           Depends: gnome-alsamixer but it is not installable
           Depends: foomatic-gui but it is not installable
           Depends: synaptic but it is not installable
           Depends: gparted but it is not installable
           Depends: gnome-system-tools but it is not installable
           Depends: x11vnc but it is not installable
           Depends: xvncviewer but it is not installable
           Depends: xscreensaver but it is not installable
           Depends: terminal-manager but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
elpanel

Score is -301

Accept this solution? [Y/n/q/?]  
```

Now, none of the solutions are very good for me. I tried elpanel, and it works just fine. It is *not* "BROKEN". Even if I try to reject the solutions, it keeps giving me new ones, and thus far I haven't been able to install anything new.

My question is: how do I get aptitude to ignore my "BROKEN"-ness for that package, and let me install other (completely unrelated) packages?

---

### Post by Nythain on 2007-07-14
not sure if you can short of uninstalling the deb via dpkg or aptitude and trying to compile from source... as long as that deb is saying that stuff = dependencies then apt is going to complain...

anyone else more experience with apt/dpkg/synaptic feel free to throw your two cents in here

---

### Post by acrefoot on 2007-07-14
Hmm, this kind of thing should be more standard. I come from a Gentoo background, where ignoring dependencies is a standard option of emerge. Well, maybe I can find the source, and try that, but I'm not sure if the source is readily available.

---

### Post by aysiu on 2007-07-14
Dependency errors usually stem from conflicting repositories sources.

Try [getting a fresh list](http://www.psychocats.net/ubuntu/sources#key) and then try again: ```
sudo aptitude update && sudo aptitude install gtk-chtheme
```

---

### Post by acrefoot on 2007-07-14
Perhaps you didn't read the whole of my original post. I realize that my sources.list is changed. In fact, I realize that the repos I'm using will probably have conflicts (I'm trying to use another disto's -- elivecd's -- repos). I'm willing to sort out the dependency issues, but I need to be able to manually ignore what aptitude (et. al.) is labeling as "BROKEN", so that I can install other packages.

Also, I can't find the source for elpanel. It's probably in svn or somesuch, but I would like something more stable.

---

### Post by Nythain on 2007-07-14
apt/dpkg doesnt recognize manually compiled software, only deb installed via apt/aptitude/apt-get/dpkg wich is why i recommended uninstalling the .deb via dpkg and manually compiling from source... though you might get dependency errors during the ./configure or make portion of the manual compile

Edit, ignore this as i just cought the last part of your post... if you cant find the source, do you have deb-src [http://whatever](http://whatever) for the repo that contains elpanel...

Edit again... wow, since elive and ebuntu dont provide deb-src repositories, and google just turns up random threads requesting the same thing (the source code for elpanel) then i think you might be screwed on the manual compile option... you might either just have to bite the bullet and install the deps or live without the elpanel... unless anyone else knows how to tell apt/apt-get/aptitude to ignore a pakcage when trying to utilize

---

### Post by dagnabit dang doohickey on 2007-07-14
Uninstall elpanel.
Make a directory in your home: mkdir elpanel-dir
Crack open the deb with: dpkg -x elpanel-package-name.deb elpanel-dir
Manually move or copy the extracted contents from elpanel-dir to the appropriate locations.

---

### Post by acrefoot on 2007-07-14
Yeah, I'm probably going to modify that approach a bit. I extracted and rebuilt the debs with just one change: removal of all the gnome bloat from the control file's dep listings.

It should work fine now.

On another note, updating using adept caused kubuntu to pull in all manner of hal and dbus stuff from the elive repos which screwed with my hardware recognition: most notably, my wifi card (Network-Manager stoppe working correctly). Must be something about the ubuntu versions of these packages that cause them to break when substitutes are used. I finally fixed it by removing those packages, removing the "main" thing (are they called "branches"? sorry, my terminology is that of a 1 day old kubuntuer) from the elive repos, and reinstalling the ubuntu versions of these packages (the versions with ubuntu in the name). Mixing distros isn't smooth work, even when they're both debian (in case you were wondering)--took about 5 hours overall to fix this morning.

---

### Post by acrefoot on 2007-07-15
It's not really solved, more like "hacked", but it'll do...and already too much energy is being wasted on this deceptively simple question.

---

### Post by der_vegi on 2007-11-05
Maybe [this]("http://linuxagora.com/vbforum/showthread.php?t=356") can help: They describe a way to extract your deb-file, edit the dependencies and rebuild it. That's how I get around this annoying "broken package" error.

> WARNING: You could break things by doing this.

You can use dpkg-deb to edit the package and change its dependencies.

Extract the filesystem tree to a directory "packagename.x.x.x":
```
dpkg-deb -x packagename.x.x.x.deb packagename.x.x.x
```

Extract the control file information:
```
dpkg-deb -e packagename.x.x.x.deb packagename.x.x.x/DEBIAN
```

```
cd packagename.x.x.x/DEBIAN
```

Edit the file called: control

Change the desired version number for the dependency that you want to change.

```
cd ../../
```

Rebuild the deb package:
```
dpkg-deb -b packagename.x.x.x packagename.x.x.x.deb
```


Reference:
man dpkg-deb

---

