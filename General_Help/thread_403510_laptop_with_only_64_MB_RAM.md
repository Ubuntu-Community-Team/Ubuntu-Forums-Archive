---
title: "laptop with only 64 MB RAM"
date: 2007-04-07
forum: General Help
---

### Post by carverj on 2007-04-07
I noticed that Knoppix recommends at least 96 MB RAM.
Anyone know of an OS that recommends at least 64 MB RAM?

---

### Post by aysiu on 2007-04-07
Damn Small Linux or Puppy Linux.

---

### Post by carverj on 2007-04-07
Yeah, I tried them. um, puppy wouldn't load at all. In fact, i believe knoppix is the only one that has worked at all so far! Perhaps the CD-ROM  is to slow to start Live CD.
 I have puppy on USB, but no boot option to load OS from USB.
If I am able to load knoppix again, could I make some extra paging space with command line? what commands do I need. I remember one was swapon !!?

---

### Post by aysiu on 2007-04-07
**Knoppix**
Unfortunately, Knoppix is a live CD (which means it's not going to run well on 64 MB of RAM), and it's also not really meant to be installed (although it can be).

If Knoppix is all you have, you may be able to do something. Try booting with these options (instead of just hitting *Enter* at the boot prompt): ```
knoppix 1
``` This should boot Knoppix to a command prompt. Then, to install Knoppix, try ```
sudo knoppix-installer
``` That *should* allow you to install Knoppix to your hard drive.

Once you do, if possible, try to use IceWM. KDE will be too slow on 64 MB of RAM.

**Ubuntu**
If you have a Ubuntu Alternate CD (the Desktop CD won't work for this), you can choose the *Install a Server* option to get a barebones installation. When you get it installed, you'll end up at a terminal prompt. Log in and type these commands: ```
sudo nano -B /etc/apt/sources.list
``` Remove the # sign from the beginning of any line that looks like a web address. Then save (Control-X, Y, Enter). ```
sudo aptitude update
sudo aptitude install menu icewm xterm wdm xorg dillo gksu synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/wdm start
```

---

### Post by carverj on 2007-04-07
Ok, inserted Xubuntu and there is an LTSP server option or install command-line system option. Will the LTSP option do the barebone system?

---

### Post by aysiu on 2007-04-07
You're downloading Feisty Fawn? I think that *Install a Command-line System* is the new terminology for *Install a Server*

---

### Post by carverj on 2007-04-07
> Knoppix
Unfortunately, Knoppix is a live CD (which means it's not going to run well on 64 MB of RAM), and it's also not really meant to be installed (although it can be).

If Knoppix is all you have, you may be able to do something. Try booting with these options (instead of just hitting Enter at the boot prompt):
Code:

knoppix 1

This should boot Knoppix to a command prompt. Then, to install Knoppix, try
Code:

sudo knoppix-installer

That should allow you to install Knoppix to your hard drive.

Once you do, if possible, try to use IceWM. KDE will be too slow on 64 MB of RAM.

Followed these instructions but even though gave same password for admin and my user, I cannot authenticate root user. How would I alter the sudoers' file?
Thanks

---

### Post by carverj on 2007-04-07
> Knoppix
Unfortunately, Knoppix is a live CD (which means it's not going to run well on 64 MB of RAM), and it's also not really meant to be installed (although it can be).

If Knoppix is all you have, you may be able to do something. Try booting with these options (instead of just hitting Enter at the boot prompt):
Code:

knoppix 1

This should boot Knoppix to a command prompt. Then, to install Knoppix, try
Code:

sudo knoppix-installer

That should allow you to install Knoppix to your hard drive.

Once you do, if possible, try to use IceWM. KDE will be too slow on 64 MB of RAM.

Followed these instructions but even though gave same password for admin and my user, I cannot authenticate root user. How would I find and alter the sudoers' file?
Thanks

---

### Post by aysiu on 2007-04-07
This might help:
[http://www.knoppix.net/forum/viewtopic.php?t=11500](http://www.knoppix.net/forum/viewtopic.php?t=11500)

---

### Post by linuxonbute on 2007-04-07
I run Puppy on my ancient Fujitsu 780TX ( 233MHz Pentium with 3Gig Hard Disc and 64 Meg Ram.}

What you need to know is that "Puppy loads entirely into Ram".

What this actually means is that if you are using it as a live boot from CD it will try to load into and run entirely from Ram.

Puppy 2.2 needs 128Meg Ram to do this.

Puppy 2.02 only needs 64Meg Ram so try 2.02

BUT 

if you install it to Hard Disc then even 2.2 will run real quick because then it can use swap and doesn't need all of the Ram. This is because it uses programs which use small amounts of memory.

I have a wireless card in mine and can surf, send emails - all the usual stuff - but don't forget you cannot expect it to run memory hungry programs like OpenOffice.

Still I get round this by using ssh to get onto my main PC then set up X forwarding to display on my laptop. That way the programs run on my main PC but display on the laptop.
:)

---

### Post by carverj on 2007-04-07
Thanks for assisting me aysiu once again.
I appreciate it, and also took for granted how easy Ubuntu is to configure.
It is taking me hours just to figure out how to use an image as a desktop background !!
Happy easter Sunday everyone 
[-o<

---

### Post by cantormath on 2007-04-07
> **carverj said:**
> I noticed that Knoppix recommends at least 96 MB RAM.
Anyone know of an OS that recommends at least 64 MB RAM?

I recommend damn small linux.

---

### Post by honeydew on 2007-04-19
I recomend dynebolic.. it has a live cd is a really cool distro and is really easy to operate.  I have used it on systems with only 64megs of ram and it has run well.  I would also suggest if you have the ability check out openbsd or netbsd  these are a bit more advance but they run on anything.

[http://www.dynebolic.org/](http://www.dynebolic.org/)
[http://openbsd.org](http://openbsd.org)

---

### Post by barbarian on 2007-04-19
Feisty "server" install from alternate CD, then xserver and icewm..

---

### Post by aysiu on 2007-04-19
> **barbarian said:**
> Feisty "server" install from alternate CD, then xserver and icewm..
I did wrote up a tutorial on this recently:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by barbarian on 2007-04-20
Thanx, Aysiu that was exactly what i meant. IMHO, that the easiest way to run ubuntu on a weak machines..

---

