---
title: "Verify that swap is working"
date: 2014-05-24
forum: General Help
---

### Post by Jason_Minns on 2014-05-24
I've been running this laptop soundly for several months. I never noticed any activity on the swap partition in System Monitor's resource's tab, htop, etc...:confused: I have 8 gigs of memory, so I just kind of figured the swap was never needed/ used, or if it was I just never noticed. Now, I'm beginning to believe that it doesn't work at all. The swap is set to on. 

I searched online. Does anyone have any suggestions? 
All help is greatly appriciated. 


$ sudo tune2fs -l /dev/sda6

tune2fs 1.42.9 (4-Feb-2014)
tune2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn't find valid filesystem superblock.

Stumped, 
Jason

---

### Post by steeldriver on 2014-05-24
Are you showing us the tune2fs output for your swap partition? afaik swap doesn't use an ext filesystem, so I don't think that's significant - what is the output of

```

swapon -s

free

```

---

### Post by vanadium on 2014-05-24
It appears you see your swap in your monitoring tools. I guess it will be OK. With 8 GB of RAM, one rarely if ever uses swap during normal desktop usage.

---

### Post by Jason_Minns on 2014-05-24
I done both of these before I posted:
 swapon -s

free

I still get the message: tune2fs: Bad magic number in super-block while trying to open /dev/sda6

Couldn't find valid filesystem superblock. 

Do others get this message when using the tune2fs tool to investigate the partition that swap is on? I'm curious.

sudo tune2fs -l /dev/sda6

Thanks,
Jason

---

### Post by grahammechanical on 2014-05-24
I am using 14.04 on a machine with 1 GB of RAM and at the moment it is using 356 MB of swap space. Why would you expect swap to be used with 8 GB of RAM? You could install system-load-indicator. It is in the software centre. That will give you, among other things, a memory usage readout in real time. Next, you would need to find some really memory intensive process that will use up most of your memory and then start to load other applications and see what happens.

Regards.

---

### Post by coffeecat on 2014-05-24
> **Jason_Minns said:**
> 
Do others get this message when using the tune2fs tool to investigate the partition that swap is on? I'm curious.

From man tune2fs:

>  tune2fs  -  adjust  tunable  filesystem  parameters  on  **ext2/ext3/ext4** filesystems

(My bold.) A swap partition doesn't have a ext2/ext3/ext4 filesystem. Using tune2fs to investigate a swap partition is a bit like using a cheese grater to fry onions. It's the wrong tool for the wrong job. But to satisfy your curiosity (my swap is on sda5):

```
$ sudo tune2fs -l /dev/sda5
tune2fs 1.42.9 (4-Feb-2014)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```

The same output as you, but it doesn't worry me because that output is meaningless. Wrong tool; wrong job.

I think you've been sufficiently answered by others - there is nothing wrong in what you are seeing.

---

### Post by Jason_Minns on 2014-05-24
Good to know. Which bring me to my next question: If you next to never use swap, why would they recomend that the swap partition size should be 1.5 to 2 times the size of your ram? That doesn't make much sense to me. 

Thanks, 
Jason

---

### Post by LastDino on 2014-05-24
I've 4GB RAM and the only time my machine has to ever use SWAP  is whenever  I  try to run VM with granting it 40% of my installed RAM, and even then it is used below 50MB. 

General thumb rule is keeping it in equal amount as your RAM or 1.5xRAM, that is if your RAM is really low. It is used for things like Hibernation & suspend (I don't use or advise it anyway) and in some really really off chance, there is some malfunction with application which keeps opening windows till your RAM runs out of space and then it starts  to access your SWAP. When it hits SWAP area, it gets slow and easy to damage control, because by nature; SWAP is quite slow, especially compared to RAM. The latter has actually happened with me but I hit hardreboot before it reached SWAP, so no real worries there either. 

However, IMO, when you've more than 4GB RAM and don't plan to hibernate or suspend, you are actually quite free to reduce that SWAP size to around 1 or 2GB or something. It doesn't really hurt in these days of TB HD's and GPT.

The easiest way to check whether SWAP is mounted or not is to have gparted on your system, you can simply open it and see if there is ''key'' icon in front of SWAP partition. It being there indicates that; that particular partition is currently mounted. Of course, you can check other partitions also, gparted is quite handy.

---

### Post by Bashing-om on 2014-05-24
Jason_Minns; Well, consider

Ram is the memory usage area on your computer, if you are doing some heavy duty stuff, and run out of ram, recon what is going to happen ? =>
Crash big time ! Not a good thing at all as all the system files are open and the crash leaves them in an inconsistent state. Swap gives the system someplace to move less needed stuff out of ram, and if you do run short on ram space, a place to go to . Particularly so in hibernation and suspend of the operating system.

Depending on what you are doing, or might do in the future, is how much hard disk space (swap partition and/or a "swap file") one allocates to that use.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by coffeecat on 2014-05-24
> **Jason_Minns said:**
> If you next to never use swap, why would they recomend that the swap partition size should be 1.5 to 2 times the size of your ram?

That recommendation is from years ago when RAM was measured in MB rather than GB, and running out of RAM was more likely. As mentioned, if you wish to hibernate your system, it's best to set your swap to be the same size as your RAM. Other than that, with 8GB RAM you may rarely see any swap used.

---

### Post by Jason_Minns on 2014-05-24
Thanks to all who responded. It makes a lot more sense to me now. Atleast the next time I read about swap, there won't be as much confusion. I know the next machine I configure won't have 15 Gb of Swap, unless I have an excess of several Tbs of space to throw around, and even then I'll think it through. 

It appears all is in working order. My swap shows up in Gparted. It just eases my mind to know for sure that all is working soundly.

Thanks again, 
Jason

---

