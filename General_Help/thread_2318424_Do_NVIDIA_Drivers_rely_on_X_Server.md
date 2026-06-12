---
title: "Do NVIDIA Drivers rely on X Server?"
date: 2016-03-26
forum: General Help
---

### Post by TripleD on 2016-03-26
Installed Ubuntu Server onto my machine and everything worked fine. Terminal came up and I was able to log in. Used apt-get for xinit and kodi, uninstalled nouveau, and downloaded the latest Nvidia Driver for my card. After installing that and rebooting the machine I was greeted with a black screen.

Pressing Alt + CTRL and the various F keys did not bring up any terminals. 

I could still SSH into my computer with no problems. I tried typing in my login credentials, followed by "shutdown" or "reboot", into the tower directly and the machine responded correctly. So I know the problem is solely with getting information to the monitor.

I fiddled around with Xorg and Grub before I found a deceptively simple solution. If I started the X Server manually, via xinit, everything worked exactly as it should. I could move between different terminals and type in commands.

My current theory is that using hardware accelerated graphics, as with a graphics card, requires a Display Server. But unless you have a Display Manager the Display Server will not be started automatically. Ubuntu Server does not come with a Display Manager (really, why would it?) so Xorg is not started and I'm greeted with a black screen.

My question is: is my theory plausible, or am I misunderstanding something fundamental about the way displays are handled? I have a solution, but the whole point of my project (build a multimedia PC without a desktop) is to gain a deeper understanding of Linux, so I want to make sure I am understanding this correctly.

---

### Post by buzzingrobot on 2016-03-26
X is required to support a GUI desktop.

A display manager will start things off automatically, but isn't mandatory,  E.g, a system can be configured to boot to a console, with a user starting X and a GUI when needed.  This is usually done with the startx command and, perhaps, a bit of scripting.

If you do not intend to run X, i.e., just a server with no GUI, I'm not sure I see any discernible advantage to using the Nvidia driver.

---

### Post by kc1di on 2016-03-26
If your wondering if nvidia will support mir when it's released the answer at this time I believe is no.
But I believe there are plans to do so in the future.
[here's one article ]("http://www.phoronix.com/scan.php?page=news_item&px=mtgxmde")about it.
if your just running a server I don't see the need for Nvidia as buzzingrobot has said :)

---

### Post by TripleD on 2016-03-26
Thank you for the replies!

The main reason for Nvidia is that this is going to be used as an HTPC to access my gaming library, and hopefully streaming to other devices in my home. I'm also planning to get a VPN server working, but that's down the line.

I actually managed to get this gui-less setup working before, with "xinit", "kodi", "wine", and "steam" all playing together nicely. But it was a bit of a Frankenstein creation. I finally decided to reinstall Linux and, along with working through "How does Linix Work", rebuild the whole thing one piece at a time in order to really understand what is going on.

In this case, it's trying to figure out why the terminal does not appear when I turn my machine on after installing the Nvidia driver.

---

### Post by Bashing-om on 2016-03-26
TripleD; Hello;

It all depends on what the desktop is, and how you want to start it ( what are the dependencies !).

Have a read in the source:
```

cat /usr/bin/startx

```
Be aware, a misuse of 'startx' in an inappropriate environment can have disastrous effects . Apply the right tool to the right job.
'lightdm', for instance, requires to be started as a service .

Then also, when in doubt, read the instructions:
```

ls -al /usr/share/doc/xinit/

```

I also prefer to boot to a terminal, and activate a GUI as only on demand. As you are aware learning how the DE is started puts you a big step up on the learning curve .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TripleD on 2016-03-27
> **Bashing-om said:**
> 
It all depends on what the desktop is, and how you want to start it ( what are the dependencies !).


Thank you for the reply and advice Bashing-Om.

Ideally, I would like to have no desktop environment at all. Kodi for launching games and movies, with emacs (another thing I am trying to master) set up for Python development.

---

### Post by Bashing-om on 2016-03-27
TripleD; Uh Uhh ...

> 
launching games and movies,

is the realm of a GUI and is mutually exclusive.
Graphics ! .. if you are going to activate a graphical application, then the GUI must be started 1st  for that application to run in and have access to the required libraries.

[INDENT][INDENT]'nuff said
[/INDENT][/INDENT]

---

### Post by TripleD on 2016-03-27
> **Bashing-om said:**
> 

is the realm of a GUI and is mutually exclusive.
Graphics ! .. if you are going to activate a graphical application, then the GUI must be started 1st  for that application to run in and have access to the required libraries.


My apologies, I didn't state it well. What I meant is that I will be launching programs using xinit or startx without installing something like GNOME or KDE. For example:

```
startx kodi
```

will launch Kodi, giving me access to movies. Wine can be launched using startx as well, so that's how I will be accessing my Steam library.

---

### Post by Bashing-om on 2016-03-27
TripleD; YeYaw ...

That works well for me ( xfce4) .

[INDENT][INDENT]I do like control
[/INDENT][/INDENT]

---

