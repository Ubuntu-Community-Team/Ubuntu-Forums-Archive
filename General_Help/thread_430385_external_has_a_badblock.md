---
title: "external has a badblock"
date: 2007-05-02
forum: General Help
---

### Post by raffytaffy on 2007-05-02
my external hard drive seems to have a badblock 1. its a ext3 file system. How do i run the commend badblocks to fix this? I mean whats the exact command i need to input when its /dev/sda1. ?
also if it does find the badblock. ( which im pretty sure a pop up stated bfre..i cant recall where or when) what do i need to do? how would i run a low level format on an external hard drive?
im also confused as how to use the results frm badblocks in e2fsck. im reading the man pages for both programs and it says something about using the result from badblocks in e2fsck. how is this done exactly?

i decided to try to fix on my own. i did sudo e2fsck -p -v /dev/sda1

the output i got said i had no bad blocks... some non contigous files and i was missing a "lost and found" folder..which was made. then i rebooted and now the HD seems to mount via fstab. im not sure if anything was actually fixed, or what. i will monitor this HD closesley. and i was thinking of making it "0     1" in fastab to check it every 30 mounts? is this a good idea guys?

---

### Post by Herman on 2007-05-13
You could do that, or run a file system check manually with a Live CD, make sure you don't mount the file system first, that's all.
Here's a command I made up from looking at the output from 'man e2fsck', this is for when you suspect there might be bad blocks,
```
sudo e2fsck -c -c -k -v /dev/sda1
```Where: your external hard disk's partition to be checked comes up as 'sda1' in the output from 'sudo fdisk -lu', and has an ext3 filesystem.>  -c     This option causes e2fsck to use badblocks( 8) program to do a read-only scan of the device in order to find
              any bad blocks.  If any bad blocks are found, they are added to the bad block inode to  prevent  them  from
              being allocated to a file or directory.  If this option is specified twice, then the bad block scan will be
              done using a non-destructive read-write test.>  -k     When combined with the -c option, any existing bad blocks in the bad blocks list are preserved, and any new
              bad blocks found by running badblocks(8) will be added to the existing bad blocks list.
 > -v     Verbose mode.That command should be good for what it is you are trying to do. I would be interested in any comments on this so I can learn more.


                                            
Here's another command just for a regular ordinary everyday file system check that I like,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` Where: your external hard disk's partition to be checked  comes up as 'sda1' in the output from 'sudo fdisk -lu', and has an ext3 filesystem.
> -C fd  This option causes e2fsck to write completion information to the specified  file  descriptor  so  that  the
              progress  of  the  filesystem  check can be monitored.  This option is typically used by programs which are
              running e2fsck.  If the file descriptor specified is 0, e2fsck will print a completion bar as it goes about
              its business.  This requires that e2fsck is running on a video console or terminal.
 > -p     Automatically repair ("preen") the file system.  This option will case  e2fsck  to  automatically  fix  any
              filesystem  problems  that  can  be safely fixed without human intervention.  If e2fsck discovers a problem
              which may require the system administrator to take  additional  corrective  action,  e2fsck  will  print  a
              description  of  the  problem  and then exit with the value 4 logically or’ed into the exit code.  (See the
              EXIT CODE section.)  This option is normally used by the system’s boot scripts.  It may not be specified at
              the same time as the -n or -y options.>  -f     Force checking even if the file system seems clean.
>  -v     Verbose mode. Do you like those? I think they should be okay, I use the second one sometimes, I have tested the first one  a few times myself, but since I don't have any problem to begin with, I can only presume that it works. If you try it, let me know how you get along.
Regards, Herman :)

---

### Post by majorlacko on 2007-05-20
Hi!
I have a similar problem. Mine is a WD Essential 250GB HDD but I did not format it from FAT32 to ext3 because I thought it doesn't necessary. So I was wrong after copied about 160GB to the HDD from two PC but both of them was Linux: Fc6 and Ubuntu 6.10. Now I use Feisty of course on them. So I1d like to ask something about solution if its not too late. I removed three win apll. and even lost and found. Now the unit only start and click twice. There is nothing on the screen. I tried to format as a simple HDD but no any success, even Debian or Slackware. Now, as I see Your solution(s) there's only one question I have. Does it works on an unformatted disk? I really don't care any file on this HDD, I just would like to rescue a new HDD if it's possible. 
Thanks and excuse me for my very "foreign" english :)

---

### Post by Herman on 2007-05-21
I think you mean you have a [Western Digital Essential Edition 250 GB external USB hard drive]("http://www.wdc.com/en/products/products.asp?DriveID=218"). You left it formatted with it's original FAT32 file system rather than converting to ext3 even though you are a Linux user. You had about 160 GB of data saved on it when you deleted some files you didn't think were important. 
After that I'm not sure what you mean. 
The disk won't start anymore? 
Or it does start but you can't 'see' any of your files?

Then you tried to format it in Debian and Slackware to just make it into an ordinary external hard drive but it still doesn't work.

Here's a CNET review on it, [http://www.cnet.com.au/desktops/storage/0,239029473,240091204,00.htm?type=pop](http://www.cnet.com.au/desktops/storage/0,239029473,240091204,00.htm?type=pop)

What I am worried about is whether those strange files you deleted were part of some software that is vital to the operation of the hard disk? It seems unlikely.

To answer your question, no, these commands will not do anything if there is no file system in your disk to be checked.
They will only work when you have an ext3 file system in a partition in the hard disk. If you have an unformatted hard disk you need to make a partition and a file system in it. I always use a [GParted -- LiveCD]("http://gparted.sourceforge.net/") to do that. For most external usb hard disks you can delete all the files that come with the hard disk that are only good for Windows. If you are a Linux user you don't need them. That's what I always do. Then I make a partition and a filesystem with GParted LiveCD and that's it! It should work.
I don't know if your WD Essential 250GB HDD had any special software on the hard disk that would be vital to the operation of the hard disk itself. If it did, you would need to contact Western Digitai and ask them about how to fix it. But I think it will probably work if you just format it with ext3 with GParted LiveCD.
Regards, Herman :D

---

