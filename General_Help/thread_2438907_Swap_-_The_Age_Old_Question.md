---
title: "Swap - The Age Old Question"
date: 2020-03-20
forum: General Help
---

### Post by Shibblet on 2020-03-20
I have searched the entire internet for a reasonable answer to these questions, only to find that people continue to have differing opinions on the matter.

**With a computer that has 16gb of RAM, do I need a swap file?**

I will not be using hibernate.

If I tell the Ubuntu installer that I do not have a Swap partition, it makes a file on my SSD to use as Swap anyway...

**How do I disable this entirely, if it is okay to do so?**

Maybe I should ask a better question... **What is the whole purpose of the Swap file, in a modern computer that has plenty of RAM, and will not be using hibernate?**  This seems like a Windows question...

**Can someone explain how Ubuntu uses Swap?**

---

### Post by CatKiller on 2020-03-20
Yes, you need a swap file.

Out of memory situations are simply awful. Some applications simply misbehave. Setting aside a tiny proportion of your drive space to prevent running out of memory addresses is a trivial trade off. If it never ever gets used for anything: great!

---

### Post by Tadaen_Sylvermane on 2020-03-20
I dont know the technical side of things involving swap. I iust know that some things need it to exist. I keep no more than a 2gb swap on any of my machines at home. Small price to pay to avoid problems.

---

### Post by Shibblet on 2020-03-20
> **CatKiller said:**
> Yes, you need a swap file.

Out of memory situations are simply awful. Some applications simply misbehave. Setting aside a tiny proportion of your drive space to prevent running out of memory addresses is a trivial trade off. If it never ever gets used for anything: great!

Is there any way to have the file put on a different drive, or do I have to make a Swap partition for that?

> **Tadaen_Sylvermane said:**
> I dont know the technical side of things involving swap. I iust know that some things need it to exist. I keep no more than a 2gb swap on any of my machines at home. Small price to pay to avoid problems.

So, 2g is enough with 16g of RAM?

---

### Post by CatKiller on 2020-03-20
> **Shibblet said:**
> Is there any way to have the file put on a different drive, or do I have to make a Swap partition for that?
It's just a file that's full of zeros. I'd imagine you can put it wherever you want, although you'd want it on your fastest storage in case it ever does get used. Not having played around with it much, I think you'd just create your file wherever and then use *mkswap* to say that you want to use that file as swap, and use fstab so that it gets used automatically at boot.

---

### Post by deadflowr on 2020-03-20
Set the swappiness to a low usage number.
The default is 60 (or last I checked it was), setting it to 10 will make it swap less.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")
That should allow it to be less aggressive.

---

### Post by Cavsfan on 2020-03-20
I had a quad core for 10 years and it never used 1% of swap, now on an i7 with SSD it still never uses %1 of swap. 
But, rather than finding any alternative, I setup a 4GB (2GB as mentioned above would do) swap file just because every Linux system there is wants a swap file.

So, it's like you need one to install but, it doesn't really get used. Maybe swap files will not be needed in the future.

I have 16GB RAM and suspend rather than hibernate and that works great.

---

### Post by TheFu on 2020-03-20
There are many opinions about swap and there are some technical mandates that are dependent on settings and the specific kernel.

[LIST]
[*]Purpose of swap is to provide feedback when a system is running low on real RAM, but not crash.
[*]To that end, "some" swap is necessary.
[*]About  a year ago, there was a bug in the kernels that cause all sorts of performance problems when zero swap was setup. A token amount was needed to avoid  
[*]4.1G is the easy answer for all desktop systems related to swap.
[*]Heavy modern browsers can easily grow to use that amount of RAM and crash a system w/ 1-4G of RAM
[*]6+GB RAM systems might have many "cheese" programs open, so we need the swap to warn us, before a system crash.
[*]12-64GB systems need it because users of those computers will quickly become complacent, use more RAM than available and crash.
[/LIST]
The best feedback from swap comes by using slower storage.  Users need to "feel" that the system is getting slower so they can take action, usually by closing some hog program, but certainly by saving any unsaved work.

People doing video or audio editing will quickly discover that 16G isn't sufficient for all but the most trivial files.

These days, very few systems are storage constrained. 4.1G for swap is easily setup just after an install.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  for the "community" version.

On my servers,  i specifically setup the RAM to ensure peek workloads don't ever swap or need swap.  For desktops, the workloads are just too variable.  I&#8217;ve tried 1, 2, 4, 8GB of swap on systems w/ 384M, 512M, 1G, 2G, 4G, 6G, 8G, 16G of RAM and found that 4.1GB is the best compromise.

IMHO. Lots of different needs, so there isn't 1, true, correct, perfect, answer that meets all requirements.

---

### Post by Cavsfan on 2020-03-21
I have not ever seen any of my swap file being used. I've monitored it too. I seen someone with a 1 core processor need to and did use swap but, not here on any systems: an old and a newer computer.

I know it's required and I'm not trying to argue here. :D
I have never seen any of my swap file used. I suspend and it suspends in < 5 seconds. It wakes about as fast too.

