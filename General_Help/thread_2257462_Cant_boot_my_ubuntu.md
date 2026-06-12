---
title: "Cant boot my ubuntu"
date: 2014-12-20
forum: General Help
---

### Post by epraveenns on 2014-12-20
When i tried to open ubuntu, i am getting the following screen (see attachment). What should i do? should i format my ubuntu?

---

### Post by CantankRus on 2014-12-20
Hi,
Helps if you provide more info...
[LIST]
[*]have you been able to login previously?
[*]is it dual boot with windows?
[*]how did you install?
[/LIST]

Post any info you think is relevant to your situation.

---

### Post by Bucky Ball on 2014-12-20
Welcome. Is this a fresh install? Which release? Don't reinstall at this point (unless this is the first time you've booted a fresh install). That is generally a last resort around here. ;)

Please let us know the details requested.

* Beaten to it by CantankRus. What they said. ;)

---

### Post by kowloon2 on 2014-12-20
download boot repair -> [http://sourceforge.net/projects/boot-repair/](http://sourceforge.net/projects/boot-repair/)
procedure -> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by epraveenns on 2014-12-20
ya i have been using ubuntu since a couple of years. 
yes it is dual boot with windows
previously i had ubuntu, windows 7 and linuxmint. Due to some problems, i deleted partition of linux mint. There after i am not even able to access ubuntu too. i am sure that ubuntu and linuxmint are in different partitions and ubuntu partition is safe and untouched

---

### Post by Bucky Ball on 2014-12-20
> **kowloon2 said:**
> download boot repair -> [http://sourceforge.net/projects/boot-repair/](http://sourceforge.net/projects/boot-repair/)
procedure -> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

^^^
This. Boot Repair would be worth a try at this point. Sounds to me like Linux Mint was controlling the grub. If this is the case, when you uninstalled it screwed up grub. Did you install Mint last, after Ubuntu?

Boot Repair creates bootinfoscript output. Take note of the link and post it hear if BR doesn't work. Good luck.

---

### Post by ajgreeny on 2014-12-20
This is a duplicate thread with only half of the needed info; here's the other thread:-
[http://ubuntuforums.org/showthread.php?t=2257462&p=13190657#post13190657](http://ubuntuforums.org/showthread.php?t=2257462&p=13190657#post13190657)
You previously had Mint as well as Ubuntu and Windows, ie three OSs.  I wonder if Mint was managing grub and as you have now removed Mint from the system grub finds no configuration files and goes to the screen you are now seeing.

Boot-Repair will put this right easily.

Please don't post duplicates; it means **you** may miss useful solutions, and **we** may not see the full details of the problem in the first place.

EDIT:
Sorry, I see this has already been merged.

---

