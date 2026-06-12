---
title: "General question about installation procedures in Linux"
date: 2015-12-08
forum: General Help
---

### Post by franz.patz on 2015-12-08
Dear Community,

It's just my second post in this forum and the question deals with a very basic thing: Installation of software / packages in Linux (Ubuntu).

I read about package managers and the ways of installing software on the system (I also followed some discussions on whether to use apt-get, aptitude, synaptic, etc...) and found out that people suggest to stick to either apt-get or aptitude, but one obviously (in general) should not mix their usage.

So for the first steps, I chose apt-get but during experiments with the Ubuntu OS and trying out different things, It did not take long to have the problem that a software is not available in form of a recent version within the "apt-get system" (or it is not included there at all).
But hey, not only the source files but also some configuration file and all the necessary steps for building the software were documented, so I used the configure script and make && make install to get the software up and running. Of course (and I suppose that's no exception) some other packages stopped working because of some conflicts because of the newly installed software.

So I searched the web and was surprised that there is (in general) no easy way of undoing such a make install process unless you have tracked all the changes during the installation process. Ok, bad for me ;)
Then, I found the package "checkinstall". Well, It was too late but I will try to use this "tool" in the future. But now - finally - I come to the point and ask the questions:

1.) Is it a "common" way to use "checkinstall" instead of the plain make commands? If so, why do most of all tutorials found on the web NOT make use of it? Or is this not the standard way but then, how do you make sure a new installation does not brake some other package somewhere in the system if you have to install something from scratch?? I have the feeling that this is some lind of russian roulette?!
So the actual question is? How do you guys manage or maintain new  installations? Are you checking dependencies by hand before each  installation using "make install"? Seems like a nightmare...

2.)Many software installations (and even those for which packages exist and a simple "apt-get install xxx" does the rest for the user) obviously create files (setting, etc.) somewhere in the file system. I also read, that completely wiping a installed software is not even (necessarily) possible with the different usages of apt-get remove or apt-get purge. So this is a point which I can't really understand. Isn't THAT the purpose of using a package management system (or call it as you want ;) )? If you try out things and install many tools until you have found what you actually want you have already bloated the file system with stuff you don't need and cannot (unless you are a "PRO") get rid of it - then what's the point? I understand, that a package managment system hast nothing to do with my question 1.), since it cannot know what you are doing manually, but I use apt-get to setup some installation then I would expect that I can completely remove it again using again apt-get?
So the question is: Why does apt-get install not log ALL the files that are created during the installation process? Is it difficult to do so? What is your way of maintaining your system "free" from non-used stuff?

I somehow have the feeling of not having understood how to keep a Linux system running without creating package conflicts.....-frequently.... =) Maybe you can tell me something about it?

Thanks and best regards,
Franz

---

### Post by Bucky Ball on 2015-12-08
For packages installed from the repositories with apt-get, once you've removed/purged the package:

```
sudo apt-get autoremove
```

... should get rid of unwanted/unused, redundant dependencies. You can also use 

```
sudo apt-get autoclean
sudo apt-get clean
```

> I have the feeling that this is some lind of russian roulette?!

If you're make installing a package that hasn't been officially tested on your release from an untrusted third-party source you do so at your own risk, so yes, it is a bit like that dangerous parlour game. You can only really rely on the experiences of other users of that package as a gauge for whether you want to take the leap. Best to figure out how to uninstall a particular package before you install it, so you're doing the right thing asking here.

I avoid make installing and stick to officially tested stuff from the repos generally, but hopefully a third-party using Maverick can leap in and give more pertinent advice about make install stuff, but hope my contribution helps in some way. Good luck. :)

---

### Post by buzzingrobot on 2015-12-08
The configure/make/make install approach is a generic compilation method that very often needs to be adjusted. Sometimes the developer provides useful info in the source archive and sometimes the developer does not. Source code archives in Linux are not intended to be used as a program installation method.

Linux programs have dependencies on other components that must also be installed.  Those components have their own dependencies on other components, and so and so forth.  A dependency chain can be quite lengthy and complex.

