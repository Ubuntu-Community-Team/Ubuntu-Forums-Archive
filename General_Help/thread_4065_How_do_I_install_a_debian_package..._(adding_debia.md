---
title: "How do I install a debian package... (adding debian repositories)"
date: 2004-11-11
forum: General Help
---

### Post by Monika on 2004-11-11
Ubuntu's repositories do not have a program I want (a gadu gadu Instant Messenger called "Kadu"), but there is a package made for debian...
There is also a tar file, but the ubuntu repositories don't seem to have some of the dependencies for that either... or at least when I search for Glibc, there is no such package. So maybe I shouldn't be installing the debian package either? I don't know...

Anyway, kadu's main page is:
[http://www.kadu.net/index.php?page=news&lang=en](http://www.kadu.net/index.php?page=news&lang=en)

The repositories for the debian packages are:
deb [http://kadu.net/debian/woody](http://kadu.net/debian/woody) ./
deb [http://kadu.net/debian/sarge](http://kadu.net/debian/sarge) ./
deb [http://kadu.net/debian/sid](http://kadu.net/debian/sid) ./

I think I should be choosing the sarge repository. I tried adding it via synaptic but I'm not sure what to put in under distribution and section and whatever I tried it would give me errors...

help please :)

---

### Post by az on 2004-11-11
deb http:http.us.debian.org/debian testing main 

so in synaptic that would be
http.us.debian.org/debian
testing
main


You could also use 
main contrib non-free
 as your last line.

glibc = libc6

To compile, you will need libc6-dev;  Just install build-essential.

---

### Post by ashley_v on 2004-11-11
If you get your hands on the package itself and you know it won't complain about a dependency then use:

dpkg -i package.deb

You don't always have to use apt but apt is really convenient most times.  For more info just 'man dpkg'

---

### Post by Monika on 2004-11-11
azz, this totally doesn't solve the problem.
I do not want to add http.us.debian.org/debian to my repositories because the kadu package is not there and I don't need anything from there I think. The addresses for the debian kadu packages are listed on this page:
[http://www.kadu.net/download/binary/debian/](http://www.kadu.net/download/binary/debian/)

And I have no idea how to add them. I added:
deb [http://kadu.net/debian/sarge](http://kadu.net/debian/sarge) testing ./

But when I asked synaptic to reload, it said something about this repository not being there or something like that. Since I have absolutely no idea what the "./" on the page I just linked is for, I'm assuming I've done something wrong.
Especially that there are debian kadu packages listed at that address.

---

### Post by Monika on 2004-11-11
Thanks ashley :) I can get hold of it, but I'm pretty sure that it will have some dependencies... especially that it's a program for KDE originally, so it might need some KDE libraries or something and I'm not too keen on doing the dependencies on my own...

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 Ok then make sure you add the entry for the repository correctly.   Also I'm pretty sure you want to run apt-get update first but synaptic will have exclusive lock on apt database so when you know that you added the location look for an option in the synaptic menu to reload or update your apt sources.

I'd bet it would be more simpler to just open up your /etc/apt/sources.list and add it there then run apt-get update ; apt-get install thepackageyouwant.  That way you can see how the other repositories are listed and you can just copy and paste.

---

### Post by Monika on 2004-11-11
The thing is, I don't know how to put it in correctly... If I did then I wouldn't be having a problem!
I tried manually editing /etc/apt/sources, and put in the exact line that's on the kadu page:

deb [http://kadu.net/debian/sarge](http://kadu.net/debian/sarge) ./

I also tried doing it based on other lines in threads on this forum and naturally the ubuntu ones I have synaptic. But none of my attempts work!
Synaptic still complains that it can't find that repository (it can't connect to it). But it's obviously there cause if you click on the link, it loads.

I just tried looking through the dependencies listed on the site, but it's awfully confusing because about 80% of those libraries seem to have different names in ubuntu. Either that or the ubuntu repositories are seeeeriously lacking in libraries. Anyway, it's practically impossible for me to even check if I have them installed. Very annoying!!

---

### Post by Monika on 2004-11-13
Nobody else has any ideas on how I should input the repository? :(

---

### Post by wallijonn on 2004-11-13
I noticed that there is a libgadu in SPM...

---

### Post by Monika on 2004-11-13
Well, there are instant messengers in the ubuntu repositories that I can use for gadu gadu.
Gaim supports gadu gadu, but gaim only supports a veeeeery limitted amount of gg's functions.
Then there's gnu gadu which IMO is buggy and annoys me. It doesn't support all gg functions either (although more than gaim does) and I hate the interface. Like gaim, it doesn't have the native emoticons which I would like and also it's in Polish which means it has Polish characters missing in the commands, settings and all which is annoying cause I get strange characters instead.
Then there's ekg which supports just about all gg features I can think of but is a) console based (so no native emotikons either - that's my biggest issue with it being console based) b)also has Polish characters missing.

Kadu supports all gg features I would like, can be set to English so I don't have to get annoyed at the lack of Polish characters in the menus and has native gg emotikons, so I deeeefinetely want kadu.
I did manage to get kadu running on SuSE linux and this even though I was solving all the dependencies myself, so it has to be possible. It's just that Ubuntu seems to be complicating it for me even more than SuSE was :P

Unless you ment that I don't have to worry about the libgadu dependency, but there's lots of others for kadu anyway... (or at least for compiling kadu from sources) And many of them I can't find in synaptic which means they're probably under different names like the glibc that azz mentioned.

---

### Post by Oolong on 2004-11-13
Monika-

Synaptic's Repository entry forms have a problem with the ./ of some of the 3rd party Debain depository's.  the way to get around this is to open a terminal and edit the sources list by hand.

$ nano -w /etc/apt/sources.list

then add  your new repository on a blank line at the end of the file

deb [http://kadu.net/debian/sarge](http://kadu.net/debian/sarge) ./

"Control - X"  to exit   "Y" to save

if you don't do a " sudo apt-get update" before running synaptic again. Synaptic will give you an error message about the missing  packages.gz file for the new repository.  Just close the pop-up and "Reload" (update ) the packages list and you will be able to install packages form your new repository through the gui interface. 

Eric

---

### Post by Monika on 2004-11-13
Thank you!! :)

It worked :)

---

