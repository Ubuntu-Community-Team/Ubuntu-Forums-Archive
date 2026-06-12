---
title: "How do I add extra hdd to Grub"
date: 2007-11-01
forum: General Help
---

### Post by epicurus on 2007-11-01
Hi

Hope this is in the right section.

My PC has 3 SATA HDD's setup as follows.  Ubuntu, XP and Vista

When I installed Ubuntu I unplugged my other HDDs so that I would not mess things up.  Now I want to add them to GRUB.. 

Can anyone give me some advice/help in how I work out what I need to add so that I can chose which OS i want to load.

Cheers in advanced

---

### Post by Pumalite on 2007-11-01
[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

---

### Post by epicurus on 2007-11-02
Thanks for the info

Most of that I understand,  What I am a little confused about is the:

root   (hd0,0)

Can someone explain the (hd0,0)

Is that first zero the Partition or the physical disk

Thanks again for the help

---

### Post by petteriIII on 2007-11-02
> **epicurus said:**
> Thanks for the info

Most of that I understand,  What I am a little confused about is the:

root   (hd0,0)

Can someone explain the (hd0,0)



First zero is disk, second is its partition.

---

### Post by epicurus on 2007-11-02
thanks for that.

Will have a play tonight and see what I can mess up  :)

Cheers

---

### Post by epicurus on 2007-11-06
Hi

OK..  I have managed to get Vista to boot OK but I am having a few problems getting XP to load..
Ubuntu = 0,0
Vista = 1,0


is there a program I can run that will let me know which HDD is which?

Thanks

---

### Post by dabl on 2007-11-06
This should help:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:popcorn:

---

### Post by epicurus on 2007-11-07
wow.  some info there.  Thanks.  I will have a good read when I get home

Cheers

---

