---
title: "new firefox doesn't start automatically"
date: 2004-10-31
forum: General Help
---

### Post by Sebastian Richter on 2004-10-31
Hello there,

because the 0.99-whatever-mozilla-firefox had problems with favicons, a known problem, i installed the 1.0rc1. It all worked without problems, well, i had to make a dummy package for mozilla-firefox with equivs so that dependencies with ubuntu-desktop are satisfied.

The problem is, that that new mozilla-firefox doesn't start automatically with gnome, the old one did. When I do "save current setup" it says, that firefox doesn't support it, but that said the log out manager with the old firefox too, so I don't think, that thats the problem.

What is the easiest way to start my new firefox automatically?

Thank you very much in advance,

Sebastian

---

### Post by Charlotte on 2004-10-31
Hi, Sebastian,

please, have a look at this thread:

[http://www.ubuntuusers.de/viewtopic.php?t=49](http://www.ubuntuusers.de/viewtopic.php?t=49)
(in German language)

Beware of the links to the tarball, if necessary.


Hth,
Charlotte

---

### Post by yoha on 2004-10-31
what is & the purpose of dummy package?

yoha

---

### Post by Sebastian Richter on 2004-10-31
Ah,

thanks a lot. So they say, i just shouldn't remove my old firefox? Mpf. Well.

Bye :),

Sebastian

---

### Post by Sebastian Richter on 2004-10-31
[QUOTE=yoha]what is & the purpose of dummy package?

yoha[/QUOTE]

The purpose is, that the debian package management thinks, that a mozilla-firefox package _is_ installed, because I remove the old one, and installed the new one manually. In aptitude, there is a option "installed manually", but it didn't work.

Bye,

Sebastian

---

### Post by ynef on 2004-10-31
[QUOTE=Sebastian Richter]Hello there,

because the 0.99-whatever-mozilla-firefox had problems with favicons, a known problem, i installed the 1.0rc1. It all worked without problems, well, i had to make a dummy package for mozilla-firefox with equivs so that dependencies with ubuntu-desktop are satisfied.

The problem is, that that new mozilla-firefox doesn't start automatically with gnome, the old one did. When I do "save current setup" it says, that firefox doesn't support it, but that said the log out manager with the old firefox too, so I don't think, that thats the problem.

What is the easiest way to start my new firefox automatically?

Thank you very much in advance,

Sebastian[/QUOTE]
 What programs are started up automatically when you log in (assuming you're running gdm, or "graphical login" -- Ubuntu's default) are governed by your .xsession file. You can add any program you want there, even if gnome doesn't feel like letting you.

The order of the items in this file is important.

1) Programs that customize the X environment (usually not needed for something as huge as gnome, since it handles all these things itself, but if you want to remap your keyboard or something, you need to run it first)

2) Any programs that you want to run asynchronically (that is, not waiting for the applications to finish before running the next one) followed by the ampersand symbol (&). This is where you'd start firefox.

3) The window manager to use. If you want to run gnome, the command would be "gnome-session". This is the last command in the file and should NOT have the ampersand symbol following it. For obvious reasons -- see below.

Basically, the file tells the computer what programs to run and what to do when control is passed back to the program that parses the .xsession file. If you run all your apps with an trailing ampersand (asynchronically), you will see them start up and then you will be logged out immediately. That is why you need to run the window manager last and without the ampersand, since it will keep control over the session until you choose to end it.

Default for Ubuntu is to have no user defined .xsession file. This means that the system default is run instead.

In your case, you'd want to have this in your .xsession :

> firefox &
gnome-session

If you've never played with your .xsession file, I suggest also running an xterm, so you can somehow delete the .xsession file without having to drop to a console:

> xterm &
firefox &
gnome-session

---

### Post by Sebastian Richter on 2004-10-31
Thank you very much.

And another way, I figured out is to use the gnome-session-properties program.

I don't know, I used fvwm2 before, and I'm not sure if I like gnomes behavior.

Whatever :)

Bye,

Sebastian

---

