---
title: "lots of questions about dell, ubuntu, and linux in general"
date: 2007-10-09
forum: General Help
---

### Post by gamelord12 on 2007-10-09
1a) I plan on getting a laptop soon as it seems like it would make my computer science classes in the future infinitely easier.  Do I have to get the Dell laptops that come with Ubuntu or can I just install it off of a downloaded disc?

1b) Are there drivers that I could download for any Dell laptop to make it work with Ubuntu?  Like one with a pretty decent nVidia GeForce graphics card?

2) If I for some crazy reason decided to go back to a dual-boot environment on my desktop, is there any way to bypass the X-Fi sound card and use the integrated sound on my Asus A8N-SLI motherboard, since X-Fi won't work on Linux?

3) How good of a graphics card would I need to run Beryl or Compiz-Fusion with no problems whatsoever?

4) How much RAM would I need?  I would be using instant-search indexing, Beryl or Compiz Fusion, OpenOffice software of some kind, instant messaging, and a music player at any given time.  So, it comes down to 1 or 2 GB?  I'd also be doing some Java programming/compiling on this thing, which leads me to my next question...

5) How the heck do I install Java?!  I've got the binary file, but I have no clue how to use it (Virtual Box Ubuntu).

6) What is the rhyme and reason to how the files are organized?  If you guys could throw a link at me that explains it, it would be nice.  For instance, I know that the system files for Windows go in the C:\Windows directory, files associated with your installed programs go in the C:\Program Files directory, etc.

7) I want to see if I have a good understanding of desktop environments: if I had no actual distro, could I just install the kernel, then install a desktop environment on top of it?  Or would I have to somehow join the desktop environment to the kernel before I could do ANYTHING?  For instance, once I installed a dekstop environment, I could never just switch from GNOME to KDE?

8) What desktop environment is better for what purposes?  What are the pros and cons of each?  Which one makes everything pretty?  Do any of them have transparent windows and a flip3D-like feature like Windows Vista Home Premium and higher?

I'm really getting into the free software movement here.  If it weren't for the fact that I'm a serious gamer, I'd be all for ditching even Windows.  However, games aren't all made to natively run in Linux, causing problems and such.  As a pure work machine though, Linux would be fine for my needs though, which is why I'd like to get it on my upcoming laptop.  Thanks in advance for answering these questions to the best of your ability!

---

### Post by Digitallysick on 2007-10-09
1a) I plan on getting a laptop soon as it seems like it would make my computer science classes in the future infinitely easier. Do I have to get the Dell laptops that come with Ubuntu or can I just install it off of a downloaded disc?

You can use any laptop, but the dells that come with ubuntu are cheap, but its your choice, might just want to double check the hardware on the laptop you get to make sure it works (im 90% most of it will) except some obscure things)

1b) Are there drivers that I could download for any Dell laptop to make it work with Ubuntu? Like one with a pretty decent nVidia GeForce graphics card?

I would say that any modern laptop should run it with no problem, nvidia seems better to me at the moment (your choice) The "drivers" you can get from add/remove in ubuntu its as easy point and click

2) If I for some crazy reason decided to go back to a dual-boot environment on my desktop, is there any way to bypass the X-Fi sound card and use the integrated sound on my Asus A8N-SLI motherboard, since X-Fi won't work on Linux?

Sure thing, just select the sound you want to use in linux, if X-fi isn't supported, than your motherboards onboard sound probably is for sure. 

3) How good of a graphics card would I need to run Beryl or Compiz-Fusion with no problems whatsoever? 

see above

4) How much RAM would I need? I would be using instant-search indexing, Beryl or Compiz Fusion, OpenOffice software of some kind, instant messaging, and a music player at any given time. So, it comes down to 1 or 2 GB? I'd also be doing some Java programming/compiling on this thing, which leads me to my next question...

1gb should be plenty, but the more the better for any os

5) How the heck do I install Java?! I've got the binary file, but I have no clue how to use it (Virtual Box Ubuntu).

Its in add/remove , just click and install

6) What is the rhyme and reason to how the files are organized? If you guys could throw a link at me that explains it, it would be nice. For instance, I know that the system files for Windows go in the C:\Windows directory, files associated with your installed programs go in the C:\Program Files directory, etc.

Most of everything installs to /usr/bin think of it as C;\Program Files, and for My Documents = Home

