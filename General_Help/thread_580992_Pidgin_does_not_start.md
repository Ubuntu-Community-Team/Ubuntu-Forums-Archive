---
title: "Pidgin does not start?"
date: 2007-10-19
forum: General Help
---

### Post by chunchengch on 2007-10-19
I install pidgin from Synaptic, but I can not find it in the Application menu, so I create one from System> Preference > Main Menu, while when I click the icon, nothing happens, no pidgin window appears, no icon appears in the system tray, what is the problem? :confused:

Thanks for any help!

---

### Post by LanDan on 2007-10-19
what the problem is? no idea, but first lets figure out what is not the problem ;)

can you open a terminal and type "pidgin" (if that doesn' t work try /usr/bin/pidgin ) and see what happens

---

### Post by chunchengch on 2007-10-19
It is weird, I type command "/usr/bin/pidgin" in the launcher, pidgin does not start, while I change the commmand to "pidgin", it works.

BTW, the package in Synaptic is of version 2.2.1, while the pidgin I open is 2.0.2, another weird thing?:confused:

However, thank you!

---

### Post by LanDan on 2007-10-19
mine is 2.2.1

try an upgrade

---

### Post by mahousaru on 2007-10-19
Did you have an earlier version compiled from source?

You should be able to tell where you are running the app from, by opening up a console and typing:

whereis pidgin

The gutsy pidgin binary is located in /usr/bin/pidgin (as already posted)

---

### Post by chunchengch on 2007-10-19
> **mahousaru said:**
> Did you have an earlier version compiled from source?

Thanks, you remind me that this version 2.0.2 was compiled from source.

But, there is a new problem, this version 2.0.2 is installed under /usr/local, in order to install the 2.2.1 from Synaptic, I remove those Pidgin files and directories from /usr/local, and re-install from Synaptic, however, when I type pidgin in terminal, there is error occurs, I do not know what the error message means, would you please tell me what and how to do? thanks again!

$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance
$ cd /usr/bin
/usr/bin$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

---

### Post by LanDan on 2007-10-19
somebody else might know what the error means, but they will have to be able to read it first ;)

can you copy paste the errror message here?

---

### Post by chunchengch on 2007-10-19
I find this thread [http://ubuntuforums.org/showthread.php?t=491673&highlight=symbol+lookup+error%3A+pidgin%3A+undefined+symbol%3A+purple_core_ensure_single_instance#cooliris](http://ubuntuforums.org/showthread.php?t=491673&highlight=symbol+lookup+error%3A+pidgin%3A+undefined+symbol%3A+purple_core_ensure_single_instance#cooliris) ,
and then I delete these files and links under /usr/local/lib

libpurple.so
libpurple.so.0
libpurple.so.0.0.1
libpurple.so.0.0.2

now, I can activate Pidgin 2.2.1 installed from Synaptic.:)

---

### Post by esun819 on 2007-10-22
i had this problem too, but managed to solve it by removing pidgin, then i deleted the pidgin folder /usr/local/lib (and all instances of libpurple.so) as well as those in /usr/local/ and reinstalled it. it starts now, no problem.
hope that helped

---

### Post by Zogg on 2007-10-23
> **esun819 said:**
> i had this problem too, but managed to solve it by removing pidgin, then i deleted the pidgin folder /usr/local/lib (and all instances of libpurple.so) as well as those in /usr/local/ and reinstalled it. it starts now, no problem.
hope that helped

Had similar problem and this really did help. 
Thank you. :)

---

### Post by TheTank on 2007-10-23
Just wanted to say thanks!
Had the same problems when wanting to remove my self-compiled version to an official version.

Deleted the libpurple stuff and it worked,
Thanks guys and gals!

---

### Post by Kymus on 2007-10-23
> **chunchengch said:**
> I install pidgin from Synaptic, but I can not find it in the Application menu, so I create one from System> Preference > Main Menu, while when I click the icon, nothing happens, no pidgin window appears, no icon appears in the system tray, what is the problem? :confused:

Thanks for any help!

I had the same problem before. I installed it, then it wasn't in the menu :confused::confused:

after I upgraded to Gutsy, it was there and ran fine...

I've experienced this problem with two other programs thus far: Avast! and Virtual Box.

---

### Post by Kymus on 2007-10-23
> **LanDan said:**
> what the problem is? no idea, but first lets figure out what is not the problem ;)

can you open a terminal and type "pidgin" (if that doesn' t work try /usr/bin/pidgin ) and see what happens

that actually fixed some of the problems I was having with something else thanks! :)

---

