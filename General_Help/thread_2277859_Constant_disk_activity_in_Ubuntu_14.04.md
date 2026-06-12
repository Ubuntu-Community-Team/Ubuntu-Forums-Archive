---
title: "Constant disk activity in Ubuntu 14.04"
date: 2015-05-12
forum: General Help
---

### Post by crazybear on 2015-05-12
I have two OS of Ubuntu [12.04 and 14.04] on separate disks. Never mind why I do, but I do. I've long noticed in system monitor that the OS in 14.04 is almost always showing very high levels of read/writes and that will quickly wear out the drive. I've seen others report this problem on the internet, but the fixes suggested that I tried only worked until the next boot. I'd love to find a fix ***that stays fixed***. Is there a terminal command that might tell me what is causing the problem? Looking at the %cpu and what programs are using memory, what is doing all the reads/writes is not obvious. In 12.04, the disk activity is occasional and what I consider normal. I have about the same general set up on both, given the obvious differences in the OSs. Both drives are quality drives showing no obvious problems I'm aware of. I'm assuming it is the OS and not the drive. Any suggestions appreciated.

---

### Post by davidvandoren on 2015-05-12
First thought, your pc doesn't have enough ram and when it runs out of it, ubuntu uses the swap disk.
Then, what's supposed to be loaded in and from ram runs from your disk.
Open your system monitor and see what it says about swap usage. 
It should be zero nowadays.

---

### Post by tgalati4 on 2015-05-12
Modern browsers (firefox and google-chrome) use up RAM when a lot of tabs are open.  That will cause a lot of swap and disk activity.  During such an event, open a terminal:

```
free
```

---

### Post by steeldriver on 2015-05-12
You could install and run iotop to see exactly what process(es) are responsible for the disk activity

---

### Post by crazybear on 2015-05-12
> **davidvandoren said:**
> First thought, your pc doesn't have enough ram and when it runs out of it, ubuntu uses the swap disk.
Then, what's supposed to be loaded in and from ram runs from your disk.
Open your system monitor and see what it says about swap usage. 
It should be zero nowadays.

I have 24MB of quality RAM and while I do have a swapspace, I've only once seen it used at about 1-3% in months and months of intensive use. I also have a very powerful processor with six cores and twelve virtual cores that run over 3.5GHz. I'd think that would be enough!....:rolleyes:

---

### Post by crazybear on 2015-05-12
> **tgalati4 said:**
> Modern browsers (firefox and google-chrome) use up RAM when a lot of tabs are open.  That will cause a lot of swap and disk activity.  During such an event, open a terminal:

```
free
```

Hmmm....running free did reduce disk activity quite a large amount for a while.....but not to the extent that it is normally in 12.04. I have the EXACT same browsers in use in 12.04 and 14.04, but something is very different in 14.04. Disk use [according to System Monitor] rarely drops below 15% and is often at 70-85%! Now, about 15 minutes after trying to run free, disk activity is back up to 'normal' [abnormal].....

---

### Post by crazybear on 2015-05-12
> **steeldriver said:**
> You could install and run iotop to see exactly what process(es) are responsible for the disk activity

OK, running iotop right now. 
Tracker-store seems to be using most reads
kworker/u32:20 (whatever that is) the most writes
followed by the two browsers open - chrome and firefox

As stated above, the same two browsers are almost always open in my 12.04 and give only a trickle of read/write activity. If I did something in 12.04 to suppress this, I've long ago forgotten what I did.

---

### Post by dino99 on 2015-05-12
Linux by default try to use the ram instead of reading the device (hdd/sdd/...). With a large amount of ram, it also need to check the indexes. A possible device(s) activity can come from the used caches (apps like browser, but also zeitgeist). Also check that hddtemp is not installed, it has been proved to do lot of hdd spinnings, and can be purged safely. Indeed caches can be reduced to a minimum if your internet link is not limited.

---

### Post by crazybear on 2015-05-12
> **dino99 said:**
> Linux by default try to use the ram instead of reading the device (hdd/sdd/...). With a large amount of ram, it also need to check the indexes. A possible device(s) activity can come from the used caches (apps like browser, but also zeitgeist). Also check that hddtemp is not installed, it has been proved to do lot of hdd spinnings, and can be purged safely. Indeed caches can be reduced to a minimum if your internet link is not limited.

hddtemp was installed. I just removed it. That does seem to have reduced disk usage so far...I'll keep an eye on it for a while....amazing if one unneeded program can do that much damage! What do you mean by 'internet link not limited'? I have **very** high speed internet, both up/down. How does one minimize caches on browsers, if I need to?...though looking at the System Monitor now, it looks more like my Ubuntu 12.04. Thanks for that tip on hddtemp! However, after disk activity going way down after removal, I see it moving back up now to 60-90%; then down again for a while - the pattern is different and less, but it still goes too high at times - strange. Still would like to know about reducing browser use of memory and disk if not necessary.

