---
title: "How do I check a USB key is really size reported"
date: 2015-07-02
forum: General Help
---

### Post by kazakore on 2015-07-02
I have recently bought a few cheap(ish) large size USB keys. Went directly from the Amazon shop, rather than a third party reseller or Ebay etc, so hopefully they are genuine and have the storage capacity reported but I would like to check this if possible.

Currently I am thinking make a file (how?) of say 8 or 16 GB and then copy this file across multiple time, say using a script putting it in folders with names counting up in number, and then do an md5 checksum on each copied across file. Hands with writing a bash script to do this (I've never got used to using While or For in CLI or Bash yet) could be useful.

Or it did pass my mind, would partitioning the drive into multiple smaller partitions and then just attempt writing into the partition that uses the highest section of the physical space. If the file in this partition has good integrity we can assume the rest of the device is good as reported.

How would you do it? Are there any tools to do so automatically? All my search results just came up with testing drives which have failed with use (SMART, bad sectors etc...)

---

### Post by TheFu on 2015-07-02
I would create a single large partition with ext4 and mount it.  Then use **df -h** to see the total storage. That is the total storage for the device. After formatting, it is slightly less than the amount on the package.

BTW - amazon has 3rd party sellers on it and not all of them are reputable.

If you want to make an 8G file, use **dd**. It is possible to make a file of any size with dd using either /dev/null or /dev/urandom as inputs.

When it comes to USB flash memory - there is cheap stuff and there is good stuff. Do the research *BEFORE* purchase for the fast, automatic write-leveling, flash memory models so you aren't mad after only a year of use.  Flash memory wears out. Specific models from specific vendors have extra features to level the wear across the entire storage, thus reducing the writes to any 1 area.

---

### Post by kazakore on 2015-07-02
> **TheFu said:**
> I would create a single large partition with ext4 and mount it.  Then use **df -h** to see the total storage. That is the total storage for the device. After formatting, it is slightly less than the amount on the package.

I have read many reports (obviously being mostly Windows users as they have the highest userbase) about a lot of flash keys claiming to be say 128GB, formatting at 128GB but then anything after about 16GB not actually being readable after being supposedly written to the device. Are you sure such a simple check as above would work against such situations? Which is what I'm trying to protect myself from!

> BTW - amazon has 3rd party sellers on it and not all of them are reputable.

Yes I know. That's why I specifically stated I bought directly from Amazon themselves and not any of their third party sellers!! Fingers crossed to help me escape getting fakes...

> If you want to make an 8G file, use **dd**. It is possible to make a file of any size with dd using either /dev/null or /dev/urandom as inputs.

Ahh urandom, was wondering how to not have all zeros and thus something with a md5/sha checksum that is actually worth checking for.

> When it comes to USB flash memory - there is cheap stuff and there is good stuff. Do the research *BEFORE* purchase for the fast, automatic write-leveling, flash memory models so you aren't mad after only a year of use.  Flash memory wears out. Specific models from specific vendors have extra features to level the wear across the entire storage, thus reducing the writes to any 1 area.

Bit late now but I have them more for backup usage that is less unacceptable to damp, humidity, extreme temperature and shock than a disk based drive so performance matters should be quite so important, assuming they have the reported space. But for completeness I bought.
2x 128GB SanDisk Cruzer Blade (SDCZ50-128G-B35)
1x 256GB Corsair Flash Voyager Slide (CMFSL3B-256GB )

---

### Post by kazakore on 2015-07-03
So nobody done this and want to expand on best, easiest way??

---

### Post by TheFu on 2015-07-03
> **kazakore said:**
> So nobody done this and want to expand on best, easiest way??

Sorry - I'm confused. I this hard?
* format to ext2 (probably don't want journaling)
* mount the storage
* copy over 120G of data/stuff/crap/whatever - slightly less than the advertised size since a "format" takes a little space.
* Does that give an out-of-space error or not?

If it does, see how much fits and you know if there are any limits and whether you got what you paid for or not.

Those steps are basic skills for anyone running Linux (or any OS), IMHO.

When you are done, reformat to the appropriate file system type for flash memory.

---

### Post by kazakore on 2015-07-03
> **TheFu said:**
> Sorry - I'm confused. I this hard?
* format to ext2 (probably don't want journaling)
* mount the storage
* copy over 120G of data/stuff/crap/whatever - slightly less than the advertised size since a "format" takes a little space.
* Does that give an out-of-space error or not?

If it does, see how much fits and you know if there are any limits and whether you got what you paid for or not.

Those steps are basic skills for anyone running Linux (or any OS), IMHO.

When you are done, reformat to the appropriate file system type for flash memory.

Yes that was one way I mentioned as a possibility, I just wondered if there was any easy or more recommended way. Such as the multiple partitions so you don't have to copy across a full 120 odd Gigabytes (or double that for my 256GB key) just testing the partition that *should* use the last sectors. But I didn't know if such things as physical sectors to be partitioned existed with flash storage. So copying across a known large file multiple time and doing md5sum on the last copy of it (or enough random files and try and read the last few copied back) is definitely the easiest/most recommended way to do this?

---

### Post by TheFu on 2015-07-03
Flash storage is solid state. I don't have any belief that there is a physical layout involved at all. Sectors, especially on write-balanced devices, will be moved around as needed. This is all logical.

If you want to see whether the flash storage will hold about 128G of data, I'd copy over a 10G file 12 times and change the name every time. Ain't no shortcut that i can see. If it is USB3 - this is about an hour, right?

cp ./10gfile /mnt/10gfile-a
cp ./10gfile /mnt/10gfile-b
    ...
cp ./10gfile /mnt/10gfile-Z

That ought to do it.

---

### Post by kazakore on 2015-07-03
OK, thank you very much.

Would it not be possible to do a little while/for loop for this? Something along the lines of (sorry I don't know Bash syntax...):
(Create 8GB file using dd and urandom)

#!/bin/bash
i=0
while [ i -le 16 ]
do
mkdir $((i++))
cp if=/path/to/created/8GB/file of=/usb_mount_path/$i/
done


Would this wait until each write is finished before starting the next one? Or can I used && in Bash to make sure it does so? How far off is my syntax?

---

### Post by kazakore on 2015-07-09
Nothing useful from you guys in near a week. Less than one day after posting on a mailing list (for which is really was a bit of off topic conversation I would have preferred keep off there) and I get what seems to be a link to the exact tool I need!

If anybody else wants to try testing flash devices for fakes, pretty much automating the method I outlined above, then maybe give this a try. I know I will be!

[http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)

---

