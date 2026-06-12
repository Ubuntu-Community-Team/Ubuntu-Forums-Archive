---
title: "Rythym Box wont play music"
date: 2005-06-29
forum: General Help
---

### Post by jetan11000 on 2005-06-29
i try to play mp3s but rythym box wont play them. i dont know y. i only new to linux, can someone pls help..........
thx

---

### Post by phen on 2005-06-29
Hello!

You have to install some extra codecs and gstreamer plugins.

please take a look at this page, where all your questions regarding mediaplayers etc are answered:

[www.ubuntuguide.org](www.ubuntuguide.org)

and especially:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)


cheers,#

kai

---

### Post by arnieboy on 2005-06-29
from terminal do a:
sudo apt-get install gstreamer0.8-mad 

before that make sure u have the backports enabled. 
this shd make ur rhythmbox start playing mp3's

---

### Post by danubuntu on 2005-07-05
How do you enable back ports? I tried to apt get gstreamer mad and I got this error message:

E: Couldn't find package gstreamer0.8-mad

---

