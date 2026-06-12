---
title: "Possible to Boot From ISO With Persistence?"
date: 2012-11-13
forum: General Help
---

### Post by bzowk on 2012-11-13
Good Morning!

Yesterday, I was excited to receive my new [Zalman ZM-VE300 drive enclosure]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817379026").  The cool thing about it, is that it has "Virtual-ODD" meaning I can scroll through and select an ISO directly on the enclosure using a built in LCD screen, then mount it in Windows or even directly boot to it!

[IMG]http://www.zalman.com/images/productinfo/ZM-VE300_02.jpg[/IMG]

After setting it up, it works flawlessly! Of the many ISO files I am using with it, though, are a few Linux distros including Ubuntu Desktop 12.10 x64.

I understand how to add persistence when using the extracted/installed OS on a USB drive (adding persistence to the string); but don't know how to do so with the method I'm using.

I'm sure I could edit the files inside the ISO to add persistence automatically upon each boot, but where would the persistence data go?  In the ISO?  Outside of it?  Would I need to create a file with Casper-RW and if so, where?

The drive has a folder in the root named "_iso" which contains all of the ISO files.  Any file kept in this folder will be displayed on the LCD screen.  Therefore, the Ubuntu ISO as well as a few others are all in this folder. 

Any Ideas?  Thanks!

---

### Post by audiomick on 2012-11-13
Hi. I found this in the Ubuntu Help site. It looks to me to be what you need. I haven't tried it, though.

[https://help.ubuntu.com/community/LiveCD/Persistence]("https://help.ubuntu.com/community/LiveCD/Persistence")

---

### Post by Cheesemill on 2012-11-13
When you're using it in ISO mode does it present another USB drive at the same time?

You can create a casper-rw file in the root of any connected drive to use it with a Live CD, obviously where *you* can put it depends on whether you can see the drive at the same time as using it to boot from an ISO.

---

### Post by C.S.Cameron on 2012-11-14
You can also make casper-rw and home-rw partitions, you will need to edit grub.cfg and add persistent to the Buntu version you wish persistent.
Making more than one Buntu version persistent can lead to problems.
You can have Puppy persistent at the same time though.

---

