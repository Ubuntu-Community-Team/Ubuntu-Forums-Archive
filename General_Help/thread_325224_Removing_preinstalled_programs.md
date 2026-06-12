---
title: "Removing preinstalled programs"
date: 2006-12-25
forum: General Help
---

### Post by zazen666 on 2006-12-25
Hi all!~
I am a newbie to ubuntu and so far really like it..
One issues though, one of the main reasons I wanted to give linux a try is I have always been really turned off by the fact that windows installs so much junk on my computer and I have to find ways to remove it. 
I want my computer to have as much free space as possible and I dont need two movie players, music players, etc.

I would like to remove some of the programs that came with ubuntu such as evolution, gimp, etc that I wont use. But it seems to not be possible from Add/Remove.
any help on this?
Thanks so much
m

---

### Post by nikhilk on 2006-12-25
Package mangers like Adept (I guess Synaptic too) can show you a list of all installed packages. I am sure you can remove them from Adept/Synaptic.

---

### Post by PurplePenguin on 2006-12-25
Add/Remove seems to be a simplified front-end to the package manager.  If you need to do more complex things, such as remove programs that have other dependencies, you'll need to go to System -> Administration -> Synaptic Package Manager.

---

### Post by zazen666 on 2006-12-25
Thanks for the clear feed back guys.

Quick and new question.
If I remove things like GIMP, ekiga softphone, evoulution, totem, etc, will there be any unforeseen problems with other programs, in the future?
Thanks so much

---

### Post by Falcorian on 2006-12-25
There shouldn't be any problems. Linux uninstalls rather cleanly in my experience, and anything you need again can be reinstalled without problems.

You may find some odd dependencies when removing stuff, but you'll be warned before hand. To create an absurd example, it may tell you you need Ekiga to use emacs. No, it won't really, but something like that ;).

---

### Post by Azakus on 2006-12-25
Remember that when you uninstall anything that comes preinstalled, the package "ubuntu-desktop" will also be uninstalled. Don't worry, it's just a little meta-package that lists the preinstalled stuff, so uninstalling it actually doesn't do anything.

---

