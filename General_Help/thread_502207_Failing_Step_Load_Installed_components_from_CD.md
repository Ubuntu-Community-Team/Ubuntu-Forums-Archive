---
title: "Failing Step: Load Installed components from CD"
date: 2007-07-16
forum: General Help
---

### Post by RaigyCar on 2007-07-16
I just ran the Wubi installer, the download and installation seemed to work ok but when i rebooted and selected Ubuntu from the boot menu, the following message appears:

Failing step:  load installer components from cd

How do i resolve this problem.  

I can boot into Windows XP no bother, but when i select Ubuntu i get this failing step error!??

Thanks in advance :)

---

### Post by RaigyCar on 2007-07-16
I rebooted and tried again , when i select to boot into Ubuntu i now get the following message:

"Unable to access Alt ISO, probably the installation action was interrupted, please run the installer again."

---

### Post by ago on 2007-07-16
Uninstall and do a clean installation

---

### Post by RaigyCar on 2007-07-16
I uninstalled then, did a clean installation.  I am still getting the "Failing step: load installer components from cd"
error??

---

### Post by ago on 2007-07-16
Look inside /var/log/syslog for the exact error (use the "nano" command, or copy to /media/host which is the windows drive)

---

### Post by open2linux on 2007-07-16
I tried to install Edubuntu with the latest Wubi rc4 version and i get the same error message:

Installing step failed:
Load installer components from CD

If you can explain a bit more where, how to look for errors I will do that.
I don´t understand what I should look for in /var/log/syslog
or /media/host

---

### Post by ago on 2007-07-17
In that stage there is also a section when the virtual drives are formatted and mounted, that might create issues. 
The easiest thing is to copy syslog to /media/host which is mapped to C: in windows. Then zip it and post it here.

---

### Post by RaigyCar on 2007-07-17
> **ago said:**
> Look inside /var/log/syslog for the exact error (use the "nano" command, or copy to /media/host which is the windows drive)


Sorry i am new to Linux.  How do you do this?

I have 2 hard drives on my system.  On the installer i selected my secondary hard drive D: with 15GB to install.  Could this be the issue as i did not choose to install on my primary HD C: ?

---

### Post by ago on 2007-07-17
> **RaigyCar said:**
> Sorry i am new to Linux.  How do you do this?

I have 2 hard drives on my system.  On the installer i selected my secondary hard drive D: with 15GB to install.  Could this be the issue as i did not choose to install on my primary HD C: ?

No that should no make any difference.

Run a fresh install, when it jams, press Alt+F2, then run:

```
cp   /var/log/syslog   /media/host
```

This will copy the code to windows D:\. Now start windows and open the file with wordpad. You can attach the file here after you zip it.

---

### Post by RaigyCar on 2007-07-17
After i hit Alt & F2 do i just type 

cp   /var/log/syslog   /media/host

Then hit enter?

---

### Post by RaigyCar on 2007-07-17
I think it work three files appeared on my D:/ drive:

syslog
wubildr
wubildr.mbr

I have zipped the three and attached them:

---

### Post by ago on 2007-07-17
Yep

---

### Post by ago on 2007-07-17
The size of wubi/disks/system.virtual.disk appears to be 0. Not sure how that happen. But basically reinstall and before rebooting check that the files in c:\wubi\disks have a reasonable size

---

### Post by RaigyCar on 2007-07-17
Yeh i see that in D:\wubi\disks

system.virtual.disk is 0kb

home.virtual.disk is just under 2gb i think 

swap.virtual.disk is 217Mb

What happens if i reinstall and the system.virtual.disk is still 0kb?

What could be causing this?

---

### Post by RaigyCar on 2007-07-17
I reinstalled and the wubi/disks/system.virtual.disk is still 0kb?

Any suggestions? Thanks for your help.

---

### Post by ago on 2007-07-17
Try with a different size. What is the free space in your drive?

---

### Post by open2linux on 2007-07-17
Since I have exactly the same problem as RaigyCar, I am also attaching my syslog so to confirm
if it is a bug that may affect to more people.

I have more than 10Gb of free space in WinXP, so in my case space is not the issue.

---

### Post by RaigyCar on 2007-07-17
> **ago said:**
> Try with a different size. What is the free space in your drive?

My D:\ drive has 30GB of free space.  I will reinstall and select 10GB this time instead of 15GB.  I'm away out for dinner so i won't be able to do it untill later.

Would it work using an external HD? I have an external HD attached to another computer, and might try to install Ubuntu on it using Wubi.

I will keep you posted.

---

### Post by ago on 2007-07-17
Ok but can you check to see what happens when you select different sizes in the installer? No need to reboot, just run the wubi then look into c:\wubi\disks. Anything peculiar about your disk? What filesystem do you use?

---

### Post by ago on 2007-07-17
The temporary solution, by the way is to create/copy a large enough file and save it as c:\wubi\disks\system.virtual.disk 

Do that BEFORE rebooting.

---

### Post by RaigyCar on 2007-07-18
> **ago said:**
> The temporary solution, by the way is to create/copy a large enough file and save it as c:\wubi\disks\system.virtual.disk 

Do that BEFORE rebooting.


Could i .zip my music folder which is around 10GB, then just rename it as system.virtual.disk?

Would this work?

---

### Post by RaigyCar on 2007-07-20
Good News!

I reinstalled Wubi selecting the 4GB install and it has worked!

Thanks for all your hep ago!

---

### Post by hans12345 on 2007-08-05
Thank goodness for this thread and the 4 GB solution.

I had a similar problem, and was posting in a different, but similar thread.

Having looked here,  I tried the same (earlier I had allowed Wubi to take 10 GB), and, like magic, it worked.

Wubi developers - this is a silly bug.

My advice to everyone who sees this in their disks folder:

        system.virtual.disk : 0 MB

just set your default size in the Wubi install screen to 4 GB

:)

---

### Post by ago on 2007-08-06
What OS do you use? Is it a 64 bit machine?

---

### Post by hans12345 on 2007-08-07
It is an Athlon 64 3200 running Win 2000 SP4

---

### Post by hazahel on 2007-08-07
i have the same problem. I fist tried to set a 6 Gb space disk, and i get the same error info. Now, i set only 4 Gb, and i don't have any problem.

may be a little bug?

thanx for the solution anyway....

---

