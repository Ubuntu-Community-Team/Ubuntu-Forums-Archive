---
title: "Sony Vaio - Built in memory stick"
date: 2005-09-12
forum: General Help
---

### Post by Zotova on 2005-09-12
My vaio (pcg-k115b) has a built in memory stick slot however when I put a card in ubuntu does not seem to be able to access it.

I have tried mounting /dev/sda and /dev/sda1 as stated in other topics but neither of those work.

Anyone got any ideas, or a program/driver to get the slot working?

Thanks.

---

### Post by Zotova on 2005-09-13
Anyone got any ideas?

---

### Post by ExMachina on 2006-09-22
Same issuse

Sony Vaio PCG-K13 <<
This is the ONLY issue ive had. I love the Ubuntu but i need to be able to upload my pictures for work .

---

### Post by nyy3321 on 2006-10-11
Same problem as the 2 others... anyone?

running dapper on a vaio R505GCK

---

### Post by evereign on 2006-11-17
me too. pcg-k23. anyone? i've been trying to solve this problem for ever...](*,)

---

### Post by maikischa on 2006-11-18
Same Problem on FE21M

---

### Post by tugh on 2007-01-02
Same problem on pcg-k27 ](*,)

---

### Post by fragos on 2007-01-02
Enter lsusb on the command line.  Then insert a memory stick and lsusb again.  If there's no difference, perhaps Sony has a proprietary interface not supported by Linux.  My friends Vaio has a memory stick slot in the front but doesn't have any USB ports.  It's common for the different memory cards to use USB to connect to the readers.

---

### Post by glenndavy on 2007-01-12
Seen this?
[http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_SD_Card_Reader](http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_SD_Card_Reader)

---

### Post by gorgonikos on 2008-06-28
I am booting 8.04 on a Vaio NR21Z. I've got exactly the same problem: the built-in 'Memory stick Pro' slot doesn't work. However the SD slot just near it works fine. Note that the instructions given in previous posts refer to SD slots, not to the Sony Memory stick one. 
This looks like a proprietary drivers issue don't you think? 
Any solutions, anyone?

---

### Post by fragos on 2008-06-28
On desktops, all card readers use USB. To save money laptops will use proprietary hardware which will require a special driver. Sony's original laptop designs only supported memory sticks. The SD was a concession to their customers and may use a different chip set than their memory cards.

---

