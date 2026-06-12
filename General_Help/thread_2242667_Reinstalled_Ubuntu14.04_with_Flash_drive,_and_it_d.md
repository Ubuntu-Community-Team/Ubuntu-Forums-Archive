---
title: "Reinstalled Ubuntu14.04 with Flash drive, and it did a complete wipe of my system"
date: 2014-09-03
forum: General Help
---

### Post by lee29 on 2014-09-03
Hi all,

I believed Ubuntu installation did a complete wipe of my windows OS. And i would really greatly appreaciate any help to get back my windows OS. 


Here is what happened.
0. I had unbuntu 14.04 dual booting with my windows os, till i found some problems with ubuntu, and decided to reinstall it back to default.
1. I proceeded to clear the ubuntu partitions from windows, and completely deleted them. 
2. I booted with a ubuntu flash drive, and started to install ubuntu . But because there was some problems when installing, i restarted the whole computer.
3. Repeated step 2 by proceeding to boot via flash drive, and found some options like install "ubuntu 14.04 alongside ubuntu 14.04", and picked the 3rd one(if not mistaken), which is delete and reinstall ubuntu.
4. After reinstallation, i believed it reinstalled ubuntu as my ONLY OS, and deleted my windows OS.

Is there any way to get back my windows OS. Ubuntu should have warned that this would happen.

Please help me. I am really at a loss, and i really need both OS for my work. 

I did not make any recovery disc 

I have a lenovo ideapad u330p laptop windows 8.1.

All help appreciated

Lee

---

### Post by christopher9 on 2014-09-03
"I did not make any recovery disc"   
"But because there was some problems when installing, i restarted the whole computer"  


So, no backup of any kind?  Nothing stored on Dropbox/OneDrive/et al. ?
Does your company store your files on a server ?
Does your IT department have a company disk image to install in such cases ?
Can your systems administrator(s) offer Data Recovery utilities ?
Still have a Windows install disc or a copy of your license ?

---

### Post by Mark Phelps on 2014-09-03
IT DOES warn you -- but the warning isn't well worded and leads folks to believe that it's only going to replace Ubuntu, when in fact, it replaces ALL the files on the drive.

What MIGHT work is the following:
1) Download and burn a CD from the ISO file of the Minitool Partition Wizard (Windows partitioning tool).
2) Boot your PC from that CD
3) See if you can Recovery the partitions that were there before

If that does not work, you next need to consider using Windows data recovery utilities to get your files and folders back.  You will need to be able to connect your drive to a working Windows PC to do this, and then download and install Recuva.  If that doesn't work, you can then try using RecoverMyFiles but while it's free to try out, you have to buy it to do the actual file recoveries.

---

### Post by LostFarmer on 2014-09-03
If you can not get a reinstall disk from the manufacture, you can try a semi long and some what complicated process of downloading the correct Win 8.1 iso and installing,  I can verify it works to load the OS but did not try going on line and activating it.  But first need to see if the key can be read from the comps firmware. in a linux console run** sudo acpidump -s -z** , it is a long output, find the section that is titled **MSDM** @ the first part of list give manufacture name of your comp and at the bottom with luck your key will be listed. (do NOT post the output here).  If it is listed just post back saying so, then can post the next step when I have time.

The information will be from [http://forums.mydigitallife.info/forums/42-Windows-8](http://forums.mydigitallife.info/forums/42-Windows-8)   , have a look about, but it can be difficult to find what one needs.  I download the wrong iso (4gig or so) 3 times and it took me 12 hours each.

---

### Post by xc3RnbFO8P on 2014-09-03
Dont use "**Reinstall Ubuntu**" on multiboot computer!
[http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions]("http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions")

---

