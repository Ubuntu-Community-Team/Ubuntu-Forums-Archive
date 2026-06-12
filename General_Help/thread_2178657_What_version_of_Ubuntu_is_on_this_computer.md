---
title: "What version of Ubuntu is on this computer?"
date: 2013-10-04
forum: General Help
---

### Post by Clopper Almon on 2013-10-04
Does anyone know a **sure** way to answer the simple question: What version of Ubuntu is on this computer?

It used to be easy to find what version of Ubuntu one was running. Under Applications | Accessories (or something like that) there was an "About Ubuntu" applet which answered that question. It has disappeared in newer versions. On one computer running 13.04 with the Gnome desktop, I found that under the *-like symbol in the upper right corner (which one uses mainly to logout) there is an "About Ubuntu" ltem which tells you what version you are running. But on the computer from which I am writing this -- which also has the Gnome desktop -- there is no * in the upper right corner, but the user name and a "balloon". These two offer the same options: Available, Busy, ..., Log out, ..., Power off.  But no way to learn what version is being run. I think it is 13.04 but cannot tell for sure. It ought to be easy to learn that important fact.

---

### Post by enterdavertex on 2013-10-04
[LIST=1]
[*=left][FONT=inherit]Open the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=Terminal#Starting_a_Terminal") (keyboard shortcut: Ctrl+Alt+T)[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Enter the command _***lsb_release -a***_[/FONT]
[/LIST]
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by Clopper Almon on 2013-10-04
Thanks, Enterdavertex, that is just what I was looking for. For others looking at this thread, here is what the Linux manual says about this command:
The lsb_release command prints certain LSB (Linux Standard Base) and Distribution information.

The -a means to display *all* information.

---

### Post by SeijiSensei on 2013-10-04
You can also just examine the file /etc/lsb_release which contains:

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

```

---

### Post by 3rdalbum on 2013-10-05
Or go to System Settings and click on Details.

---

### Post by Dave_L on 2013-10-05
> You can also just examine the file /etc/lsb_release which contains:
...

The file name is actually "/etc/lsb-release" (hyphen, not underscore), unless that's changed since 12.04. It's an easy mistake to make, since the command uses an underscore.

---

