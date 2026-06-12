---
title: "Using ram as a swap..."
date: 2007-05-30
forum: General Help
---

### Post by gopoo on 2007-05-30
I just upgraded to 2 gb ram , but ubuntu seems to use only 200-500 MB of it , 

can i use rest of the ram as swap ?

if yes , how ?

Thanks . :D

---

### Post by loathsome on 2007-05-30
.. Um, are you aware of what you're saying? :p

---

### Post by reckless2k2 on 2007-05-30
"swap" is a partition in linux unlike in windows. you can increase the size of your swap partition to adjust for the new ram size if you'd like though although i doubt you are going to need 2x to 3x of it. query enlarging swap partition.

---

### Post by gopoo on 2007-05-30
yep , i know ram can be use as swap , i just dont know how to do it OR is it possible in latest kernel or not....

---

### Post by drummingpariah on 2007-05-30
> **gopoo said:**
> yep , i know ram can be use as swap , i just dont know how to do it OR is it possible in latest kernel or not....

you do realize that swap is almost always used as slow ram, right?  Your system will first use your ram, and will use swap instead when you run out of ram.  Swap is also used for hibernate, because ram will lose everything in its memory when it is powered down.  What are you trying to accomplish here?  From the sounds of it you're aiming to make your system very unstable.

---

### Post by gopoo on 2007-05-30
i am aiming to make my laptop faster by using some extra ram ,,,, and as i realised that linux is using the swap even tho there is a space in memory. and from that 2 gb ram only 500 mb is used at most , so i am targeting the rest 1500 mb ram for swap memory , so virtually forcing the kernel to use my ram .

---

### Post by hillbilly on 2007-05-30
Using ram as as swap space is "oxymoronic". The  very reason you need swap is because the RAM memory becomes full. So then the designated swap space kicks in to "help" RAM.
   Now if you are planning to use part of RAM as swap that means you dont need swap at all and the logical thing would be to delete the swap partition altogether. But be warned, I'm not sure how the system would react to that, i.e. I'm not sure whether the system requires some sort of swap partition (whatever be the size) !!

---

### Post by hillbilly on 2007-05-30
oh I missed drummingpariah's last post. If swap is used for hibernate, then you certainly cannot use your RAM as a swap and also your swap size must be comparable to that of your RAM.

---

### Post by gopoo on 2007-05-30
thats what i thought , removing swap partition altogether...but then  , linux kernel is optimized to cache extra data as swap , rather than on ram... i google for same thing and found following links...

