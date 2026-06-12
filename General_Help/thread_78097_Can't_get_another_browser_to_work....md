---
title: "Can't get another browser to work..."
date: 2005-10-17
forum: General Help
---

### Post by G_u_s on 2005-10-17
hello !

first, i'm not so sure i'm posting where i should, so feel free to tell me where to go instead if i am indeed not =)

ok, now to my problem(s).

i was a happy Firefox user under Windows, and to a lesser extent on my desktop computer under Ubuntu. now, i'm using it on my laptop, and it sometimes freezes when i open a new tab (i can move the cursor but cannot click anything), which is VERY annoying. i've read that Opera and Epiphany were faster, so wanted to try them (actually, i was not too keen on Opera because of it's non-open status but wanted to try anyway, to compare).

the problem is that, after i have installed them, they just won't run. here is what i get when trying to run them:

for Epiphany
```
augustin@kronenbourg:~$ epiphany
epiphany: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory
```

and for Opera
```
augustin@kronenbourg:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
waitpid: No child processes
Segmentation fault
```

things that can be of interest: i tried to tweak Firefox, following various tutorials etc. My current running firefox is one downloaded from mozilla.org, not the original Ubuntu one. To be able to run the firefox-installer, i had to install libstdc++5, because the libstdc++.so.5 was missing. i'm providing this information since, to my newbie eyes, it looks similar to the above problems and may be related =)


anyway, if you need any additional information, feel free to ask and i'll provide them asap.

thanks in advance, good people of the Ubuntu forums =)

---

### Post by realwhz on 2005-10-17
Hi,

Epiphany needs Gecko engine provided by mozilla.  Since this engine is not released lonely, epiphany has to be built on other mozilla browsers, say, mozilla suite or firefox.  In ubuntu, it's foundation is firefox.  The problem you encountered should be due to the fact that you have not install firefox from deb.  libgtkembedmoz.so should be in /usr/lib/mozilla-firefox/libgtkembedmoz.so.  In fact, I guess you may have installed epiphany-browser forcely, which broken the dependences between it and deb-based firefox.

As for opera, I don't have any experiences about it.  Sorry.

---

### Post by kperkins on 2005-10-17
How did you install Opera? I've got it working for me, no problems, and it is faster than Firefox.
The libs you're missing are from the java/sdk,do you have jave installed on your system?

---

### Post by G_u_s on 2005-10-18
thanks for the quick answers guys =)

@realwhz
it is very possible that my messing around with Firefox caused the problem you describe. how can i circumvent that, then ? what package should i reinstall so that i get the gecko engine in a place that Epiphany will find ? (obviously, it IS there or i wouldn't be able to run firefox and type this to you, right ?)

@kperkins
i have downloaded the .deb from the Opera website and installed it with dpkg -i operaXXXXXX.deb
i have java installed, but i installed the JRE, not the JDK. will installing the JDK fix the problem ?

i'm off to Uni right now, but will try these when i'm back =) thanks again for your help.

---

### Post by kperkins on 2005-10-18
That may be the problem jdk provides those libs, I don't know if jre does. Which opera deb did you download--they have 3 for Ubuntu (one for each version) if you installed the one for the wrong version, it may give you problems.

---

### Post by G_u_s on 2005-10-18
i have dl'ed the JDK and will try it to see if it solves the problem.

also, i am pretty sure i have downloaded Opera for Breezy, but a mistake is always possible, so i'll double-check that as well.

---

### Post by G_u_s on 2005-10-19
okay, resintalling Firefox from Synaptic made epiphany work. of course, i'm back to the very slow Firefox with freezes when i open tabs... but since Epiphany didn't really conquered me anyway, i might re-install from mozilla.org eventually. Opera i didn't have time to test yet.

---

### Post by dakira on 2005-10-19
Hi,

I have to admit I'm kind of an Opera evangelist ;) Best browser I ever met. I even paid for it when it wasn't free.

You could try the statically linked version of Opera:

```
wget ftp://ftp.heanet.ie/pub/opera/linux/850/final/en/i386/static/opera-static_8.50-20050916.1-qt_en_i386.deb
sudo dpkg -i opera-static_8.50-20050916.1-qt_en_i386.deb

```

If you want nice AdBlocking I wrote a small script which installs a CSS-based AdBlocker.. it's somewhere at the end of this thread:
[http://ubuntuforums.org/showthread.php?t=33945](http://ubuntuforums.org/showthread.php?t=33945)

---

### Post by G_u_s on 2005-10-19
cheers =) it seems to have worked perfectly, except i still get an error message (from within Opera this time) saying that i need to install "Motif" (whatever that is). i will look in Synaptic though. and thanks for your link, i will follow it soon =)

EDIT: weird... i DO have the said file (operamotifwrapper-3) in a dir listed in the plug-in dir (/usr/lib/opera/plugins/) but i get a message telling me i don't =/

---

### Post by G_u_s on 2005-10-20
any idea about that ?

---

