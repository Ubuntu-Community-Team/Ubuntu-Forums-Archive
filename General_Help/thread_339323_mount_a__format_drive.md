---
title: "mount a ?? format drive"
date: 2007-01-15
forum: General Help
---

### Post by RavenndudE on 2007-01-15
I just formatted and installed Edgy. I used to have Dapper.

I have two hard drives, one has Windows and Edgy on it, the other has my music and some other stuff on it.

When I formatted I unplugged the power to the hard drive with my music on it so that I wouldn't accidentally erase it all. After the installation of Edgy was complete I shut down and plugged my hard drive back in. Now I'm having a hard time mounting this drive. I can't remember what format the drive is in. I did this back in August, so I'm not too sure about it. 

I know I could access it in Windows ... but I also remember installing something on windows that let me view my linux partitions and edit them if the permissions were set right.

Anyways ... How can I go about getting info on this drive and mounting it correctly?

---

### Post by aysiu on 2007-01-15
```
sudo aptitude update
sudo aptitude install gparted gksu
gksudo gparted
``` That should give you an idea of what format the drive is, and allow you to reformat it if you don't like the current format.

More details here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by RavenndudE on 2007-01-15
That's a nice tool =)

one problem though...

[[IMG]http://img384.imageshack.us/img384/2561/screenshotdevhddgpartediy4.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotdevhddgpartediy4.png)

Now I'm confused...

---

### Post by aysiu on 2007-01-15
Looks like you might have to reformat it. Can you right-click and delete the partition and the right-click and create a new one?

---

