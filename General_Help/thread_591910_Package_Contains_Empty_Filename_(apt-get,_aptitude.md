---
title: "Package Contains Empty Filename (apt-get, aptitude, update-manager)"
date: 2007-10-25
forum: General Help
---

### Post by mlissner on 2007-10-25
Does anybody know how to fix this? It's been a pain for a few days now. I thought it was one of the package maintainers whoopsies, but nobody else seems to be having this problem.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-gnome-support ghostscript ghostscript-x gnome-screensaver gs-common gs-esp gs-esp-x kdelibs-data kdelibs4c2a libgs8 libssl0.9.8
  mozilla-thunderbird openssl thunderbird
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/45.9MB of archives.
After unpacking 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... dpkg: error processing [B]/var/cache/apt/archives/libssl0.9.8_0.9.8e-5ubuntu3.1_i386.deb (--unpack):
 files list file for package `xserver-xorg-video-voodoo' contains empty filename[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/libssl0.9.8_0.9.8e-5ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So far, I've tried doing apt-get clean, but that didn't do it.

Any thoughts?

---

### Post by mlissner on 2007-10-28
Any thoughts out there? I can't install/remove anything until I get this figured out...so far other searches of similar problems have all been deadends...

---

### Post by mlissner on 2007-10-30
Help?

---

### Post by mlissner on 2007-10-31
OK. I fixed this. I had to do some work, but here's the solution to this type of problem. First, do this:```
sudo mv /var/lib/dpkg/info/xserver-xorg-video-voodoo.list /var/lib/dpkg/info/xserver-xorg-video-voodoo.list.bak
```
Once that is done, do this:```
sudo aptitude reinstall xserver-xorg-video-voodoo
```

That should fix the problem, but look at the old contents of /var/lib/dpkg/info/xserver-xorg-video-voodoo.list:
```

¼¼Ðî"Mblx¤´Å'LvÂÒÞô%}¾Ðâ)Martin L. Gore=Marty Balin/Paul Kantner'Maurice Ravel
 CMichael Chapman/Nicky Chinn*YMichael Ivins/Steven Drozd/Wayne Coynex-Michael McDonaldm        MobyÚ
                                                                                                     MorÃ©5N. Reyes/T. Baliardo%Neil Diamond"!Nick DrakeÜ#Nor
man SpanP!Organized Noize, Marqueze Etheridge, Lisa "Left Eye" Lopes, Andre Benjami
```

Looks like my hard drive wrote some data in some strange places.

---

### Post by iTony on 2007-11-12
Thanks for sharing, I hope it works with me. Just a question,I need to change the line xserver-xorg-video-voodoo.list with whichever pakage i need to install, right? What if it doesnt' let me install/uninstall anything, do I have to do that for each of the pakages I want to install?

---

### Post by mlissner on 2007-11-12
My understanding is that the database is corrupted, so yeah, change xserver-xorg-video-voodoo to whatever error you are getting. 

Then, reinstall whatever package it was that was giving you trouble, and once you've reinstalled that package, you should be able to reinstall whichever it was that you actually wanted to install in the first place.

---

### Post by iTony on 2007-11-13
I tried what you said (in my case is the package *libart-2.0-2*) but when i try to reinstall it again it gives me a different package that has an empty filename (*gutsy-wallpapers* this time) and then i redo the steps, but now with *gutsy-wallpapers* and gives me another one. And it keeps going giving me different packages every time I try to reinstall the previous one.

I haven't find how to fix it yet. I'll keep going redoing the steps see if it stops somewhere. But I doubt it. If anyone has an idea, please shoot it here. And yeah I am new in ubuntu, if you haven't notice :popcorn: .

---

### Post by unix4linux on 2007-12-29
iTony,

Did you find out any solution for your problem?  I can't find anything on this and this post is the closest I've gotten.  I tried the suggestions from the other posters but to no luck.

Thanks

---

### Post by mlissner on 2007-12-29
Sorry for not replying sooner...iTony, did you figure out a solution? unix4Linux, what's the error message you're getting?

---

### Post by fadereu on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/159163](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/159163) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, I haven't been able to install any packages on Gutsy for over a month now.
The situation is beyond urgent, and quite ridiculous since I can't
continue any of my work.

The system kept saying that the file containing list of files for libtheora0 and
libtracker-gtk0 were missing every time I run apt-get. I fixed that by getting the same from
elsewhere. Now when I tried re-installing dpkg itself, it says:

```
dpkg: serious warning: files list file for package `libtiff4' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb (--unpack):
 files list file for package `libtrackerclient0' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
fadereu@fadeurium:~$
```

I think a few files might be corrupted in /var/lib/dpkg/info/
which is pictured here:

[http://sand.a3ai.com/images/dpkginfo.png](http://sand.a3ai.com/images/dpkginfo.png)

Kindly propose me a solution that will work. I'm not very experienced in Linux,
but I can follow clearly written instructions.

yours,
-- fadereu
-------    -.-
1/f   )))  --.
-------    ...
[http://www.algomantra.com](http://www.algomantra.com)

---

### Post by mlissner on 2008-01-20
It sounds like you may want to rebuild your apt database (index?). I, unfortunately, don't know how to do that, but that might yield a lead for you. If nothing else, we can consider this post a bump for you.

---

### Post by MauriceGoodf on 2008-06-06
Thanks for this info - it has solved my problem - except that I couldn't use Aptitude to reinstall the package.  However, the Update Manager (System -> Administration) was able to install the packages once I had renamed the .list file to .bak

Maurice

---

