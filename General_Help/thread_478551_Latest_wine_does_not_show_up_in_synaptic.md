---
title: "Latest wine does not show up in synaptic"
date: 2007-06-19
forum: General Help
---

### Post by jobsonandrew on 2007-06-19
Ive followed the instructions on adding the key or whatever it is on the winehq ubuntu download page, and ive added the repository too, but in synaptic, the only available version of wine is 0.9.37 rather than the latest version 0.9.39

I dont understand what im doing wrong, and yes ive typed sudo apt-get update and clicked reload in synaptic about a million times, ive also forced update manager to check for updates (I have 0.9.37 currently installed).. I downloaded the source for version 0.9.39 as well but the readme file must have been written by a dog or something because it is no help, whenever i type ./tools/wineinstall i get an error saying 'C compiler cannot create executables' or something, does anyone know of a very CONCISE and CLEAR guide on installing the latest wine from source...?

but id mainly like to know how to get synaptic to show me the latest stuff

---

### Post by reset3x on 2007-06-19
I did the same thing... Then when I went back and read the announcement I saw that the binaries are still being built.... So we have to compile or wait...... :(

---

### Post by vexorian on 2007-06-19
maybe you forgot to update the repository?


maye you needed:

sudo ./tools/wineinstall

?

Also, did you make sure 0.9.39 is supposed to be in the repository, they take some time to do it, and also, are you sure you need to update WINE? From my experience they don't really fix too much un 2 small versions.

---

### Post by JanvL on 2007-06-19
Hi,

Synaptic will not show you tha latest versions.
This is because the latest has dependancies with newer
programm-libraries.
So with synaptic you have a tool to install the newest STABLE
versions as a rule of thumb.

Sometimes programms are stable within themself like with
OpenOffice but you need quite some work to install them
seperately.

Or you could use autopackage for some programma but these will
start slower.

A good advise is to stick to the stable programms first.
As for Wine, I get new versions al the time with the next repo's
[http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper

Or install Automatix2 that gives you newer versions that work.

Have fun,

Jan

---

### Post by jobsonandrew on 2007-06-19
oh rite... im SURE i had version 0.9.39 showing in synaptic before i reformatted, but i forgot how i did it... anyway, i need the latest version (or a version other than the one im using) because I am experiencing a crash with a particular windows program that apparently only happens with 0.9.37... i might get the deb package for 0.9.36 and install that for now.. not unless someone can show me EXACTLY how to compile the version 0.9.39 from source..

ive tried sudo ./tools/wineinstall it wont let you do it, it says that doing it as root is not advisable and aborts the install

---

