---
title: "Window decorations gone after installing compiz fusion git"
date: 2008-07-07
forum: General Help
---

### Post by MaxIBoy on 2008-07-07
I installed compiz fusion git, and something disappeared. (I think it's called window decorations or titlebar, but I always took it for granted so I don't know what they're called. They have the name of the window and the minimize/maximize/close buttons on them.) Anyway, they're gone, see attached screenshot of a window. Window decorations are still enabled in compizconfig.


Also, windows that are opened are way at the top of the screen, under my top panel. Luckily I know about super+click-'n-drag for moving windows or I'd be completely screwed.

What did I do wrong, and how I fix it? I know I can use key combos for everything but it's nice having my visual methods as well. Also, I don't know all the key combos.

---

### Post by karasuman on 2008-07-07
Have you tried disabling the decorations in advanced options and reenabling them?  Switching themes under appearance settings?  I'm sorry I can't be more helpful.

---

### Post by MaxIBoy on 2008-07-07
I've tried that, it doesn't seem to do anything.



Do you think that uninstalling the git version will work?

---

### Post by Victormd on 2008-07-07
You need to add the fusion-icon to startup sessions. With fusion-icon, you will choose your windows decoration and that should do the trick (I'm assuming that compiz is working :)).

---

### Post by isaacj87 on 2008-07-07
Before you uninstall, I have a couple of questions for you...

1) Did you remove the Compiz that came installed by default in Hardy (I'm assuming you're on Hardy) before installing from Git?

2) How did you install from Git? Did you use a script or did you manually clone each and compile.

3) Does running 

```
emerald --replace
```

in Terminal fix anything?

---

### Post by Victormd on 2008-07-07
> **isaacj87 said:**
> 1) Did you remove the Compiz that came installed by default in Hardy (I'm assuming you're on Hardy) before installing from Git?

2) How did you install from Git? Did you use a script or did you manually clone each and compile.

3) Does running 

```
emerald --replace
```

in Terminal fix anything?

good point

---

### Post by MaxIBoy on 2008-07-08
I didn't replace it, the original is still there. I'll try the emerald --replace thing.

---

### Post by MaxIBoy on 2008-07-08
Okay, "emerald --replace" put a window decoration on only the terminal window. Nothing else. Closed the terminal, and it wasn't on the terminal again next time. Plus the window decoration was weird and I didn't like the look of it at all.



As for how I installed it, I just followed this howto:
[http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/](http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/)

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> I didn't replace it, the original is still there. I'll try the emerald --replace thing.

Are you saying that you didn't remove the original Compiz? That could cause conflicts with the Git installation...

You should probably remove the Git installation, remove the original repo version of Compiz (the one installed by default) and then re-install from Git.

I can't say whether or not you should for sure, but I always do (whenever I compile from Git). I remember I left a package installed from the default Compiz and caused me some trouble.

---

### Post by MaxIBoy on 2008-07-08
How would I do that? Delete the folder? apt-get install uninstall compiz-fusion?

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> Okay, "emerald --replace" put a window decoration on only the terminal window. Nothing else. Closed the terminal, and it wasn't on the terminal again next time. Plus the window decoration was weird and I didn't like the look of it at all.



As for how I installed it, I just followed this howto:
[http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/](http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/)

Ah...I see...You used a script...

Okay, well I poked around in the script, and I didn't see anything in there that removed the default Compiz...that's not good!

**Follow the instructions from the blog to remove Compiz from git.** Then run this command:

```
sudo apt-get remove compiz*
```

**Make sure that it only removes Compiz related packages, there should only be 12 or 13 (maybe less)**

then run...

```
sudo apt-get remove libdecoration0
```

Compiz should be completely off your system...

Then re-run the script and install from git again.

---

### Post by MaxIBoy on 2008-07-08
> maxtothemax@maxtothemax-laptop:~$ cd compiz-git
maxtothemax@maxtothemax-laptop:~/compiz-git$ ./compiz-git uninstall
Configuration-file says to use sudo, following.

Distribution specified in configurationfile, following.

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

[sudo] password for maxtothemax: 
maxtothemax@maxtothemax-laptop:~/compiz-git$ cd ..
maxtothemax@maxtothemax-laptop:~$ rm -r compiz-git
maxtothemax@maxtothemax-laptop:~$ sudo apt-get remove compiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-git-newest.tar.gz
maxtothemax@maxtothemax-laptop:~$ 
Huh?

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> Huh?

Lol...you and me both man...

Well, go into Synaptic and do a search for "Compiz" are any packages installed?

I really don't like that script...

---

### Post by MaxIBoy on 2008-07-08
Just about all of them. Should I get rid of them all?

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> Just about all of them. Should I get rid of them all?

Yeah, remove all of them...Make sure that emerald, fusion-icon, and libdecoration0 are gone as well...

That was strange that the command I gave earlier didn't work...

Once all of Compiz is removed...re-install from git and see if you have better luck. If not, we'll try something else :D

---

### Post by MaxIBoy on 2008-07-08
A little odd... emerald wasn't even installed (or didn't register as installed under synaptic.

Anyway, I'm going to build from git again, wish me luck.

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> A little odd... emerald wasn't even installed (or didn't register as installed under synaptic.

Anyway, I'm going to build from git again, wish me luck.

Yeah, more than likely it wasn't. It isn't installed by default. Good luck! Let me know how it goes. :D

---

### Post by MaxIBoy on 2008-07-08
It worked! Thanks for the help. Now excuse me while I recover my settings.:)

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> It worked! Thanks for the help. Now excuse me while I recover my settings.:)

Ahhh...sweet success :)

My guess is there was a conflict between the two installed versions of Compiz, but it's in the past now huh? Glad to hear it's all working.

---

### Post by MaxIBoy on 2008-07-08
Except for a couple of hiccups: some plugins (show mouse, splash, and workspace naming are all I've found so far) will not let themselves be selected, they somehow de-select themselves. I'm guessing more plugins will exhibit this problem.

---

### Post by isaacj87 on 2008-07-08
> **MaxIBoy said:**
> Except for a couple of hiccups: some plugins (show mouse, splash, and workspace naming are all I've found so far) will not let themselves be selected, they somehow de-select themselves. I'm guessing more plugins will exhibit this problem.

Try a restart...might clear up the problem.

---

### Post by MaxIBoy on 2008-07-08
No such luck, it still glitches. I'll record a video of it later, but right now I need to sleep.

---

### Post by Victormd on 2008-07-08
If you're still having trouble, take a look at this how to install compiz git. There's a detailed step on removing all traces of the previous version of compiz fusion.
[http://ubuntuforums.org/showthread.php?t=643485](http://ubuntuforums.org/showthread.php?t=643485)
This is what I used to get it working...

and here for additional plugins (se my post#82):
[http://ubuntuforums.org/showthread.php?t=820802&page=9](http://ubuntuforums.org/showthread.php?t=820802&page=9)

also check my post#86 on how to remove compiz and compiz-git to start from scratch. Ultimately that's what I did to get it all working.

---

