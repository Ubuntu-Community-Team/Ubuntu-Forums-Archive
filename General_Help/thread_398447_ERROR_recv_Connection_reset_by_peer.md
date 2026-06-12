---
title: "ERROR: recv: Connection reset by peer"
date: 2007-04-01
forum: General Help
---

### Post by masteryoda on 2007-04-01
I am having problems with connecting to windows thru rdesktop :( 
i am getting following message when i run rdesktop :confused: 

Autoselected keyboard map en-us
ERROR: recv: Connection reset by peer

any help will be greatly appreciated 

thanks in advance :)

---

### Post by masteryoda on 2007-04-03
anyone???

---

### Post by gp2x on 2007-06-17
Cant help, but Im getting the same thing!

---

### Post by HeXonX on 2007-07-22
Make sure you fill out the client hostname.

---

### Post by ilektron on 2007-09-19
I'm getting the same error with windows xp pro on vmware server on my local machine.  I nmap'ed it and it shows port 3389 open.  I have a bridged connection.  Nothing I do seems to change the error message.

---

### Post by kosu on 2007-10-04
Hello ilektron,

the same problem ist bugging me for x days now.
I copied two VMs (Win XP pro, Win Vista Business) from my old System (Suse 10.2) to my new Ubuntu workstation and installed the VMware-Server. Everything is working fine, only rdesktop from my host to my guests does not work.

Magically, connections from other workstations (Linux OR Win) are accepted without any problems :confused:

Did somebody have any solution for this?

Thx

---

### Post by mazirian on 2007-11-12
Any progress on this?

Nothign changed on the remote server's end, so something's up with rdesktop.

---

### Post by weblordpepe on 2007-11-12
Am I on IRC?
Connection reset by peer means that your connection has been disconnected from a remote source. 
I know that Windows doesn't let you log on to the local console with Remote Desktop. It doesn't even let you type in localhost or 127.0.0.1. Maybe there is some kinda awkward thing going on? Just a guess.

---

### Post by mazirian on 2007-11-12
I'm connecting to a Windows 2000 Server box at work, which I have connected to using rdesktop for years. I stopped being able to make the remote connection shortly after two things happened: (1) rdesktop version bumped; (2) a new firewall was installed at the office.  As no one else (the other employees use windows xp pro laptops for this) is hindered from making the remote connection, I assume it must be an rdesktop issue.  Anyway, this is one of those applications I have little experience troubleshooting.

---

### Post by weblordpepe on 2007-11-12
There's a new version of rdesktop? Awesome. Hey, you could try using a different version of the rdp protocol (RDP or RDP 5).
I would strongly suspect the firewall. Connection reset by peer is the error you get on IRC all the time when the server bumps you off.

---

### Post by MrDetermination on 2007-11-28
Me too.  Bump.

Sucks.

I installed Gnome-RDP and RemoteDesktopClient but I guess those are just different front ends for the same thing TSC is using as the give similar or identical errors.

Would really appreciate the help in reconciling.

Things like this are why I lose my Linux steam and enthusiasm.  No support/response on something I *must* have.  I basically have to go back to Windows and then I start always booting to Windows because I know this is something I have to face when I come back in to Linux and that may mean reinstall Ubuntu... etc, etc, etc.

Dear Linux,

I so want to love you. Stop frustrating me.

xoxoxo

---

### Post by mazirian on 2007-11-29
Those are all backends for rdesktop.  Don't blame linux, or even rdesktop, blame M$ for making *nix developers have to reverse engineers things like their remote desktop connection protocols!

---

### Post by MrDetermination on 2007-11-29
LIke others before me in this thread, it was working just fine and nothing changed on the server side.  Linux just vomits from time to time and the explination is (to us novice users) illusive.

Just seems like in Windows, assuming I am paying attention to my usage, at least I have some notion of what I've done to cause such a thing, if anything.

---

### Post by mazirian on 2007-11-30
At least as a linux user you have the chance to fix things.  I don't know how many times I've contacted the developers of a project like rdesktop and received help. So, rather than giving up here, we should work on solving this problem the correct way.  Run rdesktop using strace, check the rdesktop bugs and mailing lists, if there are any, and so on.  

I haven't really tried to hard to fix this yet, mostly because doing so means I may have to work from home again on occasion, but I'll look into it again this evening and let you know what I find.  

Over time you'll find that you become quite familiar with the reasons things go wrong when using the various flavors of *nix and be releived that you're not using windows anymore, because there is almost always an answer and you can get under the hood and fix it yourself.

---

### Post by Clochard on 2007-12-14
I had this exact problem happen today, and there hasn't been any recent rdesktop updates to gutsy.  But I did resolve it, and here's my thinking.

When I logged in today I was greeted with a dialogue asking me if I wanted to keep my X keyboard settings (PC 105) or my Gnome keyboard settings.  I'm not really sure what I did to get that problem, but I chose to keep the Gnome keyboard settings (evdev).

I then tried to use rdesktop, and received this error.  Consistently.  Chaning RDP version didn't help, etc.

Just for fun, I went into my keyboard preferences and changed it from evdev back to Generic PC 104.  I then logged off and back on.  I am now able to connect to my XP box normally.

So my suggestion is that this is related to the keyboard settings of your Gnome desktop.  Try changing them in the keyboard preferences and logging back on.

---

