---
title: "Read data from an unfinnished ddrescue clone?"
date: 2017-01-19
forum: General Help
---

### Post by speldosa on 2017-01-19
I found [this old (closed) thread]("https://ubuntuforums.org/showthread.php?t=1931788") where OP asked whether he could read data from an unfinished ddrescue clone. One of the answers he got was

> [COLOR=#000000]... when ddrescue makes an image it will copy bad sectors, everything, but if it doesn't complete you will have nothing, at least nothing resembling a filesystem.[/COLOR]

Is this correct? In my world (and brace yourself, I have a very limited understanding of partitions, file systems, and data storage, but I'm trying to learn), this would work fine. That is, say that you have a 100GB hard drive where you manage to copy the first 50GB. Couldn't you here just write 50GB of random data for the other half of the hard drive image, if the partition expects there to be 100GB worth of data, and then have a lot of corrupted, non-working files. Is this maybe what ddrescue does when it finnishes the whole process, and if that is the case, can you invoke it somehow after the fact? Or have I completely misunderstood how everything fits together?

---

### Post by TheFu on 2017-01-19
No - that is not correct.

ddrescue is like dd, just a little smarter.  dd is a byte-for-byte copy of an "input-file", but if something doesn't work, it crashes.  That is why ddrescue was created. It doesn't stop, it just moves onto the next sector and keeps going for the input-file (what ever that might be).

Input files can be anything that isn't a process on Unix systems.  Basically, there are 2 things on Unix - files and processes.  Everything that isn't a process, can be thought of at a very, very, very low level as a file.  That means that dd/ddrescue can read pretty much any device, directory, disk, partition, volume, keyboard, video card, whatever    and write the output somewhere else.  "Output file" can also be anything that isn't a process.

So ... whether an unfinished ddrescue can be used or not depends on how much of the bytes are copied and how large any corruption is in the output file.

At 50%, I wouldn't expect much.  At 90%, I would.  Also, if the ddrescue is still running when you try to access the storage, that can add to corruption.  Hopefully, you used a log file and ddrescue will pick up where you left off if the log file is provided as an input.

If you want any more details - **man ddrescue**. There are manpages for pretty much every Unix command.

---

### Post by speldosa on 2017-01-20
Thanks for your answer! 

It seems like we're not really saying different things (I might have been a bit unclear regarding what I mean).

Basically (let's see if this question is clearer), let's say that you've managed to clone 50% (or 90% or 99.9999%) of the drive with no errors but you **KNOW** that the rest of the drive is totally unreadable (let's say that God has told you that this is the case). In this case, would there be any benefit in letting ddrescue finish? From the quoted answer, it seems like ddrescue does something extra to the output drive once it finishes.

---

