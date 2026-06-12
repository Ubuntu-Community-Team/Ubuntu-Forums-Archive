---
title: "Gstreamer0.8-faad dependancies"
date: 2005-07-26
forum: General Help
---

### Post by fatum on 2005-07-26
Trying to install Gstreamer0.8-faad so I will be able to play my AAC files through rhythmbox and get a dependancy that says can not be installed. The file that needs to be installed is libfaad2-0. I have tried this through apt-get and the add/remove programs under system in the main menu. Is there something I am missing or another way to give rhythmbox a way to play AAC files? I need to be able to play AAC files being that 95% of my music is in that format. Any help is appreciated thanks in advance.

---

### Post by varunus on 2005-07-26
Have you activated the extra repositories?  (Hoary-backports and hoary-extras, in particular?)  You need them for a lot of codecs.  Try this:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by daigorobr on 2005-07-27
[QUOTE=varunus]Have you activated the extra repositories?  (Hoary-backports and hoary-extras, in particular?)  You need them for a lot of codecs.  Try this:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE]
 You have to add the Marillat repos to get the latest libfaad.
Add this to your /etc/apt/sources.list

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

It helps to uncomment Universe repos and use the Backports, as in [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by fatum on 2005-07-27
I have already added extra's and backport to to sources but I'm going to have to try the third one when I get home. thanks

---

### Post by fatum on 2005-07-27
was able to get libfaad2 to install but now I get another dependancy for libc6 2.3.2.ds1-21 where I have libc6 2.3.2.ds1-20 installed and it claims to be up to date. Any idea what other source I have to put into the list?

---

### Post by daigorobr on 2005-07-27
[QUOTE=fatum]was able to get libfaad2 to install but now I get another dependancy for libc6 2.3.2.ds1-21 where I have libc6 2.3.2.ds1-20 installed and it claims to be up to date. Any idea what other source I have to put into the list?[/QUOTE]
 You can't really upgrade to libc6 21, coz it's crucial to Ubuntu proper work. It seems you are trying to install some non-Ubuntu version. Are you using Synaptic?
If so, go to Package -> Force Version and choose version 0.8.8-0.2~5.04ubp1

---

### Post by fatum on 2005-07-27
Went into Synaptic and Force Version is grayed out for libc6. Is there something I'm missing.

---

### Post by RaymondQE on 2005-07-28
The marillat packages are compiled against a higher version libc6 so it is best to stick with the extras repository.  You should probably downgrade your libfaad2-0 version to the one present in hoary and install the gstreamer0.8-faad package in the extra repository.  Having the marillat repository just adds dependency issues.

---

