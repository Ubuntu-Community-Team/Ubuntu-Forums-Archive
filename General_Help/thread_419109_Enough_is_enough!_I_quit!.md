---
title: "Enough is enough! I quit!"
date: 2007-04-22
forum: General Help
---

### Post by thebluejay on 2007-04-22
That's it. I did my best, but I'm just so damned tired of getting stupid results like this:

[COLOR="DarkRed"]checking for BRASERO... configure: error: Package requirements (        glib-2.0 >= 2.6.0                       gdk-2.0 >= 2.6.0                gtk+-2.0 >= 2.10.0                      libgnome-2.0 >= 2.10.0          libgnomeui-2.0 >= 2.10.gnome-vfs-2.0 >= 2.14.2          gnome-vfs-module-2.0    libnautilus-burn >= 2.16.0      gstreamer-0.10 >= 0.10.6        gstreamer-plugins-base-0.10 >= 0.10.0  libxml-2.0 >= 2.6.0) were not met:

Requested 'gtk+-2.0 >= 2.10.0' but version of GTK+ is 2.8.20
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libnautilus-burn' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BRASERO_CFLAGS
and BRASERO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jayr@ubuntu:~/extract/brasero-0.5.1$

[/COLOR]

Back to Windows for me where I can just download a program and it installs automatically without having to hunt for 16 dependencies that can't be found, or can't install because they all require another 14 dependencies each.

Bye bye, Linux lovers. :)

---

### Post by johnc4510 on 2007-04-22
I really don't know how to answer people like you. Usually I don't, but I just looked in Synaptic and that package is listed(Feisty). Why the heck are you trying to compile it (especially since you are new to linux) when Synaptic will install it and all dependencies. Please educated yourself a little better before ragging on what we consider to be a fantastic OS.

---

### Post by bionnaki on 2007-04-22
all you have to do is open a terminal and type:

**sudo apt-get install brasero**

that's as easy as installing applications can possibly get.

---

### Post by hikaricore on 2007-04-22
> **thebluejay said:**
> 
Back to Windows for me where I can just download a program and it installs automatically without having to hunt for 16 dependencies that can't be found, or can't install because they all require another 14 dependencies each.


bye, tell Bill we said hi.

---

### Post by ashz on 2007-04-22
my thoughts exactly, i have been using Ubuntu since Nov i have not even tried to compile anything lol why make life difficult for urself it works fine without it!!

---

### Post by hikaricore on 2007-04-22
Compiling software can be a difficult task at times depending on the libraries used in the project.

95% of the time the authors include a list of dependancies on their website or at the very least
in an INSTALL or README file in the source directory.  Computer users too lazy to bother reading
through them shouldn't be compiling anything as it leads to this kind of useless venting.

---

### Post by ashz on 2007-04-22
> Compiling software can be a difficult task at times depending on the libraries used in the project.

95% of the time the authors include a list of dependancies on their website or at the very least
in an INSTALL or README file in the source directory. Computer users too lazy to bother reading
through them shouldn't be compiling anything as it leads to this kind of useless venting.

agreed!!

---

### Post by srt4play on 2007-04-22
I noticed the version you are trying to compile (0.5.1) is older than the one available in synaptic (0.5.2). Is there a feature missing or problem you were having that caused you to attempt to compile an older version?

---

### Post by silkstone on 2007-04-22
Let me tell you a story....

It's true. ;)

Not long ago my XP machine automatically downloaded some updates. It does this quite often. Then it told me I had to reboot. That's not unusual either.

When it rebooted, it came up with an error message saying that something had occupied some memory reserved for something else, and that it may not work. I tried rebooting again and got the same error.

```
The system DLL user32.dll was relocated in memory. The application will not run properly. The relocation occurred because the DLL C:\WINDOWS\system32\HHCTRL.OCX occupied an address range reserved for Windows system DLLs. The vendor supplying the DLL should be contacted for a new DLL.
```

