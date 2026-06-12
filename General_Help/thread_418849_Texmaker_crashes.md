---
title: "Texmaker crashes"
date: 2007-04-22
forum: General Help
---

### Post by ernstblaauw on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/texmaker/+bug/88891](https://bugs.launchpad.net/ubuntu/+source/texmaker/+bug/88891) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm running Feisty Fawn on a AMD64 proc. I installed Texmaker using apt-get. However, when I try to start Texmaker, it crashes with the message:
```
Segmentation fault (core dumped)
```
I also tried to compile Texmaker myself, but then, I get the same error message. And when I try to run the static i386 binary package from the [Texmaker website]("http://www.xm1math.net/texmaker/download.html"), I get the following message:
```
./texmaker_linux_installer: error while loading shared libraries: libXfixes.so.3: cannot open shared object file: No such file or directory
```
Does anyone know how I can get Texmaker to work?

---

### Post by nanotube on 2007-04-22
i haven't used texmaker, and this is probably not exactly what you are looking for, but...

try using "kile" instead. it's a really good latex editor. :)

---

### Post by diegor on 2007-04-25
I was using texmaker with Ubuntu 6.10 edgy amd64 and I worked very well.

Then I updated to Ubuntu 7.04 Festy and I obtained the same crash as you. I have tried to install it again but there is the same problem.

I used to use Kile, however I think that texmaker is much better: It is faster!.

---

### Post by chipfay73 on 2007-05-01
I am running u7.04 on an amd 64 texmaker runs fine if I 
sudo su
texmaker

this works, but not as a regular user

---

