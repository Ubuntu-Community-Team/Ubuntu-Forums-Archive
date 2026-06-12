---
title: "Finding software"
date: 2020-12-17
forum: General Help
---

### Post by x-ge-u on 2020-12-17
I am new to Ubuntu.  I am trying to get new software installed, but the  link to Ubuntu Software  in the desktop panel only shows me the editor picks, and the tabs there do not work.  How can I access the full overview?

---

### Post by CelticWarrior on 2020-12-17
Just click the 3-dot button and wait a few seconds.

---

### Post by TheFu on 2020-12-17
run these, in order, inside a terminal:
```
sudo apt update
sudo apt upgrade
sudo apt install synaptic
```

Now run synaptic - there may be a menu item or you can always run it from a terminal.  Synaptic was the default GUI for software package management for many releases.  It will access the same local APT database and the same remote repositories. It doesn't filter, so you'll probably see 60K items.  That should keep you busy for a day or two. ;)  

There are lots of "Top 10 Linux Software Options for X" articles on the web too and don't forget alternativeto.net - visit the website, type in the name of a program you've used on, cough, some, cough, other, cough, platform or OS and see if anything comes back that is Linux native.  For 20% of the programs you'll want, there is a 1-to-1 match and it will be fine.  For many things you seek, the Unix-way to solve that problem is very different from the Windows way. As more users move from Windows to Linux, they seem to forget that Unix solves problems very differently.  Just look at my answer above.  I provided 3 commands that will work on any Ubuntu version, release, DE, GUI. I didn't have to ask which flavor you are running because it doesn't matter. In a *terminal*, also called *shell* or *CLI*, those commands work the same.  I didn't have to include 5 captured images or a long list of menu choices.  That's Unix in a nutshell.  Make programs that do 1 thing, exceptionally well, nothing more.  We can use multiple programs together if more complex tasks are needed for the solution.  That happens all the time too, but each program is still doing 1 thing, exceptionally well. It is a different way of thinking and takes a little time to sink into our thought process. 

You don't actually need synaptic.  I haven't used it in probably 10 yrs, perhaps longer. In general, I install programs from a shell. For me, that is much faster and has been for a long time. But synaptic is a reasonable middle-ground between GUI and CLI package management.

---

### Post by ajgreeny on 2020-12-17
For users who won't, or perhaps can't, use the terminal, insisting that "it is far too difficult", synaptic is the obvious choice.
Unlike software-centre, Ubuntu-Software or whatever it's now called, it will show every package available, not just those that are considered to be best for a purpose, but absolutely everything including all the lib packages that never show in the software-centre.

When I first started with Ubuntu I used synaptic all the time but like TheFu I now use the terminal as it is faster and in spite of my slow typing, easier.  It also gives a lot of information as it carries out the command.

---

### Post by thomasrjohnson on 2020-12-20
I've been running Linux since 1998 and don't have a problem using the terminal. Synaptic is pretty cool because I can browse the repositories and find less popular stuff.

---

### Post by grahammechanical on 2020-12-20
What version of Ubuntu are you using? Over the last few years Ubuntu Software Centre/Software store/Software has been experiencing  somewhat of an identity crisis and did not always work correctly. There has been confusion as to whether it was offering apps published as deb packages or apps packaged as snap packages. I do not think that Flatpack packaged apps are offered by Ubuntu software. But I could be wrong.

If you are using Ubuntu 20.04 then underneath the Editor's Picks you should see Categories. Selecting one of them should give you icons of applications under that category.
Or you can use the magnifying glass icon which should be at the top left of the home page. That icon will present a search panel.

Regards

---

