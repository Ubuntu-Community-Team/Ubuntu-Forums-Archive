---
title: "Locked out of a ntfs usb drive partition"
date: 2006-10-22
forum: General Help
---

### Post by ubunutucyclotron on 2006-10-22
Hi all.

Got a very strange one here I hope you can help me.

I have a 40gig usb drive (/dev/sdb) that has one fat32 and one ntfs partition. When I first installed kubuntu I could access both fine (read, write, everything)

I then accidentaly deleted the ntfs partition using qtparted, yikes! I used an xp machine to get all my data back and then trashed all partitions, recreated them, formatted them, copied data back etc.

Problem is now I cant get into the ntfs partition! Trying to access it from the storage media folder I simply get the error "could not enter folder /media/datapouch". Browsing to /media I see:

DATAPOUCH
datapouch
DATAPOUCH-1
FAT32CHUNK
FAT32CHUNK-1
FAT32CHUNK-2
FAT32CHUNK-3

and datapouch has a lock on it. It is a locked folder.

Incidentally, running sudo nautalis or sudo konqueror lets me in but is hardly ideal and also when I now run qtparted and select the /dev/sdb drive the application just closes. No crash or errors just the progress window as its getting the drive info pops up for a split second and then the app closes. I cannot change ownership info or anything like that even when running a sudo'd browser. It says not enough perms to do that!!!

So the ultimate newbie request: How can I get everything back to how it was (access the partition from storage media and everything). The drive is blank so we can do anything to it in terms of deleting partitions, creating them, fdisking, whatever.

Many thanks in advance.
Daryl

---

### Post by Najand on 2006-10-22
Hmm, can you post your /etc/fstab file here?

---

### Post by ubunutucyclotron on 2006-10-22
Hi.

Even when the usb drive is plugged in and mounted no /dev/sdb entries appear. The only entries in the file are for my local hard drive and cdrom.

So its only /dev/hda1 - / , /dev/hda2 - /home , /devhda3 - none (my swap) and /dev/hdc - /media/cdrom0

Daryl

---

