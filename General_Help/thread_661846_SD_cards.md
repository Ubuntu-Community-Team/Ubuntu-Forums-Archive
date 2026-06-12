---
title: "SD cards"
date: 2008-01-08
forum: General Help
---

### Post by Jmosler on 2008-01-08
ok this may seem a bit odd...

i have a windows mobile phone (verizon vz 6700)
and a gutsy laptop which is my desktop pc.

it seems that any time i take an 2gb micro sd card from my phone and put it into the ubuntu laptop for a file then put it back in my phone, my phone no longer sees it.

i was just trying to put a cab file on it for installing later.

so far i have tried reformatting the card to both fat 16 and 32. no dice.

and its not just this card. this happened to a co workers card a while back when in the same situation. 

it appears that linux/ubuntu does something to this card that freaks out windows mobile 5.

---

### Post by megamania on 2008-01-08
But does Linux still see it? And does a non-mobile Windows system see it?

Just to understand if the card gets corrupted...

---

### Post by Jmosler on 2008-01-08
yes linux still sees it. and it shows up in an xp machine

---

### Post by Jmosler on 2008-01-09
anyone have any ideas about this?

---

### Post by fragos on 2008-01-09
Mobile devices seem to be very picky about where you put things on an SD card.  If your phone can't see it perhaps it's not where the phone wants it.

---

### Post by Jmosler on 2008-01-10
its not that the phone isn't seeing the file on the card. its that the phone stops recognizing the cards existence.

---

### Post by fragos on 2008-01-10
Has the card been reformatted.  FAT16 I believe is the norm and other formats might not be supported.

---

### Post by Jmosler on 2008-01-14
yeah i have tried reformatting to fat32 and fat16 using gparted. and still nothing.

---

### Post by megamania on 2008-01-15
> **Jmosler said:**
> yeah i have tried reformatting to fat32 and fat16 using gparted. and still nothing.
If you didn't change anything in the card besides adding a file, the only thing I can think of is that linux may have written a *.trash* directory to the card, and your phone doesn't like it (maybe it checks for the directory structure, and if it's "touched" it refuses to use the card).

So, try deleting any linux-related hidden directory on the card.

---

### Post by fragos on 2008-01-15
> **megamania said:**
> If you didn't change anything in the card besides adding a file, the only thing I can think of is that linux may have written a *.trash* directory to the card, and your phone doesn't like it (maybe it checks for the directory structure, and if it's "touched" it refuses to use the card).

So, try deleting any linux-related hidden directory on the card.

Good suggestion.  I've noticed that with 7.10 when you unmount an SD or other USB disk you're asked if if you want to empty the trash which I always do.  I tried an experiment with an SD.  I verified the .trash directory is created when you move to trash on the SD card.  If when prompted to empty trash you do the directory is deleted.

---

### Post by Jmosler on 2008-01-17
ok this is gonna show how much of a newcomer i am....

how do i see the hidden directory?

---

### Post by megamania on 2008-01-17
> **Jmosler said:**
> ok this is gonna show how much of a newcomer i am....

how do i see the hidden directory?
When your card is mounted, double click on it as you would with any other device (i.e. if it appears on the desktop, double click on that icon).

When the Nautilus window opens and you see the contents of the card, select view -> show hidden files, or just press ctrl+h. 
I'm assuming you're using gnome. With other desktop environments, the thing could be slightly (but only slightly) different.

---

### Post by fragos on 2008-01-17
Files and directories whose names start with "." or end with "~" are hidden from normal view.  In nautilus you can do a "CtrlH" to see them.  On the command line "ls -a" will show them.

---

