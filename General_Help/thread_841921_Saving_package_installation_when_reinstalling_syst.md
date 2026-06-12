---
title: "Saving package installation when reinstalling system"
date: 2008-06-26
forum: General Help
---

### Post by ceclauson on 2008-06-26
Hello!

I'm currently thinking to reinstall Ubuntu on my system.  The reasons include upgrading to Hardy (I'm running Gutsy), and the fact that when I boot up now,  I get a message about a difficulty initializing Gnome, and I get into what I think is an X desktop.

However, I'm daunted by the prospect of reinstalling all those packages.  I must have typed "sudo apt-get install xxx" a half a billion times. In the Synaptic Package Manager window, there's an option that says "Generate package download script" which I thought might bail me out, but when I chose this, and entered a filename and destination, the script it generated was empty -- it just had the line "#!/bin/sh" at the top and nothing else.

Is there any way to save the packages I have now, or some list thereof, so that I can easily reinstall/download them when I redo my system?  Any insight anyone might have would be appreciated.

Thanks,
Cooper

---

### Post by ryanhaigh on 2008-06-26
The following should give you a list of all installed packages, note that these will include the packages initially installed with the system as well as your dependancies.

```

dpkg --get-selections > isntalled.txt

```

This thread may also be useful to you:
[http://www.linuxquestions.org/questions/debian-26/aptitude-how-to-get-a-list-of-all-installed-packages-458119/](http://www.linuxquestions.org/questions/debian-26/aptitude-how-to-get-a-list-of-all-installed-packages-458119/)

---

### Post by ceclauson on 2008-06-29
I clicked the link you posted, and it looks like what they describe is pretty much exactly what I'm trying to do.  Thanks so much!

-Cooper

---

### Post by cariboo on 2008-06-29
Have a look here:

[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

Look under the heading: Automated software installation or reproducing an existing (model) configuration

Jim

---

