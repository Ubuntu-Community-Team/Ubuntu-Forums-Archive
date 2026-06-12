---
title: "Question about documentation found for moving my Ubuntu partition"
date: 2015-06-03
forum: General Help
---

### Post by stevecro2 on 2015-06-03
I recently found this article to learn how to move my Ubuntu partition:

help.ubuntu.com/community/MovingLinuxPartition, 

and except for the slight difference of my file system being ext3 instead of the mentioned assumed ext4, it looks like it should be quite handy, but I do have a concern about something that I think could be significantly different.

If I'm reading the article correctly, it looks like the grub menu that it is talking about is the grub menu that I have in my Ubuntu partition, the one that asks which Ubuntu version/kernel/etc. that I want to run. After talking about the grub menu, it then talks about "Updating MBR to point to the new grub".

But I think that my setup is a bit more complicated because (again, if I understand the article, and what I've already installed (and which has worked for years), correctly), then I actually have *two* grub menus. I think that the first one is in my MBR. It's the menu that asks "Do you want to run SuSE? or do you want to run "Ubuntu?", and if I choose "Ubuntu" then it takes me into another grub menu, the one that I think the above article is talking about.

Can anyone give me an idea of what other things I may need to do, or what other additional documentation may be available, so I that I can move my Ubuntu partition to a different spot on my hard disk and end up with both my (now moved) Ubuntu and my other linux(es) on the disk (in this case, my SuSE) all still booting correctly after I have done the move? Thank you in advance!

---

### Post by Bucky Ball on 2015-06-03
Did you install Opensuse last? If so, that probably 'owns' the grub anyhow. 

If it does, then you would move your Ubuntu partition (ALWAYS backup valuable data before proceeding), boot into Opensuse (nothing should have changed with the boot if Opensuse is controlling it) and in a terminal:

```
sudo update-grub
```

... if OpenSuse uses grub, which I don't have clue about. That should pick up the Ubuntu partition wherever you move it to. If Opensuse doesn't use grub, not sure how you would update whatever it does use. Good luck and hope that helps.

---

### Post by v3.xx on 2015-06-03
And here's the nuts and bolts

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by sisco311 on 2015-06-03
You can use [Boot Info]("https://help.ubuntu.com/community/Boot-Info") to get a better picture of your boot environment. Boot Info and Boot Repair can also be used to diagnose and resolve boot problems that you might encounter after moving the partition.

---

### Post by stevecro2 on 2015-06-04
Hi, thanks BB, actually, no, the machine had only OpenSuSE on it first, with a grub menu, and then I installed Ubuntu, which resulted in a second grub menu that I enter after coming out of the first (original) one when I'm running Ubuntu...

---

