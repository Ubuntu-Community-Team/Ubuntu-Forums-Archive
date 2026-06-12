---
title: "Advanced GRUB Question - relocate menu.lst to another partition"
date: 2007-02-28
forum: General Help
---

### Post by toddhd on 2007-02-28
This might be the wrong place to ask this, but I'm just not sure what to do. Any info would be appreciated.

Here's the problem. When you install Ubuntu (or any Linux frankly) it installs GRUB (or Lilo) in the MBR, and then puts the menu info in /boot/grub/menu.lst on the partition where Linux resides. Normally, this is fine.

But consider the case when Linux is installed on a removable drive. My (work) laptop has a bay that I can swap the CD for a second hard or other devices, and I regularly swap items in/out of there. I have linux installed on my removable drive.

If I boot up with that second drive in place, all works well. But if something else is in there, then Grub just dumps and refuses to run. I don't know why Grub isn't smart enough to just give you some sort of default menu for whatever partitions do exist, but it doesn't - you simply can't boot.

The most obvious solution to me (aside from re-writing Grub) is to simply move the menu.lst file to the hard drive/partition where Windows resides, instead the Linux drive. 

So the question is - can this be done? How would I go about relocating menu.lst to my Windows partition?

Thanks for any advice you can offer. I've been scouring the web, even the Grub website, and I just can't seem to locate the info I'm looking for. Maybe I'm just searching on the wrong terms, but hopefully someone here has some ideas.

---

### Post by john.nicholls on 2007-03-01
The best resource I've found on the options in GRUB is [www.linuxjournal.com/article/4622](www.linuxjournal.com/article/4622)
Hope that helps.

---

### Post by rsambuca on 2007-03-01
I assume you are getting a grub error 22?  

One method to get around this is to create a small /boot partition on your XP drive.  I would recommend using the gParted live CD and creating a tiny partition to be used as your /boot drive.  Then all of your booting instructions can be stored there.

---

