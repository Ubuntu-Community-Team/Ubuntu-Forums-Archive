---
title: "Phantom file"
date: 2013-01-01
forum: General Help
---

### Post by PinkFloyd102489 on 2013-01-01
Hello,

I have a file (which is supposed to be a directory) that is showing up with ls and also in Nautilus, but I cannot delete it. I have tried deleting it from the GUI, with rm -rf, and even switching to root. All I get is "No such file or directory" but I can still see it.

```
brandon-mint Waiting # ls -al
total 9
drwxrwxrwx 1 root root 4096 Jan  1 11:03 .
drwxrwxrwx 1 root root    0 Nov  1 15:59 ..
-rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
drwxrwxrwx 1 root root 4096 Nov 21 15:48 Hyundai
drwxrwxrwx 1 root root    0 Dec 13 10:39 Mazda
```

The "3KI1344" is the one that needs to be removed. I tried another method, thinking it may be a corrupt file. Initially, the file size of the phantom file was "1842892". I created a test file with some text and cp'd it to the phantom file, which reduced the file size, but it still exists and cannot be removed.

Any help with this would be appreciated. :)

---

### Post by dino99 on 2013-01-01
so you get : KIA, Hyundai & Mazda

that kia folder have not the same right (d missing), so a little:

sudo chmod 777 thatfoldername

---

### Post by rnerwein on 2013-01-01
> **PinkFloyd102489 said:**
> Hello,

I have a file (which is supposed to be a directory) that is showing up with ls and also in Nautilus, but I cannot delete it. I have tried deleting it from the GUI, with rm -rf, and even switching to root. All I get is "No such file or directory" but I can still see it.

```
brandon-mint Waiting # ls -al
total 9
drwxrwxrwx 1 root root 4096 Jan  1 11:03 .
drwxrwxrwx 1 root root    0 Nov  1 15:59 ..
-rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
drwxrwxrwx 1 root root 4096 Nov 21 15:48 Hyundai
drwxrwxrwx 1 root root    0 Dec 13 10:39 Mazda
```The "3KI1344" is the one that needs to be removed. I tried another method, thinking it may be a corrupt file. Initially, the file size of the phantom file was "1842892". I created a test file with some text and cp'd it to the phantom file, which reduced the file size, but it still exists and cannot be removed.

Any help with this would be appreciated. :)
hi
if i see the permissions of your files and dirs then i think it's windoz filesystem ????
cheers

---

### Post by PinkFloyd102489 on 2013-01-01
> **rnerwein said:**
> hi
if i see the permissions of your files and dirs then i think it's windoz filesystem ????
cheers

Indeed it is. It's an NTFS partition that I share between my Linux and Windows installations. I work primarily in Linux but I am required to use some Windows programs from time to time.

---

### Post by bobnn on 2013-01-01
try 

ls -alb

to see any possible non-printing characters in the filename.  

for example I did:

```

$ touch 'test '
$ ls -al test
ls: cannot access test: No such file or directory
$ ls -al test*
-rw-rw-r-- 1 bobn bobn 0 2013-01-01 14:40 test 
$ ls -alb test*
-rw-rw-r-- 1 bobn bobn 0 2013-01-01 14:40 test\ 

```

The \ character shows that there is something else at the end of the filename, in this case a space.

---

### Post by PinkFloyd102489 on 2013-01-01
```
brandon@brandon-mint ~/work/New/Waiting $ ls -alb
total 9
drwxrwxrwx 1 root root 4096 Jan  1 11:12 .
drwxrwxrwx 1 root root  240 Jan  1 11:12 ..
-rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
drwxrwxrwx 1 root root 4096 Nov 21 15:48 Hyundai
drwxrwxrwx 1 root root    0 Dec 13 10:39 Mazda
```

---

### Post by rnerwein on 2013-01-02
> **PinkFloyd102489 said:**
> ```
brandon@brandon-mint ~/work/New/Waiting $ ls -alb
total 9
drwxrwxrwx 1 root root 4096 Jan  1 11:12 .
drwxrwxrwx 1 root root  240 Jan  1 11:12 ..
-rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
drwxrwxrwx 1 root root 4096 Nov 21 15:48 Hyundai
drwxrwxrwx 1 root root    0 Dec 13 10:39 Mazda
```
hi
your ls -al output: -rwxrwxrwx[COLOR=Red] 2[/COLOR] root root    6 Jan  1 11:02 3KI1344
the fifth field ! (number 2) of your ls command disorient me.
this field specifies the number of links or directories inside this directory.
try: ls -ali 
cd ..
ls -ali
post the output.
or try: rm *3KI1344*
cheers

---

### Post by PinkFloyd102489 on 2013-01-02
> **rnerwein said:**
> hi
your ls -al output: -rwxrwxrwx[COLOR=Red] 2[/COLOR] root root    6 Jan  1 11:02 3KI1344
the fifth field ! (number 2) of your ls command disorient me.
this field specifies the number of links or directories inside this directory.
try: ls -ali 
cd ..
ls -ali
post the output.
or try: rm *3KI1344*
cheers

rm command did not work.

Output of ls -ali:
```
6678 -rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
```

From directory above:
```
brandon@brandon-mint ~/work/New $ ls -ali
total 12
2336 drwxrwxrwx 1 root root    0 Jan  1 11:12 .
2259 drwxrwxrwx 1 root root 4096 Dec 17 14:14 ..
2387 drwxrwxrwx 1 root root 4096 Jan  1 10:54 2013
2388 drwxrwxrwx 1 root root 4096 Jan  1 17:44 Waiting

```

---

### Post by rnerwein on 2013-01-04
> **PinkFloyd102489 said:**
> rm command did not work.

Output of ls -ali:
```
6678 -rwxrwxrwx 2 root root    6 Jan  1 11:02 3KI1344
```From directory above:
```
brandon@brandon-mint ~/work/New $ ls -ali
total 12
2336 drwxrwxrwx 1 root root    0 Jan  1 11:12 .
2259 drwxrwxrwx 1 root root 4096 Dec 17 14:14 ..
2387 drwxrwxrwx 1 root root 4096 Jan  1 10:54 2013
2388 drwxrwxrwx 1 root root 4096 Jan  1 17:44 Waiting

```
hi
i thougt it's a inode link with the directory ( reference 2).
the only way to solve this misterouse behavior i think run chkdsk from windoz.
there must be the problem.
good luck
cheers

---

### Post by Calinou on 2013-01-04
Slightly irrelevant, but: [http://sf.net/projects/ext2fsd](http://sf.net/projects/ext2fsd)
This makes reading and writing ext2/ext3/ext4 partitions possible on Windows.

---

