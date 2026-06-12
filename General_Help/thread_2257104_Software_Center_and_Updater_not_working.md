---
title: "Software Center and Updater not working"
date: 2014-12-16
forum: General Help
---

### Post by matthew62 on 2014-12-16
As of yesterday (2014-12-15), both the Software Center and Software Updater have refused to run. There is a red icon that looks like a "do not enter" sign in the notification bar, which gave a notification about the software updater, which stopped working after it attempted to intstall Ubuntu 14.10. After the unsuccessful installation, the Software Center would appear to start, but then close. For a few hours, the same happened to Rhythmbox, which resolved itself. After having looked around a bit, it appears as though I do not have specific packages installed, as though my computer is still in the process of installing the update.

---

### Post by spiffymoo on 2014-12-17
try fixing broken packages by typing[INDENT][B]```

sudo apt-get --fix-broken install

```[/B][/INDENT]
[B]into the terminal
if above dosnt help try [/B][INDENT][B]```

sudo rm /var/lib/apt/lists/* -vf[/B][/INDENT]
[INDENT][B]sudo apt-get update

```[/B][/INDENT]
**also may i ask how you tried to install 14.10**

---

### Post by Bucky Ball on 2014-12-17
When you say update, do you mean upgrade, i.e. from 12.04 or 14.04 to 14.10? You tried to do that?

spiffymoo, please use [code] tags for code. See the last link in my signature for how. ;)

---

### Post by spiffymoo on 2014-12-17
will do

---

### Post by deadflowr on 2014-12-17
If you click on the red dot, it should tell you what's wrong.
And usually what you need to do to fix it.
If you copy it down and post it, we can figure out the best method to go forward.

---

