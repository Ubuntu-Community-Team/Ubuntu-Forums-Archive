---
title: "Synaptic Installs Require System Disc (Already in Drive, not Recognized by System)"
date: 2007-08-13
forum: General Help
---

### Post by Brendo613 on 2007-08-13
I have had many problems with this specific computer under Windows and Ubuntu.  Ubuntu works flawlessly on my Laptop, so I know it's the computer that's at fault.  Regardless, I reinstalled the OS yesterday, this time using Ext3 filesystem just for the hell of it.  

I'm now trying to install KTorrent (and several other appsi) through Synaptic, but it keeps asking for me to insert the system disc labeled Feisty Fawn 7.04 i386.  It's already in the drive ... I even tried the other CD drive, and, despite both being able to read the disc and display its contents, it's not recognized under Synaptic.  I also can't install KTorrent via "sudo apt-get install ktorrent".  

What is the problem here?  Is this related to using Ext3 vs. ReiserFS?

=Brendan

---

### Post by igknighted on 2007-08-13
Sounds like you used the alternate CD.  Go to (in synaptic) tools->repositories (IIRC) and disable the CD as a repo source, or just comment that line out in the /etc/apt/sources.list file.

---

### Post by kelvin spratt on 2007-08-13
Just go to settings in sypaptic click repossitories at the bottom of the sources  list uncheck Feisty Cd that it cured it will then download the files you want

---

### Post by Brendo613 on 2007-08-13
Thanks guys, that did the trick!  Any clue why the CD wasn't being read, even though it was in the drive?  Very odd.

=Brendan

---

