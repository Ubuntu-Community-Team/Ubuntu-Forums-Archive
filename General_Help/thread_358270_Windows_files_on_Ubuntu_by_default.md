---
title: "Windows files on Ubuntu by default?"
date: 2007-02-10
forum: General Help
---

### Post by ardchoille42 on 2007-02-10
I am using Ubuntu 6.06.1 LTS. I use only the package manager to install/uninstall things and I only use the default Ubuntu repos, I never compile apps. I never use Windows or Windows files.

Have a look at this:

```

[~ @ 05:53:53] locate .exe
/usr/lib/python2.4/distutils/command/wininst-6.exe
/usr/lib/python2.4/distutils/command/wininst-7.1.exe
[~ @ 14:05:52] locate .dll
[~ @ 14:06:07] file /usr/lib/python2.4/distutils/command/wininst-6.exe
/usr/lib/python2.4/distutils/command/wininst-6.exe: PE executable for MS Windows (GUI) Intel 80386 32-bit
[~ @ 14:09:36] file /usr/lib/python2.4/distutils/command/wininst-7.1.exe
/usr/lib/python2.4/distutils/command/wininst-7.1.exe: PE executable for MS Windows (GUI) Intel 80386 32-bit
[~ @ 14:09:49]

```

Why do I have two Windows .exe files on my system? Does Ubuntu install .exe files when you install Ubuntu? Are these files necessary or can I delete them? Which package installed them?

I don't like Windows or its files. I guess I'll have to install a virus checker if there are going to be windows files on my system.

[COLOR="Blue"]EDIT[/COLOR]: I have found that these two .exe files were installed with the main python2.4 package from the main repo. But why? Why would a Linux system need .exe files?

---

### Post by Gibbs on 2007-02-10
They are included in the Python packages...

Edit: Bah just saw your edit. No idea.

---

### Post by ardchoille42 on 2007-02-10
Well, it's my opinion that this should be looked into. I am reminded of a few stories lately (Apple iPod?) where company A's software is contracted out to company B only to find that company A's software/hardware had viruses upon release because company B didn't do proper virus checking before sending the completed work to company A. Who compiled those .exe's?

Just my opinion, but I feel that the Ubuntu and/or python devs/packagers should look into this.

---

### Post by deanlinkous on 2007-02-10
It is "normal" as I have seen the same thing reported on other distros and so forth....

Never have checked to see what it is. I should though.

---

### Post by ardchoille42 on 2007-02-10
Sounds like the python devs need to be made aware of this. If it's seen on other distros, then it isn't an Ubuntu problem. Has anyone ever checked these two files for viruses/malware/trojans/worms? Kinda worries me that distro maintainers take .exe files and distribute them to millions of Linux users. I hope someone is checking these files out first.

---

### Post by R3linquish3r on 2007-02-10
Even if there is, Windows viruses and such wont effect Linux.

---

### Post by ardchoille42 on 2007-02-10
> **R3linquish3r said:**
> Even if there is, Windows viruses and such wont effect Linux.

Well, that's true. But, it may need to be looked into for those people who dual boot Windows and Linux, have a Windows box on their network or share files between the two platforms.

Since Windows .exe don't run on my Ubuntu installation, is there a problem with deleting these two files:

/usr/lib/python2.4/distutils/command/wininst-6.exe
/usr/lib/python2.4/distutils/command/wininst-7.1.exe

[COLOR="Blue"]EDIT[/COLOR]: I sent en email to [email]python-help@python.org[/email] in hopes that someone can clarify this situation.

---

### Post by ardchoille42 on 2007-02-10
I's like to share an email I recieved from the Python Help centre:

> 
Dear Ian,

> Hello,

Hello!

> First of all, I love python and I thank the python developers for
> their work.

You and I both do. We're mostly not the core developers here, but
we're glad to help.

> Secondly, I would like to bring something to the attention of the
> python developers. It's mostly explained in this thread:

> [http://ubuntuforums.org/showthread.php?p=2136724](http://ubuntuforums.org/showthread.php?p=2136724)

> I have been told that this is a python issue. Has anyone checked
> this out? I don't want to cause undue alarm, but I felt this should
> be looked into.

Speaking only for myself, they're there but I have a hard time
imagining why they'd cause a problem. Here on my OS X laptop:

$ ls /usr/local/src/Python-2.5/Lib/distutils/command/wininst-*
/usr/local/src/Python-2.5/Lib/distutils/command/wininst-6.exe
/usr/local/src/Python-2.5/Lib/distutils/command/wininst-7.1.exe

$ file /usr/local/src/Python-2.5/Lib/distutils/command/wininst-*
/usr/local/src/Python-2.5/Lib/distutils/command/wininst-6.exe:
MS-DOS executable (EXE), OS/2 or MS Windows
/usr/local/src/Python-2.5/Lib/distutils/command/wininst-7.1.exe:
MS-DOS executable (EXE), OS/2 or MS Windows

They're part of distutils, which is documented at:

[http://docs.python.org/lib/module-distutils.html](http://docs.python.org/lib/module-distutils.html)

Distutuils is an answer to the question:

    I have written a nifty module for Python. How do I go about
    packaging it so that Python users on any platform can install
    it easily?

That's not an entirely trivial thing to do and distutils does a
pretty good job of making it easy to install modules other people
have written. Distutils can create various sorts of installers. Over
at:

[http://docs.python.org/dist/postinstallation-script.html](http://docs.python.org/dist/postinstallation-script.html)

it says:

    Executable installers are the natural format for binary
    distributions on Windows. They display a nice graphical user
    interface, display some information about the module distribution
    to be installed taken from the metadata in the setup script, let
    the user select a few options, and start or cancel the
    installation.

    [. . .]

    These installers can even be created on Unix or Mac OS platforms.

A look at the code suggests that those Windows executables are
"skeletons" that are used to create the Windows installers.

I'm as sure as I can be without testing it everywhere that they won't
run or do much of anything else on anything but a Windows machine.

Someone who knew that they never wanted to create a graphical
installer for Windows users could delete them. Of course, I don't
know how any particular package-management utility would react to
finding that some of the files it had installed had disappeared.

You're welcome to reproduce this answer anywhere you like as long as
it remains clear that I'm speaking for myself only.

Regards,
Matt


I won't worry about these files as they won't run on Linux and I am not connected to any Windows boxes. There doesn't appear to be any problem with them. 

Thanks goes out to the python folks for their quick and explanatory reply :)

---

### Post by deanlinkous on 2007-02-10
Great! Thanks for finding that out. Still kind of strange...creepy...weird IMO :D

---

### Post by russell.h on 2007-02-10
Thats impressive service. Thanks Matt!

---

### Post by ardchoille42 on 2007-02-11
> **deanlinkous said:**
> Great! Thanks for finding that out. Still kind of strange...creepy...weird IMO :D

I agree.

---

