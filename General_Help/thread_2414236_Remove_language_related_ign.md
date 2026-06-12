---
title: "Remove language related ign"
date: 2019-03-07
forum: General Help
---

### Post by raleigh3 on 2019-03-07
Is this safe and useful?
 ```
[B]
6. Remove language related ign from apt-get update:[/B]

 Have you ever noticed the output of sudo apt-get update? There are three kinds of lines in it, **hit** , **ign** and **get** . You can read their meaning [here 2]("http://ubuntuforums.org/showthread.php?t=231300").  If you look at IGN lines, you will find that most of them are related  to language translation. If you use all the applications, packages in  English, there is absolutely no need for a translation of package  database from English to English.
 If you suppress this language related updates from apt-get, it will  slightly increase the apt-get update speed. To do that, open the  following file:
 sudo gedit /etc/apt/apt.conf.d/00aptitude
 And add the following line at the end of this file:
 Acquire::Languages "none";
```

---