### Post by dakira on 2005-10-20
[QUOTE=G_u_s]any idea about that ?[/QUOTE]
yep. what you saw there is the operamotifwrapper. Opera's wrapper for motif. Of course this doesn't work if motif is not installed.

You should not have these problems if you downloaded the statically linked version I posted above.

---

### Post by G_u_s on 2005-10-21
yeah, i should not, but i do, that's why i am puzzled =/

---

### Post by dakira on 2005-10-21
[QUOTE=G_u_s]yeah, i should not, but i do, that's why i am puzzled =/[/QUOTE]
Mhh.. Have you ever tried installing motif?
```
sudo apt-get install libmotif3
``` What puzzles me is that Opera usually doesn't use motif at all. It's a QT application. For me it was always THE application proving the QT is the way to go for cross-plattform development.

---

### Post by G_u_s on 2005-10-21
thanks =) what repository do i need to install it, please ? apt-get couldn't find it.

this is what i got when trying to apt-get libmotif (without the 3):

```
augustin@kronenbourg:~$ sudo apt-get install libmotif
Reading package lists... Done
Building dependency tree... Done
Package libmotif is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lesstif2
E: Package libmotif has no installation candidate

```

---

### Post by dakira on 2005-10-21
[QUOTE=G_u_s]thanks =) what repository do i need to install it, please ? apt-get couldn't find it.

this is what i got when trying to apt-get libmotif (without the 3):

[/QUOTE]

You have to get libmotif**3** (*with* the 3!). It is in the official repositories. If you can't find it try adding universe and multiverse to your repositories.

Nonetheless, I don't have this installed and Opera works for me.. so this is quite strange. How are you running Opera? Where are you getting the error message? Try running it with CTRL+F2 -> opera

---

### Post by G_u_s on 2005-10-21
[QUOTE=dakira]You have to get libmotif**3** (*with* the 3!).[/quote]
sorry, i didn't express myself correctly.
what i meant is: i have tried with the 3 and got nothing. i then tried without, and got the above message.

> It is in the official repositories. If you can't find it try adding universe and multiverse to your repositories.
i have universe added but not multiverse. maybe i haven't looked around properly, but i couldn't find how to add multiverse in the ubuntu wiki, and didn't look too much into it since i didn't need it. could you be so kind as to tell me what i must add, please ?

> Nonetheless, I don't have this installed and Opera works for me.. so this is quite strange. How are you running Opera? Where are you getting the error message? Try running it with CTRL+F2 -> opera
when i launch Opera, i get this message, then click ok, then Opera launches and i can navigate without any problem. i also get the opportunity to "not show this message again".
i am running opera through the "opera" command, for which i have created a "custom application launcher".

i don't get the "CTRL+F2" part, sorry: when i do it from my desktop, it does nothing (or at least i can't see it doing anything), and when i go into a terminal, it just inputs the letter "Q".

thanks for your help, sorry to be so bad at that =/

---

### Post by dakira on 2005-10-22
[QUOTE=G_u_s]i have universe added but not multiverse. maybe i haven't looked around properly, but i couldn't find how to add multiverse in the ubuntu wiki, and didn't look too much into it since i didn't need it. could you be so kind as to tell me what i must add, please ?[/QUOTE]
Yep. My /etc/apt/sources.list looks like this:
```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
```

> i don't get the "CTRL+F2" part, sorry: when i do it from my desktop, it does nothing (or at least i can't see it doing anything), and when i go into a terminal, it just inputs the letter "Q".
Ouch... my fault.. I meant ALT+F2 ;) But your launcher should do it.. I really don't know what else to do.. have you tried google with the error message?

One thing: Are you sure you installed the statically-linked version of opera which I gave you the link to?

Oh.. another question: Is it possible you are running a 64bit architecture? I heard there where problems with plugins and i64.

Anyway.. I checked for other motif libraries and figured out I have lesstif1 und lesstif2 installed. Both are located in the universe repository. I also figured out that the operamotifwrapper is only needed if you want other plugins (like flash) to work properly. If you have a 64bit computer install lesstif1 and lesstif2 for both 32bit and 64bit because the operamotifwrapper-x needs them in 32bit.

**EDIT:** I also found [this]("http://ubuntuforums.org/showthread.php?t=76648") thread where people have the same problem you do. Installing libmotif3 worked for some, installing the statically linked version worked for others. Could you check if you have all 3 operamotifwrapper-X files in /usr/lib/opera/plugins? If there is only operamotifwrapper-3 you need to install the statically linked version of opera (which includes -1 and -2) or install libmotif3. If all three are there you might want to reinstall lesstif1 and lesstif2.

---

