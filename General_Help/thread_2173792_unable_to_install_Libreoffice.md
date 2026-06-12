---
title: "unable to install Libreoffice"
date: 2013-09-11
forum: General Help
---

### Post by Coder88 on 2013-09-11
Libreoffice is kind of important since I do a lot of writing, but my Ubuntu 12.10 synpatic/apt will not let me install libreoffice. Getting unmet dependency issues, even after I run 'apt-get -f install'
Any help solving this greatly appreciated; frustrating to get the unmet dependencies issues. Seems like I am caught in unmet dependency hell, Hotel California, no way out.

```

beowulf@hexacore:~$ **sudo apt-get install libreoffice**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have **unmet dependencies**:
 libreoffice : Depends: libreoffice-core (= 1:3.6.2~rc2-0ubuntu4) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
beowulf@hexacore:~$ **sudo apt-get install libreoffice-gnome**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 **libreoffice-gnome : Depends: libreoffice-core **(= 1:3.6.2~rc2-0ubuntu4) but it is not going to be installed
                    ** Depends: libreoffice-gtk** but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
beowulf@hexacore:~$ **sudo apt-get install libreoffice-gtk**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 **libreoffice-gtk : Depends: libreoffice-core** (= 1:3.6.2~rc2-0ubuntu4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
beowulf@hexacore:~$ sudo apt-get install libreoffice-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 libreoffice-kde : **Depends: libreoffice-core** (= 1:3.6.2~rc2-0ubuntu4) but it is not going to be installed
E: **Unable to correct problems, you have held broken packages.**
beowulf@hexacore:~$ 
beowulf@hexacore:~$ **sudo apt-get install libreoffice-core**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
** libreoffice-core : Depends: libexttextcat-1.0-0** (>= 2.2-8) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
beowulf@hexacore:~$
beowulf@hexacore:~$ **sudo apt-get install libexttextcat-1.0-0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 **libexttextcat-1.0-0 : Depends: libexttextcat-data** (= 3.3.1-2) but 3.4.0-1~quantal1 is to be installed
E: Unable to correct problems, you have held broken packages.
beowulf@hexacore:~$ 
beowulf@hexacore:~$ **sudo apt-get install libexttextcat-data**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libexttextcat-data is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
beowulf@hexacore:~$ 

```

---

### Post by Lars Noodén on 2013-09-11
I didn't see a refresh of the package database in your output there.  Have you tried an update first?

```

sudo apt-get update

```

---

### Post by Coder88 on 2013-09-11
> **Lars Noodén said:**
> I didn't see a refresh of the package database in your output there.  Have you tried an update first?
```

sudo apt-get update

```

So I thought after doing apt-get updated, apt-get -f install, apt-get dist-upgrade that I successfully installed libreoffice using apt-get install libreoffice-common but then when I try to run libreoffice there is no joy. :(
```
$ libreoffice
/usr/bin/libreoffice: 181: exec: /usr/lib/libreoffice/program/oosplash: not found
$ 
```

---

### Post by ajgreeny on 2013-09-11
Why do you need to install libreoffice?  12.10 has it in the default install, unless you are using Lubuntu or Xubuntu, or maybe even Kubuntu (I'm not sure what comes with that).

I suggest you purge all applications related to libreoffice using synaptic, then enable the ppa for the newer version of LO and try installing that, which should give you LO 4.0.4.2 if not a newer version in 12.10.

---

### Post by vasa1 on 2013-09-11
> **ajgreeny said:**
> Why do you need to install libreoffice? ....
+1 to that. I wonder what is meant by "12.10".

---

### Post by Coder88 on 2013-09-11
> **ajgreeny said:**
> Why do you need to install libreoffice?  12.10 has it in the default install, unless you are using Lubuntu or Xubuntu, or maybe even Kubuntu (I'm not sure what comes with that).

I suggest you purge all applications related to libreoffice using synaptic, then enable the ppa for the newer version of LO and try installing that, which should give you LO 4.0.4.2 if not a newer version in 12.10.

I was using ArtistX linux (built on Ubuntu 12.10). I decided to just scrap ArtistX and I just installed Ubuntu 13.04 AMDx64 on my desktop. Was not too painful, preserved /home, preserved my Thunderbird email accounts and Firefox addons and Dropbox and wallpaper, etc. Just had to install a couple of non-synaptic apps (Trelby, FadeIn Pro).

So now I have Libreoffice!

---

### Post by bapoumba on 2013-09-11
That is one way to solve it :)

---

### Post by vasa1 on 2013-09-11
> **Coder88 said:**
> I was using ArtistX linux (built on Ubuntu 12.10). I decided to just scrap ArtistX and I just installed Ubuntu 13.04 AMDx64 on my desktop. Was not too painful, preserved /home, preserved my Thunderbird email accounts and Firefox addons and Dropbox and wallpaper, etc. Just had to install a couple of non-synaptic apps (Trelby, FadeIn Pro).

So now I have Libreoffice!
**This is the second time you haven't clearly stated the distro you've been using**. Next time, please be clear. People will still try to help but it will be easier for all concerned.

---

### Post by Coder88 on 2013-09-12
> **vasa1 said:**
> **This is the second time you haven't clearly stated the distro you've been using**. Next time, please be clear. People will still try to help but it will be easier for all concerned.

Well I did start out this thread saying "Libreoffice is kind of important since I do a lot of writing, but my  Ubuntu 12.10 synpatic/apt will not let me install libreoffice." because ArtistX is built on Ubuntu, and when I clicked 'About this Computer' it said Ubuntu 12.10 and ArtistX is not available as a distro prefix here on the forums. Regardless, I now have 'pure' Ubuntu 13.04 installed on my desktop.

---

### Post by coffeecat on 2013-09-12
> **Coder88 said:**
> ArtistX is built on Ubuntu,

It may be built on Ubuntu but, as you have discovered, distros built on Ubuntu sometimes do things that the parent Ubuntu does not - hence the need to be clear in your OP about what you are running. Good luck with using real Ubuntu 13.04, but in future if you need help with one of the derivative distros, please use the Other OS/Distro support forum here:

[http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

---

### Post by Coder88 on 2013-09-12
> **coffeecat said:**
> It may be built on Ubuntu but, as you have discovered, distros built on Ubuntu sometimes do things that the parent Ubuntu does not - hence the need to be clear in your OP about what you are running. Good luck with using real Ubuntu 13.04, but in future if you need help with one of the derivative distros, please use the Other OS/Distro support forum here:
[http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

Fair enough, will do.

I a dubious that the issue had to do with ArtistX, but who knows. I have a theory, not wanting to test it though-- that the issue might have been with my installing Dropbox via the .deb file at dropbox.com  That is what I had been doing, and I noticed after installing Ubuntu 13.04 (from ubuntu website) yesterday that when I was about to install the dropbox .deb that such an installed wanted to remove almost 300 packages. 300?!? I can not believe all of those 300 packages were simply meta reference packages. Maybe it was dropbox that messed up my ArtistX-Ubuntu system so I could not install libreoffice? I installed Dropbox instead by 'apt-get nautilius dropbox' and that method said it was doing to install a couple of new packages and no removal of other packages. Something seems very fishy about the .deb method of installing Dropbox that wanted to remove 300 packages (maybe it was 250, but it was very high between 250-300 as i recall).

---

