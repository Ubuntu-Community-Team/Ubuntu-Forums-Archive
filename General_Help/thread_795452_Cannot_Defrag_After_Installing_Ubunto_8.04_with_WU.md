---
title: "Cannot Defrag After Installing Ubunto 8.04 with WUBI"
date: 2008-05-15
forum: General Help
---

### Post by ColTom2 on 2008-05-15
Hi:

  I installed Ubunto 8.04 with WUBI and the installation went fine. However, after running defrag 2-3 times successfully I now no longer can run defrag without it hanging.

  The reason is defrag at 3% now always tries to move the file boot.disk in the Ubunto folder, which is over 13GB in size and it hangs at this point. As long as I was running defrag and it did not try to move the boot/disk file everything was fine. But there is no way that defrag can move a 13GB file such as boot.disk.

  Installation of Ubunto 8.04 into a single Windows folder with WUBI was a great idea until I found that I could no longer can defrag my computer.

  Does anyone know a fix or work around for this? I would hate to uninstall my Ubunto installation, but I do need to have my defrag capabilities returned.

---

### Post by danwood76 on 2008-05-15
I know this doesnt solve your issue.

But why do you defrag?
Modern PCs and filesystems dont need to defrag, if your running an NTFS filesystem on windows you should be ok to continue without defragging.

You could always create a second partition and install ubuntu on that to solve your issues.

---

### Post by cdenley on 2008-05-15
You would probably have more luck on a MS forum, since this is a Windows problem. Are you sure it hangs? Maybe it's just moving the 13GB file. How long did you wait for it to finish?

---

### Post by ColTom2 on 2008-05-15
I don't know if this problem came up during Beta testing using WUBI to install into one Windows Folder and having the file boot-disk so large that it renders defrag virtually impossible, but to me it's a major issue. 

I was not a Linux user previously and this was an extremely easy way to get into the Linux world without having to partition your computer. However, that now appears the only viable solution and they can put WUBI back on the shelf.

WUBI was a great idea and it's a shame that it all comes down to the defrag issue. I had never seen a hard drive so fragmented in all my years. NFTS and other prior file systems require defrag if they are going to function as desired capacity.

Hopefully someone can resolve this issue for future WUBI installations at some point in time.

---

### Post by cdenley on 2008-05-16
You could try this windows tool
[http://www.microsoft.com/technet/sysinternals/FileAndDisk/Contig.mspx](http://www.microsoft.com/technet/sysinternals/FileAndDisk/Contig.mspx)

The wubi developers can't be expected to fix a problem with a windows component, but I suppose they could have the file split every 1GB to make it easier to defrag. There is no reason for windows not to be able to handle a file that large. How much free space do you have? Did you check for errors in the event log? Disk errors can cause windows to hang.

[https://bugs.launchpad.net/wubi/+bugs](https://bugs.launchpad.net/wubi/+bugs)

---

### Post by ColTom2 on 2008-05-16
Let me try and state this problem once again....

The Windows defrag process can defrag a 13GB file (boot.disk), but as I have previously stated, it cannot move such a large file in Windows defragging.

The WUBI developers should have taken this into consideration when they developed the WUBI concept of installing Ubunto into one Windows folder. The Windows defrag process was developed prior to WUBI and it's not up to Windows to change their process to accommodate WUBI, but up to the WUBI developers to develop their processes accordingly.

This problem was not identified or recognized I don't believe until now or they would have taken this into consideration in their development of WUBI. 

I have a 250GB hard and had used approx 20GB prior to the WUBI installation. The size of the hard drive in this case is not an issue. Again I just do not believe that the WUBI developers took into account that at one point Windows defrag moves files in its defragging process. It can defrag the 13GB file, but it cannot move it.

This is a major issue and renders the functionality of one's computer in time to zero because of the impact of a highly fragmented hard drive. In all my years I have never seen my hard drive so fragmented after installation using WUBI. My computer in either Windows or Ubunto mode was highly affected by the sluggish response in use to the point that made it inoperable.

Hopefully the WUBI developers will become aware of this problem and develop a fix. Otherwise it is not a functional application.

---

### Post by ColTom2 on 2008-05-16
After second thought I might have reported this issue under Ubunto "Reporting Bug" process, but I thought this forum is monitored by WUBI support etc and they would pick up on this issue.

Should I in fact report this issue additionally as a bug now or just wait and see what develops?

---

### Post by cdenley on 2008-05-16
> 
I now no longer can run defrag without it hanging


I thought you meant the system became unresponsive. If windows can't defrag a file that size, and this fragmentation can cause a file to become unusable, I'm glad I don't use windows anymore. Did you try the tool from the first link I posted? I think I saw somewhere it can defrag large files the windows defrag utility can't. If you hope for any functionality to be changed in future releases, I suggest you file a bug report with the second link I posted.

---

### Post by danwood76 on 2008-05-16
File fragmentation on a modern machine will not cause a noticable difference in speed unless you are trying to open an extremely large file fragmented into millions of pieces.
I doubt that situation would ever come up on a large drive.

With a 250GB drive file fragmentation should be low if your using NTFS.
Bits will be distributed over the entirety of the drive and this is normal to avoid fragmentation.

To be honest I dont think the WUBI developers should have to worry about such things as MS defragger not being able to handle large files, if you want to use ubuntu properly install it properly!
I havent defragged a windows volume in years and my PC runs just as fast in windows as it used to.

Also you say it can defrag a 13 GB file but not move it, surely part of defragging would be moving it if necessary and so obviously it cant.
Complain to bill about it!

---

