---
title: "How do I make an instalable ubuntu with all my favorite settings and programs ?"
date: 2007-02-14
forum: General Help
---

### Post by gvzfs1972 on 2007-02-14
Imagine this...

You have all the settings right, the programs are all in and running as they should.
Now it´s time to make a back up and have the system packed to one .ISO which you then can boot for reinstall at your convenience.

Is this at all posible?:confused:

---

### Post by Jammy_Stuff on 2007-02-14
I'm also interested in this. Anyone?

---

### Post by ssam on 2007-02-14
i think [reconstructor]("http://reconstructor.aperantis.com/index.php") is what you want.

---

### Post by ezphilosophy on 2007-02-14
> **ssam said:**
> i think [reconstructor]("http://reconstructor.aperantis.com/index.php") is what you want.

Took the words right out of my mouth.

---

### Post by barney_1 on 2007-02-14
At first look Reconstructor kicks butt!  Is it pretty stable?

---

### Post by KaroSHiv0n on 2007-02-14
Oh this looks good, thanks for this im gonna check it out now.

---

### Post by ssam on 2007-02-14
> **barney_1 said:**
> At first look Reconstructor kicks butt!  Is it pretty stable?

i have not used it myself, but i think it is used by some of the non-english speaking  groups to make localised ubuntu version, and by some of the derivative distros (maybe the christian and satanic editions).

---

### Post by barney_1 on 2007-02-14
On further review, this won't take the desktop I have setup right now and make an install disc out of it will it?  I got excited there for a bit.

---

### Post by Artemis3 on 2007-02-14
Read here: [http://ubuntuforums.org/showthread.php?t=256406](http://ubuntuforums.org/showthread.php?t=256406)
I have tried Reconstructor but its gnome only; UCK uses a bunch of scripts but in the end i only attained full control following the instructions here: [https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06) which works with current live isos. With this method you "mount" the iso and then in a chroot enviroment proceed to add / remove the packages you want, and edit pretty much anything as if the os was already installed, then you finish and rebuild the iso again.

This is even easier than the painful gNewsense builder process, and works with those isos (and any ubuntu livecd derivative) too :)

---

### Post by aysiu on 2007-02-14
Since this is really a support question, I've moved the thread to general help.

---

### Post by ardchoille42 on 2007-02-15
> **ssam said:**
> i think [reconstructor]("http://reconstructor.aperantis.com/index.php") is what you want.

Reconstructor makes a livecd of your installed system, but, does it allow some way for that livecd to be installed to the hard drive?

---

### Post by aysiu on 2007-02-15
> **ardchoille42 said:**
> Reconstructor makes a livecd of your installed system, but, does it allow some way for that livecd to be installed to the hard drive?
Yes. It does.

---

### Post by ahmatti on 2007-03-20
I read about this from the reconstructor forums [http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=260&catid=2](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=260&catid=2).

So to put your settings in a live (or installation) cd you can copy them to /etc/skel/ directory of the reconstructor root. The files in this directory will be in the home folder of each user of the installed ubuntu meaning  that the same files and settings will be then copied to **all** users of the system. Anyway this is not a problem for me :) I haven't tried this yet, but maybe I will this evening...

Quote from nuclear_eclipse in reconstructor forums:
>  /etc/skel/ is the user home "skeleton" directory. Whenever a new home folder is created (via adduser, etc), the contents of /etc/skel/ are copied to the new location. Anything that should be in a user's profile by default (like links to Examples, program settings, etc) should be placed in this location.

---

### Post by ahmatti on 2007-03-20
> **Artemis3 said:**
> I have tried Reconstructor but its gnome only.  

Reconstructor works also with Xubuntu (I guess also Kubuntu, but I haven't tried) as far as package and splash screen customization goes. The desktop conf you can do as mentioned in my post above :) Reconstructor is **great**!!!!

---