I don't believe the 2 are even related but, I have used 1MB of swap and it was fine. The old PC had 4GB RAM so I decided to make it that same size 4GB and have done that for the past several years without difficulty.
New PC has 16GB RAM and the 9 Linux systems on this PC all use the same 4GB swap file.

---

### Post by TheFu on 2020-03-21
```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:            15G        9.7G        200M        7.5M        5.7G        5.2G
Swap:          4.3G        2.2G        2.0G

```
Just saying.

And on another machine:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           7.5G        4.8G        275M         24M        2.4G        2.3G
Swap:          3.6G        2.4G        1.2G
```

And on another machine: 
```
free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.9G        2.3G        494M        130M        1.1G        1.0G
Swap:          3.1G        1.4G        1.7G

```
and ...
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           996M        648M        109M        6.3M        238M        194M
Swap:          2.0G        775M        1.2G
```
and
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           991M         78M        119M         10M        793M        648M
Swap:          1.0G        2.0M        1.0G
```
and
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           992M        235M         94M         21M        662M        531M
Swap:          1.0G        147M        874M
```
and
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1191        960        231          0        182        332
-/+ buffers/cache:        445        746
Swap:            0          0          0
```
And email server:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           2.9G        2.0G        261M         18M        683M        736M
Swap:          979M        201M        778M
```

Guess which are desktops and which are servers.
The 3rd one is the desktop. All the others are servers without any GUI running.

---

### Post by daniewicz on 2020-03-21
My beloved 10 year old MacPro

```
 $ free -mh              total        used        free      shared  buff/cache   available
Mem:           23Gi       1.7Gi        17Gi       137Mi       4.2Gi        21Gi
Swap:         2.0Gi          0B       2.0Gi
 
```

---

### Post by TheFu on 2020-03-21
Few people have 24G of RAM and reboot daily.

---

### Post by sgage on 2020-03-21
What are the benefits/tradeoffs to having a swap file vs. a swap partition?

---

### Post by TheFu on 2020-03-21
> **sgage said:**
> What are the benefits/tradeoffs to having a swap file vs. a swap partition?

Swap files are 
* more convenient for users who aren't comfortable w/ partitioning
* easier for MBR systems that are limited to 4 primary partitions
* worse for file fragmentation, unless added early
* backups need to exclude the swap file; snapshots at the partition level would freeze the swap, unnecessarily

Swap partitions have 
* no chance of fragmentation
* more hassle to resize

Systems that use LVM drastically mitigate the negatives of swap partitions, but LVM is not normally used by users new to linux.

i use LVM **and** swap LVs (like partitions).

---

### Post by sgage on 2020-03-21
In the early years, when RAM was expensive and scarce, I always had a swap partition equal to my RAM. A couple of years ago, I got a computer with 12G RAM, and did the same. I monitor things pretty closely, and I noticed that the swap was never touched. So I did away with it - I have not had a single problem. I do NOT do anything like video editing or such. I use my computer a lot, but almost never touch 4G RAM usage.

I have been away from Ubuntu for a long time - used it from Warty to Natty and the whole Gnome3/Unity thing, when I checked out other options. Nowadays I use MATE, and Ubuntu MATE is quite nice, and I notice that Ubuntu sets up a swap file...

---

### Post by Cavsfan on 2020-03-24
All I get is this:
```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:           15Gi       1.2Gi        13Gi       120Mi       1.0Gi        13Gi
Swap:         4.0Gi          0B       4.0Gi

```
I have one computer with many Linux systems on it (9 soon to be 10) and none of them use swap while they all seem to require it.

Not sure what causes one to use swap and others to see no usage whatsoever.

While installing some systems you can't point to/use the 1 swap file you have or it will be formatted.
So, I choose just the root partition and install; it still finds the existing swap and mounts it upon the 1st reboot.
So, then I add the swap file properly to the fstab file. No big deal as I add a Media partition as well.

---

### Post by TheFu on 2020-03-24
if you want to see swap used, run 5 instances of chrome and run some  batch handbrake transcoding jobs for an hour.
Or run a geospacial DB w/ 5 VMs as clients.
Or do some light Android development using the normal android dev tools.

---

### Post by Cavsfan on 2020-03-25
Put a lot of effort into it eh?  :P

On Arch I just turned on SimpleScreenRecorder which uses up the most CPU of any app I know of.
Recording a 3480x2160 video at 60hz with sound and *still* 0% of swap was used.

I have used a 1MB swap and it still functioned the same. I just gave it 4GB because I could.

---

### Post by CatKiller on 2020-03-25
CPU usage is orthogonal to RAM usage.

The big one is Java. It gets round to clearing up after itself, mostly, eventually, but in the meantime you'd better have some way of creating new pages.

Websites running arbitrary code, with unknown provenance, from the lowest bidder, is another prime misbehaver, too, of course.

---

### Post by fahrbach on 2020-03-25
My work computer only has 16G of RAM.  I've had others that have 32G.  I depends on what you need to run.  I have home computers running 16.04 LTS.  They mostly do web browsing and are barely breathing with 8G of RAM.  And they're speedy. :-)

---

