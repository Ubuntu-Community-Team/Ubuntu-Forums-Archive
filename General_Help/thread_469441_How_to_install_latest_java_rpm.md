---
title: "How to install latest java rpm?"
date: 2007-06-09
forum: General Help
---

### Post by SeattleUser on 2007-06-09
The repository has a really old version of java.  I want to install java 1.6 jre and sdk.  I downloaded the rpm from Sun.  The Ubuntu documentation says that you can use the alien command to convert it to a deb file.  When I type sudo alien I get the command not found message.

First, is there a place to get the latest java for Ubuntu?
Second, How do I install this rpm?

Thanks

---

### Post by taurus on 2007-06-09
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

And if you want to install it by hand, download the .bin version.

---

### Post by NeoLithium on 2007-06-09
Blast! You're a speed demon Taurus ;)

---

### Post by SeattleUser on 2007-06-09
Thanks for the quick reply.  I didn't see the development kit there though.  Is it there?

---

### Post by NeoLithium on 2007-06-09
```
sudo aptitude install sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-fonts
```

EDIT: Ensure you have all the repositories enabled. See [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories) if you don't :)

---

### Post by Pheetuz on 2008-04-06
To install latest Java plugins.

```
sudo apt-get install sun-java6-plugin
```

To install alien.

```
sudo aptitude update
```

```
sudo aptitude install alien
```

---

