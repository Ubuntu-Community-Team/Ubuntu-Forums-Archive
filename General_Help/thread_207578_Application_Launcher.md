---
title: "Application Launcher"
date: 2006-07-02
forum: General Help
---

### Post by SpunkyMonkey on 2006-07-02
I am trying out Kubuntu on my PC. Currently my main OS is Mac OS X, but that just might change. :) 

One of the things that I have grown to love in OS X is a program called [QuickSilver](http://quicksilver.blacktree.com/), a handy application where you, at any time, type in a shortcut (CTRL + Space for me), type in the name of the program or file you want opened, and hit enter. So I could open up, say, report.doc, or open up a program like Firefox, just by typing its name and be done within the blink of an eye. You can also do other things like playing/pausing/stopping music and skipping tracks with it.

Is there anything similar to this for Linux that will run on Kubuntu? If there is that would be simply awesome. Thanks.

---

### Post by Jucato on 2006-07-02
You're in luck! There is. The program's name is Katapult. You choose which "catalogs" it scans through: Documents, Bookmarks, Amarok (playlists and music), Programs, and Calculator (you can use Katapult for instant and basic calculations). Unfortunately, you can't really control which directories it scans. I think it scans the whole /home directory for Documents, Konqueror's bookmarks for Bookmarks, and Amarok's Collection for Amarok. And it only scans the K Menu for Programs, so only programs that have entries in K Menu could be launched from it. The default shortcut key for it is Alt+Space, but that can be changed.

---

### Post by SpunkyMonkey on 2006-07-02
Sweet! This will make my Kubuntu experience much, much better. Thanks. :)

EDIT: I think I posted too soon. I downloaded Katapult 0.3.1.2 and extracted it. I read the install instructions, and it told me to run the configure file in Konsole. When I did this, Konsole returned this:
> checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Any idea what to do? Thanks again.

---

### Post by Jucato on 2006-07-02
Katapult is found in the repositories. It can be installed using Adept. It's in the main repositories, AFAIK.

---

### Post by gingermark on 2006-07-02
In fact, it is **installed by default** in Kubuntu! :)

It's in your "Utilities" menu

---

### Post by Jucato on 2006-07-02
[QUOTE=gingermark]In fact, it is **installed by default** in Kubuntu! :)

It's in your "Utilities" menu[/QUOTE]

I didn't notice that in my default install. :D
Thanks for pointing that out gingermark.

---

### Post by SpunkyMonkey on 2006-07-02
Oh nice. That'll save me a ton of work. Thanks a lot! Problem solved.

---

### Post by gurgle on 2006-07-13
is there a gnome version of katapult? i know i can just use it with gnome, but then i feel dirty :neutral:

---

### Post by hackerssidekick on 2006-07-14
You should take a look at deskbar-applet (found in the add to panel option in gnome) if you haven't already.

I works pretty well and has a ton of plugins already!

---

