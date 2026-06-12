---
title: "Linux--Ubuntu tricks."
date: 2008-04-12
forum: General Help
---

### Post by kaginken on 2008-04-12
You cannot open/use/doanythingwith .exe files in Linux.  .exe is strictly a Winblows file extension.  In Linux, it will be .bin or .tar, etc.

I would recommend you find yourself a good tutorial or two online.  That's very helpful, as well as posting your questions here.  You definitely picked the best Linux distro for yourself as Ubuntu is very well supported  -  that's how I got into Linux.  Be patient and you will be well rewarded.  :)

---

### Post by jakupl on 2008-04-12
1. depends on what it is... windows apps? if they are, then install wine.
in terminal:

```
sudo apt-get install wine
```

2. to open the file browser with super user rights, enter in terminal:


#######################################################
THIS IS VERY DANGUROUS!!!! BEWARE OF WHAT YOU DO WHEN IN SUPER USER MODE
#######################################################
```
gksudo nautilus
```

---

### Post by tango_ninja on 2008-04-12
Hi, welcome to the forums :)

well, for starters.....  .exe files are M$ executables, they serve no purpse in Ubuntu. programs in ubuntu can be instaled from the command line, or in synaptic package manager.

sofware in ubuntu is managed by repositories (synaptic package mgr). you can also download software from the web in either  .deb   or .rpm  formats.

hope this helps out....sounds like you've got your work cut out for you !

---

### Post by ibuclaw on 2008-04-12
1) OK, if someone hasn't already beaten me to saying, Linux **does not have native binary compatibility** with Windows .exe files. So if you are trying to install your favourite Windows applications, then you may have your foot in your mouth on trying that.

Though, that said. There is a Windows Compatibility Layer Engine called WINE (Wine Is Not an Emulator).
Best thing is that you don't need to go searching round the internet for it either!
Binary based Linux Distributions, such as Ubuntu have what we call a repository that contains 95% of all **Linux** software that we will ever need.
To obtain WINE, go into "Applications>Add or Remove Software" in the gnome menu. Search for "WINE" and mark it for installation. Then, click apply, and Ubuntu will download, install and configure the application without you needing to do anything.

And a new Slot in your menu bar will appear after it is installed too. "Applications>Wine"
Try running Notepad to start with, it'll take about 5 seconds the first time, as Wine copies it's link libraries to your home folder.

Now, before you go off clicking all Windows files, don't get your hopes up high, as WINE is not 100% compatible with Windows Binaries. So there is a 75% chance that it won't work.


2) All Linux binaries may be owned to root, but you don't need to be root to execute them!
This is a safety feature in all Linux and UNIX systems alike, made so so you can't go off and delete all the files that you like at your own will. Unlike Windows for example.

You do, however, still have execute and reading permissions of the Linux Binaries in you /usr/bin folder.
Though, you will never have to run these binaries by double clicking them. As most are command line apps, or apps that require commandline arguments to start it.

And before we go down the road of being root. One word of warning:
```
You must never, **never**, **NEVER** be root!
That is **Especially** when in GUI mode.
```
To have unlimited write permissions to the whole of your filesystem is a complete and utter security risk. Never do it! Ever!

3) With your last point of downloaded Linux "exe" files. Well, I hate to break it to you, but they aren't Linux Compatible. As Linux Binaries **never have the suffix ".exe"**
Clamwin is a **Windows App.**
ClamAV is probably what you want to look for.
That is availiable in the Ubuntu Repository.
Again, if you search it in "Applications>Add or Remove Software", you will find it there.

And as a last note. I advice that you **never go off to random sites to download apps for Linux**.
That is just not the way to do it. Especially binaries, you just don't know what you are running!

First thing that I advice is getting used to the repositories, and shaking off the Windowsy ".exe" format as being a way to run programs, because it natively isn't.

Now I'll on the word that there is another way to access it your sofftware repository.
Open up "System>Administration>Synaptic" and you'll have the full list of applications at your disposal.

Regards
Iain

---

### Post by oldos2er on 2008-04-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