After hunting around for a while, I found that this update caused a conflict with realtek audio, and that Microsoft had issued a hotfix. I downloaded and installed that, and it cured the problem.

A couple of days later there were some more Windows updates which were automatically downloaded, but the machine froze while trying to install them with an error to SVCHOST.exe. It transpired that the first hotfix had caused a problem with the Windows Update system, and that I had to install a second hotfix to fix the bug in the first one. So I did, and all is now well again.

Now don't get me wrong. I'm not an anti-MS crusader and I do use WIndows for programs for which there is no Linux equivalent, but overall - once you get used to Ubuntu and accept that it is not WIndows and you have to learn it - I find that it is a lot less prone to self-destruction than Mr Gates' creations. ;)

---

### Post by Dave54 on 2007-04-22
I say don't be so hard on the guy. When I first came to linux, I didn't know what compiling was, but I thought it was the ONLY way to install anything. Even then, it took me a few weeks to figure out what people meant when they were talking and broke out into random spouts of code (like sudo gedit /etc/X11/xorg.conf) and another week to find terminal itself.

I really think there needs to be a good place for beginners to get the most basic information, like:
what terminal is
how to install software
WHERE TO FIND INFORMATION (like [https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/"))
how to use terminal (how to copy/paste, use up+down, tab compleation, what "/", "~", or "./" mean, and even things like cd, cp, mv, rm, ls, etc.)
what to do when linux crashes (and yes, it does), or when a program crashes
and other simple information like that.

If such a place exists, then it needs to be advertised much better, because I still haven't found it.

Because of this problem, I insist that **Ubuntu (even Feisty) is not friendly to new users**.

---

### Post by ashz on 2007-04-22
hey dave54 try here...

[http://ubuntuclips.org/](http://ubuntuclips.org/)

cheers
ash

---

### Post by wh0rd on 2007-04-22
Ubuntu out of all the distros is probably the easiest and fastest to install software on. I wonder if this person compiles his/her programs on Windows from scratch also.

---

### Post by JerseyShoreComputer on 2007-04-22
Whats funny about all this is that nothing is perfect - not Linux, Windows, OS X or anything! I use Windows Vista for work. It crashed during my first two (not one, TWO) attempts at installs. After that, for months I have been downloading updates, new drivers, and all sorts of things... Finally, it works, although my webcam acts a little wierd. Other than that - fine. I still cannot use some of my most prized peripherals, like my Dymo label writer or Logitech IO2 pen, but I'll keep waiting for drivers.... And waiting... And this is for a top of the line HP DV9000T laptop to boot!!!

Now here is Ubuntu. I am running it on my old IBM Thinkpad A30.. Installed perfect first shot. Upgraded to Fiesty perfect first shot. Did the wireless work right away? No, but after researching the problem in the community I used NDISWRAPPER and got it to work. Works great in Fiesty too! I use this old computer and Ubuntu more than my expensive company bought work computer with Vista. There is a good reason why - the community. And simply, it just works.

Although I've been longwinded, the moral here is that before you give up, go to the community forums and seek help. That is what makes Ubuntu great - the people. You feel like you are part of something. I have not felt like this since the 1980's (OK, I am dating myself) when the Apple ][ was out and we worked on software developement there.

Don't give up so fast, and don't be afraid to ask for help! This is a really great piece of software that keeps getting better! I am looking forward to hopefully taking part in some of the professional classes. Hope to see some of you there!

---

### Post by Dave54 on 2007-04-22
Hey, for anyone who thinks that Jay didn't ask the community or just suddenly gave up without trying, the you haven't read his other threads.

To explain this thread, I'd recommend [http://ubuntuforums.org/showthread.php?t=409487]("http://ubuntuforums.org/showthread.php?t=409487")

---

### Post by jfinkels on 2007-04-22
> **Dave54 said:**
> Hey, for anyone who thinks that Jay didn't ask the community or just suddenly gave up without trying, the you haven't read his other threads.

To explain this thread, I'd recommend [http://ubuntuforums.org/showthread.php?t=409487]("http://ubuntuforums.org/showthread.php?t=409487")

Yeah, I just saw that too. Sometimes I wish I could go help people in person :\

---

### Post by loell on 2007-04-22
i like this guy, he's leaving ubuntu with a smile 

:lolflag: 

well, we will always see users come and go.
we win many , we loose some, no biggie.

---

### Post by Slim Odds on 2007-04-22
> **thebluejay said:**
> Bye bye, Linux lovers. :)


And good riddance to linux "users" like you.

Seriously though, I'm completely sick of this kind of crap. Ubuntu (and linux in general) work quite well, so if you're having strange problems, it's probably something that you did that was unusual  (or completely stupid). So get over yourself and go back to Windows where you belong.

And while you're there, enjoy:
1) The high COST.
2) The frequent crashes and reboots.
3) The viruses
4) Microsoft's total commitment to themselves (they don't give a crap about you).
5) Buying WAY more hardware that you should really need to run an OS.
6) Semiannual reinstalls
7) Very poor use of resources (memory, disk space, etc, etc, etc).

