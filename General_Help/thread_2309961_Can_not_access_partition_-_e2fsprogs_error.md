---
title: "Can not access partition - e2fsprogs error"
date: 2016-01-14
forum: General Help
---

### Post by mikee2 on 2016-01-14
While trying using Gparted to access a partition /dev/sdb2/ on my recently cloned drive i noticed some errors:


[IMG]http://i.stack.imgur.com/xJYIa.png[/IMG]

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4
file system support: e2fsprogs v1.41+

I checked with Synaptic Package Manager to see, and I already have  e2fsprogs v1.42.9-3 installed. 
I looked up some googles searches on the issue and tried the  following solutions that have worked for other people:


  ```
sudo fsck.ext4 -f /dev/sda6 
sudo touch /forcefsck 
Sudo reboot

```  


this seemed to work temporarily (there was no longer an exclamation mark next to the partition in Gaprted), but after another reboot or two, the problem still persists. 

Another thing I tried was:

```
sudo mke2fs -n /dev/sdb2
``` 

with the output being:


[COLOR=#0000cd]mke2fs 1.42.9 (4-Feb-2014)[/COLOR]
[COLOR=#0000cd]Filesystem label=[/COLOR]
[COLOR=#0000cd]OS type: Linux[/COLOR]
[COLOR=#0000cd]Block size=4096 (log=2)[/COLOR]
[COLOR=#0000cd]Fragment size=4096 (log=2)[/COLOR]
[COLOR=#0000cd]Stride=0 blocks, Stripe width=0 blocks[/COLOR]
[COLOR=#0000cd]3203072 inodes, 12800000 blocks[/COLOR]
[COLOR=#0000cd]640000 blocks (5.00%) reserved for the super user[/COLOR]
[COLOR=#0000cd]First data block=0[/COLOR]
[COLOR=#0000cd]Maximum filesystem blocks=4294967296[/COLOR]
[COLOR=#0000cd]391 block groups[/COLOR]
[COLOR=#0000cd]32768 blocks per group, 32768 fragments per group[/COLOR]
[COLOR=#0000cd]8192 inodes per group[/COLOR]
[COLOR=#0000cd]Superblock backups stored on blocks: [/COLOR]
[COLOR=#0000cd]    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, [/COLOR]
[COLOR=#0000cd]    4096000, 7962624, 11239424
[/COLOR]
Then trying to restore one of the bad backup blocks with:

```
 sudo e2fsck -b block_number /dev/sdb5
``` 
with the output of that being:

[COLOR=#0000cd]Free inodes count wrong for group # [/COLOR][COLOR=#0000cd](lots of different #s here)[/COLOR][COLOR=#0000cd]
[/COLOR][COLOR=#0000cd]Free blocks count wrong for group [/COLOR]# [COLOR=#0000cd](lots of different #s here)[/COLOR][COLOR=#000000] there were numerous lines just like this with different numbers. It asked me if I wanted to[/COLOR][COLOR=#0000ff] Fix<y>? yes[/COLOR][COLOR=#000000] and I did hit YES each time. 

[/COLOR][COLOR=#0000ff]Free inodes count wrong (2939126, counted=2942022).[/COLOR]
 
/[COLOR=#0000ff]dev/sdb2: ***** FILE SYSTEM WAS MODIFIED *****[/COLOR]
[COLOR=#0000ff]/dev/sdb2: 261050/3203072 files (0.4% non-contiguous), 8357747/12800000 blocks[/COLOR]

This solution that worked for others, did nothing for me. After a reboot, I go back into Gparted and the alert for that partition is still present.  

I ran the test that Matt Symes described in his answer here on #16:

[http://ubuntuforums.org/showthread.php?t=2305215&page=2](http://ubuntuforums.org/showthread.php?t=2305215&page=2)

While this was informative and handy information to learn, it did not yioeld any practical results. The only folder that inside the mounted volume of the image file created was Lost & found with nothing in it. 

What is strange is that I can successfully boot from this drive despite not being able to access the partition in Nautilus or Gparted. I am thinking  that is may have been caused by the re-sizing of the partition after the cloning process, but can not  be sure, as it will still allow me to boot to this installation.



A more in depth desciption of the cloning process that took place before trying to access the drive can be seen at my post:
 [http://askubuntu.com/questions/720889/cloning-multiple-partitions-in-ubuntu](http://askubuntu.com/questions/720889/cloning-multiple-partitions-in-ubuntu)

Running 64 bit Ubuntu 14.04

---

