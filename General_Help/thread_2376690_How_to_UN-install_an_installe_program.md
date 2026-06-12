---
title: "How to UN-install an installe program?"
date: 2017-11-04
forum: General Help
---

### Post by sterator on 2017-11-04
Right after I set up my Ubuntu install, I installed (through the terminal) Scribus. Then I learned of the Scribus Daily build and have been using and updating that ever since.

Is there I can un-install Scribus (not the daily build)?

if so, how can I do that without harming Scribus Daily Build?

Thank you!

---

### Post by vasa1 on 2017-11-05
What does```
apt policy scribus
```show you?

---

### Post by sterator on 2017-11-05
It shows this:

scribus:
  Installed: 1.4.6+dfsg-4
  Candidate: 1.4.6+dfsg-4
  Version table:
 *** 1.4.6+dfsg-4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by vasa1 on 2017-11-05
How did you install the daily build? Did you use the system tools (apt, dpkg) or did you unpack an archive?

---

### Post by sterator on 2017-11-05
Honestly, I don't recall! I first installed "regular" scribus, then learned that I couldn't opened a Scribus file created on my Mac, with a more recent version of Scribus...but that the "Daily build" was even more recent than what I had on my Mac, so I installed that.

I'm fairly new to Linux, and I only know about the apt get install command in terminal in terms of how to install software, so I'm pretty sure that's how I installed both Scribuses.

---

### Post by vasa1 on 2017-11-05
How do you launch the daily build?

---

### Post by sterator on 2017-11-05
I hit the cmd key - apple keyboard - which brings up a window top left of the screen..you can begin typing the name of the desired application..I type "s-c-r-i" and then I get to choose between Daily build and regular

---

### Post by vasa1 on 2017-11-05
What do you see when you run the following **simulation** command?```
apt-get purge -s scribus*
``` remembering to include the "-s" and the "*". There's _no need_ for *sudo* because this is just a simulation.

---

### Post by Impavidus on 2017-11-05
It seems there's an active PPA available for scribus. If you install that, you can install the daily build (or a more stable but recent 1.5 version) the regular way from the repositories. First uninstall the normal 1.4 version and the non-repository daily build, then install from the PPA. It may also be possible to have two versions of scribus installed side-by-side. If the package manager allows it, it should be fine.

Just to check if you installed already via PPA, run this command:```
apt policy scribus*
```The more recent versions of scribus from the PPA are called scribus-ng and scribus-trunk.

[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)
[https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

---

### Post by dragonfly41 on 2017-11-05
I had overlooked Scribus daily build when I migrated from 14.04 to 16.04.

I've just installed it on 16.04 using instructions here ...

[https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

```
sudo add-apt-repository ppa:scribus/ppa
sudo apt-get update
sudo apt-get install scribus-trunk
```


scribus: current 1.4.x branch
scribus-ng: current 1.5.x branch
scribus-trunk: whatever inside the current svn repository, built daily.
scribus-trunk is not updated anymore in 14.04 LTS Trusty Tahr (and 14.10, 15.04 and 15.10) due to a too old Qt, please upgrade your system to a newer Ubuntu release (suggested: 16.04 LTS Xenial Xerus).

---

### Post by vasa1 on 2017-11-06
> **Impavidus said:**
> ... run this command:```
apt policy scribus*
```...
That what I should have suggested instead of ```
apt policy scribus
```

---

