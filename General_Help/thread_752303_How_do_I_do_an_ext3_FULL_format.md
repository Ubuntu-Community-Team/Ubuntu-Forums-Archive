---
title: "How do I do an ext3 FULL format?"
date: 2008-04-11
forum: General Help
---

### Post by Holonet on 2008-04-11
Just that...how do you do a full format of any sort in Linux?  I know from how fast it does this during installation that it is doing the quick format.  This is not a problem, but I would like to know how to do the full format.  Hate to see an "option" which Windows has and Linux does not.

I admit for me, it's just a meaningless peace of mind that sometimes when I start fresh, I like to wipe the data...but this does have practical use.  Let's say I'm a developer and I'm testing my undelete software--need to be able to wipe data, and multiple times.

---

### Post by Koybe on 2008-04-11
Uh... clean your partitions then ;-)

Seriously, you shouldn't compare NTFS/FAT and ext3 or whatever you use in linux. There is nothing in common. 
Anyway to simply format, use mkfs.ext3 for ext3 partition.
```
mkfs.ext3 /dev/sda2
```

original command would be
```
mke2fs -j /dev/sda2
```

---

### Post by bingoUV on 2008-04-11
Your example use case can be solved by shred. 
```

shred -z -f -n 1 <device id>

```

It overwrites all data on the device. After this, you can use mkfs (or whatever GUI tool you prefer) to format the device to ext3. 

Remember that "full"format can mean anything. If you know exactly what microsoft does when you ask it for a "full" format, tell it here so that we will be able to provide a way to doing it for ext3.

---

### Post by Holonet on 2008-04-11
Thanks for the reply, but I'm not sure I understand it.  I didn't mean to compare the file systems' characteristics in any way.  I realize they are very different...but um...I still thought the principle of writing 0s to wipe the data still applied.  Is this incorrect?  I just can't picture the hard drive physically wiping the data so fast.  Blah, I'm not making much sense anymore.  So I guess I just don't understand what these vast differences are...so let me modify the question a bit:

When installing Windows XP, you are given the option to leave the fliesystem in tact, format, or format (quick).  As I understand it, format (quick) just rewrites the file allocation tables, etc...but the regular format writes 0s to every sector, actually wiping the *data* instead of just the file system.

If I'm messed up there, do tell me hehe... but assuming that's at least reasonably accurate, is there a parallel concept on an ext3 partition, or do I have to change how I think about this entirely?

---

### Post by Koybe on 2008-04-11
OK, you can use dd too.
Be very careful, do not use this command without knowing what you do. It will erase everything and put zero on the entire partition :
**```
dd  if=/dev/zero  of=/dev/yourpartition**
```

---

### Post by Tuna-Fish on 2008-04-11
If what you want to do is to clear all the data from the drive so it cannot be recovered, shred does exactly what you want. Also, overwriting the drive with 0's is not good enough when the drive contents are really valuable, because the data usually can still be recovered by professionals. The guidelines for secure data removal is overwriting with random data (not just ones and zeroes) for 20 times or so. Shred does this, with proper arguments. Try "man shred" in terminal for instructions.

---

### Post by Therion on 2008-04-11
I'm going way out on a limb here and going by some pretty distant memory... But assuming it's correct, when you use the format command in MS Windows, you are in fact performing what is often referred to as a "low level format" but is, in point of fact, a disk *reinitialization*; which is nothing more than adding control information such as track and sector numbers, to enable the stored data to be accessed correctly by the drive.

Writing (a zero, for instance) to each and every sector of the drive is, as I recall, properly referred to as a "zero-fill" operation. I remember having to use a specific parameter with the Windows "format" command to perform a zero-fill. 

But again, I'm going by memory and it's quite likely the the technology itself has progressed and changed everything.

---

### Post by bingoUV on 2008-04-11
yes, shred will write your zeros for you. Then you can format as you wish.

---

