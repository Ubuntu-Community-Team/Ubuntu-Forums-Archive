---
title: "freenx installation"
date: 2005-05-31
forum: General Help
---

### Post by goingnutzz on 2005-05-31
i just downloaded and installed ubuntu hoary and wondering what i should do with it next. i would like to access it from work desktop (win xp) so am trying to install freenx. i've searched and followed the instructions posted by others but havent seen a response to this issue yet.

i made the changes to the /etc/apt/sources.list

added deb [http://kanotix.com/files/debian](http://kanotix.com/files/debian) ./

$sudo apt-get update
$sudo apt-get install freenx

everytime i get the error

the following packages have unmet dependencies:
freenx: depends: nxagent (>=1.4.0.2) but is not going to be installed
            depends: nxproxy (>=1.4.0.2) but is not going to be installed
E: broken packages

any help would be greatly appretiated. 

followed the faq for installing ssh and that works fine. is there a conflict somewhere? i also tried configuring samba but that's another question altogether.

thanks for the input.

linux convert to be...

---

### Post by Leif on 2005-05-31
Take out kanotix and add the backports, then install freenx.

---

### Post by goingnutzz on 2005-05-31
thanks.. i'm a little new to this.. so it should be

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) ./

and it'll find the correct files?
or do i need to point to a specific dir?

ex
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) ./dist/hoary-extras/main/binary-i386

---

### Post by jobezone on 2005-05-31
[QUOTE=goingnutzz]thanks.. i'm a little new to this.. so it should be

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) ./

and it'll find the correct files?
or do i need to point to a specific dir?

ex
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) ./dist/hoary-extras/main/binary-i386[/QUOTE]
 The backports homepage has the correct line:) 

Anyway, this is my backports apt line. Add it manually or using Synaptic:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

This lines give me the backports and extra packages.
The main server you are using in your example has been closed by the maintainer, so you have to use one of the mirrors listed in ubuntu backports homepage (like I did).

---

### Post by goingnutzz on 2005-06-01
thanks.  worked perfectly.  its a little slow though and i'm on a lan. there is a slight window lag when i drag a terminal window across the screen.  other than that.. it's so nice to sit at my xp machine and work on my ubuntu box without the extra accessories.

now onto getting samba.. apache and secure ftp working.

---

### Post by viniosity on 2005-06-02
[QUOTE=jobezone]The backports homepage has the correct line:) 

Anyway, this is my backports apt line. Add it manually or using Synaptic:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

This lines give me the backports and extra packages.
The main server you are using in your example has been closed by the maintainer, so you have to use one of the mirrors listed in ubuntu backports homepage (like I did).[/QUOTE]

I added those lines (and I've tried other mirrors) to my sources.list but when I do an apt-cache search for freenx or nxserver it comes up empty.  Have they been removed from the backports? Else is it possible that I need a different repository for amd64?

---

### Post by Jamesia on 2005-06-12
I installed freenx on Hoary fine, but I was wondering how I make a connection to an XP machine. Is there a manual somewhere that I'm missing? Thanks...

---

### Post by Leif on 2005-06-13
[QUOTE=Jamesia]I installed freenx on Hoary fine, but I was wondering how I make a connection to an XP machine. Is there a manual somewhere that I'm missing? Thanks...[/QUOTE]

You can only run a server on a linux machine. So for your XP machine you'd go to the nomachine website and download the client, then fill in the details and voila, you've got a linux session running in a window on your XP machine.

---

