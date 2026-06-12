---
title: "How to transfer settings from one Firefox to another?"
date: 2007-07-09
forum: General Help
---

### Post by 67GTA on 2007-07-09
What is the best way to transfer all my Firefox settings, usernames/passwords for websites, about:config tweaks?

---

### Post by oomingmak on 2007-07-09
From where to where?

If it's from one Ubuntu install to another, then just copy the .mozilla folder in your home folder to a safe place and then copy it back when ready.

A similar thing applies when transferring settings between Windows & Linux (although the folder names are different). Remove the dot at the beginning of the mozilla folder name when restoring to Windows and add it when restoring to Linux.

In WIndows, your Firefox settings folder is located at:

%USERPROFILE%\Application Data\Mozilla


%USERPROFILE% usually relates to:   *C:\Documents and Settings\<your_username>*, but you need to check what it is on your particular system,

---

### Post by aysiu on 2007-07-09
C:\Documents and Settings\*username*\Application Data\Firefox

or

/home/*username*/.mozilla

---

### Post by 67GTA on 2007-07-09
I was trying to move them from Ubuntu partition to PCLinuxOS partition.  I wasn't sure if they were compatible enough to copy and paste folders. I hate setting up Firefox every time I try a new distro:(

---

### Post by aysiu on 2007-07-09
> **67GTA said:**
> I was trying to move them from Ubuntu partition to PCLinuxOS partition.  I wasn't sure if they were compatible enough to copy and paste folders. I hate setting up Firefox every time I try a new distro:(
They're compatible.

Just copy from /home/*username*/.mozilla in Ubuntu to /home/*username*/.mozilla in PCLinuxOS

---

### Post by oomingmak on 2007-07-09
> **aysiu said:**
> C:\Documents and Settings\*username*\Application Data\**Firefox**

or

/home/*username*/.mozilla
Shouldn't that be: ' .... Application Data\**Mozilla**'

---

### Post by aysiu on 2007-07-09
Maybe that's it. I'm going on memory here, since I don't have Windows in front of me.

---

