---
title: "How to handle obsolete dependencies/packages?"
date: 2015-11-04
forum: General Help
---

### Post by fkervin on 2015-11-04
Hi All,

I'm suffering a problem that I 'm sure many people find when decide to move to a newer version of Ubuntu: I'm unable to install programs I used before, and the problem is that they ask for dependencies/packages that are no more available because of they have been replaced by newer versions.

To be exact, when moving from ubuntu 14.04 to 15.10 I've found I cant install some programs becouse they ask for thoses packages:

-**libavcodec54**, but it's not installable on 14.10 since has been replaced by... libavcoded-ffmpeg56 perhaps?
-**libavcodec-extra54** , but it's not installable on 14.10 since has been replaced by... livavcodec-extra perhaps?
-**libicu52**, but it's not installable on 14.10 since has been replaced by libicu55
-**libboost-filesystem1.54.0**, but it's not installable on 14.10 since has been replaced by libboost-filesystem1.58.0

What is the procedure on those cases? I can't believe that those programs can't be installed by some workaround.

Many thanks in advance

Regards

---

### Post by ajgreeny on 2015-11-04
Let's see an example of one or two of those programs that you want to install but can not, because of missing dependencies.  Are they from the standard repos, or maybe from outside sources or PPA repos which have still to catch up with 15.10?

---

### Post by fkervin on 2015-11-04
Many thanks for your answer, ajgreeny,

OpenTTD appears as available for trusty, when try to install requires libicu52 (>=52~m1-1~)

[https://www.openttd.org/en/download-stable](https://www.openttd.org/en/download-stable)

Emulation Station requires libboost-filesystem1.54.0:

[http://emulationstation.org/#download](http://emulationstation.org/#download)

Ultrastar Deluxe 1.1.o requires: libacodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>=6:9.13)

I have not the link to ultrastar deluxe, sorry, I stored the .deb quite ago.

I'd like to solve those problems, but more than this, I want to learn que procedure in way I can fix by myself in the future.

Regards

---

### Post by ajgreeny on 2015-11-04
Ah.  So these are .deb files downloaded from sources other than the usual repos, or even PPA repos, which do not generally have any dependency issues.

I note the emulation station download is for debian, not ubuntu and that may be a difficulty, in the same way that we can not install most applications direct from the debian repos without similar problems occurring.  Also openttd is for 14.04 not 15.10, and that is very often a cause of dependency problems even between the official ubuntu repos for the different ubuntu versions.

Not sure I can help any further, I'm afraid.  Have you tried contact with developers, or forums, for those problem applications?

---

### Post by fkervin on 2015-11-04
As always, MANY THANKS for your answer, ajgreeny,

My question was in the direction of cheating the installer in some way it would see installed those packages. I mean, make the system "offer" libboost-filesystem1.58.0 to the .deb when it ask for the older version, making a copy of it or something.

If you, who are a guru of this, say that what i'm asking for is nearly impossible to do, I'm afraid I'll have to surrender :(.

I asked on Emulation Station forum and had no reply, I'll try in Open TTD. But the truth is that the most important for me was ultrastar deluxe, I'll look for a newer version, but I have no much faith.

Regards and thanks again

---

### Post by grahammechanical on 2015-11-04
We are often the authors of our own misfortune. I cannot find fault with a software developer who only packages his software for LTS version of Ubunu. I cannot find fault with the designers of a software package management system that prevents the OS from breaking by not allowing the installation of old libraries over newer libraires. 

If you have the hardware capable of running a VM you could install 14.04 in KVM. I have found that Linux Containers have lower hardware requirements than KVM. So, you might want to look at using 14.04 in an LXC/LXD container. There is a session on Inroducing LXD on tomorrow's Ubuntu Online Summit. The sessions are recorded so we can watch at any time.

I have done a little bit of experimentation with Linux Containers (LXC) and they are fast.

[http://summit.ubuntu.com/uos-1511/2015-11-05/](http://summit.ubuntu.com/uos-1511/2015-11-05/)

Regards.

---

### Post by ian-weisser on 2015-11-04
That's not a good idea.
Deb packages aren't merely 'containers of software'. They include versioning information for all their dependencies. The software *uses* features in the correct version.
You are deliberately introducing *version conflicts* into your system when you add some non-Ubuntu software, and that can cause all sorts of terrible breakage.
You are risking total system failure when you consider trying to 'cheat' the package manager.

---

### Post by fkervin on 2015-11-04
Manu thanks again! :)

Well, I'll try to live without those programs, the truth is that running a virtual machine for this is not an usable idea for my needs, and of course, I don't want to broke the system, ian-weisser

If you tell me that there is no *real* solution for this, it's OK, I asked thinking that some workaround could be made.

Regards
Regards

---

### Post by ian-weisser on 2015-11-04
It's always possible to use multiple VMs. One VM for Ubuntu, another VM for Debian, yet another VM for some legacy version of a game that runs only on older Ubuntu, etc.
That's not cheating - it's what VMs are intended for....

---

### Post by SeijiSensei on 2015-11-04
One alternative is to compile the programs from source code yourself.  I used to compile mplayer from source by using
```

sudo apt-get install build-essential
sudo apt-get build-dep mplayer

```
then downloading the source code "tarball" from the developers' site. The first installs the gcc compiler and other tools.  You need only do that once.  The second installs the required libraries and other dependencies that the program requires.  This may or may not work for you.  If you have never compiled anything from source code before, I suggest you start by reading this: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Usually when the appropriate tools and supporting libraries and headers are installed, you can compile a well-behaved program just by running the sequence
```

./configure
make
make install

```
in the top-level directory of the source code tree. The standard is to install self-compiled programs under /usr/local/, so a compiled version of mplayer would be written to /usr/local/bin/mplayer.  Your default path is set up so that the OS will look in /usr/local ahead of /usr:
```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```
That way it will use the self-compiled version even if there is a program with the same name that came with your distribution and is stored in /usr/bin or /usr/sbin.

---

### Post by tgalati4 on 2015-11-05
I have had luck running multiple versions of some libraries to run older software.  You need to simple copy the older libraries to the correct locations.  These older libraries will not show up in the apt system, and other than take up disk space, they generally won't harm other programs.  

Now, it is possible that running older software will just not work on a newer Desktop, because of changes in frameworks.  You won't know until you try it, and you won't get much support because nobody else is running your configuration.

Because this is a general help forum, I won't list specific procedures, but it can be done.

But asking the developer to provide a deb package for 14.10 is reasonable, but understand that it takes hours of work to recompile from scratch and fix things that are broken when moving to 14.10.  That is one reason to stick to LTS releases.  Developers tend to target them so they don't have to maintain too many versions of their software.

---

