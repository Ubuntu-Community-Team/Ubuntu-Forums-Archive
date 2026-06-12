---
title: "What Does &quot;-y&quot; Mean?"
date: 2013-11-11
forum: General Help
---

### Post by cessanfrancisco on 2013-11-11
Hi,

I am a noob with the command line so please bear with me.  

I just upgraded GIMP to the latest version (2.8.8).  I added the GIMP PPA (since 2.8.8 is not available in the Ubuntu repository) and installed GIMP via the command line using:

sudo apt-get install -y gimp

As instructed at ubuntuhandbook.org.

So, what does the "-y" mean, in the above command?  Why wouldn't I just use:

sudo apt-get install gimp

And if I did use that command, would Ubuntu have tried to install from both the GIMP and Ubuntu repositories?

Thanks in advance!

---

### Post by bapoumba on 2013-11-11
```
-y, --yes, --assume-yes
Automatic yes to prompts. Assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package or removing an essential package, occurs then apt-get will abort.
```
It will force to answer yes to any prompt apt-get might give you during the install.

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by oldos2er on 2013-11-11
From ```
man apt-get
``` ```
-y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and run
           non-interactively. If an undesirable situation, such as changing a held
           package, trying to install a unauthenticated package or removing an essential
           package occurs then apt-get will abort.
``` If you know exactly what you're doing, feel free to use -y. Personally I like having the option to abort, so I seldom use it.

> And if I did use that command, would Ubuntu have tried to install from both the GIMP and Ubuntu repositories? If you have the gimp PPA (I'm assuming there is one, haven't looked), apt-get will install the most recent version of gimp from it.

---

### Post by cessanfrancisco on 2013-11-11
Thanks!

So how does Ubuntu know to download and install 2.8.8 from the GIMP PPA and not 2.8.6 from the Ubuntu PPA?

Nevermind:  this was answered by oldos2er while I was writing and posting...

---

### Post by oldos2er on 2013-11-11
As far as I know, APT will always install the most recent version it can find, as defined by your sources.list and any PPAs you have in /etc/apt/sources.list.d/

---

### Post by cessanfrancisco on 2013-11-11
Thanks!  I really appreciate the help!

---

### Post by oldos2er on 2013-11-11
Welcome!

---

