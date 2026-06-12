---
title: "Burn backup to multiple DVD's?"
date: 2007-12-25
forum: General Help
---

### Post by perryrt on 2007-12-25
I'm currently using Feisty on my laptop and planning to upgrade to Gutsy as part of my New Year's Resolution (which, for the record, is to *"Get Things Done, Dammit!"*) 

Since I'm a cautious sort, I want to completely backup my system before I do this. I've been using the built-in Simple Backup Suite, so what I'd like to do is copy my last full backup and incrementals since that to DVD's  (I should mention that I'm not so much worried about a catastrophic system failure as I am about losing my personal info, music, etc.)

The only problem is that my backup file is like 11G or so.

I figured out a way to cut it into chunks (using "split -b" on the command line) and then rip the chunks to disc, but I figured I would check - is there a way to have a file "span" multiple DVD's (i.e. let the burner software do the cutting up and restoration later?) It would be much easier.

I should stress that there IS actually a solution to this - but only on the command line - and I'd really like a GUI of some sort for this kinda deal.

Appreciate the help!

---

### Post by TidusBlade on 2007-12-26
Not sure if this is what your looking for, but you can check out ryanVicker's [RAR splitter with a GUI](http://ubuntuforums.org/showthread.php?t=556756), just split them into 3 archives of ~4.5GB and then burn them seperatly, and when you put them back in to your HD, make sure theyre in the same folder and extract one and it will be like how it was when you backed it up.

---

### Post by perryrt on 2007-12-26
> ...check out ryanVicker's RAR splitter with a GUI... 

That's a start, actually. It's roughly the same as I'm doing now at the command line (although I'm using 2.2G chunks, they seem to burn better without any errors - the 4.5G ones make "coasters" about half the time.)

Better, however, would be a single program that would automate the backup process, cut it into bits, and burn it all for me. 

I really have a hard time believing this program isn't out there somewhere - I remember having a similar application for tape drive back in the days I was running a BBS - and that was a QIC-80 drive - I think it had a capacity of maybe 2G or so! (Course, it was attached to a Pentium DX2/66 with a 5G hard drive and a four port modem running XBBS, but that's REALLY dating myself.)

---

### Post by perryrt on 2007-12-26
Woops. Make that a 486 DX2-66 (I had forgotten it had been so long.)

---

