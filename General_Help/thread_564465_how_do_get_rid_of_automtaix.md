---
title: "how do get rid of automtaix"
date: 2007-10-01
forum: General Help
---

### Post by don durito on 2007-10-01
Hi,

i have used automatix now for about 3 years and it worked soomthly. but lately it seemd to be a bit bugy. so  i googled around and found some horror stories about it (like destroying your system). now would like to rid of it. 

but i don't know what will happen to my apps installed with automatix and how will i keep them updated regulary.

thanks in advance

your don

---

### Post by por100pre1 on 2007-10-01
The installed packages will stay in your PC, no problems with that. You can go ahead and uninstall Automatix, just **make a backup of your sources.list first**, just in case Automatix breaks it while removing its repositories:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

---

### Post by strabes on 2007-10-01
[Here's](http://www.psychocats.net/ubuntu/sources#feisty) a sources.list that you should overwrite your sources.list with if automatix messes it up. A lot of stuff automatix does can be done really easily, like with this command: ```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras w32codecs
```

---

### Post by don durito on 2007-10-01
thanks for your quick replys

now i just want to know how i will keep those apps installed by automtix up to date. so fare i have installed:

dvd and audio codecs
falsh plugins
mplayer plugins
java
multimedia codecs

thunderbird 2.0
deluge
kino
read and write ntfs
extra fonds
adobe reader
gtk-record my desktop
google earth

archiviing tools
wine

now i would like to know how will i keep them uptodate cause i won't use the autmatix repos anymore?

will my apps work with the medibuntu repos if i just add the medibuntu repos to my sourecs.list
or do i have to uninstall them all and reinstall it the clean way?

thanks for your quick help

yours don

---

### Post by por100pre1 on 2007-10-01
IMHO, just leave everything like that. To change those packages with the repository ones can get messy.

Just keep in mind that the suggested way to install java, flash, etc. is to open:

```
gksudo software-properties-gtk
```

and then ensure that the main, universe, restricted, and multiverse repositories are enabled.

Once there click the second tab and add this APT line to your repositories:

```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Then close it. Add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository.

Most of those application should then be able to installed with apt-get or Synaptic. This [how to]("http://ubuntuforums.org/showthread.php?t=413625") helps with codecs.

---

### Post by don durito on 2007-10-01
hi,

thanks alot for your help guys/girls.
i have now uninstalled automatix2 with```
sudo apt-get remove automatix2
``` hope that this did the job (or do i have to purge remove automatix?);

anyway for everyone who uninstalls automatix watch out cause it defently destroyed my sourecs.list.
so just be sure and back it up.

after this i added the mediubuntu repos to my sources.list. and after a short ```
sudo apt-get update
```  it updated my acroread. which means i works like charm and my apps and codecs installed with automatix will be updated :lolflag:

thanks again 
yours don

---