---

### Post by crazybear on 2015-05-12
Aha, using in terminal iotop -P is the way to go.....things not moving around so fast. While Chrome seems to be the program on now using the most resources, they don't seem excessive.

Interestingly, I see the swap is being used at 5%....and I'd think none would be needed...with all my RAM....something is weird. The RAM reports 30% used by programs and 70% used by cache...yet it wants to use some swap too. Need I change something?

---

### Post by QDR06VV9 on 2015-05-12
> **crazybear said:**
> Aha, using in terminal iotop -P is the way to go.....things not moving around so fast. While Chrome seems to be the program on now using the most resources, they don't seem excessive.

Interestingly, I see the swap is being used at 5%....and I'd think none would be needed...with all my RAM....something is weird. The RAM reports 30% used by programs and 70% used by cache...yet it wants to use some swap too. Need I change something?
To see if there is any difference with swap you could disable it for the current session by.
```
sudo swapoff -a  
``` 
and then to turn back on.
```
sudo swapon -a  
```
You may have already known that though;)
Regards

---

### Post by tgalati4 on 2015-05-12
Does a reboot improve performance for a while?  I have noticed the same thing in 14.04.  The caches seem to get so full that swap gets hit and that will cause a lot of disk activity.  Perhaps keep track of your uptime versus disk activity.  A cleanly-booted system will have no cache used, but after a while the entire RAM will get full of cache and moving that cache around causes disk writes.  What kernel are you running?

```
uname -a
```

Perhaps search for a bug against that kernel.

---

### Post by crazybear on 2015-05-12
> **tgalati4 said:**
> Does a reboot improve performance for a while?  I have noticed the same thing in 14.04.  The caches seem to get so full that swap gets hit and that will cause a lot of disk activity.  Perhaps keep track of your uptime versus disk activity.  A cleanly-booted system will have no cache used, but after a while the entire RAM will get full of cache and moving that cache around causes disk writes.  What kernel are you running?

```
uname -a
```

Perhaps search for a bug against that kernel.

3.13.0-53-generic is what I'm using. It is the latest and I'm not aware of any bugs...but this has certainly been a constant through all the kernels.
I don't find that a reboot changes anything. In fact, when I first boot up there is a lot of disk activity, as I'd expect as programs are loaded. I believe I read researching this that OS usually does some searching of the disk in the first several minutes to many minutes - it is the constant activity no matter how long the system is up that is concerning me.

---

### Post by crazybear on 2015-05-12
> **runrickus said:**
> To see if there is any difference with swap you could disable it for the current session by.
```
sudo swapoff -a  
``` 
and then to turn back on.
```
sudo swapon -a  
```
You may have already known that though;)
Regards

Tried that and it went back to 5%. In fact is is ALWAYS exactly at 5% no matter what I'm doing and no matter how many programs I have on. Strange, no? In 12.04 I also have a swap space, but it has only been used once in two and a half years when some program started to go a bit crazy.

---

### Post by crazybear on 2015-05-12
> **runrickus said:**
> To see if there is any difference with swap you could disable it for the current session by.
```
sudo swapoff -a  
``` 
and then to turn back on.
```
sudo swapon -a  
```
You may have already known that though;)
Regards

Tried that and it went back to 5%. Didn't see any change in disk activity when swap was off. In fact is is ALWAYS _exactly_ at 5% no matter what I'm doing and no matter how many programs I have running. Strange, no? Also strange is that swap priority is -1 [I didn't set it, and I didn't know it could have negative values]. 

Just searched and -1 priority indicates an error!!...no surprise there....but how to fix it?!? The line for the swap in /etc/fstab looks ok to me....but now I'm wondering if that 'swap' is doing something weird and constantly doing it.....hmmm.

In 12.04 I also have a swap space, but it has only been used once in two and a half years when some program started to go a bit crazy.

---

### Post by QDR06VV9 on 2015-05-12
> **crazybear said:**
> Tried that and it went back to 5%. Didn't see any change in disk activity when swap was off. In fact is is ALWAYS _exactly_ at 5% no matter what I'm doing and no matter how many programs I have running. Strange, no? Also strange is that swap priority is -1 [I didn't set it, and I didn't know it could have negative values]. 

Just searched and -1 priority indicates an error!!...no surprise there....but how to fix it?!? The line for the swap in /etc/fstab looks ok to me....but now I'm wondering if that 'swap' is doing something weird and constantly doing it.....hmmm.

