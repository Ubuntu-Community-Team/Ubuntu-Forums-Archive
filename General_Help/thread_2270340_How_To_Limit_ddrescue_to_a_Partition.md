---
title: "How To Limit ddrescue to a Partition?"
date: 2015-03-22
forum: General Help
---

### Post by johny why on 2015-03-22
hi

this image from gparted shows the first sector and last sector of the partition i want to recover. 

how can i translate those numbers into ddrescue parameters -s and -i? do i need to divide by 8 (a byte) or by 512 (sector size)?

thx!

[ATTACH=CONFIG]260823[/ATTACH]

[ATTACH=CONFIG]260824[/ATTACH]

---

### Post by bardo2 on 2015-03-23
good question. answer (from man ddrescue): <in bytes>
whereas parted gives sectors, which used to be 512 bytes in the old days, more and more advances format drives are in use, where a sector has 4096 bytes. so no dividing... more like multiplier necessary

As a side note: since you are comfortable using RAID, why not make the output file sparse?

---

### Post by bardo2 on 2015-03-23
Sorry, i missed to answer your question: just use the partition (sda4) instead of the whole disk as input to ddrescue. In linux, everything is seen as a file, even those block devices can be regarded as being files.

---

### Post by johny why on 2015-03-23
> **bardo2 said:**
> use the partition (sda4) instead of the whole disk as input to ddrescue.

tried already, didn't work. i think the partition is too damaged. Plz see the gparted screenshot in the OP. 

that's exactly why i want to enter the specific locations using ddrescue start-position option.

---

### Post by johny why on 2015-03-23
> **bardo2 said:**
> good question. answer (from man ddrescue): <in bytes>
whereas parted gives sectors... so no dividing... more like multiplier necessary

my drive is 512 sector size. Therefor, 512 x 2721792 = 1393557504

and for the ddrescue -s option: 512 x 580456448 = 297193701376

If the above is correct, we'd do:

ddrescue -i 1393557504 -s 297193701376 /dev/sda /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

Is -s the correct parameter to specify input size? The ddrescue manual says **"Maximum size of the rescue domain, in bytes. It limits the amount of input data to be copied." **So i'm not sure if that means *number of bytes to TRY to copy, *or *number of bytes to ACTUALLY copy* (minus the bad data that could not be copied). 

> As a side note: since you are comfortable using RAID, why not make the output file sparse?

My understanding of ddrescue -S sparse is that it skips contiguous 0's, to avoid loading the output file with empty data. I understand RAID to be a scheme for preventing data-loss, by combining multiple hard-disks. Is that correct? How is 'sparse' related to RAID?

thx!

---

### Post by Hadaka on 2015-03-23
Hi, here is a nice link to tips and tricks with dd rescue.
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
have fun !

---

### Post by johny why on 2015-03-23
> **Hadaka said:**
> Hi, here is a nice link to tips and tricks with dd rescue.
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
have fun !

That's not the same command. Thx anyway.

---

### Post by bardo2 on 2015-03-23
> **johny why said:**
> my drive is 512 sector size. Therefor, 512 x 2721792 = 1393557504

How is 'sparse' related to RAID?



It isn't. (Sorry, still new in here and learning my ways, missed your reply.)
I am using RAID myself and consider that to be somewhat advanced technology, just as understanding sparse files. Here, i use zfs, which has raidz & compression, just saving space while copying huge amounts of data. And you are hinting to be an experienced user - to say the least - . Could i "help" someone like you? - I guess not much.
My conclusion was: there may not be a need to preserve each and every byte from ddrescue, depending on the input of course. :-)

Yup, but damaged drives are a pain, been there myself. And ddrescue would have been my choice as well.

---

### Post by johny why on 2015-03-24
thx for information, tho' not related to my OP. 

i'm not 'advanced'. I do not know the answer to the question in my OP-- just trying to solve that! 

i appreciate any info about my question-- unrelated stuff just confuses me!

 thx

---

### Post by pmi2 on 2015-03-24
If I understand what u r trying to do (and I apologise in advance if I dont)

