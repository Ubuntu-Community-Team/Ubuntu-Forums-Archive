---
title: "How necessary is a swap partition?"
date: 2008-03-21
forum: General Help
---

### Post by Sweet Mercury on 2008-03-21
I have a MacBook (this isn't necessarily an Apple specific question so I'm putting it in General area), with 2GB of RAM.

I have a 200GB Hard Drive (186.3 Useable) in 2 partitions, 172.0 GB for OSX and 13.9 GB set aside for Xubuntu.

So those are the basics. Today I tried to install Xubuntu onto the smaller partition, and after I assigned the root directory, it advised me that I needed a swap partition.

When I ran Ubuntu on my Dell with 512 MB of RAM I never saw more than 270 MB in use, and the swap partition was never touched, according to the resource meters I had running. I was told by the installer that I didn't *need* a swap partition, but that it was "recommended."

My question is, do I need to eat up 2+GB of that Space to use as a swap?

---

### Post by thenetduck on 2008-03-21
Here is a good read for ya

[http://en.wikipedia.org/wiki/Swap](http://en.wikipedia.org/wiki/Swap)

My answer would be: whatever you feel is necessary. You can think of swap as really slow fake memory that your computer uses for various of things. Kind of like making a partition for extra memory (someone correct me if im wrong ;) 

So, you can get away with only using your memory, but it's healthy for your system to have some swap. I like to do about 1gb per 100gb of hard drive space, but some might think that is overkill. If you did something like 512mb you should be fine. I don't recommend no swap but its your computer :)

The Net Duck

Hope that helps.

---

### Post by forestpixie on 2008-03-21
and if you hibernate you need swap 

If you don't do that - it might be worth having some - I have 1Gb of RAM and swap and rarely use the swap - but it's there justin case

---

### Post by justleen on 2008-03-21
If you hibernate you need as much swap as you have internal memory..

THere is a rule of thumb to have atleast half the amount of memory as swap, but i find that a bit to much personally, since my swap is hardly used any way i find 512 is plenty for me (2GB interal) but then, all i do is use a lot of terminals with ssh sessions.. I wouldnt delete my whole swap, even though your system will run just fine (perhaps a bit  slower..)

YOu can even test it easily
```

sudo swapoff
sudo swapon

```
to check the swap usage (when its on)
swapon -s
[/code]


just a quick example of one of ours bussiest servers, not using any swap at all :)  :

Swap partition /dev/disk/dsk2c (default swap):
    Allocated space:      1570944 pages (11.99GB)
    In-use space:             922 pages (  0%)
    Free space:           1570022 pages ( 99%)


Total swap allocation:
    Allocated space:      1570944 pages (11.99GB)
    Reserved space:        404489 pages ( 25%)
    In-use space:             922 pages (  0%)
    Available space:      1166455 pages ( 74%)

---

### Post by Sweet Mercury on 2008-03-21
Alright thanks guys, I'll probably section of a bit for the swap, not a huge amount.

I don't really hibernate, I just use the standby option, so it's not an issue. Thanks.

---

