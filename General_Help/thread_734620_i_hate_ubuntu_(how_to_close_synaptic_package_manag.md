---
title: "i hate ubuntu (how to close synaptic package manager)"
date: 2008-03-24
forum: General Help
---

### Post by davesec on 2008-03-24
so my latest problem is that i tried to download and install limewire. it froze while installing and i had to do a 'forced quit' or whatever, which is something i seem to have to do dozens of times a day on all sorts of programs, regardless of what they are.

anyway so after the force quit i tried to install another program (frostwire) but it says 'Only one software manager is allowed to run at the same time', which isn't really a great sentence when you think about it, but whatever. So apparently I need to shut down the synaptic package manager. So I open that up and get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So now I don't know what to do, I tried opening Terminer and typing in 'dpkg --configure -a', (you know, "to correct the problem") and it says i need 'superuser' privileges to do that.

I've only had ubuntu for maybe 3 weeks now but I have to force quit everything all the time, certain programs freeze when they load no matter what (open office database program), the music production software is sub par and difficult to navigate, and my computer makes that whirring noise that i think is indicative of it "working hard" about 10x more frequently than it did with windows. also my camera is only recognized/mounted maybe a third of the time and my mp3 player seems to be incompatible.

---

### Post by scragar on 2008-03-24
just put sudo before a command to have root privilages for a short time:
```
sudo dpkg --configure -a
```

a small warning though, this command will take a while(it checks all installed packages against it's listings, and corrects the listings etc).

---

### Post by kerry_s on 2008-03-24
maybe it's time to move to a different distro.
something like pclinuxos> [http://en.wikipedia.org/wiki/PCLinuxOS](http://en.wikipedia.org/wiki/PCLinuxOS)

normally i would recommend debian, but if you can't handle ubuntu, i don't think debian would help.

here's the list in case you want to try others.
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

---

### Post by plunkjunket on 2008-03-28
Thanks sudo dkpg --configue -a work for me too.

---

### Post by randavance on 2008-03-28
In the future I would recomend using frostwire, it tends to be safer, and it's identically the same thing (plus bit torrent support).

I hate synaptic personally, try just opening a shell and typing "sudo apt-get" and then the program to install things. It's the best part of Debian based systems and a cool thing to show off to your poor Window using friends. I wouldn't say to give up right away, we were all lost and confused in the beginning, and breaking your system is all part of the learning process. I keep an icon on my panel that runs the "xkill" command and back up my data personally.

---

