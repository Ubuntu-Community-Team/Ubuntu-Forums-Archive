---
title: "Adobe on Ubuntu"
date: 2007-01-15
forum: General Help
---

### Post by imnocowboy on 2007-01-15
How do I properly install Adobe 7. I have it downloaded and extracted but when I attempt to run it a message appears saying there is no PATH???  What now?  Or , What have I missed.  I am a totally new user.  Thanks

---

### Post by Sef on 2007-01-15
Easiest way to install Adobe 7 is this way:  Applications > Add/Remove > search > type in Adobe > click on the box next to it > click install > click again > just wait for instructions.

You will need to open multiverse (and universe), so read [Psychocat's]("http://www.psychocats.net/ubuntu/sources") sources and [Psychocat's]("http://www.psychocats.net/ubuntu/installingsoftware") installing software.

---

### Post by confused57 on 2007-01-15
> **imnocowboy said:**
> How do I properly install Adobe 7. I have it downloaded and extracted but when I attempt to run it a message appears saying there is no PATH???  What now?  Or , What have I missed.  I am a totally new user.  Thanks

You could also use Synaptic Package Manager(System---Administration) to install the Ubuntu version...in Search, type **acroread**.

If you want to try to install the version you downloaded, you'd need to open a terminal(Applications---Accessories---Terminal) & change to the directory you downloaded, probably to the Desktop:
```
cd Desktop/name of extracted directory
```

then

```
sudo ./INSTALL
```

Before you do any of this you might want to open the Directory that was created when you extracted the file you downloaded and read the "README" file for instructions on installing. It'll give you details of where Adobe will be installed(/usr/local/Adobe/Acrobat7.0/bin/acroread)

You might want to look into Automatix2 for installing programs & packages:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

It "automates" installing such things as flashplayer, media players, codecs, adobe acrobat reader, firefox plugins, etc.
I've never had any problems using Automatix and you can get your system "up-to-speed" quickly...

---

