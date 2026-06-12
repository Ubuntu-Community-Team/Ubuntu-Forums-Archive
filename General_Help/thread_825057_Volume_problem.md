---
title: "Volume problem"
date: 2008-06-10
forum: General Help
---

### Post by Snockis on 2008-06-10
[FONT="Verdana"]As you might notice this thread is a about my problem with my volume :P
Any ways, the whole started with that I couldn't mount my external hard driver with NTFS, so I tried some tweaks, first of all I ask'd a dude at work who's a Unix technician and he said that i should type in the "terminal" (Donno if it's named terminal in the un-swedish version :P )

He told me to type "mount -t NTFS /dev/sdb1 /media/externalusb"

So that is what I did. dumb as I was. but I made that dir first since there didn't exist any there before :P

The thing was that sdb1 was another volume with NTFS about 150 GB worth of data.
As you might see I only changed the volume path to /media/externalusb.

At that point I didn't realize that I had changed the path or moved the whole volume or changed the volume name or whatever.
So I DELETED all files/data in that folder which was named externalusb.

Then later I looked in "Hard drive 1" which was the original name of that NTFS volume and saw that all data/files was gone, at that point I realized that I just had deleted 150 GB data.

So I've been lookin' for a program to recover data of a volume and discovered "PhoteRec" which was kinda good but not the thing I was looking for, Since it requires that you have that amount of free space of the data that you want to recover (which in my case was 150 GB), on another partition. I don't have another partition with so much free space.
[SIZE="4"]
[COLOR="Red"]So the question is now, how can I recover my deleted data/files on my "hard drive 1" volume, without being in need to recover all data to another partition?[/COLOR][/SIZE]
As I would have with PhotoRec.

Just a pointer:
:)

I later realized how to mount my external NTFS hard drive :P
just wrote "mount -t ntfs /dev/sdg1 /media/real\ thing force -0" in the "terminal" and all work as intended. (had to force the mount since it didn't allow me to mount it in another way).

another pointer:
I use NTFS cos I got a school laptop with Windows as OS and I'm not allowed to change the OS. So I use NTFS so I can use the hard drive with both my windows based computer and this Unix based computer.[/FONT]

---

### Post by medic2000 on 2008-06-12
"chkdsk /f DRIVE:" command on Win systems to fix the corrupted drives. And sometimes umounting disk from windows solves some problems.For full ntfs read and write support use ntfs-3g driver.

[www.ntfs-3g.org](www.ntfs-3g.org)

---

### Post by drs305 on 2008-06-12
Can you mount the partition you deleted the files from? Preferably to externalusb but it doesn't really matter where you mount it as long as you can access it. I believe Hardy now shows deleted non-ext3 files in a hidden folder called .Trash-1000 (if 1000 is your uid number). Before doing anything to the partition I would look to see if the files were still in a hidden trash folder which you might be able to restore.

---

