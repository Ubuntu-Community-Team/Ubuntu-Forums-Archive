---
title: "Disk use analyzer claims almost out of space"
date: 2019-06-08
forum: General Help
---

### Post by Gnusboy on 2019-06-08
Hello


The Disk Use Analyzer suddenly shows my system is extremely low on memory on available space.Ubuntu 16.04 64 bit

The system folder shows there is 73.1 GB used out of 74.4 GB
The Hard drive has 4 volumes: 
A)  113 GB volume 49.8 GB used out of 110 GB
B)  194 GB volume 106.9 GB out of 190.6 GB
C)   93 GB volume   14.9  GB out of 91.8 GB

The other volume is 156 GB, but it was not formatted when I installed the 650 GB drive. I never went back to set it up because I did not need the space.
From what I can understand, I can use the Disk Analyzer to delete files to free up space - but only on that volume? 

Should I go through the files to get rid of things I don't need? Will that cause any problems with the other volumes
Can I instead move files from the full volume over to one with more available space? If necessary, I'm sure there are numerous files that I don't need. If that is the best solution.
I have dozens of Deja Dup backups that I could sacrifice. The problem is that they are not properly dated and it's difficult to identify the oldest files. 
Most of those backups have identical dates and sizes so there is a problem to check the contents. 

Can I fix everything by upgrading to 18.04 or 19.04?

I appreciate your help. Thanks.

---

### Post by kpatz on 2019-06-08
I'm guessing by "system folder" you mean the root filesystem, which is showing almost full.

Run the command **df** and post the output here inside [code] tags.  That will show us what partitions you have for what, where they're mounted, and how much space is on each.

