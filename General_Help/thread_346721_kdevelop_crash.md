---
title: "kdevelop crash"
date: 2007-01-26
forum: General Help
---

### Post by tomane on 2007-01-26
Hi all,

I'm running kubuntu edgy and kdevelop.
In the past few days kdev crashes a few seconds after starting up. It brings up the window, toolbars, etc. Then it shows "project" loaded and puf(!), SIGSEGV.
This is the output whan launched from a terminal:
```
QLayout "unnamed" added to IndexView "unnamed", which already has a layout
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
QObject::connect: No such slot ClassViewPart::removeNamespace(const QString&)
QObject::connect:  (sender name:   'ClassViewWidget')
QObject::connect:  (receiver name: 'ClassViewPart')
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
QObject::connect: No such slot subversionPart::slotActionAddToIgnoreList()
QObject::connect:  (sender name:   'subversion_ignore')
QObject::connect:  (receiver name: 'Subversion')
QObject::connect: No such slot subversionPart::slotActionRemoveFromIgnoreList()
QObject::connect:  (sender name:   'subversion_donot_ignore')
QObject::connect:  (receiver name: 'Subversion')
QObject::connect: No such slot subversionPart::slotStopButtonClicked(KDevPlugin*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'Subversion')
ASSERT: "part && parent" in /build/buildd/kdevelop-3.3.4/./parts/fileview/partwidget.cpp (40)
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 3' gave syntax error
KCrash: Application 'kdevelop' crashing...

```
When it starts normally without crashing it gives the same output, except the assert message.
Does anyone have an idea of what is going wrong?

cheers,
--to

---

### Post by agentq on 2007-03-17
I'm an Ubuntu n00b, and this started happening to me too.

I fixed it by upgrading to the latest kdevelop using the instructions here:
[http://kubuntu.org/announcements/kde-356.php](http://kubuntu.org/announcements/kde-356.php)

---

### Post by tomane on 2007-03-17
Were you using any kind of version control in your project?
I have a slight suspiction that it was causing my problem, but I can't tell for sure. Since I removed version control from the project and manage it using, for instance, kdesvn, I haven't experienced these crashes..

cheers,
--to

P.S: there's no such thing as an ubuntu "n00b", some people just might be more advanced than other in the learning process, that's all :)

---

### Post by MoridinBG on 2008-02-19
I have the same problem. For something like 2 or 3 days I was using kdevelop just fine. In fact I selected Subversion for Versoning Control, as it would be nice to have it, but there was an error with creating working copy, so I left it and continued developing my project. I have closed and reopened KDevelop several times with no problems until today. It would crash as soon it loads. No matter if there are open projects or no.
After one or two hours deleting config files, messing with project.kdevses and "apt-get purge"-ing KDevelop I made it start by moving my project folder out of the Projects folder. If I start it from there: crash. If I start it from somewhere else: no problems. If I start it as root via kdesu (just to see if it works! Don't kill me!) it works even from Projects directory...

The error messages are like the ones from the first post, almost the same.

And this on Kubuntu.

I have been Slackware userall the way from 9.1 to the time when slackware-current started to look like slackware-12, then Gentoo user for another year, and I have used KDevelop extensively, but I see this kind of behaviour for the first time. Almost made me use Eclipse as it is really important to finish the project soon.

---

### Post by MoridinBG on 2008-02-26
BUMP!

Any ideas? KDevelop now completely refuses to work. It starts and freezes just after loading last opened files... With kdesu starts with no glitches, but using it this way brings some other glitches.

Purged it numerous times, deleted all files related to it, but the damned thing just doesn't run. It's from the official Ubuntu repositories, version 3.5.0.

This is really driving me crazy, because I NEED working, comfortable QT4 development environment...

---