[http://kerneltrap.org/node/3660](http://kerneltrap.org/node/3660)

---

### Post by gopoo on 2007-05-30
> **hillbilly said:**
> If swap is used for hibernate, then you certainly cannot use your RAM as a swap and also your swap size must be comparable to that of your RAM.

Is hibernate is buit in to the kernel ? or on top of the kernel ?

I am just wondering about the possibilities of using a single file for hibernation...

---

### Post by arvevans on 2007-05-30
I think (don't quote me here) that the reason you may be seeing stuff in swap when you still have available RAM is that some sleeping tasks are paged out to swap when not actively running.  It works this way in UNIX, and Linux, being a POSIX compliant OS, is like UNIX in many aspects.  This frees up RAM for use by actively running programs, and thus makes your computer run more efficiently.

Making a RAM based file system may be possible.  It also might also be possible to tag this as SWAP.
However, this sounds like it would just subtract from your available amount of RAM, for only a very limited speed increase when paging to and from swap.

My expectation is that if you downsized your RAM by making part of it into swap, the end result may be a slower computer because this would require more paging of active tasks into and out of swap.  This is really a trade-off of how much RAM you routinely use versus how much swap you usually need.  But, why cripple you computer in that way when you can just use all your RAM as RAM and still have overflow storage, idle task paging, etc. in a disk based swap partition?  Are you using a very slow hard disk and trying to compensate for this situation?

If you have USB and USB-based pen drives, it is also possible to designate one of these as swap.  I'm not sure what this would get you, but it might be worth a try?

Arv
_._

---

### Post by dnzz on 2007-05-30
> **drummingpariah said:**
> you do realize that swap is almost always used as slow ram, right?  Your system will first use your ram, and will use swap instead when you run out of ram.  Swap is also used for hibernate, because ram will lose everything in its memory when it is powered down.  What are you trying to accomplish here?  From the sounds of it you're aiming to make your system very unstable.

I don't think swap is used for hibernate because i have 2gig of ram and no swap but i can hibernate.

Also i noticed that if your ram is not full ubuntu do not use swap location. I used to allocate some memory for swap and ubuntu never used it so i removed it.

---

### Post by psusi on 2007-05-30
> **dnzz said:**
> I don't think swap is used for hibernate because i have 2gig of ram and no swap but i can hibernate.

Also i noticed that if your ram is not full ubuntu do not use swap location. I used to allocate some memory for swap and ubuntu never used it so i removed it.

No, swap is used for hibernation.  You must either be thinking of suspend, or you actually do have swap.  

As the others have said, it makes no sense to use ram as fake ram when you are out of ram, which is what you are suggesting.  Linux won't swap things out unless you start using most of your ram.  You can tweak the parameters that control this by modifying the values in /proc/sys/vm.  The most interesting one is probably swappieness.

---

### Post by drummingpariah on 2007-05-30
> **psusi said:**
> No, swap is used for hibernation.  You must either be thinking of suspend, or you actually do have swap.  

As the others have said, it makes no sense to use ram as fake ram when you are out of ram, which is what you are suggesting.  Linux won't swap things out unless you start using most of your ram.  You can tweak the parameters that control this by modifying the values in /proc/sys/vm.  The most interesting one is probably swappieness.

I had been looking around off and on for the /proc/sys/vm settings all day, thanks for posting that.  Basically, not using swap won't make your system much faster for everyday tasks.  If you're doing something really intense, all of your ram will be used to its fullest (try compiling a new kernel, or playing DoomIII).  I'm quite certain that swap is used for hibernation because it used to be a huge pain with Debian trying to get Hibernate to work, you had to create a separate fat32 partition and create a file within that partition that identified it as a hibernate partition.  I did a happy dance when the use-swap-for-hibernate was developed, and that's the main reason that the installer automatically creates a swap partition that's RAM+VideoRam+256buffer.  That way it can save everything that you're actively working on so when you restart, it'll pop right back up where you left off.

---

### Post by eXisor on 2007-05-30
I found this discussion on the virtualbox forums, and oddly enough, it's the same thing but with a crazily valid reason for wanting it. 

The section I quote is relevant to the 'fs in ram' part of our discussion.

[quote='Technologov']

mount -t ramfs My_ramfs /mnt/ramdisk -o maxsize=10000 
-or- 
mount -t ramfs My_ramfs /mnt/ramdisk 

The difference between "ramfs" and "tmpfs" is that tmpfs is real RAM + swap, while ramfs uses real RAM only, there is also an option of compressed RAM disk. This "ramfs" is fully dynamic and is giving back to host all RAM, once the file(s) that reside on it gets smaller.[/quote]

Taken from [http://forums.virtualbox.org/viewtopic.php?t=113&highlight=ramfs](http://forums.virtualbox.org/viewtopic.php?t=113&highlight=ramfs).

The discussion between Technologov and kilou towards the bottom of the first page is where to start. 

They explore, so far unsuccessfully, the possibility of getting a virtualbox host & client to share ramfs swapfile space, in the hope of circumventing the virtual machine problem that ram is allocated at vm startup, not dynamically allocated as the need arises. Their theory is a swapfile in ramfs can shrink and grow, and is going to be rather quicker than a hdd, so one can start a vm with the barest minumum ram - they mention xp starts with 32mb - yeah, right - and then to let the swapfest begin, dynamically allocating 'ram' by growing and shrinking ramfs as the needs arise. 

Ingenious, hey? If only.

But there you have it. Scoff ye not. There are no silly questions or ideas.

---

### Post by zekopeko on 2007-05-31
if you want to make linux/ubuntu use more ram for caching try looking at this post

[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

i think that's the thing you are looking for.

---

