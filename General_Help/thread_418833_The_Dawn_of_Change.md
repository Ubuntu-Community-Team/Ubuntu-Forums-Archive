---
title: "The Dawn of Change"
date: 2007-04-22
forum: General Help
---

### Post by Harkainos on 2007-04-22
I have Ubunto 6.10 installed onto the same hd as Windows XP Pro. Currently I cannot boot XP Pro. I need to edit the grub (which I have no idea how to do :). Any help would be appreciated.) 

But, I haven't had the NEED to go to XP. I have found the Ubuntu is currently running all the things I am using. I am a gamer and using wine. I am sure there will be something that wont work in wine - but with tinkering will probably get working.

The question I have for you hardcore Ubuntu Gamers out there is:


Do I still need Windows XP?

---

### Post by orb9220 on 2007-04-22
> The question I have for you hardcore Ubuntu Gamers out there is:
Do I still need Windows XP?


Yes I dual boot

Fixing your grub

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Harkainos on 2007-04-22
I have no idea what i need to type in to get the grub to pull actually boot xp. I have it in the menu.lst but I dont know what the settings need to be. On to reading more.

---

### Post by orb9220 on 2007-04-22
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by Harkainos on 2007-04-22
When I had just windows installed:

First partition: a temp/cache partition
Second Partition: My OS
Third Partition: All my Data



I installed Ubuntu to the 4th partition (and took most of the data partition)

So what should mine look like. I apologize for sound stupid. But I don't know what harddrive nr is and the like.

---

