---
title: "/home partition"
date: 2008-03-05
forum: General Help
---

### Post by Riffer on 2008-03-05
[SIZE="2"]OK so after learning lots and breaking tons of stuff its time for a re install.  This time I want to try and create a separate /home partition.  I can use gpart to create partitions but from there I'm lost.

In the install at the partition segment if I create a separate patition and mount it as ./home, will Ubuntu install all the /home stuff there?  And in case of a reinstall will Ubuntu automatically install what programs that the /home says I had?

I'm planning on installing Hardy, it seems it may solve some of my sound issues.

Gotta say I'm impressed with Ubuntu and linux.  I learn by trying things and end up many times breaking things.  This is how I learned windows.  The big difference here is that in windows when I broke something the whole OS would shut down, with Ubuntu when I break things it still chugs along. [/SIZE]

---

### Post by Oldsoldier2003 on 2008-03-05
> **Riffer said:**
> [SIZE="2"]OK so after learning lots and breaking tons of stuff its time for a re install.  This time I want to try and create a separate /home partition.  I can use gpart to create partitions but from there I'm lost.

In the install at the partition segment if I create a separate patition and mount it as ./home, will Ubuntu install all the /home stuff there?  And in case of a reinstall will Ubuntu automatically install what programs that the /home says I had?

I'm planning on installing Hardy, it seems it may solve some of my sound issues.

Gotta say I'm impressed with Ubuntu and linux.  I learn by trying things and end up many times breaking things.  This is how I learned windows.  The big difference here is that in windows when I broke something the whole OS would shut down, with Ubuntu when I break things it still chugs along. [/SIZE]

no. what you are doing is saving the data and configurations that are stored in the home dir. You will still have to install all the apps. make sure you save the /home directory tree to a partition that you don't intend on formatting or you will lose all of the data.

---

