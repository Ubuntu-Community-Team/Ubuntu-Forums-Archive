---
title: "WINE: How do I install for all users?"
date: 2007-07-10
forum: General Help
---

### Post by ThrashJazzAssassin on 2007-07-10
When I install something in WINE it is only accessible by the user who installed it. How can I set it up so it installs for all users?

It would also be cool if the installed app was added to a shared WINE submenu in the Applications menu.

---

### Post by thunderduck3141 on 2007-07-10
chreate soft links to the program and modify its permissions

---

### Post by ThrashJazzAssassin on 2007-07-13
I asked about this on the WINE chat room

> ME: is there an easy way to install an app with wine and have it available for multiple users?

killertux: "yes", but it's unsupported and complicated and it depends on the applicatation.

killertux: basicly what you need to do is install app in one user then copy changes in registry keys and the application to other users ~/.wine then make new c: or better d: pointing somewhere where all users have at lest read acces and also write if app requires that.

nanonyme: killertux: wouldn't WINEPREFIX be a better option?

nanonyme: (if it works)

nanonyme: that is, use only one .wine folder

killertux: nanonyme: well WINEPREFIX and be used with that "trick" too.

killertux: sure you could use _ONE_ registry where all users have access and set that to read+write for all... but remember different wineservers are not aware of eatch others since all multi user stuff is missing from Wine... when wineserver closes it writes the registry so last wineserver that is closed.

killertux: this means registry keys could be "lost" because this stuff... anyway I do not recoment using this kind of tricks at all since it's all so hacky.

nanonyme: wineserver -d0 looks nice

ME: I like the idea of one .wine directory

nanonyme: any particular reason not to have one account dedicated for wine?

nanonyme: that all wine users on the computer can use

ME: its a good idea but not very elegant

ME: i understand the problems now. thanks for your help

---

### Post by stchman on 2007-07-13
> **ThrashJazzAssassin said:**
> When I install something in WINE it is only accessible by the user who installed it. How can I set it up so it installs for all users?

It would also be cool if the installed app was added to a shared WINE submenu in the Applications menu.

That should not be when I do a which win it tells me /usr/bin/wine

As far as I know that folder is not limited to just one account for reading.

---

### Post by ThrashJazzAssassin on 2007-07-13
stchman: I'm not talking about WINE itself. I'm talking about the windows apps I install with WINE which install to  my ~/.wine folder

---

### Post by stchman on 2007-07-13
> **ThrashJazzAssassin said:**
> stchman: I'm not talking about WINE itself. I'm talking about the windows apps I install with WINE which install to  my ~/.wine folder

Ok, then yes.  ~ is the CLI shortcut for YOUR home folder.  If you type cd ~ in a terminal then you will be taken to /home/<your home>

By default only the user logged in and root can get to your /home folder.  You need to transfer those Win programs to another folder where all can see.  I recommend another partition.

There might be ways to change others users to get to your /home folder but I would not since it is a security feature.

---

### Post by UK-Wobbie on 2007-07-13
> **thunderduck3141 said:**
> chreate soft links to the program and modify its permissions

I say what thunderduck3141 say, Thats the easy way on doing something like this!

---

### Post by ThrashJazzAssassin on 2007-07-13
> **UK-Wobbie said:**
> I say what thunderduck3141 say, Thats the easy way on doing something like this!

Have you tried it? Does it work? How do you do it?

---

