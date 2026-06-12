---
title: "Can't update - can't install - can't repair - can't find source of problem!"
date: 2014-01-03
forum: General Help
---

### Post by freebird54 on 2014-01-03
On my main machine (32-bit 12.04) I have run into an intractable problem with updates.  For the second time, the package system has apparently decided to break.

Attempts to Repair the damage fail - attempts to "-f install" fail - and attempts to follow up the clues about the source of the problem have been unsuccessful.  Partial output of a Repair follows:

```

|
|
|
(Reading database ... 470280 files and directories currently installed.)
Unpacking linux-image-3.2.0-57-generic-pae (from .../linux-image-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-57-generic-pae_3.2.0-57.87_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-57-generic-pae/kernel/drivers/input/ff-memless.ko.dpkg-new' (while processing `./lib/modules/3.2.0-57-generic-pae/kernel/drivers/input/ff-memless.ko'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
|
|
|

```

This would suggest that space has run out somewhere - but I can't seem to find anywhere with space problems.  This should be simple - and I have never run into problems with Ubuntu (Debian) packaging before - but it seems to have defeated me for the moment.  Sheer irritation led me to a re-install from scratch once (whereupon it reappeared in about a month) but it isn't worth **that** much effort if it doesn't **STAY** fixed.

Any help out there?  Additional places to look?  Do I resize partitions even if no space restrictions are seen?  Am I looking in the right places for those space restrictions?  Is the complaint about out of space irrelevant?

Thanks in advance.....

---

### Post by ajgreeny on 2014-01-03
Can we see the output from ```
sudo fdisk -l
df -hT
``` one by one, please.

---

### Post by freebird54 on 2014-01-03
Working on 2 systems here...

```
freebird@aerie:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda9      ext4      7.4G  5.9G  1.2G  84% /
udev           devtmpfs  2.0G  4.0K  2.0G   1% /dev
tmpfs          tmpfs     793M  892K  792M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.0G  520K  2.0G   1% /run/shm
/dev/sda5      ext4      106G   65G   36G  65% /home
/dev/sdc1      fuseblk   932G  191G  742G  21% /media/Iomega HDD
/dev/sdb1      fuseblk   1.9T  344G  1.5T  19% /media/Expansion Drive

```


and
```

freebird@aerie:~$ sudo fdisk -l
[sudo] password for freebird: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f254d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sda2   *     3903795    19535039     7815622+  83  Linux
/dev/sda3        19535040   224411984   102438472+  83  Linux
/dev/sda4       224412109   976771071   376179481+   5  Extended
/dev/sda5       752046080   976771071   112362496   83  Linux
/dev/sda6       224412111   240043229     7815559+  83  Linux
/dev/sda7       240044032   256043007     7999488   83  Linux
/dev/sda8       256045056   736417791   240186368   83  Linux
/dev/sda9       736419840   752033791     7806976   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7cfdf51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024127  1953512032+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc487ffe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001    7  HPFS/NTFS/exFAT
```


Nothing looks to me to be overflowing - but I don't really know the space requirements for apt-get operations...

Thx

---

### Post by Impavidus on 2014-01-03
And ```
df -i
``` please. You could have run out of inodes.

---

### Post by freebird54 on 2014-01-03
Ok - I copied from the other system, so only the most relevant info made it :)

```

Filesystem         Inodes  IUsed      IFree IUse% Mounted on
/dev/sda9         488640  485271       3369  100%  /

```

hmm- looks a little tight - even if I know nothing about it...

---

### Post by ian-weisser on 2014-01-03
Your file system index (inodes) is full (~100%). You can't add any more files.
You can store up to 488,640 files, directories, sockets, and links in that filesystem. And you are.

Using up inodes is rare. My system partition, for comparison, is 85% space used, but only 4% inodes used.
Do you have some application that generates lots of links? Or lots of mostly-empty directories?

---

### Post by freebird54 on 2014-01-03
Sure looks that way!  I haven't seen that since...hmmm... 1994 on TAMU (Texas A&M Linux w/Motif) ?  Never crossed my mind.  Nothing I KNOW of does that - so it's probably something running amok!

I researched a bit (now that you steered me to the find!) and I'll be running a 'count' script to locate the problem - and hopefully fix it.  I'll post results here (and mark SOLVED if it is) after that.

Thank you, thank you, thank you!  It is the conception of the problem that usually allows solution....

---

### Post by Impavidus on 2014-01-03
Old kernel headers maybe? There could be a large population of those living in /usr/src/linux-headers-<some version>. Remove some files (a few tens of thousands or so), fix the package manager and uninstall them using the package manager. They belong to linux-headers-<some version>.

---

### Post by freebird54 on 2014-01-05
I got the inodes count back under control (46%) by removing src/include (hopefully that shouldn't cause too many repercussions) - and **tried** to fix the package system - unsuccessfully!  I still have errors when trying to get the package system fixed - and can't install anything.

I have dependency errors
```

dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-56-generic-pae; however:
  Package linux-image-3.2.0-56-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-54-generic-pae; however:
  Package linux-headers-3.2.0-54-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.54.64); however:
  Version of linux-image-generic-pae on system is 3.2.0.56.66.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                                 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.54.64); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-pae
 linux-headers-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

which I don't know how to rid myself of.  Currently can't even get the software centre or the update manager to run.  Still trying though!

---

### Post by Impavidus on 2014-01-05
Did you try **sudo apt-get -f install**?

---

### Post by lsutiger on 2014-01-05
I am having the same exact problem. I tried to remove a lot of the /usr/src files, but the inodes are still at 100% use. Any other steps I should try to resolve? I tried to repair the package manager after emoving the old kernel files, same results.

Thanks for any suggestions.

---

### Post by ian-weisser on 2014-01-05
> **freebird54 said:**
> 
```

dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on [COLOR=#ff0000]linux-image-3.2.0-56-generic-pae[/COLOR]; however:
  Package linux-image-3.2.0-56-generic-pae is not installed.
[...]

Errors were encountered while processing:
 linux-image-generic-pae
 linux-headers-generic-pae
 linux-generic-pae


```

Look at that version number, and compare it to this one:
```
$ rmadison -u ubuntu linux-image | grep precise-updates linux-image | [COLOR=#ff0000]3.2.0.58[/COLOR].69  | precise-updates  | amd64, i386


```

See the difference? This problem has festered long enough that the kernel has incremented twice. The package manager doesn't know that, it simply knows that you don't have -56 installed anymore. 

Try reinstalling those three kernel metapackages. They should magically reset to the correct dependencies.
```
sudo apt-get install --reinstall  linux-image-generic-pae linux-headers-generic-pae linux-generic-pae
```

---

### Post by freebird54 on 2014-01-05
Still left with a difficulty - as seen here:
```

freebird@aerie:/var/lib/dpkg$ sudo apt-get install --reinstall  linux-image-generic-pae linux-headers-generic-pae linux-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-image-generic-pae is not possible, since it cannot be downloaded.
Reinstallation of linux-headers-generic-pae is not possible, since it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.58.69) but 3.2.0.58.88 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.58.69) but 3.2.0.58.88 is to be installed
E: Unable to correct problems, you have held broken packages.


```

Apparently that opening is closed off.  I did try something that is in the same line, and stopped the error messages - I edited the status file in **/var/lib/dpkg** so that the latest kernal ID replaced the 'old' versions being called for from the error messages. As I mentioned - it appeared to work (however ill-advised!).  Unfortunately, the 'No Entry' logo remains on the top bar, and Software Centre and Update Manager still refuse to load.  Does anyone know their 'real' names/ - so I can try to run them from the CLI and get error messages?

Thanks for any further ideas.... (yes, I know I could re-install from scratch again :) )

---

### Post by freebird54 on 2014-01-05
OK - I think I have this finalized and functional...so here's a recap of the moves that got made.

1. Original problem - broken packages (lack of space)

2. Someone pointed out that inodes could run out - they had

3. Tried to find source of "many small files" that ate up the inode allocations (used **count_em** script
```

#!/bin/bash
# count_em - count files in all subdirectories under current directory.
echo 'echo $(ls -a "$1" | wc -l) $1' >/tmp/count_em_$$
chmod 700 /tmp/count_em_$$
find . -mount -type d -print0 | xargs -0 -n1 /tmp/count_em_$$ | sort -n
rm -f /tmp/count_em_$$

```
to help locate them)

4. Deleted /usr/include - which reduced the ***df -i*** inode usage report from 100% to 46% (but had other consequences)

5. ***apt-get -f*** still not capable of fixing all problems - took the chance of editing **/var/lib/dpkg/status** to change version numbers to those which I actually had on board. It stopped the package errors, by some miracle (no idea if it was dangerous or not - probably was :) ).

6. Still had blocked access to Update Manager and Software Centre - figured out that update-manager was the name to test run from the CLI.  Errors let me know that I broke Python by wiping out the include directory earlier!

7. Was able to ***sudo apt-get -f install Python2.7*** to fix Python - whereupon Update Manager could run properly at last.

8. When Update Manager ran, it started "fresh" and updated all 180 things on here - and NO ERRORS.  Everything appears OK again.

9 - CONCLUSION to be drawn:  DON'T try to run a 'hobby' system with such a small root partition!  No need for it these days, and it is dangerous to your inode allocation!  Hope this adventure gets someone else on their way to a smooth runner again.

Thanks to all who had suggestions/pointers/thoughts - they all helped!

---

