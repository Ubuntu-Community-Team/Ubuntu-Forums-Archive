---
title: "Differences in reported file size, disk usage"
date: 2013-02-16
forum: General Help
---

### Post by dazz100 on 2013-02-16
Hi
I am trying to write a script that will delete old files based on the size and age of the directories that contain them.  I want to be able to get accurate info on the space used by the directories.

When I use the commands:
ls -l and,
df

the sizes of the directories don't match the added total of the file sizes.  Why is that????

Below is output of the above commands.

```
dazz@alpha:~$ ls -l /var/images/trackcam1
total 1432
-rw-r--r-- 1 motion motion 71021 Feb 16 09:25 20130216-092448-1-snapshot.jpg
-rw-r--r-- 1 motion motion 71452 Feb 16 09:26 20130216-092548-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76268 Feb 16 09:27 20130216-092648-1-snapshot.jpg
-rw-r--r-- 1 motion motion 75436 Feb 16 09:28 20130216-092748-1-snapshot.jpg
-rw-r--r-- 1 motion motion 75861 Feb 16 09:28 20130216-092818-1-motion-00.jpg
-rw-r--r-- 1 motion motion 76205 Feb 16 09:29 20130216-092848-1-motion-00.jpg
-rw-r--r-- 1 motion motion 76205 Feb 16 09:29 20130216-092848-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76588 Feb 16 09:30 20130216-092948-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76684 Feb 16 09:31 20130216-093048-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76498 Feb 16 09:32 20130216-093148-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76439 Feb 16 09:33 20130216-093248-1-snapshot.jpg
-rw-r--r-- 1 motion motion 77193 Feb 16 09:34 20130216-093348-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76847 Feb 16 09:35 20130216-093448-1-snapshot.jpg
-rw-r--r-- 1 motion motion 75002 Feb 16 09:36 20130216-093548-1-motion-00.jpg
-rw-r--r-- 1 motion motion 75002 Feb 16 09:36 20130216-093548-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76145 Feb 16 09:36 20130216-093618-1-motion-00.jpg
-rw-r--r-- 1 motion motion 76401 Feb 16 09:37 20130216-093648-1-snapshot.jpg
-rw-r--r-- 1 motion motion 76396 Feb 16 09:38 20130216-093748-1-snapshot.jpg

dazz@alpha:~$ ls -l /var/images/
total 3344
drwxrwxr-x 2 darren darren 352256 Feb 13 21:57 20130208-2350
drwxrwxr-x 2 darren darren 352256 Feb 13 21:51 20130209-2350
drwxrwxr-x 2 darren darren 352256 Feb 13 21:49 20130210-2350
drwxrwxr-x 2 darren darren 352256 Feb 13 21:46 20130211-2350
drwxrwxr-x 2 darren darren 258048 Feb 12 23:50 20130212-2350
drwxrwxr-x 2 darren darren 233472 Feb 13 21:42 20130213-2142
drwxrwxr-x 2 darren darren  32768 Feb 13 23:50 20130213-2350
drwxrwxr-x 2 darren darren 266240 Feb 14 23:50 20130214-2350
drwxrwxr-x 2 darren darren 262144 Feb 15 23:50 20130215-2350
drwxrwxrwx 2 root   motion 499712 Jan 25 22:03 current
drwx------ 2 root   root    16384 Dec 30 22:16 lost+found
drwxrwxr-x 2 root   motion   4096 Feb  5 23:09 testday
drwxrwxr-x 2 root   motion   4096 Feb  5 22:45 testdaybackup
drwxrwxr-x 2 root   motion 188416 Feb 16 09:40 trackcam1
drwxrwxr-x 2 root   motion 204800 Feb 16 09:40 trackcam2

darren@alpha:~$ df
Filesystem               1K-blocks    Used Available Use% Mounted on
/dev/mapper/alpha-images   5761140 2262548   3498592  40% /var/images
```

Dazz

---

### Post by Doug S on 2013-02-16
I think you are confusing the file size of the directory itself with the sum of the sizes of the files within that directory. Perhaps use du if you want the total bytes within a directory. Example:```
doug@s15:~$ ls -l zzzx
total 16777224
-rw-rw-r-- 1 doug doug 8589934592 Feb 16 07:39 big
-rw-rw-r-- 1 doug doug 8589934592 Feb 16 07:48 big2
doug@s15:~$ ls -l -d zzzx
drwxrwxr-x 2 doug doug 4096 Feb 16 07:47 zzzx
doug@s15:~$ du -b -s zzzx
17179873280     zzzx

```

---

### Post by dazz100 on 2013-02-17
Hi

The ls command lists all the files in the trackcam1 directory.
Adding up the file sizes in that directory gives an answer of 1,361,643.

The ls command of the directory that contains the trackcam1 directory gives a directory size of 188,416.  These numbers are different by a factor of ~ 7.

I am trying to understand why the size of a directory differs so much from the sum of the file sizes contained in that directory.

Dazz

---

### Post by Doug S on 2013-02-17
I guess I didn't explain very well, nor was my very simplified example of any help.
188,416 is NOT the size of the testcam1 directory. It is the size of the directory file "testcam1" itself. Directory files themselves will be N times 4096, where N is a positive integer.

---

### Post by dazz100 on 2013-02-18
Hi
OK.  One of those quirks of Linux that probably made sense at the time.

So is the size of the directory file related to the space taken by the files, or the number of files in the directory?  

How to I determine the value of <N>?

---

### Post by dcstar on 2013-02-18
> **dazz100 said:**
> Hi
OK.  One of those quirks of Linux that probably made sense at the time.

So is the size of the directory file related to the space taken by the files, or the number of files in the directory?  

How to I determine the value of <N>?

You have already been given the answer in a previous post, again:

```
man du
```

---

### Post by Doug S on 2013-02-18
> So is the size of the directory file related to the space taken by the files, or the number of files in the directory? It is not related to the space taken by the files. (At least as far as I know).
It is related to the maximum number of files that have ***_EVER_*** been in the directory, and the length of the file names, regardless of how many files are there at the time.> How to I determine the value of <N>? The short answer is don't try. Out of curiosity and by experiment, and for a IO block size of 4096, it seems that one can have 339 files in a directory before the size jumps from 4096 to 12288. Why it jumps from N=1 to N=3 instead of N=2, I don't know.
 
Edit: I expect there would be different results for different file systems, for my experiment. I did the test on an ext4 filesystem.
 
Edit: The experiment was flawed. The number of files before more space required for the directory file also depends on the file name itself (duh). Short file names means more files before the jump from 4096 to 12288 bytes, and longer file names will be less.

---

### Post by dazz100 on 2013-02-18
Hi

OK thanks. 
Another small step up the Linux learning curve.

---

