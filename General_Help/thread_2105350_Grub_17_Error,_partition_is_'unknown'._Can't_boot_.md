---
title: "Grub 17 Error, partition is 'unknown'. Can't boot or mount."
date: 2013-01-15
forum: General Help
---

### Post by yamagami on 2013-01-15
I appear to be facing the loss of my digital life...
After some GPU failure on my laptop, and the subsequent loss of the SSD drive, I got a nice new laptop. I managed to run a recovery on the SSD, and put the data on the bigger mechanical drive I used before (containing all of my digital life). 
At some point I connected that drive to a usb enclosure, mounted it on an Ubunutu laptop and all was fine. Then removed and replaced it back in the old laptop (which still works with external monitor) but now I get a Grub (I think 1.5) 17 error, the file system is 'unknown' and I cannot mount or boot that drive. 
I went though many posts about grub 17 error, though non helped. I tried testdisk though at the stage of listing files none could be listed as the filesystem was unknown.  
This is the output of boot-repair: [http://paste.ubuntu.com/1535948/](http://paste.ubuntu.com/1535948/)

In the span of 3 days I've lost 2 drives and I absolutely must figure out how to mount or boot this grub-17 error one. Any help is extremely appreciated

Harel

---

### Post by oldfred on 2013-01-17
Why grub legacy? Only versions since 9.04 will read ext4 partitions as Ubuntu tweaked it to work with the then new ext4 type partitions.

[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

Which looks correct as Boot-Repair was not able to mount sda5 either.

You might try e2fsck first.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

