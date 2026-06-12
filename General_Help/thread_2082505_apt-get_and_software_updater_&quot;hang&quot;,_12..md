---
title: "apt-get and software updater &quot;hang&quot;, 12.10"
date: 2012-11-09
forum: General Help
---

### Post by Chakravant on 2012-11-09
I cannot update my version of Ubuntu 12.10 in ant way shape or form I know of.  Software Updater just gives me the loading bar for "querying software sources" for over an hour.  Sudo apt-get update gives me multiple "Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)" errors, usually around quantal Release.gpg, quantal-updates Release.gpg, and quantal-security Release.gpg.  The system never gets above 25%, often only 19%, then terminal hangs, staying at that % for over an hour and having the cursor stop blinking.  The last archive it gets to before freezing is often quantal/restricted amd64 Packages/DiffIndex.

I've tried removing both "locks" and using apt-get update, and tried the --fix-missing "thing".  I've tried moving my software sources between US and Main, as well as reducing all of my installed updates to -security and -updates, using main, restricted, universe, and multiverse.  I saw a similar known bug that has a workaround, requiring you to change your DNS to something.something.222.222 and something.something.220.220.  I've tried reinstalling.  Nothing has helped.

I noticed on my first installation, when I chose to update during install, the updating "hung" on a single file, which I neglected to write down.  For the second installation, I chose to update later.  There was no change in dysfunction, however.

Firefox accesses the internet just fine.

Ideas?  I'm not 100% fluent with Linux, but I'd like to think I have above average general computer knowledge.  Sorry for my poor Linux speak, but DOS and BASIC were my first languages. ;P

---

### Post by mörgæs on 2012-11-11
Hi, welcome to the fora.

Have you tried installing using the minimal ISO?
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by ibjsb4 on 2012-11-11
I just finished helping someone else with their software center; there seems to be more breakage than usual going around related to the software center.  You can checkout that thread and see if anything works for you, but I think the most painless fix is just use another package manager.  Myself I don't even have software center installed, but instead use synaptic package manager.  Can you install with terminal?

sudo apt-get install synaptic

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

[http://ubuntuforums.org/showthread.php?p=12347909#post12347909](http://ubuntuforums.org/showthread.php?p=12347909#post12347909)

---

### Post by Chakravant on 2012-11-15
I am unable to install synaptic package manager.  Even after permitting all software sources, I get the error "Package synaptic is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.

E:  Package 'synaptic' has no installation candidate"

Software updater now hangs on 'Downloading from Ubuntu' now, although sudo apt-get update still provides the same errors.

I can open the software center, but when I try to download synaptic, it locks up at "Querying software sources".

But on the bright side, I have achieved change in the error.  That is a good thing, right?  :)

I haven't tried the minimal iso yet.

---

### Post by Chakravant on 2012-11-15
I've been trying the minimal ISO, but I keep getting "Bad archive mirror" errors.  I tried using the mirrors of my own country and our two closest neighbors, all with no luck.  It did successfully read and use our network, however.

---

