---
title: "Startup Programs: Where's the FULL List??"
date: 2007-06-20
forum: General Help
---

### Post by OzzyFrank on 2007-06-20
OK, I know about Sessions, and the gconf editor, and various other places were you can change programs that run on startup. But isn't there one central list somewhere, or at least a file that lists the zillion other things I know are being loaded, but I can't find mention of? I have a firewall that loads at startup, even though it actually isn't anywhere to be seen when I'm online, I have at least 2 different antivirus apps loading, for whatever reason that is (since they ain't scanning my mail)... as you can imagine, i'd like to tidy up my boot process, as I believe things are using up resources for no apparent reason.

At least in Windows when apps annoyingly make themselves part of the boot process and then don't give you a way to disable that you can go to Run in Regedit and delete the line. I'd like to have similar control in Ubuntu. Is this possible?

Cheers

---

### Post by Rui Pais on 2007-06-20
For tweak the boot precess and started services check [this thread here]("http://ubuntuforums.org/showthread.php?t=89491").

---

### Post by vexorian on 2007-06-20
Actually windows apps got 30 different ways to run on startup.

Either way it is not possible because there are also many things that run on Ubuntu and each of them may have its own list of things to start.

What's the specific service / program you want to get rid of?

---

### Post by linfidel on 2007-06-20
> **vexorian said:**
> Actually windows apps got 30 different ways to run on startup.

Either way it is not possible because there are also many things that run on Ubuntu and each of them may have its own list of things to start...Yes, in Windows there are several different ways to start programs, and one can start another, just like linux.

But the list isn't that long, certainly nowhere nerar 30; more like half a dozen or less.  And there is a way to see all the running processes, and how they were started (name, description, company, and command line), and what files and dlls they have open, from one list (process explorer, free from Systernals).  Finding where they are started can usually be done using one of a number of utilities, including another one from the same place (I think it's called starts).

With Ubuntu, I usually use the tray utility, but I haven't been using it long enough to notice any deficiencies yet.  Is there a better way to list all running processes?  The link above had lots of information I'll be looking at for where things get started from.

---

### Post by OzzyFrank on 2007-06-20
Well, I'd like to know what system files load these things for general knowledge, and for being able to keep an eye on things, like I how peep into Run in Regedit in Windows to see what has stuck itself there (and other startup places in Windows).

As for programs I would like to disable now, a start would be the aforementioned Firestarter and 2 (or more) antiviruses, since I actually have to load them manually to use them anyway. The latter don't seem to do anything... can't see them guarding the system, and not like it needs it, and they ain't scanning emails, so why are they loading? As for Firestarter, don't know what it is protecting me from at boot, but if i get online, i need to manually start it as it isn't actually running.

If I had a list of the startup files or whatever, I could then also look through and trim unwanted things, comment them out to see the effect, etc.

---

### Post by Rui Pais on 2007-06-20
hi,
do you read the link on my post?

Linux is not a full centralized unique entity.

Is a: 
kernel + "a kind of unix clone os" + an X server + graphical manger + Desktop Environment

They are all different, and use initializations and options in diferent ways.

For kernel you got:
/etc/modules for load modules and /etc/modprobe/blacklist for blocking modules.
Or recompile all, exactly like one likes, for the brave :)

For the "Unix" part, the boot process and base system see the link above.
Use an app called sysv-rc-conf to turn services on/off. use /etc/rc.local to add personal stuff to boot process.
  
X and gdm you can control with /etc/X11/xorg.conf and /etc/X11/gdm/gdm.conf-custom files. (don't know kdm) 

DE (windows have 1 DE with same name of OS) Linux have around 3 hundred of them... (well some are just Window managers, but serve the same purpose, for simplification)
gnome use gconf-editor (a registry, puahh), kde use kcontrol, 
almost all the others use text files editable by any text editor (man file says where they are stored.

For any other thing... well think of your /etc/ as a kind of registry. The only thing is that Linux don't need to read it all in one time (so no need for reboots) , there is no cryptic CID (or what ever was they names) and one can (but shouldn't!) edit anything with text editor :) 

I think you are thinking too much as a Windows User. They are very different OSs... What applies in one is not true in other and vice-versa. 
Tweak with services at boot level (one of the weakest parts of Ubuntu) the rest you may do more harm then good.

hope that Linux in 12 lines can help in someway :)

---

### Post by OzzyFrank on 2007-06-20
"process explorer, free from Systernals"

