---
title: "Installer That Sloves Dependency Problems"
date: 2008-05-29
forum: General Help
---

### Post by Brando569 on 2008-05-29
Whats a good program that will solve (download) dependency problems for packages I download from websites (ex. outside of synaptic)?

---

### Post by bwhite82 on 2008-05-29
I've never heard of anything like this, however, that doesn't mean it doesn't exist (the intarweb is a big place). Most decent applications/utilities also come with decent documentation which lists required dependencies. Usually the README file in tarballs.

---

### Post by Brando569 on 2008-05-29
i remember i had something before, i want to say it was called GdebiK or something like that but i cant find it anymore. I'm trying to install the RPM version of the usenext client since when i try to download the DEB for it it gives me a 404 error.

---

### Post by bwhite82 on 2008-05-29
Check out the package alien for RPM packages. And is it GDebi you're thinking of?

EDIT: I'm pretty sure GDebi is what Ubuntu uses when you double-click a downloaded .deb. I thought you meant a tool for resolving dependencies for things you need to compile.

---

### Post by ibuclaw on 2008-05-29
Dpkg + Aptitude does a pretty good job for me.

```
cd /path/to/deb
sudo dpkg -i name-0.1.2-3.deb

```
And if there are problems.

```
sudo aptitude install -f
```
And aptitude should either:
A) Sort out and install the dependancies along with your deb file.
or
B) Try to make a working solution (a way to get the deb file installed with as less hassle possible) and presents you a list of what needs to be installed/removed/heldback/etc (You either accept or reject it).

If the above doesn't work, or you can't find a solution that actually includes the installation of the deb file.
There is always strict pinning on your side to force things aggressively into place.
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
Then...
```
sudo gedit /etc/apt/preferences
```
And type in something like:
```

Package: **name**
Pin: version **0.1.2-3**
Pin-Priority: 1001

```
Information about the deb file can be found using:
```
dpkg -I name.0.1.2-3.deb
```
Under the aliases **Package:** and **Version:** respectively.

So! Save the file and when you next upgrade or force install, apt will have no choice but to accept it.
Although, do so at your own risk.

But, to be honest, if I'm usually getting this much trouble with a deb file, I usually just install the build-deps and compile the source with the option **PREFIX=/usr/local/bin/** enabled in the "./configure" settings.

Regards
Iain

---

### Post by Brando569 on 2008-05-29
thanks guys, gdebi is most likely what I was thinking of but for some reason it wasnt installed by default in linux mint, but yet it still wont open it because it says its owned by root and group is plugdev and it wont let me change them, even if i try to open it as root which is odd. it says it also might be corrupt which i know isnt the case because i can open it with kpackage and it gives me dependency errors.

---

### Post by oldos2er on 2008-05-29
I'd probably try auto-apt.

---

### Post by drs305 on 2008-05-29
Brando569,

Could you be thinking of getlibs, which obtains 32-bit dependencies for 64-bit systems.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

It also works for just 32-bit computers.

---

### Post by Brando569 on 2008-05-29
nah thats not it, it was most likely gdebi, i remember getlibs but forgot about it, ill check that out too thanks.

---