### Post by G_u_s on 2005-10-22
i am sure i have installed the static version oyu have given me. a search with "opera" in Synaptic returned an installed package of the name of "opera-static", version 8.50-20050916.1. i also have another "opera" package, uninstalled though (most likely from when i installed Opera using the package on Opera's website).

i also have libmotif3 installed (since i have added multiverse to my repositories sooner in the afternoon).

here is the content of the directory you wanted:
```
augustin@kronenbourg:~$ ls /usr/lib/opera/plugins/
libnpp.so            operamotifwrapper-2  operaplugincleaner
operamotifwrapper-1  operamotifwrapper-3
```

i am currently installing libmotif3-dev, to see if it will fix the problem. i'll edit the result in a short while.
EDIT: it did not fix anything i'm aware of.

could it be that the error comes from me not giving enough rights, or something ?
EDIT: chmod +777 * in the /usr/lib/opera/plugins/ dir didn't change anything (predictably).

EDIT: removing/resintalling opera-static didn't change anything.

i'll read the thread you linked and see if i can do anything about that.
EDIT: none of the solutions found in the other thread worked. something wicked's at work here ^^

thanks again =)

---

### Post by dakira on 2005-10-22
again my question: Do you have a 64bit processor?

---

### Post by G_u_s on 2005-10-22
sorry forgot this one. no, i have a regular i386 architecture, no 64bit.

---

### Post by dakira on 2005-10-22
Well.. I think I will make use of my Opera Premium support account and ask them what to do ;)

Can you run opera from a terminal and post any errors you get here, please?

---

### Post by G_u_s on 2005-10-23
hehe cheers =)

when i launch opera in a terminal, i get only:
```
waitpid: No child processes
```

then, when i try to access a website with some Flash in it (i think: [http://www.sports.fr](http://www.sports.fr) ), i guess those errors repeating themselves:
```
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

```

i will also take a shot of the error message and edit it in later.
EDIT: added as an attachment.

EDIT: i have tried rebooting (yeah, i had not thought of it), but to no avail, unfortunately =/ i will try googling the error messages to see if i can get any help from there. not sure how soon i will be able to do that however.

---

### Post by dakira on 2005-10-23
One thing before I send the support request:
```
/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-2: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
/usr/lib/opera/plugins/operamotifwrapper-3: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
```
Did you try to look for these files? On your system all three of them should be present, since you have lesstif1, lesstif2 and libmotif3 installed. Maybe they are not in the PATH or something?!
Try:
```
find /usr/ -name libXm.so.* 
```
This should give you a couple of files and usually they should be in /usr/lib. If not the motif libraries are not installed correctly on your system. Try reinstalling them.

If you only find files like libXm.so.2.0.1 but not libXm.so.2 then create a symlink with
```
ln -s /usr/lib/libXm.so.2.0.1 /usr/lib/libXm.so.2
```
etc.

But as I said.. it should usually all be there and should all be found by opera..

---

### Post by G_u_s on 2005-10-23
tried typing your command "find", here is the result:
```
augustin@kronenbourg:~$ find /usr/ -name libXm.so.*
/usr/X11R6/lib/libXm.so.3.0.2
/usr/X11R6/lib/libXm.so.3
```

also, i provide this:
```
augustin@kronenbourg:~$ ls /usr/lib/opera/plugins/
libnpp.so            operamotifwrapper-2  operaplugincleaner
operamotifwrapper-1  operamotifwrapper-3
```

i'll try re-installing lesstif1 and 2, and maybe copying libXm.so.3 to /usr/lib/


EDIT: ok, it works. here is what i did: i have reinstalled lesstif1 and 2, libmotif3 and libmotif3-dev, motif-clients and INSTALLED motifnls. i don't know which one fixed it, but i'd tend to think it's motifnls, since the other were installed anyway.

WELL, that works, so let's leave it at that. thanks a WHOLE load for your time and perseverance dakira, it was very nice of you to spend so much time helping me. thanks a bunch =)

---

### Post by dakira on 2005-10-23
> **G_u_s]EDIT: ok, it works. here is what i did: i have reinstalled lesstif1 and 2, libmotif3 and libmotif3-dev, motif-clients and INSTALLED motifnls. i don't know which one fixed it, but i'd tend to think it's motifnls, since the other were installed anyway.[/QUOTE]
You can safely uninstall  libmotif3-dev, motif-clients and motifnls as you really don't need them. You problem was that lesstif1/2 were not installed correctly (as the libraries didn't show up in you "find"-search) and libmotif3 was in the wrong place (it should have been in /usr/lib) so Opera couldn't find it. But if you want you can leave it as it is  said:**
> WELL, that works, so let's leave it at that. thanks a WHOLE load for your time and perseverance dakira, it was very nice of you to spend so much time helping me. thanks a bunch =)
As I said in the beginning.. I'm an Opera evangilist.. it's one of the best internet tools I know and I like the company.. so I help spreading the word ;)

To get you started you might want to check out these sites:
[Opera Wiki]("http://nontroppo.org/wiki/Opera")
[Andrew Gregory&#8217;s Opera pages]("http://www.scss.com.au/family/andrew/opera/")
[30 days to becoming an Opera lover]("http://operalover.tntluoma.com/")
[Opera Resources]("http://www.howtocreate.co.uk/operaStuff/")

...and of course opera.com and my.opera.com since there's a lot of stuff on their pages, too.

Hope you will stick with it ;)

---