then

 the command above will not limit the size of the image file to exactly that of your partition.  In other words, the image file will not be the same as using /dev/sda4.  It will be bigger.

To put it another way, this (hilite is the difference in the two commands):

ddrescue [COLOR=#ff0000]**-i 1393557504 -s 297193701376 /dev/sda**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

will not give you the same image file as this:

ddrescue [COLOR=#0000ff]**/dev/sda4**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

---

### Post by johny why on 2015-03-24
> **pmi2 said:**
> this (hilite is the difference in the two commands):

ddrescue [COLOR=#ff0000]**-i 1393557504 -s 297193701376 /dev/sda**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

will not give you the same image file as this:

ddrescue [COLOR=#0000ff]**/dev/sda4**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

Because?

Is my math wrong? Or something else?

thx

---

### Post by bardo2 on 2015-03-24
i am sorry, but i have to confirm that info. It took a while to setup a scenario to play with, but i did and found above to be true. unfortunately, i did not yet find the method to improve, and will stop right here: my "simulation" is too cumbersome to investigate further. also i am afraid, this already had been quite time consuming. :-(

edit:
If at all possible, you may safely copy the whole of /dev/sda and later use partprobe to create "virtual" partitions from it. (Doing that on a regular basis, so i know, it works. It is basically a loop mount of the image with an automated way to create /dev/mapper/* subdevices according to the partition table.)

---

### Post by johny why on 2015-03-24
> **bardo2 said:**
> i found above to be true.

which above?

---

### Post by bardo2 on 2015-03-24
> **pmi2 said:**
> If I understand what u r trying to do (and I apologise in advance if I dont)

ddrescue [COLOR=#ff0000]**-i 1393557504 -s 297193701376 /dev/sda**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

will not give you the same image file as this:

ddrescue [COLOR=#0000ff]**/dev/sda4**[/COLOR] /mnt/sdc1/recovered.img /mnt/sdc1/recovered.log

unfortunately is correct, i didnt check, if it is just off by 1 sector or whatever...

---

### Post by bardo2 on 2015-03-24
> **bardo2 said:**
> 
If at all possible, you may safely copy the whole of /dev/sda and later use partprobe to create "virtual" partitions from it. (Doing that on a regular basis, so i know, it works. It is basically a loop mount of the image with an automated way to create /dev/mapper/* subdevices according to the partition table.)

No, not partprobe, i meant kpartx there. Sorry

---

### Post by johny why on 2015-03-24
> **bardo2 said:**
> unfortunately is correct, i didnt check, if it is just off by 1 sector or whatever...

why do you believe my command is wrong? are you just guessing? plz tell.

thx

---

### Post by bardo2 on 2015-03-24
(replied by PM)

---

### Post by johny why on 2015-03-24
hi, bardo. it's great that you experimented about this topic. 

i'm not trying to argue. just want to understand. I think folks are saying the output file-size will be a LITTLE different than the original partition. 

for my needs, that's ok. i don't care if there's a slight mismatch, as long as the scan gets all of the partition i want. It's ok if the output includes a bit more. 

and, if the output is a little bit too small, i can increase my scan-size a little bit. 

so, are people saying i need to take a **_little bit more, _**to get the whole partition?

*OR, *are people saying my numbers are **_way off,_** and won't even get ANY of the partition i want?

thx!
i appreciate everyone's advice!
:)

---

### Post by pmi2 on 2015-03-24
> **bardo2 said:**
> ...if it is just off by 1 sector or whatever...no, those -i and -s options do not work the way the OP wants to use them (at least not if I read his posts correctly).
U can test this quite easily yourself, using a small image file, say 10Mb ( -i defaults to 0)
The test will take less time than this post, LOL:

> peter@Flattop:~$ sudo ddrescue -s [COLOR=#0000ff]1048576[/COLOR] /dev/sda1 ~/recovered10.img ~/recovered10.log
[sudo] password for peter: 

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued: [COLOR=#0000ff]    1048 kB[/COLOR],  errsize:       0 B,  current rate:    1048 kB/s
   ipos:    983040 B,   errors:       0,    average rate:    1048 kB/s
   opos:    983040 B,    time since last successful read:       0 s
Finished                   

and,
> peter@Flattop:~$ ls -l recovered10.img
-rw-r--r-- 1 root root [COLOR=#0000ff]1048576[/COLOR] Mar 24 21:15 recovered10.img

So far so good, but:
add the -i option, say 5Mb
> peter@Flattop:~$ sudo ddrescue -i 524288 -s [COLOR=#0000ff]1048576[/COLOR] /dev/sda1 ~/recovered11.img ~/recovered11.log

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued: [COLOR=#0000ff]    1048 kB[/COLOR],  errsize:       0 B,  current rate:    1048 kB/s
   ipos:     1507 kB,   errors:       0,    average rate:    1048 kB/s
   opos:     1507 kB,    time since last successful read:       0 s
Finished 
and,
> peter@Flattop:~$ ls -l recovered11.img
-rw-r--r-- 1 root root [COLOR=#ff0000]1572864[/COLOR] Mar 24 21:25 recovered11.img
Not so good!!

So this is what I think the OP will get, just on a much grander scale, and after much time... :(

---

### Post by johny why on 2015-03-24
heh, ok, this will take me a bit of time to study and understand. thx pmi2!

---

### Post by pmi2 on 2015-03-24
> **johny why said:**
> *OR, *are people saying my numbers are **_way off,_** and won't even get ANY of the partition i want?Your math is correct, it just does not work exactly as you expect.

edit: 

If you want to grab more, just use -s, not both -s and -i.
I suppose u already tried TestDisk or something similar?

---

### Post by johny why on 2015-03-25
> **pmi2 said:**
> 
peter@Flattop:~$ sudo ddrescue -i 524288 -s 1048576 /dev/sda1 ~/recovered11.img ~/recovered11.log


it appears you are targeting a partition: sda1

i want to use the -i and -s parameters against the entire drive: sda. Something like:

```
ddrescue -s 1048576 /dev/sda ~/recovered10.img ~/recovered10.log
```

i think you're not doing the right test.

thx, tho!

---

### Post by pmi2 on 2015-03-25
> **johny why said:**
> ... i think you're not doing the right test.

thx, tho!U are correct, it was not a completely valid test.  

However, the result is the same using all of SDA as a source, or just SDA1. The -i will not allow you to limit the image file to the bounds of the partition, which is what I thought u wanted.

In the example I am using as a test, the resulting image file is about 50% bigger in the second case.  U can try yourself, only takes a couple minutes with a small number of sectors/bytes, run the command with and without -i <# bytes>, let it create one image file each time, look at the size of the files.  Simple.

So, your math is not way off, but the image file size will be.

Or, if the extra size does not present a problem, just go for it, not much to lose except a little extra storage space, right?

---

### Post by johny why on 2015-03-25
as i mentioned above, i don't mind getting a bit extra, as long as i can get my files off that partition. 

my partition is 300 gb, and has so many errors, that a simple 'test' can take hours or days. and i don't expect any correlation between input partition size and output image size.

one thought: assuming a mountable partition on the source drive without any errors, is it correct to assume the output file will be the same size as the original partition? Or to put it another way, would it be a better test to mount the recovered partition and look at the contents?

thx!

---

### Post by bardo2 on 2015-03-25
Hi,

to reiterate, i am keeping several disk images of whole disks on my main computer, partly for backup reasons, partly just out of curiosity and i did lots of things with those (for instance: run zerofree on them, clean swap area, changed partition sizes,...) to achieve better compression. As an example, i was able to get from a 45G compressed file to a 17G compressed file (of a 500 GB image) without losing any relevant information.

unfortunately ddrescue doesnt write to stdout, so you need quite a lot of space WHILE using it. But as soon as you got, say... sda.img, you can compress it.
What makes it far easier on my machine is the intrinsic compression for the filesystem. But - let's be clear here - i only use it for STORING. When i create an image (using dd, my disks didnt fail yet), i immediately compress using bzip2, saves a lot of bandwith while transfering). 

so basically, i am trying to isolate the two problems (one: save the disc's content, two: access the inner partition on it.)

Maybe you have limited disk space for that? - That would kill my suggestion of course.
Then i would approach it from this side:

You are going to need a replacement for the defective drive anyway. So why not NOW? - There will be space on the replaced drive, so you could copy from one to the other directly (with ddrescue) and later edit as needed. Or are disk connections a limit as well?

Just trying to get you going as fast as possible. - And: YES, you CAN access single partitions from the loop mounted image, even make modifications there! as i mentioned earlier.
What is stopping you from such a clean solution?

---

### Post by pmi2 on 2015-03-25
> **johny why said:**
> ...assuming a mountable partition on the source drive without any errors, is it correct to assume the output file will be the same size as the original partition?Good question.  Meaning using ddrescue to produce a .img file of a "good" (error-free) partition?  I think so, but I honestly don't remember if I ever compared the exact size down to the byte.  

If nobody else has the answer, I can give that a shot later today after working hours.  Should be an interesting test.  I can try a 60Gb partition from one HD, to a second, larger drive.

---

### Post by bardo2 on 2015-03-25
ddrescue is good at recovering as many raw sectors as possible and log the ones that were lost. nothing can second that. if the will be data gone lost, and what, you'll have to see. The thinking (inside of ddrescue) is this: any unnecessary access to the drive might break it, especially usage like mounting. So it is very carefull, and when it discovered a defective area, it doesnt give up completely, it skips it and comes back to it only later, reading smaller pieces (forward and backwards) until it got all it could get. That is why it is slow, but it gets the absolute maximum saveable data from a defective drive.

---

### Post by pmi2 on 2015-03-25
@bardo2: Any idea how gparted editor can see the partition, and @ the same time, the OP said ddrescue does not work using /dev/sda4 as a source?  Have you ever come across that? (I have not)

---

### Post by johny why on 2015-03-25
> **bardo2 said:**
> unfortunately ddrescue doesnt write to stdout, so you need quite a lot of space WHILE using it. But as soon as you got, say... sda.img, you can compress it. And: YES, you CAN access single partitions from the loop mounted image, even make modifications there! as i mentioned earlier.
What is stopping you from such a clean solution?

i think you are misunderstanding what this thread is about. Thanks for you comments, but they do not address the topic of this thread. 

best

---

### Post by johny why on 2015-03-25
> **bardo2 said:**
> ddrescue is good at recovering as many raw sectors as possible and log the ones that were lost. nothing can second that. if the will be data gone lost, and what, you'll have to see. The thinking (inside of ddrescue) is this: any unnecessary access to the drive might break it, especially usage like mounting. So it is very carefull, and when it discovered a defective area, it doesnt give up completely, it skips it and comes back to it only later, reading smaller pieces (forward and backwards) until it got all it could get. That is why it is slow, but it gets the absolute maximum saveable data from a defective drive.

thanks, i know all that, but it might help others. Unfortunately, you're not addressing the question of this thread. 

thx anyway!

---

### Post by johny why on 2015-03-25
> **pmi2 said:**
> @bardo2: Any idea how gparted editor can see the partition, and @ the same time, the OP said ddrescue does not work using /dev/sda4 as a source?  Have you ever come across that? (I have not)

that is weird, ain't it!? But, gparted knows the partition is bad, as shown in the image in my OP.

---

### Post by johny why on 2015-03-25
> **pmi2 said:**
> Good question.  Meaning using ddrescue to produce a .img file of a "good" (error-free) partition?  I think so, but I honestly don't remember if I ever compared the exact size down to the byte.  

If nobody else has the answer, I can give that a shot later today after working hours.  Should be an interesting test.  I can try a 60Gb partition from one HD, to a second, larger drive.

That would be awesome!
I may have misunderstood, but i think your previous test was based on comparing sizes, right?

thx

---

### Post by bardo2 on 2015-03-25
> **johny why said:**
> i think you are misunderstanding what this thread is about. Thanks for you comments, but they do not address the topic of this thread. 

best

Oh, ok, let me apologize. You may be correct (i may be involved in too many of those simultaneously and some confusion could be possible).

So, since i missed some relevant parts apparently, i am out. Sorry for having disturbed unintentionally.

Good luck to all of you. :-)

---

### Post by pmi2 on 2015-03-26
> **johny why said:**
> that is weird, ain't it!? But, gparted knows the partition is bad, as shown in the image in my OP.Yes, the partition definitely is bad, however it does not explain why running ddrescue the most common way did not work for you (per your second post in this thread).  You said that using /dev/sda4 did not work.  Despite that, gparted finds the partition name, start, and end.  All that should be needed for ddrescue to attempt a recovery.  If gparted can find it, so should ddrescue.

> **johny why said:**
> That would be awesome!
...i think your previous test was based on comparing sizes, right?...Yes it was, but the number of bytes was set by the arguments of the command, and it was a small part of a whole partition, to save time.

I meant comparing the size of /dev/sda4 (for example), to the size of an output file from something like

ddrescue /dev/sda4 <recoveredfile>.img <recoveredfile>.log

This would be the most common way to recover one out of several partitions.

---

### Post by pmi2 on 2015-03-26
I ran ddrescue, partition as source, image file as destination, and the image file is exactly the same size as the partition.  Exact meaning same number of bytes.

> peter@Flattop:~$ sudo ddrescue   /dev/sda6   /media/Archive/Backup/recovered.img  /media/Archive/Backup/recovered.log

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:    60393 MB,  errsize:       0 B,  current rate:   30081 kB/s
   ipos:    60393 MB,   errors:       0,    average rate:   47072 kB/s
   opos:    60393 MB,    time since last successful read:       0 s
Finished     
              
peter@Flattop:~$ ls -l /media/Archive/Backup/recovered.img
-rw-rw-rw- 1 root root 60393783296 Mar 25 23:32 /media/Archive/Backup/recovered.img


It took about 23 minutes for a 60Gb partition with no errors.  i would say try it again.  Reboot, make sure the source partition is not mounted, and don't even try to access it before you run ddrescue.  It may take a very long time with retries if there are many errors.

---

### Post by matt_symes on 2015-03-27
Hi

I have not read all this thread so i don't know if this information is redundant or not but i may as well put it out there...

If you want to know the start, end and size of your partitions in bytes then use parted.

```
sudo parted /dev/sda "unit B print"
```

Change sda if required. Here's mine.

```

matthew-laptop:/home/matthew:6 % sudo parted /dev/sda "unit B print"
Model: ATA ST320LT012-9WS14 (scsi)
Disk /dev/sda: 320072933376B
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start          End            Size           File system     Name  Flags
 1      1048576B       10485759999B   10484711424B   ext4
 2      10485760000B   316236890111B  305751130112B  ext4
 3      316236890112B  320072581119B  3835691008B    linux-swap(v1)

matthew-laptop:/home/matthew:6 %
```

You can then plug these values into ddrescue to recovery the partition and then try to mount it as a loop device. However i suspect it will not mount. Still it is a much better idea to try data recovery on an image.

Kind regards

---

### Post by pmi2 on 2015-03-27
> ...You can then plug these values into ddrescue to recovery the partition...I believe the thread started with a question on how exactly to do that with ddrescue, once you have the start and end of the partition.  The final goal was to copy some data from the image file, assuming it could be mounted, or copied to another disk.  All this assuming that you could only use the abosolute start and end as ddrescue arguments, when using /dev/sda4/ did not work.

In other words, finding the start and end was not the problem, the q. was how best to make use of it.

---

### Post by matt_symes on 2015-03-28
Hi

> **pmi2 said:**
> I believe the thread started with a question on how exactly to do that with ddrescue, once you have the start and end of the partition.  The final goal was to copy some data from the image file, assuming it could be mounted, or copied to another disk.  All this assuming that you could only use the abosolute start and end as ddrescue arguments, when using /dev/sda4/ did not work.

In other words, finding the start and end was not the problem, the q. was how best to make use of it.

I was replying to the other thread the OP opened on this topic and, as i said, i did not read all this thread.

Kind regards

---

### Post by johny why on 2015-03-29
> **matt_symes said:**
> 
If you want to know the start, end and size of your partitions in bytes then use parted.

```
sudo parted /dev/sda "unit B print"
```

hey Matt

i tried this, and got:
```
# parted /dev/sdc "unit B print"
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                      
```

i hit ctrl-C there, and got:

```
Model: Apricorn  (scsi)
Disk /dev/sdc: 320072933376B
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start          End            Size           File system  Name                          Flags
 1      1048576B       315621375B     314572800B     fat32        EFI system partition          boot
 2      315621376B     1259339775B    943718400B     ntfs         Basic data partition          hidden, diag
 3      1259339776B    1393557503B    134217728B                  Microsoft reserved partition  msftres
 4      1393557504B    298587258879B  297193701376B  ntfs         Basic data partition
 5      298587258880B  320072581119B  21485322240B   ntfs         Basic data partition          hidden, diag

```

does this tell us anything new about the drive?
i want to recover the big one, #4 (and #5 if i can)
btw, what's "unit B print"?

---

### Post by johny why on 2015-03-29
> **pmi2 said:**
>   i would say try it again.  Reboot, make sure the source partition is not mounted, and don't even try to access it before you run ddrescue.

Didn't work. ddrescue says no such file or device.

---

### Post by matt_symes on 2015-04-01
Hi

> **johny why said:**
> hey Matt

i tried this, and got:
```
# parted /dev/sdc "unit B print"
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                      
```

i hit ctrl-C there, and got:

```
Model: Apricorn  (scsi)
Disk /dev/sdc: 320072933376B
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start          End            Size           File system  Name                          Flags
 1      1048576B       315621375B     314572800B     fat32        EFI system partition          boot
 2      315621376B     1259339775B    943718400B     ntfs         Basic data partition          hidden, diag
 3      1259339776B    1393557503B    134217728B                  Microsoft reserved partition  msftres
 4      1393557504B    298587258879B  297193701376B  ntfs         Basic data partition
 5      298587258880B  320072581119B  21485322240B   ntfs         Basic data partition          hidden, diag

```

Sorry for the delay. been away from keyboard.

To use ddrescue to the recover the partition (partition 4) you would use

```
sudo ddrescue -i 298587258880 -s 297193701376 /dev/sda /path/to/partition_4.img
```

That should backup the partition for you.

For partition 5 use

```
sudo ddrescue -i 1393557504 -s 21485322240 /dev/sda /path/to/partition_5.img
```

> does this tell us anything new about the drive?
i want to recover the big one, #4 (and #5 if i can)
btw, what's "unit B print"

The "unit B" will display the partition size in bytes.

When you have backed up each partition, you can then attempt to recover the files on them.

You can try mounting as a loopback device but i suspect that will fail so you may be looking at some data recovery tools. 

This will attempt to mount it as a loop back device on the mount point */mnt*. It will mount it read only.

```
sudo mount -t ntfs -o ro /path/to/partition_5.img /mnt
```

See how you get on with that and post back any error messages the terminal spits out.

Have you ran chkdsk on the partition (using a windows CD or hirens boot CD) or the recovered partition image?

Kind regards

---

### Post by johny why on 2015-04-03
hey Matt, thx for this great stuff! You're the first one to show how to use PARTED to get the exact bits and bytes.

Some questions:

> **matt_symes said:**
> 
To use ddrescue to the recover the partition (partition 4) you would use

```
sudo ddrescue -i 298587258880 -s 297193701376 /dev/sda /path/to/partition_4.img
```


hrm, you're using the start of partition 5 to recover partition 4?

> For partition 5

```
sudo ddrescue -i 1393557504 -s 21485322240 /dev/sda /path/to/partition_5.img
```

and using the start of partition 4 to recover partition 5?

many thx!

---

