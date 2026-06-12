---
title: "FSCK Woes: -everything- moved to Lost+Found"
date: 2007-11-17
forum: General Help
---

### Post by Gnu32 on 2007-11-17
Egads.

I had a ubuntu setup on a USB external drive, split into three partitions, A data warehouse + Ubuntu + 3GB of Swap.

I've been trying to experiment with Second Life and the 3D graphics on this laptop, so I decided to shrink the 13GB ubuntu partition i had to 10 GB, shrink the swap to 2 and make a partition for Windows (I used a special USB installable version for that).

I used Paragon Partition Manager to do the assumingly non-destructive partition resizing and moving. My first partition, 130 gigs of storage in FAT32 format, didn't have anything done to it so it was fine. Next, the ubuntu partition was resized to 10GB and no errors reported. The swap partition was moved and then shrunk, no errors reported too.

So everything seems to be hunky dory, so I boot into it. Because of the modifications, a FSCK check had been forced, but then stopped and told me to run it manually, so I go into maintanence mode and do so. I knew I probably should not have done what I did next: Inode problem after inode problem. It kept asking me to press Y or N on these following types of problems (if i can remember correctly):
Inode 0 has incorrect position. Correct? Y/N

I held Y for all these prompts for about 5 minutes until all was done. After a reboot, I couldn't boot into it! GRUB was having problems.

So I investigated the drive, to find that **everything** in the ubuntu partition had been moved into this folder called lost+found in these weird #XXXXX filenames.

I've done all these searches into threads and pages on the net, and all I could find out was that this is where FSCK puts mis-placed files. Are there not any solutions to recover those files at all? I spent quite a while on this system D:

---

### Post by Herman on 2007-11-18
Yes, as it happens I was just looking into that this weekend.

Another Web Forum member, by co-incidence, sent me a P.M. containing some links I posted a long time ago and afterwards lost, with some info on recovering files from /lost+found.. 
So now is my chance to pass them on! :)

Here is the best link I have been able to find on this subject so far, 
[SIZE=-1]
[www.oreilly.com/catalog/morelnxsvrhks/chapter/hack  96.pdf]("http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf") - [Similar pages]("http://www.google.com.au/search?hl=en&q=related:www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf")

[/SIZE] Here are some more links on /lost+found, as well,
[http://www.tldp.org/LDP/Linux-Filesy...lostfound.html]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

[http://www.sunmanagers.org/pipermail...er/005866.html]("http://www.sunmanagers.org/pipermail/summaries/2004-November/005866.html")

[http://archives.free.net.ph/message/...c72f03.en.html]("http://archives.free.net.ph/message/20050811.104345.e1c72f03.en.html")

[http://ubuntuforums.org/archive/index.php/t-229143.html](http://ubuntuforums.org/archive/index.php/t-229143.html)

Any feedback on how you get along would be much appreciated. It isn't every day something like this happens, so good information on this subject seems to be hard to find.

Regards, Herman :)

---

### Post by Dusal on 2008-05-20
I just found this:

[http://www.linuxforums.org/forum/suse-linux-help/118214-solved-saving-data-broken-opensuse-partition.html](http://www.linuxforums.org/forum/suse-linux-help/118214-solved-saving-data-broken-opensuse-partition.html)

---

