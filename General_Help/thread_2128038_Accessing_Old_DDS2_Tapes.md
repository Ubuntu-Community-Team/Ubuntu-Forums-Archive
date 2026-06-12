---
title: "Accessing Old DDS2 Tapes"
date: 2013-03-21
forum: General Help
---

### Post by laundryday on 2013-03-21
I’m trying to access data from a set of DDS2 tapes dating from 1995-1997. I’m using a Sun Systems DDS2 drive and have been successful in reading and writing to a spare blank DDS2 tape using that drive. But I’m having trouble doing the same with the collection of older tapes. Attempts at creating disk images of the tapes has yielded files with 0 bytes and when I attempt to read any of the data on the tapes or generate a table of contents, I get a series of error messages. I’ve tried querying the tape using wildcards to stand in for file names (no idea what’s on the tapes, so can’t search for individual files) and for tar, zip and gzip formats, which were frequently used at the time the tapes were created. 
 
Here are the commands I’ve used and the errors I’ve gotten: 
 
To create the disk image: 
> problems@problems-desktop:~$ sudo dd if=/dev/st0 of=/home/problems/tape1.img
dd: reading `/dev/st0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 9.58826 s, 0.0 kB/s

 
To generate a table of contents: 
> problems@problems-desktop:~$ sudo tar -tzf /dev/st0
tar: /dev/st0: Cannot read: Input/output error
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
 
Anyone know why I might be getting these errors or any workarounds for them?

---

### Post by dcstar on 2013-03-23
> **laundryday said:**
> I’m trying to access data from a set of DDS2 tapes dating from 1995-1997. I’m using a Sun Systems DDS2 drive and have been successful in reading and writing to a spare blank DDS2 tape using that drive. But I’m having trouble doing the same with the collection of older tapes.
..........
[LIST=1]
[*]Unless you have been doing regular tape maintenance - and that means loading each tape and running it through end to end - every year or two **at most** then chances are those tapes have deteriorated beyond recovery.
[*]If the tapes were originally written on a particular drive then the head geometry of the drive you are now using may just be different enough not to be able to read very old tapes (and these are VERY old).
[*]Being able to recover magnetic media that has not been stored in optimum conditions after just a couple of years is problematic, if these 17+ year old tapes have not been stored in perfect conditions then I would be surprised that you would get any data at all off them.
[/LIST]

---

