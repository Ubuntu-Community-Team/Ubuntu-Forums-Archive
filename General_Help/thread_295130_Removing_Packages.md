---
title: "Removing Packages"
date: 2006-11-07
forum: General Help
---

### Post by JackRazz on 2006-11-07
Hey everyone,
Is Synaptic suppose to complete remove all dependent packages if they were installed and nothing else depends on them?  As an example I installed Amarok on Ubuntu last night and then uninstalled it today.  Nothing else was changed in between.

When I look at the installed packages (File/History menu item), I see that most of the dependent packages were not removed.  Just for funzies, I manually removed them.  However, this has to be a very unreliable method.

If there are orphaned packages on my system, how do I find and remove them?



From Synaptic History
-----------------------------

[INDENT][SIZE="1"]INSTALLED AMAROK
Commit Log for Tue Nov  7 01:02:01 2006

Installed the following packages:
amarok (2:1.4.4-0ubuntu1)
amarok-xine (2:1.4.4-0ubuntu1)
kdelibs-data (4:3.5.5-0ubuntu3)
kdelibs4c2a (4:3.5.5-0ubuntu3)
libarts1c2a (1.5.4-0ubuntu1)
libavahi-qt3-1 (0.6.13-2ubuntu2)
libifp4 (1.0.0.2-3)
liblua50 (5.0.2-6)
liblualib50 (5.0.2-6)
libnjb5 (2.2.5-4.1ubuntu1)
libopenexr2c2a (1.2.2-4.3)
libpcre3 (6.4-2ubuntu1)
libtunepimp3 (0.4.2-3ubuntu3)
python-qt3 (3.16-1.2ubuntu1)
python-sip4 (4.4.5-2ubuntu1)


REMOVED AMAROK
Completely removed the following packages:
amarok

Removed the following packages:
amarok-xine

Commit Log for Tue Nov  7 15:00:26 2006


PACKAGES I MANUALLY REMOVED
Completely removed the following packages:
kdelibs-data
kdelibs4c2a
libarts1c2a
libavahi-qt3-1
liblua50
libnjb5
libopenexr2c2a
libpcre3
libtunepimp3
python-sip4

Removed the following packages:
liblualib50
python-qt3
[/SIZE][/INDENT]

---

### Post by Ramses de Norre on 2006-11-07
I think there are packages deborphan & gtkorphan to do this.

The best is using aptitude in the future to install packages, it will automatically hold a list of packages which are installed as dependencies and it will remove these when the original package gets removed.

---

### Post by pitkali on 2006-11-07
Indeed synaptic never did this. Although now in Edgy there is autoremove status listing packages that were automatically installed to satisfy dependencies and are not needed any more.

Regards,

---

### Post by JackRazz on 2006-11-08
First thanks for both of your insights.  I'll test both suggestions: using Aptitude & unsintalling the *Installed Autoremovable* items under Status in Synaptic.

I was surprised to hear that Aptitude works, but Synaptic doesn't.  But the Autoremovable may be the solution here.  Lastly, I'll check deborphan & gtkorphan and see how they work.  I guess no package manager is perfect.


Thanks Again - JackRazz

---

