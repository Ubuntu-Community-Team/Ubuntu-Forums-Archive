---
title: "Lost Program"
date: 2004-11-19
forum: General Help
---

### Post by ~zoey~ on 2004-11-19
I installed the program 'reminder' with a downloaded deb using dpkg -i <file>.deb and it installed with no problem but I can't find it.  It doesn't show up anywhere, not even in synaptic.

When I use run I get this:

Cannot display location 'file://reminder

Details:  The specified location is invalid

How do I go about finding it and setting it up so that I can use it?

Thanks, zoey :confused:

---

### Post by dataw0lf on 2004-11-19
go to the command line, and run a 'locate -u'.  After that is finished do a 'locate reminder' or whatever the exact name of the program is, it should show up somewhere (most likely in /usr somewhere).
dataw0lf

---

### Post by ~zoey~ on 2004-11-19
I had a typo in my first post.  It is called remind.

I logged out and back in and now it shows up in synaptic but nowhere else.  I upgraded it with synaptic but that didn't help any.

Locate remind brings up a bunch of files that all begin with/usr/share/icons/.

Run remind now just causes the run box to dissapear, but nothing else happens.

What do I need to do to get the program to run so I can see it?

Off subject....how can I copy the terminal output?  Middle clicking or right clicking don't work, and when I use file copy is greyed out, but not paste. 

Thanks zoey   :-?

Edit Addition
  The second time that I used locate remind I got a lot more files.  I used /usr/bin/remind/ and got it added to the menu.  When I click on it nothing happens, no error message and no remind.  zoey

---

### Post by WW on 2004-11-19
Out of curiousity, I installed the package **remind**.  It appears that the **remind** command is intended to be used from a command line in a terminal.  The command for the graphical interface is **tkremind**.

---

### Post by ~zoey~ on 2004-11-19
Yeah, I know that it can be used that way, but the info says that it also has a graphical interface, which is what I am interested in running.

Thanks, zoey

---

### Post by WW on 2004-11-19
**tkremind**

---

### Post by ~zoey~ on 2004-11-19
Duuh, It is probably time for me to give it up for the day!

Thanks, zoey :oops:

---

