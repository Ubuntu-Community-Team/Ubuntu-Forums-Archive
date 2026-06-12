---
title: "avi movie editor?"
date: 2005-05-03
forum: General Help
---

### Post by Gandalf on 2005-05-03
Hello,
does anyone know an avi files editor, i mean a program that can cut a part of a movie file, combine two avi files into one, spilt one into multiple file, does this exist???

---

### Post by wwwolf on 2005-05-03
The only thing I know of is Windoze Movie Maker but It is probably programmed to destroy itself if it detects linux. Although you could probably run it under Wine. I sure hope there is another editor out there but I have still not been able to find it yet. :cry:

---

### Post by Gandalf on 2005-05-04
i found Kino but it didn't open the avi file, don't have another format to try :(

---

### Post by wwwolf on 2005-05-04
Yea, and Cinelerra can't open them up either.  :-?

---

### Post by Bogart on 2005-05-04
I think that [Avidemux](http://fixounet.free.fr/avidemux/)   is what you're looking for. It's like VirtualDub for Linux. Unfortunately I didn't find it in the repositories. Maybe it is in debian's, so you can try that. Otherwise try to grab it from the site and install it by yourself (no clue about how to do it, didn't use it yet with Ubuntu).

---

### Post by JDay on 2005-05-04
Avidemux is in the marillat repository. It's not perfect by any stretch of the imagination, but it's the best we've got right now. Also, I think virtualdub is supposed to run well under wine, I believe winetools has a wizard or something for installing it.

---

### Post by wwwolf on 2005-05-04
[QUOTE=JDay]Avidemux is in the marillat repository. It's not perfect by any stretch of the imagination, but it's the best we've got right now.[/QUOTE]

Hmmm, I added the marillat respository and now this is what I get while trying to install it:

wwwolf@ubuntu2:~$ sudo apt-get install avidemux
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avidemux: Depends: liblame0 (>= 3.96.1-0sarge1)
            Depends: libxvidcore4 (>= 1:1.0.0-rc4-0.0) but it is not going to be installed
E: Broken packages

Do I need to add another repository?
Why is it telling me it depends on libxvidcore4 but that it is not going to install it?
Thanx,

wwwolf
ps I'm really new to this apt-get thing since I migrated from SuSE.

---

### Post by rnickum on 2005-05-05
On my system I now get the following error on instal of avidemux

The following packages have unmet dependencies:
  avidemux: Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages


Same error in synaptic or apt-get

Any ideas on how to resolve and install a working version?

---

### Post by wwwolf on 2005-05-05
[QUOTE=rnickum]On my system I now get the following error on instal of avidemux

The following packages have unmet dependencies:
  avidemux: Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages


Same error in synaptic or apt-get

Any ideas on how to resolve and install a working version?[/QUOTE]

I gave up on Avidimux and installed the new version of Kino which _was_ able to edit the avi file I had. Version 0.7.5 has alot more support for other file formats than previous versions did.

It sure helped me,

wwwolf

---

### Post by kori.mendocino on 2005-05-09
btw, avidemux in the merillat repo's is quite old, and so are it's dependancies' names. better compile from source

---

### Post by dukeinlondon on 2005-05-09
Has anyone tried Lives ? I think it does this sort of things and is under active development.

Correct me if I am wrong though

---

### Post by ralfsmith on 2006-03-22
Oh its very interesting. Could you provide me more information ?

[email]ann@digitalhardcore.us[/email]

---

### Post by nolan- on 2006-05-26
[QUOTE=JDay]Avidemux is in the marillat repository. It's not perfect by any stretch of the imagination, but it's the best we've got right now. Also, I think virtualdub is supposed to run well under wine, I believe winetools has a wizard or something for installing it.[/QUOTE]


Got it installed now, works a treat!

Cheers :-D 

NoL

---

