---
title: "A spare partition? (56k warning) &amp; Bizarre root icon on desktop"
date: 2006-11-12
forum: General Help
---

### Post by Velotix on 2006-11-12
Whilst getting used to KDE (this initially being a Xubuntu install), I stumbled upon the menu showing the list of mounted hard-drive partitions. What I found was rather surprising (see attached screenshot).

What is that second partition (/dev/sda2)doing there, and two: could I make good use of it by resizing it and putting my /home/ folders within that partition?

Also, there's an icon on my desktop which points directly to the root folder (see other attachment), and I'm a bit weary of it - it appeared on startup one day automatically and has just sat there. Whilst I'm happy to use it, I'm not sure exactly what it is - is it a symlink? Is it safe to remove if I so wish?

Similarly, how do I add desktop icons that point to my mounted drives? I recall having some difficulty trying to get icons to point to individual partitions.

---

### Post by catlett on 2006-11-12
/dev/sda2 is your extended partition. It isn't a 'real' partition. Meaning you do not access it directly. An extended partition is a primary partition that houses logical partitions. In this instance it houses /dev/sda5.
You only have 2 partitions that can be 'used', /dev/sda1 and /dev/sda5.
For future reference, Primary partitions own 1 thru 4
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
Logical partitions start at /dev/sda5
/dev/sda5
/dev/sda6
etc
No matter how many primaries you have, the logical partitions will start at 5. That is why your partitions skip from sda2 to sda5. It is also how you can quickly tell that sda5 is a logical partition and you can further deduce that  one of your primaries is an extended partition because a logical partition has to reside in an extended primary partition.
The last bit of evidence is the size of /dev/sda2. It is only 1kb.

As for the icon, you must have enabled icons visible somehow. I do not know how it is done in kubuntu but in ubuntu you go into the 'configuration editor' under Systems Tools and enter into Apps>Nautlus. In that section is a box you can check or uncheck to make 'volumes visible' or invisible on the desktop.

P.S. How are you able to crop your screen shot of your desktop to just show the volume icon? I always end up posting the entire screenshot and use a pencil in Gimp to circle the specific area. Not very professional or appealing but it is the limits of my ability just the same. Anyways, is there a simple procedure to 'crop' the screenshot or is it very involved? If it is relatively simple, would you do me the favor of enlightening me? Thanks.

---

### Post by syadnom on 2006-11-12
exactly.  to add a tidbit here.  the 1K sda2 'extended' partition very simply maps out the extended partitions, it doesn't contain them... an extended partition counts as a primary so you can have
sda1 sda2 sda3 and sda4 with 1-3 bing primaries and sda4 mapping the extended sda5 sda6 sda7 sda8...

---

### Post by catlett on 2006-11-12
> **syadnom said:**
> exactly.  to add a tidbit here.  the 1K sda2 'extended' partition very simply maps out the extended partitions, it doesn't contain them... an extended partition counts as a primary so you can have
sda1 sda2 sda3 and sda4 with 1-3 bing primaries and sda4 mapping the extended sda5 sda6 sda7 sda8...

Thanks for the detail. I apologise for my lack of technical knowledge. I'll make sure to state 'the extended maps out the logicals' in the future.  I was wondering why the 1kb, now I know.:D

---

### Post by Velotix on 2006-11-12
> P.S. How are you able to crop your screen shot of your desktop to just show the volume icon? I always end up posting the entire screenshot and use a pencil in Gimp to circle the specific area. Not very professional or appealing but it is the limits of my ability just the same. Anyways, is there a simple procedure to 'crop' the screenshot or is it very involved? If it is relatively simple, would you do me the favor of enlightening me? Thanks.

You could probably tell me how to simplify the procedure, but in essence I rip off the procedure from the way I do it in Windows, except for some reason GIMP doesn't want to paste in screencaps, so I have to do it the long way round. Anyway:

1) Take a screencap and save as a PNG.
2) Open GIMP or equivilent.
3) Using rectangular select tool, highlight the area of the desktop that you actually want.
4) Copy the selection to clipboard (<Ctrl>-C or via menu)
5) Open a new file.
6) Paste into the new file.
7) Save.

Much neater. Hope that helps. ^^

> As for the icon, you must have enabled icons visible somehow. I do not know how it is done in kubuntu but in ubuntu you go into the 'configuration editor' under Systems Tools and enter into Apps>Nautlus. In that section is a box you can check or uncheck to make 'volumes visible' or invisible on the desktop.

I should have mentioned that the icon appeared only after I tested my USB flash drive on the system, which also creates a link to itself on the desktop when it's connected. I'm guessing this also forced it to show hard drives as well... which come to think of it **is** my fault. Now I know why it's disabled by default. Now I just have to find it again. :P

And I did, under System Settings > Desktop > Device Icons. Yay. Looks like it'll take effect when I restart. Thankede.

> Similarly, how do I add desktop icons that point to my mounted drives? I recall having some difficulty trying to get icons to point to individual partitions.

And I can answer my own question with something I remembered from when I first installed Xubuntu: if a device isn't blank, it'll show up on the desktop unless you tell the desktop manager otherwise, so problem solved. ^^

Thanks for your help, folks. That leaves the one unanswered question, which I shall update with the extra info:

**Could I make good use of /dev/sda2/ by adding a /dev/sda6/ partition, shrinking my huge /dev/sda1/ partition in the process and put my /home/ folders within /dev/sda6/?**

I should note that this install is so recent that my /home/ folder isn't very big right now, and most of the files are already backed up because they came from the backup in the first place.

---

### Post by catlett on 2006-11-12
The easiest thing would be to make another primary partition. There are certain limits about where and how you can add space to partitions. I would attempt to shrink sda1 and make another primary ext3 partition out of the new space, leaving sda2 and sda5 alone. It should come up as sda3 but it may take sda2, I am not sure but it shouldn't affect your system since sda2 isn't mounted anywhere and sda5 will stay the same no matter what.
That is a long way to say, shrink sda1 and make a new primary ext3 with the space (if the system allows you).
To do the procedures, I would use gparted live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and follow the instructions laid out in Aysiu's How To [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

P.S. Thanks for the instructions for the 'cropping'. :-D  Hope the links are helpful, it is past my bedtime and I need to turn in. Good luck.

---

