---
title: "Backing up my Hard Drive"
date: 2007-04-11
forum: General Help
---

### Post by mrmonday on 2007-04-11
Hi all.

After a terrible shock last night, when I found my PC could not detect my hard drive, I would like to know how to back it up. Really I am looking for software, and it needs to have these features:

[LIST]
[*]The ability to back up everything - (MBR, my partitions(NTFS, ext3, swap)and sizes, data)
[*]The ability to back up to external hard drive
[*]The ability to warn me if I have not backed up in x amount of days
[*]The ability to be able to restore a back up to a new HDD (or RAID array)
[*]The ability to resize the partitions to fit the new HDD
[*]The ability to add to an existing backup, not just create a new one
[*]EDIT: The ability to restore backups and restore my partitions etc back using a live CD or similar
[/LIST]

Thanks if you can help. Also I do not want beta software Reliability is everything for this.

Thanks

---

### Post by borobudur on 2007-04-11
Use the software sbackup or make an image of your harddisk.

---

### Post by mrmonday on 2007-04-11
Thanks for your quick reply borobudur, what do you mean by make an image of your hard disk? how do I do this? Does sbackup to the extra point i added to the list?

Thanks.

---

### Post by borobudur on 2007-04-12
With sbackup you can make an daly or even hourly backup of exact chosen files or direcories to a remote machine or drive. So you hit most of your points in your list.

With the image I don't have any experiance. But I konw from the Windows world that you make an image of your HD with a CD/DVD software (that should be easy with Linux). Then you need a diskette or a CD/DVD where you can start from your machine and do this imaging in the other direction. 

The image is just to restore the system exactly it was at a certain time. And it works just for this machine again. 

But have a closer look on sbackup. That's the backup tool in the linux world.

Cheers!

---

### Post by mrmonday on 2007-04-12
How do i run sbackup? I installed it from synaptic, but I don't know how to run it...

EDIT: Found it. It can only backup my files though. It is important to me that if my hard drive fails, I can restore it, and not have to mess around with installing all my programs in windows, and not have lot my data from windows or ubuntu

---

### Post by cmost on 2007-04-12
Create an image of your hard disk easily with the 'dd' command.  It's fast, easy and foregoes a lot of unnecessary fluff.

Here's an example of how you might do it; create a hard disk backup directly to another hard disk (note, "#" indicates run as root, or use the sudo command:)
#dd if=/dev/hda | gzip > /mnt/hdb1/system_drive_backup.img.gz

Here's an excellent source of information about backing up in Linux.
[http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html](http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html)

Here's another one with even more information:
[http://wiki.linuxquestions.org/wiki/Dd#Creating_a_hard_drive_backup_directly_to_another_hard_drive](http://wiki.linuxquestions.org/wiki/Dd#Creating_a_hard_drive_backup_directly_to_another_hard_drive)

---

### Post by mrmonday on 2007-04-12
Thanks cmost. It looks quite complicated, because if I want to add options, I have to find them in the man page, and check they are right etc... Is there a graphical tool? thanks.

---

### Post by borobudur on 2007-04-12
Looks good to me, cmost!

For your requirement you definitely need to do some studies to be sure what you are doing.

I suggest you still the sbackup. There you define what you want to backup and what you do not want to backup. You can make a daily backup to a remote directory. sbackup also writes a whole list of your packages installed. So if you have to reinstall your system you just use this list and make a restore with the sbackup software. Easy!

---

### Post by mrmonday on 2007-04-14
I have backed up anything highly important using sbackup, but reading into using dd, I don't want to risk using it. Is there a graphical tool for it?

Thanks.

---

### Post by mongooseman1128 on 2007-04-15
If you don't mind spending the $40 for the program, and you have a windows partition on your computer then I would suggest Acronis True Image. It's a pretty nice program, I've used it for reimaging my hard drive many times. It meets all the conditions you need (except I'm not sure how it'll handle a RAID). The downside of course is that it's not freeware and requires windows. I assume it requires windows at least. I highly doubt it can run through wine, but I suppose a VM could do the job. Finally, if you google "acronis true image torrent" it's not difficult to find a good torrent (the setup file with a keygen is only about 35 MB)

---

### Post by mrmonday on 2007-04-17
I have seen good review of Acronis True Image, but can it back up my linux partitions? 
Also will I be able to use it on more than one PC? 
an I restore and have it like nothing had changed? 
Do I have to have to have windows installed to restore? 
Thanks.

---

### Post by mongooseman1128 on 2007-04-19
I think you have to buy a copy for each computer you use it on (but like I said it's a pretty easy to find torrent). Yes, it has full support for all windows and linux file systems (ext 2/3 and ReiserFS-3 and linux swap), it also has sector based support for other file systems.
To restore a computer to the way it was, you boot to a rescue media (CD or floppy) that the program has you make then when you boot the disc (or disk) you point it to where the image file is and it restores from that.
As far as needing windows, the program is for windows. I doubt it will work with wine or something along those lines, but I haven't tried. I also haven't tried it with a virtual machine but see no reason why it wouldn't work with that.
I think I may actually try using wine to install it right now so I'll post when I'm done and let you know if it works or not.

---

### Post by mongooseman1128 on 2007-04-19
Okay, I just attempted installing acronis with wine. It doesn't seem to work. the install will go through alright, but when you try to run the program it says it can't locate a serial number and needs to be reinstalled. I'd say if you want to try and run the program with linux, you're going to need a VM.

---

