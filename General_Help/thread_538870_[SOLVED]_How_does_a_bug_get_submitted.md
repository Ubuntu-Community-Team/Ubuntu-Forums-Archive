---
title: "[SOLVED] How does a bug get submitted?"
date: 2007-08-30
forum: General Help
---

### Post by lotuseclat79 on 2007-08-30
I posted two threads 1 wk apart two weeks ago,  So far, I have been the only respondent to either of those threads.

I am convinced that there is a bug in Fiesty Fawn's mount command, but not exhibited in Dapper Drake.

The problem seems to be that my Linux hard drive with Fedora Core 3 (FC3) which is a journaled file system (ext3), occasionally does not get the journal applied when the disk is mounted.

I am using a Fiesty knockoff known as Ultimate Ubuntu 1.4 Live CD by TheeMahn and I have also posted the problem to the Ultimate Ubuntu thread.

Here are the two threads I have posted here:
1) [http://ubuntuforums.org/showthread.php?t=521372](http://ubuntuforums.org/showthread.php?t=521372) (two weeks ago)
2) [http://ubuntuforums.org/showthread.php?p=3222634#post3222634](http://ubuntuforums.org/showthread.php?p=3222634#post3222634) (one week ago)

The intermittent incident just happened yesterday.  Immediately after the incident I threw the dmesg command.  Nothing unusual logged.  I saved an output file of the /root directory on the mounted FC3 drive with: ls -lt > lsltroot.txt.

I then booted up the Dapper Drake Live CD, and the journal was applied - no problem.  However, because the journal had not been applied previously, the file I had saved of the /root directory was absent - i.e. no journal to record it with.

After that, I presume because Dapper may have marked the drive clean, the next attempt at booting up the Ultimate Ubuntu 1.4 Fiesty Fawn Live CD worked.

When I looked again at the /root directory, the file I had saved was, of course, not there.

Between Dapper Drake>Edgy Eft>Fiesty Fawn my question is was there a change to the mount command code?

I now have a mount count of 72 without fsck being run on the FC3 hard drive, with a max-mount-count attribute of 30.  How do I know you may ask?  I ran the dumpe2fs command and saved the contents.  The drive is now marked as clean, but for some reason I suspect that I will find when I run dumpe2fs the next time the incident occurs I may find that the drive is marked dirty.  Next time I will run dumpe2fs immediately after the incident occurs to ascertain if that is the case.  Obviously, it is not now, since this AM there was no incident when I booted up with the Live CD.

It sure looks and feels like a bug to me, and I would appreciate it if someone responsible for the system code of Fiesty Fawn would register this notification as a bug against Fiesty.

Tia,

-- Tom

P.S.  Never mind - I found [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu) and submitted the bug

---

### Post by ayoli on 2007-08-30
If you need to submit a bug, do it here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

