---
title: "OpenOffice.org refuses to open files with 'strange' names"
date: 2006-11-22
forum: General Help
---

### Post by joe.turion64x2 on 2006-11-22
Hello there, I am new to these world of Ubuntu (not to Linux) and am really pleased with it, well almost.

I am experiencing some problems with OpenOffice, mainly because it refuses to open some files. For a better understanding of the problem I will divide it in sections:

BEFORE.
I was really happy with my new installation of Ubuntu 6.10 "Edgy Eft". After trying several other 'distros' I prefer Ubuntu (at least for my notebook) because it has an outstanding power management feature (battery lasts longer than in Windows) and it recognized everything.
For the sake of completeness I will say that I couldn't get entirely rid of KDE and installed Kile, KOrganizer, and Amarok :mrgreen: (perhaps it will be useful to check dependencies).
OpenOffice.org ran smoothly and could handle every file I thrown to it (I only worked with Calc, Writer and Draw).

PRELIMINARY PROBLEM.
I tried to use for the very first time OpenOffice.org Database and had problems when attempted to create a form (I could make a table 8) ). I couldn't solve this but I won't discuss it here because I believe there are some threads already devoted to it.

ACTIONS TAKEN.
-Reinstalled the packages through Synaptic (those I could figure where related to OpenOffice.org). It did not work.
-Tried to get rid of the OpenOffice bundled with Ubuntu (I actually removed it with Synaptic) but couldn't install the one I downloaded from [www.openoffice.org](www.openoffice.org) because of RPM issues(I installed rpm through Synaptic also).
-Reinstalled the OpenOffice.org bundled with Ubuntu (with all the Java support).

A NEW PROBLEM AROSE. ](*,) 
-When I try to open a file (from any OpenOffice.org application) whose name includes one or more SPECIAL character, OOo displays an error message saying that the file (I am trying to open) does not exist and refuses to open it.

SOME FACTS.
-Only files with 'special' names are affected. Nevertheless I can open them through the Open command in OOo.
-I think it is not an OOo fault itself because, in the case of the database, I could make it in another computer with Fedora Core and even an older version of OOo.
-I suspect that is a problem of integration of OOo and Gnome (or Ubuntu itself).
-Everything worked perfectly (except the database) before I reinstalled OOo.

FUTURE ACTIONS.
-My next action would be to reinstall the system but I'd rather make something more civilized so please, if anybody has an idea please help!
(I would be happy even with the database not functioning, I just want to access my files normally).

Thanks in advance.

---

### Post by joe.turion64x2 on 2006-11-25
Just to complete this post I will add that I could solve the issue (along with the one related to the database) by installing OpenOffice.org official package through alien.
Unfortunately I couldn't enjoy that because my system became unstable several days after that: it was very slow and out of the sudden it refused to boot ("can not find tty"). I read this was produced by something wrong in Ubuntu's installation procedure **when you make a custom partitioning** (the default partitioning option works just fine), and that was my case. According to this, Ubuntu will likely corrupt its own filesystem along with the FAT32 filesystems. I am not saying this is true but since it refused to work and I want to keep my data safe I will try some other distro (at least until I can give Ubuntu my whole hard drive).
Cheers and good luck.

---

### Post by cantormath on 2006-11-25
> **joe.turion64x2 said:**
> Just to complete this post I will add that I could solve the issue (along with the one related to the database) by installing OpenOffice.org official package through alien.
Unfortunately I couldn't enjoy that because my system became unstable several days after that: it was very slow and out of the sudden it refused to boot ("can not find tty"). I read this was produced by something wrong in Ubuntu's installation procedure **when you make a custom partitioning** (the default partitioning option works just fine), and that was my case. According to this, Ubuntu will likely corrupt its own filesystem along with the FAT32 filesystems. I am not saying this is true but since it refused to work and I want to keep my data safe I will try some other distro (at least until I can give Ubuntu my whole hard drive).
Cheers and good luck.

what file extentions do these unopenable files have?

---

### Post by fragos on 2006-11-25
Special characters in file names can cause problems, don't use them.  "-" and "_" are fine.  On the command line even spaces can be a problem.

---

### Post by joe.turion64x2 on 2006-11-27
The files I attempted to open where normal OpenOffice files (.odt, etc) with an accent in any part of either its name or in their path.
Installing the official OpenOffice build solves the problem.

---

### Post by fragos on 2006-11-27
Being an English speaker I don't have accented characters to deal with.  Actually I wouldn't be surprised if there were treated as special charaters.  It might also be impacted by which character encoding you're using.  Glad your problem was solved.

---

