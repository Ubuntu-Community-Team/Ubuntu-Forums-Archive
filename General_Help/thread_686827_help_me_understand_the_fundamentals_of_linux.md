---
title: "help me understand the fundamentals of linux"
date: 2008-02-03
forum: General Help
---

### Post by Cew27 on 2008-02-03
hello 
here a few questions that i hope when answered will help me understand linux further
1. why is installing programs with linux so hard, why doesn't every program install the same, in windows its simple, run the setup exe and the rest is done for you but on linux it is so much harder, you need to know terminal code 
2. why do most programs need plugins or codecs to run the most common file formats e.g. totem and the other media players 
3. why doesn't linux have one file format executable windows have exe macs have img 
 thanks i hope you can help me

---

### Post by overdrank on 2008-02-03
> **Cew27 said:**
> hello 
here a few questions that i hope when answered will help me understand linux further
1. why is installing programs with linux so hard, why doesn't every program install the same, in windows its simple, run the setup exe and the rest is done for you but on linux it is so much harder, you need to know terminal code 
2. why do most programs need plugins or codecs to run the most common file formats e.g. totem and the other media players 
3. why doesn't linux have one file format executable windows have exe macs have img 
 thanks i hope you can help me

Hi and 
1. you can use add and remove along with synaptic manager that is very easy to install.
2. for codecs and restricted formats that is legal.
3. Well there are several distros and some use rpm's, deb's, and tar. files so if you are using Ubuntu you would normally use a deb file. But sometimes you will want a app that is not offered in a deb then you will use a tar or bin. 
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Cew27 on 2008-02-03
to install many of my programs i have had to use terminal and compile the source, what is the point in compiling source

---

### Post by overdrank on 2008-02-03
> **Cew27 said:**
> to install many of my programs i have had to use terminal and compile the source, what is the point in compiling source

Well it is not in the repos or you are wanting the latest version.

---

### Post by Cew27 on 2008-02-03
i dont underdstand your post ? what are repos

---

### Post by overdrank on 2008-02-03
> **Cew27 said:**
> i dont underdstand your post ? what are repos

