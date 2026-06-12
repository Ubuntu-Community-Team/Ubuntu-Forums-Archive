---
title: "Adept giving error"
date: 2006-07-16
forum: General Help
---

### Post by true_friend on 2006-07-16
I am using Kubuntu DD. i installed Automatix and Easyubuntu. unfortunately once i openend both applicatons at same time i.e. Adept and Automatix. now adept is giving error. plz see the pic and  suggest me. thnx for reading this message.
[[IMG]http://img139.imageshack.us/img139/9717/adepterroruk9.th.png[/IMG]](http://img139.imageshack.us/my.php?image=adepterroruk9.png)

---

### Post by mogelhead on 2006-07-16
The short answer: you cannot do that.

There are a number of different package managers in (k)ubuntu. Utility programs that lets you install other programs. Examples are Synaptic, Adept, Automatix, Easy Ubuntu. All of them are graphical frontends for the command line tool apt-get. You cannot have two instances of apt-get (the package manager) running at the same time.

The solution is to only have one package manager running.

From the [thread about automatix]("http://www.ubuntuforums.org/showthread.php?t=80295"): "Important Note: Please DO NOT run synaptic while running automatix"

---

### Post by true_friend on 2006-07-16
i know this. but is it possible to remove this error know. the application does not run while it gives error

---

### Post by mogelhead on 2006-07-17
[QUOTE=true_friend]
...
the application does not run while it gives error
[/QUOTE]
So you mean that Automatix is not running?

Can you post the output of the command ```
ps aux
```?

---

### Post by ThrobbingBrain66 on 2006-07-17
when i've gotten that error before all i've done is to open up a konsole and enter:

sudo dpkg --configure -a

maybe this has nothing to do with the problem, but like i said, its worked for me before.

this command takes all packages that are unpacked AND unconfigured, and configures them.

---

### Post by true_friend on 2006-07-21
Adept is not working not the automatix.automatix is is working fine. i try this command also.

---