7) I want to see if I have a good understanding of desktop environments: if I had no actual distro, could I just install the kernel, then install a desktop environment on top of it? Or would I have to somehow join the desktop environment to the kernel before I could do ANYTHING? For instance, once I installed a dekstop environment, I could never just switch from GNOME to KDE?

Sure you can get ubuntu with gnome (straight from the site) and then add kde, fluxbox, xfce, your choice and switch between them if you like

What desktop environment is better for what purposes? What are the pros and cons of each? Which one makes everything pretty? Do any of them have transparent windows and a flip3D-like feature like Windows Vista Home Premium and higher?

Compiz Fusion has that option for the flip 3d, the window manager is up to you, start out with gnome probably, and then try kde next

---

### Post by p_quarles on 2007-10-09
> **gamelord12 said:**
> 1a) I plan on getting a laptop soon as it seems like it would make my computer science classes in the future infinitely easier.  Do I have to get the Dell laptops that come with Ubuntu or can I just install it off of a downloaded disc?
It will make your computer science classes easier -- unless you have assignments involving Visual Studio, C# or ASP.NET, which is fairly likely. You may want to dual-boot.

The Dell laptops (or System76 laptops) are good choices, because you *know* they will work with Linux. If you don't want to go that route, the main thing to look for is a wireless adapter that is supported by the kernel or the restricted modules. It's a pretty big hassle to get a Windows driver working.

> 1b) Are there drivers that I could download for any Dell laptop to make it work with Ubuntu?  Like one with a pretty decent nVidia GeForce graphics card?
Depends on the hardware. nVidia has good support, as do Intel products (graphics, wireless, etc.). 

> 2) If I for some crazy reason decided to go back to a dual-boot environment on my desktop, is there any way to bypass the X-Fi sound card and use the integrated sound on my Asus A8N-SLI motherboard, since X-Fi won't work on Linux?
Someone else will have to answer this one. 

> 3) How good of a graphics card would I need to run Beryl or Compiz-Fusion with no problems whatsoever?
Those programs don't require resources as much as they require compatibility. Intel and (older) nVidia cards are your best bet. "No problems" is unlikely, though, as both programs are still in Beta. 

> 4) How much RAM would I need?  I would be using instant-search indexing, Beryl or Compiz Fusion, OpenOffice software of some kind, instant messaging, and a music player at any given time.  So, it comes down to 1 or 2 GB?  I'd also be doing some Java programming/compiling on this thing, which leads me to my next question...
You'll be fine with 512 MB of RAM, but more is always better. 

> 5) How the heck do I install Java?!  I've got the binary file, but I have no clue how to use it (Virtual Box Ubuntu).
Use Synaptic to search for it and then install it. No need to download anything from any web sites.

> 6) What is the rhyme and reason to how the files are organized?  If you guys could throw a link at me that explains it, it would be nice.  For instance, I know that the system files for Windows go in the C:\Windows directory, files associated with your installed programs go in the C:\Program Files directory, etc.
Executables are stored in /bin , /sbin , and in various subdirectories with the same names.

Filesystems that aren't part of the basic system are usually stored in /media

System startup and other functionality settings are in /etc

Logs and other "variable" files are in /var

User-specific settings (as well as icons) are in /usr

> 7) I want to see if I have a good understanding of desktop environments: if I had no actual distro, could I just install the kernel, then install a desktop environment on top of it?  Or would I have to somehow join the desktop environment to the kernel before I could do ANYTHING?  For instance, once I installed a dekstop environment, I could never just switch from GNOME to KDE?

8) What desktop environment is better for what purposes?  What are the pros and cons of each?  Which one makes everything pretty?  Do any of them have transparent windows and a flip3D-like feature like Windows Vista Home Premium and higher?
This is a matter of preference. Both are completely customizable. Also, you can install them both, and choose which one you want to use at login by clicking on the "session" menu.

---

### Post by gamelord12 on 2007-10-09
Could you elaborate more on the directories?  What "other functions" and other file systems?

A few more questions:

