---
title: "How To recover '/bin '"
date: 2013-12-10
forum: General Help
---

### Post by Regis_Wang on 2013-12-10
hi, all
i just did a stupid thing. 
i deleted the /bin directory with command ~$ sudo rm -r /bin
i have a very old backup, but after that i intalled many many software...
what can i do to recover it?
or i can only reinstall the system?
if i must reinstall the system,  which configuration files should i keep?

thx!

[B][SIZE=5][SOLVED]
in #7[/SIZE][/B]
thanks to [SIZE=4]**Bashing-om**[/SIZE]
[COLOR=#000000]long time ago, i used 'remastersys' backup my system, and i made a liveCD(actually it's a *.iso file).[/COLOR]
[COLOR=#000000]i wrote this iso file to my usb, and start my system with usb.[/COLOR]
[COLOR=#000000]i used command[/COLOR]

[COLOR=#000000]~$ sudo cp -r -p /bin /media/185FEF56D231/regis[/COLOR]
[COLOR=#000000]~$ sudo reboot[/COLOR]

[COLOR=#000000]and everything is OK![/COLOR]

---

### Post by PaulBx on 2013-12-10
Pull it off your backup. You DO have a backup, don't you?

---

### Post by Regis_Wang on 2013-12-10
yes, but it's a very old backup, does it work?

---

### Post by Bashing-om on 2013-12-10
Regis_Wang; Hi !

A lot can change, version to version.
Maybe; copy that directory from a liveDVD, exact version that you have installed. Not real sure that the links will be (re)established but, it is worth a shot.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Regis_Wang on 2013-12-10
thx a lot!
i'll try it!
but after that how can i repair the links? you know, i installed many software.

---

### Post by Bashing-om on 2013-12-10
Regis_Wang; Hey,

I would not expect any installed software to be  directly related to the "/bin" directory.
Maybe there will be no broken links, will cross that bridge when we get to it.
Worth a shot and see what results. I can think of nothing better to try, others here are also not offering a alternate solution.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Regis_Wang on 2013-12-11
how can i express my gratitude to you?
i'm very appreciate!
long time ago, i used 'remastersys' backup my system, and i made a liveCD(actually it's a *.iso file).
i wrote this iso file to my usb, and start my system with usb.
i used command

~$ sudo cp -r -p /bin /media/185FEF56D231/regis
~$ sudo reboot

and everything is OK!

thank you!

---

### Post by sisco311 on 2013-12-11
> **Regis_Wang said:**
> yes, but it's a very old backup, does it work?


Traditionally, /bin contains some essential command binaries that need to be available in single user mode for all users, like ls, cp, rm.... The syntax of this commands didn't change substantially in the past few years. So yes, it should work.

> **Regis_Wang said:**
> thx a lot!
i'll try it!
but after that how can i repair the links? you know, i installed many software.

You can list the packages which have files installed in /bin with:
```
dpkg -S /bin
```
and you can reinstall them with:```

sudo apt-get update
sudo apt-get --reinstall install **pkg1 pkg2 pkg3 ...**
```
where **pkg1 pkg2 pkg3 ... **are the name of the packages listed by dpkg.

Even if you don't have a backup you only need a few GNU/utilities which you can copy over from a (binary compatible) Live CD/USB or existing Linux installation:


[list]
[*]/bin/dash (I guess any POSIX-compliant shell will do it)
[*]/bin/sh (must be a symlink to the shell /bin/dash)
[*]/bin/sh.distrib (optional, same as sh, a symlink to dash)
[*]/bin/cp
[*]/bin/rm
[*]/bin/sed
[*]/bin/grep
[*]/bin/tar
[*]/bin/gzip
[/list]

Then you can chroot into Ubuntu and reinstall the packages you need.

---

### Post by Regis_Wang on 2013-12-11
thank you!
i learned a lot of things from you!
next time i wouldn't worry about it.

---

