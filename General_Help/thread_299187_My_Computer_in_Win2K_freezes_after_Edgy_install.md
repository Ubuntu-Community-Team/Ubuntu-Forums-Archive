---
title: "My Computer in Win2K freezes after Edgy install"
date: 2006-11-13
forum: General Help
---

### Post by el_manaba on 2006-11-13
Hi all. Welcome another newbie...

I have two hard drives. One has several large NTFS partitions (with Windows 2000 installed one the primary partition). The smaller slave drive is where I installed Edgy.

I had previously used the Win2K utility to format the slave drive to FAT32. Windows could recognize it. I could save to it from the Live CD. No problems. Then I let the Ubuntu installer reformat the whole thing. So now it has an *ext3* partition and a *linux-swap* partition. I also modified fstab to automate mounting my ntfs partitions.

Then I rebooted to Windows. It boots fine and I can open my NTFS partions from the command line or from the address bar in 'Windows Explorer'. But if I attempt to open 'My Computer', The window that opens says that the folder contains no items and it freezes 'Windows Explorer', apparently looking for something to display. I have a similar problem if I attempt to browse to a file from the "Open.." dialog of any application.

Maybe this has nothing to do with reformatting the slave drive, but that's when I noticed the problem.

Any suggestions, please??

---

### Post by digby on 2006-11-13
I really don't think the two could be related... especially since windows still boots fine... 

Have you run the obligatory spyware/antivirus sweeps?

---

### Post by el_manaba on 2006-11-21
UPDATE, FYI:
Although Windows couldn't access the partitions on the slave drive,  it was able to recognize the hard drive in 'Device Manager'. From there I disabled the drive so Windows would stop trying to access it. The freezing problem was resolved immediately; I can now access the master drive and all its partition through 'Windows Explorer' as well as 'Open...' dialogs.

So the problem is resolved, but I'm still curious about its cause. I suspect that Windows couldn't handle the partition formats on the drive where I installed Ubuntu, so it stalled when trying to access the disk that it could once access (when it had FAT formatting). Does anybody have a good explanation?

---

