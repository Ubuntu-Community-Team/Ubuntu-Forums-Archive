---
title: "I/O error copying files"
date: 2005-04-25
forum: General Help
---

### Post by Domhnull on 2005-04-25
I decided to start with a clean install of Ubuntu.  Before I did I saved my files to CD-R discs and checked each to make sure the files were there.  Everything looked fine... but now I can't access most of the files.

When I open the disc I can see all of the files on the CD and the file sizes look right.  But most of them (not all) won't copy over to the computer. 

Any suggestions would be much appreciated.  Thank you.

---

### Post by ape on 2005-04-25
What errors do you receive while trying to copy the files over? 

How did you copy the files to the CD-R? What file system are you using on the CD-R?

---

### Post by Domhnull on 2005-04-25
I had been using Ubuntu "Breezy" and decided that it was too early to upgrade.  Figured I'd just do a clean install of Hoary.  To back up the files I:

Put in a blank CDR
Dragged files and folders the the Nautilus window
Clicked File | Write disc

After the disc ejected I put it back in and checked that everything looked okay - but I didn't try to open any of the files.  It looked okay and I did the next batch of files.  Took three discs.

After I backed everything up I downloaded the Hoary CD, burned the .iso (again just using Nautilus) and restarted with the install disc.  Installation went fine, very easy, during which I reformatted/partitioned the drive.

But then when I put in the discs I couldn't access the files.  They show up, the file sizes look okay, but when I try to copy them I get a 'I/O error' dialog with the options to Skip, Cancel, Retry.  Retry doesn't work.

I found it interesting that a handful of files on different discs copied fine - but most of them won't copy.

---

### Post by ape on 2005-04-27
Really bizzarre!  Can you access the files through a shell?  Trying to determine if it's a Nautilus thing or the CD copy itself didn't work.

What about on another machine?

---

### Post by Domhnull on 2005-04-27
Thanks.  I think the CD copy itself didn't work.  If I try to copy them using the shell I get the same sort of message.  I/O error.  I tried the disc on another machine and it wouldn't work either.  I think the files are just lost.  I wonder if Nautilus tried to write the files too fast.  I left it on the 'as fast as possible' setting - maybe I should have set it to a slower speed?

---

