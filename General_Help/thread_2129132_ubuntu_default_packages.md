---
title: "ubuntu default packages"
date: 2013-03-25
forum: General Help
---

### Post by Drenriza on 2013-03-25
Is their a place where you can see the default packages installed by the Ubuntu 12.04 LTS installation process,
without creating a VM installing the OS and seeing what packages are their?

The reason i ask, is that i removed totem-movieplayer (because i use VLC).
This then removed some packages that distorts the audio in movies with example high explosions, jets or such. Which just sounds all wrong.

I tried and install totem again, but still the same.
This first happends after the revoment of totem aka Movie Player(default movie player)

Kind regards.
Drenriza

---

### Post by schragge on 2013-03-25
There are many definitions of *default*. [Here](http://people.canonical.com/~ubuntu-archive/germinate-output/ubuntu.precise/desktop) are the packages installed by Ubuntu desktop.

---

### Post by ibjsb4 on 2013-03-25
Heres a package list of necessary and recommended packages.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

---

### Post by slickymaster on 2013-03-25
[Here]("http://packages.ubuntu.com/precise/metapackages/allpackages?format=txt.gz"), you have a list of all Ubuntu Packages in "precise".

---

### Post by ibjsb4 on 2013-03-25
> **slickymaster said:**
> [Here]("http://packages.ubuntu.com/precise/metapackages/allpackages?format=txt.gz"), you have a list of all Ubuntu Packages in "precise".

Your list includes lubuntu and xubuntu desktop :confused:

---

### Post by slickymaster on 2013-03-25
> **ibjsb4 said:**
> Your list includes lubuntu and xubuntu desktop :confused:

You're right, I'm noticing that now. Not only those, but also Edubuntu and Kubuntu desktops.
My bad, I should payed more attention to the fact that at the top of the page they do mention that the list contains all the Ubuntu Packages in "precise", which means that includes all the available desktop environments.

---

### Post by Frogs Hair on 2013-03-25
There are Gstreamer AV plug-ins/codecs which are Totem dependencies , but having never removed Totem I don't if some of them might have be removed . All Gstreamer plug-ins are in the sofware center and most are included with the restricted extras  .

---

### Post by stinkeye on 2013-03-25
Go to [http://releases.ubuntu.com](http://releases.ubuntu.com) for the release you want.

eg for precise (12.04.2)
[http://releases.ubuntu.com/precise](http://releases.ubuntu.com/precise)

Download the **.manfest** file for your architecture.
Just a text file you can open in gedit and do a search.

If you want the the older 12.04.1 release go to
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

