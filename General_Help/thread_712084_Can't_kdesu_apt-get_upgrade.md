---
title: "Can't kdesu apt-get upgrade?"
date: 2008-03-01
forum: General Help
---

### Post by Dojan5 on 2008-03-01
This is bugging me..
I am trying to upgrade since there are some outdated packages that need to be upgraded.
So, when i run ```
kdesu apt-get upgrade
```
It says ```
The package KoolDock needs to be reinstalled, but i cant find any archives for that.
```
First i thought it was a joke. My computer never talked about itself as an "i"
Anywho, this error is appearing in GNOME too.
I cant use Add/Remove programs and neiter can i use Synaptic or Adept...
/
Joel

---

### Post by Dojan5 on 2008-03-01
And im using KDE 4.something (How do i know what KDE verision i have???)

---

### Post by bukwirm on 2008-03-01
You could try removing the package which is giving you trouble (KoolDock, in this case) then reinstalling it.
WARNING: This may break something else.

---

### Post by Dojan5 on 2008-03-01
I know i could try to remove it...
But how do i do that?
I tried ```
sudo rm kooldock
```
And that didnt work...
Whats the proper command?

---

### Post by Dojan5 on 2008-03-01
Nothing works :'(
Plus, if i cant remove that i WONT BE ABLE TO INSTALL MORE PROGRAMS!!!
So please help.

---

### Post by sumguy231 on 2008-03-01
The proper command is:
```
sudo apt-get remove kooldock
```
P.S. It looks like it worked anyway, but kdesu is meant to be used for graphical progrmas, and it would probably be more convenient to use regular sudo for terminal programs like apt-get.

---

### Post by Dojan5 on 2008-03-01
I dont think it ever got properly installed...
Cause i get the error: "The package Kooldock needs to be reinstalled, but i cant find any archive for that."
And yes i ran sudo apt-get remove kooldock...

---

### Post by Dojan5 on 2008-03-01
I got an idea...
It is called ```
sudo apt-get install -f
```
I doubt it will work...
But, worth a shot!

---

### Post by Dojan5 on 2008-03-01
HA!
It didnt work...
Wanna know why?
Well.
```
The package kooldock needs to be reinstalled, but i cant find any archives for that.
```
PLEEEEEEEEEEAASEEEE HELP!

---

### Post by Dojan5 on 2008-03-01
Note to future:
> **stego_s_aurus said:**
> **To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.**

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
The post can be found here:
[http://ubuntuforums.org/newreply.php?do=newreply&p=3297507](http://ubuntuforums.org/newreply.php?do=newreply&p=3297507)

---

