---
title: "why does &quot;apt-get * install&quot; require CDROM?"
date: 2006-07-08
forum: General Help
---

### Post by duderonomy on 2006-07-08
I had a friend visit who had not seen a CD-ROM toasted in a microwave 
so I no longer have my CD-ROM. Is the ubuntu-server (dapper) leaving 
me hanging? Must I burn another CD to get sshd installed? What's the 
logic here? When I run apt-get install sshd I am aksed to insert my CD-ROM. 
WTF...Is this Windoze? ;-)

Thx!
D

---

### Post by Titus A Duxass on 2006-07-08
Edit your sources.list and hash out the line (usually the first line) that refers to the CD.

---

### Post by duderonomy on 2006-07-08
Thanks much! Will try.

:-)

---

### Post by atoponce on 2006-07-08
Calm down.  No, this is not Windows.  It is asking for your CDROM, because it is a repository of software for your system.  Just edit your /etc/apt/sources.list file, and comment or delete out the first line, then do:

```
sudo aptitude update
```

Yes, you should use aptitude instead of apt-get every time you want to install software.

---

### Post by duderonomy on 2006-07-08
Hey, thanks for the explicit guidance to use the other app, aptitude. 

As usual... unexpected behavior turns out to be a cool feature. Thanks for the 
hint about the apt config! After that installing sshd went really fast. 
[I skipped the obligatory Debian phase in the 90's so pls excuse my ignorance.] :) 

If anyone is aware of the best and notable "primers" that talk about the debian 
package management system, or topics that are useful for Ubuntu then feel free 
to post some links. Maybe, too, there are some useful threads within these forums 
that would be considered **must reads** for users coming from other GNU/Linux
distributions. 

Cheers!
D

---

### Post by infoseeker on 2006-07-08
What exactly is the difference between > sudo aptitude update and > sudo apt-get update
I have ALWAYS used 'apt-get'. And does it make a difference doing an update from Gnome (Synaptic) and 'Adept' (KDE) ?

---

### Post by yopnono on 2006-07-08
> **infoseeker said:**
> What exactly is the difference between  and 
I have ALWAYS used 'apt-get'. And does it make a difference doing an update from Gnome (Synaptic) and 'Adept' (KDE) ?

Read this link: [http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

---

