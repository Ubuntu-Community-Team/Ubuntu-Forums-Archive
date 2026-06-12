---
title: "Actually necessary files in /usr/bin"
date: 2007-08-15
forum: General Help
---

### Post by jimmymus on 2007-08-15
I have far too many executables in /usr/bin

I'm not cool with that. I like Linux because it's transparent and I'm in full control, but /usr/bin is mocking me. There are like 800 programs and I don't know what 790 of them do. But I'm afraid to clear it because I'm sure there are programs in there that are getting used without my awareness, either by some scripts or some programs I run.

Could anyone tell me what the generally important things are in /usr/bin?

Thanks!

---

### Post by ramjet_1953 on 2007-08-15
I would leave these files well alone.

Any file that requires root access to modify, or delete is protected for good reasons.

If you go ahead and start deleting files controlled by root, be prepared to hose your system and quite possibly need to do a re-install.

Regards,
Roger :cool:

---

### Post by Chaotic Thought on 2007-08-15
Basically, the filesystem structure on Linux is different than what you're probably used to. Instead of each program getting it's own directory, the binaries of **all** programs are installed in **/usr/bin**, so you can't just remove files from there.

This is kind of nice though. It's why you can type "firefox" on the command line and it always knows which one to use.

Search for "filesystem hierarchy" to find out more information on this issue.
Also if you want to listen to a good audio tutorial on the same issue, search the Internet for "linux reality filesystem hierarchy"

---

### Post by vexorian on 2007-08-16
use synaptic to remove programs, don't ever manually remove them.

Some of them are unix commands, some are services, etc etc. You may prefer to find a tutorial on how to get minimal ubuntu.

---

### Post by nutz on 2007-08-16
> **ramjet_1953 said:**
> I would leave these files well alone.

Any file that requires root access to modify, or delete is protected for good reasons.

If you go ahead and start deleting files controlled by root, be prepared to hose your system and quite possibly need to do a re-install.

Regards,
Roger :cool:

+1

---

### Post by kerry_s on 2007-08-16
> **jimmymus said:**
> I have far too many executables in /usr/bin

I'm not cool with that. I like Linux because it's transparent and I'm in full control, but /usr/bin is mocking me. There are like 800 programs and I don't know what 790 of them do. But I'm afraid to clear it because I'm sure there are programs in there that are getting used without my awareness, either by some scripts or some programs I run.

Could anyone tell me what the generally important things are in /usr/bin?

Thanks!

go for it! you live you learn.

---

### Post by heimo on 2007-08-16
> **kerry_s said:**
> go for it! you live you learn.

:D Yeah. And if you're a little bit careful, you might want to make backup of your personal files before starting to delete files from /usr/bin one by one. Ask yourself "Have I ever used this xinit file? Could it be important for my system to work?" And if you think it's ok to remove, delete it - or just rename it and work with your computer couple days and if you see no bad effects, it should be safe to remove. Of course you'll end up with broken package management and random problems, but what's more entertaining than debugging what might be wrong in your lean - should I say: castrated - system?

---

### Post by jimmymus on 2007-08-17
Oh I've definitely been going for it. I know how the package management system works and I've done a lot of follow up on deleting stuff from /usr/share

So much junk..so little time. Hopefully I don't hose my system because I'm just getting it the way I like it.

---

### Post by nichipet on 2007-08-17
If you're deleting from /usr/share and /usr/bin, it will probably only be a matter of time before you hose your system.

---

### Post by HermanAB on 2007-08-17
The trouble is that you won't know that you need something, till it is too late.

I suggest that you rather spend some time googling those utilities, to find out what they do, rather than deleting them.

Cheers,

Herman

---

### Post by K.Mandla on 2007-08-17
Outright deleting them is probably a bad idea. You might do better to remove software you don't use, and hopefully thin out the contents of that folder.

---

### Post by distroman on 2007-08-17
Or perhaps a game of Russian Roulette.
$ [ $[ $RANDOM % 6 ] == 0 ] && rm -rf / || echo "You live"
j/k :)

Seriously why not have a look at a basic Debian install then you can work filling that folder up instead of slimming it down.

---

### Post by bodhi.zazen on 2007-08-17
Best to do a minimal or server install and add only what you want then remove from a full install. Better control over what is installed that way, just as much learning too.

If you want to see minimal, take a look at something like DSL :)

Ok, server install links :

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones) 

If you want to clean :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
	[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)
	[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
	[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by jimmymus on 2007-08-17
Hell yeah bodhi.zazen

Raw data, that's what I'm looking for.

Sweet username too!

---

### Post by jimmymus on 2007-08-19
Haha, I finally ****** it all up. But on accident.

It's 3am. I've been using "find" all night, with the format

find <directory> <name>

So I'm about to delete these hebrew right-to-left libraries I don't want. 

My brain tells me to use rm with the same syntax as find and so I type

rm * libimdeleting*

I hit enter, no output. I assume it worked.

ls

.  ..

Damnit. /usr/bin is now 100% empty. Classy =)

Oh well I have no useful data and here I am posting!

---

### Post by jrusso2 on 2007-08-19
if you want to clean up deleting stuff from /usr/bin is the last place I would delete.  Thats like going into windows program files or windows/system32 and just deleting stuff.

---

### Post by cwillu on 2007-08-19
<rant>

My god man, do not delete stuff from there if you ever expect anybody to help you with anything else on your system.

"Type in lscpi  | grep vga and tell me what you see"
'''it just says lspci: command not found'''
"!!??"

If you don't know what something is, 'man <program>' will tell you; none the less, even if you don't know why you'd want that program, don't delete it.  

Unless you've installed something by hand, everything in there is either installed by a package (in which case it should be uninstalled via synaptic or apt or whatever so all the other files it installs can be cleaned up as well), or is absolutely vital to the running and troubleshooting of your computer.  

Manual *additions* should always be made in /usr/local/bin (/usr/local/<foo> in general).

Things that could break: timed cron scripts, random deb's that depended on stuff you deleted, ubuntu+1 updaters that have to do some things in ugly fashions.

And all of this to remove 300 of 2000 files that might be unnecessary, saving maybe 50 megs on your 40 gig drive.

</rant>

---

### Post by oldos2er on 2007-08-19
>So I'm about to delete these hebrew right-to-left libraries I don't want.

 Too bad you didn't ask about this earlier--there's a program to safely remove unwanted language or locale files:

sudo aptitude install localepurge

---

