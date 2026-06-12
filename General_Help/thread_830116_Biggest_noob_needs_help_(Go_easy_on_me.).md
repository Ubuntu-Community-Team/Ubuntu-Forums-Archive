---
title: "Biggest noob needs help (Go easy on me.)"
date: 2008-06-15
forum: General Help
---

### Post by Gus122000 on 2008-06-15
Today i decided to install Ubuntu because i was starting to grow tired of vista :KS I have been using windows for about my whole life since I was 10 (17 now lol)
now that i switched to Linux I feel as if i just started using a computer all over again.I have no idea how to do anything.Ive tried to download a couple themes and install them (such as a mac os theme i found on gnome look) but no dice.Some of them are in zip format and they keep giving me errors when i try to open them.Heck i don't even know how to install anything for sure.I think i got beryl installed but i'm not even really sure about that.I'm not even really sure what version of Ubuntu do i have.Could someone who might have a little extra time that might have yahoo or msn messenger help me a bit ? Or threw the comment would be fine (btw:I've looked threw the guides but there just not doing it for me for some reason..Also sorry if i posted this in the wrong section.)

:confused::confused::confused::confused::confused::confused::confused:

---

### Post by Pjotr123 on 2008-06-15
OK. Start with this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

There's a lot more beginners info on my website; feel free to check it out.  :-)

Greeting, Pjotr.

---

### Post by Quantumstate on 2008-06-15
Go *easy* on you?!  This is Linux man. [-o<


Now; the first thing you need to decide is which desktop you're going to use.  I can tell you right now that sooner or later you're going to want a bit more control than Gnome gives you and so will graduate to KDE.  KDE is no more difficult than Gnome, but hidden under the covers is far more power and control, if you're willing to learn about it.  If you want to start with KDE, get thee over to Kubuntu, forthwith.  

You don't say what kind of machine, but if a Core2Duo download the CD image for Hardy Heron AMD64 Desktop, and install it.

Don't download styles from the [Internets](http://www.youtube.com/watch?v=_cZC67wXUTs) just yet because at least half of them are busted and you'll wreck your install.  Use Adept to install the official styles & color schemes and stick with those for now, while you learn the OS.  Skip Beryl, Compiz, and Compiz Fusion for now, unless you want a real mess on your hands;  not for beginners.

---

### Post by drs305 on 2008-06-15
> **Gus122000 said:**
> I'm not even really sure what version of Ubuntu do i have.

Okay, here is your introduction to the command line. Open a terminal (Applications, Accessories, Terminal) and type this to see what version you have:
```
uname -a
lsb_release -a
```

Mine is:
```
Linux mycomputer 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

```
It tells me I'm running linux, my computer's name is mycomputer, I'm running kernel 18 on a 64-bit computer. The second command will tell you the flavor, version and code name. For me, it's Ubuntu 8.04 hardy.

By the way, you will probably be using Terminal a lot. Go back to the menu, and when you see the Terminal icon, drag it to the top or bottom panel and release it to create an easily available shortcut.

Welcome to ubuntu. Enjoy!  :)

---

### Post by Gus122000 on 2008-06-15
> **drs305 said:**
> Okay, here is your introduction to the command line. Open a terminal (Applications, Accessories, Terminal) and type this to see what version you have:
```
uname -a
lsb_release -a
```

Mine is:
```
Linux mycomputer 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

```
It tells me I'm running linux, my computer's name is mycomputer, I'm running kernel 18 on a 64-bit computer. The second command will tell you the flavor, version and code name. For me, it's Ubuntu 8.04 hardy.

By the way, you will probably be using Terminal a lot. Go back to the menu, and when you see the Terminal icon, drag it to the top or bottom panel and release it to create an easily available shortcut.

Welcome to ubuntu. Enjoy!  :)

Linux Gus-PC 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

Well that solves that.Thanks

---

### Post by ibuclaw on 2008-06-15
Hi there Gus.

You have no need to apologise about anything. Everyone has absolutely no problem at all with you needing help.

Although this section in the forums is perfectly suitable, I do recommend that you try posting in the [Beginners Forums]("http://ubuntuforums.org/forumdisplay.php?f=326"), there is a dedicated team of people (note my avatar) who will try their utmost to safely guide you through the fog of learning to administer a completely new system.

And lastly, if you would like to talk to us personally with issues in a one to one chat, feel free to pop into our IRC channel #ubuntuforums-beginners.

The preferred IRC client of choice is usually xchat.
You can install it by going into "**Applications>Add/Remove...**" in Gnome menu, and search up "xchat" and mark it to install, then apply.
NOTE: you can use this method to install most/all your applications.

XChat is ran by going into "**Applications>Internet>XChat IRC**"
Then join "**FreeNode.net**" and join the chatroom "**#ubuntuforums-beginners**".

Regards
Iain

---

### Post by drs305 on 2008-06-15
Just so you know: There is a 64-bit forum that deals with items specifically for the 64-bit version of ubuntu. Most of your questions can be answered right here, but if they involve 64-bit issues they are best addressed over there. 

So how do you know a 64-bit issue? First, there have been great strides made in the availability of apps and applets in 64 bit. A couple of issues still remain. Historically, there has been limited support of java in 64-bit but gains area being made every day and it's almost been solved. Flash was another issue that used to be a problem. If you have issues with either flash or java, do a search of the 64-bit forum. A poster named Kilz has done some really fine work over there and has written several tutorials to help get 64-bit apps running well. 

If you use synaptic, any listing you see is for the 64-bit version you are running. You can force install 32-bit apps but hopefully that won't be necessary.

PS. I've sent you a PM.

---

### Post by spiderbatdad on 2008-06-15
> **tinivole said:**
> Hi there Gus.

Although this section in the forums is perfectly suitable, I do recommend that you try posting in the [Beginners Forums]("http://ubuntuforums.org/forumdisplay.php?f=326"), there is a dedicated team of people (note my avatar) who will try their utmost to safely guide you through the fog of learning to administer a completely new system.


The Beginner's Team is in no way complete representation of the "dedicated team of people" who comprise this forum. This forum is part of a community of Ubuntu users. And memberships to teams does not give more or less validity to the contributing efforts of anyone in this forum.

---

