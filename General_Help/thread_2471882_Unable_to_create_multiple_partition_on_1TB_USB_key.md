---
title: "Unable to create multiple partition on 1TB USB key"
date: 2022-02-11
forum: General Help
---

### Post by ylafont on 2022-02-11
Unable to create multiple partition on 1TB USB key


This is driving me nuts,


I am trying to create a multi-Partition 1TB usb key. 


No matter what i try, a problem exist with the second partition. 


In creating the drive i have 

[LIST]
[*]remove all previous partition
[*]Low level formatted the drive
[*]create all type of partition (Primary, secondary, Logical)
[*]used all type of fiel systems (ext2, ext3, ext4, ntfs)
[*]created them in the CLI and/or Gparted
[*]I have even left unpartitioned space at the end of the drive just in case.
[/LIST]


***The CLI reports the partition are there  but fails to mount he partition***
mount: /mnt/d: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error.




_**Gparted reports**_
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdb2 is missing
[IMG]http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci[/IMG]


What i am missing, what i am doing wrong any assistance is greatly appreciated, thank you in advance

Image
[http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci](http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci)
[IMG]http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci[/IMG]
[IMG]http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci[/IMG][IMG]http://nextcloud.eclipsephoto.net:800/nextcloud/index.php/s/ASxCDqcWNi2Mnci[/IMG]

---

### Post by oldfred on 2022-02-11
Did you purchase this from a reputable source?

Years ago before larger flash drives, we would see this where someone would internally modify a small flash drive to make it look like a larger drive and sell it as a larger drive. But it never was larger.

---

### Post by ylafont on 2022-02-11
regular amazon purchase, could that be  problem these days, I guess. these thins are so cheap these days not sure why anyone would bother.  You are makin me wonder, let me see if do some testing.

---

### Post by HermanAB on 2022-02-11
Hmm, it looks like you are confusing partitions and file systems. You cannot mount a partition.  You mount the file system that you have to create on the partition.  

Also, format is a Windows/DOS term to create a file system.  So doing a format/mkfs to create a file system and then repartitioning destroys the filesystem you just created, so then you got to do a mkfs again.

---

### Post by ylafont on 2022-02-11
I don't believe i am confused, however  i am guilty of using incorrect terminology.   if you reference the image above, you will the drive has two partition 

one with a FAT32 File system and the other with a linux ext4  file system. both we create with mfks, second  ext3 files system cannot be mounted.

---

### Post by yetimon_64 on 2022-02-12
> **ylafont said:**
> ...   if you reference the image above, you will the drive has two partition 

one with a FAT32 File system and the other with a linux ext4  file system...

The image of your second partition has a black box, not a blue box of an ext4 partition. Black boxes indicate an unformatted partition, which is one of the causes listed for the warning in gparted. Try right clicking on the entry in gparted and select "Format to" then select "ext4". If there is no problem after selecting ext4 press the "Apply all operations" button (the green tick button) at the gparted toolbar.

If this fails then there may be furthers issues to look into. Hopefully you've just missed one or two steps in your first attempt.

Regards, yeti.

---

### Post by ylafont on 2022-02-12
Tested last night and this morning, all procedures are accurate. it appears  OldFred is accurate

> [COLOR=#000000]Did you purchase this from a reputable source?[/COLOR]

[COLOR=#000000]Years ago before larger flash drives, we would see this where someone would internally modify a small flash drive to make it look like a larger drive and sell it as a larger drive. But it never was larger.[/COLOR]

tried all steps on a smaller drive without issues.   not sure is the size is being report incorrectly or if the drive is just not supported. but definitely a device issue. 

I am going to try and image the drive to a fiel and then restoring it. to see if that help. other wise - it will need to be replaced.

---

### Post by coffeecat on 2022-02-12
> **ylafont said:**
> regular amazon purchase, could that be  problem these days

Yep.

[https://bluescreencomputer.com/2020/08/26/fake-flash-drives/](https://bluescreencomputer.com/2020/08/26/fake-flash-drives/)

> Unfortunately, this scam is common on Amazon and eBay.

How much did you pay for this alleged 1TB drive?

---

### Post by ylafont on 2022-02-12
ordered this one, for $40 

[https://www.amazon.com/dp/B09M6574C3?psc=1&ref=ppx_yo2_dt_b_product_details](https://www.amazon.com/dp/B09M6574C3?psc=1&ref=ppx_yo2_dt_b_product_details)


Now considering this one for $99

[https://www.amazon.com/SanDisk-Ultra-Dual-Drive-Type-C/dp/B0842P5GG5/ref=pd_day0fbt_img_2/133-9733760-7010823?pd_rd_w=ptB39&pf_rd_p=bcb8482a-3db5-4b0b-9f15-b86e24acdb00&pf_rd_r=KT4BX6HR8GF6FVYE7ANX&pd_rd_r=6c5c564f-735a-49dd-984a-76be108b7014&pd_rd_wg=5PtGf&pd_rd_i=B0842P5GG5&psc=1](https://www.amazon.com/SanDisk-Ultra-Dual-Drive-Type-C/dp/B0842P5GG5/ref=pd_day0fbt_img_2/133-9733760-7010823?pd_rd_w=ptB39&pf_rd_p=bcb8482a-3db5-4b0b-9f15-b86e24acdb00&pf_rd_r=KT4BX6HR8GF6FVYE7ANX&pd_rd_r=6c5c564f-735a-49dd-984a-76be108b7014&pd_rd_wg=5PtGf&pd_rd_i=B0842P5GG5&psc=1)


but the review aren't that great, and they say it gets very hot. wondering what the lifespan will be.

---

### Post by coffeecat on 2022-02-12
> **ylafont said:**
> ordered this one, for $40 

[https://www.amazon.com/dp/B09M6574C3?psc=1&ref=ppx_yo2_dt_b_product_details](https://www.amazon.com/dp/B09M6574C3?psc=1&ref=ppx_yo2_dt_b_product_details)

$40, no reviews and "Currently unavailable. We don't know when or if this item will be back in stock," sounds like a scam item to me. Sorry.

---

### Post by #&amp;thj^% on 2022-02-12
> **coffeecat said:**
> $40, no reviews and "Currently unavailable. We don't know when or if this item will be back in stock," sounds like a scam item to me. Sorry.

+1 To add, there is not one review for it, something sounds amiss.

---

### Post by Skaperen on 2022-02-12
be aware that even name brands can be risky.  scammers may buy a bulk order of cheaper small size units, apply whatever changes make it look much larger, then sell them technically counterfeit as the larger size at a price much higher than the small ones but cheaper than the real-life big ones, with the brand name still on them, so you think you found a great discount.

---

### Post by HermanAB on 2022-02-13
FWIIW: I have two Sandisk 500GB widgets.  They do get very hot.  I removed the stupid big enclosures to be able to plug them in and improve the airflow over the parts, which helped.  A few years later they are still working

---

