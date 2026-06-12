---
title: "Get rid of CRUFT"
date: 2014-12-19
forum: General Help
---

### Post by mayagrafix on 2014-12-19
What is a good way to get rid of built up Cruft in the Ubuntu OS? I ran a search in the Ubuntu Software Center and found a "program that finds any cruft built up on your system" which has only one review, and then not good, plus it is still in development. When I ran it, nothing seemed to happen.

When I tried to run cruft-remover and or install it no joy.

cruft-remover: command not found
bigdaddy@bucket:~$ sudo apt-get install cruft-remover
[sudo] password for bigdaddy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
C:/> Unable to locate package cruft-remover

Thanx for any help.

---

### Post by vasa1 on 2014-12-19
> **mayagrafix said:**
> ...
**C:/>** Unable to locate package cruft-remover
...How did you get that prompt?

Anyway, isn't Bleachbit supposed to be the usual cruft remover? I've never used it because I prefer to handle things myself.

---

### Post by mayagrafix on 2014-12-20
Good eye! I thought no one would notice ;)

Ill give Bleachbit a go. Thanx!

---

### Post by vasa1 on 2014-12-20
> **mayagrafix said:**
> Good eye! I thought no one would notice ;)

Ill give Bleachbit a go. Thanx!

But be careful and read the instructions. I've seen posts from people who've been a bit casual with it :)

---

### Post by vasa1 on 2014-12-20
BTW, searching [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) for **cruft-remover** comes up empty. Google throws up a hit for Jaunty which I guess isn't of much use now ;)

---

### Post by OrangeCrate on 2014-12-20
> **mayagrafix said:**
> What is a good way to get rid of built up Cruft in the Ubuntu OS?

<snip>



**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Ignore the original post date - the info is just as relevant now, as it was then.

---

### Post by Bucky Ball on 2014-12-20
> **vasa1 said:**
> But be careful and read the instructions. I've seen posts from people who've been a bit casual with it :)

^^^
This. Bleachbit can really screw things up if you don't keep it well wrangled! I speak from experience when I first started using Ubuntu. ;)

> **OrangeCrate said:**
> **HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Ignore the original post date - the info is just as relevant now, as it was then.

+1. There are a few things that are possibly outdated. 'localepurge' and 'deborphan' don't seem to be in the repos anymore (thread suggests installing them with Synaptics, but they aren't there). Desipite this, they did install via a terminal with 'sudo apt-get install' command when I tried it. Odd. :-k ;)

---

### Post by vasa1 on 2014-12-20
> **Bucky Ball said:**
> ... 'localepurge' and 'deborphan' don't seem to be in the repos anymore (thread suggests installing them with Synaptics, but they aren't there). Despite this, they did install via a terminal with 'sudo apt-get install' command when I tried it. Odd. :-k ;)
They're visible for me with Synaptic in 14.04. Which version did you test in?

---

### Post by Bucky Ball on 2014-12-20
> **vasa1 said:**
> They're visible for me with Synaptic in 14.04. Which version did you test in?

Weird. I'm using 14.04 also, but a minimal install with xfce. Can't see how that is going to make a lot of diff, though. Still using all the default, standard repos ... :-k

* Just checked again and now I have installed them via a terminal, they are there, even though they weren't before I installed them with a terminal. Go figure. Anyway, that's my conundrum so back to the topic ... ;)

---

### Post by OrangeCrate on 2014-12-21
> **Bucky Ball said:**
> 

<snip>

+1. There are a few things that are possibly outdated. 'localepurge' and 'deborphan' don't seem to be in the repos anymore (thread suggests installing them with Synaptics, but they aren't there). Desipite this, they did install via a terminal with 'sudo apt-get install' command when I tried it. Odd. :-k ;)

That was odd, but, at least you have it worked out.

Edit:

I install most everything from the terminal. Maybe that's why synaptic was listed in the repos when I checked. But, I have no explanation as to why localepurge was there from the git go (which I do not have installed).

---

### Post by sudodus on 2014-12-21
Thanks for valuable tips :-)

My 2 cents: Ubuntu Tweak's janitor, according to this link

[http://blog.ubuntu-tweak.com/2014/04/21/ubuntu-tweak-0-8-7-released-14-04-ready.html](http://blog.ubuntu-tweak.com/2014/04/21/ubuntu-tweak-0-8-7-released-14-04-ready.html)

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update

sudo apt-get install ubuntu-tweak
```

---

### Post by ian-weisser on 2014-12-21
> **mayagrafix said:**
> What is a good way to get rid of built up Cruft in the Ubuntu OS?

If you discover a program that, upon uninstall, leaves 'cruft' behind, please file a bug report.

Packages should generally be nullipotent: They should not be leaving behind *any* traces or side effects from their past installation.
Any traces left behind should be treated as a bug, reported, and fixed, with three exceptions:

- The downloaded .deb file itself should remain in cache: /var/cache/apt/archives/foo.deb . You can remove this with the command 'apt-get clean foo'. It remains in the package cache to make reinstallation faster.
- Config files in /etc. You can remove these by using 'purge' instead of 'remove': 'apt-get purge foo'
- Config and data files in your /home. These should not be removed by any automated tool or application under any circumstances due to the risk of erroneous data loss (loss of your personal data!). You can can remove these as you discover them.

If you feel that the application is improperly filling your /home by storing non-user data or non-personal caches or non-user settings in your /home (instead of, say, in /var or /etc), please report that as a bug, too.

---

### Post by vasa1 on 2014-12-21
> **ian-weisser said:**
> If you discover a program that, upon uninstall, leaves 'cruft' behind, please file a bug report. ...
+1. Or at least post details here to let others replicate the experience.

---

