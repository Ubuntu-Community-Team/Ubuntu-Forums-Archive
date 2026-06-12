---
title: "What happened to sudo dpkg-reconfigure -a?"
date: 2015-04-16
forum: General Help
---

### Post by tehtotalpwnage on 2015-04-16
Hi there!

So I kind of screwed up my Ubuntu install. I've been trying to get NVIDIA drivers to not lock up my system to no avail, and I've somehow managed to cause Ubuntu's Unity interface to flat out not load on startup. I did read on the internet that if I have issues with my install, I could fix them with
```
sudo dpkg-reconfigure -a
```
However, in the current version of Ubuntu, or at least the version I'm stranded at (15.04 development branch), there is no such -a argument for whatever reason. What can I do here?

---

### Post by dino99 on 2015-04-17
its easy to check the manpage  [http://manpages.ubuntu.com/manpages/saucy/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/saucy/man1/dpkg.1.html)

---

### Post by CantankRus on 2015-04-17
The man page for dpkg-reconfigure in utopic seems not to include the **-a** option ... [http://manpages.ubuntu.com/manpages/utopic/en/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/utopic/en/man8/dpkg-reconfigure.8.html)
dpkg-reconfigure in trusty does... [http://manpages.ubuntu.com/manpages/trusty/en/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/dpkg-reconfigure.8.html)
You could try to purge nvidia drivers and return to the nouveau drivers.
From the greeter hit ctrl+alt+F1 and login.
Run....
```
sudo apt-get purge nvidia*
```

then 
```
sudo reboot
```

---

### Post by mc4man on 2015-04-17
stopped working some time ago - 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=721329#15](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=721329#15)

---

### Post by oldos2er on 2015-04-17
Are you thinking of ```
sudo dpkg --configure -a
``` ? As was mentioned I don't think dpkg-reconfigure ever had an -a option.

---

### Post by tehtotalpwnage on 2015-04-17
> **CantankRus said:**
> The man page for dpkg-reconfigure in utopic seems not to include the **-a** option ... [http://manpages.ubuntu.com/manpages/utopic/en/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/utopic/en/man8/dpkg-reconfigure.8.html)
dpkg-reconfigure in trusty does... [http://manpages.ubuntu.com/manpages/trusty/en/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/dpkg-reconfigure.8.html)

Well this is strange. Are there any changelogs that potentially indicate that the -a option was removed, or is there a bug filed for this?

I think I'll save my NVIDIA driver issues for a separate thread though, considering that my system is magically stable again ;)

---

### Post by mc4man on 2015-04-17
> **tehtotalpwnage said:**
> Well this is strange. Are there any changelogs that potentially indicate that the -a option was removed, or is there a bug filed for this?

I think I'll save my NVIDIA driver issues for a separate thread though, considering that my system is magically stable again ;)

In the link I gave you - 

> Changes: 
 debconf (1.5.52) unstable; urgency=low
 .
   [Joey Hess]
   * Remove dpkg-reconfigure -a, which existed only to accumulate bug
     reports about bugs in other packages.
     Closes: #721329, #664825, #558262, #617618, #707987



---

### Post by tehtotalpwnage on 2015-04-18
> **mc4man said:**
> In the link I gave you -
Well, great, doesn't exist anymore. Well, thread closed.

---

