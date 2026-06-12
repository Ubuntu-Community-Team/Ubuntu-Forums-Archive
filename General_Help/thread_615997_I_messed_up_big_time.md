---
title: "I messed up big time"
date: 2007-11-17
forum: General Help
---

### Post by fix3r on 2007-11-17
Well, I was at a website, searching the best way to install a web server on ubunut and one person said this:

I prefer using the 'tasksel' program which installs a prepackaged list of application
the commands would be

> sudo tasksel install lamp-server
> sudo apt-get install phpmyadmin

Well I did the first thing:

tasksel install lamp-server and it seemed like it installed. Me being not so linux friendly yet, I didn't know how to run it so i tryed removing it. This is what was in my terminal: It all went to fast I don't know what happened. I freaked out an i typed ctrl+z ctrl+C or something like that to get out of the removing process. What happened and how do I get back what I lost if I lost anything?

[http://pastebin.com/m5979a375](http://pastebin.com/m5979a375)

Now when i try to update it gives me error and I don't even know what I removed ;\

---

### Post by JasonF on 2007-11-17
Try running sudo dpkg --configure -a to fix the packages on your system, then sudo apt-get install ubuntu-desktop which will reinstall all of the default ubuntu packages.  You may also need to reinstall some of the packages you added yourself (through synaptic or apt-get or whatever)..

---

### Post by fix3r on 2007-11-17
is that it? I did that now just afraid to restart my computer to see what i messed up

---

### Post by JasonF on 2007-11-17
Looking at the list of packages it removed before you killed it, I don't think you should have a problem booting to at least a console.  If reinstalling ubuntu-desktop was successful you shouldn't have any problems with restarting. The packages were not purged, so any configuration should still be there after they are reinstalled.

---

### Post by fix3r on 2007-11-17
nice thank you, good thing i quite out when i did before to much stuff got removed lol

---

