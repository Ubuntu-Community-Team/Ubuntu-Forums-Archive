---
title: "SomeonePleaseHelp!"
date: 2008-07-05
forum: General Help
---

### Post by Fightparis on 2008-07-05
I recieved Ubuntu in the mail today, 8.04 LTS desktop Edition (64 bit)
So I put it in and booted off the cd to try it out like it said etc..
so after trying it for a while I restarted and took the cd out and went back to my original OS win XP media center
Not that i didnt like ubuntu just i was going to wait until later to install it.
Anyways I restarted my computer, and now it goes to a screen telling me to choose to boot with ubuntu or xp regardless if the cd is in or not, and if i choose xp it goes to the error occured screen where i can choose safe mode, or start windows normally etc.. 
so When I try that, It begins to load xp at the screen but then the BSOD Blue screen appears with a Unmountable Boot error and then everything restarts again Regardless of i try safe mode etc..
I have a lot of documents and work on my hd that i cant afford to lose, can someone please help me out with this problem,
Much appreciated.
-dhobbs

---

### Post by avtolle on 2008-07-05
You are sure you didn't begin to install then abort, right? Did you remove the CD without telling the system to shut down? I think you are going to need to repair the boot block on Windows, but I've not any idea of where to start with that.

---

### Post by Fightparis on 2008-07-05
OMG Thanks.
And yeahhh...I did go to install then abort.
But I didnt get passedthe hard drivepartitioningproblem
I stopped their to go figure out how to do it.
It didnt start installing anything i just madeit to step 3 or 4 of seven?
Do you have any idea of what I can do?
and is this a serious problem?

---

### Post by avtolle on 2008-07-05
It would be helpful to know what your partition table looks like right now; if you can, boot the Ubuntu Live CD and, after it boots and you are at the desktop, get to a terminal (since you are new, try clicking on Applications in the top panel, then click on Accessories, then Terminal), and at the terminal, type in ```
sudo fdisk-l
```and post the output here.

---

### Post by avtolle on 2008-07-05
Sorry about this, I'm needing to leave (haven't been keeping track of the time too well) so; take a look at this thread, too [http://ubuntuforums.org/showthread.php?t=848424](http://ubuntuforums.org/showthread.php?t=848424) and see whether anything there might help you (you can install the app running the Live CD). Good luck; post the results of the command I gave you, and hopefully, someone with more knowledge than I can jump in here and get your problem resolved.

---

### Post by Fightparis on 2008-07-05
ALright for sure.
I did what you said and nothing was showing up for "sudo fdisk-1"??
are their supposed to be spaces anywhere?
it just says 
Commandnot found??
am i do anything wrong?

---

### Post by Sef on 2008-07-05
> 
Code:

sudo fdisk-l

and post the output here.

That's a small L.

---

### Post by sayakb on 2008-07-05
Actually, it is sudo fdisk <space> -l
```
sudo fdisk -l
```

---

### Post by Fightparis on 2008-07-05
Alright tahnsk alot.
It says.
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads,63sectors/track, 30401cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk Identifier: 0xa8b88654
Device Boot    Start    End    Blocks    Id    System
/dev/sda1 *        1    28703  230556816  7     HPFS/NTFS
/dev/sda2      28704    30401   13639185  c     W95 FAT32 (LBA)

Hope this helps thanks ahead of time.
This is really agrivating.

---

### Post by caljohnsmith on 2008-07-05
Do you have an original Windows CD? Just boot it up, enter recovery mode, and then run the command "fixmbr" to restore the Windows boot record to the MBR (Master Boot Record) of your HDD. You may have more problems with Windows since you fiddled with partitioning it sounds like, so you may have to do a Windows repair with the Windows CD.

If you don't have a Windows CD, you can download "Super Grub Disk", burn it to a CD, boot it up, and use that to replace your Windows MBR. It's available at: supergrubdisk.org. Or if you have internet connectivity when you boot your Ubuntu Live CD, just install "ms-sys" package, and run the command "sudo ms-sys -m /dev/sda" to restore Windows to the MBR.

---

### Post by Fightparis on 2008-07-05
aweh man i dont have my windows cd
i have a Hpcomputer so its on that restore drive
and i cant really repairfrom it.
and I dont have a cd burner on my currentcomputer:(

---

### Post by falcon61102 on 2008-07-05
Most computers, even though they have a restore drive, still have a cd that comes with them for a system restore.  That should actually be your windows cd and you can use that.

---

