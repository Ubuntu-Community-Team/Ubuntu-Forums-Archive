---
title: "Install vs Repository"
date: 2018-08-07
forum: General Help
---

### Post by sardonic2 on 2018-08-07
Hi!
To be franks I did not grasp when installing a program the difference between the Install and Repository! Let me give you an example:
I want to install ffmpeg and from what I see around the internet there are different ways to accomplish this. For example:

sudo apt install ffmpeg or sudo add-apt-repository ppa:jonathonf/ffmpeg-3

So basically what is the difference between this two solutions?
Thank you in advance for your great enlightenment.

---

### Post by Holger_Gehrke on 2018-08-07
A repository is a place on the net where packages for installation are kept. It's basically a website with a fixed structure. The second of the two commands you've given adds a new repository to the list of repositories your package manager knows about. Theis command will not install anything, it just tells the package manager about a new source of packages. The first of the two commands installs the newest version of the software the package manager can find in the repositories it knows about.

PPAs (personal package archives) like ppa:jonathonf/ffmpeg-3 are a way to get packages that are newer than the ones in the official repositories. With a few exceptions the versions of software in the official repositories stay fixed for the whole lifetime of a Ubuntu release, updates only contain bug fixes.

Holger

---

### Post by sardonic2 on 2018-08-07
So cool, thank you so much.

---

### Post by Impavidus on 2018-08-08
It's recommended to always use the official Ubuntu repositories, unless you really need a more recent version of the software. PPAs are known to cause problems sometimes and it's often hard to say whether one PPA is reliable or not.

---

### Post by sardonic2 on 2018-08-09
So as an example what procedure would you use to install ffmpeg? There are so many ways out there...

---

### Post by oldos2er on 2018-08-09
```
sudo apt install ffmpeg
```

---

### Post by sardonic2 on 2018-08-09
Thanks I'll do that and for all.

---

