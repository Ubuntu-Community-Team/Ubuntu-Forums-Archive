---
title: "moving additional apps to /opt partition?"
date: 2007-10-26
forum: General Help
---

### Post by perixx on 2007-10-26
Hi again!


I just moved my /home folder successfully to another partition.
Now, I'd like to do add an /opt partition to the system....
I've heard that it is for additional applications that are being installed to the system, saving space and preserving the apps' settings in case of a system upgrade - is that correct?

Can I move those apps already installed to the system to the new /opt partition subsequently? If yes, how to do it?


perixx

---

### Post by nick_h on 2007-10-26
Application settings are usually stored in the home directory of each user.

The /opt directory is usually for applications that are not installed from the repositories.  What do you have installed in /opt at the moment?

---

### Post by perixx on 2007-10-27
Currently? Nothing. Do you mean that compiling and installing a program myself will put it into /opt?

In which other cases are applications being placed there?


perixx

---

### Post by songshu on 2007-10-27
you can put it anywhere you want, but it is a common rule that any packages not included/supported by your distro is not misplaced if you put it in /opt.

so indeed, if you compile something yourself its not a bad idea to put it exactley there

---

### Post by perixx on 2007-10-27
Thanks for your hints...

Since I'm not yet experienced with advanced (or even different from the usual Synaptic / sudo apt-get install) setup methods for applications, I am pretty much lost with knowing, when I'd need such a partition or if it makes any sense to me. 

Anyway, I can make use of it, if I compile stuff for myself, correcto? Where else does it make sense? 
As most programs are availible from the repos, there might not be much need for an /opt partition - or not much space, maybe max. 3-5 gigs for some additional stuff and newer self-compiled app-versions, right...?

Two questions, though:

Do all applications installed the usual way really always store their whole settings in the /home/USER/.APPLICATION folder? 

What about Whine, respectively installed Windows programs / games? Where are they being stored?


perixx

---

### Post by songshu on 2007-10-27
not all the settings go to /home/USER , only the user specific one, for example your bookmarks in firefox or your e-mail configuration etc...
systemwide configuration usually goes into /etc

wine is an excepion to this rule since its default is to install evrything under /home/user

personally i never used the /opt in debian or ubuntu since most programs are in the repositories anyway and in the rare case i would need to compile from source i would use checkinstall wich makes a nice .deb package

if you want a normal desktop system i think having a seperate /home partition is enough

---

### Post by perixx on 2007-10-27
So I can't specifiy self-compiled apps to install in /home if needed ?

Btw., can you provide me with a link to a comprehensive guide for compiling applications under Xubuntu and Linux in general?


perixx

---

### Post by songshu on 2007-10-27
the beauty of compiling yourself is that you can choose all options, including where you place them.

if you want too know aything about compiling this link should be a nice start [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

always read the README files in the source packages, the one who made them usually will tell you what to do

---

### Post by nick_h on 2007-10-27
If you install stuff yourself /opt is a good place to put it.

There is a [sticky](http://ubuntuforums.org/showthread.php?t=232059) in the beginners forum - section 4 gives some links - [this](http://psychocats.net/ubuntu/installingsoftware) and [this](http://monkeyblog.org/ubuntu/installing/) look good.

Most settings are held under /home.  Global system stuff is usually under /etc.  Other places for global application settings include /usr/share.

You might use /opt to install a more up to date version of a program than avialable in the repositories.  You won't need a separate partition for it though.

---

### Post by perixx on 2007-10-27
Thank you, songshu and nick_h!

The reason why I'm trying to detach as much user-specific setup applications and settings in general is, that I'd like to have a save and easy way to install new Ubuntu versions with running as much stuff from how I left it from the first start again.... that's what I've read /home and /opt partitions would offer to me. 

But I'd like to go a bit farther, if possible. Of course I'm aware, that application- or system-specific locations may vary from every new release. Still, I might have advantages with separate partitions, in case anything goes wrong with the main installation or partition, I think.

I'll have a look into those compilation tutorials anytime soon!

perixx

---

### Post by perixx on 2007-11-02
By the way, how do I tell apt-get to install 

A) a locally stored .deb package
B) to install that package into /opt
:confused:


perixx

---

### Post by perixx on 2007-11-04
Problem partially solved!

[http://ubuntuforums.org/showthread.php?t=575671&page=2]("http://ubuntuforums.org/showthread.php?t=575671&page=2")

perixx

---

### Post by perixx on 2007-11-04
Hi again...

this is why I wrote 'partially solved' a post before:

> By the way, how do I tell apt-get to install

A) a locally stored .deb package
B) to install that package into /opt


And also compiled packages, of course...


perixx

---

### Post by perixx on 2007-11-07
I will add some good supplemental link for those who want to re-activate their /home folder - it was originally aimed at recovering /home/USER-partitions, but might apply for the /opt folder as well!


> [http://ubuntuforums.org/showthread.php?t=166626](http://ubuntuforums.org/showthread.php?t=166626)


by the way, I think using the separate /opt partition is not only good for applications, but for the temporary backups as well... so you can have them separated from your system- and USER-partitions, in case there is any trouble. Taking the /home partition for scheduled backups is maybe as good or bad - but it will also keep the system's partition from a data overflow.  


perixx

---

