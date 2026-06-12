---
title: "rsync not trnsfering files"
date: 2008-07-05
forum: General Help
---

### Post by badgandalf on 2008-07-05
Still a newby in the Linux world I took the challenge to build a Xubuntu based file server to backup my home network PCs. I opted for rsync as a starter but there has to be something I'm doing wrong because when I try to run the backup in the console using:

*sudo rsync --delete -avv -e ssh /media/sda4/Images/ ignacio@192.168.1.36:./Backup/Images/*

I get:

[I]opening connection using ssh -l ignacio 192.168.1.36 rsync --server -vvlogDtpr --delete . "./Backup/Images Database/"
ignacio@192.168.1.36's password:
building file list ...
done[/I]

..and nothing more. The console stays there for hours and the only change I see on the file server is a copy of the file structure I'm backing up, but without any of the files.

can anyone give a light to resolve the problem? Thnx a lot,

Ignacio
More info that might help you help me...

I 've been running a thousand tests and everything seems to work ok in some cases (perfect backup) but not in others (stuck as described above). So far i do not have a clue as to what might cause it to work with certain directories/files but not with others.

---

### Post by HalPomeranz on 2008-07-06
That command looks correct to me, although you could simplify it a bit:

```

rsync -avv --delete /media/sda4/Images/ ignacio@192.168.1.36:Backup/Images/

```

"-e ssh" is the default and you don't need the "./" at the front of the remote path name.

Anyway, the real question is why the rsync isn't working.  Are both machines in this scenario running Xubuntu, or are there other operating systems in the mix?

Here are some tests I'd run to try and isolate the problem:

1) What happens when you do "ssh ignacio@192.168.1.36 df -h"?

2) Can you "scp /media/sda4/Images/<somefilename> ignacio@192.168.1.36:Backup/Images/" (you'll need to replace <somefilename> with the name of a file under /media/sda4/Images)?

You'll want to run the above commands on the same host you've been trying to back up with rsync.

---

### Post by badgandalf on 2008-07-13
Sorry for the late response. I'm travelling most of the week. I tried your proposals with following result:

1) ssh ignacio@192.168.1.36 df -h
[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.5G  1.8G  4.4G  29% /
varrun                474M  236K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   52K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6              21G  7.7G   12G  40% /home
[/I]

2) scp /media/sda4/Images?Database/Images?Database.i3f ignacio@192.168.1.36:

It copies the file correctly

Rgds,
Ignacio

---

### Post by HalPomeranz on 2008-07-13
> **badgandalf said:**
> 
I 've been running a thousand tests and everything seems to work ok in some cases (perfect backup) but not in others (stuck as described above). So far i do not have a clue as to what might cause it to work with certain directories/files but not with others.

Does it always lock up on the same directories, or does it get stuck on different directories during different tests?

Definitely a weird problem, though.

---

### Post by badgandalf on 2008-07-15
Same directory. Always. Ignacio

---

### Post by HalPomeranz on 2008-07-15
> **badgandalf said:**
> Same directory. Always.

That would imply to me that there's some issue with the directory that's causing your problem.  Perhaps there are strange characters embedded in the directory name or the file names in it?  If you do an "ls -lR" on the directory, any non-printable characters in the file names should show up as question marks ("?") in the output.

---

### Post by badgandalf on 2008-07-19
This is the output:
5805.jpg  5816.jpg  5827.jpg  5838.jpg  5849.jpg  5860.jpg  5871.jpg  5882.jpg
5806.jpg  5817.jpg  5828.jpg  5839.jpg  5850.jpg  5861.jpg  5872.jpg  5883.jpg
5807.jpg  5818.jpg  5829.jpg  5840.jpg  5851.jpg  5862.jpg  5873.jpg  5884.jpg
5808.jpg  5819.jpg  5830.jpg  5841.jpg  5852.jpg  5863.jpg  5874.jpg  5885.jpg
5809.jpg  5820.jpg  5831.jpg  5842.jpg  5853.jpg  5864.jpg  5875.jpg  5886.jpg
5810.jpg  5821.jpg  5832.jpg  5843.jpg  5854.jpg  5865.jpg  5876.jpg  5887.jpg
5811.jpg  5822.jpg  5833.jpg  5844.jpg  5855.jpg  5866.jpg  5877.jpg  5888.jpg
5812.jpg  5823.jpg  5834.jpg  5845.jpg  5856.jpg  5867.jpg  5878.jpg  5889.jpg
5813.jpg  5824.jpg  5835.jpg  5846.jpg  5857.jpg  5868.jpg  5879.jpg  5890.jpg
5814.jpg  5825.jpg  5836.jpg  5847.jpg  5858.jpg  5869.jpg  5880.jpg  5891.jpg
5815.jpg  5826.jpg  5837.jpg  5848.jpg  5859.jpg  5870.jpg  5881.jpg

Could this be the cause of the problems?

Also, I've tried deleting some files and with lower number of files, everything seems to work ok. Is there a limitation in the number of files it can transfer?

Ignacio

---

### Post by HalPomeranz on 2008-07-19
> **badgandalf said:**
> This is the output:


Hmmm, that didn't look like the output of "ls -lR".  I didn't see anything funny with the file names, but I would like to see the output for the directory entry.

> **badgandalf said:**
> 
Also, I've tried deleting some files and with lower number of files, everything seems to work ok. Is there a limitation in the number of files it can transfer?


That's interesting.  I've never encountered a limit like that before, and I've transferred very large directories with rsync.

It would be interesting to watch the program failing using a tool like strace to monitor what's happening.

---

### Post by badgandalf on 2008-07-19
Full output (if this is what you meant, I'm not sure):

ignacio@atico:/media/sda4/Images Database/58$ ls -IR
5805.jpg  5816.jpg  5827.jpg  5838.jpg  5849.jpg  5860.jpg  5871.jpg  5882.jpg
5806.jpg  5817.jpg  5828.jpg  5839.jpg  5850.jpg  5861.jpg  5872.jpg  5883.jpg
5807.jpg  5818.jpg  5829.jpg  5840.jpg  5851.jpg  5862.jpg  5873.jpg  5884.jpg
5808.jpg  5819.jpg  5830.jpg  5841.jpg  5852.jpg  5863.jpg  5874.jpg  5885.jpg
5809.jpg  5820.jpg  5831.jpg  5842.jpg  5853.jpg  5864.jpg  5875.jpg  5886.jpg
5810.jpg  5821.jpg  5832.jpg  5843.jpg  5854.jpg  5865.jpg  5876.jpg  5887.jpg
5811.jpg  5822.jpg  5833.jpg  5844.jpg  5855.jpg  5866.jpg  5877.jpg  5888.jpg
5812.jpg  5823.jpg  5834.jpg  5845.jpg  5856.jpg  5867.jpg  5878.jpg  5889.jpg
5813.jpg  5824.jpg  5835.jpg  5846.jpg  5857.jpg  5868.jpg  5879.jpg  5890.jpg
5814.jpg  5825.jpg  5836.jpg  5847.jpg  5858.jpg  5869.jpg  5880.jpg  5891.jpg
5815.jpg  5826.jpg  5837.jpg  5848.jpg  5859.jpg  5870.jpg  5881.jpg
ignacio@atico:/media/sda4/Images Database/58$

...and...how do i use that tool you refer to?

Ignacio

---

### Post by HalPomeranz on 2008-07-20
> **badgandalf said:**
> Full output (if this is what you meant, I'm not sure):

ignacio@atico:/media/sda4/Images Database/58$ ls -IR


I wanted "ls -lR" (ls minus el ar), not "ls -IR" (ls minus eye ar).  But it's not that important.

> **badgandalf said:**
> ...and...how do i use that tool you refer to?

strace is pretty easy to use, but it generates a ton of output.  Basically you'll want to use your rsync command line as normal, but put the word "strace" in front and some commands to capture the output at the end:

```

strace rsync ... >/tmp/OUTPUT 2>&1

```

In place of the "..." put your normal rsync arguments that you have been using all along.  The file /tmp/OUTPUT will end up being really large, but you can attach it to the thread.

---

### Post by badgandalf on 2008-07-20
Ok. Let's see what we gat from the right commands:

ls -lR

[I]ignacio@atico:/media/sda4/Images Database/58$ ls -lR
.:
total 1620
-rwxrwx--- 1 root plugdev  7539 2007-12-06 18:39 5805.jpg
-rwxrwx--- 1 root plugdev  7656 2007-12-06 18:39 5806.jpg
-rwxrwx--- 1 root plugdev  9066 2007-12-06 18:39 5807.jpg
-rwxrwx--- 1 root plugdev  9160 2007-12-06 18:39 5808.jpg
-rwxrwx--- 1 root plugdev 11357 2007-12-06 18:39 5809.jpg
-rwxrwx--- 1 root plugdev 11743 2007-12-06 18:39 5810.jpg
-rwxrwx--- 1 root plugdev  9989 2007-12-06 18:39 5811.jpg
-rwxrwx--- 1 root plugdev  9850 2007-12-06 18:39 5812.jpg
-rwxrwx--- 1 root plugdev  9742 2007-12-06 18:39 5813.jpg
-rwxrwx--- 1 root plugdev  8052 2007-12-06 18:39 5814.jpg
-rwxrwx--- 1 root plugdev 10869 2007-12-06 18:39 5815.jpg
-rwxrwx--- 1 root plugdev 16555 2007-12-06 18:39 5816.jpg
-rwxrwx--- 1 root plugdev  9070 2007-12-06 18:39 5817.jpg
-rwxrwx--- 1 root plugdev  9643 2007-12-06 18:39 5818.jpg
-rwxrwx--- 1 root plugdev  8513 2007-12-06 18:39 5819.jpg
-rwxrwx--- 1 root plugdev  9379 2007-12-06 18:39 5820.jpg
-rwxrwx--- 1 root plugdev  9918 2007-12-06 18:40 5821.jpg
-rwxrwx--- 1 root plugdev  9804 2007-12-06 18:40 5822.jpg
-rwxrwx--- 1 root plugdev 10314 2007-12-06 18:40 5823.jpg
-rwxrwx--- 1 root plugdev  7599 2007-12-06 18:40 5824.jpg
-rwxrwx--- 1 root plugdev 16226 2007-12-06 18:40 5825.jpg
-rwxrwx--- 1 root plugdev 16081 2007-12-06 18:40 5826.jpg
-rwxrwx--- 1 root plugdev 16399 2007-12-06 18:40 5827.jpg
-rwxrwx--- 1 root plugdev 15174 2007-12-06 18:40 5828.jpg
-rwxrwx--- 1 root plugdev 25795 2007-12-06 18:40 5829.jpg
-rwxrwx--- 1 root plugdev 25694 2007-12-06 18:40 5830.jpg
-rwxrwx--- 1 root plugdev 25576 2007-12-06 18:40 5831.jpg
-rwxrwx--- 1 root plugdev 25890 2007-12-06 18:40 5832.jpg
-rwxrwx--- 1 root plugdev 24659 2007-12-06 18:40 5833.jpg
-rwxrwx--- 1 root plugdev 34545 2007-12-06 18:40 5834.jpg
-rwxrwx--- 1 root plugdev 15750 2007-12-06 18:45 5835.jpg
-rwxrwx--- 1 root plugdev 21811 2007-12-06 18:46 5836.jpg
-rwxrwx--- 1 root plugdev 24575 2007-12-06 18:46 5837.jpg
-rwxrwx--- 1 root plugdev 16516 2007-12-06 18:46 5838.jpg
-rwxrwx--- 1 root plugdev 27744 2007-12-06 18:46 5839.jpg
-rwxrwx--- 1 root plugdev 15123 2007-12-06 18:46 5840.jpg
-rwxrwx--- 1 root plugdev 21383 2007-12-06 18:46 5841.jpg
-rwxrwx--- 1 root plugdev 16837 2007-12-06 18:46 5842.jpg
-rwxrwx--- 1 root plugdev 13168 2007-12-06 18:46 5843.jpg
-rwxrwx--- 1 root plugdev 16560 2007-12-06 18:46 5844.jpg
-rwxrwx--- 1 root plugdev 17592 2007-12-06 18:46 5845.jpg
-rwxrwx--- 1 root plugdev 16130 2007-12-06 18:46 5846.jpg
-rwxrwx--- 1 root plugdev 16881 2007-12-06 18:46 5847.jpg
-rwxrwx--- 1 root plugdev 19725 2007-12-06 18:46 5848.jpg
-rwxrwx--- 1 root plugdev 18033 2007-12-06 18:47 5849.jpg
-rwxrwx--- 1 root plugdev 14205 2007-12-06 18:47 5850.jpg
-rwxrwx--- 1 root plugdev 18362 2007-12-06 18:47 5851.jpg
-rwxrwx--- 1 root plugdev 17677 2007-12-06 18:47 5852.jpg
-rwxrwx--- 1 root plugdev 15120 2007-12-06 18:47 5853.jpg
-rwxrwx--- 1 root plugdev 15956 2007-12-06 18:47 5854.jpg
-rwxrwx--- 1 root plugdev 18432 2007-12-06 18:47 5855.jpg
-rwxrwx--- 1 root plugdev 16210 2007-12-06 18:47 5856.jpg
-rwxrwx--- 1 root plugdev 17635 2007-12-06 18:48 5857.jpg
-rwxrwx--- 1 root plugdev 10952 2007-12-06 18:48 5858.jpg
-rwxrwx--- 1 root plugdev 15600 2007-12-06 18:48 5859.jpg
-rwxrwx--- 1 root plugdev 16213 2007-12-06 18:48 5860.jpg
-rwxrwx--- 1 root plugdev 19288 2007-12-06 18:48 5861.jpg
-rwxrwx--- 1 root plugdev 12982 2007-12-06 18:48 5862.jpg
-rwxrwx--- 1 root plugdev 21879 2007-12-06 18:48 5863.jpg
-rwxrwx--- 1 root plugdev 22240 2007-12-06 18:49 5864.jpg
-rwxrwx--- 1 root plugdev 16807 2007-12-06 18:49 5865.jpg
-rwxrwx--- 1 root plugdev 16516 2007-12-06 18:49 5866.jpg
-rwxrwx--- 1 root plugdev 16081 2007-12-06 18:49 5867.jpg
-rwxrwx--- 1 root plugdev 17675 2007-12-06 18:49 5868.jpg
-rwxrwx--- 1 root plugdev 17111 2007-12-06 18:49 5869.jpg
-rwxrwx--- 1 root plugdev 32116 2007-12-06 18:49 5870.jpg
-rwxrwx--- 1 root plugdev 33373 2007-12-06 18:49 5871.jpg
-rwxrwx--- 1 root plugdev 19142 2007-12-06 19:16 5872.jpg
-rwxrwx--- 1 root plugdev 15984 2007-12-06 19:16 5873.jpg
-rwxrwx--- 1 root plugdev 14910 2007-12-06 19:17 5874.jpg
-rwxrwx--- 1 root plugdev 15109 2007-12-06 19:17 5875.jpg
-rwxrwx--- 1 root plugdev 13564 2007-12-06 19:17 5876.jpg
-rwxrwx--- 1 root plugdev 15690 2007-12-06 19:17 5877.jpg
-rwxrwx--- 1 root plugdev 17052 2007-12-06 19:17 5878.jpg
-rwxrwx--- 1 root plugdev 17228 2007-12-06 19:17 5879.jpg
-rwxrwx--- 1 root plugdev 16487 2007-12-06 19:17 5880.jpg
-rwxrwx--- 1 root plugdev 16561 2007-12-06 19:17 5881.jpg
-rwxrwx--- 1 root plugdev 13655 2007-12-06 19:17 5882.jpg
-rwxrwx--- 1 root plugdev 17891 2007-12-06 19:17 5883.jpg
-rwxrwx--- 1 root plugdev 21756 2007-12-06 19:17 5884.jpg
-rwxrwx--- 1 root plugdev 11098 2007-12-06 19:17 5885.jpg
-rwxrwx--- 1 root plugdev 20525 2007-12-06 19:17 5886.jpg
-rwxrwx--- 1 root plugdev 22317 2007-12-06 19:17 5887.jpg
-rwxrwx--- 1 root plugdev 16518 2007-12-06 19:17 5888.jpg
-rwxrwx--- 1 root plugdev 16791 2007-12-06 19:17 5889.jpg
-rwxrwx--- 1 root plugdev 28793 2007-12-06 19:17 5890.jpg
-rwxrwx--- 1 root plugdev 30223 2007-12-06 19:17 5891.jpg
[/I]

strace..

see attached OUTPUT.txt

After several minutes waiting, I stopped it with Ctrl-C

Rgds,

Ignacio
[/I]

---

### Post by HalPomeranz on 2008-07-21
Well looking at the strace output I see the rsync program successfully get the list of files out of the directory, cd into the directory, and send the first part of file 5824.jpg.  Then it looks like it's waiting for an acknowledgement from the other end which never comes.

The first thing would be to check if there's something hinky with the 5824.jpg file.  If you remove this file from the directory and then try the rsync, what happens?

---

### Post by badgandalf on 2008-07-21
Same result. Ignacio

---

### Post by HalPomeranz on 2008-07-21
This is such an odd problem.

The next thing I would do if I were debugging this would be to use something like tcpdump or wireshark at each end to see what's happening on the network.  From the strace output it looks like the host that's sending the files is waiting for something back from the remote machine and not getting it.  So the question is when the sending machine sends a packet, is it being received by the remote system?  If it is seen on the remote side, is the remote system sending anything back in response to the packet?  Is that response making it back to the original sending system?  Those are the sorts of questions I'd be trying to answer.

But truthfully I'm stumped as to what's going on here.

---

### Post by badgandalf on 2008-07-22
I'll be travelling a couple of days but will then come back with new tests to see if I can bring more info...Thnx sicerely,

Ignacio

---

