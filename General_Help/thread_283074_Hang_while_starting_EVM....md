---
title: "Hang while starting EVM..."
date: 2006-10-23
forum: General Help
---

### Post by Pulsating Penguin on 2006-10-23
Hey people, I really would appreciate some help here.

I have had Dapper 6.06 installed, dual booting with WinXP for a few months now. Whilst first running the Live CD, I recieved this during starting the EVM system:
```
Buffer I/O Error on device dm-1, logical block xxxxxxx
```
This repeated with the numbers going up by one each time, the number being something in the realm of 800,000.  I searched the forums and found a thread saying that you could hold a certain key combo (which I have forgotten, that is if it even works on a properly installed system and not just on the LiveCD), and it would skip that part of the boot, ignoring the errors. I did so, and after I installed it and didn't see the error, I assumed it was something to do with the CD and forgot about it.

Today it started appearing again on bootup, and I have no idea what I have done to cause it - I might add that the errors are accompanied by a strange 'urk-urk-urk' noise, repeating, from what I'm guessing is the HDD (like it is repeatedly failing to do something).  My first thought was that my NTFS partition was corrupted, because I had modified fstab to mount it at boot -  so I used the XP recovery console to do a CHKDSK /R, but to no avail.  I would try to fsck the Ext3 partition, but as I say, I cannot boot into Ubuntu to do so, and I have no LiveCD.  I thought that if there was some kind of way to bypass EVM, then             I could boot into Ubuntu and fsck.  Also, I am not sure exactly what device dm-1 refers to, could someone please tell me.  

Wow, I rambled.  If you read this far, thanks for your time, I would appreciate any thoughts. :)

---

### Post by Pulsating Penguin on 2006-10-23
Wow, I knew these forums were busy, but phew.  Please though, somebody must know something?  I really need to get onto my ubuntu system :(

---

