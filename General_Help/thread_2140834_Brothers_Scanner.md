---
title: "Brothers Scanner"
date: 2013-04-30
forum: General Help
---

### Post by exXP on 2013-04-30
Along with many others, I have found that I cannot scan with my Brothers MFC-J425W, despite having downloaded the proper brscan and brscan-tools programs.  However I have just tried running xsane under sudo and to my surprise, after a 15 second delay, it works!  
Does anybody have any suggestions as where I should be looking to change permissions?   
exXP

---

### Post by plucky on 2013-05-01
> **exXP said:**
> Along with many others, I have found that I cannot scan with my Brothers MFC-J425W, despite having downloaded the proper brscan and brscan-tools programs.  However I have just tried running xsane under sudo and to my surprise, after a 15 second delay, it works!  
Does anybody have any suggestions as where I should be looking to change permissions?   
exXP

Are you connected by USB?

From the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

> 
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".

    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Also,if connected by usb,it could be a permission problem with the USB port.

To correct,run from a terminal

```
To change permissions for USB scanner:

lsusb | grep -i Brother

which gave me
Code:

Bus 004 Device 002: ID 04f9:01ab Brother Industries, Ltd MFC-240C

so, I entered, 
Code:

sudo chmod a+w /dev/bus/usb/004/002

and the scanner software fired up perfectly!

```

Good Luck

---

### Post by exXP on 2013-05-01
Thank you for your reply.  It is connected via USB.  However the printer side works well, so I don't think it can be the permissions of the USB but I will check.  Also , following many previous posts from this forum, I have already added the two lines you listed. I will recheck that also when i have time.  Another thing I didn't mention, is that the sudo approach only woks in xsane - not in simple-scan, acquire images or guvc2pdf.
exXP

---

### Post by exXP on 2013-05-01
I have tried both your suggestions without success ( except that sudo no longer works with xsane)  My system uses Bus 001 and device 003, so made those changes.  I also added the device identity (028f) to the 40-libsane file.  I adopted all the suggestions given in Brother web-site but to no avail.  I've even tried going back to 12.10 on a live cd but no luck there.
Thank you for your efforts anyway.
exXP

---

### Post by plucky on 2013-05-01
Have you rebooted since you made the changes?

Are you running 64-bit version of Ubuntu?

---

### Post by exXP on 2013-05-02
I finally got the scanner working by installing the Brother drivers from the command line instead of the Software Centre. Weird!  Anyway I'm back in the scanning business.  On a separate post, I also got my Brother HL2240 laser printer working by rejecting the offered driver (HL2170) and using the HL2040 driver.  This was a lot more hassle than I usually get with Ubuntu releases!
exXP

---

