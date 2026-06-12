---
title: "&lt;&lt; How to install gnome-commander in Ubuntu 19.04? &gt;&gt;"
date: 2019-05-02
forum: General Help
---

### Post by icamps on 2019-05-02
Hi,

I am trying to install *gnome-commander* using *apt* inside **Ubuntu 19.04** but *apt* did not find it.

```
sudo apt install gnome-commander
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-commander
```

The repositories are the defaults.

What should I do in order to get *gnome-commander* installed?

Regards,

Camps

---

### Post by slickymaster on 2019-05-02
*Thread moved to **General Help**.*

---

### Post by cruzer001 on 2019-05-02
It is not yet available as a deb package from ubuntu software sources.  Probably need to give it a few weeks.

[https://packages.ubuntu.com/cosmic/gnome-commander](https://packages.ubuntu.com/cosmic/gnome-commander)

Same for the PPA.

[https://launchpad.net/ubuntu/+source/gnome-commander](https://launchpad.net/ubuntu/+source/gnome-commander)

---

### Post by PaulW2U on 2019-05-02
> **cruzer001 said:**
> It is not yet available as a deb package from ubuntu software sources.  Probably need to give it a few weeks.
Actually gnome-commander was removed from the disco repositories on 2018-12-05 as it depends on unmaintained libgnome libraries. Many other packages have been removed for similar reasons. gnome-commander is also being removed from [Debian]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=912383") on which Ubuntu is based so unless major changes are made to its dependencies it won't be coming back.

---

### Post by cruzer001 on 2019-05-02
Well that to bad

Thanks Paul

---

### Post by Rubi1200 on 2019-05-02
As an alternative you might want to check out Double Commander:
[https://packages.ubuntu.com/disco/doublecmd-common](https://packages.ubuntu.com/disco/doublecmd-common)

Can be added via terminal or whichever package manager you prefer using.

---

### Post by Holger_Gehrke on 2019-05-02
Actually, doublecmd-common is the package containing the parts that doublecmd-gtk and doublecmd-qt have in common. To find out more about Double Commander, take a look at its page at [sourceforge]("https://sourceforge.net/projects/doublecmd/"). There are a lot of dual panel "Commander"-style file managers. I personally prefer the [Midnight Commander]("https://midnight-commander.org/").

Holger

---

### Post by Mark Phelps on 2019-05-02
The Cosmic packages are still here:  [https://packages.ubuntu.com/hu/gnome-commander](https://packages.ubuntu.com/hu/gnome-commander)

I'm using them on Disco and they work fine.

---

### Post by rbmorse on 2019-05-02
> **Holger_Gehrke said:**
> Actually, doublecmd-common is the package containing the parts that doublecmd-gtk and doublecmd-qt have in common. To find out more about Double Commander, take a look at its page at [sourceforge]("https://sourceforge.net/projects/doublecmd/"). There are a lot of dual panel "Commander"-style file managers. I personally prefer the [Midnight Commander]("https://midnight-commander.org/").

Holger

+1 on Midnight Commander.  Takes a bit of work to learn the keyboard shortcuts, but once you have those it's ten times ten-thousand times easier than mousing around and hoping you've clicked on the right thing.

---

### Post by icamps on 2019-05-05
Thanks to all for the helpful answers!

---

### Post by ecuentas on 2019-05-08
I tried to compile gnome-commander 1.10 from source (get it at [https://gcmd.github.io/download.html](https://gcmd.github.io/download.html) ) on a fresh ubuntu 19.04 disco dingo installation with

./configure && make && sudo -i make install

and was able to get through many dependencies but finally got stuck at "configure: error: Package requirements (libgnome-2.0 >= 2.0.0) were not met:

No package 'libgnome-2.0' found", but when I issue:

sudp apt install libgnome-2.0

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgnome-2-0' for regex 'libgnome-2.0'
libgnome-2-0 is already the newest version (2.32.1-6).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So the installation rutine can't find libgnome-2.0 but apt can. What gives? Any clues on how to get forward?

Thank you very much.

---

### Post by PaulW2U on 2019-05-08
> **ecuentas said:**
> Any clues on how to get forward?
You probably need to install **libgnome2-dev**.

---

### Post by ecuentas on 2019-05-08
Sorry missed this, these are the commands I issued to get to the point I did, I think one or two are not needed but I can't anymore remember which ones. Sorry, a beginner here (still even if on ubuntu since 6.06)

```
sudo apt-get install itstool
sudo apt-get install libxml2-utils
sudo apt-get install libglib2.0-dev
sudo apt-get install gtk+2.0
sudo apt-get install libgnome-2-0
sudo apt-get install yelp-tools
```

Thank you

---

### Post by Holger_Gehrke on 2019-05-08
'configure' doesn't check for the binary library, it looks for certain small pieces of source code that tell a compiler what functions are in the library, what type their return values are and what arguments they take. These so called header files are only needed when compiling programs that use a library and are not included in the package for the library. They are in packages of their own named after the library package but with the suffix '-dev' for development. So a quick 'sudo apt install libgnome2-dev' should get these (and through the magic of dependencies a lot of other headers you'll probably need too).

Holger

---

### Post by ecuentas on 2019-05-08
Thanks for the responses they have been very helpful

UPDATE

so this is the updated list of commands

```
sudo apt-get install itstool
sudo apt-get install libxml2-utils
sudo apt-get install libglib2.0-dev
sudo apt-get install gtk+2.0
sudo apt-get install libgnome-2-0
sudo apt-get install yelp-tools
sudo apt-get install libgnome2-dev
sudo apt-get install libgnomeui-dev
./configure && make && sudo -i make install
```

it takes me up to:

"make: *** No rule to make target 'install'.  Stop."

Whta is missing? Help. Thank you very much.

---

### Post by ecuentas on 2019-05-08
REALLY SOLVED

From [https://gcmd.github.io/download.html](https://gcmd.github.io/download.html) download source [https://download.gnome.org/sources/gnome-commander/1.10/gnome-commander-1.10.0.tar.xz](https://download.gnome.org/sources/gnome-commander/1.10/gnome-commander-1.10.0.tar.xz) and extract
cd to where you extracted the source

issue

```
sudo apt-get install itstool
sudo apt-get install libxml2-utils
sudo apt-get install libglib2.0-dev
sudo apt-get install gtk+2.0
sudo apt-get install libgnome2-dev
sudo apt-get install libgnomeui-dev
./configure
make
sudo make install
```

I only had the substract the "-i" from the "sudo -i make install" I was running.

And that is it. Now I am very happily running gnome-commander 1.10

Thank you all for all for your help.

---

