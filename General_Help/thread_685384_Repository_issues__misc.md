---
title: "Repository issues / misc"
date: 2008-02-02
forum: General Help
---

### Post by Xephrey on 2008-02-02
Okay, here are the repositories that have been reset and I'm not sure if they are updated for gutsy gibbon or not, but I have tried several alternatives with no results. I was able to find an online article on PC mag's website about Advances Desktop Effects Settings installation, which looks like it does essentially the same thing as beryl, but it still does nothing. 

I'm running an ASUS F3Jm with an Nvidia GeForce 7600. 

Here are the repository errors - mainly wine and beryl:
==============================================================================
[http://wine.lowvoice.nl/apt/dists/gutsy/Release.gpg:](http://wine.lowvoice.nl/apt/dists/gutsy/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/gutsy/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/gutsy/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'
[http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz:](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 88.191.250.18 80]
[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz:) 404 Not Found
==============================================================================

I'm running KDE and it seems that I cant access the restricted driver enable/disable manager. So that has me a little confused. 

Thanks for reading!

---

### Post by zvacet on 2008-02-02
I belive beryl is replaced with compiz-fusion,so you can use that.You can remove that lines from your source list 

```
gsudo gedit /etc/apt/sources.list
```

and remove these lines and if you want wine repo read [URL=
http://www.winehq.org/site/download-deb]this[/URL].

---

### Post by Nythain on 2008-02-02
what are you trying to pull off those repos???
wine.lowvoice.nl doesnt exist, but if its wine you are trying to install then check out
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
gives instructions for adding the wine repo to the sources list and all that jazz...

as mentioned above, beryl has merged back with compiz and is called compiz-fusion... more information can be found here
[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)

and as for canonical repo, i thought they just ended up throwing all thier stuff into the default gutsy repos??? so im pretty sure anythign that used to be gotten off of ubuntu.canonical.com or whatever is now located somewhere within the regular, universe, or multiverse gutsy repo... i could be wrong on that one though

---

### Post by zvacet on 2008-02-02
> so im pretty sure anythign that used to be gotten off of ubuntu.canonical.com or whatever is now located somewhere within the regular, universe, or multiverse gutsy repo... i could be wrong on that one though

Canonical is replaced with 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

so add that line to your source list.sorry for overlooking that one.

---

### Post by Xephrey on 2008-02-02
Well, Wine is updated and the update prompts dont bother me anymore with error messages, but I still dont have compiz-fusion up and running. I run Kubuntu on this laptop with an Nvidia graphics card - and I saw and downloaded the plugins, the site said, was needed in order for it to work properly in kubuntu. I added the necessary repositories that I was told to add, and I have the advanced settings. What am I missing? 

Thanks for all the help I've already recieved! :)

---

