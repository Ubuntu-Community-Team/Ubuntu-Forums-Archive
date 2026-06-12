---
title: "LILO boot problem"
date: 2015-04-04
forum: General Help
---

### Post by ilos.venizel on 2015-04-04
I already posted a question regarding this problem, but apparently, the question was actually consisting of two, and I decided to make a thread about the more serious problem.
I've installed a minimalistic version of Ubuntu, following the instructions on this website: [http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)
It installed successfully, and I was presented with a bare-bones terminal, what I semi-expected. However, I can't seem to boot to Windows 7, an OS I had installed before Ubuntu.
Don't really know what happened, I looked it up on several places and found nothing particularly useful. Something about partitions, installing Ubuntu partitions on the same location where the ones of Windows 7 were and unintentionally disabling/overwriting them, stuff like that. LILO is the installed booting assistant for Ubuntu, by the way.
Can anyone help on this? It's most definitely appreciated.
Also, I am not able to install packages. Entering "lshw" on the terminal outputs that the network is DISABLED. This is strange, considering that the Internet was available during the installation of the Ubuntu OS.

---

### Post by Vladlenin5000 on 2015-04-04
Th guide you linked assumes no other OS is present and, accordingly, tells you to use the entire disk option, thus overwriting any previous Windows partitions.

---

### Post by ilos.venizel on 2015-04-04
> The guide you linked assumes no other OS is present and,  accordingly, tells you to use the entire disk option, thus overwriting  any previous Windows partitions.
-subtle face palm-
So, is the data lost forever? Does the installation using the entire disk option overwrite just the working, main directory (C: , in this case) or all existing directories? (In this case, both C: and D: directories) Is there any hope for rescuing something?

---

### Post by Vladlenin5000 on 2015-04-04
Entire means what it means, the entire physical disk regardless of what or how many partitions were there...

There are several tool that attempt to recover deleted files/partitions but I'm not in a position to recommend one or another. What I can recommend is stop using that disk immediately because the more you use it the less your chances will be.

---

### Post by yancek on 2015-04-04
Testdisk works pretty well in many cases.  I've never had to use it myself so...?  Take a look at the link below, their home page with a download link and scroll down the page to the Step By Step instructions and read through that to see if you understand before trying it.

  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2015-04-04
Another part of testdisk is photorec.
If testdisk shows files & lets you recover some that is best.
If you have to use photorec it just scans drive for anything that looks like a file, takes a long time, requires another drive with lots of room as it has to copy data somewhere. When I ran it on a smallish drive I had to let it run overnight. And some of my text files that I save a lot, it also found the old deleted copies. I had to compare many files to an older backup to try to restore file. It only finds files by extension, so I first had to figure out which text file was which. Ended up taking weeks.
Or always best to keep backups current. 

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Some Windows users also suggest this:
      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by ilos.venizel on 2015-04-05
I can't download any packages or programs via Ubuntu at this point, because the network seems to be disabled. Whenever I try: > sudo apt-get install something I get a bunch of errors about failing to resolve a link and failing to fetch something. Entering "testdisk" on the terminal informs me that there is an installation available for a it, but for the reasons mentioned above I can't get it.
The other option was using external memory, but whenever I insert the USB, the terminal gives the following output:
> [sdb] No Caching mode found
[sdb] Assuming drive cache: write through
Why does everything have to be so cryptic? Can't say that I understood what the terminal was trying to make me aware of. So, in order to fix this problem about partition recovery, one of the two other problems have to be solved:
- How to enable network
- How to enable Caching mode

---

### Post by oldfred on 2015-04-05
Are you trying to use the install on hard drive? If so every little bit you do overwrites more of your data. Ubuntu is not large, but ext4 rewrites every file if changed to a new location.

You need to boot installer DVD or flash drive in live mode and use that.

---

