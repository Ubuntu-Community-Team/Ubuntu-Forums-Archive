---
title: "abiword vs openoffice"
date: 2005-05-17
forum: General Help
---

### Post by upalm on 2005-05-17
i'm running ubuntu on an older laptop (266/128/12gb) and i find that openoffice word processor takes a while to load. am i correct in thinking that abiword would be a better option seeing as it has lower system requirements (esp RAM). if so, where do a i get a version which will run on ubuntu? thanks for pointers!
upalm

---

### Post by tread on 2005-05-17
Fire up synaptic, search for abiword, select and install it.

You are right, abiword would be lighter .. esp. if you are using a gtk-based desktop since the gtk libraries would already be loaded. Openoffice doesn't use gtk or qt, so loading it requires more memory since its own widget set is also loaded.

---

### Post by upalm on 2005-05-17
i've fired up synaptic had a good look in it (incl search) and abiword is not there....what have i missed? :-?

---

### Post by tread on 2005-05-17
It's in universe I think. Take a look at [here](http://ubuntuguide.org) for help on adding extra repositories.

Basically, 
1. cd /etc/apt
2. sudo gedit sources.list
3. uncomment the universe repositories
4. sudo apt-get update
5. fire up synaptic and search again.

---

### Post by upalm on 2005-05-17
Thanks for your reply. At present i'm only using this machine as standalone and have no net-connectivity as such which precludes going online in any way, shape or form. I was hoping that Abiword was part of the original install but I guess not. If i'm not mistaken, the LIVE cd has a version of Abiword on it? Assuming this is the case should I be able to install it from that CD onto my hard drive?
Cheers
upalm

---

### Post by penvzila on 2005-05-17
Abiword is enough for me, except in a few cases.  One of those cases is OpenOffice's excellent Math formula engine.  

Anyway, there are some things you actually can do in Abiword, that people complaint about not being able to do, because they are not that obvious.

For example:

In openoffice, you can export to PDF. There is no export to pdf button in Abiword, BUT you can export to postscript... from the command line:

```
abiword --print=FILE.ps FILETOCONVERT.abw
```



One thing I would like to see is better svg support. Charts that I export from gnumeric in SVG format and then import into Abiword look absoultely terrible.

---

### Post by bored2k on 2005-05-17
I don't think you can compare Abiword with OOo. It's like comparing Wordpad with Word2003. One is light and can do the job for some, the other is better but hungrier.

---

### Post by apollyonis on 2005-05-17
[QUOTE=upalm]Thanks for your reply. At present i'm only using this machine as standalone and have no net-connectivity as such which precludes going online in any way, shape or form. I was hoping that Abiword was part of the original install but I guess not. If i'm not mistaken, the LIVE cd has a version of Abiword on it? Assuming this is the case should I be able to install it from that CD onto my hard drive?
Cheers
upalm[/QUOTE]

Unfortunately it doesn't appear that an Abiword install is on the Live! CD. There's information over Abiword in the form of an html page with some screenshots, but that's it.

---

### Post by az on 2005-05-17
Abiword was on the Warty cd (ship seed) but not in Hoary.

You should be able to use a Warty Cd to get that version on your system...


Abiword is great!

---

### Post by rosslaird on 2005-05-18
[QUOTE=penvzila]In openoffice, you can export to PDF. There is no export to pdf button in Abiword, BUT you can export to postscript... from the command line:[/QUOTE]
On my system, I can use the print dialog to directly make a pdf. No command line needed.
I have Abi 2.2

---

### Post by upalm on 2005-05-18
I have downloaded some abiword package files as follows:

1)abiword-common_2.2.2-1ubuntu2_all.deb
2)abiword-gnome_2.2.2-1ubuntu2_i386.deb
3)abiword-help_2.2.2-1ubuntu2_all.deb
4)abiword-plugins-gnome_2.2.2-1ubuntu2_i386.deb

-which of these packages do i need to install for a complete version of Abiword - i.e, what is the difference between 1 and 2? I'm running a p266 so am thinking 2 would be correct??? I'm guessing that 3 and 4 will run on any installation?
-how do i install these onto my hardrive to get a functioning application? (for various reasons i cannot connect to the internet to update my packages through synaptic and thereby get Abiword)

as ever, all help is much appreciated!
upalm :???:

---

### Post by tread on 2005-05-18
You will need at least

abiword_2.2.2-1ubuntu2_i386.deb
abiword-common_2.2.2-1ubuntu2_all.deb

The gnome package might add some gnome-specific things, so you can install that tool.
Of course you would need all dependencies too, find out what you need by going to packages.ubuntu.com and searching for abiword. Then find out whats installed from that list in synaptic, and get the rest.

---

### Post by upalm on 2005-05-18
thanks for the heads up. how do i actually perform the installation though? do i look for a setup.exe file within each package or something like that?

---

### Post by tread on 2005-05-18
dpkg -i filename.deb
If that fails on a dependency, install the dependency first and try again.
It might also work if you put all on the same line .. like dpkg -i f1.deb f2.deb etc. ..

---