Also, assuming it is the root filesystem that is full (you'll see the % used in the df output, and where each filesystem is mounted, root is /), this command will list how much space is used by each of the main directories off the root:  **sudo du -xd 1 /**  Post the output of this command as well, inside [code] tags.

Where are your Deja Dup backups kept?

---

### Post by TheFu on 2019-06-08
```
df -hT|egrep '^/dev|[:/]/'
df -i 
```
output would be very helpful. Both commands, please.
IF there are any "loop" lines, please remove those - keep the output small and tidy.

Updating a broken system NEVER fixes anything. It will fail and then you'll be in a worse place.

Update: attempted to copy/paste correct command.

---

### Post by Gnusboy on 2019-06-10
Hey, thanks. Can you tell me what a "loop" line is?

---

### Post by CatKiller on 2019-06-10
> **Gnusboy said:**
> Hey, thanks. Can you tell me what a "loop" line is?

Snaps each have their own little pretend filesystem to use so that they aren't affected by anything else. Those are listed as loop devices. We don't need to see them; they'll just make the output harder to interpret.

---

### Post by Gnusboy on 2019-06-10
Kpatz
Here is what shows
system:~$ df
```

Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1840780         0   1840780   0% /dev
tmpfs             378816     10932    367884   3% /run
```

```

/dev/sda9       75540592  71315016    365252 100% /
tmpfs            1894068    221900   1672168  12% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1894068         0   1894068   0% /sys/fs/cgroup
```
tmpfs             378816       100    378716   1% /run/user/1000 
[/code]
```

/dev/sda8      108338136  48591632  54220184  48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19

/dev/sda6      186096372 104381020  72239116  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1

/dev/sda1       89608576  14537816  70495828  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59


```

The Deja Dup files are in the home folder on the 93 GB partition. It  shows a total of 92  Deja Dup files, but they are all the same size  with the same date.
I have not checked these backups. I haven't tried  to open them because I could not find out where to they would open and  whether they would overwrite my existing setup.
This is a sample of what I see in the Deja Dup files

/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol6.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol7.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol8.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol9.difftar.gz

Hope this helps.


------------------------------------------------------------------------------------

---

### Post by Gnusboy on 2019-06-10
Kpatz
Here is what shows
system:~$ df
```

Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1840780         0   1840780   0% /dev
tmpfs             378816     10932    367884   3% /run
```

```

/dev/sda9       75540592  71315016    365252 100% /
tmpfs            1894068    221900   1672168  12% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1894068         0   1894068   0% /sys/fs/cgroup
```
tmpfs             378816       100    378716   1% /run/user/1000 
[/code]
```

/dev/sda8      108338136  48591632  54220184  48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19

/dev/sda6      186096372 104381020  72239116  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1

/dev/sda1       89608576  14537816  70495828  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59


```

The Deja Dup files are in the home folder on the 93 GB partition. It   shows a total of 92  Deja Dup files, but they are all the same size   with the same date.
I have not checked these backups. I haven't tried  to open them because I  could not find out where to they would open and  whether they would  overwrite my existing setup.
This is a sample of what I see in the Deja Dup files

/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol6.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol7.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol8.difftar.gz
/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol9.difftar.gz

Hope this helps.


------------------------------------------------------------------------------------

---

### Post by kpatz on 2019-06-10
You could have put them all under one set of code tags... here's the important ones with the fluff (tmpfs and loops taken out):

```
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda9       75540592   71315016   365252 100% /
/dev/sda8      108338136   48591632 54220184  48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda6      186096372  104381020 72239116  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1       89608576   14537816 70495828  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
```Your issue is the 1st line that shows / (root) mounted on /dev/sda9 is 100% full.  Since you don't have a separate /home partition, your /home is taking up the space there.

Since you have Deja Dup files in your home, moving those to one of the /media/jess mounts would free things up nicely.  If you keep a lot of stuff in your home folder, in addition to the deja dup files, you may want to allocate the unused partition and use it for home.  If you want to do that, we can walk you through the process.

What are the /media/jess partitions for, and why are they mounted with GUID folder names?  They are partitions on your main drive (/dev/sda), while /media/jess is normally used for mounting removable drives (USB etc).

---

### Post by Gnusboy on 2019-06-10
Kpatz
Sorry. Forgot to attach the sudo du -xd 1 / output
sudo du -xd 1 /
716544    /lib
3853788    /usr
4    /mnt
13028    /bin
45012    /lost+found
4    /lib64
61331488    /home
280    /tmp
4964468    /var
14540    /etc
48    /snap
4    /srv
106904    /boot
16    /media
4    /cdrom
976    /root
12652    /sbin
184124    /opt
71243888

---

### Post by TheFu on 2019-06-10
I requested, 
```
df -hT|egrep '\''^/dev|[:/]/'\'''
```
The file system type and human readable sizes are shown, which would help understand what those partitions might be used as.

A handy alias:
```
alias dft='df -hT|egrep '\''^/dev|[:/]/'\'' |grep -vF loop'
```

Hope this helps as many people as possible.

---

### Post by Gnusboy on 2019-06-10
TheFu

I'm really glad you said to not upgrade. I was on the verge of doing just that. So thanks.

I couldn't get an output for the df -hT|egrep '\''^/dev|[:/]/'\''' command. 
jess@ranha-system:~$ df -hT|egrep '\''^/dev|[:/]/'\'''
jess@ranha-system:~$ df -hT|egrep '\''^/dev|[:/]/'\'''
jess@ranha-system:~$ 

When I put in your second ask I get this:
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             460195     558   459637    1% /dev
tmpfs            473517     862   472655    1% /run
/dev/sda9       4808704  299470  4509234    7% /
tmpfs            473517     160   473357    1% /dev/shm
tmpfs            473517       5   473512    1% /run/lock
tmpfs            473517      16   473501    1% /sys/fs/cgroup

======= loops deleted ===============

tmpfs            473517      42   473475    1% /run/user/1000
/dev/sda8       6889472 1796562  5092910   27% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda6      11829248 1110548 10718700   10% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1       5701632  534430  5167202   10% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59








Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             460195     558   459637    1% /dev
tmpfs            473517     862   472655    1% /run
/dev/sda9       4808704  299470  4509234    7% /
tmpfs            473517     160   473357    1% /dev/shm
tmpfs            473517       5   473512    1% /run/lock
tmpfs

---

### Post by TheFu on 2019-06-10
The root problem is still that / is 100% full.

Is there a reason for having full backups every time?  I thought the default in duplicity/deja-dup was to do full backups only once a month with daily incremental backups.  A daily backup that takes more than 3-5 minutes is just too long.  Anyway, like  kpatz said, move those backup files out of your HOME.  IMHO, never keep backups in HOME - keep them on separate physical disks, never on the same disk from where the backup was  taken.

duplicity is good in one way - the backup sets don't care about the underlying storage file system. The owner, group, permissions, and ACLs are included inside the backup set files, not in the file system like rsync backups use. This is good.

Below is just extra info .... 
Something funky happening with the copy/paste of characters in my command, it seems.  Probably a mix of issues on my side and in the forums. The main command is:
```
df -Th 
```
All the other stuff after that is to remove unwanted things in the output - like logical devices that don't impact storage at all. 

```
lsblk -f
```
shows some things, just in a different way, not the storage used, but other, often important, things.

Please use code tags whenever posting anything from a terminal. That applies across all threads here.  We are used to seeing that output and columns matter. Please.

---

### Post by kpatz on 2019-06-10
This doesn't work for me either:```
df -hT|egrep '\''^/dev|[:/]/'\'''
```  Removing the extra single quotes and tweaking the regex a bit allows it to work (now I just get the lines with /dev/):```
df -hT|egrep '^/(dev|[:/])/'
```Then to get rid of the loop mounts, I added another grep:```
df -hT|egrep '^/(dev|[:/])/' | grep -v '/dev/loop'
```So try that last one.

EDIT: The regex will also drop zfs mounts from the list.  This doesn't matter in the OP's case since he doesn't have any zfs mounts, but if you don't want those stripped, use this instead:```
df -hT|egrep '(^/(dev|[:/])/|zfs)' | grep -v '/dev/loop'
```

---

### Post by Gnusboy on 2019-06-10
OK. That worked. 
This is what I get with your revised input

jess@ranha-system:~$ udev             460195     558   459637    1% /dev
No command 'udev' found, did you mean:
 Command 'udv' from package 'ncbi-tools-x11' (universe)
 Command 'udav' from package 'udav' (universe)
udev: command not found
jess@ranha-system:~$ tmpfs            473517     862   472655    1% /run
No command 'tmpfs' found, did you mean:
 Command 'tmfs' from package 'tmfs' (universe)
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ /dev/sda9       4808704  299470  4509234    7% /
bash: /dev/sda9: Permission denied
jess@ranha-system:~$ tmpfs            473517     160   473357    1% /dev/shm
No command 'tmpfs' found, did you mean:
 Command 'tmfs' from package 'tmfs' (universe)
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ tmpfs            473517       5   473512    1% /run/lock
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ tmpfs            473517      16   473501    1% /sys/fs/cgroup
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ 
jess@ranha-system:~$ ======= loops deleted ===============
=======: command not found
jess@ranha-system:~$ 
jess@ranha-system:~$ tmpfs            473517      42   473475    1% /run/user/1000
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ /dev/sda8       6889472 1796562  5092910   27% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
bash: /dev/sda8: Permission denied
jess@ranha-system:~$ /dev/sda6      11829248 1110548 10718700   10% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
bash: /dev/sda6: Permission denied
jess@ranha-system:~$ /dev/sda1       5701632  534430  5167202   10% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
bash: /dev/sda1: Permission denied
jess@ranha-system:~$

---

### Post by TheFu on 2019-06-10
I give up. I'd hoped to be helpful and I've failed terrible.

We're down a rabbit hole that was solved 3-6 posts ago, right?

---

### Post by kpatz on 2019-06-10
Looks like you copied one of your forum posts (one that had the **output** of a df command) into your terminal window and tried to execute it as commands.  This doesn't work, and could cause harm depending on what was copied/pasted.

The overall issue is the deja dup files in HOME.  Move those somewhere else and you should be good to go.  Ideally, put them on an external drive and store them elsewhere... that's what a backup is for.

---

### Post by Gnusboy on 2019-06-10
Got it. I try to find logical places to put in code tags, but I'm just guessing as to where they should go.

I have had problems with Deja Dup for years. Sometimes it works, more times not. A lot of the 92 Deja Dup files are partial backups and they won't restore. Most recently
I figured out that I was attempting to store them in the wrong place. The automatic destination was set to a folder that would not work. This went on for years. Sometimes it
worked, other times not. I'd try to figure it out, but was frustrated. I'd try to jigger it to work, but no way. And I'd move on to more productive tasks.
If it looked like it was working, I'd let it be and hoped I wouldn't crash. 
Recently, I had the idea to change the destination folder to an external drive and it worked. Voila! 
I don't know how those media files got there. 
When I got the external drive and formatted it, that's when it split into so many small partitions. Again, it didn't impact my day-to-day use so I left them. I've looked at them many times with
G-parted, but trusted my ignorance to leave everything alone. Murphy's law rules my world. If it's possible to mess up something important it will.


Here's the output from your revised code:

jess@ranha-system:~$ udev             460195     558   459637    1% /dev
No command 'udev' found, did you mean:
 Command 'udv' from package 'ncbi-tools-x11' (universe)
 Command 'udav' from package 'udav' (universe)
udev: command not found
jess@ranha-system:~$ tmpfs            473517     862   472655    1% /run
No command 'tmpfs' found, did you mean:
 Command 'tmfs' from package 'tmfs' (universe)
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ /dev/sda9       4808704  299470  4509234    7% /
bash: /dev/sda9: Permission denied
jess@ranha-system:~$ tmpfs            473517     160   473357    1% /dev/shm
No command 'tmpfs' found, did you mean:
 Command 'tmfs' from package 'tmfs' (universe)
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ tmpfs            473517       5   473512    1% /run/lock
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ tmpfs            473517      16   473501    1% /sys/fs/cgroup
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ 
jess@ranha-system:~$ ======= loops deleted ===============
=======: command not found
jess@ranha-system:~$ 
jess@ranha-system:~$ tmpfs            473517      42   473475    1% /run/user/1000
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
 Command 'tmfs' from package 'tmfs' (universe)
tmpfs: command not found
jess@ranha-system:~$ /dev/sda8       6889472 1796562  5092910   27% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
bash: /dev/sda8: Permission denied
jess@ranha-system:~$ /dev/sda6      11829248 1110548 10718700   10% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
bash: /dev/sda6: Permission denied
jess@ranha-system:~$ /dev/sda1       5701632  534430  5167202   10% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
bash: /dev/sda1: Permission denied
jess@ranha-system:~$

---

### Post by kpatz on 2019-06-10
Looks like you're pasting output into the terminal window again.

Step by step, do this:

1.  Copy and paste THIS command from my post into your terminal:```
df -hT|egrep '(^/(dev|[:/])/|zfs)' | grep -v '/dev/loop'
```

You should get a bunch of stuff in your terminal that looks a bunch of lines like:

```
/dev/sda8 6889472 1796562 5092910 27% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
```

2.  Highlight those lines with the mouse, then copy this output from your terminal (right click, choose Copy).  Do not paste it into the terminal, or click the middle button on your mouse while it's over the terminal or you'll get all those errors.  

3.  Reply to this thread, and paste the output into the reply box (or middle click to paste, in the reply box).  Add [noparse]```
 and 
```[/noparse] around the output after pasting, or if you use Advanced Reply, highlight the output you pasted and click the button that looks like a #.  This will add the code tags to whatever you highlighted.

Click Preview Post and make sure it looks correct.  Then click Submit Reply.

EDIT:  I see this in your mis-pasted terminal post:```
/dev/sda9 4808704 299470 4509234 7% /
```Did you move your deja files out of HOME?  Looks like you have plenty of free space on root now!

---

### Post by Gnusboy on 2019-06-10
Hey. Thanks for your help. I appreciate it.
Too much going on here. I've gone a little goofy today.

---

### Post by Gnusboy on 2019-06-11
Kpatz

Sorry for the delay. Here's what came up with your command:

jess@ranha-system:~$ df -hT|egrep '(^/(dev|[:/])/|zfs)' | grep -v '/dev/loop'
/dev/sda9      ext4       73G   69G  332M 100% /
/dev/sda8      ext4      104G   47G   52G  48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda6      ext4      178G  100G   69G  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1      ext4       86G   14G   68G  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
/dev/sdb1      ext3      976M   60K  976M   1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3      ext3      431G   75G  356G  18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb2      ext3      500G   78G  423G  16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:~$

---

### Post by kpatz on 2019-06-11
It's more readable if you put [noparse]```
 before and 
```[/noparse] after the output when you post it here.

Like this:

[noparse]```
jess@ranha-system:~$ df -hT|egrep '(^/(dev|[:/])/|zfs)' | grep -v '/dev/loop'
/dev/sda9 ext4 73G 69G 332M 100% /
/dev/sda8 ext4 104G 47G 52G 48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda6 ext4 178G 100G 69G 60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1 ext4 86G 14G 68G 18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
/dev/sdb1 ext3 976M 60K 976M 1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3 ext3 431G 75G 356G 18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb2 ext3 500G 78G 423G 16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:~$ 
```[/noparse]

The result in your post will look like:

```
jess@ranha-system:~$ df -hT|egrep '(^/(dev|[:/])/|zfs)' | grep -v '/dev/loop'
/dev/sda9 ext4 73G 69G 332M 100% /
/dev/sda8 ext4 104G 47G 52G 48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda6 ext4 178G 100G 69G 60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1 ext4 86G 14G 68G 18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
/dev/sdb1 ext3 976M 60K 976M 1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3 ext3 431G 75G 356G 18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb2 ext3 500G 78G 423G 16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:~$ 
```It uses a monospace font so the columns line up better, and it separates out from the rest of the post to make it more readable.  An easy way: type [noparse]```
 into the reply box, then paste (Ctrl-V) your output, then type 
```[/noparse].

That said, your root filesystem (/dev/sda9) is still 100% full.  Get those deja dup files out of your home.  Put them on one of those other drives/partitions.

Are any of these devices external (USB) drives?

---

### Post by Gnusboy on 2019-06-11
[FONT=arial]Kpatz

Yes, these are both external drives.

/dev/sdb3 ext3 431G 75G 356G 18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a  on the 462GB 
/dev/sdb2 ext3 500G 78G 423G 16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3 on the 537 GB

But when I try to move the files onto either of these drives, I keep getting the the same error message saying there is no space left on drive. It happens whether I try to copy and move, move to a different location on either on the main internal drive or on either of the external drives.  These are the usual messages, but I noticed that they are not exactly the same. 

Error opening file '/media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a/Trash-1000/files/RioRanha/duplicity-full.20181219T220352Z.vol42.difftar.gz': No space left on device (/trash-1000/files)
Error opening file '/media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a/home/jess10.2015 BK/duplicity-full.20181219T220352Z.vol21.difftar.gz': No space left on device         (/home/jess10.2015 BK)
Error opening file '/media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a/duplicity-inc.20181221T214143Z.to.20190102T193356Z.vol6.difftar.gz': No space left on device           (/duplicity-inc.20181221T214143Z.)

So I'm stymied. Maybe I'm not using the right way to do it. Isn't it supposed to be ... highlight, copy and drop into another folder no matter which drive.
It also won't allow me to make a new folder or put the items into it.

Now I'm stuck for time and have to leave. I'll have to continue this later. I think I am about to have a catastrophe. So I've gotta figure it out. Thank you for your help, I appreciate it.
I'll check back when I get to it.
Here's a shot with some info too

 /home/jess/Pictures/Deja Screenshot 06-11-2019.png
file:///home/jess/Pictures/Screenshot%20disk%20use%20analyzer%20A%202019-06-08.png
[/FONT]

---

### Post by kpatz on 2019-06-11
EDIT... removed all the stuff I posted earlier... here's a simpler solution.  Do these from the command line... if you use the GUI, you may get space errors.  Also, by default deleting files in the GUI just moves them to a trash folder, freeing up no space (Shift-Delete gets around this).

1.  Backup your entire home directory to one of your external drives (we'll use the 500GB one):
```
rsync -avx ~ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
```

(You can use something other than homebackup as the folder name... I just provided that as an example).

2.  Start nuking stuff wholesale from Home now that it's backed up.
```
cd ~
rm -r .local/share/Trash
rm *.difftar.gz
rm -r trash-1000 Trash-1000

```

I'm assuming the *.difftar.gz files are all directly in home and not in a subfolder of home... if they're in a subfolder, nuke them there as well.

Check the free space with **df /**.  If it's less than 100% now, you should be able to delete/move more stuff using the GUI.  If it's still 100%, **rm -r ~/.cache** next, or find more deja dup files to delete.  Empty the trash regularly when using the GUI to move/delete files.  Close any browsers or other applications you might have running before nuking .cache.

Then run the command **du -hd 1 ~** to see if we have any more folders taking up a bunch of space.

---

### Post by Gnusboy on 2019-06-12
Kpatz

When I entered the code you gave me this is the result. It doesn't appear that rsync is creating a new folder to put this stuff in. 

jess@ranha-system:~$ rsync -avx ~ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
sending incremental file list
rsync: mkdir "/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup" failed: No space left on device (28)
rsync error: error in file IO (code 11) at main.c(674) [Receiver=3.1.1]
jess@ranha-system:~$ 

As this didn't work, I searched for something else and came up with this: 
==========================================================================================================================================================
 "I had the same issue, the destination directory had enough space but  I'd get "No space left on device". Turns out rsync copies the file to  somewhere else first, then moves it to the destination directory. To  change this behavior, use --inplace.


  According to [https://download.samba.org/pub/rsync/rsync.html](https://download.samba.org/pub/rsync/rsync.html) "This option changes how rsync transfers a file when its data needs to  be updated: instead of the default method of creating a new copy of the  file 
and moving it into place when it is complete, rsync instead writes  the updated data directly to the destination file."

   rsync --inplace source destination

Helpful or not?

---

### Post by kpatz on 2019-06-12
It's saying no space on device when it tries to mkdir on the destination.

First, make sure that destination is mounted (type **mount** and see if you see /media/jess/d60ed... mounted).  If the USB drive isn't attached, it's just going to try and create the directory in the root filesystem which is full.  If it's mounted elsewhere, use that as the destination folder instead of /media/jess/d60ed....

If it is mounted, maybe space is needed on / just to run commands like mkdir even on another partition?  Try cd-ing to the destination path and making the directory yourself:```
cd /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
mkdir homebackup
```

If that doesn't work, try it with sudo:  ```
sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
```  This may work because some space in ext4 partitions is reserved for root to use, so the system doesn't crash outright when running out of space.  If this works, chown homebackup so your regular user can write to it:```
sudo chown jess:jess /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
```

Then try sudo moving ONE file or a small group from home to homebackup (I used the asterisk because it looked like there might be a space in the filename):

```
sudo mv ~/duplicity-inc.20181221T214143Z.* /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup/
```
If this works, it may free up enough space for the rsync or cp to work to complete your backup.  Check with **df /** before proceeding.

If all else fails you may have to boot a live CD or USB, mount /dev/sda9 and the external, and move the files while the system isn't running with the full filesystem as root.

---

### Post by garvinrick4 on 2019-06-12
You can use gparted to create new space if...
Show a screen shot of gparted and we will see. Sometimes quite easy will instruct.
Gparted is a tool to create partitions if you have never used.

---

### Post by Gnusboy on 2019-06-12
I did mount the 537 GB drive and it shows that its open.
This is what I got when I typed mount. It seems like a lot of stuff for a simple command. 
I'm not sure what to change to get to the target destination. 
Is this correct?

jess@ranha-system:~$ cd /sdb2/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$ mkdir homebackup
mkdir: cannot create directory ‘homebackup’: No space left on device


jess@ranha-system:~$ cd /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$ mkdir homebackup
mkdir: cannot create directory ‘homebackup’: No space left on device
jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$ 
jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1840780k,nr_inodes=460195,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=378816k,mode=755)
/dev/sda9 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup  on /sys/fs/cgroup/systemd type cgroup  (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/evince_60.snap on /snap/evince/60 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/evince_68.snap on /snap/evince/68 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/chromium_733.snap on /snap/chromium/733 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core18_970.snap on /snap/core18/970 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/gnome-3-28-1804_51.snap on /snap/gnome-3-28-1804/51 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/evince_57.snap on /snap/evince/57 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/vestin_3.snap on /snap/vestin/3 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core18_941.snap on /snap/core18/941 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6818.snap on /snap/core/6818 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core18_782.snap on /snap/core18/782 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/gtk-common-themes_1122.snap on /snap/gtk-common-themes/1122 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/libreoffice_121.snap on /snap/libreoffice/121 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/firefox_216.snap on /snap/firefox/216 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6673.snap on /snap/core/6673 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/gtk-common-themes_818.snap on /snap/gtk-common-themes/818 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/gtk-common-themes_1198.snap on /snap/gtk-common-themes/1198 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6964.snap on /snap/core/6964 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/gnome-3-28-1804_47.snap on /snap/gnome-3-28-1804/47 type squashfs (ro,nodev,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=378816k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb3 on /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4 type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/var/lib/snapd/snaps/chromium_750.snap on /snap/chromium/750 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/firefox_226.snap on /snap/firefox/226 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/libreoffice_123.snap on /snap/libreoffice/123 type squashfs (ro,nodev,relatime)
/dev/sda8 on /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb2 on /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3 type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$

---

### Post by Gnusboy on 2019-06-12
Here's my problem: I don't know how to change the destination to mkdir 
Also, the properties on this are root. does this matter\?


d60ed036-350a-4524-833e-c91e7dd76fc3
Folder (inode/directory)
Location:/media/jess
I know I should be able to do this, but ... my brain is totally in the weeds.

---

### Post by kpatz on 2019-06-12
> **Gnusboy said:**
> Here's my problem: I don't know how to change the destination to mkdir You changed your destination when you entered the command:```
cd /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
```and your prompt changed to```

jess@ranha-system:/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3$ 
```This is telling you your current directory is now /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3.

However, the mkdir still failed.  What happens if you **sudo mkdir homebackup** while you're in /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3?

Does that work?

Also, are there any large files in your home that you can **delete**?  Ones you don't care about?  Maybe deleting works when a mkdir or rsync or cp doesn't.

Also post the output of the command **du -hd 1 ~**.  This will tell you the folders in home and how much space each takes.

---

### Post by Gnusboy on 2019-06-12
This is what I get

[sudo] password for jess: 
mkdir: cannot create directory ‘/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup’: No space left on device
jess@ranha-system:/$ sudo mkdir homebackup
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
jess@ranha-system:/$ sudo mkdir homebackup
**mkdir: cannot create directory ‘homebackup’: File exists**
jess@ranha-system:/$

---

### Post by Gnusboy on 2019-06-12
Is there a problem deleting the oldest backups? They are about 54 MB each and there are 80 of them. Wouldn't that be the easiest? And then do a full backup of the current system.

---

### Post by garvinrick4 on 2019-06-12
Hi i would like to see screen shot of Gparted 
> sudo apt-get install gparted
gparted will tell if we can add more space to your partition

---

### Post by kpatz on 2019-06-13
With no space left on root he won't be able to install gparted.  But the command ```
sudo gdisk -l /dev/sda
``` should give info on the partitioning of the drive, and gdisk should be installed by default.

How old are the oldest backups?  Maybe deleting a couple them is the key, if you don't need them.

> **Gnusboy said:**
> This is what I get

[sudo] password for jess: 
mkdir: cannot create directory &#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: No space left on device
jess@ranha-system:/$ sudo mkdir homebackup
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
jess@ranha-system:/$ sudo mkdir homebackup
**mkdir: cannot create directory &#8216;homebackup&#8217;: File exists**
jess@ranha-system:/$
You werent cd-ed to /media/jess/d60... try **sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup** and see if it creates the directory then.

---

### Post by Gnusboy on 2019-06-13
Is there a problem deleting the oldest backups? They are about 54 MB each and there are 80 of them. Wouldn't that be the easiest? And then do a full backup of the current system.

---

### Post by kpatz on 2019-06-13
If you don't need them, delete them.  Even deleting 1 or 2 might get you unstuck so you can move the rest to the USB drive.

And when you do a new backup, backup to the external drive instead of home.

---

### Post by Gnusboy on 2019-06-13
OK
A couple of things. If I delete some of the older backups, it should give me enough working space.
When I use this code does it create the (sudo) **mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup on the 500 drive.**
and get rid of the [I]jess@ranha-system:/$ sudo mkdir homebackup
sudo: unable to resolve host ranha-system ?[/I]

&#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: on the 500GB drive,?
Or do I then (sudo**) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': **on the 500 drive?

If I still get** "cannot create directory &#8216;homebackup&#8217;: File exists" ** I will need to make a folder under the homebackup directory on the 500GB to store my new backup. Have I got this right?
Now, saying this all works, I follow the steps you gave me before, which should and/or  tell me if my main drive is healthy. Yes?
As long as I don't mess with the boot drive, SDA9, everything should  start working as it was, yes?

---

### Post by kpatz on 2019-06-13
To avoid confusion, I'd use fully-qualified paths in your commands for now.  Copy and paste them from this post.

So, use **(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup** instead of **mkdir homebackup**.

If you get **cannot create directory &#8216;homebackup&#8217;: File exists** that means the directory homebackup exists already.  You can verify this from the file manager, or the command **ls -l /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3**

Once you know homebackup exists, use this command to copy everything from home to homebackup (use sudo to get around the no space issue):```
sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
```

If this works, you'll have backed up everything in home, and you can delete stuff to your heart's content (especially those big backup files!)

---

### Post by garvinrick4 on 2019-06-13
Gnusboy if in fact user doesn't have a /Home partition does it make sense to make a partition of /Home and 
move what he wants from his / to /Home partition and never have a / full again. 
I do not know if he has room on drive for new partition. He has what 4 gig of backups to move delete or keep elsewhere on different drive and 
who knows how much in Documents and such on /.
I might be missing something user wants to accomplish without having a /Home partition.

---

### Post by Gnusboy on 2019-06-14
[SIZE=4]Many of the saved Deja Dup backups show they we created on the same date. Weds Dec. 19 2018 They are also encrypted with "duplicity-full.20181219T220352Z.vol20.difftar.gz" Gzip archive (application/gzip) "could not open "duplicity-full.20181219T220352Z.vol18.difftar Archive type not supported and can't be opened
 They show "An error occurred while extracting files."

/home/jess/deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz
[/SIZE]

---

### Post by Gnusboy on 2019-06-14
Well I just lost the last 3 hours of readable notes on trying to solve the problems
All I have now are filled with some sort of formatting that I havenm't a clue as to fix. Maybe someone out there can fix this.


I just checked the 500 GB external drive and the permissions are all root. Does sudo override that?<br><br>This is what I get with sudo gdisk -l /dev/sda<br><br>sudo gdisk -l /dev/sda<br>GPT fdisk (gdisk) version 1.0.1<br><br>Partition table scan:<br>&nbsp; MBR: MBR only<br>&nbsp; BSD: not present<br>&nbsp; APM: not present<br>&nbsp; GPT: not present<br><br><br>***************************************************************<br>Found invalid GPT and valid MBR; converting MBR to GPT format<br>in memory. <br>***************************************************************<br><br>Disk /dev/sda: 1250263728 sectors, 596.2 GiB<br>Logical sector size: 512 bytes<br>Disk identifier (GUID): 7D3D8303-DF28-4883-8C20-92EB535FCBDA<br>Partition table holds up to 128 entries<br>First usable sector is 34, last usable sector is 1250263694<br>Partitions will be aligned on 8-sector boundaries<br>Total free space is 13062 sectors (6.4 MiB)<br><br>Number&nbsp; Start (sector)&nbsp;&nbsp;&nbsp; End (sector)&nbsp; Size&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code&nbsp; Name<br>&nbsp;&nbsp; 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 63&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 182342098&nbsp;&nbsp; 86.9 GiB&nbsp;&nbsp;&nbsp; 8300&nbsp; Linux filesystem<br>&nbsp;&nbsp; 5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1239736113&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1250258624&nbsp;&nbsp; 5.0 GiB&nbsp;&nbsp;&nbsp;&nbsp; 8200&nbsp; Linux swap<br>&nbsp;&nbsp; 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 640942080&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1019336258&nbsp;&nbsp; 180.4 GiB&nbsp;&nbsp; 8300&nbsp; Linux filesystem<br>&nbsp;&nbsp; 7&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 336103424&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 640940031&nbsp;&nbsp; 145.4 GiB&nbsp;&nbsp; 8300&nbsp; Linux filesystem<br>&nbsp;&nbsp; 8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1019336704&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1239734271&nbsp;&nbsp; 105.1 GiB&nbsp;&nbsp; 8300&nbsp; Linux filesystem<br>&nbsp;&nbsp; 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 182343680&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 336101375&nbsp;&nbsp; 73.3 GiB&nbsp;&nbsp;&nbsp; 8300&nbsp; Linux filesystem<br><br>Is this an issue? <br>Found invalid GPT and valid MBR; converting MBR to GPT format<br>in memory. <br>====================================================<br><br>ls -l /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3<br>total 140<br>drwxr-xr-x&nbsp; 2 root root&nbsp; 4096 Jun 16&nbsp; 2014 DishArc<br>drwxrwxrwx&nbsp; 3 jess jess&nbsp; 4096 Mar 29&nbsp; 2010 home<br>drwxrwxrwx&nbsp; 3 jess jess&nbsp; 4096 Mar 29&nbsp; 2010 home2<br>drwxrwxrwx 41 jess jess 20480 Sep 18&nbsp; 2016 jess<br>-rw-rw-rw-&nbsp; 1 jess jess 70752 Dec 25&nbsp; 2012 Linux cheat sheet.pdf<br>drwx------&nbsp; 2 root root 16384 May 24&nbsp; 2014 lost+found<br>drwxrwxrwx 65 jess jess&nbsp; 8192 Mar 22&nbsp; 2016 Ranha0316<br>drwxrwxrwx&nbsp; 2 jess jess&nbsp; 4096 Dec 29&nbsp; 2012 safebrowsing<br>drwxrwxrwx&nbsp; 2 jess jess&nbsp; 4096 Sep 12&nbsp; 2014 USDA Grant forms<br>=========================================================<br><br>sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'<br>&gt; <br>&gt; sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'<br>[sudo] password for jess: <br>mkdir: cannot create directory ‘/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup\n\nsudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup’: No such file or directory<br><br>sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup <br>[sudo] password for jess: <br>Sorry, try again.<br>[sudo] password for jess: <br>cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No space left on device<br><br>Tried all of this: <br><br><br>sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <br>&gt; <br>&gt; <br>&gt; <br>&gt;&nbsp;&nbsp; h &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; this h was a typing error&nbsp; ----- <br>&gt; sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <br><br>h<br>cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup '$'\n\n\n\n''h'$'\n''sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No such file or directory<br>h: command not found<br><br>I<br><br>Just to check,<br>Using this code: <strong>(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup</strong><pre class="bbcode_code" style="height:36px;">One thing I noticed is a missing <span class="js-about-item-abstr">apostrophe at the end of </span><em>/homebackup</em> command<br> <br>I enter sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3<strong>/</strong><em>homebackup</em><strong> without an apostrophe </strong>but the terminal returns<br><br>(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <em>with an apostrophy'</em></pre><br><br>and this shows<br>(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <strong>bash: syntax error near unexpected token `mkdir'<br></strong><br>I made a variety of small changes, adding an apostrophy, seeing if putting (sudo) before the command and inserting parenthises around sudo - but get nothing usable<br><br>Then there is a space followed by&nbsp; &gt;<br>And I get these variations<br>&gt; <br>&gt; sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'<br>[sudo] password for jess: <br>mkdir: cannot create directory ‘/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup\n\nsudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup’: No such file or directory<br>jess@ranha-system:~$ mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup<br>mkdir: cannot create directory ‘/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup’: No space left on device<br>jess@ranha-system:~$ sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup <br>[sudo] for jess: <br><br>cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No space left on device<br>jess@ranha-system:~$ sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <br><br>This didn't work<br>sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' <br>cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup '$'\n\n\n\n''h'$'\n''sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No such file or directory<br><br>I tried all of this and am still where we started. I think I get the gist of what to do, with a good dose of paranoia about screwing up something drastic.. You guys have been awesome with your time and help, but I don't seem to be catching it.<br><br>mkdir: cannot create directory ‘/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup’: No space left on device<br>jess@ranha-system:~$ (sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup<br>bash: syntax error near unexpected token `mkdir'<br><br><br><br><br><br><br>

---

### Post by kpatz on 2019-06-14
Here's your post reformatted correctly (good thing I'm a programmer with a decent text editor...)

