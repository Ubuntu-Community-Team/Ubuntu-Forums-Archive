---
title: "Grub Error 26 when want load ubuntu"
date: 2007-02-09
forum: General Help
---

### Post by skyjuice on 2007-02-09
Dear All

Hi this is maybe kinda a newb question , i have 1 pc and install it with ubuntu for a few month and its working well i think but yesterday suddenly after i want to on my pc, it show error above, i dont know what happen, its is because of ubuntu or my hdd is corrupted/near dead? but if i want to backup all the file in my ubuntu did u have any solution to do it? right now i even cant load ubuntu and its frustrating because all my important file in that pc and i not backup any of this file

somebody help me :(

---

### Post by Herman on 2007-02-10
From the Gnu Grub manual,
> 26 : Too many symbolic linksThis error is returned if the link count is beyond the maximum (currently 5), possibly the symbolic links are looped.  This is the first time I have ever heard of anyone with this grub error. This could be very interesting to learn about.

But you would not be as interested as I am, you just want to rescue your data right? Okay, what kind of media can you save it to? Have you got DVDs, CDs, or an external hard disk? Or have you got another computer maybe, such as a laptop or any other computer?
Have you got a crossover cable or two ethernet cables and an ethernet switch?

If you have even a few of those things or you can borrow them from friends then all you have to do is run a Live CD. 
Here are two how-tos about mounting your partitions in a LiveCD, 
[            Mount a Windows FAT32 or NTFS filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop")
[                           Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
If you have any problem understanding either of those, scroll up to the top of that page and read it from the top down. If you still have problems then ask me. That should help you do half of the job.
The other half of the job will be copying and pasting your files to whatever kind of media you have, through the CD drive, or a USB port, or through a network.
The easiest way is to just plug in a big empty external USBdisk and copy all your files into it. That's the fastest and best.
If you no external drive and you have a lot of data and you have another computer that can hold it and you have network wires, then here is a page that will give you some ideas about how to set up an SSH Network connection between two  or more computers. [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")

Good Luck,
Regards, Herman :)

---

