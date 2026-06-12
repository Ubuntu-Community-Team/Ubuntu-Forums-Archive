---
title: "Question on upgrades and command line installs"
date: 2007-09-26
forum: General Help
---

### Post by jfrorie on 2007-09-26
Not really a problem, more of a general knowledge question.  I don't think I've seen this covered before.

I'm running feisty and have installed a number of packages.  Of particular note, Beryl and a rather involved bit for my Broadcom wireless adapter.  Beryl was installed using apt-get.  The broadcom was a little less "packaged"

The question:  When Gutsy comes out, I understand that Beryl (or compiz) will be installed by default.  I think I read somewhere that there is a new broadcom driver as well.  Did these installations "integrate" into the system. More specifically did they get registered such that the system will upgrade them and notify me for updates, or will I need to remove the previous incarnations of them?

The more general question is under Unbuntu, do you have to install using Add/Remove programs to have the system auto-update?  Does Unbuntu scan for existing libraries to catch command line installations?

I hope this makes sense.

Jim

---

### Post by dabl on 2007-09-26
I'll take a shot at answering these:

Re: Gutsy and compiz -- I'm running Kubuntu Gutsy Tribe 5 with updates through yesterday, and I actually had to choose to install compiz and emerald (and they're not quite stable yet, BTW).  So I dunno about "default" -- it appears I can unload them and go back to straight KDE if I wish.

Re: Broadcom -- can't help, I use a wire.

Re: Updates -- YES, you gotta use the standard repositories and one of the package manager front-ends. You have 2 GUI choices (Adept Manager or Synaptic) and 2 CLI choices (apt-get and aptitude) for your package manager interface.  The GUIs have menu items to add and remove repositories, then you "refresh" or "fetch" and you will have the currently-available packages in the list, and the updates and upgrades in the "preview" window, so you can decide whether and which you want to install.

I hope this is approximately responsive!  :)

---

### Post by strabes on 2007-09-26
Add/Remove Programs and synaptic are just front ends to apt-get. To upgrade, just run ```
sudo update-manager -c
```

By the way, beryl is not installed by default in gutsy. I believe the goal is for hardy heron to have some sort of composite extension enabled by default because at that time ATI will have released acceptable linux drivers for their cards.

---

