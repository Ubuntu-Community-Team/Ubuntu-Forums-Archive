---
title: "File operations take 100% CPU"
date: 2007-04-02
forum: General Help
---

### Post by the_mouse on 2007-04-02
When I copy something wether on/to my HDD or flash card, the CPU is taken to 100%, but there's no visible prosess that takes so much CPU. Here's a screenshot of the situation:
[[IMG]http://img402.imageshack.us/img402/2534/snp2gk6.th.jpg[/IMG]](http://img402.imageshack.us/my.php?image=snp2gk6.jpg)

When the file transfer is done, everything is OK, but when the CPU is at 100%, KDE is pretty uncomfortable to use :( I'm using Kubuntu Dapper

---

### Post by rvny on 2007-04-02
Maybe you hard disk work in pio mode data transver? UDMA mode supported in you mother board and bios?

---

### Post by the_mouse on 2007-04-02
Well I think so, how can I check?

edit:
Here's what I get when I enter this in the console:
the-mouse@tilixbox:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 160836480, start = 0

---

### Post by the_mouse on 2007-04-02
Can't anyone figure out why am I having this problem?

---

### Post by kerry_s on 2007-04-02
From what i see it's the many small app's running combined that could be sending your cpu to the top. Plus your running a heavy desktop with only 256 of ram, so more than likely your cpu is working like a dog swapping info out of ram or swap. You should be running a less intensive DE/WM with those kind of specs. My bet is your running off swap because your pic shows you have 92 total tasks running and your memory is full.

---

### Post by Sencer on 2007-04-02
> **the_mouse said:**
> When I copy something wether on/to my HDD or flash card, the CPU is taken to 100%, but there's no visible prosess that takes so much CPU.

That's because it's not really taking up CPU, it's called I/O Wait and commonly confuses users that re new to linux. If you do a "man top" on the console you'll get this explanation:

> 
   2c. CPU States
       The CPU states are shown in the Summary Area. They are always shown as a  per&#8208;
       centage and are for the time between now and the last refresh.

        us  --  User CPU time
          The time the CPU has spent running users’ processes that are not niced.

        sy  --  System CPU time
          The time the CPU has spent running the kernel and its processes.

        ni  --  Nice CPU time
          The time the CPU has spent running users’ proccess that have been niced.

[b]        wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.
[/b]
        hi  --  Hardware IRQ
          The amount of time the CPU has been servicing hardware interrupts.

        si  --  Software Interrupts
          The amount of time the CPU has been servicing software interrupts.


It doesn't block other processes from using those cpu cycles, so you can look at iowait as being "available" from a cpu perspective - it would do something else, if there was actually anything to do. It merely shows that your disk i/o is the limiting factor, which is of course obvious in the process of a large file-copy, but may not be so obvious for other software. iowait means - if you wanted to speed this up, you would need a faster harddrive, a faster cpu wouldn't help at all. Whereas user/sys means the opposite (process is limited by available cpu, a faster or aditional harddrisk wouldn't help).

> , but when the CPU is at 100%, KDE is pretty uncomfortable to use

which is most likely because of your starving for io. Using KDE often means reading/loading certain files which will now take much longer, because the HDD is working overtime already. It has to read a lot of data, and at the same time write a lot of data, which leads to many seeks across the disk slowing the process down further (copying from one HDD to another would be a lot faster - unsurprisingly).
Swapping is probably not the problem, as only 50 MB of swap seems to be used. You can search for "swappiness" and try to set that lower, which will avoid swapping applications where possible (you sacrifice overall/total speed for the sake of responsiveness), but like I said I don't think that it is playing much of a role in this instance.

You can use vmstat 1 10 on the command line and watch the columns si/so under ---io--- which means "swapin" and "swapout", if they are zero all the time, no data is being swapped in or out. 1 and 10 refer to "update once a second", "10 times overall". You can monitor it for much longer, too, of course.

---

### Post by the_mouse on 2007-04-02
So what should I do to reduse the CPU usage when I copy files form/to HDD?

---

### Post by Ptero-4 on 2007-04-02
> **the_mouse said:**
> When I copy something wether on/to my HDD or flash card, the CPU is taken to 100%, but there's no visible prosess that takes so much CPU. Here's a screenshot of the situation:
[[IMG]http://img402.imageshack.us/img402/2534/snp2gk6.th.jpg[/IMG]](http://img402.imageshack.us/my.php?image=snp2gk6.jpg)

When the file transfer is done, everything is OK, but when the CPU is at 100%, KDE is pretty uncomfortable to use :( I'm using Kubuntu Dapper

What Windeco is that one you`re using?

---

### Post by kerry_s on 2007-04-02
> **the_mouse said:**
> So what should I do to reduse the CPU usage when I copy files form/to HDD?

I don't think you can, you would need to reduce your memory use. I'm betting with kde it's topped out all the time, so your mostly using swap, probably on the same drive as your install, so you have 2 process's fighting for HD use, 1 will be the copying and the other will be swap trying to find a place to put the info it's moving off ram. It's a vicious cycle. :)

---

### Post by Sencer on 2007-04-02
> **the_mouse said:**
> So what should I do to reduse the CPU usage when I copy files form/to HDD?

Maybe I did not make myself clear. Your CPU usage in the screenshot is:

21.8% user
9,9% system
-----------------
31,7% <- this is the actual utilization of your cpu cycles.

The rest is only I/O wait.

67.3% is available for other process that need cpu-cycles, but since nothing is using it, it is shown that the cpu is waiting for harddisk i/o (input/output), and that more cpu cycles might be used if the harddisks were faster.

Your sluggishness is not due to cpu, it is because of your harddisk. 

Do you have enough free space on the harddrive? It is a good idea to always leave at least 20% of free space (the more, the better). If you have less and less space and move/copy around large file, fragmentation increases like crazy (because not all free space is in one continuous block) and things slow down more and more, because the disk is doing more and more seeks and less actual reading/writing. That might also lead to more sluggishness of the system.

edit: What's that about swap all the time  - it doesn't look swap is being used much. But I suggested using vmstat to find out if that's the case. Until that is confirmed it's only a guess.

---

### Post by kerry_s on 2007-04-02
> **Sencer said:**
> Maybe I did not make myself clear. Your CPU usage in the screenshot is:

21.8% user
9,9% system
-----------------
31,7% <- this is the actual utilization of your cpu cycles.

The rest is only I/O wait.

67.3% is available for other process that need cpu-cycles, but since nothing is using it, it is shown that the cpu is waiting for harddisk i/o (input/output), and that more cpu cycles might be used if the harddisks were faster.

Your sluggishness is not due to cpu, it is because of your harddisk. 

Do you have enough free space on the harddrive? It is a good idea to always leave at least 20% of free space (the more, the better). If you have less and less space and move/copy around large file, fragmentation increases like crazy (because not all free space is in one continuous block) and things slow down more and more, because the disk is doing more and more seeks and less actual reading/writing. That might also lead to more sluggishness of the system.

edit: What's that about swap all the time  - it doesn't look swap is being used much. But I suggested using vmstat to find out if that's the case. Until that is confirmed it's only a guess.

Your not understanding, the reason it's waiting and taking up cpu cycles is because of low ram. There is always suppose to be a reserve on ram and the old data gets pushed off to swap. Because the HD is in use by the coping of the data,  it has to wait to be swapped, so the cpu has to work harder scheduling back and fourth between the priority processes. The process of copying does not go straight to the disk, it's buffered in ram first, then written to the disk.

copy from>to ram>to disk

what's actually happening->

copy from> oops not enough ram, swap out> to disk>woo need to write at the same time> oops better schedule, got to set to wait.(thanks cfq)


Anyways you need more ram.

---

### Post by dcstar on 2007-04-03
> **the_mouse said:**
> So what should I do to reduse the CPU usage when I copy files form/to HDD?

You can add the option "noatime" to your /etc/fstab line for the relevant filesystem.

Not turning off "atime" causes an Access Timestamp to be updated for every file read, which adds extra overhead (and therefore CPU usage, in your case).

---

### Post by Sencer on 2007-04-03
> **kerry_s said:**
> Your not understanding, the reason it's waiting and taking up cpu cycles is because of low ram. There is always suppose to be a reserve on ram and the old data gets pushed off to swap.

No, there's usually no reserve on RAM - that would mean wasting RAM. RAM that is not used by applications will be quickly filled with caches of accessed files.

What makes you so sure that data is being swapped in and out? The total value of used swap is around 50 MB. And the user has not run vmstat to check if any swapping is happening at all.

> The process of copying does not go straight to the disk, it's buffered in ram first, then written to the disk.

Yes, of course, but 256MB RAM is enough to have the necessary parts of KDE in memory and do a file copy without having to swap. On my system I have 512 MB RAM, of which currently 293 MB are used (the rest is file caches) and a couple dozen MB is swapped out to disk. When I start copying a large file now, it looks much the same, Little real CPU usage, the rest to 100% filled with iowait, vmstat shows no swaping in or out is happening.

The slowest part of a file copy is _always_ the writing to disk, it would be pretty stupid to read in many dozens of MB into memory (or even swapping other stuff out to disk), to keep a lot of data ready in RAm to write. Reads are cheap compared to writes. There's always going to be some data queued up for writing, but not so much that major swapping would be going on. I have another Xubuntu system set up on an old PII with 196 MB RAM, and file copies there are also always limited by disk i/o (writing the actual file and seeks), never is there swapping during a copy.

> Anyways you need more ram.

Yes, that is almost always true, isn't it... ;) I doubt it's going to speed up the copy much. A new harddrive may cost the same, but will show magnitudes of better improvement for file copies (though for the overall performance I'd still recommend more RAM over a new HDD).

---

### Post by kerry_s on 2007-04-03
Okay.

---

### Post by the_mouse on 2007-04-04
I added noatime to my fstab and now it looks like that:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda9 / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
/dev/hda1 /media/hda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser,noatime 0 0
/dev/hda5 /media/hda5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser,noatime 0 0
/dev/hda6 /media/hda6 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser,noatime 0 0
/dev/hda7 /media/hda7 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/hda8 none swap sw 0 0
/dev/hdc /media/DVD auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/flash auto defaults,ro,user,noexec,noauto,rw 0 0
/dev/hdb /media/CD-ROM auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
```
But it had no effect, I still have those 100 CPU usage when copying form DVD to HDD and from HDD to flash media :confused:

Should I add noatime to my linux partition?

---

### Post by Sencer on 2007-04-04
1) Do you have enough free space on the harddrive? It is a good idea to always leave at least 20% of free space (the more, the better). If you have less and less space and move/copy around large file, fragmentation increases like crazy (because not all free space is in one continuous block) and things slow down more and more, because the disk is doing more and more seeks and less actual reading/writing. That might also lead to more sluggishness of the system. So: What is the output of "df -h".

2) What is the output of  "vmstat 1 10" on the console (keep a terminal window open and run it during a time when you feel the system is sluggish)

3) What is the output of "cat /proc/sys/vm/swappiness"

---

### Post by the_mouse on 2007-04-10
the-mouse@tilixbox:~$ vmstat 1 10
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 1  1 114904   2068   1308 121732   29   78   706   560  492  1206 16  5 69 10
 0  1 114904   2516   1260 121396    0    0  7941  8292  518  1330 16 17  0 67
 0  1 114904   3084   1244 120628    0    0  7985  8290  508  1416 11 15  0 74
 1  0 114904   3252   1244 120408    0    0  7969  8288  551  1399 18 20  0 62
 0  1 114904   2772   1132 121240    0    0  8497  8289  498  1344  8 16  0 76
 2  0 114904   2640   1168 120660    0    0  7681  8440  535  1366 13 16  0 72
 0  1 114904   2020   1208 121344    0    0  8543  8288  583  1501  9 19  0 72
 2  1 114904   2384   1176 121460    0    0  7424  4148  516  1424 16 14  0 71
 1  0 114904   1948   1160 121420    0    0  8786 12432  533  1380  9 19  0 73
 2  1 114904   3188   1152 120400    0    0  8193  6532  524  1291 13 21  0 67


the-mouse@tilixbox:~$ cat /proc/sys/vm/swappiness
60

Here there are :)

---

### Post by Sencer on 2007-04-10
> **the_mouse said:**
> the-mouse@tilixbox:~$ vmstat 1 10

Like I assumed the si/so columns which show the numbers of bytes that are currently being swapped in or swapped out are zero. This means swapping doesn't come into it.


As for the 100%... I tried to explain that as best as I could above. It's not something that you can or want to do anything about, unless you would **want** to noticably slow down the copying and make it take longer than it does now. (And no, I am not aware of a simple way to do that).

Like I said, if your HDD is overly full (less than 20% of free space), and you move lots of big files around, then fragmentation will increase, and this will make operations slower (the is hdd is seeking so much back and forth, that is transferring less and less data), and that could also make your system feel more sluggish during heavy I/O. Or your case might be related to something entirely different, that arises when copying large files. Don't get hung up on the "100%" figure, that is not what your problem is about (everbody has 100% showing there, when copying large files; it's not what you think it means).

