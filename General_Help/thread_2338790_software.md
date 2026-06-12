---
title: "software"
date: 2016-10-01
forum: General Help
---

### Post by windowsfree on 2016-10-01
I cant get software list to load.  Any suggestions?

[ATTACH=CONFIG]271458[/ATTACH][ATTACH=CONFIG]271459[/ATTACH]

---

### Post by bearlake on 2016-10-01
Hi, Which version of Xubuntu are you using?

Have you tried to update yet?

```
sudo apt-get update

sudo apt-get upgrade
```

and have you tried synaptic?

```
sudo apt-get  update


 sudo apt-get install synaptic

```

Please post back any errors using CODE tags.

---

### Post by ajgreeny on 2016-10-02
The current software-centre, or whatever it is called now, seems to have problems at the moment, so you shouldignore that for now, and as mentioned by bearlake, I would also recommend that you install and use synaptic.  It was the default package manager when I started with Ubuntu 11 years ago and in my opinion is still the best and most flexible.

The only packages not available from synaptic are the ones that you can purchase at a cost from the software centre but that may not worry you anyway.

See
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453)
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)
and several other bugs posted.

---

### Post by windowsfree on 2016-10-04
I used Synaptic and that works.  Thank you.

---

