---
title: "Newbie Ubuntu/Windows 7 dual boot problem&#8207;"
date: 2015-03-01
forum: General Help
---

### Post by olanrewaju2 on 2015-03-01
Hello all,
It's nice seeing such a good and thriving help community.. tres bon.
My laptop came preinstalled with 64 bit windows 7 operating system. I then installed Ubuntu, I am quite sure that I partitioned my hard drive and didn't install the ubuntu over my windows 7.


After installation, the ubuntu works fine (and I love it), but theirs no option to boot my windows 7. I need my windows 7 for some work.
I ran the boot repair, hoping I'd see some option to boot up my windows 7, here is the result from the boot repair - [http://paste.ubuntu.com/10453055](http://paste.ubuntu.com/10453055).
I would like to know if my windows 7 is still on my hard drive and how I can get it back.
Thank you..

---

### Post by Elfy on 2015-03-01
*Thread moved to **General Help**.*  

Also, please don't format posts with odd fonts and colours.

As to the issue  it appears from looking at the paste that you only have linux partitions. Looks to me like you've overwritten it.

First thing I would do is reboot into whatever you used to install Ubuntu, usb or dvd. 

Look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You might be able to recover - though I personally have never needed to try.

Given that this might well take some time - you might well be better off reinstalling Windows, restoring your backups and then reinstalling Ubuntu.

---

### Post by Mark Phelps on 2015-03-01
Agree with Elfy -- it looks like you overwrote the entire drive, as there are no Windows filesystem partitions.

To get Windows back, you need to do two things:
1) Recover your data files from the drive
2) Reinstall Windows from scratch

To do the first, you need to be able to remove the drive from your PC, connect it to a working Windows PC, download and install a Windows data recovery app, point it to your drive -- and recover the files to the Windows PC, or to an external USB drive or USB stick.  One free Windows data recovery app is "recuva".  The best one I've used is RecoverMyFiles -- which is free to install and test to see what it finds, but you have to go online and buy a license to actually recover the files.

To do the second, if you just boot from Windows install media, it won't be able to make sense of the drive because it can't understand Linux filesystems, so the best approach is to boot from Ubuntu install media, run Gparted -- and remove all the partitions on drive.  Then, when you reboot using the Windows install media, it will be able to see and partition the drive.

---

### Post by pmi2 on 2015-03-01
> **Mark Phelps said:**
> ...install a Windows data recovery app, point it to your drive -- and recover the files to the Windows PC, or to an external USB drive or USB stick... Can a recovery program recover files when the file system has been over-written and replaced by a new and different file system? (not trying to be negative, but just interested if that can be done here.)

---

### Post by olanrewaju2 on 2015-03-01
Thank you so much @Mark Phelps and @Elfy, I am seriously overwhelmed by the amount of Information in both your respective posts.
I am honestly more confused right now, If it helps I did a full system backup of my windows PC on my external hdd before I installed Ubuntu.
Please what would you recommend I do?

---

