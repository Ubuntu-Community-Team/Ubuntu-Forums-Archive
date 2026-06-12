---
title: "After compiling source, how to install?"
date: 2008-04-27
forum: General Help
---

### Post by bunnyfly on 2008-04-27
Hello - I have come up with this problem a few times. Often I'm having to compile sources because there aren't any debs out there. But about a third of the time, they don't have a make install. So when I have an executable program sitting in say ...Desktop/ThingSource/thing, how do I install it?

Should I just move it to /bin? Should I make a ~/bin/ folder? Is there a command? Can I convert the directory of files or just the single executable into a deb?

Thanks!
[bunnyfly]

---

### Post by TeoBigusGeekus on 2008-04-27
Standard procedure involves typing
```
./configure
```
in the program's folder to check if everything is ok for compiling.

You then type
```
sudo make
```
to compile the package.

Finally, you give
```
sudo make install
```
and you are finished. The program should appear in your applications menu. If not, there should be a terminal command to launch it - check the software's documentation.

---

### Post by bunnyfly on 2008-04-27
Thanks for the reply. But like I said, "about a third of the time, they don't have a make install"

So when make install isn't there, what should I do? For example, the one I'm compiling right now is fakenes. After gather the dependencies, make built it and it runs fine, but make install gives me:
```
make: *** No rule to make target `install'.  Stop.
```
Another one was when I downloaded Skype 2.0, they didn't have a deb, and it just sat in a folder, no install command. It ran from the folder, but I didn't want it sitting on my desktop and wondered what to do with it?

Thanks!
[bunnyfly]

---

### Post by olskar on 2008-04-27
Skypedeb here

[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

---

### Post by bunnyfly on 2008-04-27
Thank you again - but it doesn't answer my question.

I already have the Skype deb now, but when it originally came out, it took awhile before it appeared in repos and in debs. I'm not looking for a specific deb...

**I'm looking to know where to move/how to install ANY program I compile myself that do NOT include an install script.**

Thank you,
[bunnyfly]

---

### Post by mc4man on 2008-04-27
If you stick it in /usr/bin then it'll run directly off cli, if in /usr/local/bin (preferred ) you'll need path in command
You could then make a menu item to run from

---

### Post by bunnyfly on 2008-04-27
Great! I'll try out /usr/local/bin. Since it's empty, it'll be easy to keep track of what I put into it.

Thank you,
[bunnyfly]

---

### Post by bodhi.zazen on 2008-04-27
> **bunnyfly said:**
> Hello - I have come up with this problem a few times. Often I'm having to compile sources because there aren't any debs out there. But about a third of the time, they don't have a make install. So when I have an executable program sitting in say ...Desktop/ThingSource/thing, how do I install it?

Should I just move it to /bin? Should I make a ~/bin/ folder? Is there a command? Can I convert the directory of files or just the single executable into a deb?

Thanks!
[bunnyfly]

That is a lot of compiling. Just curious have your enabled your repositories (universe and multiverse)?

---

### Post by bunnyfly on 2008-04-27
Oh yes - I have the repos enabled. I've only had to compile about 10-15 things or so since I switched to Ubuntu. Part of the problem was that I'm using the amd64 distro. So like six months ago it seemed that there were a lot of things that weren't ported yet, but now it seems like it's about on par with the 32. Then there are smaller projects, emulators like Advanced menu, fakenes, a few drivers when I was attempting to get Linux to support my RTL8187 properly, wavesurfer came compiled, but just a little executable, no deb, etc, etc.
[bunnyfly]

---

### Post by rbcl15 on 2008-05-02
Hi, can someone explain what is meant by compileing in the above sense?

---

### Post by jingo811 on 2008-05-02
Hijack - 1

Sometimes programs that you want to download from Ubuntu's package manager (Synaptic) doesn't work.  This can be because they are outdated or removed by the repository guys because of bug reports.

To install a program you want to try anyways you compile it from source code and install it yourself manually.
If I'm not mistaken most source codes are written in C or C++ so you download
a *.tar or *.tar.gz file unpack it then you configure the files just for you PC.  By running "./configure" then if everything went OK you compile the configured source code by running "make".
When that's finished you install the compiled codes by running "make install".

I've been told that you shouldn't run "./configure", "make" and "make install" as sudo/root but most of the times I've been forced to run as root anyways.
Is this what you meant by explanation? :)

---