### Post by Holonet on 2008-04-11
Ok that helps, I'm clearer now.  I realize the 0 method wouldn't make data irrecoverable.  Shred sounds useful indeed...makes me have another question though.  Is it possible to shred (or zero fill, etc...) only the free space?  This would have benefits if someone wanted to delete something with personally identifiable information or the like.  I think it would also be a nice option to put in while formatting during installation.  Heck, actually, it would be great to integrate this into the GUI...say delete is trash, shift delete is really delete it, and something else, say ctrl+shift+delete is shred the file.  Maybe I should visit the development section again \\:D/

---

### Post by louieb on 2008-04-11
> **Holonet said:**
> ...but um...I still thought the principle of writing 0s to wipe the data still applied.  Is this incorrect?  ....

The difference is the development strategy. In windows a lot of programs tend to be an all in one swiss army knife.     

In Unix/Linux the approach to development is different. Programs  for the most part and written to do one thing and do it well. In the case of a full vs quick format. In Linux you run a program like shred or use the  dd command to wipe the drive, partition, file, or whatever. and use cfdisk, or fdisk, or one of the parted family of programs partition it, and finally one of the format programs such mk2fs to create  the file system. 

As an example say you want to  list the hardware on your machine. so you run **lshw** the listing flies  by  - you can't read it. So you need a pager. 

IF you pipe the lshw output to the pager less: ** lshw | less ** you can use the page up, page down, and arrow keys to scroll through the listing.   

Each program does one thing.  IF you wanted to make a wrapper script or program (swiss army knife)  to run one program after the other - you could do that too.

---

### Post by cdenley on 2008-04-11
> 
Is it possible to shred (or zero fill, etc...) only the free space?


```

sudo apt-get install secure-delete
sudo sfill /

```

I think incorporating these functions into the GUI for a default install is a bad idea. It takes a long time to overwrite a large file 25 times (shred's default). Too many people would complain that when they use it, it takes all day to finish. It should only be used by paranoid people who know what they're doing.

I do think they should support encryption on the livecd installer. If you have such sensitive information, you shouldn't be writing it to a hard drive unencrypted. If the data is encrypted, you don't have to be too concerned about erasing it.

The way ext3 works is a good compromise of usability and security. It doesn't erase the file's actual data, but it erases the metadata about the file (including file name/path), making it a little more difficult to recover deleted files without taking much longer.

---

### Post by Holonet on 2008-04-11
> **cdenley said:**
> ```

sudo apt-get install secure-delete
sudo sfill /

```

I think incorporating these functions into the GUI for a default install is a bad idea. It takes a long time to overwrite a large file 25 times (shred's default). Too many people would complain that when they use it, it takes all day to finish. It should only be used by paranoid people who know what they're doing.


A good point, however I think requiring two buttons held down first, with the addition of an appropriate confirmation dialogue that warns of this issue would address this problem.  It's true it should not commonly be necessary, but I think it fits in with the spirit of a Linux machine--in that if you want to do something in Linux, you can do it.  It does this very well now, but not with the facility necessary to say "not only does it do this, but it's just as easy as if you were in Windows."  At the very least, I think this type of thing should be an option, and/or scripts like this be downloadable via Synaptic.

---

### Post by ezsit on 2008-04-11
I think people have gotten off track here. A "full format" in DOS/Windows does not do any type secure deletion as some posters have suggested. Disk wiping is something totally different and seperate from formatting. 

A DOS/Windows "full format" (the one that takes longer to complete) is simply a format and checking for bad blocks. I believe that the Ubuntu installer, during the advanced partitioning phase within one of the dialog boxes will give you the option of "checking for bad blocks" and this will take a long time on larger hard drives.

The command line to format and check for bad blocks would look something like this:

mkfs.ext3 -c /dev/sda1

The -c flag tells the mkfs.ext3 command to check for bad blocks and will take longer. Do man mkfs.ext3 to find the many other options.

---

### Post by Holonet on 2008-04-11
Ah swell, yes, that makes sense....and realizing data could be recovered after 0s are written, I was, indeed, searching for just why one would do that format procedure.  However, I do not recall that option to check for bad blocks when installing Ubuntu, but then again, I wasn't looking too hard, I may have just missed it.  I always use manual partition when installing.

We were getting off topic a bit, but not knowing that purpose for the original "full" format, my curiosity had been satisfied, and I think the tangent is worth discussing, but like I said, maybe in the development section.

---

