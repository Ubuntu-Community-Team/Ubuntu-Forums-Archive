---
title: "Stupid permission 2"
date: 2016-07-02
forum: General Help
---

### Post by Donnie Love on 2016-07-02
This is a continuation of this thread: [http://ubuntuforums.org/showthread.php?t=1300962](http://ubuntuforums.org/showthread.php?t=1300962), which is "closed".

However the problem still exists and I run into it quite frequently, having to beg my computer for permission to do something simple like install a font or relabel a song. Currently, I'm running Lubuntu and the solutions in the old thread apparently no longer apply.

Like this command: [gksu nautilus] seems to do nothing now. I'm not sure what it did before, but it does nothing now.

The fonts folder is controlled by the "owner", whoever that is. I still haven't found out who the "owner" is if it's not me. It should recognize ME as the owner, not itself.

So, once again, how do I get the grand glorious permission of my master the computer to add a new font?

---

### Post by The Cog on 2016-07-02
Linux is a multi-user system, designed from the ground up that way. Being a user and being administrator are separate roles. Users have limited access outside of their home folder but complete freedom within it. The administrator has full access to the whole machine of course. If you are the owner and sole user of the machine then you will be performing both roles, being a user and staying within your home folder most of the time, but occasionally switching to administrator mode when you do things like installing fonts. Try to appreciate that they are different roles, and you are either in one or the other.

The "owner" account is called root. You seem to be fighting this fact rather than accepting it. Don't fight it, that really is the way things are. 
Read and understand this link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I haven't used Ubuntu for a while (I use Xubuntu) so I can't be certain, but I thing entering the command **gksu nautilus** into a terminal should bring up a file manager window that has root privileges. That may depend on the version of Ubuntu you are using, and you haven't said. If it doesn't launch the nautilus then ask for help on that. 

Don't keep demanding that people tell you how to change the permissions system - that won't happen. Don't try to change the system permissions once you get a root nautilus working - the usual result for people who insist on doing that is that it won't boot any more and you need to reinstall.

---

### Post by DuckHook on 2016-07-03
> **Donnie Love said:**
> ...the problem...beg my computer for permission...I'm not sure what it did before, but it does nothing now....It should recognize ME as the owner, not itself...how do I get the grand glorious permission of my master the computer...I'm not sure what point there is to your hyperbole and sarcasm. The Cog has explained the way Linux security works with rather admirable patience in light of the tone of your comments. I will add only this:

If you want Linux to work like Windows, with no permissions, everyday users running amok as administrators and (at last count) over 200 million virus signatures in the wild just waiting to *actually* own those computers that their users so foolishly delude themselves into thinking that *they* own... well... it ain't happenin'. Linux will never be like Windows (thank goodness). If the security measures built into Linux are that unbearable to you, then there is only one recourse&#8213;and I say this as a simple statement of fact&#8213;you will have to run Windows.

@ The Cog

*gksudo* has been deprecated in Ubuntu, but can be installed via *apt*. Apparently, the developers have decided that any file tasks or editing tasks involving root-owned files should be done via command line. *pkexec* is now the official method to invoke graphical apps with temporary root privileges, but an app needs a PolicyKit file to use *pkexec* and neither *gedit* nor *nautilus* come with predefined PolicyKit files in a base install. To install PolicyKit files for *gedit* and *nautilus*, simply do:```
sudo apt install nautilus-admin
```This is a live land-mine for certain users, but Linux is about choice, even if that choice is a determination to hosing one's system.

---

### Post by Donnie Love on 2016-07-03
Sorry for the sarcasm. This problem has aggravated me for years. I get that Linux has all the built-in security - I love that. I just want control of the fonts folder. Hardly a high-level security risk. I'm not trying to do anything earth-shattering like changing the nature of the universe, I just want to add a font. It should be simple, but it's way overcomplicated. I just think it's silly.
Windows is even more aggravating.
But I got it to work. Thanks for the help.

---

### Post by The Cog on 2016-07-03
I have to admit that coming from Windows it was not natural to be aware of the difference between user and administrator roles. But nowadays I can always answer "Am I using or administering?" without thinking. Surely, even Windows users must be getting a hint of this now? People at work sometimes have to "run as administrator" to make things work (if IT have graced them with admin rights).

@DuckHook Thanks for the note. It's a long time since I used a graphical file manager as root. I notice on my Xubuntu system that gksu and gkduso are both installed by default as well as pkexec. All three succesfully launch thunar as root, but pkexec has a prettier password prompt.

---

### Post by HermanAB on 2016-07-03
Long ago, there was a distribution where everything ran as root.  It was called Lindows.  It didn't last very long.

Android is also an example of what happens when the security model of Linux is broken on purpose.

The problem is that a compromised machine affects other users and everything is now interconnected.  So while I or most others don't care how anyone mucks up his own computer, we do care about the blow back coming our way over the net and that is why Linux is generally locked down and will remain so.  It ensures that only people who have some inkling of what they are doing, is able to muck things up and most won't.

---

### Post by oldos2er on 2016-07-03
> **Donnie Love said:**
> I just want control of the fonts folder. 

You can create a .fonts folder inside your home folder (the . preceding fonts indicates it's a hidden folder) with ```
mkdir .fonts
``` You can move or copy any fonts to it you like, and afterwards run ```
sudo fc-cache -fv
``` to update all font caches. No elevated permissions needed except for that last command.

---

