---
title: "Hard Drive Partitioning"
date: 2005-10-19
forum: General Help
---

### Post by TrumpetMan258 on 2005-10-19
I am trying to reduce the size of my Windows partition to make some free space for Ubuntu.  However, when I try to do it during the Ubuntu installation, it doesn't work.  I put in a lower number, but then it just goes back to the list of partitions with no changes.  I also tried to use gparted off of the live CD with no success, and I found a suggestion to try the Linux system rescue CD, also with no success.  Any suggestions?  Right now, getting rid of Windows isn't an option; I'd like a dual-boot system.

---

### Post by chaumurky on 2005-10-19
I suggest you do that inside windows with a partition manager like PartitionMagic. I never trust Linux with NTFS...

---

### Post by i0h on 2005-10-19
im going to the same myself tonight :)

If the install disk thingy dont work... you maybe should look for a winapp to do it..

myself im going to use Acronis disk something.. dont know the whole name..
but google on "acronis" and you'll find it in one of the top results.. :)
(not freeware)

and ive heard that partition magic will do the trick to.. not freeware eighter..

---

### Post by unexpected on 2005-10-19
Be careful with PartitionMagic! I wanted to dual-boot linux with windows, but ended up slaughtering my windows installation. Ended up having to reboot, and now i'm just booting up Ubuntu....

---

### Post by chaumurky on 2005-10-19
I meant before the Ubuntu install. There should be no problem in that case. The dual-boot part will be handled with the grub install afterwards.

---

### Post by KevRus on 2005-10-19
I've never had any problems partitioning Windows NTFS hard drives with the Ubuntu installer's partitioner, but after you select the new filesize of your Windows partition, did you click the selection that says something along the lines of "Finish and apply changed settings?"  (I have no clue what it really says, but there's a selection along those lines :-P)

After you select the size you want to make the new partition, it doesn't instantly partition, you have to go back to the main view of all of your partitions, double-check everything's the way you want it, and then select "Finish."

---

### Post by Chris Cromer on 2005-10-19
Partition magic killed my windows as well, and I had to use my system recovery disc to fix it. But it wasn't partition magic's fault, my hard drive has bad sectors in it.

In the end I decided to make a complete backup and just wipe the entire hard drive clean and reinstall windows and install ubuntu.

---

### Post by chaumurky on 2005-10-19
I'm a little confused as to how ntfs resize is done given that Ubuntu can't write data to ntfs partitions to clear the portion that is to be excised. Sector for sector writing is one thing (a la NovaStor) but defragmenting is sometihng else.

---

### Post by Chris Cromer on 2005-10-19
I read some articles on this site saying it "can" but I read some stuff in the wiki saying it "can't". So it's a toss up, can't say for sure if it can or can't based off the docs.

But from my personal experiences with the partitioner(Hoary install disc) I couldn't get it to repartition my ntfs partition.

---

### Post by TrumpetMan258 on 2005-10-19
So...any ideas as to something else I can try?

---

### Post by TrumpetMan258 on 2005-10-19
Yeah, and still nothing happens.

---

### Post by aysiu on 2005-10-19
I realize you've probably already tried this, but just in case you don't know 100% what you're doing, this tutorial may help:

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by chaumurky on 2005-10-19
>  4. you have defragged your drive

5. you know how much free space there is on your drive(right click drive, properties)

6. you have said your prayers =;)


Figured as much.

---

### Post by TrumpetMan258 on 2005-10-19
Yeah, I've already looked at that.  It makes everything really easy to understand, except that I can't seem to be able to change the size of my Windows partition.

---

### Post by darrenrxm on 2005-10-20
Partition magic 8, works perfectly for ntfs and linux partition resizing. Except you cannot have any other linux partitions except swap, ext2 or ext3 on your harddrive. If you have ReiserFS as one of your partitions it will break partition magic. Because it does not support that file system (or any other linux filesystem other than the ones mentioned.) 

Hope this helps.

---

### Post by i0h on 2005-10-20
i just resized my 200gb ntfs disk to 150gb ntfs 50gb ext3

took about 40min i think.. and it was easy :)


edit:  ooh.. with Acronis Disk Director :)

---

### Post by tormod on 2005-10-20
[QUOTE=chaumurky]I'm a little confused as to how ntfs resize is done given that Ubuntu can't write data to ntfs partitions to clear the portion that is to be excised.[/QUOTE]
The ntfs resizing is done with the program ntfsresize, which manipulates the file system in its own way. This is not the same as mounting and using the ntfs partition as an active filesystem (with the help of the kernel ntfs module).

[QUOTE=TrumpetMan258]So...any ideas as to something else I can try?[/QUOTE]
You can try the ntfsresize program from the command line. Start a shell from the installer menu, or switch console with Alt-F2. This should give you some information about why it doesn't resize.

The ntfsresize on the installer CD is a bit old. The newest version 1.12.0 (released October 8th) is included in the RIP boot CD:
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")

Tormod

---

