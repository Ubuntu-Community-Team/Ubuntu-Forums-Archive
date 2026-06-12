---
title: "configuration question"
date: 2022-11-30
forum: General Help
---

### Post by dgkking on 2022-11-30
I am running Ubuntu 22.10 64 bit, using a intel core i5 10600KF x12 processor with 16 Gb ram and a Nvidia GeForce GT 710 graphics card: Not a very high spec machine, I know but it is all I could afford. My question is what is the best way of configuring it to get the best out of what I have got without spending any more money that I have not got.
 It's a lot to ask but I thought asking someone with more knowledge then me for help in this direction would be better than making mistakes that I am bound to make by just jumping in myself. I am going to use the computer as a desktop for everyday use of libre office, the internet, email and minor graphics etc, nothing professional or too demanding. i would like it to be as stable as possible. Any help would be gratefully received.

---

### Post by ian-weisser on 2022-11-30
Are you assuming that stock Ubuntu releases are somehow inefficient or incomplete or crippled in some way? They are not.

Are you encountering any performance or stability problems? If not, then changes or customization seems unnecessary.

The pre-installed applications will easily handle most of your proposed uses.

Your hardware specs are much more powerful than mine, and stock Ubuntu runs smoothly, responsively, and reliably.

---

### Post by dgkking on 2022-11-30
Hi Ian
No i am assuming nothing, But I have spent some time reading and have found lots of messages about problems that many people are having which suggest  one needs to spend a bit of time configuring their computers to do what they require. For instance the amount of ram one needs to give their computer a chance of doing what they want. I have guessed that the amount I have put in will enough to do what I want but I don't know.There are different ways of setting up your swap  like a partition, a file, or  in ram by using zram I believe. I ask my question because I don't assume I know everything  or all the problems I might encounter. From what I have read there are people with a great deal more knowledge than I do. So the best way forward was to accept these facts and ask those that might know. Surely that is what the forum is about. Why would you think I might assume that stock Ubuntu are inefficient or I was having any performance or stability problems. The messages I read would suggest that there are problems caused by not configuring your computer correctly. i don't need to be experiencing any problems before asking my question, just a need to tried to prevent any problems before I encounter them. I would have thought that the fact I was running Ubuntu rather than windows was a good sign that I thought it was a good enough operating system.
dave

---

### Post by TheFu on 2022-11-30
> **dgkking said:**
> Hi Ian
No i am assuming nothing, But I have spent some time reading and have found lots of messages about problems that many people are having which suggest  one needs to spend a bit of time configuring their computers to do what they require. For instance the amount of ram one needs to give their computer a chance of doing what they want. I have guessed that the amount I have put in will enough to do what I want but I don't know.There are different ways of setting up your swap  like a partition, a file, or  in ram by using zram I believe. I ask my question because I don't assume I know everything  or all the problems I might encounter. From what I have read there are people with a great deal more knowledge than I do. So the best way forward was to accept these facts and ask those that might know. Surely that is what the forum is about. Why would you think I might assume that stock Ubuntu are inefficient or I was having any performance or stability problems. The messages I read would suggest that there are problems caused by not configuring your computer correctly. i don't need to be experiencing any problems before asking my question, just a need to tried to prevent any problems before I encounter them. I would have thought that the fact I was running Ubuntu rather than windows was a good sign that I thought it was a good enough operating system.
dave

Your system is plenty capable as it is.  If you want reasonable, specific, recommendations, we need facts.  Run:
```
inxi -Fxxxz
```
and post the output here. That would be a start.  Also, review the system logs for warnings and errors, research each. Not all errors/warnings are really problems.  Sometimes looking for something and not finding it is fine.

But any Linux should behave with reasonable performance with that hardware.  Using an NVMe SSD and optimizing the swap would be about the only things I'd even guess _might_ help, perhaps 3%.  With that amount of RAM and the described workload, there shouldn't be any issues unless you have 500 tabs in a browser.

To see more about swap, run 
```
free -hm
```

---

### Post by ian-weisser on 2022-11-30
> **dgkking said:**
> Hi Ian
No i am assuming nothing, But I have spent some time reading....


I'm very pleased to read that your research has prepared you well.

The next step is testing.

The Ubuntu Desktop installer has a 'Try Ubuntu" environment specifically so you can test your hardware with Ubuntu without committing to an install.

