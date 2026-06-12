---
title: "[SOLVED] Ram problem"
date: 2007-12-19
forum: General Help
---

### Post by cotcot on 2007-12-19
I have a GA-M55plus-S3G mobo (1.5 years old) with 1 GB ram DDRII PC5300.
When I add a second ram strip (same brand, type and size) I get long beeps at boot telling me that there is a ram problem (Award Bios). I have checked the manual of the mobo. I have checked the installation of the ram strip (well pressed and lids at the end closed) but no result.
Switching the old and new ram initially gave a problem. But after 10 minutes waiting the ram was ok (static electricity ?)
Is there anything else that I could overlook ?

---

### Post by Existentialist on 2007-12-19
Have you tried differnt slots for the ram?  I belive you should have 4, 2 for each channel.  If so are both peices of ram the exact same model?  Sometimes the ram will have slightly differnt timeings or voltages if the ram is designed for overclocking.  I would check BIOS and make sure the ram speed and timings are not set manually.

---

### Post by cotcot on 2007-12-20
I have 4 slots indeed. I have tried the 2 first slots. Have not checked ram speed settings in Bios yet. 
I bought the same type of ram in the same shop with 2 weeks difference.

---

### Post by Existentialist on 2007-12-20
I would try putting the ram 1 slot apart.  I have seen some motherboards that wouldn't boot unless the same amount of ram was in each channel.  Here is the link to the manual for your board in case you don't have it:
[http://www.gigabyte.co.nz/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=17262](http://www.gigabyte.co.nz/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=17262)

Page 14-15 have details on installing more than one memory module.

---

### Post by bigken on 2007-12-20
I agree miss one slot so its in slot 0 and slot 2 you could also jumper the cmos

---

### Post by cotcot on 2007-12-20
Thanks for suggestions. I have solved the problem. 
I have 4 DDRII slots, 2 yellow ones and 2 red ones. I have put 1GB in slot 1 and 1GB (same make same speed PC 5300 667) in slot 2 (same color, so dual channel) : it fails.
Then I have moved 1GB from slot 2 to slot 3. (different color, so single channel) : This worked. 2 GB was recognised on boot.
Then I have added a third strip (1GB, different make and different speed PC-4600). It worked and 3 GB was recognised as single channel.
I wanted 3 GB to do some benchmark test between 32 bit and 64 bit. I had read that 64 bits needs more memory to show its full power.

---

### Post by Existentialist on 2007-12-20
I wouldn't give up yet, if you can get dual channel to work you may see a better performance increase than just more ram.  Having it in dual channel allows each channel to access the memory controller so it doubles the memory throughput bandwidth.  And 64 bit OSs don't necessarily need more money, it's that 32 bit OSs can only support up to 4GB of RAM but due to system resource allocation, you almost never get to take advantage of all 4GB.  64 bit OSs can theoretically address something like 16,000,000GB of RAM.  So unless you are using over 4GB the difference between 32 and 64 should be negligible.

---

### Post by cotcot on 2007-12-21
That is indeed what I see.
Rendering a video took 17 minutes on 64 bit whereas it took 16 minutes on 32 bit !  (3GB ram of which 550 MB was used). So not encouraging to keep my 64 bit. (comparision done on the same PC with multi boot  ubuntu 32 bit 64 bit)
I did another test with a big panorama photo (hugin). 64bit was not faster than 32 bit.

---

### Post by Existentialist on 2007-12-21
From everythign I have read, for the average user there is no benifit to 64-bit as of yet other than being able to address the full 4GB of RAM or more.

---

