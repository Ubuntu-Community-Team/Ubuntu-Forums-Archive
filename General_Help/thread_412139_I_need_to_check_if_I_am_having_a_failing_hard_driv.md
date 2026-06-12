---
title: "I need to check if I am having a failing hard drive.."
date: 2007-04-17
forum: General Help
---

### Post by billdotson on 2007-04-17
I have been dual booting Windows.. I used gparted to make partitions first and left the first 108GiB unallocated for the Windows XP install CD to format as NTFS.  In Windows whenever I runchkdsk I get a misallocation error with the MFT.  Chkdsk will not repair it no matter what.

What should I use to check to see if my hard drive is failing?? I downloaded Seagates Seatools and chkdsk returned no bad blocks but I do not know what I should use to check for a failing hard drive.

Also, if my hard drive is not failing I need some assistance as how to setup partitions before installing Windows.  Should I install Windows first and partition w/ the Windows installer CD partitioner and then format the unallocated as ext3 or another filesystem or should I make the partitions first and leave 100GB of unallocated space at the beginning on the drive for Windows to format when it is installing??

What partitioner should I use?? I know gparted is on the LiveCD (ubuntu) but I don't know if it is reliable.  I am thinking about wiping my drive because I think I might have a partition table error.

Any help would be greatly appreciated!

Thanks.

---

### Post by Sef on 2007-04-17
Your problem seems to be software and not hardware.  MFT = Master File Table, so it seems that has gone bad.

Here's a couple of links that may help you resolve your problem, if you don't want to reinstall Windows:

[Link 1]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/99609816/m/5260931565")

[Link 2]("http://discussions.virtualdr.com/archive/index.php/t-150922.html")

---

### Post by billdotson on 2007-04-17
I ran chkdsk /v and it said the following:

chkdsk detected minor inconsistencies on the drive.. this is not a corruption.
chkdsk is verifying securtiy descriptors...
Cleaning up 1 unused index entires from index $SII from file 9
Cleaning up 1 unused index entires from index $SDH from file 9
Cleaning up 1 unused security descriptor.

I have reinstalled twice and each time I install when I boot into Windows I run chkdsk before I install ANYTHING.  I do not get the error then.  When I install all of my games and other apps I then get the error.  Although I have not seen a large drop (or any drop at all as far as I can tell)  in the amount of available free space.

I have tried the recovery console and running chkdsk.

It says the volume appears to be clean.. not checked

Then if I do chkdsk /p it says "Found one or more erros with the filesystem"

If I run chkdsk /r it says it fixed them but when I boot back into Windows it does not.

I schduled a chkdsk by going to my computer> C:. properties> scan for errors and ticking automatially fix errors on the filesystem and try to repait and recover bad blocks.

When that runs on bootup it says it fixes the errors sometimes and others it doesn't say anything about errors.

I try to un sfc/ scannow but when I put my XP SP2 disc in it won't find it.  I am using a Volume License Key version installer CD.

I am trying the thing w/ the pagefile but you cannot set it any lower than 2.. :|

this is really odd.. security descriptors and indexes getting deleted when running chkdsk /v... hmm

I ran chkdsk /v again and I got the same message except this time it says 7 instead of 1 in removing entries

Maybe I partitioned my drive wrong w/ gparted??

I guess this should be moved to the Other OS> Windows discussions.. too bad.. this thread will probably disappear into nothingness when that happens  :(

---

