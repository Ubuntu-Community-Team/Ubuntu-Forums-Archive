---
title: "would this work?"
date: 2005-11-01
forum: General Help
---

### Post by iAlta on 2005-11-01
I have tried many times to install difrent programs, but they never work.
Now I have an idea that just may work.
My computer is not hooked up to the internet. But my father's is(the one I am currentlr useing). My father just resently got an box for external harddrives. So if I put my harddrive in that box and boot up Ubuntu on his computer and then install all kind of programs, like SDL, MPlayer, WINE and Glob2, would it then work? or if I just put a LAN-cable from my PC to my fahter's PC, wich is a laptop. would then work?
And if hooked up, I just have to use the Softwarepakage Maneger-ting, right?

---

### Post by l33tc0d34 on 2005-11-01
u would have problems.

---

### Post by iAlta on 2005-11-01
wich problems?

---

### Post by l33tc0d34 on 2005-11-01
do u get a black screen 2 with localhost? i have that problem 2.  i think u have problems doing this with box and drive. can u not download progs to floppie disc and installing from there?

---

### Post by iAlta on 2005-11-01
all the programs have been "broken" or some error when installing. It's just so annoing, whan it always fails, and when is does work it's broken. The only programs, that don't come with Ubuntu, I have got working, have been some Hello Worlds I've made myself.

---

### Post by Swoop on 2005-11-01
Either download repositories for offline use (Seen them around here somewhere) or hook up your own machine using a cross over netcable for access when installing ... 

Also you can download .deb files manually, and transfer them to your local computer and isntall them yourself there :D

The whole putting the HD in the box thing propably wont work ... you would most likely get some hardware errors when you booted up the harddrive on another machine :D

---

### Post by iAlta on 2005-11-01
I have lots of debs(well not after breezy), none of them work, but that "repositories", whats that?

---

### Post by 23meg on 2005-11-01
You can think of repositories as servers that host lots of deb files. The reason the deb files you're installing don't work is probably that they have dependencies. This means for example that one deb you're installing requires five other debs to be already installed to work. This is where repositories come in: if you point your package manager (apt / Synaptic) to a repository and choose to download a program, all the required deb packages will be downloaded and installed together with their dependencies.

Assuming the two computers are in the same house, you can make an ethernet connection to your father's computer to share his internet connection.

---

### Post by SilentCacophony on 2005-11-01
> or if I just put a LAN-cable from my PC to my fahter's PC, wich is a laptop. would then work?

If your father's internet connection happens to run through a router, you could simple connect to the router.

If no router, have you considered temporarily switching the cable from the modem from his to your computer?

That's assuming that your computer is, or can be moved, near to his.


Also, you can set up a local repository on HD or cdrom, by adding it to your sources.list (or using apt-cdrom.) There is a thread about that here:

[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

You can also use some options for apt-get to see what packages are necessary (by simulating the install) or to download them only, using the -s and -d options, respectively.

---

