---
title: "Where has dpkg-*scanpackages gone? I installed dpkg-multicd, but...?"
date: 2008-05-01
forum: General Help
---

### Post by OzzyFrank on 2008-05-01
Hi. I've set up my own local repositories before, so am aware **dpkg-scanpackages** isn't in Ubuntu by default, and that to get it you need to install **dpkg-multicd**. Now, I've just done that (in Gutsy... wanting to upgrade to Hardy with CD files in local folder)... but am still getting **dpkg-scanpackages: command not found** (and yes, I did reboot to be safe). I do an **apt-get install** in the terminal and it confirms I have the latest version. So what is happening? Has **dpkg-scanpackages** been moved into another package? Or do I now need to do something to get it recognised? I am running 64-bit Gutsy. Cheers

---

### Post by FuturePilot on 2008-05-01
Try installing dpkg-dev

---

### Post by OzzyFrank on 2008-05-01
Yeah, I know there can be errors if it isn't installed, ie dpkg-dev, but it is. I can't even get the system to recognise /usr/bin/dpkg-scanpackages exists, even though it is there alright! Copy the command to another folder and try to get the terminal to acknowledge its existence and still no go? Next?

---

### Post by OzzyFrank on 2008-05-04
I won't quite mark this as solved, but I did have success even though it was increasingly looking like it was just going to end in a migraine. No matter what I tried it was like the system wasn't seeing dpkg-scanpackages, which was more than annoying. What I found that finally worked was trying some different syntax than the usual:

**dpkg-scanpackages . /dev/null >Packages**      or
**dpkg-scanpackages . /dev/null >Packages && gzip Packages** (these always worked before Hardy)

This one below is what worked for me:

**[COLOR="DarkRed"]sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz[/COLOR]**

I wouldn't mind if someone explained the difference and why it worked (it wasn't the **sudo**, as I already tried the other commands with and without sudo). Still puzzles me how the system absolutely refused to see the command before this... like I could right-click the file and see Properties, etc, but try anything in a terminal, or double-click it or such... nothing! Anyway, hope this helps someone else with the same issue! Cheers

---

