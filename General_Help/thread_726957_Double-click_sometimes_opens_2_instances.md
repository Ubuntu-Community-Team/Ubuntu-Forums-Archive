---
title: "Double-click sometimes opens 2 instances"
date: 2008-03-17
forum: General Help
---

### Post by giuspen on 2008-03-17
Hi, I see that in the past another post was opened on this problem but it seemed that the bug (of nautilus) was solved. I continue to have this problem: often my double click opens 2 instances of what I launched, especially with video files, either with xine and mplayer. Do anybody have this problem right now and was able to solve it?
Thanks and bye.

---

### Post by raevin on 2008-03-17
> **giuspen said:**
> Hi, I see that in the past another post was opened on this problem but it seemed that the bug (of nautilus) was solved. I continue to have this problem: often my double click opens 2 instances of what I launched, especially with video files, either with xine and mplayer. Do anybody have this problem right now and was able to solve it?
Thanks and bye.

I have this a bit in KDE...not sure what it's like in Gnome, but isn't there a way to change how fast it takes for your computer to recognize two clicks as a double-click?

---

### Post by giuspen on 2008-03-18
> **raevin said:**
> I have this a bit in KDE...not sure what it's like in Gnome, but isn't there a way to change how fast it takes for your computer to recognize two clicks as a double-click?

If I change the time between clicks to consider two close clicks as a double click nothing changes unfortunally :(
The single click doesn't open the file, as correct, the double click opens sometimes correct and sometimes 2 instances... hope that 8.04 will solve this... sometimes i even don't use double click but open with right click--"open with..." cause I'm tired from this.
Bye & thanks for reply.

---

### Post by forrestcupp on 2008-03-18
> **raevin said:**
> I have this a bit in KDE...not sure what it's like in Gnome, but isn't there a way to change how fast it takes for your computer to recognize two clicks as a double-click?

KDE is made to usually accept single clicks.

---

### Post by gnivler on 2008-05-19
> **giuspen said:**
> Hi, I see that in the past another post was opened on this problem but it seemed that the bug (of nautilus) was solved. I continue to have this problem: often my double click opens 2 instances of what I launched, especially with video files, either with xine and mplayer. Do anybody have this problem right now and was able to solve it?
Thanks and bye.


I am also experiencing this issue with Hardy and the latest updates installed, still searching for threads.  It seems to follow a pattern, that I have verified with 3 different programs (VLC, Alsaplayer and File Roller), but I suspect it's for every application that doesn't otherwise limit it's own instance count.  The pattern is double clicking the application or associated file type will open 1 instance (normal) twice in a row and on the 3rd attempt it will launch two copies of the application/file.

It doesn't happen if I press enter to launch instead of clicking, and it is *not the way I am clicking* (normal double click).  My mouse is a wireless LX7.  It doesn't happen in preliminary testing for desktop items.

---

### Post by gnivler on 2008-05-19
I solved my problem by manually compiling nautilus 2.23.2 with eel 2.23.1.  I downloaded these two tarballs:

[http://chuangtzu.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.2.tar.bz2](http://chuangtzu.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.2.tar.bz2)
[http://ftp.gnome.org/pub/gnome/sources/eel/2.23/eel-2.23.1.tar.bz2](http://ftp.gnome.org/pub/gnome/sources/eel/2.23/eel-2.23.1.tar.bz2)

There were a bunch of -dev dependencies I didn't have installed but it will tell you which if any, when you run configure; they are available through Synaptic.  For eel I just ran configure then make and sudo make install, for nautilus the prefix defaults to /usr/local/ but I took a guess from 'which' results that it is just /usr on Hardy and seemed to pay off.  You would need to run:

./configure --prefix=/usr

It should summarize the settings after configure where you can see the updated prefix.  Then I just did make all and sudo make install, and rebooted.  Now all my nautilus windows Help > About shows the new version (not to mention my desktop appeared lol).  The best part is I haven't gotten any duplicate windows from double clicking on stuff.

I would suggest great **_caution_** to anyone trying to follow or duplicate what I did, it's probably pretty dangerous since nautilus is so integrated into gnome.  Be prepared for the possibility of having to repair or reinstall your OS.  It worked for me though.
[I]
edit:  should have used --prefix=/usr on the eel ./configure also, it installed to /usr/local.[/I]

---

### Post by giuspen on 2008-06-08
> **gnivler said:**
> I solved my problem by manually compiling nautilus 2.23.2 with eel 2.23.1.  I downloaded these two tarballs:

[http://chuangtzu.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.2.tar.bz2](http://chuangtzu.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.2.tar.bz2)
[http://ftp.gnome.org/pub/gnome/sources/eel/2.23/eel-2.23.1.tar.bz2](http://ftp.gnome.org/pub/gnome/sources/eel/2.23/eel-2.23.1.tar.bz2)

There were a bunch of -dev dependencies I didn't have installed but it will tell you which if any, when you run configure; they are available through Synaptic.  For eel I just ran configure then make and sudo make install, for nautilus the prefix defaults to /usr/local/ but I took a guess from 'which' results that it is just /usr on Hardy and seemed to pay off.  You would need to run:

./configure --prefix=/usr

It should summarize the settings after configure where you can see the updated prefix.  Then I just did make all and sudo make install, and rebooted.  Now all my nautilus windows Help > About shows the new version (not to mention my desktop appeared lol).  The best part is I haven't gotten any duplicate windows from double clicking on stuff.

I would suggest great **_caution_** to anyone trying to follow or duplicate what I did, it's probably pretty dangerous since nautilus is so integrated into gnome.  Be prepared for the possibility of having to repair or reinstall your OS.  It worked for me though.
[I]
edit:  should have used --prefix=/usr on the eel ./configure also, it installed to /usr/local.[/I]

thank u for ur reply, I also have the problem only when double-clicking, pressing enter the problem does not exist, or sometimes i use to right click and "open with" so I have to click only once and the problem doesn't exist again. Before I had the problem with mplayer especially, but now I use gnome-mplayer (I advice it) and i don't have the problem anymore. About compile nautilus it's quite boring cause they update it often and I should compile it all the times.
bye.

---

