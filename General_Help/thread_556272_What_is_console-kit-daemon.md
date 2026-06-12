---
title: "What is console-kit-daemon?"
date: 2007-09-21
forum: General Help
---

### Post by last1 on 2007-09-21
Or, more accurately, why is it that when I run htop it shows 60 instances of a process labelled console-kit-daemon? I got no problem with consolekit from the small description I've been able to find of it, but that seems about 59 processes too many.

---

### Post by motscousus on 2007-09-21
same here !

disabled it in /etc/init.d/consolekit script (put exit 0 on the 2nd line of the script)

---

### Post by last1 on 2007-09-21
And it didn't affect your system at all to have it completely disabled? Hmm, that's interesting.. I might just do that myself if I can't get a clear answer on why there's so many processes from it.

---

### Post by jaakan on 2007-10-10
Does anyone know what console-kit-daemon is for and or does?

---

### Post by last1 on 2007-10-18
Well from what I understand of it, it seems to exist to help unpriveledged users access devices, for when a regular user logs out and quickly access a device from a different user he's logged in as. It doesn't even seem to me like it's necessary unless you have multiple users in your system, but I haven't tried disabling it yet like motscousus has.

And it still doesn't answer why it needs so damn many running processes. 

About the only place I've been able to find a general explanation about it is in this fedora documentation of something called fast user switching. 
[http://fedoraproject.org/wiki/Desktop/FastUserSwitching](http://fedoraproject.org/wiki/Desktop/FastUserSwitching)
It has a few paragraphs about consolekit a quarter of the way down the page.

---

### Post by 11touche on 2007-10-21
Same problem here, exactly 60 instances of console-kit-daemon.
And never got this bug under Feisty, only since I upgraded to Gutsy.
Can I kill them without hurting my system?

---

### Post by racoon97 on 2007-10-21
Same probleme here. Is it possible to uninstall this processes?

---

### Post by NiklasW on 2007-10-22
Same issue here. I counted 62 process with the same name (console-lit-daemon)

I have not seen any direct issues that this has to my system. Meaning that for now my system is running OK. (other then that the processes all steal 0.2% of my RAM.

Is this a confirmed bug or should it be like this?:confused:

---

### Post by hikaricore on 2007-10-22
I've been wondering this myself.

I have 3 different systems all running Gutsy, which were upgraded from Feisty.
Both of my comps are without this mess, however my girl's system is showing the 40-60 console-kit-daemon processes.

I havn't been able to find much info on this.  O.o
However it's also mentioned atleast once on the french forums: [http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D155752&langpair=fr%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D155752&langpair=fr%7Cen&hl=en&ie=UTF8)

---

### Post by last1 on 2007-10-23
Launchpad number for this bug
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454)

Ubuntu-specific information on what this does and why
[https://wiki.ubuntu.com/UnifiedLoginUnlock](https://wiki.ubuntu.com/UnifiedLoginUnlock)

Course that still don't explain why such a glaring bug hasn't been fixed yet. :rolleyes:  :)

From what I've read about it on Launchpad and in the specs, if you only have a single user you log into Ubuntu as, you can safely uninstall the consolekit package and the fast user switch applet. I've also just uninstalled consolekit and haven't run into any problems (yet)

---

### Post by cmittle on 2007-11-17
I also have about 60 of these processes running.  What components exactly do I need to remove to remove this feature?  If I try to mark it for removal in synaptic it says ubuntu-desktop will also be removed.  To me this sounds like a bad idea, is it?

Also, I have several instances of trackerd running.  Can anyone tell me what this is about?

Thanks,
Cory

---

### Post by rasker on 2007-12-02
Apparently nothing to worry about. It's how console kit works. I think each process stores information about a single user session. I would guess a bunch of processes are fired off at startup to allow for upto whatever number of concurrent logins/sessions. Even a single user can use more than one of these.

Consolekit is a *good thing* to have around. It will be used much more as applications incorporate support.

Apart from making process lists a bit messy it has few adverse effects.

---

### Post by last1 on 2008-01-10
Naw dude, 5 processes is a *bit* messy, 60 processes is totally overkill. And that's not even mentioning that there are all of these processes just sitting there taking up valuable resources running on the system while apparently doing nothing to actually improve the desktop experience, since there isn't anything that is even using it. If each process is listed as taking up 0.2% of RAM in htop and there's 60 processes, then consolekit takes up a total of, what, 12% of system ram? Seems completely unacceptable to me for such a minor feature.

Maybe when applications actually do start to use it for stuff I'd feel differently, but in the meantime mine's uninstalled and it's going to stay that way (haven't experienced any problems either)

---

### Post by JonathanRRogers on 2008-01-11
On my system, there is exactly one process of console-kit-daemon, which has a large number of threads, only one of which has used any significant amount of time (less than a second), so this isn't as a big a deal as it seems. 

Htop seems to show all threads as distinct tasks by default, unlike other utilities. If you hit F2, then enable Display Options -> Hide Userland Threads, it should only show one line of console-kit-daemon.

---

### Post by jimmyridge on 2008-02-11
<hardy heron>  i cant find what script execs console-kit-daemon i dont see  the script you fellas speak of in /etc/init.d/  i even did a `cat /etc/init.d/* |grep console-kit ` and found nothing  decided to mv /usr/sbin/console-kit-daemon ./ckd_hate' durring after i rebooted the network manager failed to popup so i put it back and all is fine  ps ax shows

 4831 ?        Ssl    0:00 /usr/sbin/console-kit-daemon

whilke htop shows lots of pids belonging to console-kit-daemon maybe im 
overreacting and everything is fine so i'll leave it be

---

### Post by jimbob on 2008-02-11
/etc/init.d/consolekit

---

### Post by immeëmosol on 2008-03-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
I think the answer might be hidden in this text on the web:

From the **_[ConsoleKit 0.2.6 Documentation](http://people.freedesktop.org/~mccann/doc/ConsoleKit/ConsoleKit.html#id2834824)_**:
> "A session is a collection of all processes that share knowledge of a secret. In the typical (or ideal) case, these processes all originate from a single common ancestor."

If I understand this text correctly, it creates one main-program instance with quite a lot of instances under that program all those sub-programs know a `little` secret...

At least, that's what I make of it when I create the story of those facts.
(1. It has so many processes  ,  2. the text on the uri I posted above)

And if I keep this great story in mind I hope they will continue development on this fast-user-switch and what-not more application so it will not scare people by all those processes in the ps list.


I'm waiting to be corrected if anything in this article might be incorrect.

---

### Post by akin0 on 2008-04-08
hey guys, check this:

root@laptop:/etc/ConsoleKit# dpkg-query --print-avail consolekit
Package: consolekit
Priority: optional
Section: admin
Installed-Size: 348
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.2.3-3ubuntu5
Depends: dbus (>= 1.1.2), libc6 (>= 2.7-1), libck-connector0, libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libglib2.0-0 (>= 2.16.0), libx11-6
Recommends: libpam-ck-connector
Size: 64874
[B]Description: framework for defining and tracking users, sessions and seats
 ConsoleKit is a system daemon for tracking what users are logged
 into the system and how they interact with the computer (e.g.
 which keyboard and mouse they use).
 .
 It provides asynchronous notification via the system message bus.
 .
 This package provides the system daemon and tools to interact with it.[/B]
Homepage: [http://www.freedesktop.org/wiki/Software/ConsoleKit](http://www.freedesktop.org/wiki/Software/ConsoleKit)
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>

So, its part of the system.

--
Gambatte Kudasahi

---

