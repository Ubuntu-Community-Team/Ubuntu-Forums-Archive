---
title: "I cant lauch ndn - file manager for linux in Ubuntu 14.10"
date: 2014-11-19
forum: General Help
---

### Post by i12 on 2014-11-19
I copy files into home folder, permit lauch as executable, but cant launch either by mouse and in terminal ndn or .ndn.

---

### Post by cariboo on 2014-11-19
I might help if you let us know what ndn is, and where you got it, as I can't find it in the repositories.

---

### Post by i12 on 2014-11-20
Im afraid it so old the only possibility is to send to You it directly. What s Your email?

---

### Post by mcduck on 2014-11-20
Are you maybe talking about "necromancer's DOS navigator"?

Seem s like a command-line application, so clicking the executable with a mouse won't do anything, you need to run it in a terminal. And to do that, keep in mind that neither your home folder or current folder are not included in path, so you need to specifically tell the shell to look for the file in current folder:

```
./ndn
```

However, if you want better supported similar style file manager, I'd recommend giving Midnight Commander a try.

---

### Post by i12 on 2014-11-20
>  			 				[INDENT] 					Are you maybe talking about "necromancer's DOS navigator"?
[/INDENT]


Correct! It definitely is Necromancers dos navigator.

> ./ndn
does not work.

---

### Post by mcduck on 2014-11-21
you need to run it in the same directory where the file is. And of course make sure you have actually set the execute permission on the file.

(I'd still recommend trying [mc]("http://en.wikipedia.org/wiki/Midnight_Commander") instead, as it's well supported on Linux and available through Ubuntu's official repositories)

---

### Post by i12 on 2014-12-02
I checked several times. It must be old ndn impossible to execute.

---

