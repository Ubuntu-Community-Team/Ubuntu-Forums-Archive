---
title: "k9copy ripping failing in feisty"
date: 2007-05-09
forum: General Help
---

### Post by Ba66e77 on 2007-05-09
Since migrating to feisty, I am unable to rip DVD's.  The process runs along file until it gets to  around 99% complete in the last stage "Fixing VOBUS".  At that point, I get a pop-up saying burning failed and the only way to close the program is to kill the process.  It doesn't give me more information than that.

I have two machines running feisty, a desktop and laptop.  Both ran k9copy fine in edgy and both have the same result now.  The problem is also the same across disks.

Is anyone else having this same issue?  Is there a way to get more info out of k9 as to why the burn failed?

---

### Post by mazirian on 2007-05-09
Are you running the app from a terminal? If not, try running k9copy form a terminal and post whatever stderr it outputs when the error occurs.

---

### Post by Ba66e77 on 2007-05-09
"Mutex destroy failure: device or resource busy"

Mean anything to y'all?

---

### Post by mazirian on 2007-05-09
Have you installed dvdrtools and mkisofs? 

```

sudo apt-cache policy dvdrtools mkisofs

```

I guess I should assume so, since your question suggests that you had k9copy working under edgy, but I'll ask anyway.

---

### Post by Ba66e77 on 2007-05-09
odd, doesn't look like they're there

~$ sudo apt-cache policy dvdrtools mkisofs
Password:
dvdrtools:
  Installed: (none)
  Candidate: 0.3.1-1
  Version table:
     0.3.1-1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
mkisofs:
  Installed: (none)
  Candidate: 9:1.1.2-1
  Version table:
     9:1.1.2-1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages

I've gotten them installed and I'm trying it out now.  I'll post the results.

---

### Post by stchman on 2007-05-09
> **Ba66e77 said:**
> Since migrating to feisty, I am unable to rip DVD's.  The process runs along file until it gets to  around 99% complete in the last stage "Fixing VOBUS".  At that point, I get a pop-up saying burning failed and the only way to close the program is to kill the process.  It doesn't give me more information than that.

I have two machines running feisty, a desktop and laptop.  Both ran k9copy fine in edgy and both have the same result now.  The problem is also the same across disks.

Is anyone else having this same issue?  Is there a way to get more info out of k9 as to why the burn failed?

I have no problem with K9copy in Edgy.  The more I read about Feisty the more I think it was rushed.  Edgy just seems to work better from what I have read on the forums here.

---

### Post by mazirian on 2007-05-09
I don't think that's a fair assessment.  Here, the culprit was almost certainly the missing packages. Feisty has been an improvement all the way around for me with no real issues on upgrade at all and perfect stability since the upgrade.  FWIW, I used k9copy last night on Feisty with no problems at all.

---

### Post by Ba66e77 on 2007-05-09
Mazirian, did you do an upgrade from edgy to feisty or a fresh install?  I did the fresh install, so that could account for the missing packages.  I would, though, have expected installation of k9 to pick up its dependent packages as well.

In general though, I have to agree with you.  Feisty has proven to be more stable on my system that edgy was, and the fixes/changes, while generally minor from what I've seen, collectively make for a much better experience.

---

### Post by Ba66e77 on 2007-05-09
installing the mkisofs and dvdrtools packages seems to have fixed the problem.  Thanks, mazirian.

---

### Post by mazirian on 2007-05-09
Grat news!  I've been updating my workstation right along since dapper. I'm a recovering Gentooer.  I don't know how those dependancies escaped apt, but weird stuff happens like that sometimes.

---

