---
title: "Software Center shuts down when trying to install something"
date: 2015-02-05
forum: General Help
---

### Post by Kevf on 2015-02-05
Yesterday I was installing Dolphin (file manager) but the installation failed (progression balk was showing no progress after more than an hour). I rebooted my laptop but now software center won't install anything at all. When I chose 'install'  the screen freezes for a few seconds and software center closes. Any help is greatly appreciated.

---

### Post by Bashing-om on 2015-02-05
Kevf; Hi !

1st is to check the package management system functionality.
Open a terminal and execute terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C
```

If there are any errors, post back those complete outputs - Between Code Tags, please .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we know what condition
[INDENT][INDENT][INDENT]the condition is in
[/INDENT][/INDENT][/INDENT]

---

### Post by Kevf on 2015-02-06
No need, cause everything worked fine after your advice. Terminal told me to autoremove some packages as well. 

What does -f install do?

Anyway, tnx!

---

### Post by Bashing-om on 2015-02-06
Kevf; Great !

Pleased it has all worked out.

The ' -f install' of apt-get directs the package manager to (F)ix all broken packaging that it can.

If this matter is concluded at this time ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Kevf on 2015-02-06
Done :)

---

