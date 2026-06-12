---
title: "Text editor to view large text files"
date: 2007-12-17
forum: General Help
---

### Post by stchman on 2007-12-17
Hello all.

I have some very large text files (~300MB) and I have no way to view them in Ubuntu.  Textpad in Windows is able to but I don't want to have to switch back to Windows for this functionality.  I looks as though gedit is not up to this task.

Does anyone have any suggestions?

Thanks.

---

### Post by diatribe on 2007-12-17
there are hundreds of text editors, try openoffice or abiword

---

### Post by RHTopics on 2007-12-17
vim can read large text files.

Interestingly enough, found this link when confirming vim can handle large files.

[http://ask.metafilter.com/54151/TextPad-for-Linux](http://ask.metafilter.com/54151/TextPad-for-Linux)

---

### Post by stchman on 2007-12-17
Thank you all, vi or vim is not favorite editor but I will try.

---

### Post by dagnabit dang doohickey on 2007-12-17
I just ran a test on my laptop (~160MB free memory) using a 99MB text file:
vim - Opened the file in about 10 seconds. Very responsive.
geany - Took about a minute to open. Somewhat clunky when hopping around the file, otherwise useable.
gedit, leafpad, komodo edit - Killed all after waiting about two minutes for the file to open.

---

### Post by fjgaude on 2007-12-17
I would say geany is your cup of tea... nice GUI and handles very big files. Else go with the word processors mentioned by others.

---

### Post by jimmyxx on 2008-01-08
I have a 2.2 GB SQL dump I'm trying to edit with no luck.... 

All suggestions on this thread with a gui either refused to open it or they did but i was forced to kill them after waiting 5 minutes and them chewing up all my 4 gigs of my memory! I've had most luck with nano but even that is fairly unusable :(

---

### Post by p_quarles on 2008-01-08
> **jimmyxx said:**
> I have a 2.2 GB SQL dump I'm trying to edit with no luck.... 

All suggestions on this thread with a gui either refused to open it or they did but i was forced to kill them after waiting 5 minutes and them chewing up all my 4 gigs of my memory! I've had most luck with nano but even that is fairly unusable :(
Well, that's certainly an ungainly size for a text file. ;)

I'd say your best bet is Vim, and not the GUI version. You also may need to create a loopback image file and mount that as extra swap space.

---

### Post by nick_h on 2008-01-08
> I have a 2.2 GB SQL dump I'm trying to edit with no luck....
Have you thought about splitting the file into smaller pieces to edit and then re-combining them later?

---

