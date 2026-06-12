---
title: "A filesystem question that is too difficult to sumarize in a title"
date: 2020-09-30
forum: General Help
---

### Post by timothylegg on 2020-09-30
I have a Raspberry Pi 4 running Ubuntu Server 18.04.  In fact, I have four of them in a cluster but presently only one is doing any kind of work for me and I configured that one as a Minecraft server.  It had moderate, and at times, severe performance issues that are attributed to filesystem read/writes.  

I discovered something interesting.  If I created a tmpfs in RAM and launched the server from there, I had incredibly strong performance since read/writes at flash memory speeds were no longer a constraint.  The caveat is that the size of this filesystem is limited by the amount of RAM storage which, in this example, is just under 8GiB.  Power supply interruption is not considered a constraint.

There may be the occasion that game data would be hosted that would exceed 8GiB in size and there would be no RAM remaining for server or OS purposes.

I can visualize two scenarios as solutions:

[LIST]
[*]Hybrid approach where the most recently accessed files are cached in a specific RAM disk filesystem and this data is only stored to non-volatile storage either on command or as the oldest file is purged off to create space for a more recent file in the RAM disk. 
[*]A distributed, networked filesystem of RAM disks that optimizes the data storage location based on where it's accessed most frequently.  For example, three Pi devices that are always turned on could each host a 4GiB partition which would be collectively hosting a 12GiB partition. 
[/LIST]

The server software is proprietary and therefore infeasible to  modify, so these transactions would need to be invisible to it's environment.  Do open-source solutions for such problems even exist or is this still too new of an idea?

Note:  I also looked for USB-plugable RAM, or at minimum a USB-to-DDR socket adapter.  Apparently, nobody has asked China to make these.  All I could find on this topic were goofball types wanting to turn thumb drives into swap volumes.  In a world where I can buy SD-to-ATAPI adapters and USB mug warmers - how can these not exist?

---

### Post by TheFu on 2020-09-30
Perhaps use an SSD with USB3 connector?  Then you can make swap as large as you like, though if RAM is the main problem a different platform is needed. 5Gbps is pretty fast for storage. 
Does USB -to- DDR make sense? Wouldn't the performance be over 1000x slower? Check the performance. Maybe off by 1024^2 or ^4.
There are Intel systems easily available that support 256GB of RAM if you are bound by available RAM.

