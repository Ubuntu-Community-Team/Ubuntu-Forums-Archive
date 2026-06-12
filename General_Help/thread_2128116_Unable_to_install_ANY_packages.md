---
title: "Unable to install ANY packages"
date: 2013-03-22
forum: General Help
---

### Post by pallath on 2013-03-22
I'm unable to install any packages (from the Software Center and even .deb files from the net) in my new install of Ubuntu 12.10.

(For the full story of WHY I had to do a new install, see my thread at [http://ubuntuforums.org/showthread.php?t=2127246](http://ubuntuforums.org/showthread.php?t=2127246)- just in case it could be one of the causes of the problem)

Well, every time I try to install a package from Software Center, (or, e.g. GoogleChrome browser, a .deb file), I get dependency errors.

Screenshots below:
[ATTACH=CONFIG]240427[/ATTACH][ATTACH=CONFIG]240428[/ATTACH][ATTACH=CONFIG]240429[/ATTACH][ATTACH=CONFIG]240430[/ATTACH][ATTACH=CONFIG]240431[/ATTACH]

What could be the problem???

---

### Post by AIREE.Shadow on 2013-03-22
sudo apt-get -f install and/or sudo dpkg -a --configure

those commands may help you to resolve that problem

---

### Post by schragge on 2013-03-22
If it is actually a problem with RAM like your previous thread suggests, try updating your system from the command-line with
```
sudo apt-get update&&sudo apt-get upgrade
``` Best do it from a text-only console (there are six of them **Ctrl**+**Alt**+**F1** through **Ctrl**+**Alt**+**F6**, with **Ctrl**+**Alt**+**F7** running your GUI session). Command-line tools generally tend to use less memory, so there's a chance that the problem will go away, at least, for a while. BTW, have you tried to run the system with only the new 2GB RAM module installed?

OTOH, if I knew nothing about your previous problems with RAM, from the screenshots alone I'd suppose that you're trying to install on the wrong architecture (e.g. 64-bit packages on a 32-bit system). Or just the package indexes got corrupted. Then simply remove them:
```
sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ibjsb4 on 2013-03-22
Just sounds like a update is needed.  So [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And try installing a package again.

---

### Post by pallath on 2013-03-23
Thanks for the advice... I'll try it out.

As for your question, Schragge- yes, I've run the PC on my new 2gb module- still the same result. I'm beginning to feel that I should change my PC after all- mebbe it is the mobo that's gone kaput.

--------------------------------------------------

Update: Rhythmbox is unable to run- it crashes every time.

On trying to download Fluendo MP3 Plugin, the installation window crashes.

--------------------------------------------------

---

### Post by pallath on 2013-03-23
Ok- **sudo apt-get update  **fied the problem.

Thanks a lot, everyone.

But an interesting thing is that I seem to be getting wierd errors in some places- unexplained crashes which occur only maybe once or twice.

E.g.- VLC didn't download the first time, but downloaded on my second attempt.
        Google Chrome (stable, .deb file) isn't installing, bcse the messgae "Only install this file if you trust its origin' appears over and over again- every time.

---------------------------------------------------------------------------------

Update: Well, Chrome finally did install- after a lot of coaxing.

But- OK- it seems that at least I'm able to do stuff, although, admittedly, with a lot of problems and errors.

Thanks a lot guys, for helping me fix my messed up  computer.

---

### Post by ibjsb4 on 2013-03-23
> But an interesting thing is that I seem to be getting wierd errors in  some places- unexplained crashes which occur only maybe once or twice.

I suggest that you start a new thread on this.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by sanderj on 2013-03-23
> **ibjsb4 said:**
> I suggest that you start a new thread on this.



Please note that the OP has memtest86 errors on his system. See [http://ubuntuforums.org/showthread.php?t=2127246&page=2&p=12568602#post12568602](http://ubuntuforums.org/showthread.php?t=2127246&page=2&p=12568602#post12568602)

HTH

---

### Post by haqking on 2013-03-23
You have dodgy RAM, reaplce it !

---

### Post by Alan F on 2013-03-23
> **haqking said:**
> You have dodgy RAM, reaplce it !

and stop trying to install additional programs until you have the basic Ubuntu 12.10 working correctly. Adding more programs will never fix a broken system.

---