---

### Post by braveerudite on 2007-04-22
> **bionnaki said:**
> all you have to do is open a terminal and type:

**sudo apt-get install brasero**

that's as easy as installing applications can possibly get.

ROFLMAO

---

### Post by finferflu on 2007-04-22
He'll be back shortly ;)

---

### Post by thebluejay on 2007-04-27
Okay, Okay, I'm back. I couldn't resist the challenge. :)

I think my problem was that I was using a very small distro (Xubuntu- alternative) since I did not have enough memory to install a larger distro on my old PC I was using to experiment with Linux. But I really like the idea of avoiding MS. So I installed a full version of Mandrake on my main PC with dual boot (just in case! LOL) and it seems to be much better because most of the required libraries are included in the distro and updates. Still run into problems here and there - such as Logitech not furnishing adequate drivers for Linux so I lose some features of my mouse - not the fault of Linux, of course.

And I'm staying away from compiling for the time being. 

One problem I am facing is this: in trying to update stuff, in a number of cases I have been told that the update is not possible "due to unsatisfied libcap.so.1" Can anyone tell me what that is and why I am getting that message?

Thx.

Jay

---

### Post by liveforfunnow on 2007-04-27
how are you updating? if you haven't compiled anything, and you installed everything via Synaptic, the updates should be automatic.

of course, this assumes Ubuntu; I've never tried Mandrake.

---

### Post by ebash on 2007-04-27
Resolving all the dependencies in order to compile a software from the source code can be annoying. Although, if the software is already available in the depositories the task can be easier. This is because a debian package (the same format used by Ubuntu) include all the information needed for their compilation. For instance, since *brasero* is already present issuing the following command will ist the package information including the libraries needed:

```
apt-cache show brasero
```

Results:

