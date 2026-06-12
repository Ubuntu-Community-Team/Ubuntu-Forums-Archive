---
title: "IBM Lotus Notes 8 Beta 2"
date: 2007-04-17
forum: General Help
---

### Post by Silx on 2007-04-17
I was wondering if anyone has successfully got this to work in Ubuntu.

I've got fairly far with it, even to the point of it asking for my id file in Wingdings. (Or what looks like Wingdings...). If anyone has any tips to get further, please help.

Here's a screenie:

Btw, I'm using Edgy.

[IMG]http://i143.photobucket.com/albums/r152/silxinator/LN8_Screen1.jpg[/IMG]

---

### Post by Silx on 2007-04-19
Bumping (for great justice!)

---

### Post by hedger48 on 2007-04-26
have you had any luck?  I am trying the same thing and I didn't get as far as your screen shots.  Mine seemed to install ok, then I tried to creater a launcher to notes and it opened a blank Lotus Notes screen.    What did you do to get as far as you did?

---

### Post by Silx on 2007-04-26
I'm now at this point:

[IMG]http://i143.photobucket.com/albums/r152/silxinator/ln8b2.jpg[/IMG]

There are lots of packages I installed with Ubuntu to get this far. 

Copied over all the fonts from my windows xp box to the ubuntu box.
Upgraded to Feisty
Installed eclipse libraries (seems to be what the beta uses)
Installed anything and everything mozilla related
Created a blank notes.ini file in the notes folder
Copied over my notes data folder from my xp box to the ubuntu box (did weird things!)

At this point, I have an error message that just says:
Server error: Entry not found in index

:confused: :confused:

---

### Post by Silx on 2007-05-01
buuump!

---

### Post by Silx on 2007-05-07
Bumping again. I'm still looking for other beta testers that are trying to get this to work in Ubuntu.

---

### Post by davidwi on 2007-05-14
Hi I got the beta working. It was a fresh install of ubuntu 7.0.4 more of less.

I came across this posting:

[http://www.kluge.de/labels/Lotus%20Notes.html](http://www.kluge.de/labels/Lotus%20Notes.html)

So I removed the previous Notes install by deleting the ibm, IBM, and InstallShield folders then as the posting suggested:

Open a terminal window
cd /bin
sudo rm sh
sudo ln -s bash sh

not sure if I rebooted at this point, I may have.

I then Installed Notes, I had to turn off Desktop Effects as this seemed to show a blank Install window.

When I ran Notes (icon is in the Office menu) I got the setup wizard and its worked fine since.

David.

---

### Post by Silx on 2007-05-17
Alright, the steps you wrote worked very well. I got all the way through the installation procedure with no errors. The client is communicating with the server.. it even told me I have new mail.

However, I _still_ get the same error in the end. Entry not found in index. Any ideas? What version is your domino server?

thanks
-s

---

### Post by Silx on 2007-05-18
i r captain bumpalot!

---

### Post by davidwi on 2007-05-27
I'm running Domio 7.0.2, I also have a roaming profile and the came down as well. My mail file is version 8 design, changed it with he Windows version of Lotus Notes beta 2.

Going to try Notes beta 3 later.

---

### Post by jan on 2007-07-05
Hi,

Ive got problems getting the Linux Notes Beta 3 running. The install seems to be totally OK (although I cant really understand why they only name SUSE and RHEL in the specs - marketing probably) - the InstallShield went ok, but when I want to run the "notes" executable under regular user, nothing happens... When I run it under root, it starts up but then says I cant run the client under root account and exits...

---

### Post by shyster. on 2007-07-11
> **jan said:**
> Hi,

Ive got problems getting the Linux Notes Beta 3 running. The install seems to be totally OK (although I cant really understand why they only name SUSE and RHEL in the specs - marketing probably) - the InstallShield went ok, but when I want to run the "notes" executable under regular user, nothing happens... When I run it under root, it starts up but then says I cant run the client under root account and exits...

In your home folder, change the "lotus" folder to something like "lotusold" and start the application again. This should work. Good luck!

---

### Post by jan on 2007-07-11
Thanx, have fount this solution elsewhere already... however, there are some more problems with to get this beta runing.

---

### Post by kkovach on 2007-08-03
Anyone able to get Beta 3 to install on a 64-bit system?

The installation goes pretty smoothly until it tries to "launch the provisioning platform" to install other features, or something like that.  The installation log seems to indicate that it's having a problem writing the file /etc/lotus/notes/notesrc.  I have watched and seen that it creates a /etc/lotus/notes/data directory during the install, so it can clearly write to that directory.

I've created the /etc/lotus/notes directory, and I've made sure that it has write permissions.  After it fails it always seems to delete the /etc/lotus/notes directory as well.

Any hints or tips would be appreciated.  Thanks.

---

### Post by Silx on 2007-10-08
I am looking for the Final client for Linux if anyone has it.

---

### Post by eledh on 2007-11-20
> **kkovach said:**
> Anyone able to get Beta 3 to install on a 64-bit system?

The installation goes pretty smoothly until it tries to "launch the provisioning platform" to install other features, or something like that.  The installation log seems to indicate that it's having a problem writing the file /etc/lotus/notes/notesrc.  I have watched and seen that it creates a /etc/lotus/notes/data directory during the install, so it can clearly write to that directory.

I've created the /etc/lotus/notes directory, and I've made sure that it has write permissions.  After it fails it always seems to delete the /etc/lotus/notes directory as well.

Any hints or tips would be appreciated.  Thanks.

Hi kkovach. I got the same problem as you. Did you resolve it?

---

### Post by www.rzr.online.fr on 2008-03-11
[QUOTE=kkovach]
 The installation log seems to indicate that it's having a problem writing the file /etc/lotus/notes/notesrc. 

[/QUOTE]

Same issue here, I started setup.sh -console as root from C14SXEN.tar

Any other package to test ?

Error also for fedora : 
[http://forums.fedora-fr.org/viewtopic.php?id=24518&p=2&words=notesrc](http://forums.fedora-fr.org/viewtopic.php?id=24518&p=2&words=notesrc)

---

### Post by frozenjim on 2008-05-03
> **www.rzr.online.fr said:**
> Same issue here, I started setup.sh -console as root from C14SXEN.tar

Any other package to test ?

Error also for fedora : 
[http://forums.fedora-fr.org/viewtopic.php?id=24518&p=2&words=notesrc](http://forums.fedora-fr.org/viewtopic.php?id=24518&p=2&words=notesrc)

I'm having the same problem.  It dies because it cannot write to notesrc.  

Actually that was my SECOND issue.  First was easily resolved:
./setup.sh would not run in graphical mode.  Installed stdc++5 and gui works.
```
sudo apt-get stdc++5
```

We'll get this running yet.

---

### Post by Blixo on 2008-05-06
Some more info here:

Installing Notes 8 Gold on Ubuntu 7.0.4
Category Lotus Notes 8 Ubuntu Feisty Fawn

As has been mentioned in the comments of this thread over on vowe.net, you can run Notes 8 on an Ubuntu Linux Desktop.  I just completed the Notes 8 installation atop a fresh install of Ubuntu 7.0.4 (Feisty Fawn), and hit one little snag stemming from the way Ubuntu handles "administrator" or "root" access.  Being new to Ubuntu this exact approach wasn't immediately apparent, but after a little poking around the Notes 8 Forum and little trial and error, here are the steps to success:

[http://www.lotusguru.com/lotusguru/LGBlog.nsf/D6Plinks/20070820-76A4A4](http://www.lotusguru.com/lotusguru/LGBlog.nsf/D6Plinks/20070820-76A4A4)

---

