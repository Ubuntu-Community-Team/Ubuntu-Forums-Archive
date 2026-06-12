---
title: "How Can I Upgrade GTK 2.8? (Firefox Related)"
date: 2008-06-26
forum: General Help
---

### Post by Slapnut on 2008-06-26
Hey Guys,

First post so please be gentle. Been using Ubuntu 6.06 LTS for about 8 months after using Windows all my life (sad I know!) 

Just updated my Firefox browser to the newest release using Ubuntuzilla ([http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)) however my browser no longer starts up and comes up with a message saying I require GTK+ 2.10 library or above for the program to run and that I only have GTK+ 2.8 installed.

Since my browser no longer works, can I use Synaptic Package Manager to upgrade GTK to the required version? What package should I look for?

Tried searching the forums first but had no luck. Any help would be greatly appreciated!

---

### Post by nanotube on 2008-06-26
you could try these instructions:
[http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php)

(or another, somewhat more detailed, but less easy to follow, here:)
[http://blogs.warwick.ac.uk/mikewillis/entry/of_firefox_3/](http://blogs.warwick.ac.uk/mikewillis/entry/of_firefox_3/)
but they're not for the faint of heart - you need to compile the gtk library yourself.

for now, i'd suggest just sticking to ff2 on dapper...

edit: you could also probably get the binary .deb package from, say, feisty (from packages.ubuntu.com), unzip it to somewhere in /opt, and then point LD_LIBRARY_PATH to where you unzipped it - no compiling required. should work - but i don't have a dapper box to test this on.

edit2: here's a direct link to feisty's libgtk .deb: [http://packages.ubuntu.com/feisty/libgtk2.0-0](http://packages.ubuntu.com/feisty/libgtk2.0-0)

---

### Post by nanotube on 2008-06-27
more detailed instructions (and even an automatic shell script to do it all), posted here: 
[http://ubuntuforums.org/showpost.php?p=5273055&postcount=71](http://ubuntuforums.org/showpost.php?p=5273055&postcount=71)
give it a whirl, let me know if it makes firefox happy. :)

---

### Post by nanotube on 2008-07-08
Hi,
see also the latest posts in this thread:
[http://ubuntuforums.org/showthread.php?t=847484](http://ubuntuforums.org/showthread.php?t=847484)

---

