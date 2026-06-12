---
title: "dd / erasing a disk"
date: 2007-11-14
forum: General Help
---

### Post by Dave / Mosaic on 2007-11-14
Last night, I typed

dd if=/dev/urandom of=/dev/sdb

to erase a 100 gigabyte, 7200 RPM disk before returning it to where I bought it from.  At once the disk started churrying merrily along, it's activity indicator LED blinking in furious activity.  From posts on here, I figured the whole operation might take around an hour or two to complete; this is a 1.86 GHz laptop, and the disk being filled with garbage is connected by way of an external USB drive enclosure.

This morning, though, it was still going...

And it's still going now...

Does anybody have an idea how long this should take?  I wonder if it's almost done, or if I've done something that's going to take like 200 years...  maybe I should stop it and do something else??

thanks--

--dave

---

### Post by TidusBlade on 2007-11-14
Depending, if it got billions of 100 byte files, it will take almost forever, if it isint too many files, I suggest reformatting the disk, usually quicker and better ;)

---

### Post by Dave / Mosaic on 2007-11-14
Thanks for the quick reply...

But, I think that isn't right, is it?  The partitions aren't even mounted, and the OS has no notion of the filesystems in this case...  The output to the raw device is just overwriting the entire disk, including the partition table.

?

--dave

---

### Post by TidusBlade on 2007-11-14
You mentioned you were returning it, so I thought why not reformat it, I think, for example it's NTFS, you reformat it as NTFS, it will be like brand new, Ive never experienced problems with that, but Im not too experienced in partitions...

---

### Post by Dave / Mosaic on 2007-11-14
Actually, according to my understanding, anyway, that isn't correct.  Reformatting just goes and (approximately)  marks everything as unallocated; it doesn't actually erase most of the actual data, which somebody could recover if they wanted to...

---

### Post by TidusBlade on 2007-11-14
I think you can then just create an NTFS partition right? 
Wouldn't that be very close to how you bought it?

---

### Post by Dave / Mosaic on 2007-11-14
No,,,

It would show up as all empty, but if you went in with a disk editor, it wouldn't be all zeros - it would mostly all be the contents of the files that were there before.

Kind of like how if you delete a file, it doesn't actually erase it.  Formatting a disk just marks it all as unused / unallocated, but the actual data is still there.

---

### Post by TidusBlade on 2007-11-14
Oh.... Well, thats new information :P In that case, I would probably use the command line to delete the files, since it shows whats going on?

---

### Post by Dave / Mosaic on 2007-11-14
No...  none of that actually overwrites the data on the disk; not deleting files, not partitioning, not formatting.  It's kind of a standard thing you can read about in these forums, writing over the whole disk with data from /dev/urandom; just, it's taking a lot longer than I would have expected...

---

### Post by bingoUV on 2007-11-14
you are right dave, it is safer to overwrite the disk.  But is the drive really 100 megabyte, or is it 100 gigabyte?

Can you try overwriting the individual partitions and see if they finish any sooner? You can abort (ctrl-c) the dd in a minute to see what is the speed it is getting so far.

---

### Post by Dave / Mosaic on 2007-11-14
ACK! - you're right, I meant 100 GB... I just corrected above.

Anyway, the partition table is long gone by now, but that would have been a fun idea to try a small partition first...

So, dd will print out some kind of status report when it exits?  I've never actually used dd before...

I think I'll go get supper, and see what it's up to after that, maybe it will finish...

BTW, the processor seems to be working pretty hard, generating the pseudorandom data...  I guess it's a lot of work...

---

### Post by Dave / Mosaic on 2007-11-14
This is exactly the kind of reason, why I'm in the process of building a fully encrypted system on the new disk that is replacing the old one...

---

### Post by Dave / Mosaic on 2007-11-14
Kind of like Waiting for Godot...

---

### Post by rscott5 on 2007-11-14
I would suggest trying this command:
```
sudo shred /dev/sdb
```

Shred usually works pretty quickly for me, it would definitely finish if running overnight (at least in my experience).

---

### Post by trobbins on 2007-11-14
I used DD to copy the entire contents of a 420 gig disk to a 500 gig disk.  This process took about 9 hours (I used 512 byte block size).  You didn't specify block size so dd should have defaulted to 512 bytes.  This will cause DD to read and write many more times to move the same data than if you were to have used a large block size.  Try using a block size of 16 megabytes or larger.

Also, check out dcfldd.  It's pretty much an exact dd replacement but provides verbose status of the operation.

---

### Post by Dave / Mosaic on 2007-11-14
Hey, thanks - dcfldd...  good info there...

I hadn't thought about block size,,,

However, by the looks of things (processor maxed out; Drive LED light blinking (albeit so rapidly you can't tell except by scanning your eyes past it really fast) continuously between green=idle and red=active) it seems that the slow part of the pipeline is the generation of the data by /dev/urandom, at least on my 1.86 GHz laptop.

--dave

---

### Post by trobbins on 2007-11-14
I don't know how secure you really want to be, but one could just write a bunch of 0's to the disk with if=/dev/zero .  Writing random data was taking a rate of 5MB/s.  When I wrote 0's it was writing as fast as my drive could store data ~65MB/s

I've zeroed my 500 gig drive four or 5 times in an hour while playing with parition tables one day.  It's very quick.

---

### Post by Chappy7777 on 2007-11-14
I have a little program called Dban that I use to clean off HDDs either before doing a fresh install, or just to get them empty. This program is billed as being used by gov't agencies to wipe off HDDs.

Go to sourceforge.com and do a search for Dban. BTW, D B a N  stands for Dukes Blast and Nuke. It works, and on my 80Gig HD took about an hour to do the "quick clean".

This will empty your HDD of everything, and it will be formatted and ready for use when you are done. It's a small fine (I keep my copy on a 3.5" floppy.

---

### Post by Dave / Mosaic on 2007-11-14
Well, I left it alone, and it finally got around to finishing up on its own after all...

Thanks everybody for the suggestions.

Writing random data was more or less a waste of time in this case; I bet that's right about zeros would have been a lot faster, and just as well for my purposes here.

In case it's useful to anybody later on, this is the data rate I got on this machine, a small laptop with a 1.86 GHz Pentium M:

```
Z3300Ae:~$ sudo dd if=/dev/urandom of=/dev/sdb
dd: writing to `/dev/sdb': No space left on device
195371569+0 records in
195371568+0 records out
100030242816 bytes (100 GB) copied, 46177.8 seconds, 2.2 MB/s
Z3300Ae:~$ 

```

--dave

---

