---
title: "openoffice problem"
date: 2004-12-14
forum: General Help
---

### Post by mutato on 2004-12-14
I have installed Ubuntu 4.10 just few hours ago, it's wonderful! But openoffice don't work. When I call openoffice from menu it said:

"An unrecoverable error has occurred"

I tried to call openoffice from command line and it said:

```

~$ openoffice
sh: line 1: crash_report: command not found

Fatal exception: Signal 11
Stack:

```

From command line generic windows of OOo start, but when I call a specific applications from File menu it crashed.

Finally, I have tried to reinstall OOo from dselect but problem persist.

Can you help me?

---

### Post by mutato on 2004-12-15
I tried to create new user and OO.o works for it! But my original user it isn't able to use OO.o like yesterday. But my original user have same file of my temp user! I don't understand. 

Can you help me?

---

### Post by wulf on 2004-12-15
That seems really odd! Do you want to say a bit more about what hardware you've installed it onto?

Wulf

---

### Post by randy on 2004-12-15
If it's a problem for the one user you should just delete the user's config directory.  It's available at ~/.openoffice

---

### Post by jdong on 2004-12-15
Signal 11 is a segmentation fault (i.e. Access Violation).

Sometimes, it has hardware roots. (i.e. BAD RAM).

Do a Memtest -- it's in Ubuntu's bootup GRUB menu.

---

### Post by mutato on 2004-12-17
[QUOTE=randy]If it's a problem for the one user you should just delete the user's config directory.  It's available at ~/.openoffice[/QUOTE]

Yes, I thought it also. I remove ~./openoffice dir from /home/OLDuser, but when I call OO.o it said: "I can't recognize .openoffice, please fix problem manually". When I do

OLDuser:~$ cp -r /home/NEWuser/.openoffice /home/OLDuser

but OO.o sait again "An unrecoverable error has occurred"

When I replace recursively ALL referrer about NEWuser with OLDuser but situation not change. I tried too remove .openoffice dir and apt --remove --purge openoffice.org and after apt-get --install openoffice.org. Now I have a new .openoffice dir into my /home users but again "An unrecoverable error has occurred" (for my OLDuser, and not for my NEWuser).

Now, I am enough sure that the problem is locate in other place, but where? My /home/OLDuser is a home directory from Debian Woody, where OO.o and Gnome was NOT installed. I have problems with OO.o only! All other applications seems works perfectly. I had purge all reference about old applications, deleting all dotted dir before copy user data.

Please, help me!

---

### Post by mutato on 2004-12-17
[QUOTE=wulf]That seems really odd! Do you want to say a bit more about what hardware you've installed it onto?
Wulf[/QUOTE]

Normally i386. 

Intel Celeron 2.4 Ghz
Asus MotherBoard
512 MB RAM

I don't have problem. Only OO.o for one user have problem. 

I can sure 

mv /home/OLDuser /home/tempuser

deluser OLDuser
adduser OLDuser

and when copy OLDuser data in new OLDuser home dir. But I prefer know where problem is locate, because I want replace desktop box based on Debian Woody with Ubuntu.

---

