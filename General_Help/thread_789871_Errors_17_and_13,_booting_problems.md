---
title: "Errors 17 and 13, booting problems"
date: 2008-05-10
forum: General Help
---

### Post by Boris and Bailey on 2008-05-10
Here's the scenario: I have two SATA hard disks, the first one is Windows (because Billy doesn't like to be second), the second one is Ubuntu. Everything was fine until I installed a new G Force 8400 graphics card. It looked like trouble with the master boot record, as was explained to me a couple of weeks ago.

Now, when the black and white boot-up choices appear, I get error 17 if I try to get into Ubuntu, and error 13 if I try to get into Windows. How's that for a fine howdy-do?

But...if I press "e" for edit, and change the root disk from 1,0 to 0,0; press "b" for boot, I can get into Ubuntu. I cannot get into Windows no matter what edits I make.

I looked at menu.lst and it correctly lists Windows as drive hd0,0 and Ubuntu as hd1,0; just as it was before I added the new graphics card.

Any thoughts on how to solve errors 17 and 13, please?

---

### Post by Herman on 2008-05-11
Would you have unplugged a hard drive or two to get the cables out of the way when you were manouvering your new  G Force 8400 graphics card into place in your computer case?
If so, it's possible that yous PC's BIOS has set them up in the reverse order compared to the way they were before. Your Windows hard drive might be number 2 now and you Ubuntu hard drive could be number 1 in your BIOS.
Some BIOSes set the hard disks according to which ports or slots the cables are plugged into, while others will assign any port number as first boot device if the number 1 port has nothing connected to it at the time. Then when you plug number 1 back in it becomes set as number 2 instead.

You can check either with the 'sudo fdisk -lu' command in a terminal, or by taking a look in GParted (Gnome Partition Editor), or, better still by going into your BIOS and taking a look in your BIOS hard disk boot priority.
Select a hard disk in there and press + or - on your keypad, or an up or down arrow key (depending on what kind of BIOS your computer has), to move the selected item up or down in the hard disk boot order.
That should fix it.

Regards, Herman :)

---

### Post by Boris and Bailey on 2008-05-11
Herman,

What a breeze! Going into the BIOS to make the change was easy and it solved the problem! Our kitties, Boris and Bailey, are snoozing happily in their chairs with approval. Thanks much, Herman.

---

### Post by Herman on 2008-05-11
:lolflag: LOL, 'Boris and Bailey' are kittens?
I thought it sounded like a good name for a legal firm!
I was expecting Boris and Bailey to be lawyers!  :lolflag:
Anyway, I'm glad you got it fixed, 
Regards, Herman :)

---

