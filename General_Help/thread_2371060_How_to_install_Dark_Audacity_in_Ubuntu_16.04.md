---
title: "How to install Dark Audacity in Ubuntu 16.04"
date: 2017-09-10
forum: General Help
---

### Post by RobGoss on 2017-09-10
Hello everyone, I was wondering how can I install **Dark Audacity** in Ubuntu, I was able to do it on a Windows machine with out a problem but I prefer it on Ubuntu, seeing I use Ubuntu 99% of the time. This is the website but I don't see any download for Linux. thanks so much for any help

---

### Post by Perfect Storm on 2017-09-10
Have you tried the source code? [https://github.com/JamesCrook/audacity/tree/darkaudacity](https://github.com/JamesCrook/audacity/tree/darkaudacity)

Download as .zip, then unpack it.
```
cd <path>
./configure
make
sudo make install
```

You may need some -dev packages of different libs to make it ./configure

```
sudo apt install libwxgtk3.0-dev portaudio19-dev libogg-dev
```
In line 130 is the full dependency list: [https://github.com/JamesCrook/audacity/blob/darkaudacity/README.txt](https://github.com/JamesCrook/audacity/blob/darkaudacity/README.txt)

---

### Post by mc4man on 2017-09-10
I use the audacity team[ ppa]("https://launchpad.net/~audacity-team/+archive/ubuntu/daily") so the dark theme is built-in. To note it gets builds or build attempts every few days or so, whether there is a stable ppa I don't know. You'd want 2.2.x

---

### Post by RobGoss on 2017-09-10
> **mc4man said:**
> I use the audacity team[ ppa]("https://launchpad.net/~audacity-team/+archive/ubuntu/daily") so the dark theme is built-in. To note it gets builds or build attempts every few days or so, whether there is a stable ppa I don't know. You'd want 2.2.x

Thank you guys for the quick reply I will check out the PPA also, can I just add the PPA and the dark theme will be added? I look on the Audacity page you posted and I don't see** 2.2.x**

---

### Post by mc4man on 2017-09-10
The one thing that bothers me with current 2.2 is that files are opened to fit the interface whereas in 2.1.x the interface (timeline) was adjusted to the file length.
So if your default opening window is lets say 13 sec. then that's all you'll see when opening a file. If the file is less than 13 sec you still get a 13 sec. timeline.

Have asked in the audacity forum about that but posts are moderated so no explain yet..

---

### Post by RobGoss on 2017-09-10
Were is the  2.2  download I don't see it anywhere

Thanks so much

---

### Post by vasa1 on 2017-09-10
> **RobGoss said:**
> Were is the  2.2  download I don't see it anywhere

Thanks so much
[https://github.com/audacity/audacity/releases/tag/Audacity-2.2.0-beta-20170901](https://github.com/audacity/audacity/releases/tag/Audacity-2.2.0-beta-20170901) ???

---

### Post by mc4man on 2017-09-10
> **RobGoss said:**
> Were is the  2.2  download I don't see it anywhere

Thanks so much
If using that ppa just upgrade. The current package version name is 2.1.2+git20170817+r5628+17~ubuntu16.04.1 which equates to 2.2.0-alpha or so..
ctrl+f fits the track, never had to use before so never notices...

If building you'd need to use git clone as 2.2 has not yet released or just  click on the Clone or Download > ..zip

---

