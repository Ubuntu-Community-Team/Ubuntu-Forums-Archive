---
title: "Where's all my space gone? :O"
date: 2005-10-25
forum: General Help
---

### Post by PriceChild on 2005-10-25
I'm currently running a dual boot with XP and Breezy.

Ubuntu is running on a 9Gb partition and somehow i only have 500Mb left! :O

I've entered nautilus as root and checked the size of all the folders in the file system and can't account for the space being used.

I do have about 45Gb of NTFS and FAT32 mounted in linux, would ubuntu be copying some of this to it's ext3 for use?

Please could someone give me any ideas?

Pricey

P.S. Rhythm Box music player has all it's music from the NTFS partition. This is about 6Gb which at a guess is near the amount missing from my Linux. Would this program have copied all the music to it's own directory seen as it couldn't write to the NTFS? I've searched the filesystem, but couldn't find any of my music. Would this be because i've only been searching as my own, not root account? How could i search using root?

---

### Post by kurtkraut on 2005-10-25
Where do you have only 500Mb left ? In ubuntu partition or in Windows partition ? Ubuntu won't touch other partitions unless you tell Ubuntu to do it (e.g: copying a file from a partition to another)

And, have you checked if you did the partition table correctly ? Is there any unpartitioned space in you hard disk ?

---

### Post by paulle on 2005-10-25
try:  apt-get clean
       apt-get autoclean

---

### Post by PriceChild on 2005-10-25
That's all that's left on my linux (ext3) partition.

I've just noticed that despite "MOVING" a 600Mb avi file from the ext3 to the FAT32, the space is still used on the ext3 :S

(btw i'm using the disk manager to check the free space on the disks)

---

### Post by PriceChild on 2005-10-25
Thanks Paulle... i'm back to 1.28 Gb free, but still no-where near where i think i should be :S

---

### Post by timczer on 2005-10-25
Also check your trash.  On my hoary install I ended up with a ton of deleted files in my root account trash.  I would empty the desktop trash file and don't know exactly how I got so much stuff in the root trash.  I guess that is what happens when you are new and goofing around adding and subtracting stuff.  It ended up being like 2 gigs of stuff.  If you go to your file system and go to root, show hidden files, and look at .trash.  Open as root and delete all the trash.  I am sure there is a better way to get rid of those files and probably a way not to get deleted files in there, but this worked for me.

---

### Post by JurB on 2005-10-25
"try: apt-get clean
apt-get autoclean"

What is it and what does it do?
A little more info please.

---

### Post by kblood on 2005-10-25
Maybe this is silly, but have you tried emptying the trash?

If you delete stuff using Nautilus, it goes to the trashcan, it doesn't get inmediately deleted (so it works like Windows and Mac, I guess).

---

### Post by JurB on 2005-10-25
[QUOTE=timczer]Also check your trash.  On my hoary install I ended up with a ton of deleted files in my root account trash.  I would empty the desktop trash file and don't know exactly how I got so much stuff in the root trash.  I guess that is what happens when you are new and goofing around adding and subtracting stuff.  It ended up being like 2 gigs of stuff.  If you go to your file system and go to root, show hidden files, and look at .trash.  Open as root and delete all the trash.  I am sure there is a better way to get rid of those files and probably a way not to get deleted files in there, but this worked for me.[/QUOTE]


Man, i just freed up 8 gig that way... tnx!

---

### Post by PriceChild on 2005-10-26
[QUOTE=timczer]Also check your trash.  On my hoary install I ended up with a ton of deleted files in my root account trash.  I would empty the desktop trash file and don't know exactly how I got so much stuff in the root trash.  I guess that is what happens when you are new and goofing around adding and subtracting stuff.  It ended up being like 2 gigs of stuff.  If you go to your file system and go to root, show hidden files, and look at .trash.  Open as root and delete all the trash.  I am sure there is a better way to get rid of those files and probably a way not to get deleted files in there, but this worked for me.[/QUOTE]


I love you :)

Another 2.2 Gb freed :D

It's ended up there from me deleteing stuff from the root account.

Thanks all for helping, i'll settle with the free space i have now :D

Pricey

P.S. i'm amazing myself, had breezy a week, and haven't booted windows the past 4 days!!! Luvin it :)

---

