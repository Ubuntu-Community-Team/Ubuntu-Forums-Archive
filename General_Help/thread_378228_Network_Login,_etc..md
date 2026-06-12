---
title: "Network Login, etc."
date: 2007-03-07
forum: General Help
---

### Post by Andruk Tatum on 2007-03-07
Hello, my boss is still on the-os-that-is-not-to-be-named 98.  He would like to upgrade the office workstations OSes/software, but neither XP nor Vista are a good alternative for our office (we're keeping/running on really old computers).  The main premise is that we are trying to use the fewest M$ products as possible, including M$ file servers, workstation OSes, office software, etc, while still maintaining backwards and cross-compatibility between the M$ world and the Linux/OSS world.  Flash drives, ipods, IMing, A/V editing (mostly transcoding for web), and casual office work must be supported.  This is the office layout:

[LIST]
[*]IPX/SPX for inter-office stuff
[*]TCP/IP to connect to the outside world
[*]Netware file Server (ill find out what version) on IPX
[*]Workstation comps must be user friendly for non-Linux (and a few really stupid) employees
[/LIST]

I was just wondering how well/if-at-all Ubuntu supports this particular scenario, and how hard it would be for me and a sophomore CS major to set it all up.  I run it at home and would love it at work.

Thanks in advance,
-Andruk Tatum

---

### Post by gradedcheese on 2007-03-07
It will work, you can check with Novell for Netware compatibility stuff though.

What I would do is:
- dump the file server and replace it with a PC running Ubuntu with Samba shares, both Windows and Linux users can access them and now there's no more IPX
- install Ubuntu and all that, have Ubuntu mount the Samba shares, map them as network drives for the Windows users
- set up ssh and "remote login" as needed for Ubuntu (allows you to connect via VNC clients), Ubuntu users can also use Application->Internet->Terminal Server Client to connect to Windows PCs, if you have any (Win2k and above) running TS (RDP).

One of the good things about Linux in the corporate desktop is specifically that users don't know how to make their iPod work and do other things that they shouldn't.  They're at work, and they probably should just do their jobs.  You can set any of that stuff up as needed, but some companies see it as a good thing ;)

Getting rid of Windows is a good thing, especially good old '98.  It's unsupported, extremely insecure, and straight out dangerous.  However if you don't plan to get rid of your "newest MS  apps" at the same time (or at least scale it down a bit), then maybe buying some Win2k licenses is a better option.  There are Linux ways, I imagine, to do anything that these applications do for you, so why not dump them all?

Same goes for Netware... this was a popular thing many years ago, and now very few places use it.  Just get rid of it, a file server is a file server, and you don't need it to be Netware anymore.

> 
TCP/IP to connect to the outside world


I hope so ;)  It sure beats teams of trained messenger pigeons...

> how hard it would be for me and a sophomore CS major to set it all up

no idea, I guess it depends on your comfort level with this stuff.  You can always as for help here.  Make a detailed plan first, get your specific questions answered, then roll it out carefully.

---

### Post by Andruk Tatum on 2007-03-08
Well, the thing is, is that he wants to keep it...can't convince him otherwise.  We do have a lot of records (not too many that we couldn't export...we're just a bit busy).  And IPX is not only for us, but for a few other departments as well.  They need the fileserver too.  Sorry, forgot to mention that.

We do have times where it is nice to listen to our ipods (some time we do just sit in the office, and wait for something to go wrong with the event we're hosting).

And we need multiple users to be able to access their network accounts, and we don't want to have to have them as users on every single machine (boss tells me XP and possibly 2k require this), just on the server.

You did clarify one thing, though, I was thinking outside the box for solutions to increasing the "speed of the internet", and I was thinking of teams of trained messegner pigeons.  ;)

Sorry, boss says we can't just dump it all.  And it has to be user-friendly.  I would totally run the office completely on Ubuntu, but I am simply a peon/pee-on (that's why I'm doing this and not him).

---