Hi and I apologize for the abbreviation, this link can explain it better than I
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) 
And this link has more info on file types
[https://help.ubuntu.com/community/SoftwarePackagingFormats](https://help.ubuntu.com/community/SoftwarePackagingFormats)

---

### Post by markharding557 on 2008-02-03
the ubuntu documentation site will give you instruction on many things you may need to do [https://help.ubuntu.com/]("https://help.ubuntu.com/")

---

### Post by geraldm on 2008-02-03
repos = repositories, the place or URL from where you are obtaining the code.

Linux began as a way to achieve compatibility with Unix.  When distributions were created, there were different and established organizations of the executables.  Source code is needed to assure that the target executable works well with the distribution. 
Plugins are a way of reducing the size of an executable, yet remaining adaptable to a wider variety of different formats.

Linux does not use the suffix of the program name to tell whether the file is an executable.
Linux is much more public, whereas ".exe" and ".img" are used by propriatery OS.

Gerald

---

### Post by Cew27 on 2008-02-03
im sorry im still confused althaugh i think i get it 
cab someone explain what a repo is in very simple terms, 
also i hardly ever see.deb files when i try install something

---

### Post by Deep fried ice-cream on 2008-02-03
A repository is a online sever that has lots of installers on it, when you try and install a linux program the comuter asks the sever for the installer, installs it, and gets rid of the installer to save space.

---

### Post by overdrank on 2008-02-03
> **Cew27 said:**
> im sorry im still confused althaugh i think i get it 
cab someone explain what a repo is in very simple terms, 
also i hardly ever see.deb files when i try install something

HI and in a nut shell it is where you download apps for your system. So if you are wanting to install a app then search add and remove and synaptic manager first. And the links posted have good information that may help you understand.

---

### Post by Cew27 on 2008-02-03
thank you all 
i just realised when in install im wheel synaptic searches online for applications, i though it searched my computer for files i downloaded haha 
just out of interest how to people get their software on the repository

---

### Post by B'man on 2008-02-04
I don't know any more than that quite a few people have to be using it, sorry.

Just wanted to add something to the discussion about compiling source code. Basically, because systems work in different ways (Win32 v's Win64 v's some types of Linux v's some other types of Linux v's Mac OS X v's Unix etc), apps for those systems need to be set up in different ways.

In Windows, most of the software you'll use is compiled for Win32. If you're using Windows x64, it has to run all those apps through a compatibility layer, and they run without the benefits of using a 64-bit system. That's not a good thing, but it's the result of Win32 being the main executable type of the last 10 years. But, essentially, in Windows you install an app that's already been compiled.

When installing software that's in a repository on Linux, you're basically doing the same thing. Things like .deb files are like installers for that version of Linux. The difference is that the software in the repos has been compiled for your version of Linux, so if you're running 64-bit, the software will have been compiled for 64-bit. Most of the software you'll use on Linux will be in the repos, so you can install it using either the terminal (*sudo apt-get install **app***) or a GUI like Synaptic or Adept. The rest you have to compile the source, which is nice and simple usually once you get used to it.

For software developers, they'd be crazy to compile every single variation and make them all available, so they'll usually make a couple of compiled versions available (Win32, RPM, Deb, for example), and provide the source code for all other purposes. The people running the repos use the source to compile the stuff you install from there, for example.

The nice thing about source anyway - other than that you can get versions that haven't been released yet - is that one source can be compiled for any system that the app works on. For example, if you're on Win x64 and only the Win32 version is available, use the source and compile your own Win64 version. Furthermore, with the source you can modify the app itself to suit your needs if you want.

---

### Post by manimal347 on 2008-02-04
Linux is so different because it's based off Unix, a multi=-user operating system that was designed starting in the early 1970's for academic and research purposes. It was never meant to be a Windows replacement; in fact, the GUI you use is grafted onto it very much like how Windows 3.1 sat on top of DOS, and while it can do some things on its own, both make lots of calls to the Linux (or DOS) guts to do tasks with files, permissions, accessing hardware, etc. 

One could say Unix has a special philosophy, one Ubuntu doesn't hew very close to, but that is impossible to shield users from, as many of the components of Ubuntu were designed according to it. The philosophy emphasizes the hacker spirit, and expects users to WANT top know the gory details of their computers, if nothing else for the sake of knowing. Generally, Unix culture is one of self-reliancy, hence why people who fail to check a manual page first (EX: man pico) get told to RTFM and STFW, or as Thomas Bowldler would put it, search the darn web and read the darn manual. 

Understanding some Unix history and lore will make clear why your Ubuntu CD doesn't feel polished and simple like Windows, and also remind you that compared to most Linux distributions, it does darn nigh everything for you. Seriously, people used to joke that running Linux was like building a car from scratch using free junkyard parts, hence why so few people used it despite the agreeable price tag. There's still some truth to this, especially for people who rough it with Arch and Slackware, or perhaps Debian Unstable base-install.

Read this link:
[http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy)
If you find yourself giggling or grok what's being said, you'll take to Linux like a fish to water.

---

### Post by DrMega on 2008-02-04
> **Cew27 said:**
> hello 
here a few questions that i hope when answered will help me understand linux further
1. why is installing programs with linux so hard, why doesn't every program install the same, in windows its simple, run the setup exe and the rest is done for you but on linux it is so much harder, you need to know terminal code 
2. why do most programs need plugins or codecs to run the most common file formats e.g. totem and the other media players 
3. why doesn't linux have one file format executable windows have exe macs have img 
 thanks i hope you can help me

I for one could not be bothered with Linux if it was that difficult. Certainly some distros are, but there are a few that are starting to really stand out, Ubuntu being one of them. Here's my attempt to answer your questions:

1. You can get stuff to suit just about all your software needs from Synaptic, just tick the boxes and say apply. In my opinion this is far easier than Windows as you don't have to download the setup, run it, answer a million questions etc. If the package you want is not in Synaptic, often nowadays there is a setup script or very simple instructions. Only as a last resort do you need to compile from source.

2. Some file formats are a proprietary standard, and because different countries have different laws about third parties writing codecs for their standards, it is easier and safer to leave them out. In Ubuntu 7.10 (Gutsy) there is a package in Synaptic that installs most of your codecs for you. Look for "ubuntu-restricted-extras".

3. Windows has EXE, MSI, BAT, CMD, all of which are directly executable. Furthermore, if you have any programming tools installed that it will happily launch any number of other formats as executable, by their file associations.

---

### Post by manimal347 on 2008-02-04
> **Cew27 said:**
> thank you all 
i just realised when in install im wheel synaptic searches online for applications, i though it searched my computer for files i downloaded haha 
just out of interest how to people get their software on the repository

Oh, how they get it on the repository? They download a source tarball (UNIX archive) from whoever originally made the program, then compile it on their computer and package it into .deb format. The .deb stands for Debian, which is what Ubuntu was forked (derived) from. Then, they upload it to a server, whereby it goes through successive quality-control tests by unpaid community members. If the program is good enough, it enters the repository, and if it poses no legal threats, it enters the main distribution. Ask someone else to fill in the details on Ubuntu packaging... is it really just Debian Testing packages with Ubuntu an quality control layer added?

Read this:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by Cew27 on 2008-02-04
thank you for all your reply's 
is there anyway of compiling source into a deb so i can use it later without having to recompile all the components
for example the applets and software for my g15 keyboard i had to compile 4 programs 1 of which was g15daemon, could i compile all the code  into deb files (easily) so that when it comes to re-installation i can just unpackage the deb files ? 
also are all linux distro's the same configuration for example could i go get a distro that used rpm files and run it just as i would with ubuntu (obviously not using apt get install)
and what distribution uses rpm (the best one) as i would like to get familiar with all of the popular distro's 
 i would like to go to uni and study programming probably java but i was also thinking about unix, will it be usefull when looking for a job and what jobs could i get with it ? 
i really do appreciate you input thanks for replying :)

---

### Post by Cew27 on 2008-02-04
another question 
what are the differences between 
gutsy gibbon 
fiesty fawn 
and efty eft ? 
i have also thanked all of you for your input

---

### Post by B'man on 2008-02-04
Gutsy Gibbon, Feisty Fawn etc are the code names of the different version numbers of Ubuntu. v7.04 is Feisty, v7.10 is Gutsy etc. They go up in alphabetical order, so the next one will start with H (Hardy Heron) and the one after that will start with I. The "version number" is just the year and month of release (e.g. 7.04 is April '07).

Creating deb files is a bit long winded. See [this topic](http://ubuntuforums.org/showthread.php?t=51003).

Linux distros work in different ways. Some RPM packages will work on Debian (including Ubuntu) systems, others won't. You'd need an RPM manager as well, such as rpm or yum. All the Linux distros have the same basic workings, but they'll do things like handle services differently, put config files and apps in different places, etc.

The branch of Linux that uses RPM is Red Hat. This includes Red Hat Enterprise Linux (RHEL) and CentOS.

---

### Post by Cew27 on 2008-02-04
thanks 
so all the code names are just updated version i thaugh that efty was kde and fiesty knome ect

---

### Post by B'man on 2008-02-04
Nope, that's handled by the OS name itself. Ubuntu is Gnome, Kubuntu is KDE, Xubuntu is XFCE. Edubuntu is GNOME with educational software and stuff for things like school networking.

They can all switch between each other though, by installing the *-desktop packages for another OS. Example: you can give Kubuntu functionality to an Ubuntu install by installing the kubuntu-desktop package set.

---

### Post by Cew27 on 2008-02-04
ahh thanks for clearing that up

---

### Post by Kegusa on 2008-02-04
Just popping in into this for me very interesting discussion, and an excellent question from Cew27. Thanks for asking it so others can read and learn. Just started using Ubuntu myself  about a week ago and still digging into the world of Linux and loving it! 

Will ask some questions here later if I cant figure them out myself in time :)

---

### Post by Cew27 on 2008-02-04
good i will no doubt have some more questions but for now i am content

---

### Post by Zwack on 2008-02-04
One question was originally about executable formats, although that probably wan't the intent.

Most executables in Linux are in one format ELF.  Some additional "executables" are just interpreted scripts (like .bat files on DOS)... these can be interpreted by lots of different languages (python, BASH, KSH, Perl, ....) 

As for installers in the past Unix had most code distributed as source code, but packages have become more common.  There are two major package formats for Linux, deb and rpm (although there are others).  In the past DOS/Windows didn't have the one installer format, they had hundreds.  Some things came as zip files, others were rar files, some had setup scripts, some didn't...  In short, the conventions didn't exist in the Windows world.  Now there is a standard but some setup programs use MSI, some older ones don't... 

Z.

---

