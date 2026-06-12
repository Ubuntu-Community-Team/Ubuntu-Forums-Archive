---
title: "Installing Ubuntu alongside Windows 7"
date: 2015-04-12
forum: General Help
---

### Post by Tom_Heywood on 2015-04-12
HI Community! 

Hope you're all doing well. Installed Ubuntu around 5 years ago and loved every moment. Sadly, the laptop died and i've just purchased a Lenovo. It comes with win 7 as standard but want to install Ubuntu 14 along side it.

Every time i get to install, and go to click the partition i made in EaseUS it's simply not there and only shows my 1TB HDD. Of course, if i clicked that then proceeded, i'd remove everything and have Ubuntu on the whole PC. 

I went back onto windows 7 and checked my partition. It's Allocated to system E: and the name Ubuntu and i made it to Ext3 and the partition of 500gb.  

Checked some forums who said i need to make the whole hard drive to GTP (Not sure if thats right) but by HDD is MBR. I can remove all the partitions in EaseUS and then convert it to GTP. But i don't want to loose any data... 

Is there anything i can do in terminal as i can access the "Try Ubuntu" screen.

Would really appreciate some help if anyone can!

Thanks,
Tom

---

### Post by LostFarmer on 2015-04-12
boot into 'try ubuntu' and in a terminal run/post output of
```
sudo parted -l 
```  Note: -l is a small L

---

### Post by Tom_Heywood on 2015-04-12
HI , Cheers for this. I'll give it a shot! Does that usually work?

---

### Post by sammiev on 2015-04-12
> **Tom_Heywood said:**
> HI , Cheers for this. I'll give it a shot! Does that usually work?

It will give us a picture of your HDD and how it's set up.

---

### Post by oldfred on 2015-04-12
If Windows is booting in BIOS mode you must have MBR(msdos) partitioning.
And Windows only boots from gpt partitioned drives with UEFI. 
So if you change partitioning, you will erase Windows.

And if new system the UEFI may be booting in BIOS (really CSM mode) but have UEFI. So they  you can boot Ubuntu in UEFI mode but do not want to. 
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
How you boot installer is how it installs.

---

