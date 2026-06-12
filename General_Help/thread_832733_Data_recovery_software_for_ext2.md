---
title: "Data recovery software for ext2?"
date: 2008-06-18
forum: General Help
---

### Post by bscott on 2008-06-18
This isn't necessarily Ubuntu-specific, but as a Ubuntu user I'm hoping to get some advice on recovering data from a formatted ext2 drive.  I've tried searching on these forums as well as Google but can't find anything directly relevant to my situation.

I've got a small D-Link NAS and in the process of upgrading the drives, it managed to format over the data I was trying to preserve.  It uses ext2 for a filesystem, but I'm not sure exactly what it does to "format" because the data seems to be "all but" gone...

I've hooked up the drive to my main system, which has let me access the contents in the past.  Using 'dd' from the raw device, piped through 'grep' (which represents about the limit of my command-line skills!), I can confirm that data remains on the platters - some of my important text files show up clearly.  Yet I've tried e2undel, debugfs (may have been using it wrong?), and some trialware ("Kernel Linux", among others, using my Windows box at work) and nothing shows up at all!  I think e2undel found one empty inode or something, but that's it.

When the NAS wiped the drive, it took longer than a quick-format but not as long as a full format for a drive this size, so something atypical may have been done to the data structures for all I know.

So what's my best bet for trying to recover - or even just inventory! - the files which were on this drive?  Most of them are backed up here or there, but the compilation alone represented several days' work.  And what did the NAS do to so thoroughly erase everything BUT the actual contents of the files?  Thanks in advance -

---

### Post by HalPomeranz on 2008-06-18
You may be able to use the forensic tools in The Sleuth Kit (see sleuthkit.org) to recover your data.  

First I'd try ils on the file system to see if any information remains in the inodes (probably not due to the format).  If it does, you can just use icat to recover your files.

Otherwise you're going to have to use "grep -abi" on the file system to find "strings of interest".  The "-b" argument will give you byte offsets, and you divide the byte offset by the block size for the file system (which is probably 4K, but you can figure it out running fsstat) to get the block number the string resides in.  From there, you use dcat to dump the contents of the block.  For files larger than one block, the file system will tend to have allocated the blocks sequentially, so also dump the blocks before and after your "hit" in order to recover the entire file.

There's a talk on my web site that covers the basic procedure:  [http://www.deer-run.com/~hal/IntroToDigitalForensics.pdf](http://www.deer-run.com/~hal/IntroToDigitalForensics.pdf)

---

### Post by greco8523 on 2008-06-18
You can tell if the data is completely gone by using a disk hex editor to open the partition and having a quick look if it seems to be empty then the data is definitely gone. Otherwise you can scan the drive with tools that scan the disk for file headers and footers(RAW recovery). If your data is work - text files, spreadsheets you might be able to salvage something. 

Some Linux tools that might help: 
[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

---

### Post by bscott on 2008-06-18
> **greco8523 said:**
> You can tell if the data is completely gone by using a disk hex editor to open the partition and having a quick look if it seems to be empty then the data is definitely

Thanks, as I said I used _dd | grep_ to verify that data from several large/important files is present.  I'm not sure what the NAS did, but there wasn't nearly enough time to actually do a full sector-by-sector format on a drive that size.  I'll check the link you suggested.

> **HalPomeranz said:**
> Otherwise you're going to have to use "grep -abi" on the file system to find "strings of interest".  The "-b" argument will give you byte offsets, and you divide 

That sounds good for recovering critical files, but the bulk of my stuff is backed up (in one way or another) and it's really the compilation of all the disparate groups of files that I was hoping to preserve somehow.  If I can't recover substantial amounts of the filesystem structure - which was certainly over 100,000 files at least - then it'll be better to start over.

I'll look into the Sleuth kit as well, it didn't come up in my Googling and sounds like it might be very helpful.  

Thanks to you both, and if anyone else has a suggestion I'm still interested in hearing it - I feel sure there's some recovery tool out there that will address my situation, I just need help finding it!

---

### Post by HalPomeranz on 2008-06-18
> **bscott said:**
> If I can't recover substantial amounts of the filesystem structure - which was certainly over 100,000 files at least - then it'll be better to start over.

Yeah, the Sleuth Kit isn't going to help you with that.

There are professional data recovery services that might help, but they'll want big bucks.

---