Test your video card. Test your camera, microphone, speakers. Test your network connection. Play a movie and test your audio and video. Test your printer. Test all your USB peripherals.

Then you will KNOW if you have any hardware-related problems to ask about. If you encounter too many problems, then don't install.

Most folks do not encounter any serious problems.

Advice: Make your first install *successful* instead of perfect. Stick to the default settings. Once you have done a successful install or two, then you can explore and customize. For example, stick to the swap defaults for your first install. If you want to get exotic, do that on your second or third install.

---

### Post by TheFu on 2022-11-30
Ian makes good points. On any new hardware, I use the "Try Ubuntu" boot just to see what areas might have issues, then depending on any specific issue, I'll do a little research to decide if that hassle is likely to be forever, for a few months or has already been handled in a current, easily installed, new kernel.

Besides that, peripheral hardware can cause frustration. I have an all-in-one printer/scanner/fax that was supported but seems to have lost that support.  It was a $75 device that I bought in 2008, so I don't feel like I've been burned, but the replacement will specifically have 
a) driverless printing 
b) driverless scanning - actually, I want scanning to write to a USB device without any computer connected at all
c) faxing without any computer connected.

Driverless printing has been around a fairly long time and works easily. [https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)  We just need to seek out printers that support it.

Driverless scanning isn't here for the most part, not yet. [https://openprinting.github.io/gsoc2019/02-ipp-scan-server/](https://openprinting.github.io/gsoc2019/02-ipp-scan-server/) and [https://openprinting.github.io/gsoc2019/03-sane-module/](https://openprinting.github.io/gsoc2019/03-sane-module/)  But scanners do exist that will write to USB storage.  That's a good compromise for my needs and a number of Linux-friendly device makers have this capability.

Around June 2020, we had a long thread about swap in these forums.  Find that thread and review it if you want to know more about swap.  My advice about swap for desktops is overly simplistic, but here it is
1) Use a swap partition or logical volume, never a swap file.  Swapfiles are relatively new in Linux, unlike swap partitions and LVs which has been used for multiple decades.
2) Size the swap to be 4.1G in size. Any smaller and modern, bloated, browsers will lead to a system crash on computers with 8GB or less of RAM.  For compujters with more RAM, 4G shouldn't be needed, but we need help recognizing when swap is being used so we can' prevent out of memory problems that Linux doesn't handle well.  Actually, no Unix does.  On a server, swap should be tuned to the workload. These days, I try to have 500MB of swap on my servers to handle unusual memory needs, but 1G is where I start on a new server with new OS and new workloads.  System monitoring for a month lets me see how much is actually used, so it can be tuned, if I remember.
3) Place swap onto an internal spinning HDD, not an SSD.  This helps users "feel" the computer getting slower so they can close huge applications and avoid system crashes.

There are lots of details, but for most people those are more than enough.

---

### Post by mIk3_08 on 2022-11-30
> **dgkking said:**
> My question is what is the best way of configuring it to get the best out of what I have got without spending any more money that I have not got.
I prefer that you should be active here in this community "ubuntuforums" I'm sure will learn a lot here just by reading the thread post here in this forum. Then ask whatever you want to learn more because their are a lot in here in  this community that are very well versed that are willing to help and guide you  thru all the way of using the Operating System. Actually, based on my experience the best Ubuntu release I used is the LTS (Long Term Support) release. Regards and cheers.

---

### Post by Impavidus on 2022-12-01
You sound as if you're apologising for the poor specs of your computer. It's better than what most of us use. As long as you don't open 50 tabs in your webbrowser simultaneously, it should handle your needs without any problems. I'm on an 11 year old laptop with 8 GiB RAM (it originally came with 3 GiB) and it never uses swap.

If you want stability, it's best to avoid the interim releases and stay on Long Term Support. Interim releases have a somewhat experimental nature and are less stable and a release upgrade isn't good for stability either. 22.10 is an interim release, so you'll have to upgrade to 23.04, 23.10 and 24.04 LTS within 3 months after they get released. You can't downgrade, so either you stay on the interim releases until April 2024 or you fresh install 22.04 LTS now.

---

