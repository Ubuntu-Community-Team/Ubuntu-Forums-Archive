---
title: "fsck: Couldn’t fix parent of inode : Couldn’t find parent directory entry"
date: 2013-03-30
forum: General Help
---

### Post by aplusr on 2013-03-30
Got the above error after booting into a gparted live cd and it crashing five minutes into a complete move of my main system. Now ubuntu is all messed up and running fsck gives me this error. 

Pass 3: Checking directory connectivity
'..' in /lost+found/#1837905 (1837905) is <The NULL inode> (0), should be /lost+found (11).
Fix? yes

Couldn't fix parent of inode 1837905: Couldn't find parent directory entry

after searching around a bit I found this blog [http://bitc.bme.emory.edu/~lzhou/blogs/?p=70](http://bitc.bme.emory.edu/~lzhou/blogs/?p=70) describing how to fix the error. I got as far as cd into lost+found and using the command ls -al which displays 
root@ubuntu:/lost+found# ls -al
total 20
drwx------ 2 root root 16384 Mar 30 17:17 .
drwxrwxrwx 1 root root  4096 Mar 30 12:19 ..

Which is nothing like the output mentioned in the blog post. I've got no idea where to go from here.

---

### Post by aplusr on 2013-03-30
Anybody? All my computing needs are hanging in the balance of being able to recover these lost data blocks. 

When I try to type  chown root:root #1837905 it gives me an error like...
root@ubuntu:/lost+found# chown root:root #1837905
chown: missing operand after `root:root'

Could it be because I'm logged in as root?

Here is the original output of the fsck 

/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 1837905: 3072
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
'..' in /lost+found/#1837905 (1837905) is <The NULL inode> (0), should be /lost+found (11).
Fix<y>? yes
Couldn't fix parent of inode 1837905: Couldn't find parent directory entry

Pass 4: Checking reference counts

Pass 5: Checking group summary information

/dev/sda5: ********** WARNING: Filesystem still has errors **********

/dev/sda5: 57156/7790592 files (0.2% non-contiguous), 964555/31162368 blocks

After running 

sudo e2fsck -f -y -v /dev/sda1

e2fsck 1.42.5 (29-Jul-2012)
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 1837905: 3072
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
'..' in /lost+found/#1837905 (1837905) is <The NULL inode> (0), should be /lost+found (11).
Fix? yes

Couldn't fix parent of inode 1837905: Couldn't find parent directory entry

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ********** WARNING: Filesystem still has errors **********


       57156 inodes used (0.73%, out of 7790592)
          66 non-contiguous files (0.1%)
          47 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 12489/12477/12482
             Extent depth histogram: 30947/11/1
      964555 blocks used (3.10%, out of 31162368)
        4220 bad blocks
           7 large files

       27254 regular files
        3769 directories
        6143 character device files
        6210 block device files
        5829 fifos
          20 links
        2028 symbolic links (1983 fast symbolic links)
        5898 sockets
------------
       57151 files

HELP! The last thing I want to do is reinstall the entire computer.

---

### Post by aplusr on 2013-03-31
No one?

---

### Post by dino99 on 2013-03-31
you probably know the actual date; meaning most people are away until Thusday.

Something i dont fully understand about your request:
- /lost+found is a windows folder; so what are you trying to do here with ubuntu ? No one care about that folder anyway. So i doubt about your important data inside :mad:
- if you want to clean your windows system, then run ccleaner

---

### Post by aplusr on 2013-03-31
I dual boot windows 7 and Ubuntu on the same internal HDD. Trying to recover grub boot after gparted live froze halfway through moving/expanding ubuntu partition. 

Using boot repair only boots into windows 7. I need my Ubuntu install back. Here's the output from boot repair.
[http://paste.ubuntu.com/5666209/](http://paste.ubuntu.com/5666209/)

Didn't even think about easter. Guess it explains the lack of responses.


Edit: Boot repair doesn't even detect Ubuntu or grub. Both options are greyed out.

---

### Post by aplusr on 2013-03-31
Ran gparted again. Lost+found seems to be the problem. 

GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
 [TABLE]
 [TR]
 [TD="colspan: 2"] **Check and repair file system (ext4) on /dev/sda5**  00:00:10    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] calibrate /dev/sda5  00:00:00    ( SUCCESS ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]path: /dev/sda5
start: 1,535,352,832
end: 1,932,670,975
size: 397,318,144 (189.46 GiB)[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] check file system on /dev/sda5 for errors and (if possible) fix them  00:00:09    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] ***e2fsck -f -y -v /dev/sda5*** [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 1837905: 3072
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
'..' in /lost+found/#1837905 (1837905) is <The NULL inode> (0), should be /lost+found (11).
Fix? yes

Couldn't fix parent of inode 1837905: Couldn't find parent directory entry

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ********** WARNING: Filesystem still has errors **********


       57156 inodes used (0.73%, out of 7790592)
          66 non-contiguous files (0.1%)
          47 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 12489/12477/12482
             Extent depth histogram: 30947/11/1
      964555 blocks used (3.10%, out of 31162368)
        4220 bad blocks
           7 large files

       27254 regular files
        3769 directories
        6143 character device files
        6210 block device files
        5829 fifos
          20 links
        2028 symbolic links (1983 fast symbolic links)
        5898 sockets
------------
       57151 files
[/I] [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] [I]e2fsck 1.42.5 (29-Jul-2012)
[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 ========================================

---

### Post by faucets xp on 2013-03-31
The installing mirror image is not complete. You may try downloading another one

xp
partner of [http://faucetsexpert.com/](http://faucetsexpert.com/)

---

### Post by aplusr on 2013-03-31
> **faucets xp said:**
> The installing mirror image is not complete. You may try downloading another one

xp
partner of [http://faucetsexpert.com/](http://faucetsexpert.com/)

Which mirror image? Ubuntu?

Can you explain?

---

### Post by aplusr on 2013-04-04
Guess I'll have to take it to my local repair shop. Hope they will be able to recover my data at the very least.

---

### Post by schragge on 2013-04-04
> **aplusr said:**
> I got as far as cd into lost+found and using the command ls -al which displays
```
root@ubuntu:/lost+found# ls -al
total 20
drwx------ 2 root root 16384 Mar 30 17:17 .
drwxrwxrwx 1 root root  4096 Mar 30 12:19 ..
``` */lost+found* folders are created in the root directory of every partition. Perhaps you are looking at the wrong place. Where is */dev/sda5* mounted? Check the output of
```
sudo blkid -o list -c /dev/null /dev/sda5
```

> **aplusr said:**
> When I try to type  chown root:root #1837905 it gives me an error like...
```
root@ubuntu:/lost+found# chown root:root #1837905
chown: missing operand after `root:root'
```
Could it be because I'm logged in as root?This is because the bash shell has option *interactive_comments* set by default and ignores anything that comes after #. You can quote # by prepending it with a backslash like this ```
chown root: \#1837905
```
But I suspect the command would have no effect anyway as the *lost+found* directory where you were trying it doesn't contain the file *#1837905*.

---