Can't we get much better performance for less money using a cheap Intel/AMD CPU+motherboard+RAM than the overpriced r-pi v4.  
[https://www.phoronix.com/scan.php?page=news_item&px=Raspberry](https://www.phoronix.com/scan.php?page=news_item&px=Raspberry)  
R-pi v4 w/ 8GB of RAM is $90 without PSU, case, and other needed stuff. People often get excited about $35 computers, but forget that is for the base model only. When compared against AMD and Intel, it isn't $/performance you seek when getting a Pi. It is something else.

If I were starting a new project, I'd go with 20.04 today. That's for any CPU architecture. If 20.04 isn't ready for r-pi, then I'd be ready to switch and check weekly.

---

### Post by Tadaen_Sylvermane on 2020-09-30
> 
[LIST]
[*]A distributed, networked filesystem of RAM disks that optimizes the data storage location based on where it's accessed most frequently. For example, three Pi devices that are always turned on could each host a 4GiB partition which would be collectively hosting a 12GiB partition.
[/LIST]
Not worth it. You would have ramdisks but they would be limited to lan speed between each other. Unless they have a pi with 10gb ethernet it's not even worth considering.

> 

[LIST]
[*]Hybrid approach where the most recently accessed files are cached in a specific RAM disk filesystem and this data is only stored to non-volatile storage either on command or as the oldest file is purged off to create space for a more recent file in the RAM disk.
[/LIST]
Supposedly possible but I can't imagine how you would do this.

Rpi are hobby computers that can be used as a light server or desktop. If you need more than they have on them then you need a real computer with real hardware that can handle gobs of ram. Running server off an ssd would be good but I agree on the ramdisk. At home our worlds combined barely break 1gb so I have them all ramdisked on my server. If this is your first foray into ramdisking a Minecraft server I will share my current script. It has the systemd services in the comments.

```
#!/bin/bash
# tadaen sylvermane | jason gibson
# minecraft server stop & backups
#
# originally sourced from init.d script found at
# https://minecraft.gamepedia.com/Tutorials/Server_startup_script


# relevant systemd service files #


##


# mcbackup@.service


# [Unit]
# Description = Minecraft Server Backups
# After = mcstart@.service
#
# [Service]
# Type = oneshot
# User = mcserver
# Group = mcserver
# ExecStart = /usr/local/bin/mcbackup %i
#
# [Install]
# Also = mcbackup@.timer


##


# mcbackup@.timer


# [Unit]
# Description = Timer For Minecraft Server Backups
# Requires = mcbackup@%i.service
#
# [Timer]
# OnCalendar = *:0/15
#
# [Install]
# WantedBy = timers.target


##


# mcramdisk@.service


# [Unit]
# Description = Loads & Unloads Ramdisk
# After = network.target
#
# [Service]
# WorkingDirectory = /home/mcserver/
# Type = oneshot
# User = mcserver
# Group = mcserver
# ExecStart = /usr/bin/rsync -auv --progress gameworlds/%i /ramdisk/
# ExecStop = /usr/bin/rsync -auv --progress /ramdisk/%i gameworlds/
# ExecStop = /bin/rm -r /ramdisk/%i
# RemainAfterExit = yes
#
# [Install]
# WantedBy = multi-user.target


##


# mcstart@.service


# [Unit]
# Description = Starts Servers
# After = network.target mcramdisk@.service
#
# [Service]
# WorkingDirectory = /ramdisk/%i
# Type = forking
# User = mcserver
# Group = mcserver
# ExecStart = /usr/bin/screen -dmS %i /usr/bin/java -jar /home/mcserver/server.jar nogui
# ExecStop = /usr/local/bin/mcbackup %i stop
#
# [Install]
# WantedBy = multi-user.target


# source #


. /scripts/mymainsource


# sourced variables#


# $NOW
# $POOLLOC


# local variables #


BACKUPLOC="$POOLLOC"/backups/minecraft
WORLDDIR=/ramdisk/"$1"
WORLDS=/home/"$USER"/gameworlds


# functions #


mc_save_func() {
    mc_screen_cmd_func "$1" save-off
    mc_screen_cmd_func "$1" save-all
    sync
    sleep 10
}


mc_stop_func() {
    mc_screen_cmd_func "$1" "say world saved"
    sleep 5
    for seconds in 15 10 5 ; do
        mc_screen_cmd_func "$1" "say stopping in ${seconds}"
        sleep 5
    done
    mc_screen_cmd_func "$1" "stop"
}


mc_screen_cmd_func() {
    screen -p 0 -S "$1" -X eval "stuff \"${2}\"\015"
}


# begin script #


find "$WORLDDIR"/logs/ -name '*.log.gz' -exec rm {} \;
mc_save_func "$1"
[[ -e "$WORLDDIR"/.ramdisk ]] && rsync -au "$WORLDDIR" "$WORLDS"/
case $(date +%H%M) in
    0300|1500)
        tar -czf /"$BACKUPLOC"/"$1"."$NOW".tar.gz "$WORLDDIR"/*
    ;;
esac
[[ "$2" == stop ]] && mc_stop_func "$1" || mc_screen_cmd_func "$1" save-on
find "$BACKUPLOC"/ -type f -mtime +3 -exec rm {} \;


# end script #
```

---

### Post by timothylegg on 2020-09-30
Yes, I can go an buy a mediocre desktop from a discounter and achieve an immediate goal, but I also mentioned Minecraft and Raspberry Pi as they are both familiar examples.

Let's put it to a more severe example:  Let's say I just ordered 60+ ASUS desktops and need to create a 40TiB drive that is common and available to all machines, because, who knows, you might want to do a distributed FFT of a 4.5 trillion element 2D array of floats captured from a radio telescope.  I would imagine that there are a more than a handful of people pay for this service using proprietary architectures.  For most people, it's easy to say Minecraft and a few Pi devices to get the idea across.

---

### Post by timothylegg on 2020-09-30
Thanks for that script.  I did that as an experiment to see what differences there were in performance.  It's not likely I will deploy Minecraft on a PI permanently (I already have a digital ocean server that hosts a couple of my websites and a MC Server since its not very busy at all.

Doing this, it raised the question in my mind of a distributed filesystem.  The pi only has a 1GHz Ethernet bandwidth, but we already have memory management built into the Linux kernel for prioritizing registers, caches, memory and swap - Certainly somebody applied this concept to filesystems distributed across machines for efficiently handling very large data collections.  I figured Minecraft+Raspberry would me an enticing learning experience - but I could also do a test case with md5sum and a bunch of VM's in VirtualBox.

---

### Post by metacell on 2020-10-01
Dumb question: Doesn't letting the disk buffers fill up and turning on write caching solve most of your problem automatically?

The fastest SATA SSDs are about 500 - 600 MB/s, while the fastest M.2 SSDs are about 5000 MB/s, and the theoretical maximum speed for USB 3.0 is 625 MB/s. So unless your PI supports USB 3.1 or 3.2, you're unlikely to get better performance out of USB-connected RAM than out of an SSD. And even then, you'd probably need top-end, expensive USB hardware, which negates the benefit of using a cheap computer like the PI.
I'll assume cost is a constraint, since otherwise you could just buy a high-end computer with lots of RAM or an M.2 SSD and be done with it.

For the same reason, 1 Gb/s Ethernet (150 MB/s) would give worse performance than an SSD.

With 10 Gb/s Ethernet (1500 MB/s), you should be able to get better performance than with a SATA SSD.
But having a distributed RAM disk that automatically moves around data to where its most frequently accessed sounds very complicated. The process of learning what data is needed where would have to start over each time you turn on your cluster, unless you save metadata about where RAM data should be stored to your SSD, making it even more complicated.

A much simpler solution, that would give better performance, would be to use one computer as a network RAM disk, and simply cache the data you need on the other computers. Then you could use a cheap PC as RAM disk (it only needs to support 16 GiB RAM and 10Gb/s Ethernet), and other cheap PCs to run your applications (they only need to support 8 GiB RAM and 10 Gb/s Ethernet). No special software would be needed; you just need to make sure your client computers use all available RAM as disk buffers. You could even save the cost of SSDs by letting them boot over the network.

---

### Post by TheFu on 2020-10-01
FYI - m.2 storage has 3 different protocols, so more needs to be specified.  

There are m.2 SATA, m.2 mSATA and m.2 NVMe storage devices. Each has different throughput specs. I've seen (mSATA and SATA and NVMe) to USB enclosures. These were all relatively cheap, less than $25. Perhaps paying more would provide better throughput. The NVMe ones were more costly overall and the NVMe SSD would be 20-40% more costly than the other two SSD m.2 interfaces.

10Gbps networking isn't yet "cheap" for home users, though it is getting there.  It is about 4-5x more expensive than GigE still and 10Gbps NICs are still much more expensive.  Sadly, vendors are trying to push 2.5Gbps and 5Gbps for "home" and 10 Gbps for enterprise so networking will become fractured. 10Gbps will take another decade before it is the default, just like 1 Gbps ethernet took from 2005 - 2015 to become the default.  Enterprise vendors will hold back the 10Gbps and 40Gbps hardware through pricing much longer than they held the 1 Gbps standards.

IMHO.

If someone wants to run huge clusters of computers, there are existing solutions that scale. Performance has always been about the interconnect between systems.  That's why infiniband was created.  I've deployed DB clusters of 500 nodes, but that's completely different than compute nodes.  I'm certain people here are more versed on the huge nodes of compute clusters from famous locations.  If you have a local LUG, you might find that a local university supercomputing team has a few member who can help.  My LUG has a few admins who manage the clusters for their universities and they can talk about infrastructure, but not the actual workloads.  Most corporate owned supercomputers don't get much press after being installed due to trade secrets, so their knowledge is often locked up, unfortunately.

---

### Post by Tadaen_Sylvermane on 2020-10-01
I apologize, I uploaded a wrong version. I noticed, fixed a few things. Now the script above is right. Didn't even know I had those few errors.

[https://github.com/jmgibson1981/general-scripts/tree/master/minecraft]("https://github.com/jmgibson1981/minecraft")

---

### Post by HermanAB on 2020-10-02
Two things come to mind: Increase the size of your disk caches (Depends on the file system used) and the other is a Distributed File System called Glusterfs.

---

