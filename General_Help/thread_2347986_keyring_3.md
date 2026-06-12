---
title: "keyring 3"
date: 2016-12-30
forum: General Help
---

### Post by pete1977x on 2016-12-30
anyone else on 14.04  having to click on keyring pop up 3 times in a row every time they open a browser like Opera..??

---

### Post by #&amp;thj^% on 2016-12-30
My fix for this on 14.04 was to install seahorse:

```
sudo apt-get install seahorse
```
More Information here: [http://askubuntu.com/questions/184266/what-is-unlock-keyring-and-how-do-i-get-rid-of-it](http://askubuntu.com/questions/184266/what-is-unlock-keyring-and-how-do-i-get-rid-of-it)
Regards

---

### Post by pete1977x on 2016-12-31
why was  that a fix and what will it replace??

---

### Post by #&amp;thj^% on 2016-12-31
It was a fix...because it stopped the  annoying keyring pop-up.
This from "man seahorse"
> DESCRIPTION
       Seahorse  is  a  front  end for GnuPG - the Gnu Privacy Guard program -
       that integrates to the GNOME desktop. It is a tool for secure  communi&#8208;
       cations  and  data storage.  Data encryption and digital signature cre&#8208;
       ation can easily be performed through a GUI and Key  Management  opera&#8208;
       tions can easily be carried out through an intuitive interface.
Did you bother to read the link I provided.
It dose not replace anything..but rather a added easier method in dealing with keys.
Are you using Auto-Login?
More reading and information: [https://www.lifewire.com/guide-to-seahorse-tool-2196541](https://www.lifewire.com/guide-to-seahorse-tool-2196541)
 [http://forums.fedoraforum.org/showthread.php?t=293104](http://forums.fedoraforum.org/showthread.php?t=293104)

[http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot](http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot)

[http://mensfeld.pl/2014/09/ubuntu-14-04-gnome-keyring-seahorse-auto-unlock-when-auto-login/](http://mensfeld.pl/2014/09/ubuntu-14-04-gnome-keyring-seahorse-auto-unlock-when-auto-login/)

You are Free to do what you want of course.
Cheers

---

### Post by pete1977x on 2017-01-02
I will try to disable auto login for awhile and then enable it again. Canonical knows about this bug.

---

