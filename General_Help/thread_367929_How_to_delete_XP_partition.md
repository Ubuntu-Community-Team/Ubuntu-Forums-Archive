---
title: "How to delete XP partition"
date: 2007-02-22
forum: General Help
---

### Post by SirPaPa on 2007-02-22
Hi, I'd like to delete my Windows XP partition so that my box will boot directly into Ubuntu without losing any data or grub. How would I go about this so that I may use the space being used by Windows? I mean simply deleting the Windows partition would leave me just the Ubuntu partition and not necessary the additional space taken by Windows wouldn't it?

    Thank,you.:-k

---

### Post by Boule on 2007-02-22
grub is located in the MBR (master boot record) of the hard drive, deleteing windows partition won't do anything to grub.

u can use fdisk to format it

---

### Post by SirPaPa on 2007-02-22
> **Boule said:**
> grub is located in the MBR (master boot record) of the hard drive, deleteing windows partition won't do anything to grub.

u can use fdisk to format it

Thank,you. But where do I get fdisk and how do I format it? Once again, thank you.:-k

---

### Post by Kateikyoushi on 2007-02-22
I think gparted is better for you, it can delete, resize partitions with a graphical user interface, quite easy to use.

You just delete your windows partition and make a new ext3 partition in it's place and format it.

Then follow this guide to mount it so can be used. [LINK]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by SirPaPa on 2007-02-22
> **Kateikyoushi said:**
> I think gparted is better for you, it can delete, resize partitions with a graphical user interface, quite easy to use.

You just delete your windows partition and make a new ext3 partition in it's place and format it.

Then follow this guide to mount it so can be used. [LINK]("http://www.psychocats.net/ubuntu/mountlinux")

While in gparted I:-k  found this on the Windows partition:


What does this mean? This symbol on the Windows parttion.
 
Thank,you very much.

---

### Post by netkid91 on 2007-02-22
It means GParted can't read NTFS partitions....won't stop you from reformating it.

---

### Post by jprb85 on 2007-02-22
There is a thing called partition magic which you will want to use if you want to keep your XP files. Other than that the easiest way is just to boot an Ubuntu CD and install it and when given the option, wipe the whole hard drive.

---

### Post by netkid91 on 2007-02-22
He already has Ubuntu installed and just wants to wipe XP off now.  Read the posts please!

---

### Post by SirPaPa on 2007-02-23
> **netkid91 said:**
> He already has Ubuntu installed and just wants to wipe XP off now.  Read the posts please!

Thank,you very much for your help [COLOR="DarkOrange"]netkid91[/COLOR], I regained 40.9 GB of space. Sorry I didn't thank you earlier,by the time I was finished with your instructions I was very tired. But I sincerely thank you.

---

### Post by netkid91 on 2007-02-23
It's no problem, thats why I am here.  If there is anything else you need, just ask.

---

### Post by theslicknick6 on 2007-03-31
hey i am trying to do something similar, I would like to resize the separate hard drive I have windows on down to around 20 gb of the 80 currently in use. I would like to transfer all my music over to ubuntu as well but cant quite figure out how to do that as well. cant find the gpartition thing either. I know I'm full of all kind of problems here but any help would be greatly appreciated, thank you.

---