---

### Post by the_mouse on 2007-04-10
So there's nothing I can do??? And always when I do this my system will be that slow???

---

### Post by Sencer on 2007-04-11
> **the_mouse said:**
> So there's nothing I can do?

What I am saying is that the 100% figure is not an indicator as to whether you have a problem or not, because in the course of a file copy it is expected to show 100%. Usually that will have little or no effect on the responsiveness of KDE/Gnome.

> And always when I do this my system will be that slow?

You have mentioned that KDE becomes "uncomfortable to use", and that "the system is slow". I have offered one possible explanation (and somewhat a solution) above, you never responded whether the partition(s) used for ubuntu and/or copying are or were at some point overly full or not (output of "df -h"). 

Another possibility is that the driver for your graphic chip is not the right/best one. I've heard people complain that this leads to a sluggish Dektopenvironment, however I don't know if this effect would worsen during a large copy (drop of HDD I/O). 

If neither is not the case for you, you might be seeing another problem. In any case I would suggest you open a new topic with a more appropiate title (like "KDE is sluggish when copying large files"), all the basic information that we pieced out of you bit by bit in this thread, and a link to this topic for some background, to see if anybody has other suggestions to try.

Good Luck.

---

### Post by the_mouse on 2007-04-12
the-mouse@tilixbox:~$ df -h
File system            Size Used  Free Used% Mounted on (the titles was in bulgarian, I changed them to english, so they may be different)
/dev/hda9             6,0G  4,0G  2,1G  66% /
varrun                126M  108K  126M   1% /var/run
varlock               126M  4,0K  126M   1% /var/lock
udev                  126M  116K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/hda1              18G   18G  529M  98% /media/hda1
/dev/hda5              20G   20G  202M 100% /media/hda5
/dev/hda6              27G   27G  852M  97% /media/hda6
/dev/hda7             6,0G  2,0G  4,0G  34% /media/hda7
/dev/hdc              4,3G  4,3G     0 100% /media/DVD

I'll try to free space of hda6 which was used to copy the files and see if thers's any change
Sorry for not answering to your suggestion before, somehow I missed it :(

---

### Post by cudjoe on 2008-06-02
Same problem with two different computers with Hardy.

[http://ubuntuforums.org/showthread.php?t=86418](http://ubuntuforums.org/showthread.php?t=86418)

My HD are not full.

I am using Gnome, and I think those problems appeared recently (I would say with last kernels, don't remember Gutsy sucking so much ressource)

What tools would you use to monitor hard disk activity ? System monitor applet reports full CPU use (background dark blue color) and very few hard disk activity...
Strange and thus so hard to fix.

Good luck and thank you for sharing !

---