Does Ubuntu support writing to NTFS-formatted devices (I'm not sure if flash drives are formatted in NTFS or not by default in Windows)?  What makes it able to read or write to other kinds of file systems?

Is it safe to say that most laptops will run Linux without any problems?

Even though Java is covered by the package manager, wouldn't it be helpful to know how to do it myself as well?

---

### Post by p_quarles on 2007-10-09
> **gamelord12 said:**
> Could you elaborate more on the directories?  What "other functions" and other file systems?
There's too much for any of us volunteers to fully explain. If I had a link, I'd provide it, but I'd suggest just looking through all the directories and seeing what's there. 

> Does Ubuntu support writing to NTFS-formatted devices (I'm not sure if flash drives are formatted in NTFS or not by default in Windows)?  What makes it able to read or write to other kinds of file systems?
It does, but it can buggy sometimes. Look for the package "ntfs-3g" in the package manager and you'll be able to configure it. 

Flash drives are usually FAT-32, since this system is supported by all Windows and most Mac systems. 

> Is it safe to say that most laptops will run Linux without any problems?
That's not what I said! There are huge problems with proprietary wireless drivers, and if you get one that isn't supported you'll regret it. 

> Even though Java is covered by the package manager, wouldn't it be helpful to know how to do it myself as well?
That's your choice.

---

### Post by steveneddy on 2007-10-09
> **gamelord12 said:**
> 1a) I plan on getting a laptop soon as it seems like it would make my computer science classes in the future infinitely easier.  Do I have to get the Dell laptops that come with Ubuntu or can I just install it off of a downloaded disc?

1b) Are there drivers that I could download for any Dell laptop to make it work with Ubuntu?  Like one with a pretty decent nVidia GeForce graphics card?

2) If I for some crazy reason decided to go back to a dual-boot environment on my desktop, is there any way to bypass the X-Fi sound card and use the integrated sound on my Asus A8N-SLI motherboard, since X-Fi won't work on Linux?

3) How good of a graphics card would I need to run Beryl or Compiz-Fusion with no problems whatsoever?

4) How much RAM would I need?  I would be using instant-search indexing, Beryl or Compiz Fusion, OpenOffice software of some kind, instant messaging, and a music player at any given time.  So, it comes down to 1 or 2 GB?  I'd also be doing some Java programming/compiling on this thing, which leads me to my next question...

5) How the heck do I install Java?!  I've got the binary file, but I have no clue how to use it (Virtual Box Ubuntu).

6) What is the rhyme and reason to how the files are organized?  If you guys could throw a link at me that explains it, it would be nice.  For instance, I know that the system files for Windows go in the C:\Windows directory, files associated with your installed programs go in the C:\Program Files directory, etc.

7) I want to see if I have a good understanding of desktop environments: if I had no actual distro, could I just install the kernel, then install a desktop environment on top of it?  Or would I have to somehow join the desktop environment to the kernel before I could do ANYTHING?  For instance, once I installed a dekstop environment, I could never just switch from GNOME to KDE?

8) What desktop environment is better for what purposes?  What are the pros and cons of each?  Which one makes everything pretty?  Do any of them have transparent windows and a flip3D-like feature like Windows Vista Home Premium and higher?

I'm really getting into the free software movement here.  If it weren't for the fact that I'm a serious gamer, I'd be all for ditching even Windows.  However, games aren't all made to natively run in Linux, causing problems and such.  As a pure work machine though, Linux would be fine for my needs though, which is why I'd like to get it on my upcoming laptop.  Thanks in advance for answering these questions to the best of your ability!

1a) cool - no - yes

1b) yes - yes

2) yes

3) Intel video on the MB seem to be running CF now a days - the more you can afford, the better the CF experiance, and watching movies is good on a good card, too

4) 1 Gig is good, 2 is better

5) don't know - search the forums - it's in there, I promise

6) [URL="http://www.freeos.com/articles/3102/"]look here
[/URL]

7) yes - yes - you can install both and at login, choose which one you want to boot into - it's easy

8) You will just have to use them and decide what you like best - Gnome with compiz-Fision has flipping pages.

Linux desktops - Gnome, KDE, Fluxbox, XFCE, Enlightenment, and many, many more.

Have fun.

:popcorn:

EDIT - look at [www.system76.com/](www.system76.com/)

---

### Post by gamelord12 on 2007-10-09
Well...how would I go about installing Java without the package manager?  Would it require the command line?  Do most programs require the command line to install if you don't use the package manager?  How would you avoid using the command line to install programs if they're not covered by the package manager?

