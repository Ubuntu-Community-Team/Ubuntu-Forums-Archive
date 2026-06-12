---
title: "New WD My Passport 2tb USB drive very slow"
date: 2015-05-31
forum: General Help
---

### Post by Ralph L on 2015-05-31
I just got a new Western Digital My Passport 2tb USB drive.  It is a USB 3 interface, but I am running it on USB 2 as that is all my laptop has.  Writing to it is very slow much of the time.  I experimented with copying jpeg images and mp4 videos to it.  The jpeg files ranged from 2MB to 6MB and the mp4 from 4MB to 50MB.  On the shorter jpeg files my old 250GB USB2 Toshiba wrote files at 20-27MBs--about 4 times faster than the new WD USB3 disk (4-9MBs).  On the longer files the WD sometimes approached the USB2 Toshiba in speed, but still took about 1.5 times longer to write the files.  My questions are:
1.  Has anybody else had this kind of experience when using new multi-terabyte USB3 disks??
2.  I formatted the disk as ext4.  I have a couple of small partitions at the top end, but otherwise the disk is one big partition 1.7 terabytes long.  Should I have used a different format?  Would a different format speed things up?
3.  Is there a special linux driver for this disk?  When I used the disk on windows vista, it installed a new driver.  In general, the disk runs about 1.5 times faster on vista than on xubuntu.
4.  Anybody know of a 2tb disk that runs fast on xubuntu (25MBs or better on short files)?  I think I may be sending this one back if I can't get more speed out of it.

Thanks for any help you might be able to give.

---

### Post by sudodus on 2015-05-31
I have experience of USB 2 and USB 3 drives in USB 2 and USB 3 ports, but I run my huge 2 and 4 TB external disks via eSATA, which works well. My experience of USB 3 disks extend to 500 MB (and I have a built-in USB 3 disk as well as standard HDDs and SSDs in external enclosures (USB 3 and esata boxes)). During [iso-testing]("http://iso.qa.ubuntu.com/") of Lubuntu I'm booting a computer via USB 3 from an SSD in a 'USB 3 and esata box' by AKASA.

It works well for me with ext4. It works well for me with USB 3. But I know, that some interfaces do not work well. I think USB 3 is still so new, that there are non-standard solutions. I suggest that you buy a 'USB 3 and esata box' and buy separate HDDs. That way you have better chances to get a fast USB system.

The following link concerns USB pendrives, but I think some of if can be applied to selecting and testing equipment for USB HDDs too.

[Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

See also this link (and links from it) [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by Ralph L on 2015-06-07
sudodus:  Thank you very much for responding.  Your pendrive test web site was very helpful not only for my current issue with the WD hard drive, but also for future purchases of pendrives.  I ended up running the following dd test generating the data to write the file in the cpu:```
time sh -c "dd if=/dev/zero of=ddfile bs=8k count=250000 && sync" 
```This showed that the WD drive would accept various size blocks at around 25MB/sec on USB2.  I also found that some of the picture images from my internal hard disk copied to the WD usb disk much faster than others.  I came to the conclusion that the reason for the slow copies, in some instances, was that the image files, while being in the same folder, were scattered around the disk, and required a great deal of head movement between files on the internal hard disk. So it looks like the WD disk is working fine and that my problem was with reading the source of the copy.  I really didn't find a simple way to test the WD usb drive for capability to handle many short files, since I didn't know of a way to, in the cpu, to generate multiple short files.

---

### Post by kryten35 on 2015-06-07
On USB 2 (old computer) i was getting 30-35 MB/s
 On USB 3(new computer) i get 125-130 MB/s
  
4-9MB/s is pathetic,even for USB 2.There is something wrong if you get speeds as low as that. Either driver or the cable.Updating to a more recent  kernel,or switching to a distro which already contains one will  install newer/updated  drivers which might fix it.

Edit  sorry,  i see youve marked this as solved.

---

### Post by sudodus on 2015-06-08
> **Ralph L said:**
> sudodus:  Thank you very much for responding.  Your pendrive test web site was very helpful not only for my current issue with the WD hard drive, but also for future purchases of pendrives.  I ended up running the following dd test generating the data to write the file in the cpu:```
time sh -c "dd if=/dev/zero of=ddfile bs=8k count=250000 && sync" 
```This showed that the WD drive would accept various size blocks at around 25MB/sec on USB2.  I also found that some of the picture images from my internal hard disk copied to the WD usb disk much faster than others.  I came to the conclusion that the reason for the slow copies, in some instances, was that the image files, while being in the same folder, were scattered around the disk, and required a great deal of head movement between files on the internal hard disk. So it looks like the WD disk is working fine and that my problem was with reading the source of the copy. [COLOR=#ff0000] I really didn't find a simple way to test the WD usb drive for capability to handle many short files[/COLOR], since I didn't know of a way to, in the cpu, to generate multiple short files.

In that post (#6) [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085"), there is a link to a batch file and files belonging to it, that I used, and that you can use too, if you want to test the capability to handle many short files.

 See this link [http://phillw.net/isos/linux-tools/usb-speed-test/](http://phillw.net/isos/linux-tools/usb-speed-test/)

---

