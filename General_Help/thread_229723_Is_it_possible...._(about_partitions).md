---
title: "Is it possible.... (about partitions)"
date: 2006-08-04
forum: General Help
---

### Post by btboudreaux on 2006-08-04
I was wondering, is it possible to install ubuntu on a second patition of a harddrive with Windows being the first partition, then creating an image of ubuntu, then erasing windows and putting the image on the first partiton???

I know if you do this in Windows, all hell breaks loose. Just wondering if Ubuntu could work on a different partition than it was originally installed on.

---

### Post by Ramses de Norre on 2006-08-04
I think it can.. Though I'm not totally sure.. You'll need to fiddle with grub and fstab to make it work but I think those are the only two files affected by the change.
Back up before trying!;)

---

### Post by btboudreaux on 2006-08-04
Thanks! Anyone else can confirm that it would work?

In windows you'd have to change every instance of D to C in the registry and everywhere else. It's pretty damn near impossible and much easier to just do I reinstall. It would be great if you could do this in Ubuntu with just configuring grub and fstab!!

---

### Post by Herman on 2006-08-04
> Thanks! Anyone else can confirm that it would work? Yes, I can confirm that it will work. I have tested out this and quite a few similar things to do with copying and pasting partitions with [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"). 
You will need to [re-install Grub]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") if your Ubuntu partition gets a new partition number, and edit /etc/fstab, as Ramses de Norre suggested.

It is also possible to copy and paste the entire Ubuntu operating system, and delete the original Ubuntu install. Then the next time you copy and paste it, it will be given the original install's partition number back again. If you can manage things in such a way as to finish up with it located where you want it and with its original number you will not even need to re-install Grub or edit /etc/fstab. Just boot it and use it as normal.

I used GParted LiveCD to shrink my Ubuntu partition and then I pasted it to the end of my disk as a backup copy. 
Then I deleted the original Ubuntu installation and moved Windows to the middle of my disk (without changing its partition number). After that I copied the backup copy of the Ubuntu partition to the start of my disk so that it was given its original partition number again. So Ubuntu is first on my disk, with partition number 2, and Windows is still partition number 1, but it is actually located second on my disk. Neither operating system knows the difference, they boot boot up and operate perfectly.   
And also, I just keep the small copy (2.5 GB) of my Ubuntu partition at the end of my disk to restore from if I do something silly to my operating system.

Regards, Herman :D

---

### Post by btboudreaux on 2006-08-05
Well that's awesome! I've been using Ubuntu for about a month straight on my laptop ever since I got wireless working. I keep learning new things everyday! Thanks for all the help, both of you. I may need to do this soon and didn't want to have to reinstall and reconfigure.

---

