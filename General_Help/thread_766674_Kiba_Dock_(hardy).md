---
title: "Kiba Dock (hardy)"
date: 2008-04-25
forum: General Help
---

### Post by ronb94 on 2008-04-25
Hello
I installed kiba from this howto [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock) but using 602 version with physics enabled. This what I am getting when I am trying running kiba from terminal:
```

** Message: cant load file '/home/ron/.kiba-dock/config': Error reading file '/home/ron/.kiba-dock/config': Is a directory
```
I am running 64bit Hardy Heron.
Thanks

---

### Post by azazku on 2008-04-27
try this 

[http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/](http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/)

but i test it in my Hardy Heron 32 bit.

---

### Post by yogo on 2008-04-27
> **azazku said:**
> try this 

[http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/](http://tomateotra.wordpress.com/2007/02/04/howto-desktlets-en-ubuntu-kibadock-gdesklets-y-cairoclock/)

but i test it in my Hardy Heron 32 bit.


That is the most straight forward way I have seen of installing Kiba-dock, all the other guides listed in this forum have poorly written ways. I spent much time trying to install the Kiba-dock but many failures and tried on several different methods.

This link had it installed in seconds with no errors.

Great link!

---

### Post by adza on 2008-04-30
couldn't agree more... great link! works perfectly!

---

### Post by kulebreeze on 2008-06-01
i follow the steps from the link but nothing is happening for me am getting this when i run from terminal:
(kiba-dock:1465): Gdk-CRITICAL **: gdk_screen_get_monitor_geometry: assertion `monitor_num < GDK_SCREEN_X11 (screen)->num_monitors' failed

am using the 32 bit version..

---

### Post by redonwhite on 2008-06-02
That linke.  How do i get that page to display in english?

---

### Post by DaymItzJack on 2008-06-03
> **redonwhite said:**
> That linke.  How do i get that page to display in english?

You don't need to know the language, follow the instructions.

```
sudo apt-get remove &#8211;purge kiba-dock

sudo aptitude remove automake1.4

sudo aptitude install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

wget http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2

tar -xf kiba-dock-0.1.tar.bz2

cd kiba-dock

./autogen.sh

make

make install-schemas

sudo make install

Y luego se ejecuta:

kiba-dock
```

---

### Post by DXM31 on 2008-06-03
I'm getting a 404 on the wget step
So I just downloaded it.
But it didn't work:confused:
also what does "Y luego se ejecuta:" mean?
I just keyed in kiba-dock in the terminal and got an error.

---

### Post by rated_emman on 2008-06-11
hey guys.. i have the latest kiba dock without the physics... do i have to uninstall that and then install this one? or do they just over write?

thanks in advance :D

---

### Post by SiN_AmoR on 2008-06-11
```
sudo apt-get remove –purge kiba-dock

sudo aptitude remove automake1.4

sudo aptitude install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

wget http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2

tar -xf kiba-dock-0.1.tar.bz2

cd kiba-dock

./autogen.sh

make

make install-schemas

sudo make install

kiba-dock
```

that's how you do it :guitar:

---

### Post by bob_hilton on 2008-06-22
> **SiN_AmoR said:**
> ```
sudo apt-get remove –purge kiba-dock

sudo aptitude remove automake1.4

sudo aptitude install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

wget http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2

tar -xf kiba-dock-0.1.tar.bz2

cd kiba-dock

./autogen.sh

make

make install-schemas

sudo make install

kiba-dock
```

that's how you do it :guitar:

That did it perfectly for me! 8-)

---

### Post by Watchtow3r on 2008-06-27
How can I delete it if I wanted to? I can't find it in Synaptic or add/remove, and I can't even find the folders for it.

---

### Post by Jen5en on 2008-06-29
For some odd reason, the dock is "crashing" i.e. shutting down, whenever I try to drag the Home folder into it. Anyone else having this problem?

---

### Post by Watchtow3r on 2008-07-06
> **Watchtow3r said:**
> How can I delete it if I wanted to? I can't find it in Synaptic or add/remove, and I can't even find the folders for it.

bump

---

### Post by antid0te on 2008-07-08
Watchtow3r, just go to the kiba source dir and do 

```
make uninstall
```

that should uninstall kiba from source instalation :)

---

### Post by Teddy_P on 2008-07-13
the first time I did this I got this:
The following packages have unmet dependencies:
  libglitz-glx1-dev: Depends: libglitz-glx1 (= 0.5.6-1) but it is not installable
                     Depends: libglitz1-dev (= 0.5.6-1) but it is not installable

and it worked but was a little glitchy.
So I installed them first and everything is a lot smoother.



Good job and thanks a lot.
Teddy_P

---

### Post by lumix700i on 2008-07-16
As I tried to install libgtk2.0 dev thru synaptic, I get this error message

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 is to be installed

Is there anyway I can fix this..?

---

### Post by weweboom on 2008-08-11
I used the website to install kiba dock on hardy and it worked at first, but the next time I started my computer and tried to start it from terminal I got: 
```
** Message: Failed to merge unused desktop file /root/.kiba-dock/weweboom. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

** ERROR **: Failed to read config from gconf: (null)
aborting...
Aborted

```

---

### Post by astermagik on 2008-08-24
Hi,

I get the following, once  I have followed all the instructions and then try to run the final run command:

(kiba-dock:16832): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(kiba-dock:16832): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(kiba-dock:16832): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(kiba-dock:16832): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(kiba-dock:16832): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",


I can see that the dock launches but doesnt do anything useful.

Any ideas?

PS: Use google.com/translate and then paste the URL into the box to translate the original guide into english (or whatever other language you choose)

---

