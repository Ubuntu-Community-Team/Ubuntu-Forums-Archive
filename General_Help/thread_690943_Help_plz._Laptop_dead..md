---
title: "Help plz. Laptop dead."
date: 2008-02-08
forum: General Help
---

### Post by drpwnage on 2008-02-08
I had ubuntu on my laptop (gateway used to be windows xp) everything was fine, decided to go back to windows for gaming reasons, tried putting in windows xp cd and it didnt recognize any hard disks, read up on it found out you need a ntfs format for windows to read it, tried using gparted to turn it onto that, now ubuntu doesnt start and neither does windows. the ubuntu cd starts up with the live cd but i dont want ubuntu back, i want windows. this computer does not have a floppy drive, so i need an iso file or somthing that will reformat my hard drive to a ntfs format, any help?
message me on aim asap or leave a message on here. Biohazarduz

---

### Post by kesman on 2008-02-08
Insert your windows disk and make it format your entire hard disk. That way you'll get rid of ubuntu if you really need to.

---

### Post by drpwnage on 2008-02-08
how do i do that? i dont see that option when i put the xp disk in.

---

### Post by Anacranom on 2008-02-08
I do understand your frustration, I play City of Heroes, World of Warcraft, Delta force 2,3, etc. even Diablo 2, and if I could not play them, and play them better, on Ubuntu, then I would only use Linux (Ubuntu) for my business. That being said if you want windows back I would suggest using an old 98 or ME boot disk, I use a win ME resue boot disk CD that has FDISK on it, fdisk is a great windows tool, once booted to the command line type : 
fdisk
then you should have to say "Y" a few times then you should have 4-5 options, #4 should be ""Display..." hit that and see what you have  and remember that. then just delete all partitions and create a new primary DOS partition, reboot to the cd, at the command line type:
format c:
Y
Enter
once all is done remove the cd and put in your xp cd and reboot.

If you want to learn more about gaming in Linux (Ubuntu), look me up.

---

### Post by drpwnage on 2008-02-08
the problem isnt that i have linux on my computer, its that the xp cd does not even see my hard drive at all. Oh and btw when i start up the computer with no cd in it it gives me the reg boot screan saying grub loading stage 1.5
grub loading, please wait...
error 17

---

### Post by Anacranom on 2008-02-08
Please describe what happens when you power on the PC with the WinXP disk in the drive? Do you get the Install/Repair screen? The EULA screen? it searches for previous installs? Or does it say there are no drives?

---

### Post by kesman on 2008-02-08
If there's not a disk partitioning utility on xp boot disk, then insert the ubuntu livecd and use the partitioning tool in it to erase all data in the disks and format them to ntfs for windows.

---

### Post by drpwnage on 2008-02-08
> **Anacranom said:**
> Please describe what happens when you power on the PC with the WinXP disk in the drive? Do you get the Install/Repair screen? The EULA screen? it searches for previous installs? Or does it say there are no drives?Uh blue screen with windows setup at the top loading like its going to instal the windows xp cd, loads all these things at the bottom, and then says press enter to install windows xp sp2, press f3 to quit, and r to repair, repair says no drives, instal gives the same, and then quit just restarts my computer

---

### Post by mbsullivan on 2008-02-08
Hi drpwnage,

Is the harddrive attached via a SATA interface? If so, an old XP disk does not have the drivers necessary to install to it by default. That being said... you say that you have an SP2 CD. I'm guessing that newer installation CDs have the necessary drivers, unless you're using a homemade slipstreamed CD.

If you think that it's a SATA driver problem (which would manifest itself this way), then I believe you need to boot along with a floppy disk containing the drivers, which will be a problem in your case. 

There very well may be other ways to get around a SATA driver issue... I suggest you look around online for something.

Hope this gives you another angle to attack!
Mike

---

### Post by drpwnage on 2008-02-08
> **mbsullivan said:**
> Hi drpwnage,

Is the harddrive attached via a SATA interface? If so, an old XP disk does not have the drivers necessary to install to it by default. That being said... you say that you have an SP2 CD. I'm guessing that newer installation CDs have the necessary drivers, unless you're using a homemade slipstreamed CD.

If you think that it's a SATA driver problem (which would manifest itself this way), then I believe you need to boot along with a floppy disk containing the drivers, which will be a problem in your case. 

There very well may be other ways to get around a SATA driver issue... I suggest you look around online for something.

Hope this gives you another angle to attack!
MikeXP came on this laptop when i bought it from bestbuy, ive had gateway fix this computer before back when it was xp.

---

### Post by drpwnage on 2008-02-08
> **kesman said:**
> If there's not a disk partitioning utility on xp boot disk, then insert the ubuntu livecd and use the partitioning tool in it to erase all data in the disks and format them to ntfs for windows.
How do i do that, i am on it live, then what?

---

### Post by kesman on 2008-02-08
Go to system -> administration -> partition manager. If it's not there, then install gparted via apt.

---

### Post by Jon Monreal on 2008-02-08
> **drpwnage said:**
> How do i do that, i am on it live, then what?

Personally, I would recommend using the repair function on the Windows XP Install CD by pressing r. Then, you can type in the repair console either format C: /Q  /FS:NTFS or, for a regular format, use format C: /FS:NTFS .

If neither of these work and you are still having a problem, I might be able to further assist you if you tell me a bit more about the problem.

Hope this information helps you.

---

