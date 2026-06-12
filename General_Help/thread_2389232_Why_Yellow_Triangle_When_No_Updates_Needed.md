---
title: "Why Yellow Triangle When No Updates Needed?"
date: 2018-04-13
forum: General Help
---

### Post by Rick St. George on 2018-04-13
Posting only after Search = No Specific Results.

Problem: Yellow Triangle shows up on Panel Bar

Clicking on "Show Updates" pops up a window "Software on this computer is Up To Date".

So ... Why is this Yellow Triangle showing ???

In Pkg Mgr there are no "Broken Pkgs", "Marked Changes" or "Upgradeable". I am all upto date!
Under Software & Updates / ubuntu software (tab), have the following checked.
  Canonical supported free and open source
  Proprietary drivers
  Source Code

Under "other software" tab;
  virtual box
  canonical partners
  opera
  kdenlive

Under "updates" tab;
  Important security
  Recommended updates 
  for LTS versions ONLY

Any suggestions?
Thanks

---

### Post by deadflowr on 2018-04-13
Well, yellow usually means some kind of warning so open a terminal take a look at what
```
sudo apt update
```
shows.
Anything of odd?

---

### Post by Rick St. George on 2018-04-13
Thanks Deadflowr:  Why didn't I think of that!?!? Here's the result ...

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
56 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

Then ran "upgrade". WOW ... Why didn't Software Update detect any of these ???

Also ran the usuals;

```

apt dist-upgrade
apt clean
apt autoremove

```

All is well, case closed.


):P

---

### Post by Autodave on 2018-04-13
That quite often happens with the software center. I always check manually to make sure.

---

### Post by deadflowr on 2018-04-13
is there an "Automatically check for updates" line in the Software and Updates > Updates tab?

---

### Post by Rick St. George on 2018-06-10
Wow .. its back. Ran UPDATE and got this;

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)


The open printing key may be the problem ? ? ?  Any suggestions?  

BTW - upgradable shows;

Listing... Done
libdw1/xenial-security,xenial-updates 0.165-3ubuntu1.1 amd64 [upgradable from: 0.165-3ubuntu1]
libelf1/xenial-security,xenial-updates 0.165-3ubuntu1.1 amd64 [upgradable from: 0.165-3ubuntu1]
libldap-2.4-2/xenial-updates 2.4.42+dfsg-2ubuntu3.3 amd64 [upgradable from: 2.4.42+dfsg-2ubuntu3.2]
liblouis-data/xenial-security,xenial-security,xenial-updates,xenial-updates 2.6.4-2ubuntu0.3 all [upgradable from: 2.6.4-2ubuntu0.1]
liblouis9/xenial-security,xenial-updates 2.6.4-2ubuntu0.3 amd64 [upgradable from: 2.6.4-2ubuntu0.1]
python3-louis/xenial-security,xenial-security,xenial-updates,xenial-updates 2.6.4-2ubuntu0.3 all [upgradable from: 2.6.4-2ubuntu0.1]
snapd/xenial-updates 2.32.9 amd64 [upgradable from: 2.32.3.2]



Thanks!

---

### Post by Rick St. George on 2018-06-18
Also got the following when running Synaptic Pkg Mgr. and selecting "RELOAD";

> 
W: Can't drop privileges for downloading as file '/root/.synaptic/tmp//tmp_cl' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)


Any suggestions - how to solve signature Key problem?
Thanks!

---

### Post by #&amp;thj^% on 2018-06-18
Debian and Ubuntu enforce SHA256 or higher entries in the Release and/or Packages files since March 2016. **Repositories missing these need to be fixed by their owners.**
and this is a problem with the repository not with your computer. 

The temporary solution is to comment out with a # the following line in /etc/apt/sources.list

```
# deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main
```

Also see this: [https://answers.launchpad.net/ubuntu/+question/253803](https://answers.launchpad.net/ubuntu/+question/253803)

---

### Post by Rick St. George on 2018-06-18
Thanks "1fallen".. Acomplished.  Seems I keep having to use Terminal and run update, upgrade, dist-upgrade, clean commands rather than to rely on Software Updater. Is this good or bad? Just curious!

---

### Post by #&amp;thj^% on 2018-06-18
there is nothing at all wrong with using the terminal to keep your system updated, in fact that is all I use and have done it this way for years. :)
FWIW it well known around here that I'm just not a fan of "Soft Ware Package managers">>outside of synaptic or gdebi. (Just my 2cents worth)

---

### Post by Rick St. George on 2018-06-18
THANKS BRO ... Case Closed.

Haaappy Ubuntuing ! ! !

---

