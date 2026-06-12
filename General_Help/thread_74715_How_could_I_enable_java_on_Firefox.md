---
title: "How could I enable java on Firefox ?"
date: 2005-10-12
forum: General Help
---

### Post by kurtkraut on 2005-10-12
Ie found some instructions to do that on [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) but it doesn't work. 

Ubuntuguide says:

**sudo apt-get install sun-j2re1.5**
**java -version**

apt.get doens't find this packages. I've already expanded my repositories. How should I proceed ?

Thanks

---

### Post by Olav on 2005-10-12
If you already edited /etc/apt/sources.list, did you also do

apt-get update

before you did

apt-get install blah

??

---

### Post by bored2k on 2005-10-12
[http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

That should work.

---

### Post by Olav on 2005-10-12
[QUOTE=bored2k][http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

That should work.[/QUOTE]

Aha!

---

### Post by kurtkraut on 2005-10-12
[QUOTE=bored2k][http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

That should work.[/QUOTE]


Hi,

It works ! Thanks for the help.

---