> I just checked the 500 GB external drive and the permissions are all root. Does sudo override that?

This is what I get with sudo gdisk -l /dev/sda

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


******************************* ********************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
********************************************** *****************

Disk /dev/sda: 1250263728 sectors, 596.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7D3D8303-DF28-4883-8C20-92EB535FCBDA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Partitions will be aligned on 8-sector boundaries
Total free space is 13062 sectors (6.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63       182342098   86.9 GiB    8300  Linux filesystem
   5      1239736113      1250258624   5.0 GiB     8200  Linux swap
   6       640942080      1019336258   180.4 GiB   8300  Linux filesystem
   7       336103424       640940031   145.4 GiB   8300  Linux filesystem
   8      1019336704      1239734271   105.1 GiB   8300  Linux filesystem
   9       182343680       336101375   73.3 GiB    8300  Linux filesystem

Is this an issue? 
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
============================================== ======

ls -l /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
total 140
drwxr-xr-x  2 root root  4096 Jun 16  2014 DishArc
drwxrwxrwx  3 jess jess  4096 Mar 29  2010 home
drwxrwxrwx  3 jess jess  4096 Mar 29  2010 home2
drwxrwxrwx 41 jess jess 20480 Sep 18  2016 jess
-rw-rw-rw-  1 jess jess 70752 Dec 25  2012 Linux cheat sheet.pdf
drwx------  2 root root 16384 May 24  2014 lost+found
drwxrwxrwx 65 jess jess  8192 Mar 22  2016 Ranha0316
drwxrwxrwx  2 jess jess  4096 Dec 29  2012 safebrowsing
drwxrwxrwx  2 jess jess  4096 Sep 12  2014 USDA Grant forms
========================================= ================

sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'
&gt; 
&gt; sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'
[sudo] password for jess: 
mkdir: cannot create directory &#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup

sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: No such file or directory

sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup 
[sudo] password for jess: 
Sorry, try again.
[sudo] password for jess: 
cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No space left on device

Tried all of this: 


sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' 
> 
> 
> 
>   h         &n bsp;       &nbs p;                &nbsp ; this h was a typing error  ----- 
> sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' 

h
cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup '$'



''h'$'
''sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No such file or directory
h: command not found

I

Just to check,
Using this code: **(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup**One thing I noticed is a missing apostrophe at the end of **/homebackup** command
 
I enter sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3**/****homebackup**** without an apostrophe **but the terminal returns

(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' **with an apostrophy'**

and this shows
(sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' [b]bash: syntax error near unexpected token `mkdir'
[/b]
I made a variety of small changes, adding an apostrophy, seeing if putting (sudo) before the command and inserting parenthises around sudo - but get nothing usable

Then there is a space followed by  >
And I get these variations
> 
> sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup'
[sudo] password for jess: 
mkdir: cannot create directory &#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup

sudo mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: No such file or directory
jess@ranha-system:~$ mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
mkdir: cannot create directory &#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: No space left on device
jess@ranha-system:~$ sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup 
[sudo] for jess: 

cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No space left on device
jess@ranha-system:~$ sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' 

This didn't work
sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup' 
cp: cannot create directory '/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup '$'



''h'$'
''sudo cp -av ~/ /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup': No such file or directory

I tried all of this and am still where we started. I think I get the gist of what to do, with a good dose of paranoia about screwing up something drastic.. You guys have been awesome with your time and help, but I don't seem to be catching it.

mkdir: cannot create directory &#8216;/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup&#8217;: No space left on device
jess@ranha-system:~$ (sudo) mkdir /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3/homebackup
bash: syntax error near unexpected token `mkdir'

 

Anyway, it appears the mkdir even with sudo isn't working... and the copy command didn't either.  Sudo overrides the permissions as it runs the command as root.  Besides, if it were a permissions issue, you'd get a message to that effect ("permission denied") rather than "no space left on device".

Also, when I gave an example with sudo in parentheses, that wasn't literal... I was mentioning that sudo may or may not have been needed.  Typing or pasting the sudo commands I gave that had parentheses... like **(sudo) mkdir...** won't work.  Also, you copied a stray apostrophe in some of your commands which prevented them from working.

The messages gdisk gave you were just because you have an MBR instead of GPT partition table... that's not a problem.  But there are no open partitions on your internal drive to expand root either, though you have several other Linux partitions on the drive... what are those for?

Are *all* the backup files dated 12/19/2018?  Are there any with older dates?  If you delete one, it may render the entire backup moot.  But if you don't care, and can take a new backup, I'd just delete one with the command **rm ~/deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz**  If you want to delete more than one, just repeat the command, changing the vol33 to another one of the files you have.

If that doesn't work, try it again with sudo: **sudo rm ~/deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz**  If that still doesn't work, we'll have to get out the big guns... you'll have to boot from a live CD or USB, mount the drives, and move/delete the files from there.

---

### Post by kpatz on 2019-06-14
Ok, I just filled up the root on a VM, and I have no problems deleting, copying or moving files off.

It seems odd that you get "no space on device" when accessing /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3.

Can you run the command **df -hT -t ext3 -t ext4** and post the output?  We need to make sure the external drive we're trying to move to is mounted.  LOL.  If it isn't, we're trying to move from the root FS to the root FS, which won't work since it's full.

Also post the output of **ls -l /media** and **ls -l /media/jess**.  Let's make sure there aren't any stray directories in there that aren't part of a mount.

---

### Post by Gnusboy on 2019-06-15
Kpatz,
You sir, are a god-like programmer with an exceptional text editor. Many kudos.

Here's the output for df
```

jess@ranha-system:~$ df -hT -t ext3 -t ext4 
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda9      ext4   73G   69G  150M 100% /
/dev/sdb3      ext3  431G   75G  356G  18% /media/jess/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sdb1      ext3  976M   60K  976M   1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sda8      ext4  104G   47G   52G  48% /media/jess/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sdb2      ext3  500G   78G  423G  16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
/dev/sda6      ext4  178G  100G   69G  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/sda1      ext4   86G   14G   68G  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
jess@ranha-system:~$ 
```
```

jess@ranha-system:~$  ls -l /media
total 4
drwxr-x---+ 10 root root 4096 Jun 14 12:19 jess

```
```

jess@ranha-system:~$  ls -l /media/jess
total 32
drwxrwxrwx 11 jess jess 4096 Jun 12 15:10 205504c6-6bf7-4fc0-a732-4ea634c2d00a
drwx------  2 root root 4096 Dec  9  2018 77aacfae-f704-422a-82f5-047bb0dcb95f
drwxr-xr-x 26 root root 4096 Oct 11  2014 77aacfae-f704-422a-82f5-047bb0dcb95f1
drwxr-xr-x  3 root root 4096 May 24  2014 897fbe47-71a3-4afa-9722-109fc80bc2a4
drwxr-xr-x 23 root root 4096 Jul 22  2018 a2aad275-090f-490e-a903-e4b68f52eb19
drwx------  2 root root 4096 Dec  9  2018 Apr 08 2010
drwxrwxrwx 10 jess jess 4096 Mar 22  2016 d60ed036-350a-4524-833e-c91e7dd76fc3
drwxr-xr-x 25 root root 4096 Feb  8  2017 d936da7d-f118-4a64-87cb-ea8377a17d59
jess@ranha-system:~$  ls -l /media

```

---

### Post by kpatz on 2019-06-15
Let's start by getting rid of the directories that aren't mounted.  Make sure you copy everything including the single quotes, and make sure you paste the command correctly before entering your sudo password... sudo rm -rf is dangerous if mistyped/mis-pasted.

```
sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
```

Did you try deleting 1 or 2 files from home to see if it freed up any space, as I mentioned in my prior post where I deobfuscated your previous post with my editor?

```
rm ~/deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz
```

---

### Post by Gnusboy on 2019-06-15
When I try the code you show can I use a careful copy/paste. Does it delete the file I see, or will I need to delete file by file? Should I also check to make sure the file you show is still
in my Deja Dup folder first so it doesn't hickup.

Yes, I did previously delete a couple of old backup files. But then I started looking at them closely and the dates they show don't match.
When going through the numerous Deja Dup backups, Most show the same date until I opened the properties which were different.
Kinda crazy. The file manager list shows the modified date Dec.19, 2018 and size 52.4 MB
But when opened with Properties, the size is not 52.4 it shows as 101.5 MB. They will not open and some actually seem to be copies of each other, but when opened have different info.

But ... the get things moving with the over all problem. I'm just gonna delete some older looking files and hope for the best. One question: Just moving them to trash does not delete them. right? 
I have to delete them to free up space. I think I saw something about a quicker method. And .. . my trash file is about 2 GB. So most problems can be fixed just by emptying the Trash, yes?
Before that, if I spot a couple of things I still want - I need to move them some where else.

---

### Post by kpatz on 2019-06-15
The command I gave will delete 1 file.  Figured we'd start small, and see if we can free up some space.  But before you do that, try emptying your trash.  That may free up enough space that you don't have to lose any of your backups.

If emptying trash fails from the file manager, try it from the command line: **rm -r ~/.local/share/Trash**

If you delete files with the file manager, by default they are moved into trash.  If you use Shift+Del it will delete them outright without moving them to trash, freeing up space.

Another thing to try, if you use a web browser on that machine, empty its cache.

Of course, if you want to go for broke, you could just nuke the entire deja dup folder (shift-del it in file manager, or use the command **rm -r ~/deja-dup** - deleting all your backups, then take a new backup (to your external drive!!) once space is freed.  I'd save that as a last resort.

---

### Post by Gnusboy on 2019-06-15
This is odd. I entered the command 
sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
and nothing is moving. It just stopped blinking.

jess@ranha-system:~$ sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
jess@ranha-system:~$ sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
jess@ranha-system:~$

---

### Post by kpatz on 2019-06-15
Did the prompt come back?  Looks like it did based on your copy/paste.  Which means the deletes worked.  (rm -f will not return a "not found" error if what you're deleting isn't there)

Have you tried emptying your Trash yet?  If the GUI won't do it, use the command **rm -r ~/.local/share/Trash**

After deleting trash, do a **df -h /** to see if any space was freed.

---

### Post by Gnusboy on 2019-06-15
This is odd. I entered the command 
sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
and nothing is moving. It just stopped blinking.

jess@ranha-system:~$ sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
sudo: unable to resolve host ranha-system
[sudo] password for jess: 
jess@ranha-system:~$ sudo rm -rf '/media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f' '/media/jess/Apr 08 2010'
jess@ranha-system:~$

---

### Post by kpatz on 2019-06-15
You just reposted the same thing.

Empty trash with **rm -r ~/.local/share/Trash**  (you won't see any messages if it worked)

After deleting trash, do a **df -h /** to see if any space was freed.

---

### Post by Gnusboy on 2019-06-15
I cleared the cache and I'm looking at the trash to dbl check I'm not throwing away anything I really want.
Dumb question: How do I refresh the system to check out how much I have or made?

And ... I don't think I entered the second command. I should do that now.
rm ~/deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz
OK the /deja-dup/duplicity-full.20181219T220352Z.vol33.difftar.gz is gone.

---

### Post by kpatz on 2019-06-15
> **Gnusboy said:**
> Dumb question: How do I refresh the system to check out how much I have or made?Run the command **df -h /** and see what the % Used is.  If it's under 100%, you should have enough space now to start moving/deleting files using the GUI.

---

### Post by CatKiller on 2019-06-15
Note: this isn't about fixing your actual problem, it's simply for information.

> **Gnusboy said:**
> When going through the numerous Deja Dup backups, Most show the same date until I opened the properties which were different.
Kinda crazy. The file manager list shows the modified date Dec.19, 2018 and size 52.4 MB
But when opened with Properties, the size is not 52.4 it shows as 101.5 MB. They will not open and some actually seem to be copies of each other, but when opened have different info.

It seems you're confused about the way that Déjà Dup works, and it's adding to your frustration.

The first time you run it, and after *x* amount of time, it will do a *full backup* of the files that you've selected. It does some compression (it uses tar) to try to squash it a bit, but a full backup is *big*. For each of the subsequent backups, until *x* amount of time has passed, it will only back up the differences between the last backed-up version and now (using rdiff). These *incremental backups* are small. To successfully restore files from your backup you will need the last full backup and *every* intermediate backup between then and now, so that it can step through each of the incremental changes to each of the files. That's why you seem to have archives of the same files with different contents.

---

### Post by Gnusboy on 2019-06-15
Thanks Cat,
When you say backups are incremental. How far back should they go? If just to the last full backup, is there a way to determine whether a backup is the initial one without looking through the entire contents?
And if failing to locate the full backup, will I still have access to what is there?

---

### Post by CatKiller on 2019-06-15
> **Gnusboy said:**
> Thanks Cat,
When you say backups are incremental. How far back should they go? If just to the last full backup, is there a way to determine whether a backup is the initial one without looking through the entire contents?
And if failing to locate the full backup, will I still have access to what is there?

That depends on your settings. How long between full backups, and how often the incremental ones are done are configurable, and you probably set those when you set up which files to back up. I think mine is set up to do a full backup every month and incremental backups every day, but I have no idea if that was the default or not. I also don't know whether the default is to automatically delete stale backups, or whether you're expected to manage that manually. 

If you don't have a full backup and all the incremental backups you can't restore anything. But if you do, you can roll the files back to wherever an incremental backup was taken. I believe Déjà Dup aims to keep at least two full backups at all times, so that you can't lose everything from a tiny error - it just has to march through more incremental backups to get to the final state. 

From skimming the thread, though, I understood that your plan was to put all of your backup files somewhere more sensible, anyway.

---

### Post by Gnusboy on 2019-06-15
Here's the **df -h** output
Before and after. Looks like  I recaptured 4% of sda9 boot partition. I actually never thought much  about the 93GB being the boot partition. I work in all of them without  thinking. Which is how I got into this mess.
I still need to  backup my system to figure out the bigger problem. 
I may have dug myself into a hole. I deleted several backup files while trying to free up space. I don't know whether they were the partials or not. 
With luck, I might dodge that bullet, but I could have to go back pretty far to start the process.
I still need to  backup my system to figure out the bigger problem. Should I use Deja Dup  for this, or another program  - rsync maybe?

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           370M   39M  332M  11% /run
/dev/sda9        73G   68G  699M 100% /
tmpfs           1.9G   62M  1.8G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop1      8.2M  8.2M     0 100% /snap/evince/68
/dev/loop3      155M  155M     0 100% /snap/chromium/733
/dev/loop4       54M   54M     0 100% /snap/core18/970
/dev/loop6      152M  152M     0 100% /snap/gnome-3-28-1804/51
/dev/loop11      66M   66M     0 100% /snap/vestin/3
/dev/loop8       54M   54M     0 100% /snap/core18/941
/dev/loop10      90M   90M     0 100% /snap/core/6818
/dev/loop12      54M   54M     0 100% /snap/core18/782
/dev/loop18      35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop17     519M  519M     0 100% /snap/libreoffice/121
/dev/loop13     212M  212M     0 100% /snap/firefox/216
/dev/loop14      90M   90M     0 100% /snap/core/6673
/dev/loop9       35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop16      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop20      89M   89M     0 100% /snap/core/6964
tmpfs           370M  132K  370M   1% /run/user/1000
/dev/sdb1       976M   60K  976M   1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/loop21     156M  156M     0 100% /snap/chromium/750
/dev/loop15     212M  212M     0 100% /snap/firefox/226
/dev/loop22     519M  519M     0 100% /snap/libreoffice/123
/dev/sdb2       500G   78G  423G  16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
/dev/sda6       178G  100G   69G  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/loop2      8.2M  8.2M     0 100% /snap/evince/95
/dev/loop7      152M  152M     0 100% /snap/gnome-3-28-1804/55
/dev/sda1        86G   14G   68G  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
jess@ranha-system:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           370M   39M  332M  11% /run
/dev/sda9        73G   66G  2.9G  96% /
tmpfs           1.9G   62M  1.8G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop1      8.2M  8.2M     0 100% /snap/evince/68
/dev/loop3      155M  155M     0 100% /snap/chromium/733
/dev/loop4       54M   54M     0 100% /snap/core18/970
/dev/loop6      152M  152M     0 100% /snap/gnome-3-28-1804/51
/dev/loop11      66M   66M     0 100% /snap/vestin/3
/dev/loop8       54M   54M     0 100% /snap/core18/941
/dev/loop10      90M   90M     0 100% /snap/core/6818
/dev/loop12      54M   54M     0 100% /snap/core18/782
/dev/loop18      35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop17     519M  519M     0 100% /snap/libreoffice/121
/dev/loop13     212M  212M     0 100% /snap/firefox/216
/dev/loop14      90M   90M     0 100% /snap/core/6673
/dev/loop9       35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop16      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop20      89M   89M     0 100% /snap/core/6964
tmpfs           370M  136K  370M   1% /run/user/1000
/dev/sdb1       976M   60K  976M   1% /media/jess/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/loop21     156M  156M     0 100% /snap/chromium/750
/dev/loop15     212M  212M     0 100% /snap/firefox/226
/dev/loop22     519M  519M     0 100% /snap/libreoffice/123
/dev/sdb2       500G   78G  423G  16% /media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3
/dev/sda6       178G  100G   69G  60% /media/jess/77aacfae-f704-422a-82f5-047bb0dcb95f1
/dev/loop2      8.2M  8.2M     0 100% /snap/evince/95
/dev/loop7      152M  152M     0 100% /snap/gnome-3-28-1804/55
/dev/sda1        86G   14G   68G  18% /media/jess/d936da7d-f118-4a64-87cb-ea8377a17d59
jess@ranha-system:~$

---

### Post by CatKiller on 2019-06-15
> **Gnusboy said:**
> I may have dug myself into a hole. I deleted several backup files while trying to free up space. I don't know whether they were the partials or not. 
With luck, I might dodge that bullet, but I could have to go back pretty far to start the process.

Déjà Dup is just a simplified front-end to **duplicity**, which has more options. I'm pretty sure you can get it to look at the state of your backups and delete all but a few. I'm on my phone, so I can't check all the syntax. **man duplicity** will probably show you all the details.

Worst case scenario, if you've knackered your backups, you can do a full backup of the files you want to keep to the new location, and nuke all the old ones to get a functioning system again. I'm guessing that you'd prefer to have an operational computer than pristine version history for those files, if it came down to the choice.

You're probably fine, though.

---

### Post by kpatz on 2019-06-16
At this point, since you've deleted some of the deja-dup files already and your backups are probably useless now, I'd just blow away the whole deja-dup directory (which will free up a BUNCH of space), then start with a fresh backup saved to an external drive.

What is the bigger problem you speak of?  The way I see it, you saved backups to your home folder in the boot partition, and that's what filled it up.

Did you delete anything else besides deja dup backup files?  Did you empty trash?  With a little space remaining now, you should be able to work in the GUI again.

Where do you get 93GB from?  Your boot partition is 73 GB.

Also, what are the partitions on /dev/sda1, /dev/sda6, /dev/sda7 and /dev/sda8 for?  (/dev/sda9 is your root partition that has been full).  /dev/sda1 and /dev/sda8 appear to be mounted to /media/jess as well, like they're external, but /dev/sda* is your internal drive.

---

### Post by Gnusboy on 2019-06-16
Geez, I didn't think of it until now - I have a duel boot.

I still have Ubuntu 14.04 in a separate partition on this 650 GB hard drive! I kept it when I upgraded to 16.04, because there were things on the drive I wanted to be certain to survive the upgrade process. But I seldom use it or check it. I thought it was a cool idea at the time.

Man! I'm about two peachs short of a cobbler.

For one reason or another I have always had trouble getting Deja Dup to work on either partition. It would work for a while, then it wouldn't. It started to do a backup, but then it choked. I think it was mostly because I did not have the right configuration. I'd mess with it until I got frustrated and then just hoped I had saved the data. Is it possible that having 14.04 on the other partition has messed 
up the 16.04 install on the main partition? I wouldn't normally think that, but ...
I just recently figured out that the location Deja Dup picked for a backup was in my home folder - the same place as Deja Dup. Once I figured that out, Deja worked as it was supposed to.

I'm thinking the best thing would be to do a full backup and then torch the whole thing. Comments?

---

### Post by kpatz on 2019-06-16
> **Gnusboy said:**
> Geez, I didn't think of it until now - I have a duel boot.

I still have Ubuntu 14.04 in a separate partition on this 650 GB hard drive! I kept it when I upgraded to 16.04, because there were things on the drive I wanted to be certain to survive the upgrade process. But I seldom use it or check it. I thought it was a cool idea at the time.

(snip)

I'm thinking the best thing would be to do a full backup and then torch the whole thing. Comments?14.04 is at end of life... if there's anything in that partition you want, I'd copy it off and nuke the partition, and reuse it for your home or something.  What are you on now, 16.04?  Maybe do that backup (delete your deja-dup files first so you aren't backing up a half baked set of backups), nuke everything and then install 18.04, going for the manual partitioning route and creating a separate /home partition.  You could leave another partition open to allow for installing 20.04 next year in its own partition if you like as well.  650 GB is a lot of space especially for Linux, so you have plenty of options.

Another thing you should do (not now, but once the dust is settled) is put labels on your external drive partitions so they mount with meaningful names instead of UUIDs.  No rush on this, but the command is **sudo e2label /dev/device new-label-name-here**  For example, if you want /dev/sdb2 for backups, you could use the command **sudo e2label /dev/sdb2 backup** and then next time you mount that drive it will mount as **/media/jess/backup** instead of **/media/jess/d60ed036-350a-4524-833e-c91e7dd76fc3**.

---

### Post by Gnusboy on 2019-06-16
Great advice. I hope I can call on you the next time I'm tripping over my feet.

---

### Post by kpatz on 2019-06-16
> **Gnusboy said:**
> Great advice. I hope I can call on you the next time I'm tripping over my feet.Sure... if I come across your post and have a clue how to help... lol.  I've used Ubuntu for years but I don't know the answer to everything.  I'm also on again off again on this forum... been active recently since i upgraded a few boxes to 18.04, but eventually I'll probably drop off again for a while until I start upgrading to 20.04 lol.

---

### Post by Gnusboy on 2019-06-17
Hi CatKiller

I get what you say, but does that mean the files I deleted will prevent a restore? When Deja tries to restore everything, will it stop the process or does it skip over the missing file to restore what is available?
Also, is moving the volumes that are in the Deja Dup folder over to my bigger drive a simple cut and paste, file after file, or can I move the entire folder in one swell foop. 
If I want to look through the files in a volume, can I pick and choose individual things to examine. I have never restored a backup and don't know how to go about it. Is it as easy as hitting the restore button and letting run its course
Thank you
Lastly, when I restore a backup does it just open into a separate folder, or does it automatically overwrite and install the existing setup?
Thanks

---

### Post by CatKiller on 2019-06-17
> **Gnusboy said:**
> Hi CatKiller

I get what you say, but does that mean the files I deleted will prevent a restore? When Deja tries to restore everything, will it stop the process or does it skip over the missing file to restore what is available?

I don't know. I'd imagine it will try its best and then shout at you if it can't do it.

>  Also, is moving the volumes that are in the Deja Dup folder over to my bigger drive a simple cut and paste, file after file, or can I move the entire folder in one swell foop. 

You should just be able to dump the whole shebang somewhere. What happens to the files in the interim doesn't actually matter, as I understand it, as long as it can find the right place when doing a backup or restoring from the backup.

> If I want to look through the files in a volume, can I pick and choose individual things to examine.

Nope. There are different backup approaches that do file-level snapshots, so you can just browse through the collection and restore individual files. Duplicity works on snapshots of the whole thing. So you can restore *all* the files from a particular day, or *all* the files from a different day, but you can't restore a particular file from a particular day.

> I have never restored a backup and don't know how to go about it. Is it as easy as hitting the restore button and letting run its course
Thank you
When I tested that my backups worked, it was just pointing it at where the backups were stored, then pointing it where I wanted them put, and then telling it to go.
> 
Lastly, when I restore a backup does it just open into a separate folder, or does it automatically overwrite and install the existing setup?
Thanks
You get to say where they go. If you're overwriting files of the same name, I'd imagine that it will ask you what you want to do, the same as any other file operation.

---

