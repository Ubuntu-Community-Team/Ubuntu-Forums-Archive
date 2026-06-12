---
title: "gparted problem"
date: 2017-02-13
forum: General Help
---

### Post by chunkydrew2 on 2017-02-13
[COLOR=#141414][FONT=&quot][IMG]http://www.linux.org/attachments/gpartedscreenshot-02-13-17-png.2520/?temp_hash=02cae2b96188c268f6c6357743f41916[/IMG] 
[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]I'm having trouble with my partitions in gparted. I have Ubuntu 16.04 (/dev/sda5) and Mint 18.1 (/dev/sda2) installed on this dual-boot laptop. I had each setup with 140.15GB of space. When I noticed that I was getting fairly low on space in Ubuntu, I decided to shrink Mint by 20Gb and grow Ubuntu by the same amount. Shrinking Mint was no problem, but now that space is just unallocated, since gparted won't allow me to grow the Ubuntu partition to use the new unallocated space. Is that because they are not adjacent? Is there a workaround?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2017-02-13
You can not resize a partition when it is mounted. You need to boot to a 'live' session from install media ('Try Ubuntu'), launch Gparted and do it there. If the partition you want to extend is sda5, no, it is clearly not adjacent with the free space. Not sure how you were going to put them together. :-k

A comment: Not sure why you've got your disk partitioned like that. Your install partitions only need to be about 20Gb and the storage partition can then be huge and contain all data (note that the install in sda2 takes up less than 10Gb). Having personal data in two different install partitions like you have is begging for redundancy, as in duplicate files and confusion. Still, you're used to your system I guess. You also only need about 2Gb for /swap unless you're hibernating in which case it should be size of installed RAM. :)

PS: You could extend sda6 and chuck a bit of data in there from sda5, if that's what you're looking to do.

*** NOTE: Just noticed that sda6 is LVM. All bets are off. Know nothing about them except they are stubborn and need special treatment if they are going to be resized in any way. You have a big road block jammed in there. Can't help with that, sorry. Also note that it has an ugly exclaimation point next to it and that is not usually a good sign. Despite this, why don't you just put some data in there if you want some space on sda5? There's heaps of room there.

Please attach large pics using 'Adv Reply' or 'Go Advanced' and the paperclip icon. Spare a thought for potential helpers with slow connections or vision issues. :)

---

### Post by Dennis N on 2017-02-13
You can't take space from sda2 and combine with sda5 because (as you surmised) they are not physically adjacent. You could reduce sda6 from the right, and expand sda5 into the unallocated space that results, but this I believe is risky since you are moving data from the start of sda5. I would not recommend it. But, I recall reading a thread here where it worked out ok (sorry, have no link to this). 

You don't have LVM, even though a flag is set. If sda6 was for LVM, then the file system column would say **lvm2 pv**, not ext4.

---

### Post by Bucky Ball on 2017-02-13
> **Dennis N said:**
> You don't have LVM, even though a flag is set. If sda6 was for LVM, then the file system column would say **lvm2 pv**, not ext4.

And there's that answered. Thanks, Dennis. Told you I knew nothing about LVM. ;)

---

