---
title: "Newbie needs help adding gui to server"
date: 2007-04-04
forum: General Help
---

### Post by bdemers on 2007-04-04
OK, I have both server and workstation cd's.  What I'm after is based on a LAMP arrangement, which server provides and workstation does not. (well, at least simply).  Problem is I need a crutch in the form of either Gnome or KDE, so that I can run Firefox, as an install of Firefox by itself on server doesn't seem to set up the graphics needed.  While command line control should be sufficient, for a nimrod such as myself, its a teensie bit slow going.  So what to do?  Do I use workstation so that I get the interface and Firefox, but am forced to download and install Apache, Mysql and PHP, or, do I use server and download and install Gnome and Firefox.  My vote, should I be allowed a vote, is for me to download Gnome and Firefox.  

If it works out that I do choose to do Gnome, is it possible for me to acquire the files via a command line input, or is there a browser already available on server that I can use? ( I don't own stock in Firefox).  Is there a cookbook approach toward adding a gui to server and if so, what is it?

---

### Post by taurus on 2007-04-04
```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Titus A Duxass on 2007-04-04
sudo apt-get install ubuntu-desktop or kubuntu-desktop for KDE.

That will give you a full desktop, for a minimal install sudo apt-get install xterm, gdm and gnome-core.

---

### Post by bdemers on 2007-04-04
In a matter of nanoseconds I had 2 replies!  Just got back from following the procedure outlined and got this message when starting up:
"Cannot  stat  /etc/x11/x    No such file or directory."

From my command prompt I looked at the /etc directory and saw /x11.  I could not access /x11 however.  Wait a minute... Holy Cow, it's case sensitive!  OK, under X11, x doesn't exist, but gdm does. 

Right after the install ubantu-desktop gdm finished I typed in sudo  /etc/init.d/gdm start .  Did I mess up case again?  Or do I need to edit the file that has "/etc/X11/x" to read "/etc/X11/gdm"

If this edit is needed, what and where is this file?

---