In 12.04 I also have a swap space, but it has only been used once in two and a half years when some program started to go a bit crazy.
**This is not Recommended: **But when "I" do an install I do not create a swap partition and I do notice a ever so slight increase in performance. (in terms of memory snappy opening and how apps work)
Here is my out put from
```
cat /proc/meminfo
```
> mate@mate-Aspire-M3300:~$ cat /proc/meminfo
MemTotal:        6110676 kB
MemFree:          235980 kB
MemAvailable:    4634440 kB
Buffers:          117232 kB
Cached:          4398288 kB
SwapCached:            0 kB
Active:          3313936 kB
Inactive:        2194888 kB
Active(anon):     995000 kB
Inactive(anon):    34392 kB
Active(file):    2318936 kB
Inactive(file):  2160496 kB
Unevictable:          48 kB
Mlocked:              48 kB
[COLOR=#0000ff]SwapTotal:             0 kB
SwapFree:              0 kB[/COLOR]
Dirty:                68 kB
Writeback:             0 kB
AnonPages:        993352 kB
Mapped:           329044 kB
Shmem:             36088 kB
Slab:             214176 kB
SReclaimable:     172420 kB
SUnreclaim:        41756 kB
KernelStack:        8192 kB
PageTables:        30036 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3055336 kB
Committed_AS:    3628580 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      320204 kB
VmallocChunk:   34359413244 kB
HardwareCorrupted:     0 kB
AnonHugePages:    487424 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      182976 kB
DirectMap2M:     6107136 kB
DirectMap1G:           0 kB

This is with only 6gigs of ram
Regards

---

### Post by tgalati4 on 2015-05-12
Unfortunately, without swap the out-of-memory process killer has no wiggle room and the slow-down (that swap is known for) gives you some time to examine what is going on.

---

### Post by QDR06VV9 on 2015-05-12
> **tgalati4 said:**
> Unfortunately, without swap the out-of-memory process killer has no wiggle room and the slow-down (that swap is known for) gives you some time to examine what is going on.
Agreed Thats why I put  _"**This is not Recommended:" **_ but I have been doing this way for years with no Ill effects.(under heavy loads at times again with no ill effects.)
I also participate in the testing cycles rolling from one release to the other.(with no swap)
If my RAM was below 4 Gigs I would have a swap partition to be sure!;)
I am kind of wondering if Zeitgeist dose not have a factor here for OP.
Kind Regards

---

### Post by crazybear on 2015-05-13
I've been doing a LOT of comparisons lately between my Ubuntu 12.04 which generally works much better than my 14.04 [sadly - as it can do a few things better, but most on my OS it does worse]. 
As I mentioned the two systems have almost the exact same programs, which are usually opened in the same groupings; yet the 12.04 uses less memory and doesn't have the issues with the disk activity.
In my /etc/fstab for 12.04 I see something I don't remember adding, but might have long ago and forgot. I'm wondering if anyone can tell me what it does and if it would help adding it to my 14.04 fstab.

> ......
UUID=2cb0ff36-4be7-404f-93f5-0492407d3b39 none            swap    sw              0       0 
tmpfs /dev/shm tmpfsdefaults,ro 0 0 
# Move /tmp to RAM 
tmpfs /tmp tmpfsdefaults,exec,nosuid 0 0  


As to swap vs. no swap, I have a ton of RAM and can anyone make a good arguement for having the swapfile? - however, shutting it off doesn't change my disk write problems.

---

### Post by crazybear on 2015-05-13
Hey!? I just noticed something most strange [to me] - in terminal I ran sudo iotop -P and the disk activity dropped DRAMATICALLY! Is this some artifact or reporting error?!~seems counterintuitive. Close the terminal and the activity is reported as before, around 60-80%!

---

### Post by v3.xx on 2015-05-13
> can anyone make a good argument for having the swapfile?

I also have 24G and use upward of 10.  I have ran with swap and without, it does not make a difference on my box.  I have a 2G swap for convenience, one less step when setting up a new flavor. 

A way to kill disk activity :)
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

I do not see this disk activity in either 12 or 14o4.  So I don't have a answer for your real problem.

---

### Post by crazybear on 2015-07-30
Hello again. This has been inactive for a while, but my problem HAS NOT BEEN! As far as I know, my disk physically is good, but the activity level on 14.04 compared to 12.04 is about 10-30x more and not usually related to what I perceive as logical times to be active [often busiest when computer is doing nothing I can imagine it would be]. It is often quieted down some by turning off the swap file, but not always and it is a pain to always have to open a terminal and turn off the swap...which I've been hesitant to remove totally. Any ideas how I can diagnose this strange phenomenon. Disk activity is so intense, I worry about the disk no lasting long.

---