```

Package: brasero
Priority: optional
Section: universe/gnome
Installed-Size: 1944
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.5.2-0ubuntu1
Replaces: bonfire (<= 0.4.4-1)
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.0), libdbus-1-3 (>= 0.94), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgstreamer-plugins-base0.10-0 (>= 0.10.12), libgstreamer0.10-0 (>= 0.10.12), libgtk2.0-0 (>= 2.10.3), libhal1 (>= 0.5), libice6 (>= 1:1.0.0), libnautilus-burn4, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.16.1), libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), libsm6, libtotem-plparser1 (>= 2.17.5), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, zlib1g (>= 1:1.2.1)
Recommends: gstreamer0.10-plugins-good
Conflicts: bonfire (<= 0.4.4-1)
Filename: pool/universe/b/brasero/brasero_0.5.2-0ubuntu1_i386.deb
Size: 757602
MD5sum: 93f943069fd678d5fec3f5d6e4adbd6a
SHA1: ab387cdd75fc825b202e8bcef237235c171a93a9
SHA256: a55d55ecbf59de1884df0190ea02d99940e38f7c7217d3bf93c81c125cbf25a8
Description: CD/DVD burning application for GNOME
 Easy to use CD/DVD burning application where you can:
  * Burn, Copy and Erase CD/DVD
  * On-the-fly burning of CD/DVD
  * Append data to multisession CD/DVD
  * Burn Audio CD
  * CD-Text writing for Audio CD
 .
 Homepage: http://www.gnome.org/projects/brasero/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

Of course, installing the libraries by hand is still annoying but all hope is not lost, apt-get provides the command build-dep just for this purpose! In this particular case, running it would most likely fix the compilation issues:

```
sudo apt-get build-dep brasero
```

PS: Also remember to install build-essential it can make life easier.

---

### Post by Josey on 2007-04-27
edit:  I should just shut up. heh

---

### Post by Slim Odds on 2007-04-27
> **thebluejay said:**
> But I really like the idea of avoiding MS. So I installed a full version of Mandrake on my main PC with dual boot (just in case! LOL) and it seems to be much better because most of the required libraries are included in the distro and updates. Still run into problems here and there - such as Logitech not furnishing adequate drivers for Linux so I lose some features of my mouse - not the fault of Linux, of course.

And I'm staying away from compiling for the time being. 

One problem I am facing is this: in trying to update stuff, in a number of cases I have been told that the update is not possible "due to unsatisfied libcap.so.1" Can anyone tell me what that is and why I am getting that message?

Thx.

Jay

So you want Mandrake (Mandriva) help in an Ubuntu forum?

Wrong site dude!!

---

### Post by xoros on 2007-04-27
what a quitter.

---

### Post by strabes on 2007-04-27
You guys need to stop being such jerks and be glad that he's back. Seriously.

I'm glad you're getting your problems with linux worked out.

---

### Post by Slim Odds on 2007-04-27
> **strabes said:**
> You guys need to stop being such jerks and be glad that he's back. Seriously.

LOL, when a guy enters a post with the title:[INDENT]Enough is enough! I quit!
[/INDENT]He deserves whatever he gets.....................


I'm more than willing to help people out. I do it all the time. But if you come in with an attitude like that, you might get a little reaction.

-

---

### Post by Josey on 2007-04-27
> **Slim Odds said:**
> LOL, when a guy enters a post with the title:[INDENT]Enough is enough! I quit!
[/INDENT]He deserves whatever he gets.....................


I'm more than willing to help people out. I do it all the time. But if you come in with an attitude like that, you might get a little reaction.

-

I agree.
You get what you give...
Threads with titles like this irritate me and people will come in here with aggressive attitudes so what do you expect?

If people call my mom a ho I'm not gonna play nice.

If these threads were tittled "I'm a mentally lazy idiot and it's linux's fault" I would play nicer with them.

---

### Post by Tomosaur on 2007-04-27
Regardless of how you perceive the poster to be, problems are frustrating. You're representing a community, and we're trying to be the best community around, so if you've nothing nice to say, then say nothing.

---

### Post by kelvin spratt on 2007-04-27
you are both right but people think they know best you see it every where you look and arrogance does not fix it i'm new to linux and i have messed it up 5 or 6 times and because i don't have the knowledge to fix it i reload it as i learned very quickly about the home folder and learn what i've done wrong its a computer it only does what i tell it to do all i can say is i have triad so many flavours this is by far the best to learn on suse is solid but no support unless you pay mandriva is not for the novice

---

### Post by Slim Odds on 2007-04-28
> **Tomosaur said:**
> Regardless of how you perceive the poster to be, problems are frustrating. You're representing a community, and we're trying to be the best community around, so if you've nothing nice to say, then say nothing.

You should take your own advise.

---

