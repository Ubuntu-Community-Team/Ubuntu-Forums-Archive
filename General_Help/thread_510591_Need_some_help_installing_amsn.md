---
title: "Need some help installing amsn"
date: 2007-07-26
forum: General Help
---

### Post by nu buntu on 2007-07-26
Ok, I was following this guide at [http://ubuntuforums.org/showthread.php?t=75276]("http://ubuntuforums.org/showthread.php?t=75276") and I got up to the part with gedit and when I tried to run the script, this is the error I got.

```
[: 50: 0: unexpected operator
/home/****/amsn-installer: 172: Syntax error: "do" unexpected (expecting "}")
```

It has something to do with the code, but since I don't know how to properly change it, could someone please tell me what to change?

---

### Post by dje on 2007-07-26
Try installing amsn using synaptic?

---

### Post by louistan3 on 2007-07-26
hi....

uhmm not really sure about that... but did u try making the file again and recopying the script?

it might be that you just missed something...

hope this helps :)

---

### Post by nu buntu on 2007-07-27
Ok, I tried to get it a different way, I am now using

```
sudo apt-get update
sudo apt-get install amsn
```

But it gives me the error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amsn
```

Do I need to add a repository for this to work?  If so, what is it?

---

### Post by por100pre1 on 2007-07-27
[Automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation") adds a repository that includes amsn and other programs. Use it carefully.

---

### Post by Majorix on 2007-07-27
Go to system, preferences. Check everything there. If it shows a minus instead of a check, unminus it and check it. Then you will have the necessary repos enabled. If that still doesn't help
```
sudo gedit /etc/apt/sources.list
```

Then uncomment the lines starting with deb-src etc.

---

### Post by nu buntu on 2007-07-27
> **Majorix said:**
> Go to system, preferences. Check everything there. If it shows a minus instead of a check, unminus it and check it. Then you will have the necessary repos enabled. If that still doesn't help
```
sudo gedit /etc/apt/sources.list
```

Then uncomment the lines starting with deb-src etc.

Thank you so much!  The sudo gedit /etc/apt/sources.list fixed my problem and I now have amsn installed.

---

