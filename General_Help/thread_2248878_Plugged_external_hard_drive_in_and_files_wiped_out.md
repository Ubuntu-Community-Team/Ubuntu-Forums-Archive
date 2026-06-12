---
title: "Plugged external hard drive in and files wiped out"
date: 2014-10-17
forum: General Help
---

### Post by Bill_Leonard on 2014-10-17
I have a Western Digital 2TB external hard drive that I've been using with a Windows 8 machine.

I just installed Ubuntu 14.04LTS on another laptop.  After I plugged the external HDD into the Ubuntu laptop's USB port, all the files are missing!

The external HDD is in /media/bill, and it looks like linux formatted it (?) and copied its files over (?) because I see the following folders on my external hard drive:  bin,boot,cdrom, dev, etc,home,lib,lib64,media,mnt,opt,proc,root,run,sbin,srv,sys,tmp,usr,var     I also see the following files: initrd.img,vmlinuz

I did a find/grep for my old files and don't see them there.  I don't know how the linux files and folders were created.

When I plug the external HDD into the windows laptop, it now doesn't show up in windows as a drive.  

Does anyone know a) how I can retrieve my files and/or b) what happened here?

Thanks,
Bill

---

### Post by yancek on 2014-10-17
I'm not sure I'm understanding what happened.  You say you installed Ubuntu to a laptop and then took your 2TB hard drive which you had used on another computer with windows and plugged it in to the laptop and now it has Ubuntu?  It would be pretty difficult to overwrite files on a drive not attached to the computer.  The directories/files you report seeing are what one would expect on seeing the / of a Linux filesystem.

---

### Post by Bucky Ball on 2014-10-17
Welcome. I'm guessing your files will still be there, they are just hidden. I had the same problem awhile ago and can't remember how I fixed. Is the external drive formatted as NTFS by any chance? If you check the drive in Gparted it should show that there is used space. If you boot to Windows it should show the files are still there. 

Have a bit of a dig about on a search engine. As I say, can't remember how I solved this, but I did some research and did solve it. 

As mentioned, there is no way Ubuntu could have wiped your external drive if all you did was plug it into the machine while booted into Ubuntu. Not possible. You would need to delete them manually. 

Good luck.

---

### Post by Vladlenin5000 on 2014-10-18
> **Bucky Ball said:**
> As mentioned, there is no way Ubuntu could have wiped your external drive if all you did was plug it into the machine while booted into Ubuntu. Not possible. You would need to delete them manually. 

Exactly. Unless... You had the drive connect during the installation and inadvertently installed Ubuntu in that drive. The folders/files you just listed certainly look like you have have some Linux installed precisely in that drive.

---

### Post by O9aIevckc0 on 2014-10-18
assuming you have accidently put ubuntu on the drive and lost your files

if its important i would either pay for a profesional data recovery service 

if its not quite so important you could try photorec following this guide

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by Bill_Leonard on 2014-10-18
Thanks everyone for the much-appreciated feedback.  Now I remember -- I think that I forgot to unplug the external HDD from the USB port when I was installing Ubuntu which resulted in Ubuntu thinking that the external HDD was part of the whole system that I wanted under the management of Ubuntu.  I'm going to try the different suggestions and see if I can get back what is missing.  Will let everyone know one way or the other -- thanks.

---

### Post by Bucky Ball on 2014-10-19
Main thing is DON'T BOOT FROM THE DRIVE! The more you use it, the less chance there is of recovering everything. You see, when you delete something, the data remains but the system marks the bit of the drive where it lives as 'writable'. If you use the disk, it will see where the data is as writable and write right over your data.

Boot from the LiveDVD/USB instead to investigate.

---

### Post by Bill_Leonard on 2014-10-19
Photo_rec is working!  I have it running on my external HDD from Ubuntu using the command in the link sent by abpabp.  I didn't know where the files were so .. I selected the whole 2tb & selected to look for fat32/NTFS file system. It's finding my missing files & putting them onto my Linux+based laptop. It detects the correct file type (Java, ppt, doc, jpg, mpg, txt, etc).  For doc (ms word) it creates the name from the first sentence in the file (along with a unique generated string).  For others it just generates the name as a unique string with no meaning.  I'm going to then format by external HDD as either NTFS or UDF (haven't decided yet) and copy the files back on & rename them.

---

### Post by Bill_Leonard on 2014-10-21
Final set of notes:  photo_rec finished after something like 54 hours for a 2TB external hard drive. I was going to stop it at a couple of point because I thought it was broken when it would go back to processing sectors that it had already processed (and the estimate time left would change from, let's say, 4 hours to 8 hours).  I saw a thread from the author ([http://forum.cgsecurity.org/phpBB3/photorec-stuck-in-cyclic-reading-t1936.html](http://forum.cgsecurity.org/phpBB3/photorec-stuck-in-cyclic-reading-t1936.html)) explaining why this behavior is ok so ... I let it run.  

I'm now formatting my external hard drive via Linux by following: [http://www.runtime-era.com/2012/01/format-external-hard-drive-using.html](http://www.runtime-era.com/2012/01/format-external-hard-drive-using.html)  Note: I was going to format it as UDF (compatible w/ Linux, Windows, Mac) but decided to use NTFS (compatible with all 3 as well).  It was currently formatted as ext3/ext4 (I read that you can get drivers for windows to understand ext3).

---

### Post by Bill_Leonard on 2014-10-21
Final set of notes:  photo_rec finished after something like 54 hours  for a 2TB external hard drive. I was going to stop it at a couple of  point because I thought it was broken when it would go back to  processing sectors that it had already processed (and the estimate time  left would change from, let's say, 4 hours to 8 hours).  I saw a thread  from the author  ([http://forum.cgsecurity.org/phpBB3/photorec-stuck-in-cyclic-reading-t1936.html](http://forum.cgsecurity.org/phpBB3/photorec-stuck-in-cyclic-reading-t1936.html))  explaining why this behavior is ok so ... I let it run.  

I'm  now formatting my external hard drive via Linux by following:  [http://www.runtime-era.com/2012/01/format-external-hard-drive-using.html](http://www.runtime-era.com/2012/01/format-external-hard-drive-using.html)   Note: I was going to format it as UDF (compatible w/ Linux, Windows,  Mac) but decided to use NTFS (compatible with all 3 as well).  It was  currently formatted as ext3/ext4 (I read that you can get drivers for  windows to understand ext3).

---

