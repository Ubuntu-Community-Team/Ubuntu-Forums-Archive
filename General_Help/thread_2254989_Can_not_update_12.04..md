---
title: "Can not update 12.04."
date: 2014-12-01
forum: General Help
---

### Post by Ken Steele on 2014-12-01
I am trying ot update Ubuntu 12.04. I get the following error "E: Type 'b-src' is not known on line 2 in source list /etc/apt/sources.list.d/atareao-atareao-precise.list
E: The list of sources could not be read.
  In gedit my source list is blank.

---

### Post by carlwsnyder on 2014-12-01
1) Is this a new problem, or has this been the case since installation?
2) Are you updating from a terminal, from Synaptic, or from Ubuntu Software Updater program?
3) Did you attempt changing your update mirror?

---

### Post by ajgreeny on 2014-12-01
I suggest you remove that** /etc/apt/sources.list.d/atareao-atareao-precise.list** file or perhaps, rename it for the moment, then try adding again the ppa with ```
sudo add-apt-repository ppa:atareao/atareao
```as there seems to be a problem with your current sources.list.d file for that repository.

---

### Post by Ken Steele on 2014-12-01
[**[COLOR=#000000]carlwsnyder[/COLOR]**]("http://ubuntuforums.org/member.php?u=1847630")   This is a new problem. I have tried updating from a terminal, and from Update Manager. I have tried changing the update mi[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")rror.
  
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")    I was unable to rename or delete the folder.

---

### Post by Ken Steele on 2014-12-01
[**[COLOR=#000000]carlwsnyder[/COLOR]**]("http://ubuntuforums.org/member.php?u=1847630")   This is a new problem. I have tried updating from a terminal, and from Update Manager. I have tried changing the update mirror.
  
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")    I was unable to rename or delete the folder.

---

### Post by Ken Steele on 2014-12-01
Thanks for the help. I fixed it by deleting the 2nd line in the "**/etc/apt/sources.list.d/atareao-atareao-precise.list" file.**

---

