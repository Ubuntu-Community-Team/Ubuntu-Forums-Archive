---
title: "[SOLVED] I Screwed Up OpenOffice"
date: 2008-02-01
forum: General Help
---

### Post by alsamman on 2008-02-01
I was tired of OO presentation not running smoothly in slide shows so someone advised me to install OO from the website, I got the tar.gz and decided to change it to a deb using alien, i installed it once it was done but i could not find oo anywhere so I then decided to install it in synaptic. Ever since i did this, oo has been really weird, when I open presentation or word processor, it doesnt work with compiz anymore and the exit, minimze, and maximize bar is gone and oo overlaps my panels and stuff so i can minimize it from there and when i go to something like Format>Paragraph, the window goes full screen. I tried reinstalling oo but it didnt fix anything, how can i just erase what i did with alien and start over?

---

### Post by Kingsley on 2008-02-02
If I were you, I'd uninstall OO.o,  delete /usr/lib/openoffice.org contents, and reinstall the suite again through Ubuntu's repositories.

---

### Post by alsamman on 2008-02-02
thats what i want to do i just want to make sure that every trace of oo is gone

---

### Post by alsamman on 2008-02-02
i uninstalled oo in synaptic as well as removed my usr/lib/openoffice folder but when i reinstalled i still get it all messed up:(:(:(

---

### Post by Kingsley on 2008-02-02
I forgot about ~/.openoffice.org2.0/

Deleting that and reinstalling OO.o might solve the problem. Note that the name might be different for you. I use Fedora.

---

### Post by alsamman on 2008-02-02
alright now i just made it even worse:( i decided to search for all openoffice files and delete them all and then reinstall it, oo still gets the weird behaviour and now the oo packages are kinda broken
```

kenan@kenan-desktop:~$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openoffice.org is already the newest version.
The following packages were automatically installed and are no longer required:
  guile-1.8 lilypond-data texlive-base texlive texlive-fonts-recommended
  texlive-common texlive-base-bin guile-1.8-libs tetex-bin blt
  texlive-latex-recommended texlive-latex-base texlive-doc-base tex-common
  texinfo
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up openoffice.org-common (1:2.3.0-1ubuntu5.3) ...
/var/lib/dpkg/info/openoffice.org-common.postinst: 94: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

the dictionaries are all gone and how the hell can i fix all these damn problems

---

### Post by alsamman on 2008-02-02
alright good news, i got the whole gui thing fixed so it doesnt go fullscreen and all. Im still getting the errors though when i try to reinstall openoffice as shown in the other post so how do i fix that

---

### Post by alsamman on 2008-02-02
bump

---

### Post by c0met on 2008-02-02
I don't know much about OOo, but looking at what you pasted, it requires a lot of java related files. Have you thought about uninstalling and then reinstalling java before reinstalling OOo?

---

### Post by raptir on 2008-02-02
Just out of curiosity, why didn't you just download the DEBs off of OO.o's site? I just installed through the DEBs today and I have it working great... Sorry, I can't really help on uninstalling it though.

---

### Post by alsamman on 2008-02-02
> **raptir said:**
> Just out of curiosity, why didn't you just download the DEBs off of OO.o's site? I just installed through the DEBs today and I have it working great... Sorry, I can't really help on uninstalling it though.
lol where the hell is the deb file i can only find the tar.gz

---

### Post by alsamman on 2008-02-02
ahh nevermind i was clicking the JRE link before i didnt notice the deb lol

---

### Post by Hagar Delest on 2008-02-03
Beware that to install the official OOo version (from website), you need to remove any OOo package coming from Ubuntu. See that thread: install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