Packages and package managers were invented to ease the extremely tedious and error prone burden of manually chasing down every dependency of the source archive you are trying to compile and install. (Dependencies are typically not identified in the source archive. You find out when the linker complains it can't find something.) Packages typically contain compiled code and scripts that execute and control the installation of that code.  A package manager implements that process and maintains a local database of every installed package. When you use the package manager via a tool like 'apt-get' (or the Software Center or Synaptic, etc.) it consults the software repositories your system is configured to use, determines the dependencies of the package you have asked it to install, determines which, if any, of those packages are already installed, and then offers to download and install the desired package and all of its remaining dependencies.

A package manager, then, completes in a few seconds a process that might easily take hours done manually (and more hours when a mistake is made).

That's the *big* advantage of relying on repositories of pre-compiled and vetted software packages rather than grabbing source archives from someplace on the net. Yes, very often the very latest versions are not in the repositories. But, unless a new version offers a new capability you need or fixes a bug you need to be fixed, the knee-jerk installation of the latest packages isn't likely to pay off. (If a new package release is dependent on versions of core Linux libraries that are newer than your distribution is built on, the package probably can't be made to run on your distribution.)

---

### Post by grahammechanical on 2015-12-08
> the question deals with a very basic thing: Installation of software / packages in Linux (Ubuntu).

Actually, your question is more to do with the compiling of software source code. And that is truly a basic way of installing software.

If the author of some software has packaged the software and followed the packaging guide lines when doing so, then installing a software package becomes much easier. If the software has been accepted into the software repositories of a Linux distribution then so much the better.

The advantage of using a GUI tool like the Software Centre is that it uses a database of all the available software in the repositories and knows the accurate package name. If we use a tool like apt-get and we do not type the package name accurately then apt-get will not be able to find the package.

So, in my opinion, if we are using the term "basic" and applying it to the user's understanding of how to install software, then I would say, use the Software Centre. Let us not give the impression that installing applications in Linux/Ubuntu (a basic task) is at all difficult. It can be so if we want to do it the hard way.

Regards.

---

### Post by mastablasta on 2015-12-08
you can search for PPA first. see if ti was already precompiled for Ubutnu. Many programs will offer information as to how to install it on most popular Linux distros. and in case of Ubuntu they give a link to their own PPA (you add their repository to sources so you can install it with apt-get or from software center) or a .deb file which is kind of like an exe in windows.

only if boths of these method fail or do not exists do we go compiling and then you need to carefully read the readme file. there might be a reason why the package is not included in Ubuntu or latest version of Ubuntu - e.g. it conflicts with other things

---

### Post by franz.patz on 2015-12-08
Thank you for the explanations!

What about "setting files", that are sometimes installed together with or as part of a package? Even if the package is removed via apt-get, why are those additional (often user setting) files not removed? Is there some way of logging every file that is created during installation of a package? I have seen that there is the apt-get log but it did not show all files that were somewhere placed on the file system.... it's a bit tedious to search for files that have been possibly created (especially if you don't know the typical places). For example, an eclipse install left files in "many" different locations but those places are well documented, so no problem here - but it was a pain for some other packages.


Because you mentioned it, a question regarding "[COLOR=#000000]software repositories your system is configured to use[/COLOR]": I know that the repositories that the package manager recognizes are listed in [COLOR=#333333][FONT=UbuntuMono]/etc/apt/sources.list 

[/FONT][/COLOR]Now: I have (graphically) made a cross in Ubuntu's Software Center to also show up updates/packages from 3rd parties. Where does the Software Center store those additional repository paths? The Software Center notified me about "Base" updates whereas a "sudo apt-get update upgrade" did not show any updates, so I suppose the Software Center does not make use of the sources.list file although it's just a "frontend" for apt-get?

Kind regards,
Franz

---

### Post by ian-weisser on 2015-12-08
> **franz.patz said:**
> Even if the package is removed via apt-get, why are those additional (often user setting) files not removed?
Safey and policy.
Settings files in /etc are removed by the package manager when you specify 'purge' instead of 'remove'
Files in your /home are never removed by the package manager under any circumstances - to protect you from unintentional data loss.
See [https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

> **franz.patz said:**
> Is there some way of logging every file that is created during installation of a package?
See man dpkg. Look for the -L flag.

> **franz.patz said:**
> Where does the Software Center store those additional repository paths?
It uses apt's source list: /etc/apt/sources.list AND /etc/apt/sources.list.d/

> **franz.patz said:**
> The Software Center notified me about "Base" updates whereas a "sudo apt-get update upgrade" did not show any updates
Depends upon the order you checked them in, and how much time elapsed between the two checks.
They use the same repositories, which update throughout the day and night.
Software Updater may show different updates than using apt directly due to Phased Updates, which is another repository-based system to protect users.

---

### Post by Bucky Ball on 2015-12-08
> **franz.patz said:**
> What about "setting files", that are sometimes installed together with or as part of a package? Even if the package is removed via apt-get, why are those additional (often user setting) files not removed? Is there some way of logging every file that is created during installation of a package? I have seen that there is the apt-get log but it did not show all files that were somewhere placed on the file system.... it's a bit tedious to search for files that have been possibly created (especially if you don't know the typical places). For example, an eclipse install left files in "many" different locations but those places are well documented, so no problem here - but it was a pain for some other packages.

You don't have to search for anything. A Windows flashback where if you install a program it is like a mushroom that drops spores and germinates all over the place and can never be completely removed. In Ubuntu you remove/purge the app, then, to triple check there is no fudge left, see the commands I gave in post #2:

```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

The first one is generally plenty and purging it before that is usually enough. Gone. You can check there is no trace in your home folder also (like a folder or file containing config data for the app). :)

Oddly enough, the only app I've ever had a problem eradicating was Wine which is used to run Windows programs in Ubuntu. There's a couple of others that are tricky to kill 100% that I've seen, but they'd be in the 1%.

---

### Post by franz.patz on 2015-12-09
Ok, I thinks that's all I wanted to know for now! ;) Thank you for the quick and detailed answers!

---

