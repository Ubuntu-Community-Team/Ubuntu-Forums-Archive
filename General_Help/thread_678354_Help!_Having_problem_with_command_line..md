---
title: "Help! Having problem with command line."
date: 2008-01-25
forum: General Help
---

### Post by Fangs on 2008-01-25
I just did a clean install of Ubuntu 7.10 Server Edition on another desktop of mine, but it is in command line.  I would rather have it in a desktop view, though.  How do I exit out of the command line and view the desktop?  Thanks for the help!

From,
   Fangs

---

### Post by overdrank on 2008-01-25
> **Fangs said:**
> I just did a clean install of Ubuntu 7.10 Server Edition on another desktop of mine, but it is in command line.  I would rather have it in a desktop view, though.  How do I exit out of the command line and view the desktop?  Thanks for the help!

From,
   Fangs

Hi and the sever is that, command line. You will have to install a desktop ```
sudo aptitude install xubuntu-desktop
or
sudo aptitude install ubuntu-desktop
or
sudo aptitude install kubuntu-desktop
```
Or you may use apt-get instead of aptitude.

---

### Post by Fangs on 2008-01-25
I think that it worked, but I am unsure.  It looked like it installed, yet somewhere in the middle of it said, "Couldn't find any package whose name or description matched "ubuntu-desktop""  How would I view the desktop to see if it worked?  Thanks.

---

### Post by overdrank on 2008-01-25
> **Fangs said:**
> I think that it worked, but I am unsure.  It looked like it installed, yet somewhere in the middle of it said, "Couldn't find any package whose name or description matched "ubuntu-desktop""  How would I view the desktop to see if it worked?  Thanks.

Hi and maybe this will help
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```
According to this link
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by Fangs on 2008-01-25
.

---

### Post by Fangs on 2008-01-25
That computer is not hooked up to internet, unfortunately.  I just tried moving the USB wireless adapter from this one to that, but I could not figure out how to  install the drivers from the flash drive for it.  I tried the other two, but neither of them worked.

---

### Post by Jawnboy on 2008-01-25
If you can it might be easiest for you to download a copy of Ubuntu Desktop Edition  if you don't have network access on the machine in question.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Fangs on 2008-01-28
I am going to install a PCI NIC to be able to access the internet (As long as it installs itself, like it should) and then I will re-install the server edition and try getting the desktop downloaded onto it.  If, for whatever reason this will not work, I shall download the desktop edition and install the server software onto it from there.  I will let you all know how it goes.  I give my thanks to everyone who helped me with this problem.

---

