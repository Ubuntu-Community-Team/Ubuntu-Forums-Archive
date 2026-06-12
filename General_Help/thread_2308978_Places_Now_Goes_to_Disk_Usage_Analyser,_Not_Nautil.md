---
title: "Places Now Goes to Disk Usage Analyser, Not Nautilus as it Should"
date: 2016-01-07
forum: General Help
---

### Post by oldefoxx on 2016-01-07
Using 14,04, and have a new problem:  Click on Places (Classic Gnome), and suddenly Disk Usage Analyser come up, not Nautilus.  D.U.A.  does not give me access to contents of partitions, runs forever, and is blocking normal usage.  Gnome-utils is not installed, so don't even know where D.U.A. came from.  Copied ./usr/share/applicarions/nautilus.desktop to ~/Desktop, then set the Execute under Properties/Permissions and can click on that to get Nautilus up. but would prefer just to get matters back as they were.

So some help would be appreciated, because I don't know how this happened.  Everything goes back to irratic mouse movements and unintentional simulated mouse clicks due to an over-sensative touchpad and no way provided to block hand pauses from being read as intent to press a button, change focus, or whatever.  That might help the handicap, but it way overkill in my case.

---

### Post by slickymaster on 2016-01-07
You might want to review your thread title. Reason being the fact that you prefixed it with the "Xubuntu" tag and following your post you're clearly not using that flavor.

---

### Post by Dennis N on 2016-01-07
> Using 14,04, and have a new problem: Click on Places (Classic Gnome), and suddenly Disk Usage Analyser come up, not Nautilus.

You are expecting clicking on 'Places' to launch the file manager? Doesn't 'Places' normally just display a menu consisting of locations (Home Folder, Desktop, Computer, etc)? 

The file manager should open when you click on one of these menu entries in 'Places', not when clicking on 'Places' in the panel. 

How exactly does yours misbehave? Please clarify.

---

### Post by oldefoxx on 2016-01-13
Solved.  <problem first reported in <ubuntu 13.04.  Here are the links:

[http://askubuntu.com/questions/300972/places-opens-in-disk-usage-analyzer-in-ubuntu-13-04]("http://askubuntu.com/questions/300972/places-opens-in-disk-usage-analyzer-in-ubuntu-13-04")

[http://askubuntu.com/questions/288270/disk-usage-analyzer-replacing-nautilus]("http://askubuntu.com/questions/288270/disk-usage-analyzer-replacing-nautilus")

[https://bbs.archlinux.org/viewtopic.php?pid=1186209#p1186209]("https://bbs.archlinux.org/viewtopic.php?pid=1186209#p1186209")

Note where it says to "edit /usr/share/applications/baobab.desktop", use "sudo gedit /usr/share/applications/baobab.desktop".  Where it says "update-desktop-database -q". use "sudo update-desktop-database -q".

You are offered two solutions when it comes to fixing baobab.desktop.  One is to change "MimeType=inode/directory;" to "MimeType=inode/directory:1;" and save the file.  Instead, I just removed "MimeType=inode/directory;" as another person suggested.  That works as well.

Three big complaints about Gnome's Disk Usage Analyser: 

 (1)  It does not automatically update or report on each mounted oartition's free/total disk space.  You have to click on each partition in turn and have it at least initiate a scan.  The scans themselves can take forever, and when you start it the next time, the free disk space numbers are what they were at  the start of the last scan, so not very useful.

(2)  What the program reports seems meaningless.  Everything is a 0.  What good is that?

(3)  You would never use it, but if you ask Ybuntu Software Center to remove it. USC doesn't know it by that name.  You nave to abbreviate the name or do a search on baobab.  It's rated 5 stars (not in my opinion), and you are warned that it is part of the core Ubuntu package, and that removing it could effect future upgrades.  That might mean getting warnings that only a partial upgrade was possible.  I don't need warnings like that, so I left it in place.  But you don't need it, because you have better alternatives, such as, from a terminal:```
    df -H
    lsblk
```
Here is a link for different uses for the ["df" command]("http://www.tecmint.com/how-to-check-disk-space-in-linux/").   To learn more. you can preceed a command with "man ".  which opens an instruction manual for that speciific command.  Again. this is done from a terminal window.  You might also be interested in the "du" command [discussed here]("http://www.tecmint.com/check-linux-disk-usage-of-files-and-directories/").

---

