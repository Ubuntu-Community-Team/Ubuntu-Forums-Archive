---
title: "Help build HandBreak please"
date: 2013-04-28
forum: General Help
---

### Post by FishboyFive on 2013-04-28
Hello I have tried to contact John stebbins about updates to HandBreak for Ubuntu 13.04 he has chosen to ignore all attempts to contact him about updating HandBreak ppa with stable and nighty builds.


[https://launchpad.net/~stebbins](https://launchpad.net/~stebbins)


My question is as a casual user how do you build HandBreak from source for Ubuntu 13.04 ? I want to build a stable version and a version from there beta .


Is there anything I need to download in order to build before I begin ?


Thank you

---

### Post by The Spectre on 2013-04-28
> **FishboyFive said:**
> Hello I have tried to contact John stebbins about updates to HandBreak for Ubuntu 13.04 he has chosen to ignore all attempts to contact him about updating HandBreak ppa with stable and nighty builds.


[https://launchpad.net/~stebbins](https://launchpad.net/~stebbins)


My question is as a casual user how do you build HandBreak from source for Ubuntu 13.04 ? I want to build a stable version and a version from there beta .


Is there anything I need to download in order to build before I begin ?


Thank you

You could use the HandBrake Snapshot PPA...
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```There is a Raring build there.


Then this to install...
```
sudo apt-get install handbrake-gtk
```

---

### Post by FishboyFive on 2013-04-28
Will this install the GUI version of HandBreak or just the command line version 
and thank you.  Or is gtk the ui sorry kinda new to this

---

### Post by The Spectre on 2013-04-28
The GTK version is the GUI Version.

---

### Post by FishboyFive on 2013-04-28
> **The Spectre said:**
> The GTK version is the GUI Version.


Thank you very much would have had no idea this was available if it wasn't for you.

its a shame this app is not in the Ubuntu software center.

---

### Post by The Spectre on 2013-04-28
> **FishboyFive said:**
> Thank you very much would have had no idea this was available if it wasn't for you.

its a shame this app is not in the Ubuntu software center.
Glad I could Help.:)

I have wondered that myself on why it isn't in the Ubuntu Software Center but at least it is easy enough to get with the PPA.

---

### Post by JohnAStebbins on 2013-04-29
> **FishboyFive said:**
> Hello I have tried to contact John stebbins about updates to HandBreak for Ubuntu 13.04 he has chosen to ignore all attempts to contact him about updating HandBreak ppa with stable and nighty builds.


[https://launchpad.net/~stebbins](https://launchpad.net/~stebbins)


My question is as a casual user how do you build HandBreak from source for Ubuntu 13.04 ? I want to build a stable version and a version from there beta .


Is there anything I need to download in order to build before I begin ?


Thank you

I have not ignored all attempts.  I get a lot of spam on that email address.  I must have missed yours.  13.04 has been supported in the snapshots ppa for a few days now.  The releases PPA will get support when we do our next release (any day now I think).

For building your own, I recommend using current svn:
svn checkout svn://svn.handbrake.fr/HandBrake/trunk hb-trunk

And then follow the instructions in doc/BUILD-Linux

---

### Post by converted on 2013-04-30
> **FishboyFive said:**
> Hello I have tried to contact John stebbins about updates to HandBreak for Ubuntu 13.04 he has chosen to ignore all attempts to contact him about updating HandBreak ppa with stable and nighty builds.


[https://launchpad.net/~stebbins](https://launchpad.net/~stebbins)




Sheesh.  You know the first "P" in PPA stands for "Personal", right?

Developers and advanced users maintain these for their own use, and/or as a graciously provided resource for the rest of us, so we (the rest of us) don't have to compile when a program or particular program version is not available in the standard repos.

Being so affronted that he hasn't updated it yet, when Raring has been out for less than a week, when he's under no obligation to *ever* update the PPA again (or respond to emails about it) seems kind of rude, to me.

Side note -- if you find yourself in a similar situation in the future, most times you can use the PPA builds for the prior Ubuntu release with no ill effects.  Often I set them like this during the beta, then go back a few weeks after release to change them to the correct release version when they have all been updated.

---

