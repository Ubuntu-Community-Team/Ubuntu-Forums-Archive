---
title: "Bit of a odd question/request"
date: 2018-12-11
forum: General Help
---

### Post by wingnut144 on 2018-12-11
I am using a little Asus pc as a media server, and have my video server set up and running on it just fine.  The problem is, I don't have a monitor at home (I know, they're cheap, but I don't really need one).  The problem is that I would like to be able to get onto this box remotely when I'm at home, and make changes (add shared drives, install a printer, etc)

I have tried Teamviewer, but unless there is a monitor plugged into the box, I just get a black screen on the remote terminal.

How can I do this so I can see the desktop of the Asus (running Bionic Beaver, if that helps) remotely without having to go out and purchase a monitor for this small box??

Thanks a bunch! :)

---

### Post by QIII on 2018-12-11
If it's being used as a server, you could SSH into it and administer it in the terminal.  That's generally how it's done in the Linux world.  If it's a server you don't need the overhead of the truckload of services that run when you have a GUI.

For a few bucks you could get a beat-up used 4:3 15" monitor and use that just long enough to install openssh-server -- or to use as a monitor if you wish.

I have just one such monitor that I connect to my servers only as I have need, for instance when installing/reinstalling the OS.  Otherwise, it sits in a corner with the cables wrapped around it.

---

### Post by CatKiller on 2018-12-11
SSH is definitely the way to go when administering things remotely. You can do it from any computer. Heck, if I'm feeling lazy I'll SSH from my phone to do something on one of the computers without getting up.

---

### Post by wingnut144 on 2018-12-11
Ok, what about setting up a USB printer?  I've seen in the GUI there are options when adding a printer, like make it shared (I need it to be shared for Windows/iphones/Android tablets).  Are there instructions somewhere that will walk me through how to do that?

---

### Post by QIII on 2018-12-11
This is not an answer as such (I'm at a client location and not at a Linux machine), but there is a lot of good information [here]("https://www.cups.org/documentation.html").

Reading through some of that will likely give you a migraine.  But it will give you a chance to start understanding the purpose of the whiz-bang instructions you are about to get.  These are the sorts of resources that most of us use (and man pages) to figure things out.  Reading documentation from developers sometimes leaves one more confused than before, but it can all start to make sense as you get more help.

---

### Post by CatKiller on 2018-12-11
Generally the graphical tools are simply front-ends for commands that could be run from the command line.

---