OK, figured you meant Sysinternals (didn't even see the typo at first actually) and they do indeed have a Process Explorer.... trouble is, it's for Windows. I'm actually asking about the Ubuntu boot process, not my Windows one. Any Linux apps?

---

### Post by OzzyFrank on 2007-06-20
"do you read the link on my post?"

Yes, unfortunately not quite what I wanted, especially since the guy's disclaimer was that you could render your system inoperable, hehe. Your last post was much more informative, thanks. And yes, I've come to realise some things aren't as simple as in Windows (shock! horror!) but figured there would have to be a list of config files and what-not that I could find startup programs and processes. After all, Ubuntu doesn't boot up on magic (unless it's this African voodoo thing).

---

### Post by linfidel on 2007-06-20
> **OzzyFrank said:**
> "process explorer, free from Systernals"

OK, figured you meant Sysinternals (didn't even see the typo at first actually) and they do indeed have a Process Explorer.... trouble is, it's for Windows. I'm actually asking about the Ubuntu boot process, not my Windows one. Any Linux apps?Sorry about the typo.:)
Actually, I was sort of seconding your question - I was responding to vexorian, and I meant that Windows had Sysinternals tools, and wondering if Ubuntu had something like that - that would tell what was running, regardless of where or why it started.

Maybe top, or whatever it's called.  I've seen it, but haven't tried it yet.  It looks like a command-line process explorer.  Actually, I guess all the real Linux programs are command-line programs.  :)

---

### Post by Rui Pais on 2007-06-21
> **OzzyFrank said:**
> "do you read the link on my post?"

Yes, unfortunately not quite what I wanted, especially since the guy's disclaimer was that you could render your system inoperable, hehe. Your last post was much more informative, thanks. And yes, I've come to realise some things aren't as simple as in Windows (shock! horror!) but figured there would have to be a list of config files and what-not that I could find startup programs and processes. After all, Ubuntu doesn't boot up on magic (unless it's this African voodoo thing).

he he! well playing with system services can have wild efects of course, but the good thing here is that as long you remember what you done you can always put things back. Theres no magical keys (not even african) to  be registered and stuff like that. If you want think of /etc as a "registry" of plain text files.

About the boot process, it's not voodoo (unless you use Arch ;)   /i always wanted to says that).
It's a funny method. All services are done by scripts located at /etc/init.d/. 
The boot up process is controlled in a delightful way. There are different level that allow different forms of boot (normal, single user, safe recovery mode,shutdown). 
They are set as folders /etc/rcX.d (X is a number from 0 to 6, indicating the level) with link(shortcuts) to the init.d scripts. No repetitions to avoid bugs and waste. 
And all is done with they names (an weird concept). If the link it's named S* it will be started. If its starts with a K* service will be killed. They have a number too, indicating the order. Ingenious. 

As an example: S40networking will start network services at step 40 (after all services numbered till 39 have run). If you want to do that manually, you can: sudo /etc/init.d/networking [start|stop|restart]. Easy :)

Of course, that it's hard to deal in practice. The app that i mention sysv-rc-conf, allows to do that easily. 
The thread i pointed it was not to be followed line by line, it's obsolete, now, in fact, but has good directions as a starting point, and explain what services do. Some times they names are a little beyond average human comprehension...

Have an happy tweaking
:)

---

### Post by OzzyFrank on 2007-06-23
That's the kind of info I was looking for (in regard to system processes), so many thanks! What about startup programs? They in there too? As in installed "third party" programs that make themselves run at startup without asking you? Thanks again.

---

### Post by Rui Pais on 2007-06-26
hi again (i almost forget to reply...)

thats the part where Linux may be very different from Windows. With Windows you don't have a separated Desktop Environment, no separation between that and the underlaying OS. So it's all mixed, all reads from registry.

Under Linux each DE/WM deals with it at it's own way... so it's hard to generalize. Under gnome you have something called gconf-editor that allow you edit gnome "registry" (it's equally enigmatic and hard to deal :()

Sometimes the best option is use gnome-control-center and check all options, turning off things you may not need, like power related daemons, update-manager, etc. Sometimes you may find the only way to turn things off, is to manually kill it on a terminal and then save the session to avoid the "creature" to came back from the dead... sometimes you may need to uninstall and that may imply remove the meta-package ubuntu-desktop (not the desktop itself)...

I think that if you want to tweak behind that you may well give an eye to other environments, like xfce or fluxbox where those stuff is much easier to deal, or even consider another distro more oriented for "user" control, like Gentoo or Arch. 

Good luck.

---