And it looks like I'll just go for that Dell laptop pre-configured with Ubuntu.

---

### Post by virtuallinux on 2007-10-09
> 
1a) I plan on getting a laptop soon as it seems like it would make my computer science classes in the future infinitely easier. Do I have to get the Dell laptops that come with Ubuntu or can I just install it off of a downloaded disc?


Either option will work.  The options on Dell's Ubuntu laptops are somewhat limited.  I have a Dell Latitude D820 which I got with XP, but installing Ubuntu on another partition was pretty easy.  I definitely recommend going dual boot, because there are often times when I am forced to use Windows for something.

> 
1b) Are there drivers that I could download for any Dell laptop to make it work with Ubuntu? Like one with a pretty decent nVidia GeForce graphics card?


In general, Nvidia and Linux get along pretty well.  I have an Nvidia Quadros NVS 120M graphics card, and the restricted drivers in Ubuntu seem to be working pretty well.  The best part about the Nvidia drivers in Linux is the display management utility, which provides an easy to use interface for customizing your display settings (no direct editing of config files); you can run this by typing:
```

gksudo nvidia-settings

``` 
into the command line.

> 
2) If I for some crazy reason decided to go back to a dual-boot environment on my desktop, is there any way to bypass the X-Fi sound card and use the integrated sound on my Asus A8N-SLI motherboard, since X-Fi won't work on Linux?

3) How good of a graphics card would I need to run Beryl or Compiz-Fusion with no problems whatsoever?


Not my areas of expertise, sorry.

> 
4) How much RAM would I need? I would be using instant-search indexing, Beryl or Compiz Fusion, OpenOffice software of some kind, instant messaging, and a music player at any given time. So, it comes down to 1 or 2 GB? I'd also be doing some Java programming/compiling on this thing, which leads me to my next question...


1GB should be plenty, for both XP and Ubuntu (I really do recommend going dual boot); but if you can afford 2GB, then go for it. The more the merrier.

> 
5) How the heck do I install Java?! I've got the binary file, but I have no clue how to use it (Virtual Box Ubuntu).


Not real familiar with Java, but the easiest way to add apps is through Add/Remove.  I've found an IDE that I like called Geany.  As far as coding in Linux, keep in mind that Linux handles executables differently than Windows.

> 
6) What is the rhyme and reason to how the files are organized? If you guys could throw a link at me that explains it, it would be nice. For instance, I know that the system files for Windows go in the C:\Windows directory, files associated with your installed programs go in the C:\Program Files directory, etc.

7) I want to see if I have a good understanding of desktop environments: if I had no actual distro, could I just install the kernel, then install a desktop environment on top of it? Or would I have to somehow join the desktop environment to the kernel before I could do ANYTHING? For instance, once I installed a dekstop environment, I could never just switch from GNOME to KDE?

What desktop environment is better for what purposes? What are the pros and cons of each? Which one makes everything pretty? Do any of them have transparent windows and a flip3D-like feature like Windows Vista Home Premium and higher?


Not extremely well versed in these areas either.

One other thing to consider is wireless, which generally doesn't get along well with Linux.  I'm fortunate enough to have an Intel 3945 wireless card, for which there are restricted drivers.  I just told Ubuntu to use the restricted drivers, so I never had to mess with using and api wrapper for the windows drivers.  If at all possible, go for the Intel wireless card.

---

### Post by p_quarles on 2007-10-09
> **gamelord12 said:**
> Well...how would I go about installing Java without the package manager?  Would it require the command line?  Do most programs require the command line to install if you don't use the package manager?  How would you avoid using the command line to install programs if they're not covered by the package manager?
Java is proprietary software, which means that you can't compile it from the source code. Because of this, using the package manager is the best way to get it.

If you want to use the command line:
```
sudo apt-get install sun-java5-jre
```

---

### Post by steveneddy on 2007-10-09
I just saw [this post]("http://ubuntuforums.org/showthread.php?t=558623") about X-Fi.

---

### Post by gamelord12 on 2007-10-10
You guys keep recommending that I dual-boot, but I already have a powerful desktop for running Windows.  My CS classes won't be using any OS exclusively; it's just the department policy.  They cover every OS that a student would possibly want to use.

---

### Post by Digitallysick on 2007-10-10
install ubuntu then =)  if you have a 64bit processor then get the 64bit version and try it out

---

