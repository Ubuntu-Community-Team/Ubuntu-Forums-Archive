---
title: "Firestarter randomly closes, no errors?"
date: 2008-01-05
forum: General Help
---

### Post by WinterWeaver on 2008-01-05
Firestarter will randomly close, without any errors.

I've run it in the terminal, to check if it dumps any errors there, but there is absolutely none. O.o?

How can I find the problem, and how can I fix this?

I know it's just a front-end to configure the IPtables, so I'm not really concerned about security, but I like to be able to see the ips and ports connected to my PC, so I occasionally check back with Firestarter to see whats going on, only to find that on a random occation, it's just dissapeared... O.o

thx for any help.

WW

---

### Post by rubicon on 2008-01-05
ARAIK, this is a known bug in firestarter. I don't know any workarounds or fixes for it, but you may find something in launchpad. [https://bugs.launchpad.net/firestarter](https://bugs.launchpad.net/firestarter) or [here](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=firestarter&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Tyche on 2008-01-05
> **WinterWeaver said:**
> Firestarter will randomly close, without any errors.

I've run it in the terminal, to check if it dumps any errors there, but there is absolutely none. O.o?

How can I find the problem, and how can I fix this?

I know it's just a front-end to configure the IPtables, so I'm not really concerned about security, but I like to be able to see the ips and ports connected to my PC, so I occasionally check back with Firestarter to see whats going on, only to find that on a random occation, it's just dissapeared... O.o

thx for any help.

WW

I wish I could find the particular link in launchpad where I found the answer.  I'll try to give you the gist of the information, to the best of my ability.

Firestarter has an instability with respect to "Active Connections".  If you minimize Firestarter to the system tray with "Active Connections" open, Firestarter will drop out within about 10 to 15 minutes (sometimes even shorter periods of time).

The work-around is actually very simple.  Always be sure that "Active Connections" is closed before minimizing it.  Since I've been doing that the program has stayed available without any problem.

Hope this helps.

---

### Post by seventhc on 2008-01-05
it might still be running, just that the visible window dissapeared, you can check by doing this.
```
sudo /etc/init.d/firestarter status 
```

---

### Post by frogotronic on 2008-01-16
Here's the active BUG link.  Looks as if the DEVs are on it:

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445)

- CH

---

