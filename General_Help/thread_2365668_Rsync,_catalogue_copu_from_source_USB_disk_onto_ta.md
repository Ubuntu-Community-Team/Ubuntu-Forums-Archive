---
title: "Rsync, catalogue copu from source USB disk onto target USB disk."
date: 2017-07-09
forum: General Help
---

### Post by smithbox on 2017-07-09
Hello everyboday.
I, am going to copy catalogue " 1Windows" from USB disk /dev/sdc device /dev/sdc1 onto USB disk /dev/sdb device /dev/sdb1.
```
Disk /dev/sdb: 1.8 TiB, 1999664930816 bytes, 488199446 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C9F84354-B814-4222-A80A-52FAF80268F1

Device     Start       End   Sectors  Size Type
/dev/sdb1    256 488199167 488198912  1.8T Linux filesystem


Disk /dev/sdc: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0EBC06E1-5858-9090-8081-828310111213

Device     Start        End    Sectors  Size Type
/dev/sdc1     63 7801475915 7801475853  3.6T Microsoft basic data
```
The problem is the command, I never done it before and can not afford loose data.
```
Rsync -r / media / mike / Seagate / -1Windows / /media / mike / Back1 / -1Windows
```
Seagate = source
Back1    = target.
I would appreciate if someone more experienced, confirm that given above  command will work god for me and copy all possible files and catalogues  from sdc1 onto sdb1.
Regards.
Mark

---

### Post by The Cog on 2017-07-09
I assume that you have the drives mounted in /media/mike and they have the names Seagate and Back1, and you wnat to copy from Seagate to Back1. 
Your posted command has several problems.
1: The program rsync does not start with a capital R. Linux is case sensitive
2: The spaces round the slashes have to go. There should only be a space between the two arguments - the source path and destination path
3: You say the you want to copy "1Windows" but the command you posted names -1Windows with an extra - sign in front.

The command you posted, when fixed, should look like this:
```
rsync -r /media/mike/Seagate/1Windows/ /media/mike/Back1/1Windows
```
but that still has problems.
1: The trailing / on the source /media/mike/Seagate/1Windows/ implies that you want to copy everything in that directory, not copy the directory itself. Which would work if the quoted destination /media/mike/Back1/1Windows already existed and was a directory. But the destination directory 1Windows probably doesn't already exist in Back1 so I think the command would fail with a no such file/folder error/.

I would have used this command:
```
rsync -r /media/mike/Seagate/1Windows /media/mike/Back1/
```
In this command, the source is /media/mike/Seagate/1Windows which is the name of the directory you want to copy. We have dropped the trailing slash, so now 1Windows itself will be copied instead of just all its contents. The -r (recursive) flag says that the contents must also be copied. The destination /media/mike/Back1/ says that 1Windows must be copied **into** the directory Back1 (the trailing slash says that Back1 must be a directory: without the trailing slash Back1 could have been a regular file to be overwritten).

There is no danger of losing data here because the command does not delete anything in 1Windows. The worst danger is failure to copy the data. 

Your destination drive is half as big as your source drive. Are you sure it is big enough to hold everything you want to copy? 
As a check that everything was copied, you can try these two commands to print the total file sizes of the two directories, and they should give the same answer:
```
du -sb /media/mike/Seagate/1Windows
du -sb /media/mike/Back1/1Windows
```
Hope this helps.

---

### Post by smithbox on 2017-07-10
@The Cog.
I,am very, very grateful for your extensive and professional answer.
This is it, what I exactly needed.
If you allow, last one question.
Command final shape if I:
- will see copy operation progres.
- have on device sdc1 - 5 different directories, like:
   - - 1Windows
   - - 2Linux
   - - 3Unix
   - - 4BSD
   - - 5MacOS

---

### Post by The Cog on 2017-07-10
You are welcome.
To copy all the contents of Seagate to Back1, I would do this:
```
rsync -r /media/mike/Seagate/ /media/mike/Back1/
```
This says copy everything inside the Seagate folder into the Back1 folder.
If you have already copied 1Windows, then rsync will not copy it again - it will know from the file size and timestamp that the file is already there. Using rsync even on big directory trees is very fast when little has changed.

Again, beware that the backup disk is smaller than the source disk.

You can use the Thread Tools menu at the top of the page to mark the thread solved.

---

