---
title: "I overloaded my Hard Drive using rsync now I can't locate the files..."
date: 2016-09-12
forum: General Help
---

### Post by Cacique on 2016-09-12
Last night I copied some files from my USB drive to my internal hard drive on Ubuntu 16.04.1 and without first checking the size of the source directory it turned it to be way too large for my internal hard drive.   

I got a warning message that the Hard Drive was out of space so I hit CTRL-C on the rsync process to stop it.   

This morning I went into the destination directory and deleted all the files and directories that were visible in the destination directory.   However, my computer still reports that I only freed up 10GB of space by doing so, and my hard drive is still 98% (approximately) full.   

I'm not sure where all the files were copied to.  I assume to the destination directory, but cleaning out that directory still leaves me with a nearly full hard drive.   

I'm a little perplexed by this; can anyone shed some light as to what filled up my hard drive and where those files are?

Thanks.

---

### Post by Cacique on 2016-09-12
My apologies, I located the files but they were not from rsync.   I just had a bunch of files buried about 5 sub-directories deep that I had forgotten were there.   They were using my diskspace.   I was able to locate them using the ncdu utility.   Please feel free to delete this thread as the answer and the question are not really congruent.

---

### Post by Bashing-om on 2016-09-12
Cacique; Ha ha ...

Erra We  have all been there and done that .. Glad you owned up to it .

It is on you too to mark this thread solved :
drop down in the thread tools menu :

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]onward and upward
[/INDENT][/INDENT]

---

