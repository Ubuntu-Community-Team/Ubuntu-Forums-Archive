---
title: "Copy updates to another computer"
date: 2007-09-30
forum: General Help
---

### Post by TCE on 2007-09-30
I need somebody's help or opinion.  I need a way to transfer updates to another computer.  The reason for this is my computer has a high speed connection, but my parents' computer has dialup. Instead of having my parents internet connection on for hours or days for updates; I was wondering if there is software or any sort of way such as saving the updates on cd or flash drive to transfer updates from my computer to my parents computer.  There is one problem that i have my computer is a ubuntu ppc, and my parents is ubuntu i1386.  Also is there perhaps a better distro for this problem that would be better than ubuntu
thanks

---

### Post by Jussi Kukkonen on 2007-09-30
It's not possible to easily and reliably do what you want. I suggest you enable only security updates --this will make the download sizes easier to cope with...

---

### Post by vanadium on 2007-09-30
I am quite interested in this myself because my father is about to try Ubuntu, indeed also with a dial-up connection. I guess it is a matter of mirroring repositories on CD-roms or DVDs, then use these as "software source", but I am angry for the details myself.

---

### Post by Irihapeti on 2007-09-30
This might work.

On your parents' computer, open synaptic and choose the upgrades you (they) want. Then instead of clicking on "apply" to start the installation, choose 'generate package download script' (file menu). You can then take that away and use it on your own computer.

Note that the script, at least on my version of Feisty, has a bug: the wget commands don't have a space between the -c and the http: address. It's easy enough to go through and edit it by hand (it's just a text file), or you can just use the urls in another download manager.

The packages can be put onto a cd using APTonCD (in the repositories). You might get some "software can't be authenticated" messages when you come to install. As you have already got the software from the proper source, I figure that is not a huge issue.

I use separate download because I'm on a dialup and I want to be able to download updates overnight and have the computer hangup automatically. Synaptic doesn't have that function.

HTH

---

### Post by keithweddell on 2007-09-30
If you search through the repos there are several apt packages with differe3nt soluitions.  AptonCD may do what you're looking for.

Keith

---

### Post by TCE on 2007-09-30
What do you think about debian you can download update cds and releases your system would not be perfectly up to date but sort of.

---

