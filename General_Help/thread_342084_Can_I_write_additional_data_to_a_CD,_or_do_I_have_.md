---
title: "Can I write additional data to a CD, or do I have to burn a whole new one?"
date: 2007-01-19
forum: General Help
---

### Post by tc101 on 2007-01-19
I am using ubuntu 6.10.  Can I write additional data to a CD, or do I have to burn a whole new one?  I know how to go to Places>CD/DVD Creator and write data to a CD from scratch, but what if I want to add new data to a CD I have already created?  If I open the CD in Nautilus and try to paste a file I have copied from somewhere else it won't let me.

---

### Post by jimbob on 2007-01-19
The only program I know of that will do that is Nero.

I think they offer a free trial if it is only a one-time thing you need.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by tc101 on 2007-01-19
Too bad.  Windows lets you do it.

---

### Post by tc101 on 2007-01-20
Let me ask another related question then.  Once I have burned a CD, is there a way to erase everything on it and start from scratch a reburn it with new data?

---

### Post by jimbob on 2007-01-20
Well sure if you buy the CD+RW/-RW blanks and your burner is capable of eraseing.

EDIT:  It may be that only the CD-RW re-writeable format is available.   I was thinking of the DVD+RW/-RW which has both.

---

### Post by Tiede on 2007-01-20
It depends on the type of CD you are using. And the Nero bit above is quite misleading.
If the data is on a CD-R (Compact Disk - Recordable), it means that it can only be written to somewhere *once*. If data is written on a CD-R, it *cannot* be erased. Ever. The way to get a CD-R to write *additional* data depends on the burning option you use. If you used DAO (disk-at-once) the entire disk gets finalized and you can no longer write on it; If you used SAO (session-at-once) then there is a chance for it to be written to again, albeit enough remaining freee space. Same goes for TAO (track-at-once) with enough free space available.

As you can see, this does not depend on the software, be it nero or whatever. I use Gnomebaker (Gnome-centered) and K3B(KDE-centered), and they too have the options discussed above for burning to a CD-R disc.

Finally, to answer the question on how to erase a CD and rewrite on it, the only possible way is if you buy a CR-RW disc (which stands for Compact Disk Re-Writable). Such discs can be blanked (erase) and rewritten to -although not indefinitely. On average, they allow for 10 such operations.

---

### Post by wpshooter on 2007-01-20
> **tc101 said:**
> Let me ask another related question then.  Once I have burned a CD, is there a way to erase everything on it and start from scratch a reburn it with new data?

Look under the add/remove section of Ubuntu in the sound section and the find, check and install the K3b CD burning program and then get yourself a few good name brand (I prefer Imation) CD-RWs and you are good to go.  K3b has the ability the erase CD-RWs and also to add files, etc. to an exiting CD media.

Good luck.

---

### Post by tc101 on 2007-01-20
I am using CD-RW.  I should have said that in the beginning.  They are Memorex, CD-RW.  It says 4x, 700mb, 80 min.  Rewritable copact discs for computer CD writers.

---

### Post by tc101 on 2007-01-20
I just installed the K3b CD burning program.  It looks like it will do what I want.  I need to read the help manual.  I'll report back later and tell you how it worked.

---

