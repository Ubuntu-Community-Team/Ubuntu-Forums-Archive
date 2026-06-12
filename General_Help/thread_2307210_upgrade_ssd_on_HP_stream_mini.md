---
title: "upgrade ssd on HP stream mini"
date: 2015-12-22
forum: General Help
---

### Post by snapback77 on 2015-12-22
I have a HP stream mini box with 30G ssd that is maxed-out. . I want to upgrade to 128G ssd.  I need to make a copy of  30G ssd, remove it, replace it with the 128G ssd, then load it with my copy of the 30G ssd.  Then, I will have plenty room for updates. I am confused about how to start.  I have a Seagate external HD  to store my copy and then boot the HP stream mini from it?  Or could I copy the 30G ssd to a 32G usb thumb drive and install it to the HP with the newly installed 128G ssd from it? the HP doesn't have a CD drive.  Clonezilla, DD, Ubuntu Live CD?  Recovery disc? What is best?
I would like to keep my installed settings and Windows in case I need it. 
Thanks.

---

### Post by efflandt on 2015-12-22
You might want to open it up and see what is inside to see if it can use a regular SSD. While the Pavilion mini sounds like it has a regular 500 GB or 1 TB hard drive, something I saw about the Stream mini says it has 32 GB M.2 SATA SSD (which is a card). If that is the case it might not have provisions for a normal drive. See [https://en.wikipedia.org/wiki/M.2](https://en.wikipedia.org/wiki/M.2)

M.2 is physically smaller than the mSATA SSD card that I put in my laptop for booting Linux. I have a tablet PC with Win7 on 32 GB SSD that I wish was larger. But I think it may have been a proprietary SSD card from before mSATA or newer M.2. I boot Ubuntu on it from 32 GB SD card which is the largest SD card it supports.

---

### Post by snapback77 on 2015-12-23
Hi
I failed to mention it was 32 GB M.2. sata ssd (Card).  I ordered such a card with 128 GB.  Watched a guy on youtube install it.  My space for updates is non-existent.  Filled up fast too with dual boot of windows and ubuntu updating more than ever before.  Deleted all that I could. Needed more GB.  Perhaps I can:  
1. clone an image to seagate ext. hd. 
2. replace ssd card with larger one in my HP stream mini. 
3. boot my HP stream mini with the saved image either from Seagate or usb thumb drive.
. Does this sound reasonable?  I say "image" instead of "clone" because I read that is the way if you want to use all of the rest of space on new drive.  I've never done anything like this before.  
Thanks for your insights.
regards

---

### Post by Image on 2015-12-23
It may be possible to clone the drive over to a usb drive. Remove the m.2, see if it boots to the usb drive. 
If it can boot to windows from external then just install new 128 and clone usb back to new 128. 
Personally I would just do a clean install and start over, but if you have good enough reason not to this would be my suggestion as if all else fails you still have your original rig untouched....

---

### Post by snapback77 on 2015-12-23
I think you might be right about a clean install.  Just install the new card and just install ubuntu from a usb drive?  Am I right? 
Regards

---

