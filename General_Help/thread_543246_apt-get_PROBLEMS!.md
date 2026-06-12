---
title: "apt-get PROBLEMS!"
date: 2007-09-04
forum: General Help
---

### Post by fppl on 2007-09-04
Each time I try to install a program from apt-get I get this message (currently trying the flashplugin-nonfree)

Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

It did the same for wine... In my old ubuntu installation none of this happened!

---

### Post by SOULRiDER on 2007-09-04
Did you touch anything in the sources.list file? Also, what version are you running, Feisty?

Check that you accidentally didnt disable the multiverse and universe repos.

---

### Post by fazavon on 2007-09-04
OKay well I am going to guess that you have a GUI installed. If you do you should be able to open "Synaptic" under "Status" you should see "Broken Packages" click on it, choose "Remove Completely" and then click on the big green check mark. It will do some stuff, then say "complete" 

go back to your command line and type "sudo apt-get update" then you should be good.


Let me know how it goes.

//j

---

