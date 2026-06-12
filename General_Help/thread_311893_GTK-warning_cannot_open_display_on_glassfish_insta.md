---
title: "GTK-warning cannot open display on glassfish install"
date: 2006-12-03
forum: General Help
---

### Post by spectre_25gt on 2006-12-03
I'm trying to get Glassfish up and running. I downloaded the installer jar. I ran it the first time and it did everything it was supposed to and created the directory structure. I then went to run the setup.xml file through ant, but realized I hadn't gotten it installed yet. I did a quick "sudo apt-get install ant" which told me that there were a ton of dependencies including some GTK packages. I thought this was a bit odd, but I wasn't going to get it installed without them, so I let them install. 

I then ran the setup.xml through Ant, but I did it in the wrong directory and screwed everything up. So, I deleted the directory structure and went to start over. Unfortunately, now when I run the glassfish jar, I'm getting "GTK-warning cannot open display". I'm sure that it has something to do with me installing GTK. Maybe the jar is looking to see if it's installed and trying to launch a GUI installer if it is? Is there any way I might be able to tell this that I'm just running CLI? I'd be perfectly happy with getting rid of the GTK packages as well as I will never be running X on this machine.

---

### Post by finferflu on 2006-12-03
It looks to me one of those errors displayed when I'm trying to open a GUI application as root user... Are you sure you tried to open it as a normal user?

---

### Post by spectre_25gt on 2006-12-03
Yes. Actually I managed to solve the problem. Apparently, when I did my Ant install, it switched me over to the GNU version of Java. I removed Ant and the GTK packages and corrected the symlink. Now everything is working fine.

---