### Post by dgkking on 2022-12-01
[http://paste.ubuntu.com/p/FhPBXTRJdT/](http://paste.ubuntu.com/p/FhPBXTRJdT/)

---

### Post by TheFu on 2022-12-01
Use an LTS release.  

There are 2 reasons not to, but 1000 better reasons why you should.  22.04 is the current LTS.  

Depending on the GUI/DE used, it will be supported until 2025 or 2027.  Most of the DEs only get 3 yrs of support, so moving to a new LTS every 2 yrs is required for desktops.  The Ubuntu Server gets 5 yrs of standard support, but since it doesn't have any GUI, it isn't suitable for desktop users.

I didn't see anything in the inxi output that was scary.
I'm not paid enough ($0) to look through full dmesg output. Sorry.  Just not something I'm willing to do.  Throwing tons of crap into a paste makes lots of assumptions.  BTW, in a month, your like will be useless and others trying to learn from this thread cannot.

---

### Post by grahammechanical on 2022-12-01
> There are different ways of setting up your swap  like a partition, a file, or  in ram by using zram I believe.

That is true but with 16 GB RAM it is very unlikely that swap will ever be used especially as you are not going to use your machine for any thing professional or too demanding. Besides, the latest versions of Ubuntu by default use a swap file that can be enlarged or shrunk as needed. In the old days the rule was to have a swap partition that was 1.5 times the amount of RAM. That was acceptable when RAM was between 1GB and 4GB. It makes no sense for you to have a 24GB swap partition. We can run Ubuntu in 25GB of disk space.

Ubuntu 22.04 is the latest Long Term Support (LTS) release. In System Settings>Power you will get an option to choose one of three power profiles. They are Balanced; Power Saver and Performance modes. System Settings is where can can make various configuration changes.

Regards

---

### Post by TheFu on 2022-12-02
A few years ago, the kernel guys changed some defaults to make use of a little swap. If there isn't any swap at all, some performance stuff is disabled, so even on systems with well understood workloads, it is smart to have a little swap just to enable the better performance.

A few examples:
"A"
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            31G         20G        2.5G        182M        8.8G         10G
Swap:          4.3G        1.5G        2.8G
```

"B"
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           14Gi       4.6Gi       993Mi       2.0Mi       9.2Gi       9.8Gi
Swap:         4.1Gi       1.3Gi       2.8Gi
```

"C"
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       914Mi       270Mi       9.0Mi       2.7Gi       2.7Gi
Swap:         4.1Gi        34Mi       4.1Gi
```

A: this system has 32G of RAM and runs a number of virtual machines 24/7.  The amount of RAM actually used is just a little over 50%. It started with 16G, but kept swapping, so I added another 16G. Above, it is using 1.5G of swap, but it is also using 8.8GB for disk and network caching.  I haven't moved any large files in at least 12 hrs, so that caching is purely for better performance. Note also that it isn't using the full 32G of RAM and has decided that some swap should be used too.  BTW, I'd turned the "swappiness" kernel parameter way down, 10, to encourage more RAM be used before swapping is invoked.  I'll probably relook at this system, as it will be getting a CPU upgrade this weekend.  13K ---> 20K passmark upgrade. The new CPU was really cheap, I couldn't refuse.

B: this system has 16G of RAM and runs a number of virtual machines 24/7 while also doing media center duties, NFS, Calibre, and transcoding of most media files, which is hard work. It is not busy now. It doesn't have any GUI, so it isn't running any GUI programs right now and the memory use shows that. Note the buffers in use are more than the actual RAM used for programs. Again, "some" swap is being used, though I've turned the "swappiness" kernel parameter way down to encourage more RAM to be used.  Some of the RAM is taken to be used by they APU running this system.

C: This is my main desktop and is allocated 4GB of RAM. It is running heavy desktop programs like Firefox and Thunderbird. This browser is running on "C". Because it is a virtual machine actually running on system "A" above, anything that uses RAM is included in that machine's information too.  The video RAM used is minimal on VMs, since local rendering is handled by software only, not hardware.  If more RAM is needed, i.e. more swap gets used, then as a VM, I can allocate more to the system fairly easily. That's one of the great things about virtual machines.  We can give them the resources they need, if there are some available on the physical host still.  Heck, if I didn't care about total performance, I could give this VM 128GB of RAM, provided the swap on the host system was about that size too.  I played around with settings like that when I was younger and thought of swap as magical, cheap, RAM.  Over-allocation just makes systems slow. The goal is to have exactly the amount needed, but no more.  Even with NVMe SSDs, the speed difference between that storage and real RAM is staggering.  Plus, RAM is crazy cheap again.  Saw 32G for $80 last week and this was the same model RAM sticks that I choose for normal builds, not some non-name cheapo-cheapo-cheapo RAM.

So, anyone interested in a slightly used Ryzen 2600. Seems I have an excess CPU that needs a good home. The fan will come with it.  It is being used now, so it works perfectly.

---

### Post by dgkking on 2022-12-03
Hi
I can see the sense in what you say about using a LTS release and do intend to follow that advice . I thank you for looking at the inxi -Fxxxz report for  me and am pleased that you did not see anything scary in it. I do understand what you have said about the dmesg output. I was not expecting you to read it or give me advice unless you were willing and had the time to do so. I seek advice, not expect or demand it in any way. I do not understand what you said about throwing tons of crap into the paste. I was supplying information nothing more. What assumptions are you talking about.  > BTW, in a month, your like will be useless and others trying to learn from this thread cannot Again I do not understand the remark you have made here. What do you mean by "my like"? and why will it be "useless in a month"? Why won't "others trying to learn from this thread" be unable to. It appears that I have offended you in some way, that was not my intention.
dgkk

---

### Post by dgkking on 2022-12-03
Hi
When i use free -h it shows   free -h
```
               total        used        free      shared  buff/cache   available
Mem:            15Gi       1.8Gi       6.6Gi        49Mi       7.1Gi        13Gi
Swap:          4.0Gi          0B       4.0Gi
```
Which if I understand means there is enough and at that point it wasn't using any. My swappiness has been set to 10 and my vm.vfs_cache_pressure=50 following advice found out while reading. Again following advice read I have set up the swapfile to 4 gigabyte and enabled zswap. I don't know if this is right or needed as there is different advice and ideas found so it is hard to know hence why I have asked for advice from more experience  people then I at this forum. I found it difficult to find out and still don't know what is the min&max size of the partitions used when setting up Ubuntu in the first place. I was advised to use a separate partition for my home directory which I have done.  
dgkk

---

### Post by TheFu on 2022-12-03
A wasn't offended. Just stating facts, as I saw them.

The swap size and swap settings seem good to me for a desktop, from what I can tell. Again, I'd encourage finding the long thread about swap from 2020 to see other discussions and opinions about swap.

As for setting up storage, there are many opinions.  I've posted many examples in these forums over the years, sometimes with explanations for "why", which will be different for each of us.  Also, I've posted specific aliases and disk commands to show storage layouts in a fairly clean way.

Because I use LVM for my storage management, there are certain things that I do that I wouldn't do if I were using partitions for simplistic storage management.  LVM is so flexible that I can't imaging NOT using it.  

For data only, if I were just learning about enterprise storage management tools, I'd use ZFS, not LVM.  ZFS merges both volume management and a file system together into a single tool.  It supports snapshots of volumes and amazing secure remote backups of those snapshots using the zsend command.  If you have ZFS, you have the ability for excellent remote backups built-in.  There are some scripts to manage snapshots and backups with ZFS which are fairly popular these days.  Don't use ZFS for the OS, yet. It isn't quite ready, especially for someone just learning Linux/Unix stuff.  Hard core ZFS zealots do use ZFS for the boot OS storage and sometimes there are issues that aren't trivially handled, so a deeper understand of ZFS and the OS in general is needed to get back to a working system.  Not for noobs, at least not yet.

If you have more than 1 disk connected to a system, I'd avoid BTRFS, but for a laptop and a system where you never plan to run virtual machines, BTRFS might be a good choice.  There are some odd failures with BTRFS when people try to use it for RAID-anything or for virtual machines, which is why I'd say to avoid it, but for a laptop with 1 SSD inside and occasional USB flash storage connected, BTRFS can provide an intriguing interface for enterprise storage volume and file system capabilities. It also supports snapshots like ZFS and LVM do, so perfect backups for snap-shot-aware backup tools are possible. 

If it isn't clear, storage architecture and choices are mostly driven by helping to get excellent backups AND to provide different mount point options for increased system security.  That's a reason why /var/ and /tmp/ and /home/ should all be separate file systems, so we can mount them separately each with different options.  For even more security, /usr/ can be mounted read-only.  There are trade-offs in doing this, since package management  modifications through APT won't work on read-only file systems. There are just a few books that are worth having related to Linux Security from an overview and "why" perspective. These are timeless just for the "why" aspects.  They don't get updated that often because the commands change about every decade and over a decade after publishing a great book, the drive to update it for new commands is seldom there ... but the same ideas still make sense.

---

